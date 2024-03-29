# 数据库

## 2.数据库基础知识

### 2.1什么是数据？

```text
   数据是信息的表现形式和载体，可以是符号、文字、数字、语音、图像、视频等。
   通俗一点，数据就是信息，例如，个人信息、账户信息、家庭信息、企业信息、财务信息等等。
```

### 2.1什么是数据库（Database，DB）？

```text
数据库是按照数据结构来组织、存储和管理数据的仓库。
```

### 2.2 为什么要使用数据库？

![Alt text](https://github.com/luggege/book/tree/f7d098fe1f889ccf3b383f621c0b48c599f5fdd3/pic/1.png)

![Alt text](https://github.com/luggege/book/tree/f7d098fe1f889ccf3b383f621c0b48c599f5fdd3/pic/2.png)

* 数据安全

  数据库---&gt;仓库 数据----&gt;仓库中的货物

  没有了仓库，货物的安全没有保证，数据更是如此，如果一些重要的信息被我们随意的存放。

* 查找方便

### 2.3 什么是数据库管理系统（DataBase Management System，DBMS）？

数据库管理系统（DataBase Management System，DBMS）是为管理数据库而设计的大型电脑软件管理系统 例如，Oracle、Microsoft SQL Server、Access、MySQL、PostgreSQL、db2等等 我们可以简称这些数据库管理系统为数据库，虽然这种叫法不是很严谨，但是一般人都听的懂。

### 2.3 数据库的分类

* 关系型数据库

  关系数据库管理系统\(Relational Database Management System\)，

  是将数据组织为相关的行和列的系统，而管理关系数据库的计算机软件就是关系数据库管理系统，常用的数据库软件有Oracle、SQL Server、MySQL等。

* 非关系型数据库 nosql

  * 内存数据库 redis
  * 面向文档数据库 mongodb

    **2.4 数据库管理系统、数据库的关系？**

    ![Alt text](https://github.com/luggege/book/tree/f7d098fe1f889ccf3b383f621c0b48c599f5fdd3/pic/3.png)

### 2.5 表

表就是由行列组成的一个二维的数据结构

![Alt text](https://github.com/luggege/book/tree/f7d098fe1f889ccf3b383f621c0b48c599f5fdd3/pic/5.png)

### 2.6 数据类型

* 整数类型

![Alt text](https://github.com/luggege/book/tree/f7d098fe1f889ccf3b383f621c0b48c599f5fdd3/pic/6.png)

* 浮点数类型和定点数类型

![Alt text](https://github.com/luggege/book/tree/f7d098fe1f889ccf3b383f621c0b48c599f5fdd3/pic/7.png)

* 日期和时间类型

![Alt text](https://github.com/luggege/book/tree/f7d098fe1f889ccf3b383f621c0b48c599f5fdd3/pic/8.png)

* 字符串和二进制类型

![Alt text](https://github.com/luggege/book/tree/f7d098fe1f889ccf3b383f621c0b48c599f5fdd3/pic/9.png)

## 2.创建库、创建表

创建数据库 数据库名称 要有意义 基字符集 utf8 数据库排序规则 utf8\_general\_ci

练习：创建一个员工表employee --- 查看表结构：desc 表明；

属性 类型 id 整型 name 字符型 gender 字符型 birthday 日期型 entry\_date 日期型 job 字符型 salary 小数型

## 3.sql语言

### 3.1什么是sql语言？

* SQL（Structure Query Language）：结构化查询语言 是一种数据库查询语言。
* SQL就是专门用来操作数据库的
* SQL语言是一个标准。由一个规范组织提出和维护的。
* 基本上关系型的数据库都支持sql语言

  **3.2学习sql的网站**

  [http://www.w3school.com.cn/sql/index.asp](http://www.w3school.com.cn/sql/index.asp)

[http://www.runoob.com/sql/sql-syntax.html](http://www.runoob.com/sql/sql-syntax.html)

### 3.3 增删改查 CRUD

CRUD是Create\(创建\)、Read\(读取\)、Update\(更新\)和Delete\(删除\) 对于我们的web网站的后台其实就是对数据的增删改查操作。

### 3.3 insert

INSERT INTO 表名称 VALUES \(值1, 值2,....\)

我们也可以指定所要插入数据的列： INSERT INTO table\_name \(列1, 列2,...\) VALUES \(值1, 值2,....\) 使用INSERT语句向employee表中插入三个员工信息。 注意： values中的值必须与表中的字段一一对应。 插入的数据应与字段中的数据类型相同 数据的大小应该在列的规定范围内，例如不能将一个长度为80的字符串插入到长度为40个列中 字符和日期型数据应该包含在单引号中 如果要插入一个空值，不指定或者使用NULL

### 3.4 update

UPDATE 表名称 SET 列名称 = 新值 WHERE 列名称 = 某值 练习： 1. 将所有员工薪水改为10元 2. 将姓名为’张飞’的员工薪水修改为3000元 3. 将姓名为’李四’的员工薪水修改为4000元，job改为CEO 4. 将‘赵云’的薪水在原有基础上增加1000元

总结： UPDATE语句可以用新值更新原有表中行的列。 SET字句指定要修改哪些列和要给与哪些值 WHERE需要给定一个条件，表示要更新符号该条件的行，没有WHERE字句，则更新所有行

### 3.5 delete

DELETE FROM 表名称 WHERE 列名称 = 值

练习: 1. 删除employee表中名称叫‘张飞’的记录 2. 删除表中所有记录 总结： 如果不使用WHERE语句，将删除表中所有数据 DELETE不能删除某一列的值，（可使用UPDATE） 使用DELETE语句仅仅删除记录，不删除表本身，如果要删除表，使用DROP TABLE语句

### 3.6 select

SQL SELECT 语法 SELECT 列名称 FROM 表名称 以及： SELECT \* FROM 表名称 练习：

创建一张学生信息表student 并插入信息，SQL执行语句如下： CREATE TABLE student\( id INT PRIMARY KEY auto\_increment, name VARCHAR\(20\) NOT NULL, chinese DOUBLE, math DOUBLE, english DOUBLE \); INSERT INTO student VALUES\(NULL,'关羽',85,76,70\); INSERT INTO student VALUES\(NULL,'关羽',85,76,70\); INSERT INTO student VALUES\(NULL,'关羽',85,76,70\); 在所有学生分数上加10分特长分显示 select name,chinese+10,math+10,english+10 from stuent; 统计每个学生的总分 select name,chinese+math+english from student; 使用别名表示学生总分 select name as 姓名,chinese+math+english as 总成绩 from student

### 3.7 where 带条件的查询

SELECT \* FROM table\_name WHERE expr;

练习： 查询姓名为XXX的学生 查询英语成绩大于90分的同学 查询总分大于200分的所有同学

在WHERE字句中经常使用的运算符

比较运算符 &gt; &lt; &lt;= &gt;= = &lt;&gt; 大于、小于、大于\(小于等于\)、不等于 BETWEEN…AND 显示在某一区间的值 IN\(set\) 显示在in列表中的值，例：in\(100,200\) LIKE ‘张pattern’ 模糊查询% IS NULL 判断是否为空

逻辑运算发 AND 多个条件同时成立 OR 多个条件任一成立 NOT 不成立，例：WHERE NOT\(salary&gt;100\)

LIKE语句中，%代表零个或多个任意字符，&gt;\_代表一个字符，例如：name LIKE ‘\_a%’;

练习： 查询英语成绩分数在 80-100之间的同学 查询数学分数为75,76，77的同学 查询所有性张的学生成绩 查询数学分大于70，语文分数大于80的同学

