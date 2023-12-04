# Lab Report 5: Putting it All Together

---
# Part 1 - Debugging Scenario
For this lab report I will introduce a debugging scenario between a student and a TA as it would appear on an app like EdStem.

## Post 1: Symptom
From Student:

Hello! I am having trouble figuring out what is wrong with my code! I am trying to fix my merge method within the ListExamples.java file but I don't know what's wrong. When I run the test cases, this is what I get. I'll show a picture of my test cases as well.

<img width="600" alt="image" src="https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/882ffa53-f143-4c5d-abe3-bbc59383917d">


<img width="597" alt="image" src="https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/a11305dc-2679-4235-b626-f57646143ef0">

I know the merge method is supposed to merge two sorted lists into one sorted list but it's not working properly. I see in the failed test case that the first element in the sorted array is a "c" when it should be an "a" so maybe it has something to do with indexing at either the front or end of one of the merging lists. My first test case passes showing that the lists do merge and have the correct size so it has something to do with the placement of the sorted elements into the new list. I'm going to try looking into more detail about the contents of the failing merge list, like what's in the rest of the array. Please let me know if there's anything specific I should try to find out what is wrong with my code.

## Post 2: TA Response

Hi! Looking at your screenshots and your code I can suggest a few things. The most general in any case is to manually process your code by hand. Run through your code using your inputs and write down what you get in your notes. Using that information, analyze the order in which elements are placed in the new list or any unusual actions that you may want to look into, like the addition of new elements or the loss of elements. How are your elements added into your merged list and where?

## Post 3: Student Testing/Response

I took some of the suggestions you made and applied them. The first thing I did was add a small loop towards the end of my method that would print the contents of the `result` list to the terminal when I ran the code. Here is what I got when running `test.sh`. 

<img width="198" alt="image" src="https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/eeb17d95-a658-4893-9ad2-cfecf0145e3c">

The string of letters at the bottom is the order in which they appear in the `result` list. Now that I had the order of the elements in the list I wanted to find out the order in which they got into the list and how the ended up in their specific locations. I manually ran through my test case using a pen and here are my results.

<img width="930" alt="image" src="https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/644b79ed-c105-42dc-a6db-b13873fe337d">

In this small drawing I labeled the elements in the list, which list the specific element came from, and the order in which they were added to the list. This is interesting because the elements were added in the correct order but the first four elements were added backwards into the list. Looking further into my code, I found that I had a bug relating to the placement of where elements were added into the merged list. Taking a closer look I found that in the first while loop, elements were always added to the front of the list rather than the back, so although the elements were added to the merged list in the correct order, the first four elements that ran within the while loop were being added in reverse order.

## The Set Up:

The file and directories prior to fixing or tampering with the code is within this directory: https://github.com/egoswami1/lab7.git
I changed both `ListExamples.java` and `ListExamplesTests.java`. All of the files were originally from a directory given to us in class.
Here is the code for those two files.

```ruby
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
  }


  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(0, list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(0, list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      index2 += 1;
    }
    return result;
  }


}
```
Note that the `filter` method was not used within this report.

```ruby
import static org.junit.Assert.*;
import org.junit.*;
import java.util.*;
import java.util.ArrayList;


public class ListExamplesTests {
	@Test(timeout = 500)
	public void testMerge1() {
    	List<String> l1 = new ArrayList<String>(Arrays.asList("a"));
		List<String> l2 = new ArrayList<String>(Arrays.asList("a", "a"));
		assertArrayEquals(new String[]{ "a", "a", "a",}, ListExamples.merge(l1, l2).toArray());
	}
	
	@Test(timeout = 500)
    	public void testMerge2() {
		List<String> l1 = new ArrayList<String>(Arrays.asList("a", "b", "c"));
		List<String> l2 = new ArrayList<String>(Arrays.asList("c", "d", "e"));
		assertArrayEquals(new String[]{ "a", "b", "c", "c", "d", "e" }, ListExamples.merge(l1, l2).toArray());
    	}
}
```

To trigger the bug I ran the test file using a bash script called test.sh. This was premade with the original directory. After `cd lab7/` to get into the correct working directory, the exact terminal line was `bash test.sh`.

To fix the bug you get rid of the zeros within the add to list commands. So, `result.add(0, list1.get(index1));` would turn into `result.add(list1.get(index1));` and `result.add(0, list2.get(index2));` would turn into `result.add(list2.get(index2));`. This makes it so elements added within the while loop will be added to the end of the merged list rather than the front.

# Part 2 - Reflection

The coolest thing I learned in the second half of the quarter was definitely vim. While it looks inconvenient if you have access to a text editor I still think it is pretty cool to be able to edit and update entire files using only the terminal. In the future I might even just use vim to edit files because it's kind of fun to do. I also found that being able to commit changed files directly from the terminal back to github is very useful. Saves a lot of unneeded transfering steps.
