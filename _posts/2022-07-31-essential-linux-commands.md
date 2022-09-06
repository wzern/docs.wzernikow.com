---
title: Essential Linux Commands
date: 2022-07-31 12:00:00:00 -500
categories: [linux, terminal]
tags: [bash, linux]
---

---

If you’re considering using Linux, learning basic command lines will go a long way. In this article, you’ll learn 34 basic Linux commands that will undoubtedly help you navigate through Linux as a newbie.

---

- ## pwd command

  Use the pwd command to find out the path of the current working directory (folder) you’re in. The command will return an absolute (full) path, which is basically a path of all the directories that starts with a forward slash (/). An example of an absolute path is /home/username.

  ```bash
  pwd
  ```

- ## cd command

  To navigate through the Linux files and directories, use the cd command. It requires either the full path or the name of the directory, depending on the current working directory that you’re in.

  Let’s say you’re in /home/username/Documents and you want to go to Photos, a subdirectory of Documents. To do so, simply type the following command:

  ```bash
  cd Photos
  ```

  Another scenario is if you want to switch to a completely new directory, for example, /home/username/Movies. In this case, you have to type cd followed by the directory’s absolute path:

  ```bash
  cd /home/username/Movies
  ```

  There are some shortcuts to help you navigate quickly:

  ```bash
  cd .. # to move one directory up
  cd    # to go straight to the home folder
  cd -  # to move to your previous directory
  ```

  On a side note, Linux’s shell is case sensitive. So, you have to type the name’s directory exactly as it is.

- ## ls command

  The ls command is used to view the contents of a directory. By default, this command will display the contents of your current working directory.

  If you want to see the content of other directories, type ls and then the directory’s path. For example, enter

  ```bash
  ls /home/username/Documents
  ```

  to view the content of Documents.

  ### There are variations you can use with the ls command:

  ```bash
  ls -R  # will list all the files in the sub-directories as well
  ls -a  # will show the hidden files
  ls -al # will list the files and directories with detailed information like the permissions, size, owner, etc.
  ```

- ## cat command

  cat (short for concatenate) is one of the most frequently used commands in Linux. It is used to list the contents of a file on the standard output (sdout). To run this command, type cat followed by the file’s name and its extension. For instance:

  ```bash
  cat file.txt
  ```

  Here are other ways to use the cat command:

  ```bash
  cat > filename # creates a new file
  cat filename1 filename2>filename3 # joins two files (1 and 2) and stores the output of them in a new file (3)
  cat filename | tr a-z A-Z >output.txt # converts a file to upper or lower case use,
  ```

- ## cp command

  Use the cp command to copy files from the current directory to a different directory. For instance, the command

  ```bash
  cp scenery.jpg /home/username/Pictures
  ```

  would create a copy of scenery.jpg (from your current directory) into the Pictures directory.

- ## mv command

  The primary use of the mv command is to move files, although it can also be used to rename files.

  The arguments in mv are similar to the cp command. You need to type mv, the file’s name, and the destination’s directory. For example:

  ```bash
  mv file.txt /home/username/Documents
  ```

  To rename files, the Linux command is

  ```bash
  mv oldname.ext newname.ext
  ```

- ## mkdir command

  Use mkdir command to make a new directory — if you type

  ```bash
  mkdir Music
  ```

  it will create a directory called Music.

  There are extra mkdir commands as well:

  To generate a new directory inside another directory, use this Linux basic command

  ```bash
  mkdir Music/Newfile
  ```

  use the p (parents) option to create a directory in between two existing directories. For example:

  ```bash
  mkdir -p Music/2020/Newfile
  ```

  will create the new “2020” file.

---

#### Information from Hostinger.com
