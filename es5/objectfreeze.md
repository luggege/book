### Object.freeze\(\): 冻结一个对象

* 冻结基础类型的属性

```js
var person = {
    name: 'jack',
    skill: {}
}

Object.freeze(person)

person.name = 'aaa'

console.log(person)  // {name: "jack", skill: {}}
```

* **属性为对象**的**浅冻结**

```js
person.skill.name = 'eat'

console.log(person)  // {name: "jack", skill: {name: "eat"}}
```

### Object.isFrozen\(\): 判断一个对象是否冻结

```js
Object.isFrozen(person) // true
```



