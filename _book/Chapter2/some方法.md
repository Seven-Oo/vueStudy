# 第4节：some方法

some() 方法用于检测数组中的元素是否满足指定条件（函数提供）。

some() 方法会依次执行数组的每个元素：

- 如果有一个元素满足条件，则表达式返回*true* , 剩余的元素不会再执行检测。
- 如果没有满足条件的元素，则返回false。

**注意：** some() 不会对空数组进行检测。

**注意：** some() 不会改变原始数组。

```
/**
 * @param {参数类型} 参数名 参数说明
 *  {
 *    function(currentValue, index,arr): //必须
 *    {
 *        currentValue: 必须。元素值,
 *        index: 可选。元素索引值,
 *        arr: 可选。当前数组对象
 *    },
 *    thisValue: 可选。对象作为该执行回调时使用，传递给函数，用作 "this" 的值。
 *  }
 */
array.some(function(currentValue,index,arr){},thisValue);
```



```
var arr = [ 1, 2, 3, 4, 5, 6 ]; 

var some = arr.some( function( val, index, arr){
    console.log( 'val：' + val); //打印1、2、3、4、5，不会打印6

    return val > 4; 
}); 

console.log(some); //返回true
```

