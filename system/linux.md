# Linux

Documentation made by Shisuko

*** 

## Summary
1. What's Linux ?
2. Distribution
3. Utility
4. File system
5. Bash


## 1. What's Linux ?
Linux is a open-source OS based on Unix. It's very lightweight and it's the most use OS for running server around the world. The creator of Linux is Linus Torvald.

## 2. Distribution
Linux is just the kernel. It's the heart of the OS. There's somethings call distribution in Linux. It's exploatation system using the linux kernel. Each distribution have their own differences and avantages. There's a list of most used distribution in linux :

There's 2 main distribution, Debian and Arch. A lot of distribution are based on this distribution. For example Ubuntu and Mint are Debian based distribution. And Manjaro is Arch based distribution.

Fun fact : Android is linux based. Which make linux the first operating system in the world because android is used by 3,6 Billions of personn.

## 3. Utility
Linux is great for running server. More than 90% webserver of the world are debian server or debian based server.

## 4. File system
Here is the linux files system : 

![Image not found](/img/linux-filesystem.webp)

Let me explain all this folder. First of all linux use one and only one file system which is "/" even if you plug a external drive in your computer it won't be another file system.

The "/bin/ is not a folder but a link to "/usr/bin".   
The "/opt" is for all optionnal package (application) that you want to install (not realy used).   
The "/boot" store file for the boot loader (grub for example) and other file to boot the PC.   
The "/root" folder is the home partition of the root which is the superuser of linux.   
The "/dev" is where every driver are store.   
The "/sbin" is not a folder but a link to "/usr/sbin".   
The "/etc" folder is where every text configuration file are stored.   
The "/srv" folder is for service.   
The "/home" folder is where every user home is stored.   
The "/tmp" is a folder that contain temporaray file (it clean up after shutdown).   
The "/lib" is a link to "/usr/lib". 
The "/usr" is a folder that contain user file.   
The "/media" is a folder where external drive will be mount.   
The "/var" is a folder that contain different variable.   
The "/mnt" is a folder where you can mount manualy your drive.

In the "/usr" folder, there's other folder like bin, lib and sbin.

The "/usr/sbin" folder contain super-user application (require super-user perm to execute it).   
The "/usr/bin" folder contain application.   
The "/usr/lib" is a folder that contain necessary librairy for linux to run.  

## 5. Bash

In linux you can use the terminal for everything. The terminal is just a application. The backend of that application is call "Shell". There's a lot of shell, for example "zsh", "bash", "sh" etc...

The basic one is bash.

Here's a list of command that you can do on linux (debian) : 

|Name|Utility|Syntax|Example|
|-|-|-|-|
|cd|Change direcotry|cd \<directory>|cd /usr/bin|
|ls|List direcotry|ls \<directory>|ls /usr/bin|
|pwd|Show current directory|pwd|pwd|
|touch|Create a empty file|touch \<file>|touch test.txt|
|man|Show the manual of a command|man \<command>|man ssh|
|cp|Copy file to a folder|cp \<source> \<destination>|cp ~/test.txt ~/documents|
|mv|Move file to a folder|mv \<source> \<destination>|mv ~/test.txt ~/documents|
|whoami|Display current user|whoami|whoami|
|rm|Remove file or folder|rm \<file>|rm ~/documents/test.txt|
|mdkr|Create direcotry|mkdir \<direcotry>|mkdir test|
|exit|Exit session|exit|exit|
|su|Switch user|su \<user>|su root|
|echo|Return a variable|echo \<variable>|echo $HOME|
|free|Show memory usage|free|free|
|lsblk|Show drive|lsblk|lsblk|
|ln|Create a link to a file or a folder|link \<source> \<destination>|ln test.txt /opt/test.txt|
|kill|Kill a processus|kill \<pid>|kill 1442|
|sudo|Execute with superuser|sudo \<command>|sudo pwd|

You can get information about any command by typing : 

```bash
<command> --help
```























***

Twitter : @Shisukkko

