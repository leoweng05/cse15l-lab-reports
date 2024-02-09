# Lab Report 3 - Bugs and Commands (Week 5)

## Part 1 - Bugs

Failure Inducing Input:
``	
@Test 
	public void testReverseInPlace() {
    int[] input2 = {1, 2, 3};
    ArrayExamples.reverseInPlace(input2);
    assertArrayEquals(new int[]{3, 2, 1}, input2);
	} 
 ``

 Input that doesn't induce failure: 
 ``
 	@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}
 ``

Symptoms:
* For Failure Inducing Input: ![image](https://github.com/leoweng05/cse15l-lab-reports/assets/62259208/07387763-c19c-4cd1-a850-a01ea9122964)
* For Input that doesn't induce failure: ![image](https://github.com/leoweng05/cse15l-lab-reports/assets/62259208/f58603ae-3717-4f26-83c7-89321dfec4be)

Bug:
* Before:
```
// Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
  ``
* After:
```
```
// Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    int[] tempArr = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      tempArr[i] = arr[arr.length - i - 1];
    }
    for (int i 0; i < arr.length; i++){
      arr[i] = tempArr[i];
    }
  }
  ```
  The reason why there was a bug was that the array was overwriting its values at the same time it was reading through them. This logic flaw only reverses the first half of the array, leaving the second half as it already is (because the first half was switched to be the mirror of the original second half, so mirroring that again would just leave the original second half). The fix accounts for this by reading through the array values but storing them in a temporary array, so the danger of overriding values would not occur. Then, it copies over the reversed values from the temp array to the original array, correctly leaving a fully reversed array. 
