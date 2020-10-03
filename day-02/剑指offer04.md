# 二维数组中的查找
题目要求：给一个n*m的二维数组，以及一个目标值target，在二维数组中找出target值，如果没有返回false，反之返回true
## 初解
嵌套遍历二维数组，比较target与数组中的值，如果一样则直接返回true，如果嵌套函数结束还没有返回，则返回false
``` javascript
function findNumberIn2DArray(matrix,target){
  for(let i = 0 ; i < matrix.length; i++){
    for(let j = 0; j < matrix[i].length;j++){
      if(target==matrix[i][j]){
        return true;
      }
    }
  }
  return false;
}
```
## 二解
在初解中，并没有充分发挥出js的魅力，在二解中使用js数组中的.falt()以及.includes()方法，简化函数
``` javascript
function findNumberIn2DArray(matrix,target){
  return matrix.flat(infinity).includes(target);
}
```
## 知识点补充
### Array.prototype.flat()
> 深度遍历一个多维数组，将遍历到的值返回到一个一维数组中，换句话说也就是降维
> 例如：[1,2,3,[4,5]]=>.flat()=>[1,2,3,4,5]
可以传入一个参数，表示深度，默认是1
如果不太清楚数组的深度，那么可以传入Infinity，形如.flat(infinity)
### Array.prototype.includes()
> 用于查找数组中是否含有某个值，有则返回true，无则返回false
允许传入一个参数，作为target目标值
