# Linux

Documentation made by Shisuko

*** 

## Summary
1. What's Linux ?
2. Distribution
3. Utility
4. File system
5. Bash
6. Install application in Linux   
6.1 Debian based   
6.2 Arch based   
7. Configure applications in linux
8. Scripts
9. Pipe and redirection



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
|which|Show the path of a command|which \<command>|which curl|
|type|Show information about a commmand|type \<command>|type cd|
|apropos|Search in the manual|apropos \<search>|apropos partition|
|alias|Create a alias|alias \<nom>="\<command>"|alias clear="clear && neofetch"|
|unalias|Remove a alias|unalias \<aliasName>|unalias clear|
|grep|Search a string in a file|\<command>\| grep \<string> |cat .bashrc \| grep "bash"|
|cat|Concat multiple file together|cat \<file> \<file> |cat text.txt test2.txt|
|sort|Sort a file|sort \<file> |sort test.txt|
|uniqu|Return unique value of a file|uniqu \<file>|unqiq file.txt|
|wc|Give information about file|wc \<file>|wc file.txt|
|head|Show x number of line of a file|head -n \<numberLines> \<file>|head -n 5 test.txt|
|tail|Show x number of line of the bottom of a file|tail -n \<numberLines> \<file>|tail -n 5 test.txt|


You can get information about any command by typing : 

```bash
<command> --help
```

## 6. Install applications in Linux

Install applications in linux is different in every distribution, for example in ubuntu you have what's called the snap store which contain a lot of application to install. But you rarely install applications via this store. In linux you can use the terminal to do everything. Here's how to install application in the most used distribution.

### 6.1 Debian based

In linux we use what's called "Package manager" it's a software that download, store and manage app via a simple command. In debian :

To install applications:
```bash
$ sudo apt install <package>
```

In debian you can also download manualy the package which are .deb and use dpkg to install it (dpkg don't install dependencies, apt does)

```bash
$ sudo dpkg -i <package>
```

To uninstall applications : 
```bash
$ sudo apt remove <package>
```



### 6.2 Arch based

In arch the package manager is called "Pacman"

To install applications :
```bash
$ sudo pacman -S <package>
```

To uninstall applications :
```bash
$ sudo pacman -R <package>
```

## 7. Configure applications in linux
In Linux every config are store in /etc and it's text file. So you can edit every configs files just by opening them. Here's how to config a simple ssh server in linux.

First of all we need to download a text editor. Depends on your distribution you may already have one like nano, vi, vim...   
I personnaly recommend "vim" it's fast, simple and very cool ! To download it type this command (debian) : 

```bash
$ sudo apt install vim
```

After this download the ssh server :

```bash
$ sudo apt update
$ sudo apt install openssh-server ssh
```

Now you have installed ssh you can configure it by using this command :

```bash
$ sudo vim /etc/ssh/sshd_config
```
You can now press "i" to enter into the insert mode.

And now you can edit every parameter that you want don't forget to type "ESC + : + wq" to quit and save you change made by vim ! 

## 8. Scripts
In linux you can create scripts to do some actions automaticly. For example imagine that you want to create a file, append some content into it and then show the content of the file. You can create a script to do it. Just create a file call "your_script.sh" and then use a text editor to write into it. Here's how the script is make : 

```bash
#/usr/bin/bash

touch test.txt # Create the file
echo "Hello world !" >> test.txt # Add content into it
cat test.txt # Show the content of the file.
```

Then you can type this command to make it executable : 

```bash
$ sudo chmod +x script.sh
```

And then you can run it by this command : 

```bash
$ ./script.sh
```

You can use variables in bash script to create a variable you need to put a "$" before the name of the variable :

```bash
#/usr/bin/bash
$hello = "Hello world!" # Create a variable that contain the string "Hello world!"

echo $hello # Print the content of the variable on the screnn
```

You can also use positioning variable so when you're using you script you can add parameter :

```bash
#/usr/bin/bash

echo $0 # Print the parameter
```

So when you're running your script like this :

```bash
$ ./script.sh "Hello world"
```

## 9. Pipe and redirection

You can reddirect the output of a command into a file :

```bash
$ cat .bashrc >> hey.txt 
```

You can also reddirect the output to another command with a pipe :

```bash
$ cat .bashrc | grep "txt"
```

We can send the normal output and the error output differently : 

```bash
$ ls >> test.txt 2> error.txt # We send the ls ouput to test.txt and the error output into error.txt
```

We can hide the output :

```bash
$ ls >> /dev/null
```

***

Twitter : @Shisukkko

