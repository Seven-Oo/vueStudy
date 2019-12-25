# 第3节：includes方法

includes() 方法用来判断一个数组是否包含一个指定的值，如果是返回 true，否则false。



```
[1, 2, 3].includes(2);     // true
[1, 2, 3].includes(4);     // false
[1, 2, 3].includes(3, 3);  // false
[1, 2, 3].includes(3, -1); // true
[1, 2, NaN].includes(NaN); // true
```



------



```
arr.includes(searchElement)
arr.includes(searchElement, fromIndex)
```

searchElement： 必须。需要查找的元素值。

fromIndex： 可选。从该索引处开始查找 searchElement。如果为负值，则按升序从 array.length + fromIndex 的索引开始搜索。默认为 0。



