#  数组中重复的数字
题目要求：给定一个n长数组，数组中数字大小均在0～n-1区间内，数组中必有重复数字，找出并返回
## 初解
解题思路：使用Map来解，遍历数组，将遇到的数字先判断map中是否存在，如果不存在则存入map中，如果存在则直接返回结果
``` javascript
function findRepeatNumber(nums){
  var map = new Map();
  for(let i = 0 ; i < nums.length;i++){
    if(map.has(nums[i])){
      return nums[i];
    }else{
      map.set(nums[i]);
    }
  }
}
```
## 二解
使用Map类型的方式相当于是借助了map的特性，进行了判定，还有种思路，可以自己和自己判断，那么就是自身Hash的体现
解题思路：首先还是先遍历数组，判断值和索引是否相同，如果不同那么还要进一步判断，与值相同索引下的值是否和现在的值相同，如果也不同那么就将值放如对应索引的位置上（这里做个交换），若值和索引的值相同，那么就判断下一个值，如果值和相同索引下的值是一样的，那么就是出现了重复值，进行返回。
换句话说也就是将值放在与值相同的索引下，如果判断在同一索引下有两个值的出现，那么这个值就是重复的
``` javascript
function findRepeatNumber(nums){
  for(let i = 0 ;i < nums.length;i++){
    if(i!=nums[i]&&nums[nums[i]]!=nums[i]){
      var temp = nums[nums[i]];
      nums[nums[i]] = nums[i];
      nums[i] = temp;
    }
    if(i!=nums[i]&&nums[nums[i]]==nums[i]){
      return nums[i];
    }
  }
}
```
## 三解
在查看题解的过程中，发现有大佬提出用Set，因为Set会自动过滤掉重复的



