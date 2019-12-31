# 原型三角绘制

请尝试绘制如下三种情况的原型三角形图：

## 练习一： <a id="&#x7EC3;&#x4E60;&#x4E00;&#xFF1A;"></a>

```text
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

## 练习二： <a id="&#x7EC3;&#x4E60;&#x4E8C;&#xFF1A;"></a>

```text
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

## 练习三： <a id="&#x7EC3;&#x4E60;&#x4E09;&#xFF1A;"></a>

```text
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

