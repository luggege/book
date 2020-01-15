# 深拷贝浅拷贝

### 深拷贝、浅拷贝的区别

> 新对象（数组）引用旧对象（数组），改变旧对象（数组）的值，如果新对象（数组）的值也跟着改变，即浅拷贝。如果不影响，即深拷贝

```javascript
    // 1. 数组
    // 适用于深拷贝一层数组且值为基本类型的方法有：遍历属性、slice、concat、Object.assign
    var arr = [1, 2, 3, 4, 5]
    // var arr = [
    //     {number: 111},
    //     {number: 222},
    //     {number: 333}
    // ]

    function copy(arr){
        var newArr = []
        for(let item in arr){
            newArr.push(arr[item])
        }
        return newArr
    }

    var arr1 = copy(arr)

    var arr2 = arr.slice()  //arr.slice(0)

    var arr3 = arr.concat()

    var arr4 = []
    Object.assign(arr4, arr)

    arr[0] = 100
    // arr[0].number = 100

    console.log('arr```````', arr)     // [100, 2, 3, 4, 5]
    console.log('arr1```````', arr1)   // [1, 2, 3, 4, 5]
    console.log('arr2```````', arr2)   // [1, 2, 3, 4, 5]
    console.log('arr3```````', arr3)   // [1, 2, 3, 4, 5]
    console.log('arr4``````', arr4)    // [1, 2, 3, 4, 5]
    
    

    // 2. 对象(一层)
    var obj = {
        a: 1,
        1: 'aaa',
        b: 2,
        2: 'bbb'
    }

    function copy1(obj){
        var newObj = {}
        for(var item in obj){
            newObj[item] = obj[item]
        }
        return newObj
    }

    var obj1 = copy1(obj)

    var obj2 = JSON.parse(JSON.stringify(obj))

    obj.c = '333'

    console.log('obj````````', obj)            // {1: "aaa", 2: "bbb", a: 1, b: 2, c: "333"}
    console.log('obj1````````', obj1)          // {1: "aaa", 2: "bbb", a: 1, b: 2}             
    console.log('obj2````````', obj2)          // {1: "aaa", 2: "bbb", a: 1, b: 2}
    
    
    // 所有层级
    // 1. JSON.parse + JSON.stringify(obj)
    
    // 2. 递归复制所有层级属性
    function deepCopy(obj){
        let newObj = Array.isArray(obj) ? [] : {}
        if(obj && typeof obj === 'object'){
            for(key in obj){
                if(obj.hasOwnProperty(key)){
                    if(obj[key] && typeof obj[key] === 'object'){
                        newObj[key] = deepCopy(obj[key])
                    }else {
                        newObj[key] = obj[key]
                    }
                }
            }
        }
        return newObj   
    }

    let arr = [1, 2, 3, 4, 5]
    let arr1 = deepCopy(arr)

    arr[0] = 100

    console.log(arr, arr1)  
    // [100, 2, 3, 4, 5]   
    // [1, 2, 3, 4, 5]

    let obj = {
        a: {
            aaa: 1
        },
        1: 'aaa',
        b: 2,
        2: 'bbb'
    }

    let obj1 = deepCopy(obj)
    obj.a.aaa = 111

    console.log(obj, obj1)  
    // {1: "aaa", 2: "bbb", a: {aaa: 111}, b: 2}  
    // {1: "aaa", 2: "bbb", a: {aaa: 1}, b: 2} 
    
    
    // 3. jquery的extend方法(不适用与IE11及以下)
    var obj1 = $.extend(true, {}, obj);
    obj.a.aaa = 111;

    console.log(obj, obj1);
    // {1: "aaa", 2: "bbb", a: {aaa: 111}, b: 2}  
    // {1: "aaa", 2: "bbb", a: {aaa: 1}, b: 2} 
```

