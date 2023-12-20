# file-chunk-tarballs
This repo is a self-contained tarball (=zipfile) containing the components to send binary files (images, video, audio etc) as data streams.
The tarball contains an uploader and a downloader: the streaming service starts on windows or on linux. 
Elevated privileges (admin or root account) are not required: the service runs in a CMD window.


## Requirements
### Windows
1/ An app to unzip a ".tar" tarball archive. All other requirments are bundled (Java, Apache Kafka client etc)
2/ 500MB (*2) for the tarball archive and its unzipped contents
3/ 512MB or more of allocatable memory for the JVM
* note that the tarball uses its own bundled Java executable and its own 

## Un-installation Instructions
If running, close the CMD window running the Streaming service.
Delete the C:\data-streaming directory.

## Installation Instructions

### Windows
In a browser, navigate to http://gihub.com/markteehan/file-chunk-tarballs
In the repo file list, click on "data-streaming-1.0.0.tar" to open the rep file view. In the header bar, the tarball size is listed (400-500MB). 
Before downloading this file, check that the destination download folder does not contain older downloads(s) - the windows behaviour of adding " (1)", " (2)" etc will cause path naming problems later on - so remove older download tarballs from the destination folder.
Click on the "Download Raw File" button (with a downward arrow; next to "Raw").  The zipfile is several hundred MB in size so download may take a few minutes. 
Once complete, using Explorer open the download folder and look for "data-streaming-x.x.x.tar". There must be one downloaded tarball: if there are more than one; delete all and restart the download.
Double-click the zipfile and set the "Output Path" to C:\.  <<can another folder be selected>>?

#### Setup Cloud authentication
The files stream to Confluent Cloud, which uses a secure endpoint with mandatory encryption and authentication.
The endpoint, apikey (username) and secret (password) are stored in C:\data-streaming\env.cmd.
Edit this file; add the real values and save it. Do not add quote characters.


#### Run Setup
In explorer, Navigate to c:\data-streaming-1.0.0\data-streaming and double click "configure-windows.bat
