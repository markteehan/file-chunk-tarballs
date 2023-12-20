# file-chunk-tarballs
This repo is a self-contained tarball (=zipfile) containing the components to send binary files (images, video, audio etc) as data streams.
The tarball contains an uploader and a downloader: the streaming service starts on windows or on linux. 
Elevated privileges (admin or root account) are not required: the service runs in a CMD window.


## Requirements
### Windows
1/ An app to unzip a ".tar" tarball archive. All other requirments are bundled (Java, Apache Kafka client etc)

2/ 720MB (*2) for the tarball archive and its unzipped contents

3/ 512MB or more of allocatable memory for the JVM

* note that the tarball uses its own bundled Java executable and its own 

### Linux
1/ The linux built-in "tar" cmd. The streaming service will uses its own bundled JAVA_HOME; even if java exists elsewhere on the OS

2/ other requirements are the same, as per for Windows above.

## Un-installation Instructions
If running, close the CMD window running the Streaming service.
Delete the C:\data-streaming directory.

## Installation Instructions

### Windows
1/ In a browser, navigate to http://gihub.com/markteehan/file-chunk-tarballs. In the repo file list, click on "data-streaming-1.0.0.tar" to open the rep file view. In the header bar, the tarball size is listed (~700MB).  Before downloading this file, check that the destination download folder does not contain older downloads(s) - the windows behaviour of adding " (1)", " (2)" etc will cause path naming problems later on - so remove older download tarballs from the destination folder. Click on the "Download Raw File" button (with a downward arrow; next to "Raw").  The zipfile is several hundred MB in size so download may take a few minutes. 

2/ Using File Explorer, double click on "data-streaming-x.x.x.tar". If there is more than one downloaded tarball then delete all tarballs and restart the download. Double-click the zipfile and set the "Output Path" to C:\

3/ When unpacked, using explorer, navigate to C:\data-streaming and double click "configure-windows.bat"

### Linux
Steps 1/ and 2/ are the same
3/ When unpacked, in a shell, run ~/data-streaming/configure-linux.sh

## Authentication
Confluent Cloud requires authentication credentials to connect securely to an endpoint. 

### Windows
Create c:\data-streaming\env.cmd with three lines:
```
SET BOOTSTRAP_SERVERS="pkc-xxx.xxx.xxx.confluent.cloud:9092"
SET APIKEY="XXXXXXXXXXXXXXXX"
SET SECRET="XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
```

### Linux
Create ~/data-streaming/env.cmd with three lines:
```
export BOOTSTRAP_SERVERS="pkc-xxx.xxx.xxx.confluent.cloud:9092"
export APIKEY="XXXXXXXXXXXXXXXX"
export SECRET="XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
```


## Start the Streaming Service
Follow the steps to start the streaming service in a CMD window:
 Configuration Complete. Follow these steps to begin streaming
 1. Start the Streaming Service 
    c:\data-streaming\scripts\streaming_service_start.bat
 2. Start the Uploader
    %C:\data-streaming\scripts\streaming_uploader_start.bat
 3. Start the Downloader (optional)
    C:\data-streaming\streaming_uploader_stop.bat



