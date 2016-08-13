# PHP教程 - 类型
在PHP中，有8种原始类型。其中有四种标量类型，两种复合类型。

四种标量类型：
* boolean（布尔型）
* integer（整型）
* float（浮点型，也称作 double)
* string（字符串）

两种复合类型：
* array（数组）
* object（对象）

最后是两种特殊类型：
* resource（资源）
* NULL（无类型）

类型可以通俗地理解为数据的分类。更多请看下面这组代码：
```php

1; // 这是一个数字，标量
'我在学习PHP教程'; // 这是字符串，标量
true;
false; // true 和 false 是布尔类型的两个值，布尔类型也只有这两个值。true 表示真，false 表示假
3.14; // 小数，就是浮点数，标量

['123', '张三', '18']; // 数组，这是符合类型
array('123', '张三', '18') // 这是PHP5.3或以下版本的数组表示方法
null; // 「无类型」的值，这是一个特殊的类型，就表示「无」这个概念，这种类型的值也只有 「null」

// 剩下的对象、资源这两种类型由于没有字面的表示方法，所以这里举不了例子。
```