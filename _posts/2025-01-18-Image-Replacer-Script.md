---
title: Image Replacer Script
date: 2025-01-18 00:00:00 +0000
categories:
  - Image Replacer Script
tags:
  - Script
  - Image
  - Replacer
---



## The Problem

This is my first blogpost about a script I wrote to fix my obsidian notes when linking the images I took in my notes to different sites, like github. Initially I was going to make this post about a cloud exploit with Graph Runner, but I ran into a problem when trying to post my images in obsidian notes onto my github site.



## What is Obsidian?

Obsidian is a popular note-taking knowledge management application that uses Markdown as its primary format for creating and editing notes. Its designed to help users create a personal knowledge base that can be easily linked, organized, and navigated. Obsidian allows users to create notes in plain text files with the .md (Markdown) extension, which can be viewed and edited using the app's built-in editor or any text editor that supports Markdown.



## The Linking Problem

I noticed when uploading my notes from obsidian to github, the images weren't there but instead there was just a string of a link to a png. That got me thinking about what would happen when I tried to upload a blog post, using obsidian to write it.

![](../assets/Images/Pasted%20image%2020250228085625.png)


My blogsite wasn't able to be deployed. Looking further into the error of why, we see that it was because github didn't know where those images were to pull them from. After doing some digging on google I found out it was because of 2 settings.


In the "links and files" settings:

The first setting needed to be changed to "relative path" so it knows how to link to the file.
The second setting (Wikilinks) needed to be turned off, this is a special obsidian only way of pulling image links that other sites do not understand.
The last setting is to point to where the images are being saved to and where they should access them.

![](../assets/Images/Pasted%20image%2020250228091339.png)


This worked and now the FUTURE images are being linked correctly.

![](../assets/Images/Pasted%20image%2020250228091540.png)


## Not Fixed, but Solution Found?

The big issue was that it did not change the links of any already existing linked images. It would take days of manual screenshotting and repasting through all my notes to fix every image. It would be much faster to simply write a script that scans my files replaces the old versions of image links to my new updated desired version.

### Building the Tool

The easiest way for our tool to do this would be to have it scan all the files in the directory specified and replace each instance where an image is linked with the new format. We also need need it to go through any more folders inside that directory just incase we have folders in folders in our notes.

![](../assets/Images/Pasted%20image%2020250313152332.png)


When reading the files we had an issue where the files couldn't be read due to their encoding type. Looking at the error it turned out that all files were either utf8 or windows-1252 encoded so we made our tool use one or the other if we got those errors.

![](../assets/Images/Pasted%20image%2020250314101459.png)


We told the tool to replace the old formatted links to the new ones and to write it to the files. 

![](../assets/Images/Pasted%20image%2020250314102214.png)


## Conclusion



Viewing the image links we can confirm that it worked. As well as the command line telling us it scanned each file.
![](../assets/Images/Pasted%20image%2020250318110630.png)


Images now show up on github as well so uploading our blogpost will now work, which you can tell by you reading this blogpost. 

![](../assets/Images/Pasted%20image%2020250318111133.png)


There are other already existing extensions that do similar things to this script regarding this issue, however I wanted to challenge myself to solve my own problem and write my own script. All in all, running into issues and solving them while improving the script was good practice and had a very practical use case. 

https://github.com/NicholasA-B/Image-Replacer