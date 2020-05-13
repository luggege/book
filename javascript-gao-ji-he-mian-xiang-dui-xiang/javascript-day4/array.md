# Array

## Array对象属性

| 属性 | 描述 |
| :--- | :--- |
| length | 设置或返回数组中元素的数目。 |

## Array对象方法

| 方法 | 描述 |
| :--- | :--- |
| concat\(\) | 连接两个或更多的数组，并返回结果。 |
| join\(\) | 把数组的所有元素放入一个字符串。元素通过指定的分隔符进行分隔。 |
| pop\(\) | 删除并返回数组的最后一个元素 |
| push\(\) | 向数组的末尾添加一个或更多元素，并返回新的长度。 |
| reverse\(\) | 颠倒数组中元素的顺序。 |
| shift\(\) | 删除并返回数组的第一个元素 |
| slice\(索引, 索引\) | 从某个已有的数组返回选定的元素 |
| sort\(\) | 对数组的元素进行排序 |
| splice\(索引, 个数, 替换内容\) | 删除元素，并向数组添加新元素。 |
| unshift\(\) | 向数组的开头添加一个或更多元素，并返回新的长度。 |

#### 真数组

> new Array\(\)定义的 或者是 字面量出来的 \[\]

#### 稀疏数组

> \[1, ,2\]

#### 非稀疏数组

> 不缺失任何值

#### 伪数组

> 1. 伪数组是个**对象**
> 2. 有**length**属性 ，且为number类型
> 3. 有**length-1为下标**的属性（其余下标不指定默认为undefined）或length=0

**伪数组转为标准数组的方法**

1. ES6的Array.from方法
2. Array.prototype.slice.call\(\)
3. \[\].slice.call\(\)

```js
1. Array.from({1: "a", length: 2})                    // [undefined, "a"]

2. Array.prototype.slice.apply({1: "a", length: 2})   // [empty, "a"]

3. [].slice.call({1: "a", length: 2})                 // [empty, "a"]

[].slice.call({1: "a", length: 2})[0] === Array.from({1: "a", length: 2})[0]      // true
```



