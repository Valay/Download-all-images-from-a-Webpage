Problem Definition:
/******************************************************************************************************************************************************************


Java Application that when supplied with a Web URL, downloads all the JPEG images linked on the page using <IMG> tag and produces a file that has the results
from executing the following from within the Java application

1.  Color Histogram Utility written in C++
2.  Image dimension Utility written in Python

The output is in the following format

Image URL,Local path,Width,Height,Red,Green,Blue 

The source for the C++ and Python utilities can be found in jar file. 
(Works for standard linux environment)


*******************************************************************************************************************************************************************/

/************************  How to run this program  ***************************/

Make sure you have following libraries installed on your computer:
1) CImg library
2) libX11 (CImg depends on it)
3) PIL (Python Image Library)

And most important JAVA!

Go to command line and type following:
`````````````````````````````````````
$ java -jar downloadimages.jar URL

//replace URL with required URL 

example run

$ java -jar downloadimages.jar http://www.yahoo.com/ 



/******************************************************************************/


Design/Coding Decisions:
/*******************************************************************************************************************************************************************


Library for HTML parsing:
1) Jsoup html parser. (http://jsoup.org/)

Libraries for CPP Utility:
1) CImg libray (I just copied the CImg.h into CPP Utility folder).
2) libX11 (I downloaded it using sudo apt-get installer and it downloaded all its dependencies).

Libraries for Python Utility:
1) PIL (Python Imaging Library, used sudo apt-get installer)


Steps followed in the Program:
````````````````````````````
1) User enters the URL as a command line argument and the program connects the URL and downloads the HTML page.
2) The HTML is parsed to get all the IMG tags.
3) Then the program creates a DIRECTORY to store images. As multiple instance of this program can be ran simultaneously I used timestamp(in milliseconds) as directory name to give unique name to the directory created by each instance of the program.
4) I compile CPP utility and show errors if any of them occurs!
5) After creating the directory I loop over all the images in the Web Page and save only JPEG images.
6) I simultaneously ran CPP and Python Utilities on the images in the same loop.
7) The output is as expected in the problem definition.


/*********************************************************************
Output looks like this:

Image URL,Local path,Width,Height,Red,Green,Blue 

http://l.yimg.com/cv/ae/us/audience/121017/300x250lweyw4b9v.jpg,/home/valay/Dropbox/Images_2013Mar15_062230_174/300x250lweyw4b9v.jpg,300,250,0.327713,0.329234,0.343053

**********************************************************************/









