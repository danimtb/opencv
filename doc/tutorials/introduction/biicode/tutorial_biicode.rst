.. _tutorial_biicode:

Using OpenCV with biicode dependency manager
============================================

Goals
-----
In this tutorial you will learn how to:

.. container:: enumeratevisibleitemswithsquare

  * Get started with OpenCV using biicode.
  * Develop your own application in OpenCV with biicode.
  * Switching between OpenCV versions.

What is biicode?
----------------

`biicode <http://opencv.org/biicode.html>`_ is a solution for resolving and keeping track of dependencies and version compatibilities for C/C++ projects. 

Using the *"hooks” feature* of biicode, **getting started with OpenCV in C/C++** is very simple. Just write an `#include` to opencv headers and biicode will manage to retrieve and install OpenCV in your computer and configure your project.

As simple as that, that's why it is a great tool to use OpenCV in an easy way.

Prerequisites
-------------

This tutorial assumes that you have the following available in your computer:

.. container:: enumeratevisibleitemswithsquare

  * biicode installed, here is a `link to install it at any OS <http://www.biicode.com/downloads>`_.
  * Windows users: Any Visual Studio version (Visual Studio 12 preferred).

Explanation
-----------

Example: Detect faces in images using the `objdetect module from OpenCV <http://docs.opencv.org/doc/tutorials/objdetect/table_of_content_objdetect/table_of_content_objdetect.html>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

After downloading and installing biicode, execute in your terminal/console:

.. code-block:: bash
	
  $ bii init mycvproject
  $ cd mycvproject
  $ bii open diego/opencvex

Windows users also execute:

.. code-block:: bash
	
  $ bii cpp:configure -G "visual Studio 12"

Then we can build the project. **Note** that this can take a while, until it downloads and builds OpenCV. However, this is done only once in your machine, in your "user/.biicode" folder. If the opencv installation process fails, you might simply want to go there, delete opencv files inside "user/.biicode" and repeat.

.. code-block:: bash

  $ bii cpp:build

You can find your binaries into the bin folder:

.. code-block:: bash

  $ cd bin
  $ ./diego_opencvex_main

.. image:: images/biiapp.png
    :alt: biiapp
    :align: center

.. code-block:: bash

	$ ./diego_opencvex_mainfaces

.. image:: images/lena.png
    :alt: lena
    :align: center


Developing your own application
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

biicode works with **#include** headers in your source-code files, it reads them and retrieves all the dependencies in its database. So it is as simple as typing #include *"diego/opencv/opencv/cv.h"* in the headers of your *.cpp* file.

To start a new project using OpenCV, just execute:

.. code-block:: bash

  $ bii init mycvproject
  $ cd mycvproject

The next line just creates a *myuser/myblock* folder inside "blocks" with a simple "Hello World" *main.cpp* into it. You can also do it manually:

.. code-block:: bash

  $ bii new myuser/myblock --hello=cpp

Now replace your *main.cpp* contents inside *blocks/myuser/myblock* with **your app code**.
Put the includes as:

.. code-block:: cpp

 #include "diego/opencv/opencv/cv.h

If you type:

.. code-block:: bash

  $ bii deps

You will check that ***opencv/cv.h*** is an "unresolved" dependency. You can find it with:


.. code-block:: bash

  $ bii find

Now, you can just `bii cpp:configure` and `bii cpp:build` your project as described above.

If you use regular *#include* directives, you can configure it in your **biicode.conf** file. Let your includes be:

.. code-block:: cpp

	#include "opencv/cv.h"     

And write in your **biicode.conf**:

.. code-block:: text

	[includes]
	     opencv/cv.h: diego/opencv
	[requirements]
	     diego/opencv: 0


Switching OpenCV versions
^^^^^^^^^^^^^^^^^^^^^^^^^

If you want to try or develop your application against **opencv 2.4.10** and also against **3.0-beta**, you can change it easily in your **biicode.conf** file, simply alternating track in your [requirements]:

.. code-block:: text

	[requirements]
		diego/opencv: 0

replace with:

.. code-block:: text

	[requirements]
	    diego/opencv(beta): 0
	    
**Note** that the first time you switch to 3.0-beta, it will also take a while to download and build the 3.0-beta release. From that point you can easily change forth and back between versions, just modifying your *biicode.conf requirements*.

The hooks that will be used are in these blocks:

.. container:: enumeratevisibleitemswithsquare

 		* `OpenCV 2.4.10 <http://www.biicode.com/diego/opencv>`_
 		* `OpenCV 3.0 beta <http://www.biicode.com/diego/diego/opencv/beta>`_

This is just an example of how can it be done with biicode python hooks. Probably now that CMake files reuse is possible with biicode, it could be better to implement it with CMake, in order to get more control over the build of OpenCV.


Results and conclusion
----------------------

Installing OpenCV with biicode is straight forward for any OS. 
Run any example like we did with *objdetect module* from OpenCV, or develop your own application. It only needs a *biicode.conf* file to get OpenCV library working in your computer.

Switching between openCV versions is available too and effortless.

For any doubts or further information regarding biicode, suit yourselves at `Stackoverflow <http://stackoverflow.com/questions/tagged/biicode?sort=newest´>`_, biicode’s `forum <http://forum.biicode.com/>`_ or `ask biicode <http://web.biicode.com/contact-us/>`_, we will be glad to help you.