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

The following will show different applications of the `grep` command.



