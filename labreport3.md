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
