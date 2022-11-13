---
layout: post
title: Understanding Linux File System
permalink: /filesystem_hierarchy-standard/
---

To say that the Linux file system is confusing to navigate through and look at is an understatement. Especially as a new user It can be daunting and for the right reasons. 

A single wrong move and you destroy the boot loader or misuse the super user access and mess up your entire device. For that reason, let's go over the various directories in linux root directory and beyond and understand what their functions are. This tutorial assumes that you have a basic understanding of linux commands like `cd`,`ls`, `pwd`, `cat` etc. 

Some basics, first, when you do `Ctrl+Alt+T` on your keyboard, you will load up the terminal. And what you see there are generally two distinct words separated by '@'. The first half of that string tells you the username in your home directory. There could be multiple depending on how many users have accounts on your system. And the second half of the string is called the hostname or domain name. Consider that your machine's name.

And if you want to know who you are (username), just type `whoami` in the terminal and linux will tell you who you are. And if you want to know the hostname, then there are two ways to do that. Simply type `hostname` in terminal, or you can either do `cat /etc/hostname`. Remember this other one and will come back to it later when we discuss the file structure in linux. 

![whoami](/images/posts/whoami.png)   ![hostname](/images/posts/hostname.png)

Open your terminal and type `cd /` and that will take you to the root directory. Type the `ls` command to see the files and folders that are in this root directory. Alternatively if you want to see a tree, type `tree -L 1` and hit enter. 

What you see here are the important directories that almost every linux distro is made of and let's go over each of these in detail.      

# 1) /bin
The bin directory also called as binaries contains commands or programs that we can run. Note: There are several other bin directories in linux file structure like usr/bin and usr/local/bin. We will look into them later. Everytime you've switched directories until now you used the ls commands to display the contents of that directories. You will find that ls command in the form of a file here. These are binary executables that means you could look at the contents of that file right? Sure we can. let's take a look at what the ls commands looks like.
Looks like a bunch of gibberish doesn't it. Yes, you aren't supposed to understand anything because these are machine readable binaries. Other commands you should find here are cp, rm, cat etc. The cat command we used above to display the contents of a file is also here. That means you can also do cat cat and display the contents of itself. The difference between the bin directory right in the root vs the bin found elsewhere is that the binaries in this directory are considered system essentials. The bare minimum applications that your system requires to perform operations(until you mount /usr) in case you are in a single user mode.     


# **2) /sbin**
sbin also called the system binaries is like bin but it contains commands only the administrators can use. This directory contains executables too but unlike the /bin directory where even normal users can access those programs, the files in this program need root privileges and are most often useful for system administration and maintenance tasks. For example, you may want to delete that 4th user profile on your family PC coz your brother has moved out and has his own laptop. In that case, you probably would use the deluser command which resides in this directory. similarly you will find adduser command here which is used to mount a new user. Other popular commands like the root, init and ifconfig can be found here.  

# **3) /lib**
/lib directory contains the shared library files that the system needs to boot and also the binaries  we saw in the first two sections to function.  This directory is also home to the kernal modules so it's best not to mess with this directory.

# **4) /dev**
The /dev directory also called device is where you device files exist. That is, your solid state drives, hard drives, printers etc.  And what makes this directory so interesting is that it reiterates one interesting fact about the linux filesystem and that is "everything is a file in linux". That means you can cd /dev into this directory and locate your Hard drive and read it like a regular file. If you actually want to try the sudo cat sda command, then be ready with Ctrl + C to stop your terminal from exploding. There is a lot on this directory, but what's interesting are the sda files. In my case I only have sda. but if you have partitions made, you may see sda1 sda2 sda 3 etc, and if you have more drives mounted, you will see, sdb, sdc and so on.   

# **5) /boot**
As the name suggests, the /boot directory contains files that you system needs to boot. Pretty self explanatory and the other name for this directory is "DO NOT TOUCH". Don't mess with the contents of this directory unless you want to ruin your PC.



# **6) /home**
Now we come to the directory where we feel the most safe at. When you open your file manager and see folders like Documents, Downloads, Pictures etc, the home directory is where all of that exists. In the /home you will find user profiles. In my case, as you see there is only one (@drwho) but you could have multiple based on who's using the machine and in each user profile will they have their own personal files. Nothing fancy here. A neat little trick to keep in mind is this - Whenever you are in any unknown directory and feel a bit lost of overwhelmed, just type cd on your terminal and it will bring you to the home directory which is our safe and cozy space.


# **7) /root**
Just like regular users (@drwho) have their own home directory, the /root directory is our system administrator's home directory. One of the most secured directories in the linux file system. It doesn't even let me in. You could sudo ls root to look at its contents.Another one of those "DONT MESS WITH ME" privileges. In Ubuntu there are two ways you can get access to the root user. One is using the su command which stands for substitute user or super user  and the other is sudo command. They both achieve the same results but in a slightly different ways. Running su command actually lets you log into the super user account and run commands or scripts  unconditionally whereas sudo lets you be in the current user account while temporarily elevating your access to the root level. sudo is considered much more safer than su because of the inherent risks su command possesses.  

# **8) /usr**
The next directory is /usr also called the User directory and this is where things begin to get a little confusing for users. Type 'cd usr' and get inside it and take a look at its contents. That's strange. You have a another bin subdirectory, a lib and sbin folders too. Go inside the bin folder to see what you have? The contents are all the same as of the /bin directory in the root. Check sbin and you should see something similar. These days /bin and /usr/bin are identical meaning one is a symbolic link to the latter. But there is an interesting piece of history behind it as for why the original creators needed two separate directories when they're basically doing the same. In short due to storage and that being expensive back in the days. The technical difference betwen them is that the /bin folder contains bare essentials for the system to survive even before the /usr directory is mounted and the /usr/bin directory contains all the other files that users install later like word processors, search engines and other applicatins. 

# **9) /media**
This directory is a latest edition into the linux file system and is a successor to the /mnt directory. Simply put, this directory mounts drives. Any external storage you connect to your machine will be automatically mounted here as files. Take a look at the screenshots below. 

# **10) /mnt**
/mnt is the predecessor to the media directory and does the same function, i.e., it mounts drives too but something that a user does manually.

# **11) /opt**
/opt also called Optional contains any files that are optional. That is, any custom applications that the users write themselves or any add-on applications that are not part of the default installation. Let's take a look at my /opt folder. I have a few things in here. For the add on-softwares I would expect more applications to be in here. But it also makes sense to consider /opt folder as a secondary home folder.  

# **12) /proc**
The proc directory is another one of those weird directories because it's virtual. Linux file system facilitates running processes on a virtual file system mounted on /proc. From the root dir, type  'cd proc' and look at the contents of that directory. You see a bunch of numbers as directory names. These numbers are the pids. Look at my proc folder and you will notice that the total size of the contents in the directory is 0 which is weird. This is because these are created on the fly as they are read and are updated on the fly. In a nutshell this directory stores information about the various instances running on your system.   

# **13) /tmp**
Needs no introduction, /tmp stands for temporary. It contains all the temp files and directories that are being used by the computer and and are kept on disk. By default the files that are kept in the tmp folder are deleted within 10 days.

And there you have it. Now we have an idea of how linux file system is actually structured and how things from various directories work together to perform operations seamlessly. Although it may look like convoluted chaos, there is soo much efficency in how things are arranged here and as users it is very helpful to understand this 'chaos'. That said, bear in mind that although these are separate folders, they often work together exchanging files between the programs and scripts. So messing up one small thing could mean that you ruin your entire system. If you mess with the boot folder, you know your system wouldn't boot up properly. If you mess with the bin folder, then you may accidentally delete programs that the boot scripts depend on. Similarly messing with files in the /lib directory means ruining your kernel modules or the shared library files that bin and sbin depend on.

But that shouldn't stop you from exploring your OS. Happy Learning!
