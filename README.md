# file-chunk-tarballs
This repo is a self-contained tarball (=zipfile) containing the components to send binary files (images, video, audio etc) as data streams.
The tarball contains an uploader and a downloader: the streaming service starts on windows or on linux. 
Elevated privileges (admin or root account) are not required: the service runs in a CMD window.


## Requirements
### Windows
1/ Upload (or create) the credentials file env.cmd to your Documents Folder (see "Credentials" below)

2/ An app to unzip a ".tar" tarball archive (Winzip, Aukzip etc). All other requirments are bundled: Java, Apache Kafka client, etc.

3/ 720MB (*2) of free disk space on C:\ for the tarball archive and its unzipped contents

4/ 512MB or more of allocatable memory for the JVM

### Linux
1/ Upload (or create) the credentials file env.sh to /var/tmp (see "Credentials" below)

2/ The linux built-in "tar" cmd. The streaming service will uses its own bundled JAVA_HOME; even if java exists elsewhere on the OS

Other requirements are the same, as per for Windows above.


## Credentials
Confluent Cloud requires authentication credentials to connect securely to an endpoint. 
These are attached to your email (if sent by Mark) or you can configure your own credentials.

### Windows
In your Documents folder, create (or download) env.cmd with three lines:
```
SET BOOTSTRAP_SERVERS="pkc-xxx.xxx.xxx.confluent.cloud:9092"
SET APIKEY="XXXXXXXXXXXXXXXX"
SET SECRET="XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
```

### Linux
In /var/tmp, create (or Download) env.sh with three lines:
```
export BOOTSTRAP_SERVERS="pkc-xxx.xxx.xxx.confluent.cloud:9092"
export APIKEY="XXXXXXXXXXXXXXXX"
export SECRET="XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
```

## Un-installation Instructions
If running, close the CMD window running the Streaming service.
Delete the C:\data-streaming directory.

## Installation Instructions

### Windows
1/ Setup the authentication credentials (env.cmd or env.sh). The configuration script requires this file. 

2/ In a browser, navigate to http://gihub.com/markteehan/file-chunk-tarballs. In the repo file list, click on "data-streaming.tar" to open the rep file view. In the header bar, the tarball size is listed (~695MB).  Before downloading this file, check that the terget download folder does not contain older downloads(s) - the windows behaviour of adding " (1)", " (2)" etc will cause path naming problems later on - so remove older download tarballs from the destination folder. Click on the "Download Raw File" button (with a downward arrow; next to "Raw"). 

3/ Using File Explorer, double click on "data-streaming.tar" to unpack the archive using winzip/auksip or similar. If there is more than one downloaded tarball then delete all tarballs and restart the download. Set the "Output Path" to C:\

4/ When unpacked, use file explorer to navigate to C:\data-streaming and double click "configure-windows.bat"

### Linux
Steps 1/ and 2/ are the same
3/ When unpacked, in a shell, run ~/data-streaming/configure-linux.sh



## Start the Streaming Service
### Windows
Start the Streaming Service. This dos window will stay open; leave it open.
```
    C:\data-streaming\scripts\streaming_service_start.bat
```

In Explorer (or a second cmd window), start the uploader job. This window will close. 
```
    C:\data-streaming\scripts\streaming_uploader_start.bat
```
To test that the uploader is functioning, copy a .JPG file to C:\data-streaming\local\upload\queued. With 30 seconds or so, this file should be moved to c:\data-streaming\local\upload\finished (or error). Check the logfile in c:\data-streaming\local\logs

(optional) Start the downloader    
```
    C:\data-streaming\streaming_downloader_stop.bat
```
JPG files that were succesfully uploaded will be subsequently downloaded to C:\data-streaming\download 




