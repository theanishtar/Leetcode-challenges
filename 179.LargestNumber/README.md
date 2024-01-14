## 179. Largest Number
`Solved` `Medium` `Topics` `Companies`


Given a list of non-negative integers nums, arrange them such that they form the largest number and return it.

Since the result may be very large, so you need to return a string instead of an integer.

 

### Example 1:

> Input: nums = [10,2]
> Output: "210"

### Example 2:

> Input: nums = [3,30,34,5,9]
> Output: "9534330"
 

### Constraints:

`1 <= nums.length <= 100`
`0 <= nums[i] <= 109`


## My codes

```java
import java.math.BigInteger;

class Solution {
    public String largestNumber(int[] nums) {
        String result = "";
        for (int i=0; i<nums.length-1; i++){
            for (int j=i+1; j<nums.length; j++){
                if (nums[i] != getMax(nums[i],nums[j])){
                    int temp = nums[i];
                    nums[i] = nums[j];
                    nums[j] = temp;
                }
            }
        }
        for (int i=0; i<nums.length; i++){
            result += String.valueOf(nums[i]);
        }
        BigInteger resultInt = new BigInteger(result);
        return resultInt.toString();
    }

    public static int getMax(int num1, int num2){
        String numS1 = String.valueOf(num1);
        String numS2 = String.valueOf(num2);
        BigInteger nF1 = new BigInteger(numS1 + numS2);
        BigInteger nF2 = new BigInteger(numS2 + numS1);
        int result = nF1.compareTo(nF2);

        if (numS1.length() == numS2.length())
            return num1 > num2 ? num1 : num2;
        return result > 0 ? num1 : num2;
    }
}
```