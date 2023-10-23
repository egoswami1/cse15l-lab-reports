# Lab Report 1: Remote Access and FileSystem

The following examples presented demonstrate the use of 3 different commands to use within a terminal: `cd`, `ls`, and `cat`.

---
## 1. `cd`
This command is used to change the current working directory to a different one.

Example of using `cd` with no arguments:

![image](https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/b74be326-000d-4e2c-a202-5651ee729858)

As we can see, nothing happens! The working directory is still the home directory. This happens because `cd` needs a directory as an argument to move the working directory to. In this case we aren't telling the current working directory to change to anything. However this is a special case. If we start in a different directory other than the home directory, typing the command `cd` without any arguments will always bring us back to the home directory as shown below.

<img width="189" alt="image" src="https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/4787373d-c9bf-4fe9-87fc-99eb9967f7ba">

Example of using `cd` with a path to a directory as an argument. We will be using the directory `lecture1`:

![image](https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/58524b39-5a0e-4320-a24e-90972ad89a16)

This time, the current working directory changes to `/home/lecture1` because we gave the command a relative path to a directory to move to.

Example of using `cd` with a path to a file as an argument. We will be using the file `en-us.txt `.
First we will change the current working directory to `/home/lecture1/messages` and then try the new argument.
This will allow the terminal to find the file we want to work with:

![image](https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/55d044b6-977d-4587-aede-44bb8d40ce7f)

As we can see, the terminal responded with an error saying that the file we used as an argument isn't a directory. Only a directory can be an argument for this command. Thus, the working directory is still `/home/lecture1/messages`.

---
## 2. `ls`
This command lists files and directories of a specified location.

Example of using `ls` with no arguments. Our currenting working directory is `/home/lecture1`:

![image](https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/ca7756e8-5bb3-4e0d-8e81-31ec3d73c64e)

Because we started in the `lecture1` directory, this command responded without error with all of the contents within the `lecture1` directory.

Example of using `ls` with a path to a directory as an argument. We are once again starting in the `/home/lecture1` directory:

![image](https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/4151e008-8dd1-4e04-a914-fc2ad04091be)

Once again the command ran without error. In this instance, the command responded with all of the contents of the `messages` directory even though that wasn't our current working directory because we specified a path to that directory in the argument.

Example of using `ls` with a path to a file as an argument. This time, we are starting in the `/home/lecture1/messages` directory:

![image](https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/77473d58-3fc3-4195-8a61-a77c2471c1a8)

There was no error when this command ran. Because we specified a file, the command could only respond with that file because there are no other files or directories under the specified file.

---
## 3. `cat`
This command prints the contents of a file.

Example of using `cat` with no arguments. Our current working directory is `/home/lecture1/messages`:

<img width="148" alt="image" src="https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/397e47f8-a1ec-472a-8e90-7d4375048fa3">

In this example there was no error but the code doesn't stop running until we press ctrl-c. In this instance it is waiting for an input because we did not give it one. Typing a string of characters into the terminal and clicking enter will duplicate the typed string because `cat` is printing what we are typing. The working directory does not change.

Example of using `cat` with a path to a directory as an argument. Our starting working directory is the `lecture1` directory.

![image](https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/f1d55d49-e97f-4c70-8190-7b40bf9c9bcd)

As specified earlier, the `cat` command prints the contents of a file and the `messages` directory is not a file. Thus, the terminal responds with the above error message.

Example of using `cat` with a path to a file as an argument. Our starting directory is `/home/lecture1/messages`:

![image](https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/3c5853e7-4825-4424-8a3c-dba89185ed14)

Using `en-us.txt` as our file, the cat command reads the contents of the file and prints them without error as shown above.

---

That's everything here! Thank you for viewing this page!





