# 第1节：reduce方法

reduce()方法接收一个函数作为累加器，数组中的每个值（从左到右）开始缩减，最终计算为一个值。



array.reduce(function(total, currentValue, currentIndex, arr), initialValue)

total： 必须。上一次调用回调返回的值，或者是提供的初始值（initialValue）

currentValue： 必须。当前元素

currentIndex： 可选。当前元素的索引

arr： 可选。当前元素所属的数组对象

initialValue： 可选。传递给函数的初始值 / 作为第一次调用 callback 的第一个参数



```
var arr = [1, 2, 3, 4];
var sum = arr.reduce(function(prev, cur, index, arr){
	console.log(prev, cur, index);
	return prev + cur;
})
console.log(arr, sum);
```

```
打印结果：
1 2 1 
3 3 2 
6 4 3

[1, 2, 3, 4] 10
```

上面的例子的index是从1开始的，第一次的prev的值是数组的第一个值，数组的长度是4，但是reduce函数却只循环3才。这是因为没有传入初始值（initialValue）导致的。

再看一个例子：

```
var arr = [1, 2, 3, 4];
var sum = arr.reduce(function(prev, cur, index, arr){
	console.log(prev, cur, index);
	return prev + cur;
}， 0) //这里设置了初始值
console.log(arr, sum);
```

```
打印结果：
0 1 0
1 2 1 
3 3 2 
6 4 3

[1, 2, 3, 4] 10
```



> **PS：****如果没有提供initiaValue，reduce会从索引为1的地方开始执行callback方法，跳过第一个索引。如果提供了initiaValue，则从索引为0的地方开始。**



**为了不报错，还是提供初始值会更安全，因为原始数组为空并没有初始值时，reduce方法会报错**



#### 简单用法：

求和、求乘积

```
var arr = [1, 2, 3, 4];
var sum = arr.reduce((x, y) => x + y)
var mul = arr.reduce((x, y) => x * y)
console.log( sum ); // 10
console.log ( mul ); // 24
```



#### 高级用法：

1.计算数组中每个元素的出现次数

```
let names = ['Alice', 'Bob', 'Tiff', 'Bruce', 'Alice'];

let nameNum = names.reduce((pre,cur)=>{
  if(cur in pre){
    pre[cur]++
  }else{
    pre[cur] = 1 
  }
  return pre
},{})
console.log(nameNum); //{Alice: 2, Bob: 1, Tiff: 1, Bruce: 1}
```

2.数组去重

```
let arr = [1,2,3,4,4,1]
let newArr = arr.reduce((pre,cur)=>{
    if(!pre.includes(cur)){
      return pre.concat(cur)
    }else{
      return pre
    }
},[])
console.log(newArr);// [1, 2, 3, 4]
```

3.将二维数组转化为一维

```
let arr = [[0, 1], [2, 3], [4, 5]]
let newArr = arr.reduce((pre,cur)=>{
    return pre.concat(cur)
},[])
console.log(newArr); // [0, 1, 2, 3, 4, 5]
```

4.将多维数组转化为一维

```
let arr = [[0, 1], [2, 3], [4,[5,6,7]]]
const newArr = function(arr){
   return arr.reduce((pre,cur)=>pre.concat(Array.isArray(cur)?newArr(cur):cur),[])
}
console.log(newArr(arr)); //[0, 1, 2, 3, 4, 5, 6, 7]
```

5.对象里的属性求和

```
var result = [
    {
        subject: 'math',
        score: 10
    },
    {
        subject: 'chinese',
        score: 20
    },
    {
        subject: 'english',
        score: 30
    }
];

var sum = result.reduce(function(prev, cur) {
    return cur.score + prev;
}, 0);
console.log(sum) //60
```

