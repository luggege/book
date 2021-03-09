### Object.freeze\(\): 冻结一个对象

```js
var person = {
    name: 'jack',
    skill: {}
}

Object.freeze(person)

person.name = 'aaa'

console.log(person)  // {name: "jack", skill: {}}
```

* 属性为对象的**浅冻结**

```js
person.skill.name = 'eat'

console.log(person)  // {name: "jack", skill: {name: "eat"}}
```

#### Object.isFrozen\(\): 判断一个对象是否冻结

```js
Object.isFrozen(person) // true
```



