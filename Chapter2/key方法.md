# 第2节：key方法

**keys()**方法返回一个包含数组中每个索引键的**Array Iterator**对象。

```
const array1 = ['a', 'b', 'c'];
const iterator = array1.keys();

for (const key of iterator) {
  console.log(key);
}

// expected output: 0
// expected output: 1
// expected output: 2

```



------

(1)作用：该方法获取一个数组迭代器对象，该对象包含数组中每一个索引的键;

(2)语法：arr.keys();

(3)语法解释：迭代器对象Iterator具有next()方法，可以用来依次调用它的值；

(4)返回值：返回原数组的迭代器对象，通过next()方法的value属性获取迭代器对象的值；



示例代码：

```
const arr=['tom','jery','jack','wilson'];
const res=arr.keys();
console.log(res.next().value);// 0
console.log(res.next().value);// 1
console.log(res.next().value);// 2
console.log(res.next().value);// 3
console.log(res.next().value);// undefined
```

