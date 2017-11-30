# KinectV2 Python Calibration

Easy and fast camera KinectV2 camera calibration using Python 3.

This project is an updated fork of @tataraidze KinectV2 Camera calibration scripts. He describe his work, in Russian, in this link [here](http://habrahabr.ru/post/272629/) (in Russian). An English translation can be found [here](http://developers-club.com/posts/272629/).

# Dependencies
1. OpenCV 3.0 with Python 3 support
2. [PyKinect2](https://github.com/Kinect/PyKinect2)

## Installing on Windows
I recommend using [Anaconda](https://www.anaconda.com/download)'s 32 bits Python3 distribution. It bundles packages such as `comtypes` and `numpy`. 
1. Install Python 3 *32bits* from Anaconda's download [page](https://www.anaconda.com/download)
   Make sure to register Anaconda as your default path. *pykinect2* will not work on the 64bits distro ([more info here](https://github.com/Kinect/PyKinect2/issues/17)).
2. Clone and install `pykinect2`
   2.1. `pip install comtypes`
   2.2. `git clone https://github.com/Kinect/PyKinect2.git`
   2.3  `python -m easy_install PyKinect2`
3. Install OpenCV 3.3.1 (or newer from `https://www.lfd.uci.edu/~gohlke/pythonlibs/`).
   3.1. Download the right .egg file for your python version (e.g.: 3.6) and architecture (e.g.: 32bits).
     In my case I downloaded, [opencv_python‑3.3.1+contrib‑cp36‑cp36m‑win32.whl](https://download.lfd.uci.edu/pythonlibs/yhckc96n/opencv_python-3.3.1+contrib-cp36-cp36m-win32.whl)
   3.2. Install it with `pip`
     `pip install opencv_python-3.3.1+contrib-cp36-cp36m-win32.whl`

# File descriptions
* const.py - constants: paths, pattern size, e.t.c.
* takePictures.py - calibration data collecting
* calibrate.py -  single camera calibration (RGB or IR/depth)
* testDistortion.py - check whether distortion was removed or not
* stereoCalibrate.py - stereo camera calibration finds transformation |R,T| between depth camera space and RGB camera space
* depthCalibration.py - depth sensor calibration
* KinectV2.py - wrapper to PyKinect2 compensates distorion and systematic  error of depth sensor; combines depth, RGB and bodyIndex frames; saves data
* sample.py - small example of using KinectV2.py 

# How to use
1. Change constants in const.py
2. Collect data for geometric calibration by takePictures.py (20-30 images of object in different positions)
3. Calibrate RGB camera by calibrate.py
4. Calibrate IR/depth camera by calibrate.py
5. Find |R,T| transformation between depth camera space and RGB camera space by stereoCalibrate.py
6. Collect data for depth calibration by takePictures.py ()
7. Use sample.py to get corrected data 

Support for this work was provided by the Russian Science Foundation, project #15-19-30012. 
You can find more about the project [here] (http://www.rslab.ru/russian/project/rsf2/)
