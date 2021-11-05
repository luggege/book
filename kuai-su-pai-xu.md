### 快速排序

> 选取递归时的第一个值作为**基准点**，然后将大于基准点的放到右边，将小于基准点的放到左边，**递归遍历（一定要从基准点之后即 i === 1 开始遍历）**直到子串**长度为 1或为**空，**归**的时候依次拼接有序的**左、基准点、右**，最后形成升序排序数组

```js
let arr = [29, 10, 19, 9, 33];

const rec = (arr) => {
    if(arr.length <= 1) {
        return arr;
    }
    const basePoint = arr[0];
    let left = [];
    let right = [];
    for(let i = 1; i < arr.length; i++) {
        if(arr[i] < basePoint) {
            left.push(arr[i]);
        }else {
            right.push(arr[i]);
        }
    }
    const orderLeft = rec(left);
    const orderRight = rec(right);
    return [...orderLeft, basePoint, ...orderRight];
}

rec(arr)
```



