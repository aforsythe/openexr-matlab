# OpenEXR for Matlab

### Note
This is a modified mirror repository for the OpenEXR-Bindings from *HDRITools - High Dynamic Range Image Tools*. The original code is either incompatible or hard to compile with the latest versions of OpenEXR and mex, so we modified and cleaned-up their code to be hassle-free compatible with the latest versions of MATLAB, Xcode and the OpenEXR-Library.

The bindings were tested with Ubuntu 21.10, MATLAB 2021a 9.3.0, OpenEXR 2.5.4, GCC 11 (despite warning that it may not be compatible from MATLAB).

The original code can be obtained at [https://bitbucket.org/edgarv/hdritools/](https://bitbucket.org/edgarv/hdritools/). This code was adopted for Ubuntu 21.10 from [https://github.com/skycaptain/openexr-matlab](https://github.com/skycaptain/openexr-matlab). The original copyright remains to Jinwei Gu and Edgar Velazquez-Armendariz.

### What is it?
OpenEXR is a popular high dynamic range image fileformat mainly used by the film industry. This repository provides an interface for reading and writing OpenEXR files within MATLAB.

### Install
First, make sure you have setup up mex. Otherwise run
```matlab
mex -setup
```
inside of MATLAB.

Install the latest version of the OpenEXR-Library, e.g. via apt
```bash
apt install libopenexr-dev
```

Run `make.m` inside of MATLAB to compile the bindings. If you install  OpenEXR without Homebrew make sure the paths inside of `make.m` point to your OpenEXR installation.

##### Ceveats
You may also need to update `~/.matlab/YOUR_MATLAB_VERSION/mexopts.sh` (e.g. in case you get a xcodebuild error, saying a SDK can not be located). Just change all occurances of e.g. `macosx10.8` to your version e.g. `macosx10.10` (3 occurances, comments excluded). If you are still getting errors, make sure you have the correct version of XCode installed or install the SDK for your system (http://www.mathworks.com/matlabcentral/answers/243868-mex-can-t-find-compiler-after-xcode-7-update-r2015b)

You might also have issues with the GLIBCXX library version, which is [discussed here](https://de.mathworks.com/matlabcentral/answers/643300-why-do-i-receive-the-error-libstdc-so-6-version-glibcxx_3-4-22-not-found-when-trying-to-star).

### Usage
##### exrread
	>> image = exrread('my_image.exr');
	>> size(image)
	ans =

	        1080        1920           3

	>> max(image(:))
	ans =

	    2.9297

	>> min(a(:))
	ans =

	    0.3069

##### exrwrite
	>> a = 100 * rand(300,300,3);
	>> size(a)
	ans =

	   300   300     3

	>> exrwrite(a, 'a.exr');
