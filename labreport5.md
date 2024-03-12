# __Lab Report 5__

# Part 1

1. 
![image](https://github.com/theryanfo/cse15l-lab-reports/assets/156359755/01830763-6177-4cee-8421-372e44f09bc6)

I'm not sure why this test isn't passing, here is my code. The first number of the array matched but JUnit says the second number was 1, so it's like my code isn't traversing the array or something.

```
public class ArrayExamples {
  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
2.
Why don't you try drawing out each step on a piece of paper to see where the program doesn't behave as expected?

3.
![image](https://github.com/theryanfo/cse15l-lab-reports/assets/156359755/f609cfc2-4390-4b37-b290-f2958a2a4acc)

It seems like the array can't accurately copy the first half to the second half because it has already been overwritten, so I probably have to create a temporary array to fix this issue.

4.
**File and directory stucture**
  
- ArrayMethods/
  - ArrayExamples.java
  - ArrayTests.java
  - test.sh


***Before***

**ArrayExamples.java**
```
public class ArrayExamples {
  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
}
```

**ArrayTests.java**
```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
	@Test 
	public void testReverseInPlace1() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}

  @Test 
	public void testReverseInPlace2() {
    int[] input2 = {0, 1};
    ArrayExamples.reverseInPlace(input2);
    assertArrayEquals(new int[]{1, 0}, input2);
	}
}
```

**bash test.sh**
```
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore ArrayTests
```

**Bug-triggering command**

`bash test.sh`

**How the bug was fixed**

Create a temporary copy of the original array to traverse, so that it is unaffected by new assignments to the returned array
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
}
```

# Part 2

I learned about debugging using jdb. It's helpful for when I want to see the values of the variables in the middle of a program before certain commands execute in order to identify when problems occur.
