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

 

