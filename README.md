# 4-sum-problem
Given an array nums of n integers, return an array of all the unique quadruplets [nums[a], nums[b], nums[c], nums[d]] such that:  0 &lt;= a, b, c, d &lt; n a, b, c, and d are distinct. nums[a] + nums[b] + nums[c] + nums[d] == target You may return the answer in any order.     
//this code having time complexity O(n3) which is acceptable 

class Solution {
    public List<List<Integer>> fourSum(int[] nums, int target) {
       List<List<Integer>> res = new ArrayList<>();
       Arrays.sort(nums);
       HashSet<String>unique=new HashSet<>();
       for(int i=0;i<nums.length-3;i++){
        for(int j=i+1;j<nums.length-2;j++){
            int li=j+1;
            int ri=nums.length-1;
            while(li<ri){
                long sum=nums[i];
                sum+=nums[j];
                sum+=nums[li];
                sum+=nums[ri];
                if (sum<target){
                    li++;
                }else if(sum>target){
                    ri--;
                }else{
                    StringBuilder sb=new StringBuilder();
                    sb.append(nums[i]);
                    sb.append(nums[j]);
                    sb.append(nums[li]);
                    sb.append(nums[ri]);
                    String code=sb.toString();
                    if (unique.contains(code)==false){
                        unique.add(code);
                        res.add(Arrays.asList(nums[i],nums[j],nums[li],nums[ri]));
                    }
                    li++;
                    ri--;
                }
            }
        }
       }
       return res;
    }   
}
