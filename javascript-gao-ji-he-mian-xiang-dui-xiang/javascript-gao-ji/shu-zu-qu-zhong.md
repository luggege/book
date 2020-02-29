# 数组去重

### 利用indexOf去重

```javascript
var arr = [1, undefined, undefined, 2, null, 2, 3, 4, 4];
var temp = [];
for(var i = 0; i < arr.length; i++){
    if(temp.indexOf(arr[i]) === -1){
        temp.push(arr[i])
    }
}

temp   // [1, undefined, 2, null, 3, 4]
```

### 利用ES6 Set 去重

```js
1. Array.from(new Set([1, undefined, undefined, 2, null, 2, 3, 4, 4]))

2. [...new Set([1, undefined, undefined, 2, null, 2, 3, 4, 4])]

// [1, undefined, 2, null, 3, 4]
```

### 利用for循环嵌套for，然后splice删除

```js
arr = [1, undefined, undefined, 2, null, 2, 3, 4, 4]
for(var i=0; i<arr.length; i++){
    for(var j=i+1; j<arr.length; j++){
        if(arr[i]==arr[j]){  
            arr.splice(j,1);
            j--；
        }
    }
}
// [1, undefined, 2, null, 3, 4]
```

### 利用sort

```js
arr = arr.sort();
var temp = [arr[0]]
for(var i = 1; i < arr.length; i++){
    if(arr[i] !== arr[i - 1]){
        temp.push(arr[i])
    }
}
// [1, 2, 3, 4, null, undefined]
```



