Using OpenCV with Biicode dependency manager
========================================

[**Biicode**](http://opencv.org/biicode.html) is a solution for resolving and keeping track of dependencies and version compatibilities for C/C++ projects. 

Using the *"hooks” feature* of biicode, **getting started with OpenCV in C/C++** is very simple. Just write an `#include` to opencv headers and biicode will manage to retrieve and install OpenCV in your computer and configure your project.

As simple as that, that's why it is a great tool to use OpenCV in an easy way.

In the following lines, we'll try to describe how to get started with OpenCV using [Biicode](http://www.biicode.com/).

---------
Prerequsisites
----------------
This tutorial assumes that you have de following avaliable in your computer:

 1. Last version of Biicode tool.
 2. If in Windows: Any Visual Studio version (Visual Studio 12 preferred).

Installation
------------
The installation of Biicode is quite simple, follow the next [link to install it at any OS](http://www.biicode.com/downloads).

----------

Example
-------
In this example we'll show how to detect faces in images using the [*objdetect module* from OpenCV](http://docs.opencv.org/doc/tutorials/objdetect/table_of_content_objdetect/table_of_content_objdetect.html).

After donwloading an isntalling Biicode, do the following steps:

	$ bii init mycvproject
	$ cd mycvproject
	$ bii open diego/opencvex
If in windows:
		
		$ bii cpp:configure -G "visual Studio 12"

Then we can build the project. **Note** that this can take a while, until it downloads and builds OpenCV. However, that this is done only once in your machine, in your "user/.biicode" folder. If the opencv installation process fails, you might simply want to go there, delete opencv files inside "user/.biicode" and repeat.

	$ bii cpp:build

Your binaries are located inside the bin folder:
	
	$ cd bin
	$ ./diego_opencvex_main

![](images/biiapp.jpg)


	$ ./diego_opencvex_mainfaces

![](image/lena.jpg)

--------


Developing your own application
---------------------------------------

Biicode works with **#include** headers in your sourcecode files, it reads them and retrieve all the dependencies on our database. So it is as simple as typing #include *"diego/opencv/opencv/cv.h"* in the headers of your *.cpp* file.

To start a new project using OpenCV, just do the following:

	$ bii init mycvproject
	$ cd mycvproject

The next line just create a *myuser/myblock* folder inside "blocks" with a simple "Hello World" *main.cpp* inside it. You can also do it by hand:

	$ bii new myuser/myblock --hello=cpp

Now replace your *main.cpp* contents inside *blocks/myuser/myblock* with **your app code**.
Put the includes as:
	
`#include "diego/opencv/opencv/cv.h`

If you type:

	$ bii deps
You will check that ***opencv/cv.h*** is an "unresolved" dependency. You can find it with:

	$ bii find

Now, you can just configure and build your project as described above.

If you want simpler *#include* directives, you can configure it in your **biicode.conf** file. Let your includes be:

`#include "opencv/cv.h"`

And then just write in your **biicode.conf**:

	[includes]
	     opencv/cv.h: diego/opencv
	[requirements]
	     diego/opencv: 0

----------
Switching OpenCV versions
--------------------------------
If you want to try or develop your application against **opencv 2.4.10** and also try **3.0-beta**, you can change easily in your **biicode.conf** file, simply alternating track in your requirements:

	[requirements]
		diego/opencv: 0
replace with:

	[requirements]
	    diego/opencv(beta): 0
	    
**Note** that the first time you switch to 3.0-beta, it will also take a while to download and build the 3.0-beta release. From that point you can easily change forth and back between versions, just modifying your *biicode.conf requirements*.

The hooks that will be used are in these blocks:

 - [OpenCV 2.4.10](http://www.biicode.com/diego/opencv)
 - [OpenCV 3.0 beta](http://www.biicode.com/diego/diego/opencv/beta)

This is just an example of how can it be done with biicode python hooks. Probably now that CMake files reuse is possible, it could be better to implement it with CMake, in order to get more control over the build of OpenCV.

-------
For any doubts or further information regarding biicode, suit yourselves at [Stackoverflow](http://stackoverflow.com/questions/tagged/biicode?sort=newest), biicode’s [forum](http://forum.biicode.com/) or [ask biicode](http://web.biicode.com/contact-us/), we will be glad to help you.

