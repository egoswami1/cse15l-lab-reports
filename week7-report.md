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

Keys pressed: `<up><up><up><up><up><up><up><up><up><up><up><up><enter>``<up><up><up><up><up><up><up><up><up><up><enter>` The `cd lab7/` command was 12 up in the search history so I used the up arrow key to access it and switch the working directory. Similarly the `bash test.sh` command was 10 up in the search history so I used the up arrow key to access it. 
The above image shows the failing results of running the tests.

## Step7: Edit the code to fix the failing test

Keys pressed: `<up><up><up><up><up><up><up><up><up><up><up><up><enter>``<r><2>` The `vim ListExamples.java` command was 12 up in the search history so I used the up arrow key to access it which opens the file within terminal allows me to edit. I then clicked the following 2 keys to replace the "1" with a "2" on line 34 in the variable called `index1`.
