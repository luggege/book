# 选项卡

```rust
<select name="" id="type" onchange="change(this)">    
    <option value="0" selected="selected">极速赛车</option>
    <option value="1">极速赛车1</option>
    <option value="2">极速赛车2</option>
    <option value="3">极速赛车3</option>
</select>
```

> 通过给select绑定onchange事件就可获取到当前选取的option的value值

```javascript
function change(obj){
    obj.options[obj.selectedIndex].value;
    document.getElementById('type').value;
    obj.value;
    location.href=obj.value                //通过value值也可切换相应的option链接的页面
}
```

