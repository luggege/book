### 归并排序

> 分治策略

```js
let arr = [29, 10, 19, 9, 33];
let rec = (arr) => {
    if(arr.length <= 1) {
        return arr
    }
    const midPoint = Math.floor(arr.length / 2);
    const left = arr.slice(0, midPoint);
    const right = arr.slice(midPoint);
    const orderLeft = rec(left);
    const orderRight = rec(right);
    // console.log(orderLeft, orderRight, arr);
    let temp = [];
    // 逐个取出最小值放到temp中(排序)
    while(orderLeft.length && orderRight.length) {
        if(orderLeft[0] < orderRight[0]) {
            temp.push(orderLeft.shift());
        }else {
            temp.push(orderRight.shift());
        }
    }
    // 拼接剩下的(orderLeft, orderRight长度不一致的情况)
    temp = temp.concat(orderLeft, orderRight);
    console.log('temp', temp);
    return temp
}
rec(arr)
```



