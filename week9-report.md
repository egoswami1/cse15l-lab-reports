# Lab Report 5: Putting it All Together

---
For this lab report I will introduce a debugging scenario between a student and a TA as it would appear on an app like EdStem.

## Post 1: Symptom
From Student:

Hello! I am having trouble figuring out what is wrong with my code! I am trying to fix my merge method within the ListExamples.java file but I don't know what's wrong. When I run the test cases, this is what I get. I'll show a picture of my test cases as well.

<img width="600" alt="image" src="https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/882ffa53-f143-4c5d-abe3-bbc59383917d">


<img width="597" alt="image" src="https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/a11305dc-2679-4235-b626-f57646143ef0">

I know the merge method is supposed to merge two sorted lists into one sorted list but it's not working properly. I see in the failed test case that the first element in the sorted array is a "c" when it should be an "a" so maybe it has something to do with indexing at either the front or end of one of the merging lists. My first test case passes showing that the lists do merge and have the correct size so it has something to do with the placement of the sorted elements into the new list. I'm going to try looking into more detail about the contents of the failing merge list, like what's in the rest of the array. Please let me know if there's anything specific I should try to find out what is wrong with my code.

## Post 2: TA Response

Hi! Looking at your screenshots and your code I can suggest a few things. The most general in any case is to manually process your code by hand. Run through your code using your inputs and write down what you get in your notes. Using that information analyze the order in which elements are placed in the new list or any unusual actions that you may want to look into, like the addition of new elements or the loss of elements. How are your elements added into your merged list and where?

## Post 3: Student Testing/Response

I took some of the suggestions you made and applied them. The first thing I did was add a small loop towards the end of my method that would print the contents of the `result` list to the terminal when I ran the code. Here is what I got when running `test.sh`. 

<img width="198" alt="image" src="https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/eeb17d95-a658-4893-9ad2-cfecf0145e3c">

The string of letters at the bottom is the order in which they appear in the `result` list. Now that I had the order of the elements in the list I wanted to find out the order in which they got into the list and how the ended up in their specific locations. I manually ran through my test case using a pen and here are my results.

<img width="930" alt="image" src="https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/644b79ed-c105-42dc-a6db-b13873fe337d">

In this small drawing I labeled the elements in the list, which list the specific element came from, and the order in which they were added to the list. This is interesting because the elements were added in the correct order but the first four elements were added in backwards into the list. Looking further into my code, I found that I had a bug relating to the placement of where elements were added into the merged list. Taking a closer look I found that in the first while loop, elements were always added to the front of the list rather than the back, so although the elements were added to the merged list in the correct order, the first four elements than ran within the while loop were being added in reverse order.
