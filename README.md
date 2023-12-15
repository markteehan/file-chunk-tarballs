# file-chunk-tarballs
This repo is a self-contained tarball (=zipfile) containing the components to send files (images, video, audio etc) as data streams.
The tarball contains an uploader and a downloader: they will start on windows or on linux. Start up whichever is required.
Steps are provided to 


## Installation Instructions

### Windows
IN a browser, navigate to http://gihub.com/markteehan/file-chunk-tarballs
In the repo file list, click on "data-streaming-1.0.0.tar" to open the rep file view. In the header bar, the tarball size is listed (~372MB). 
Before downloading, check that the destination download folder does not contain older downloads(s) - the windows behaviour of adding " (1)", " (2)" etc will cause path problems with these scripts.
Click on the "Download Raw File" button (with a downward arrow; next to "Raw") to download the tarball.  The zipfile is several hundred MB in size so download may take a few minutes. 
Once complete, using Explorer open the download folder and look for "data-streaming-x.x.x.tar". There must be one downloaded tarball: if there are more than one; delete all and restart the download.
Double-click the zipfile and set the "Output Path" to C:\.  <<can another folder be selected>>?

#### Setup Cloud authentication
The files stream to Confluent Cloud, which uses a secure endpoint with mandatory encryption and authentication.
The endpoint, apikey (username) and secret (password) are stored in C:\data-streaming\env.cmd.
Edit this file; add the real values and save it. Do not add quote characters.


#### Run Setup
In explorer, Navigate to c:\data-streaming-1.0.0\data-streaming and double click "configure-windows.bat
