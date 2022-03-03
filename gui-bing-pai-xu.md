### 归并排序（先递分两半，然后归时依次取最小值组合）

> 分治策略，递归。递的时候先到最小单元（length===1），然后在第一次归的时候，拿出左右两个数组的值做比较，按序放到一个新数组返回，继续归的时候，新排序的左右数组length就不为1了，所以其实在第一次加一层遍历，当左右数组的length不为0的时候，依次比较左边第一个和右边第一个，拿出拿出更小的那个放到新数组，依次。。。升序排列

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
    // 从新排序的左右数组中，逐个*取出*最小值放到temp中(排序)
    while(orderLeft.length && orderRight.length) {
        if(orderLeft[0] < orderRight[0]) {
            // 一定是shift()将最小值拿出
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

时间复杂度：O\(nlogn\)，以时间换空间  
空间复杂度：O\(n\)

