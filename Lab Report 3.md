# **CSE 15L Lab Report 2** 

# **Part 1 - Bugs** <br>
I will be writing about the bug in the ```reversed``` method within ```ArrayExamples``` <br>
![Image](failInput.jpg) <br>

```
// Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }

```

```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {

  /* 
	@Test 
	public void testReverseInPlace() {
    int[] input1 = { 1, 2, 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}
*/

  @Test
  public void testReversed() {
    int[] input1 = { 1, 2, 3  };
    assertArrayEquals(new int[]{3,2,1 }, ArrayExamples.reversed(input1));
  }
}
```
<br>
My failure-inducing input was the array {1,2,3} into the JUnit test which expected {3,2,1}, but did not get the expected value from the test.



# **Part 2 - Researching Commands** <br>
