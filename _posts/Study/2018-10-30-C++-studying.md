---
layout: post
title: "C++ & OpenCV small skills"
date: 2018-10-30 16:27:26 +0900
categories: Study
tag: C++
---

* content
{:toc}



C++ and OpenCV settings
-----------------
The are two important points. My system is Mac. So use the Xcode to work for the OpenCV. The dylib file and the head source path and the lib sourch path to be the lib inside the Mac.

C++ and OpenCV for reading the video files
------------------
There are some essential functions used for getting the video data.
`VideoCapture cap;` is used for new a instance to do image analysis
`cap.open(fileName)` is used for open the file as a stream
`cap.isOpened()` is used to judge the open statement
`cap.get(parameters)` is used to get the parameters of the video

In the total function, we return the `vector<Mat>` which consist all the frames of Mat type we need. Then initial the Mat instance to push the data into the list.

Cover all the frames numbers we need. We need some more functions.
`cap >> estVideoMat;` is used for push the cap's frames into the Mat file
`.push_back(Mat.clone())` is used for save all the Mat file into the vector

This `.clone()` method is needed otherwise the estination Mat are all the pointer and once the cap stream is moved, all the data inside the frame list is changed. The out put will continue be the last one. So use this function to keep the data not to be changed by the pointer.

`cap.release()` is used to release the file out of the stream

C++ file io
----------------------





