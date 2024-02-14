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

Option 1 `-i`   

Input:
`grep -i ring DraftRecom-PDF.txt`

Output:
```
steering committee to consider. During the conference, the steering
or omissions and offering general comments. He emphasized that the
from covering preventive services, it must draw a distinction
departments, underscoring the importance of research in that
considering grant applications.
intervention, and injuries are the most common events that bring
```
   
Input: 
`grep -i there Session2-PDF.txt`

Output:
```
help ensure that positive tests represent real problems. There is a
confidential since there may be legal, financial, or social
There are multiple barriers to screening. Nurses identified lack
the ED, there are even higher case rates in subgroups. Major
```

The `-i` option allows users to search for a pattern, regardless of the case of the pattern. 
This is useful because some patterns could be starting sentences and therefore in a different case than normal occurences, as seen in the second example above.

Option 2 `-r`

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

Option 3 `-m`

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

Option 4 `-n`

Input:









