## 原型三角形绘制 {#原型三角形绘制}

请尝试绘制如下三种情况的原型三角形图：

### 练习一： {#练习一：}

```
function
Person
(
) 
{
    
this
.name = 
'张三'
;
    
this
.sayHello = 
function
 (
) 
{
    }
}


var
 p = 
new
 Person();

```

### 练习二： {#练习二：}

```
function
Person
(
) 
{
    
this
.name = 
'张三'
;
}

Person.prototype.sayHello = 
function
 (
) 
{
}

var
 p = 
new
 Person();

```

### 练习三： {#练习三：}

```
function
Person
(
) 
{
    
this
.name = 
'张三'
;
}

Person.prototype = {
    sayHello: 
function
 (
) 
{
    }    
};


var
 p = 
new
 Person();
```



