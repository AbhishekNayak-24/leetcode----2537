# leetcode----2537
Count the Number of Good Subarrays
//code in java
import java.util.HashMap;

public class Solution {
    public long countGood(int[] nums, int k) {
        long ans = 0;
        int pairs = 0;
        HashMap<Integer, Integer> count = new HashMap<>();
        
        for (int l = 0, r = 0; r < nums.length; ++r) {
            pairs += count.getOrDefault(nums[r], 0);
            count.put(nums[r], count.getOrDefault(nums[r], 0) + 1);
            
            while (pairs >= k) {
                pairs -= count.get(nums[l]) - 1;
                count.put(nums[l], count.get(nums[l]) - 1);
                l++;
            }
            
            ans += l;
        }
        
        return ans;
    }
}
