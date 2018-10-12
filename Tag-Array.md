# Majority Element
[link](https://leetcode.com/problems/majority-element/description/)

Solution1:
```
class Solution {
    public int majorityElement(int[] nums) {
        Arrays.sort(nums);
        return nums[nums.length / 2];
    }
}
```
Solution2:
```
class Solution {
    public int majorityElement(int[] nums) {
        HashMap<Integer, Integer> myMap = new HashMap<Integer, Integer>();
        //Hashtable<Integer, Integer> myMap = new Hashtable<Integer, Integer>();
        int ret = 0;
        for(int num : nums){
            if(!myMap.containsKey(num)){
                myMap.put(num,1);
            }else{
                myMap.put(num,myMap.get(num)+1);
            }
            if(myMap.get(num) > nums.length/2){
                ret = num;
                break;
            }
        }
        return ret;
    }
}
```

# Valid Parentheses
```
class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<Character>();
        for(Character c : s.toCharArray()){
            if(c == '(')
                stack.push(')');
            else if(c == '[')
                stack.push(']');
            else if(c == '{')
                stack.push('}');
            else if(stack.isEmpty() || stack.peek() != c)
                return false;
            else
                stack.pop();
        }
        return stack.isEmpty();
    }
}
```

# Plus One 

[link](https://leetcode.com/problems/plus-one/description/)

 ```
 class Solution {
    public int[] plusOne(int[] digits) {
        int n = digits.length;
        for(int i=n-1;i>=0;i--){
            if(digits[i] < 9) {
                digits[i]++;
                return digits;
            }

            digits[i] = 0;
        }
        int[] newNumber = new int[n+1];
        newNumber[0] = 1;
        return newNumber;
    }
}
 ```
 
 # Pascal's Triangle
 [link](https://leetcode.com/problems/pascals-triangle/description/)
 ```
 class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> triangle = new ArrayList<List<Integer>>();
        if(numRows == 0)
            return triangle;
        triangle.add(new ArrayList<>());
        triangle.get(0).add(1);
        
        for(int i = 1; i < numRows; i++){
            List<Integer> preRow = triangle.get(i-1);
            List<Integer> row = new ArrayList<Integer>();
            row.add(1);
            for(int j = 1;j<i;j++){
                int num = preRow.get(j-1)+preRow.get(j);
                row.add(num);
            }
            row.add(1);
            triangle.add(row);
        }
        return triangle;
    }
}
 ```
