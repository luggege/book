选项卡问题
 
` <select name="" id="type" onchange="change(this)">    
    <option value="0" selected="selected">极速赛车</option>
    <option value="1">极速赛车1</option>
    <option value="2">极速赛车2</option>
    <option value="3">极速赛车3</option>
</select> `
> 通过给select绑定onchange事件就可获取到当前选取

` function change(obj){
    * obj.options[obj.selectedIndex].value;
    * document.getElementById('type').value;
    * obj.value;   
    location.href=obj.value
} `