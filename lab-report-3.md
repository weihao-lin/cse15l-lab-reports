# Part 1: Bugs


Failure inducing input:
```
@Test 
public void testReverseInPlace() {
  int[] input1 = { 3,4,5 };
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{ 5,4,3 }, input1);
}
```
Not failure inducing input:
```
@Test
public void testReverseInPlace2() {
  int[] input1 = { 3 };
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{ 3 }, input1);
}
```
Symptom of tests:

<img width="772" alt="image" src="https://github.com/weihao-lin/cse15l-lab-reports/assets/156358635/8a5ac8b6-de67-4087-bb28-99fdfb10c2aa">

Before fix:
```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - i - 1];
  }
}
```
After fix:
```
static void reverseInPlace(int[] arr) {
  for (int i = 0; i < arr.length / 2; i++) {
    int temp = arr[i];
    arr[i] = arr[arr.length - i - 1];
    arr[arr.length - i - 1] = temp;
  }
}
```
The code before sets the elements past the middle of the array to the new elements already set at the beginning, instead of the original elements. 
The fix pairs each element from the beginning and end together, until the pairs reach the middle, which ensures that the swapped pairs don't happen past the middle.

# Part 2: Researching Commands 

Command `grep`: 

Option 1 `-i`: ignore case when searching 




