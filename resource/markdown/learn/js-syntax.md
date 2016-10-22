# JS教程 - 基础语法

## 注释

在示例代码认识注释

```js
// 单行注释
/*
多行注释
可以换行
*/
```

## 变量

### 声明变量

在 js 中用 var 关键字声明一个变量

```js
var name; // 声明变量
var age = 18; // 声明一个变量同时给变量赋值
```

如果只是声明一个变量，并没有给这个变量初始值的话，那么这个变量的值是 undefined

如果没有用 var 关键字声明变量，那么这个变量会自动变为全局对象的一个属性，在浏览器环境中就是 window 对象的属性。

```js
// 没有用 var 关键字声明变量
name = '张三';
// 浏览器环境下 window 对象就会多一个 name 属性
console.log(window.name); // 张三
```

所以始终应该记得，声明变量要用 var 关键字，不然这个就不是变量，而是一个全局对象的属性。

### 变量的命名规范

* 变量名应当是字母、数字、下划线的组合
* 第一个字符不能是数字
* 变量名用驼峰式，第一个单词首字母小写往后的单词首字母都大写。如 myName

### 变量类型

在 js 中，变量有以下类型

* 字符串(String)
* 数字(Number)
* 布尔(Boolean)
* 数组(Array)
* 对象(Object)

```js
var name = '张三'; // name 是字符串类型
var age = 18; // age 是数字类型
var array = ['张三', '李四', '王五']; // array 是数组类型
var bool = true; // bool 是布尔类型
var obj = {name: '张三', age: 18}; // obj 是对象类型
```

## 流程控制

### if

```js
if (1 > 0) {
    // 满足条件则进来这里
}
```

### if ... else

```js
if (1 > 0) {
    // 满足条件进来这里
} else {
    // 不满足条件进来这里
}
```

### if ... else if

```js
if () {
    // 分支1
} else if () {
    // 分支2
} else if () {
    // 分支3
} else {
    // 分支4
}
```

## 循环

循环地执行某逻辑

### while 循环

```js
var i = 0;
var s = 0;
while (i <= 100) {
    s = s + i;
    i++;
}
```

当 i 的值小于等于 100 时，循环地执行循环体内的逻辑，当条件不满足时就退出循环体。

### do ... while 循环

```js
var i = 0;
var s = 0;
do {
    s = s + i;
    i++;
} while(i <= 100);
```

do ... while 循环是上来就执行一下循环体，完了之后再判断，所以 do ... while 的循环体至少都执行一遍，而 while 循环有可能一次都不执行。

### for 循环

```js
for (初始化; 循环条件; 循环体结束后执行的逻辑) {
    循环体
}
```
```js
for (var i = 0, s = 0; i <= 100; i++) {
    s = s + i;
}
```

## 函数

在 js 中，函数是一种特殊的表达式，叫函数表达式，这个表达式是可以赋值给一个变量的，也可以赋值给某个对象的属性，同时函数也是一个对象。

函数表达式要用 function 关键字声明

```js
function foo()
{
    // 函数体
}
```

像上面这样就声明了一个函数，这个函数的名字叫 "foo", 没有参数。在 js 中这样的函数也叫命名函数。

如果像上面例子那样声明函数的话，事实上是在全局对象上开辟了一个以函数名为属性名的属性，在这里是"foo"，这个属性的值就是函数表达式。在浏览器环境下就是 window.foo 如

```js
window.foo = function () {
    // 函数体
};
```

所以从这个意义上来讲，js 的函数也是一种特殊的“值”，所以可以看到结束花括号后面是要加分号的。那么也就不难理解把一个函数赋值给一个变量了，请看

```js
var foo = function () {
    // 函数体
};
```

像上面这样的函数因为没有名字，所以也叫匿名函数。注意那个变量不是函数的名字，只是用来保存了这个函数表达式而已。

因为函数是表达式，所以在函数的内部还是可以声明函数的，如下

```js
function foo()
{
    function bar()
    {
        // 函数体
    }
}
```

最外面的 foo 函数，实际上是 window 的一个属性，但是注意啊，内部的那个 bar 函数就不再是 window 上的属性了。

```js
// 这个是正确的
window.foo = function () {
    function bar()
    {
        // 函数体
    }
};
```

```js
// 这个是错误的
window.bar = function () {
    // 函数体
};
```

这个问题要注意。

## 函数调用

调用函数很简单，给函数表达式加一个小括号就行了，没有参数的函数小括号就留空，有参数的就在小括号里放上参数。

```js
foo();
bar('张三', 18);
```

有趣的是，还可以直接调用函数表达式，就是既不给函数命名也不赋值给一个变量，直接用小括号扩起来，再调用，如下

```js
(function () {
    // 函数体
})();
```

这样子做的好处是什么呢，因为这个函数是匿名的，又没有赋值给一个变量，所以后文就无法再引用这个函数了，其实要的就是这个效果，就是要让后文不能再调用它，它只需要自动执行一次就够了。还有就是作用域的问题了，这个在这里先不提。