# holle-code
share and record my code in Leetcode question bank
//Leetcode #寻找数组的中心索引(java)
class Solution {
    public int pivotIndex(int[] nums) {
        int number1 = 0;//从左边加
        int number2 = 0;//从右边加
        int x = 0,m = -1,n = -1;
        int[] middleindex = new int[nums.length];
        for(int i = 0,j = nums.length-1,k = 1;k<nums.length;){
            if(m != i)number1 += nums[i];
            else if(n != j)number2 += nums[j];           
            if(number1>number2&&j>0){m = j;j--;i=i;}
            else if(number1<number2&&i<nums.length-1){n = i;i++;j=j;}    
            if((number1 == number2)&&(i+1) == (j-1)){//判断是否为中心
                middleindex[x] = i+1;
                x++;
            }
        }
        if(middleindex[0] == 0){//判断是否有中心索引
            return -1;
        }
        return middleindex[0];
    }
}
//初始版本，显示“超出时间限制”,思考的原因：if语句过多拖慢程序速度
//change code 
class Solution {
    public int pivotIndex(int[] nums) {        
        int sum = 0;
        for(int i = 0;i<nums.length;i++){
            sum += nums[i];
        }
        int number1 = 0;//从左边加
        int number2 = 0;//从右边加
        for(int i = 0;i<nums.length;i++){
            if(i == 0){
                number1 = 0;
                number2 = sum-nums[i];
            }
            else if(i<nums.length&&i>0){
                number1 += nums[i-1];
                number2 = sum-number1-nums[i];
            }        
            if(number1 == number2){
                return i;
            } 
        }
            return -1;
    }
}
