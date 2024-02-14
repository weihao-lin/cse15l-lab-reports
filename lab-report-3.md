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

Command `grep`: finds lines in files containing certain patterns   
<br /> 
<br />

Option 1 `-i`   

<br />
Input:
`grep -i ring DraftRecom-PDF.txt`

Output:
<img width="479" alt="image" src="https://github.com/weihao-lin/cse15l-lab-reports/assets/156358635/3ab88deb-529c-4e87-aa5a-10a768cdedb7">

Input: 
`grep -i there Session2-PDF.txt`

Output:
<img width="481" alt="image" src="https://github.com/weihao-lin/cse15l-lab-reports/assets/156358635/ca8e780a-7dcf-4653-a12c-b1a41f758a12">

The `-i` option allows users to search for a pattern, regardless of the case of the pattern. 
This is useful because some patterns could be starting sentences and therefore in a different case than normal occurences, as seen in the second example above.
<br />
<br />

Option 2 `-r`

<br />
Input:
`grep -r "political party"`

Output: 
<img width="879" alt="image" src="https://github.com/weihao-lin/cse15l-lab-reports/assets/156358635/53038ed6-bf59-45e9-848b-54455b961650">

Input: 
`grep -r "climate change"`

Output:
<img width="929" alt="image" src="https://github.com/weihao-lin/cse15l-lab-reports/assets/156358635/64ed3b35-dd0f-42e5-bf85-df11b1596fb4">

The `-r` option allows users to search for a pattern in the current directory, as well as its subdirectories, recursively, until every subdirectory is searched.
This is useful because for lots of data, searching every directory can take a long time, and `-r` makes finding a needle in a haystack much easier.
<br />
<br />

Option 3 `-m`

<br />
Input:
`grep -r -m 1 "climate change"`

Output:
<img width="931" alt="image" src="https://github.com/weihao-lin/cse15l-lab-reports/assets/156358635/a19b2c82-2bc2-47b9-ba3f-1532757023d3">

Input:
`grep -m 10 "," Strategic_report.txt`

Output:
<img width="480" alt="image" src="https://github.com/weihao-lin/cse15l-lab-reports/assets/156358635/c97d61a9-31fa-41a2-b312-0e4bb7597188">

The `-m` option allows users to limit the number of lines `grep` prints that matches the pattern, per file.
This is useful for users who want a broad skim of the files, and lowers the number of files to look through.
<br />
<br />

Option 4 `-n`

<br />
Input:
`grep -n standard Progress_report.txt`

Output:
<img width="511" alt="image" src="https://github.com/weihao-lin/cse15l-lab-reports/assets/156358635/a95fe130-3ba4-4fd0-af3f-6f2bb37815b4">

Input:
`grep -n -i -m 5 "the" Strategic_report.txt`

Output:
<img width="500" alt="image" src="https://github.com/weihao-lin/cse15l-lab-reports/assets/156358635/66484991-2d98-4d3e-9362-aedc062c925d">

The `-n` option prints the line numbers in front in addition to the lines themselves.
This is useful for users who want a deeper search and having line numbers also makes finding a line much easier.

<br />
<br />
<br />

Command options from `man grep`






