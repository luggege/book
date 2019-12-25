#### Number 对象属性 {#number对象}

| 属性 | 描述 |
| :--- | :--- |
| MAX\_VALUE | 可表示的最大的数。                     1.7976931348623157e+308 |
| MIN\_VALUE | 可表示的最小的数。                     5e-324 |
| NaN | 非数字值。相当于NaN                                           NaN |
| NEGATIVE\_INFINITY | 负无穷大，溢出时返回该值。相当于-Infinity       -Infinity |
| POSITIVE\_INFINITY | 正无穷大，溢出时返回该值。相当于Infinity        Infinity |

#### Number 对象方法 {#number-对象方法}

| 方法 | 描述 |
| :--- | :--- |
| toString | 把数字转换为字符串，使用指定的基数。 |
| toFixed | 把数字转换为字符串，结果的小数点后有指定位数的数字。 |
| toExponential | 把对象的值转换为指数计数法。 |
| toPrecision | 把数字格式化为指定的长度。 |
| valueOf | 返回一个 Number 对象的基本数字值。 |

#### 浮点数值

ECMAScript会将那些极大极小的值用科学计数法表示 

```js
// 极大值：小数点后大于等于6个零的浮点值会转换
0.0000002
2e-7

// 极小值：长度超过22位的整数时会转换
2200000000000000000000
2.2e+21
```



