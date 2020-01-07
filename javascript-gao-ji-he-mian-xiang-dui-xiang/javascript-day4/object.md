# Object

### Object.keys\(\)

Object.keys\(\)方法返回一个所有可枚举属性组成的数组，同for in循环遍历返回的排序一致。

```javascript
var obj  = {
  2: 'aaa',
  c: 333,
  1: 'bbb',
  a: 111,
  3: 'ccc',
  d: 222
}
obj.b = "ddd"
console.log(Object.keys(obj))
// ["1", "2", "3", "c", "a", "d", "b"]
console.log(Object.values(obj))
// ["bbb", "aaa", "ccc", 333, 111, 222, "ddd"]


var arr = [0, null, 1, undefined, 2, 3];
console.log(Object.keys(arr))
//  ["0", "1", "2", "3", "4", "5"]


var str = 'aaabbbccc'
console.log(Object.keys(str))
//  ["0", "1", "2", "3", "4", "5", "6", "7", "8"]
```

### Object.values\(\)

同Object.keys\(\)方法相反，取的是value值组成的数组，实例如上。

