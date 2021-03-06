
# 正则表达式 in Javascript

## 创建RegExp对象的两种形式

```javascript
var re1 = /test/
var re2 = /test/gim
```

和

```javascript
var re1 = new RegExp("test")
var re2 = new RegExp("test", "gim")
```

*当需要动态地创建一个正则表达式时，只能使用后者。例如由用户输入检索字符串的时候。*


## 正则表达式的标志

* **i** 匹配时不区分大小写

* **g** 执行全局匹配，返回所有结果

* **m** 多行模式，此时，^可以匹配行首，$可以匹配行尾


## 正则表达式的直接量字符

* **字母或数字或字符**  匹配自身

* **\o** NUL字符 (\u0000)

* **\t** 制表符 (\u0009)

* **\n** 换行符 (\u000A)

* **\v** 垂直制表符 (\u000B)

* **\f** 换页符 (\u000C)

* **\r** 回车 (\u000D)

* **\xnn** 十六进制字符。例如，\x0A 等价于 \n

* **\uxxxx** 十六进制unicode。例如，\u000A 等价于 \n

* **\cX** 控制字符^X。例如，\cJ 等价于 \n


## 正则表达式的特殊符号

** ^ $ . * + ? = ! : | \ / ( ) [ ] { } **

如果作为直接量使用需要使用 \ 转义


## 正则表达式的字符类

* **[...]** 括号中的任意字符

* **[^...]** 非括号中字符的任意字符

* **.** 非换行符/其他Unicode行终止符的任意字符

* **\w** ASCII单字字符，等价于[a-zA-Z0-9_]

* **\W** 非ASCII单字字符，等价于[^a-zA-Z0-9_]

* **\s** Unicode空白符

* **\S** 非Unicode空白符的字符

* **\d** ASCII数字，等价于[0-9]

* **\D** ASCII数字之外的字符，等价于[^0-9]

* **[\b]** 退格直接量（特殊）


## 正则表达式的选择、分组和引用字符

* **|** 选择。匹配该符号左边的子表达式或右边的子表达式

* **(...)** 组合。将几个项目组合为一个单元并返回匹配结果

* **(?:...)** 组合但不返回匹配结果

* **\x** 引用第x个分组的匹配结果

* **[a]{1,3}** 重复模式，1～3次

* **(...)\1** 任意三个字母叠词

## 正则表达式的锚字符

* **^** 匹配字符串开头，在m标志模式下，匹配字符串开头和行首

* **$** 匹配字符串结尾，在m标志模式下，匹配字符串结尾和行尾

* **\b** 匹配一个词语边界。即\w和\W之间的位置。

* **\B** 匹配非词语边界。

* **(?=p)** 正前向声明，要求与子串p匹配。不返回匹配结果

* **(?!p)** 反前向声明，要求不与子串p匹配。不返回匹配结果


## 使用模式匹配的 String 方法

* **replace** 使用**g**标志进行全局替换，第二个参数可传入一个回调函数

* **search** 忽略**g**标志

* **split** 忽略**g**标志。可使用第二个参数指定返回数组的最大长度

* **match**  返回结果数组，第一个元素是完整的匹配结果，余下的元素是正则表达式中使用了括号括起来的内容。使用**g**标志时，执行全局检索。

## 使用模式匹配的 RegExp 方法

* **exec** 只返回一个结果。

* **test** 行为与exec相同

#### 这两个方法每次执行匹配都以RegExp对象的lastIndex属性为起始位置开始检索（初始值为0）。当使用g标志时，它会将把该对象的lastIndex设置为本次匹配结果子串的下一个位置。如果该RegExp对象被重复使用于匹配不同的字符串，那么必须找到每个字符串中的所有匹配，或者手动将lastIndex属性的值设置为0，否则下一次匹配的起始位置可能是任何位置。




