# Lab Report 4: Vim

---
For this lab report I will reproduce the vim task from lab but I will take screenshots and record keystrokes at every step.

Before starting the timer/task I will note that I have already ran this task prior to this trial and thus have a history of terminal commands that I will reuse using arrow keys. My keystrokes and explanation will be included at every step so that there is no confusion. Additionally I will start with the clone ssh url of the lab7 directory already copied to my clipboard. Let's start! I will begin at step 4.

## Step 4: Login to ieng6
<img width="611" alt="image" src="https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/a7ce12c6-f58c-4337-991a-dd8e661ebbf2">

Keys pressed: `<up><enter>` The `ssh cs15lfa23nf@ieng6.ucsd.edu` command was the last command in the search history, so I used the up arrow to access it. After being prompted with a password I typed my password in and clicked `<enter>`. 
The above picture is the result.

## Step 5: Clone my fork of the repository
<img width="423" alt="image" src="https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/d0d49eef-f44a-4379-91c6-120a100be106">

Keys pressed: `<up><up><up><up><up><up><up><up><up><up><up><enter>` The `git clone git@github.com:egoswami1/lab7.git` command was 11 up in the search history so I used the up arrow key to access it. 
The above picture shows the lab7 repository cloned.

## Step 6: Run the tests, demonstrating that they fail
<img width="480" alt="image" src="https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/454722fc-ec60-4ed7-9c41-67999dfb40e7">

Keys pressed: `<up><up><up><up><up><up><up><up><up><up><up><up><enter>` `<up><up><up><up><up><up><up><up><up><up><enter>` The `cd lab7/` command was 12 up in the search history so I used the up arrow key to access it and switch the working directory. Similarly the `bash test.sh` command was 10 up in the search history so I used the up arrow key to access it. 
The above image shows the failing results of running the tests.

## Step 7: Edit the code to fix the failing test
<img width="463" alt="image" src="https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/5e8f553d-4abc-451a-8430-ad5f0aaa0861">

---
<img width="313" alt="image" src="https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/0f1aac6f-b9b7-4481-825b-d4cee543bea1">

Keys pressed: `<up><up><up><up><up><up><up><up><up><up><up><up><enter>` `<r><2><:><w><q><enter>` The `vim ListExamples.java` command was 12 up in the search history so I used the up arrow key to access it. This opened the `ListExamples.java` file and allowed me to makes edits. I then clicked the following 2 keys to replace the "1" with a "2" on line 34 in the variable called `index1`. The final three keys save the file and exit me out of vim editing.
I added multiple images to include what it looks like within vim editing.

## Step 8: Run the tests, demonstrating success
<img width="265" alt="image" src="https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/e7ee3360-c099-4510-a7ea-32cef724ec59">

Keys pressed: `<up><up><enter>` The `bash test.sh` command was 2 up in the search history beause we just used it so I used the up arrow key to access it.
The above image shows the now successful tests.

## Step 9: Commit and Push changes
<img width="397" alt="image" src="https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/c2193e2b-873d-49d6-aef0-d0df402f7835">

---
<img width="379" alt="image" src="https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/3fb356fb-0d7a-4169-a1c2-f31c256a4b11">

Keys pressed: `<up><up><up><up><up><up><up><up><up><up><up><enter>` `<up><up><up><up><up><up><up><up><up><up><up><enter>` `<up><up><up><up><up><up><up><up><up><up><up><enter>` `<a><f><i><x><e><d><esc><:><w><q>` The `git add ListExamples.java` command was 11 up in the search history so I used the up arrow key to access it. I repeated the key presses to access `git push` and `git commit`. Then I used the following arrow keys to type in the commit message "fixed", saved, and exited the file.
The following shows me add, pushing, and commiting `ListExamples.java` and a picture of me typing "fixed" for the commit message.
