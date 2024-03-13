# Debugging Scenario 

1. Student: Why is the expected value 3 at `expected[0]`? It shouldn't be possible for the first index to be greater than the second with this implementation. <br/>
```
public int[] twoSum() {
        int[] indices = {0,0};
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] + nums[j] == target) {
                    indices[0] = i;
                    indices[1] = j;
                    break;
                }
            }
        }
        return indices;
}
```
```
@Test
public void testTwoSum9() {
        submission x;
        int[] nums = {3,5,6,1,6,8};
        int target = 9;
        x = new submission(nums, target);

        int[] expected = new int[]{0,2};
        int[] actual = x.twoSum();
        assertArrayEquals(expected, actual);
}
```
<img width="759" alt="image" src="https://github.com/weihao-lin/cse15l-lab-reports/assets/156358635/7334f492-0fa3-4a17-b962-76eb5ad656ad">

2. TA: Try adding a print statement at critical points in your for loops to keep track of which values are in `expected`. 
You can then see at which iteration the value becomes 3 and fix your code from there. <br/>

3. Student: using suggestion <br/>
```
public int[] twoSum() {
        int[] indices = {0,0};
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] + nums[j] == target) {
                    indices[0] = i;
                    indices[1] = j;
                    break;
                }
                System.out.println(indices[0]);
            }
        }
        return indices;
    }
```
<img width="748" alt="image" src="https://github.com/weihao-lin/cse15l-lab-reports/assets/156358635/d49ea5a3-449c-40ab-bac0-a7401dc33f6b">

The bug is located on line 16. Specifically, `break;` causes the above symptom because the for loops continue iterating through the list even after it finds the match.
The print statement showed that the outer for loop ran more than once, even though it should've stopped during the first loop upon matching 3 and 6 in `nums`.

```
public class submission {
    int[] nums;
    int target;
    public submission(int[] nums, int target) {
        this.nums = nums;
        this.target = target;
    }

    public int[] twoSum() {
        int[] indices = {0,0};
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] + nums[j] == target) {
                    indices[0] = i;
                    indices[1] = j;
                    break;
                }
                System.out.println(indices[0]);
            }
        }
        return indices;
    }
}
```
4. <br/>
```
lab5/
|-  starter/
    |-  PublicTester.class
  	|-  PublicTester.java
  	|-  submission.class
  	|-  submission.java
  	|-  test.sh
|-  libs/
  	|-  hamcrest-2.2.jar
  	|-  junit-4.13.2.jar
```
PublicTester.java: <br/>
```
import org.junit.Test;

import static org.junit.Assert.*;

public class PublicTester {
    @Test
    public void testTwoSum7() {
        submission x;
        int[] nums = {3,5,3,5,6,1};
        int target = 7;
        x = new submission(nums, target);

        int[] expected = new int[]{4,5};
        int[] actual = x.twoSum();
        assertArrayEquals(expected, actual);
    }
    @Test
    public void testTwoSum9() {
        submission x;
        int[] nums = {3,5,6,1,6,8};
        int target = 9;
        x = new submission(nums, target);

        int[] expected = new int[]{0,2};
        int[] actual = x.twoSum();
        assertArrayEquals(expected, actual);
    }
}
```
submission.java: <br/>
```
public class submission {
    int[] nums;
    int target;
    public submission(int[] nums, int target) {
        this.nums = nums;
        this.target = target;
    }

    public int[] twoSum() {
        int[] indices = {0,0};
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] + nums[j] == target) {
                    indices[0] = i;
                    indices[1] = j;
                    break;
                }
            }
        }
        return indices;
    }
}
```
test.sh: <br/>
```
javac -cp ../libs/junit-4.13.2.jar:../libs/hamcrest-2.2.jar:. PublicTester.java   
java -cp ../libs/junit-4.13.2.jar:../libs/hamcrest-2.2.jar:. org.junit.runner.JUnitCore PublicTester
```
Command lines: `bash test.sh` only <br/>
Edit to fix bug: replace `break;` with `return indices;` on line 16.

# Reflection








