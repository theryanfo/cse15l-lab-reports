# __Lab Report 3__

# Part 1
## Example Bug
```
public class ArrayExamples {

  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
## Failure-Inducing Input
```
@Test
public void testReverseInPlace2() {
    int[] input1 = {0, 1};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{1, 0}, input1);
}
```
## Passing Input
```
@Test 
public void testReverseInPlace1() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
}
```
## The Symptom

![image](https://github.com/theryanfo/cse15l-lab-reports/assets/156359755/c3a53580-d70a-46cb-86e2-2dfd6ae27ee5)

## The Bug - Before
```
public class ArrayExamples {

  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
## The Bug - After (Fixed)
```
public class ArrayExamples {

  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    int[] temp = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      temp[arr.length - i - 1] = arr[i];
    }
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = temp[i];
    }
  }
```
In the original version, the bug is caused when we assign `arr[i] = arr[arr.length - i - 1]` for any array size 2 or greater, because the second half of arr is assigned values from itself which have already been overwritten. In the fixed version, we fix this problem by creating a new empty array 'temp' to assign arr's values to in reverse order. Then, we reassign arr's values to temp's values.

***
# Part 2
## The 'grep' Command
Source: https://man7.org/linux/man-pages/man1/grep.1.html

**grep -o** prints only the matching part of a matching line, each on a separate line.
```
//input
grep -r -o "base pair" | less

//output
technical/biomed/1471-2105-3-18.txt:base pair
technical/biomed/1471-2105-3-18.txt:base pair
technical/biomed/1471-2105-3-2.txt:base pair
technical/biomed/1471-2105-3-2.txt:base pairq
```
```
//input
grep -o "base pair" technical/plos/*.txt

//output
technical/plos/journal.pbio.0020190.txt:base pair
technical/plos/journal.pbio.0020190.txt:base pair
technical/plos/journal.pbio.0020223.txt:base pair
```
**grep -c** prints the number of matching lines for each input file.
```
// input
grep -c "base pair" technical/biomed/*.txt | less

//output
technical/biomed/rr191.txt:0
technical/biomed/rr196.txt:1
technical/biomed/rr37.txt:0
technical/biomed/rr73.txt:0
technical/biomed/rr74.txt:0
```
```
//input
grep -c "base pair" technical/biomed/1471-2199-3-17.txt

//output
4
```

**grep -v** inverts the matching to select only non-matching lines.
```
//input
find technical | grep -v ".txt"

//output
technical
technical/911report
technical/biomed
technical/government
technical/government/About_LSC
technical/government/Alcohol_Problems
technical/government/Env_Prot_Agen
technical/government/Gen_Account_Office
technical/government/Media
technical/government/Post_Rate_Comm
technical/plos
```
```
//input
find technical/911report/ | grep -v "chapter"

//output
technical/911report/
technical/911report/preface.txt
```
**grep -i** makes grep ignore case distinctions in patterns.
```
//input
grep -o -i "tuesday" technical/911report/*.txt

//output
technical/911report/chapter-1.txt:Tuesday
technical/911report/chapter-1.txt:Tuesday
technical/911report/chapter-1.txt:Tuesday
technical/911report/chapter-13.2.txt:Tuesday
technical/911report/chapter-13.2.txt:Tuesday
technical/911report/chapter-13.4.txt:Tuesday
```
```
//input
grep -o -i "HOW" technical/government/*/*.txt | less

//output
technical/government/About_LSC/conference_highlights.txt:how
technical/government/About_LSC/conference_highlights.txt:how
technical/government/About_LSC/CONFIG_STANDARDS.txt:How
technical/government/About_LSC/diversity_priorities.txt:How
technical/government/About_LSC/diversity_priorities.txt:How
```
