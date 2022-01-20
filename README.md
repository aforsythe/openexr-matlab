# OpenEXR for Matlab

### Note
This is a modified mirror repository for the OpenEXR-Bindings from *HDRITools - High Dynamic Range Image Tools*. The original code is either incompatible or hard to compile with the latest versions of OpenEXR and mex, so we modified and cleaned-up their code to be hassle-free compatible with the latest versions of MATLAB, Xcode and the OpenEXR-Library.

The bindings were tested with MacOS 11.6, MATLAB 2021b 9.3.0, OpenEXR 2.5.7 (despite warning that it may not be compatible from MATLAB).

### What is it?
OpenEXR is a popular high dynamic range image fileformat mainly used by the film industry. This repository provides an interface for reading and writing OpenEXR files within MATLAB.

### Install
First, make sure you have setup up mex. Otherwise run
```
mex -setup
```
inside of MATLAB.

Install the latest version of the OpenEXR-Library, e.g. via apt
```
brew install openexr@2 ilmbase
```

Run `make.m` inside of MATLAB to compile the bindings. If you install  OpenEXR without Homebrew make sure the paths inside of `make.m` point to your OpenEXR installation.

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
