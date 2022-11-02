---
layout: post
title: Summer 2020 @ Citadel
permalink: /summer_2020_citadel/
---

### Below are a list of all commands that I've used at some point in time.

1) linux command to list all the processes going on 
 - top  - traditional way to ccheck the processes in linux
 - htop - advanced and more recent one. 
 - ps - lists all the processes runnning on the system.
 - ps   -A
 - ps   -A | less  -to show less and can press q when wanted to exit
2) to search for a specific process 
 - ps   -A  |  grep firefox.  - grep is a command used to find something in linux terminal. We used grep to find firefox's process ID and time it was on
3) Understand what tty1 and tty2 etc are in ubuntu. ps command outputs this.  
 - Looks like mine is tty2. Press Ctrl+Alt+F{1,2,...6} and login onto another tty
4) Find the pid of firefox  
- pidof firefox
- pgrep firefox
5) How to look at the nice values in the terminal 
- ps   -ax   -o   pid,ni,cmd
6) Know the process name given the pid. 
- ps   -p   pid   
- ps    -p   pid   -o   comm = 
- ps    -p   pid   -o   comm 
 - the process is selected with its pid with  -p. '-o' option specifies the output format. comm command gives the command name. Example firefox or kworker etc. 
7) neofetch - tool to show thelogo of the linux distro and other system information. 
8) install a package in linux - sudo apt-get install $package_name
9) check the disk space in linux - 
 - [Check disk space](https://www.cyberciti.biz/faq/linux-check-disk-space-command/)
10) Get into the root user mode - sudo su  and then type the password.
- Getting out of the root user  -  simply type exit.
11) custom commands in linux - [custom_comm](https://askubuntu.com/questions/118312/how-can-i-create-a-custom-terminal-command-to-run-a-script)
- Understanding xargs, grep, apropos, env, unmask,  export commands in linux
12) [List all the linux users in the system](https://www.cyberciti.biz/faq/linux-list-users-command/)
13) Move , copy , paste, rename files and directoriers in linux
Working with files and directories. 
- mkdir and rmdir - to make and delete directories
- But rmdir can only delete empty directories. **rm** option can be helpful in deletion of files and also non-empty folders. 
- Also check the man command to get complete information about the command we want to know about. Example - man mkdir.  
- touch - this command is used to make empty files in linux. Not the directories but just empty .doc or .txt files. 
- touch example.txt creates an empty .txt file in the current wrkng dir
- cp example.txt exx.txt - will copy and paste the file example.txt in the same folder with another name exx.txt.
- If you want to rename the file example.txt instead of copying it with a different name, then use  mv example.txt exx.txt
- How to delete the exx.txt that we just created. 
- rm command is used to delete the files and also directories,    although directories with files in them need special permissions. 
- rm exx.txt will delete the file exx.txt that was created in the curr_dir 
- How to copy and paste a file in one directory into another. 
- mv example.txt   ~ - moves the file example.txt into the home dir. '~' is home directory.
 - If you want to copy then use cp in place of mv. 
 - If you want to delete multiple files then mention the filenames after rm command. rm file1 file2 file3....
 - If you want to copy the directories use cp directory1 path_to_other_dir. If the directories have files in them you have to specify -r along with cp command.  the  -r is recursive copy of folder and also the files in the folder.  
## WARNiNG
Never type these dangerous linux commands in the terminal. 
- rm -rf/  - Deletes all the files in the home directory. Wipes off everything.  
- : ( ) { : | : & } ; :  - Deadly fork bomb that recursily uses all the resources of the PC and keeps running until the PC freezes. 

### April 26 2018
## [Linux Tip | 10 Useful Linux Commands](https://www.youtube.com/watch?v=vAdR-M9H_1w)
- **killall** - If we have an application on the system that is misbehaving. Like a web-browser doesnt function well and clicking on the 'x' doesnt respond. The way to use it is. 
 - killall $program_name  ------> killall firefox
- **touch** command - creates files. We can create just one file at a time with the help of the GUI. But with touch command, we can create multiple files at once. 
 - touch file1 file2 file3 
 - We cn use the touch command to change the access times of that file. Helps in backup. so if we touch an already created file, then the touch command changes the access or create time of those files. 
-  We can create flag files. for instance. For example - **sudo touch /forcefsck** and then asks for the password because it is in the root.  After running this command, when the system gets opened, it takes a moment to check if all the partitions are ok. 
- **which** - This command tells where a program is in the computer. 
 - **which rstudio** gives the location of the rstudio in the computer. 

-  **ping**  command - This command is used to check if there is any coonnectivity issues with the computer or any problems with the browser. etc. 
 - **ping www.google.com -c 3** -this command will send a request to the google server and see if the system is recieving the packets or not. Dash c '-c' and 3 are used to send and recieve just 3 packets. If not mentioned, the system will send request 64 times which we dont need. 
 
- **cat** command - cat command is used to print the contents of the file in the terminal. It is mainly used with 
 - **cat /etc/somefile** and not with the text file.
 - But if we read a text file, we have the whole output on the terminal screeen which we dont need. So. 
- To tackle the above case we have the **less** command. **less abc.txt** outputs the contents of the file in such a way that we can navigate the contents one line at a time. Also there is an old way to do it  is to use the cat command as shown below  
 - **cat longfile.txt | more** - This will be equivalent to the less command that we used in an old way. 
- **sudo -s** - This command gives you the root privilages. to exit frm this command just type **exit**. But this has to be done with caution, bacuase any small mistake in the root user access can damage the entire system. 
- **su username** - this command su space username helps us to jump into other user accounts without logging out and getting in at the GUI level. Just type su space username, type the password. and press enter. Even after doing that the pwd might still be in the user's directory. to completely change into the one you logged into. Type **cd ~** to get into their home directory.  
 - To exit from their desktop, just type exit and it will bring you back to your pc.
- sudo reboot - will reboot the system. Helpful if we want to  do a kernel update. Also useful if the desktop freezes. 
- If the system locks up and even the terminal doesnt show up we use somethimg called as tty.
- We can shutdown the system using the terminal, 
- sudo shutdown -h  ----> meaning i want the system to **halt**
- sudo shutdown -r  ----> system to reboot 
But what makes this command useful is that we can give it a time 
- sudo shutdown -h now ----> will shutdown the system just now. 
- sudo shutdown -h 15 ------> will shutdown the system after 15 mnts
- sudo shutdown -c ----> will tell the system to ignore the above command. 
- **man** - opens up the manual page for all the other commands. Useful one. 
- **caffeine** allows us to halt the system from going into sleep when we are away so that the applications do not go into sleep when we are away. Use **sudo apt-get install caffeine** command to install the package. 

How to change the screen resolution from the terminal 
- xrandr -s 1920x1080

