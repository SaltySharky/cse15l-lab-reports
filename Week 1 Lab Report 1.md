# Remote Access and File Systems
This tutorial will show you how to log into a course-specific account on `ieng6`.

## Installing VScode
- Visit https://code.visualstudio.com/ to download the latest version of VS Code
- Click the download button on the left
  
![[Pasted image 20221014195801.png]]

- Locate the downloaded .exe file on your computer
- Double click to open it and follow instructions

## Remotely Connecting
- Open VS Code
- Open a new terminal using shortcut `Terminal → New Terminal`
- Enter command `ssh cs15lfa22**@ieng6.ucsd.edu`, replace the `**` with letters of your specific course account
- When you see this, type `yes` then `Enter`
  
![[Pasted image 20221014200626.png]]
- When prompted for your password, type it in (you won't be able to see what you type)
- When you have successfully logged in, you should see this message at the end:
![[Pasted image 20221014202830.png]]

## Trying Some Commands
Here are some specific commands you can try:
-   `cd ~`
-   `cd`
-   `ls -lat`
-   `ls -a`
-   `ls <directory>` where `<directory>` is `/home/linux/ieng6/cs15lfa22/cs15lfa22abc`, where the `abc` is one of the other group members’ username
-   `cp /home/linux/ieng6/cs15lfa22/public/hello.txt ~/`
-   `cat /home/linux/ieng6/cs15lfa22/public/hello.txt`

![[Pasted image 20221014203206.png]]