# Lab Report Week 1
## Tutorial: How to log into a course specific account on `ieng6`

### Step1: VS Code
Download VS Code at this link: [https://code.visualstudio.com/](https://code.visualstudio.com/)
![Screenshot 2022-09-30 203109](https://user-images.githubusercontent.com/114527221/193386022-e54e550f-4368-4a7f-a804-2b7bf6c984de.jpg)

This shows a download page that will apear when clicking the link. Click the link and download the latest version of VS Code to your computer. Make sure you get the version that correlates to the type of processing system you have.

### Step2: Remotely Connecting
Find your student login to `ieng6` at: [https://sdacs.ucsd.edu/~icc/index.php](https://sdacs.ucsd.edu/~icc/index.php) and set a password for your account.

Then open a terminal in VS Code using the "New Terminal" button.
Type the command `ssh cs15lfa22zz@ieng6.ucsd.edu` replacing the "zz" with your specific login username. This will log you into the remote server.
![image](https://user-images.githubusercontent.com/114527221/193386435-04909549-2dda-450c-bd5f-1c06878b9d43.png)

Type in your password and your terminal should look like this. (FYI Nothing will actually show up when you are typing your passowrd).

### Step3: Trying Some Commands
Try the following commands:
- cd
- cd
- ls 
- ls -a
- cp /home/linux/ieng6/cs15lfa22/public/hello.txt ~/
- cat /home/linux/ieng6/cs15lfa22/public/hello.txt

![image](https://user-images.githubusercontent.com/114527221/193386642-8904b974-6422-4b6c-8a51-4530dc933c52.png)

These are examples of how they run within the terminal.
To logout of the remote server simply type `exit`.

### Step4: Moving Files with `scp`
To move a file from a local server to the remote server follow these steps. First exit the remote server and create a new file names test.txt.
Type a message within this text file. 

Afterwords go back to your terminal and type the command `scp WhereAmI.java cs15lfa22zz@ieng6.ucsd.edu:~/` where the zz is once again replaced with your specific login. This sends the text file to the remote server. And if you login to the remote server and type `ls -a` you will see that the file has been added there.
![image](https://user-images.githubusercontent.com/114527221/193388477-3271a46c-631f-45ad-985b-2b0d88b671c1.png)

You can run this program by typing `cat test.txt`
![image](https://user-images.githubusercontent.com/114527221/193389445-8c151ddc-02df-4b6f-a4eb-f6aa963236a1.png)

### Step5: Setting an SHS Key
For this step, the user creates a key so that they don't have to input a password every time they login. Typing the following commands will result with this:
![image](https://user-images.githubusercontent.com/114527221/193391816-ea167ba3-2404-43fd-9808-31a94410a1b7.png)

This creates a public and a private key.
From here you must copy the public key to the .ssh directory of your server. This should allow you to login to the remote server without a password.

### Step6: Optimization
Code can be simplified and combined to optimize the amount of keystrokes needed to run a program or find a file. For example running the code `ssh cs15lfa22zz@ieng6.ucsd.edu "cat test.txt"` will allow you to access a remote server text file without having to do the two step process of logging in and then running the file.
![image](https://user-images.githubusercontent.com/114527221/193392345-b6f47b5c-6ee3-4ae5-9ad0-1ec7d3e3bd34.png)

For more information on how to navigate and use a remote server contact me at egoswami@ucsd.edu
