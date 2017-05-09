# QGIS Distribution for MAPIR Cameras
This repository contains the QGIS distribution for use with MAPIR cameras. The distribution is in a beta stage while we work on getting it placed in the QGIS plugin repository.

Camera supported:
- MAPIR Survey2 (all filter models)
- DJI Inspire X3 with [PEAU 3.97mm NDVI (Red+NIR) lens](http://www.peauproductions.com/products/gp39728) installed
- DJI Phantom 4 & 3 with [PEAU 3.97mm NDVI (Red+NIR) lens](http://www.peauproductions.com/products/gp39728) installed

Functionality for above supported cameras includes:
- Convert Survey2 RAW to TIFF, converts DJI DNG to TIFF
- Calibrate directory of images using [MAPIR Reflectance Target](http://www.mapir.camera/collections/accessories/products/mapir-camera-calibration-ground-target-package) image taken before survey or uses built-in reflectance values if no target image supplied
- Converts TIFF to JPG after calibration if desired

Functionality still in the works:
- Creating index images

### Installation
- Download and install QGIS program [HERE](http://www.qgis.org/en/site/forusers/download.html)
- Download the [MAPIR_Processing folder](https://github.com/mapircamera/QGIS/tree/master/Packages), unzip it and add the "MAPIR_Processing" folder to your C:\Users\ (your computer user name) \.qgis2\python\plugins folder (if the plugins folder does not exist, please create it). Note: Check to make sure there is no sub directory named "MAPIR_Processing" in your "MAPIR_PRocessing" folder. If there is, copy the contents of the sub directory to C:\Users\ (your computer user name) \.qgis2\python\plugins instead.
- Start QGIS as an administrator (right mouse click, run as admin). (Starting as admin only required the first time you run a new install of the plugin)
- In the Plugin menu, select "Manage and Install Plugins", search for "MAPIR", click the check box next to the "MAPIR_Processing" plugin.
- In the QGIS top Plugin menu bar, choose the MAPIR plugin.

![](qgis_folder.PNG)
![](qgis_folder2.PNG)
![](qgis_plugin.PNG)

##Attention: We've found a fatal flaw in trying to run the plugin on MacOS, Mac support will be discontinued until further notice


### Using Plugin

- To pre-process images (convet RAW images to TIFFs):
-- Select the "Pre-Process" tab
-- Select a camera model
-- Select an input folder
-- Select an output folder
-- Press the "Pre-Process Images" button

- To Calibrate images
-- Select the "Calibrate" tab
-- Select a camera model
-- Select a MAPIR ground target image (optional)
-- Press the "Generate Calibration Values" button
-- Select a folder containing images to calibrate
-- Press the "Calibrate Images From Directory" button

### Credits
 - [Photomonitoring Plugin](https://github.com/nedhorning/PhotoMonitoringPlugin) by Ned Horning - American Museum of Natural History, Center for Biodiversity and Conservation

## Change Log
All notable changes to this project will be documented in this file.

### [1.1.3] - 2017-05-09
#### Fixed
-Uploaded correct UI file
-Camera model index logic
-Calibration values generated from default JPG image calibration

### [1.1.2] - 2017-05-08
#### Fixed
-An logic error when reading .tiff calibration target images.

### [1.1.1] - 2017-04-16
#### Fixed
-Typoes cv2tColor -> cvtColor.

### [1.1.0] - 2017-04-05
#### Fixed
- Issue where JPGs from the DJI model cameras were coming out black.

### [1.0.9] - 2017-04-03
#### Fixed
- Issue locating QR taget when supplied with a JPG.
- Issue processing images from Survey1 camera.

### [1.0.8] - 2017-03-07
#### Fixed
- Issue with Calibration step and inproper indexing of camera models.

### [1.0.7] - 2017-03-02
#### Changed
- Removed the Vignette correction and color normalization due to a critical flaw in the design. 
- Modified the UI to support lens and filter options for future use.

### [1.0.6] - 2017-02-10
#### Changed
- Plugin now allows for users to trun vignette correction on/off

### [1.0.5] - 2017-02-07
#### Fixed
- EXIF information now properly copied, including geotagging information
- Program no longer tries to read GDAL projections from images other than GeoTIFFs

### [1.0.4] - 2017-01-31
#### Added
- Vignette correction

#### Changed
- Vignette correction and normalization are now always performed

#### Fixed
- Plugin now transfers projection data in preprocess and calibrate steps

### [1.0.3] - 2016-12-19
#### Added
- Normalization of RGB images in the Preprocess step.

### [1.0.2] - 2016-12-15
#### ADDED
- Transfer of GeoTIFF metadata.

#### CHANGED
- Application no longer requires administrator access to run on Windows.

#### FIXED
- Plugin no longer loads non image files with "tif" or "jpg" in the filepath.

### [1.0.1] - 2016-12-13
#### ADDED
- Legacy support for Survey1 camera models in Calibrate tab.

### [1.0.0] - 2016-12-13
#### ADDED
- MacOS X is now supported

#### Fixed
- Plugin now warns when trying to overwrite tiffs created when preprocessing DNG images instead of throwing an exception.

### [0.0.3] - 2016-12-6
#### Fixed
- Tiffs now properly convert to Jpegs when checking the "Convert calibrated tiffs to jpgs" box

#### TO DO
- Found issues when trying to install plugin on Mac OSX. Working on a solution.

### [0.0.2] - 2016-12-2
#### ADDED
- Now stores previously selected filepaths to make navigation easier

#### Changed
- Cleaned up UI layout

#### FIXED
- Missing default calibration for DKI camera models
- QR calibration percentage values

### [0.0.1] - 2016-12-1
#### FIXED
- Issue with merging channels in DJIx3 images


