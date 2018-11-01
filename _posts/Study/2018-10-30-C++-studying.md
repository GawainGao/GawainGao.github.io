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
`struct dirent *ptr` new a instance of struct
`DIR *dir`
`dir = opendir(PATH.c_str())` open the folder from its name
`vector<string>files` is used to set a new list to save files name
```
while((ptr=readdir(dir))!=NULL)
{
	if(ptr->d_name[0]=='.')
		countinuel
	file.push_back(ptr->d_name);
}
```
These code is used for check the ptr pointer is still point to a file name. And remove the file name with the start of . or ..
The `.push_back` method is used to add new members to the vector.
`closedir(dir)` is used to close the io.

There is another way which can directly read a series of files.
Use the add of the string in C++.
`fileName = foalderName + "/" + to_string(number) + ".xxx"` can easily read all the files inside one foalder is the file name are in arranged.

Like the d_name, the dirent type of data also have other method such as `d_ino` and `d_type` and so on.

These method all include in the `dirent.h` head file.

There is also the situation we want to get the certain .exd files. The method is use the `#include <regex>`. This head file include the method to do the string match.
`regex reg_obj(exd, regex::icase);` and then `if(regex_match(ptr->d_name, reg_obj))` to find weather the exd match to the d_name in the file name.


C++ vector container
-----------
`vector<string> stringList` can initialize a new vector for string.
Use the `for` to get access into the vectore like a dictironary.
Use the `push_back` to add new item into the vector.
There are also a lot of other method for the vector type.




