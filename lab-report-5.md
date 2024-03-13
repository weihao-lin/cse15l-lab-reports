# Debugging Scenario 

Student: Why is the expected value 3 at `expected[0]`? It shouldn't be possible for the first index to be greater than the second with this implementation. <br/>
<img width="402" alt="image" src="https://github.com/weihao-lin/cse15l-lab-reports/assets/156358635/f49d28b3-6ec3-4b7b-a5ab-961c18620297">
<img width="311" alt="image" src="https://github.com/weihao-lin/cse15l-lab-reports/assets/156358635/f21f4019-70fd-442b-80d8-43ecfef906f0">
<img width="759" alt="image" src="https://github.com/weihao-lin/cse15l-lab-reports/assets/156358635/7334f492-0fa3-4a17-b962-76eb5ad656ad">

TA: Try adding a print statement at critical points in your for loops to keep track of which values are in `expected`. 
You can then see at which iteration the value becomes 3 and fix your code from there. <br/>

Student: using suggestion <br/>
<img width="748" alt="image" src="https://github.com/weihao-lin/cse15l-lab-reports/assets/156358635/d49ea5a3-449c-40ab-bac0-a7401dc33f6b">

The bug is located on line 16. Specifically, `break;`
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
