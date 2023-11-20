# Lab Report 2: Servers and SSH Keys

---
## Part 1 - Bugs

The following is a failing test for the `merge` method within `ListExamples.java`:

```ruby
@Test(timeout = 500)
public void testMerge1() {
  List<String> list1 = new ArrayList<String>(Arrays.asList("hello", "world", "!"));
  List<String> list2 = new ArrayList<String>(Arrays.asList("code", "loser"));
  assertArrayEquals(new String[]{ "code", "goodbye", "hello", "world", "!"}, ListExamples.merge(list1, list2).toArray());
}
```

The following is a passing test for the `merge` method within `ListExamples.java`:

```ruby
@Test(timeout = 500)
public void testMerge2() {
  List<String> list1 = new ArrayList<String>(Arrays.asList("hello", "world", "!"));
  List<String> list2 = new ArrayList<String>(Arrays.asList("code", "goodbye"));
  assertArrayEquals(new String[]{ "code", "goodbye", "hello", "world", "!"}, ListExamples.merge(list1, list2).toArray());
}
```

The following is the output of running the bash script `test.sh` which runs junit tests on the previous two tests. Here is the terminal ouput:
```
JUnit version 4.13.2
.E.
Time: 0.006
There was 1 failure:
1) testMerge1(ListExamplesTests)
arrays first differed at element [1]; expected:<[goodbye]> but was:<[hello]>
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
        at org.junit.Assert.internalArrayEquals(Assert.java:534)
        at org.junit.Assert.assertArrayEquals(Assert.java:285)
        at org.junit.Assert.assertArrayEquals(Assert.java:300)
        at ListExamplesTests.testMerge1(ListExamplesTests.java:12)
        ... 11 trimmed
Caused by: org.junit.ComparisonFailure: expected:<[goodbye]> but was:<[hello]>
        at org.junit.Assert.assertEquals(Assert.java:117)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
        ... 17 more

FAILURES!!!
Tests run: 2,  Failures: 1
```

