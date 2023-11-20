# Lab Report 2: Servers and SSH Keys

---
## Part 1 - Bugs

The following is a failing test for the `merge` method within `ListExamples.java`:

```ruby
@Test(timeout = 500)
public void testMerge1() {
  List<String> list1 = new ArrayList<String>(Arrays.asList("hello", "world", "yoyo"));
  List<String> list2 = new ArrayList<String>(Arrays.asList("code", "goodbye", "zebra"));
  assertArrayEquals(new String[]{ "code", "goodbye", "hello", "world", "yoyo", "zebra"}, ListExamples.merge(list1, list2).toArray());
}
```

The following is a passing test for the `merge` method within `ListExamples.java`:

```ruby
@Test(timeout = 500)
public void testMerge2() {
  List<String> list1 = new ArrayList<String>(Arrays.asList("hello", "world", "yoyo"));
  List<String> list2 = new ArrayList<String>(Arrays.asList("code", "goodbye"));
  assertArrayEquals(new String[]{ "code", "goodbye", "hello", "world", "yoyo"}, ListExamples.merge(list1, list2).toArray());
}
```

The following is the output of running the bash script `test.sh` which runs junit tests on the previous two tests. Here is the terminal ouput:
```
JUnit version 4.13.2
.E.
Time: 0.302
There was 1 failure:
1) testMerge1(ListExamplesTests)
java.lang.OutOfMemoryError: Java heap space
        at java.util.Arrays.copyOf(Unknown Source)
        at java.util.Arrays.copyOf(Unknown Source)
        at java.util.ArrayList.grow(Unknown Source)
        at java.util.ArrayList.ensureExplicitCapacity(Unknown Source)
        at java.util.ArrayList.ensureCapacityInternal(Unknown Source)
        at java.util.ArrayList.add(Unknown Source)
        at ListExamples.merge(ListExamples.java:42)
        at ListExamplesTests.testMerge1(ListExamplesTests.java:14)

FAILURES!!!
Tests run: 2,  Failures: 1
```
The following shows the buggy `merge` method:
```ruby
static List<String> merge(List<String> list1, List<String> list2) {
  List<String> result = new ArrayList<>();
  int index1 = 0, index2 = 0;
  while(index1 < list1.size() && index2 < list2.size()) {
    if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    else {
      result.add(list2.get(index2));
      index2 += 1;
    }
  }
  while(index1 < list1.size()) {
    result.add(list1.get(index1));
    index1 += 1;
  }
  while(index2 < list2.size()) {
    result.add(list2.get(index2));
    index1 += 1;
  }
  return result;
}
```
The following shows the fixed `merge` method:
```ruby
static List<String> merge(List<String> list1, List<String> list2) {
  List<String> result = new ArrayList<>();
  int index1 = 0, index2 = 0;
  while(index1 < list1.size() && index2 < list2.size()) {
    if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    else {
      result.add(list2.get(index2));
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
```
In the scenario that all of the words in `list1` were already sorted the code is meant to iterate through `list2` and add the remaining words to the end of the new merged list. However, instead of increasing the variable `index2` the code was increasing `index1`. This caused the last while loop to be infinite if `list2` had the highest words on the list alphabetically. The fix was to change the `index1 += 1;` to `index2 += 1;`.

---
#Part 2 - Researching Commands

The following will show different applications of the `find` command.

First `find -name`
```
$ find -name "*Aid.txt"
./government/Media/Coup_Reshapes_Legal_Aid.txt
./government/Media/Marylands_Legal_Aid.txt
./government/Media/Poor_Lacking_Legal_Aid.txt
./government/Media/Providing_Legal_Aid.txt
```
In this example, the find command found every file within `/technical` that had a name that ended with "Aid.txt". The asterisk specifies that the file name before "Aid.txt" does not matter.
Here is another example:
```
$ find -name "*2028*"
./plos/pmed.0020281.txt
```
In this example we searched for a file wtih a name that conatined 2028 anywhere within the name. There was only 1 result in the entire directory. The `-name` option is useful because it allows a user to quickly find if a file exists or files with similar names.

Second application: `find -type`
```
$ find . -type d
.
./911report
./biomed
./government
./government/About_LSC
./government/Alcohol_Problems
./government/Env_Prot_Agen
./government/Gen_Account_Office
./government/Media
./government/Post_Rate_Comm
./plos
```
In this example, the `-type` option searches for only a specific type of response. In this case, we signified we wanted type "d" which refers to "directories". The terminal then printed all the directories found within `technical` including the working directory itself.
```
$ find government/Alcohol_Problems/ -type f
government/Alcohol_Problems/DraftRecom-PDF.txt
government/Alcohol_Problems/Session2-PDF.txt
government/Alcohol_Problems/Session3-PDF.txt
government/Alcohol_Problems/Session4-PDF.txt
```
Here we seached for all "files", signified by "f", within the specified directory and it returned the four files within the directory. This command is useful because it allows us to filter the type of response we want the terminal to respond with. If we only wanted to specifically look at all the directories or only all of the files this command filters out everything else for us and prints out exactly what we want to see.

Third application: `find -
```
$ find -mmin 1
./government/Alcohol_Problems/Session3-PDF.txt
```
In this example, I made a small edit to 1 of the files within the working directory. The `-mmin` commands expresses all files that were changed within a certain time frame. In this case within the past minute.
```
$ find -mmin 1

```
Yes this is the same exact input as last code but in the time it took me to explain the last code block, the edit to that file was no longer within a minute so nothing appears. This option is useful because it allows you to find edited files. For example lets say I edit a file and accidentily close out of it but I forget the file name. This option will allow me to find that file.
```
$ find -empty
./government/About_LSC/empty.txt
```
This option finds all the empty files within a directory and prints them. In this case I made a file called `empty.txt` which was then printed back as it is the only empty file in the entire directory.



