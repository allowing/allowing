# PHP教程 - 类与对象

类的概念很简单，如人类、鸟类、长方形、学生、植物、动物、蔬菜、水果等，这些都是类，而对象就是这些类中的一个实例，比如说“学生”，如果单单就说“学生”它是指一类人，而如果张三是一个学生，那么张三就是学生的一个实例，也就是说张三是一个学生类的对象。

## 类的属性

拿学生这个类来举例，学生一般会有下列属性：

* 年级
* 班级
* 学校
* 姓名
* 性别
* 身高
* 体重
* 班主任

但不是只有这些属性。

## 类的方法

学生一般会有下列方法：

* 上课
* 写字
* 读书
* 给老师起外号
* 擦黑板
* 做广播体操
* 吃饭

## 在PHP代码中表示类

在代码中怎么表示学生这个类呢，请看一组代码

```php
class Student
{

}
```

像声明函数一样，声明一个类用「class」关键字，接着是类名，再接着是一对花括号。

注意：类名首字母要大写，如果是多个单词，每个单词的首字母都要大写。

像上面这样只是声明了一个类，但是还没表示出属性和方法啊，接着看

```php
class Student
{
    $grade; // 年级
    $school; // 学校
    $teacher; // 班主任
    $name; // 姓名
    $height; // 身高
    $weight; // 体重
}
```

就像上边的示例一样，在类中用一个变量表示属性。那么方法呢怎么表示，继续看

```php
class Student
{
    $grade; // 年级
    $school; // 学校
    $teacher; // 班主任
    $name; // 姓名
    $height; // 身高
    $weight; // 体重
    // 学习方法
    function study()
    {
        return '正在学习';
    }
    // 吃饭方法
    function eat()
    {
        return '吃饭中';
    }
    // 阅读方法
    function read()
    {
        return '阅读中';
    }
}
```

正如看到，在PHP中用一个函数表示类的方法。

OK，类可以很完美地在代码中表示出来。怎么表示一个实例？请看

```php
$student = new Student;
```

「new」是新建的意思，「new Student」就是新进一个学生类的实例。返回的是一个实例的引用，根据这个引用就能找到这个实例。

至此，已经完全可以用代码的形式表示出现实中的类与对象的概念了。

## 访问实例的属性

看示例代码，注意怎么设置实例的属性值，获取实例的属性值，怎么调用实例的方法：

```php
$student = new Student;
$student->name; // null 获取属性值
$student->name = '张三'; // 设置属性值
$student->name; // 张三 再获取的时候就变成了张三
$student->study(); // 调用方法
```

如实例代码所示，在PHP中是通过「->」箭头这个符号来访问属性和方法的，这只是一种表示形式，就这写就行。

## 构造方法

上面的「Student」类里，属性都没有赋值，那么默认就是「null」实例化出来的对象的对应属性也就是 null。所以在定义类时，可以给属性赋上默认值，这样做的话，实例化出来的对象就具有相同的属性值，可是更多时候我们希望调用者传递进来，这该怎么做呢，下面引入构造方法的概念。

事实上，当我们「new Student」新建对象的时候，会触发一个魔术函数的执行这个魔术函数叫做构造方法，函数名是固定的「__construct」，看示例代码

```php
class Student
{
    $grade = 1; // 年级 这样可以设置默认值
    $school; // 学校
    $teacher; // 班主任
    $name; // 姓名
    $height; // 身高
    $weight; // 体重
    // 这个叫做构造方法
    function __construct()
    {

    }
    // 学习方法
    function study()
    {
        return '正在学习';
    }
    // 吃饭方法
    function eat()
    {
        return '吃饭中';
    }
    // 阅读方法
    function read()
    {
        return '阅读中';
    }
}
```

这样，我们就可以通过编写构造方法的函数体，实现想要的逻辑，例如新建学生实例时，要求指定学生的姓名，可以这样做

```php
class Student
{
    $grade; // 年级
    $school; // 学校
    $teacher; // 班主任
    $name; // 姓名
    $height; // 身高
    $weight; // 体重
    // 这个叫做构造方法
    function __construct($name)
    {
        $this->name = $name;
    }
    // 学习方法
    function study()
    {
        return '正在学习';
    }
    // 吃饭方法
    function eat()
    {
        return '吃饭中';
    }
    // 阅读方法
    function read()
    {
        return '阅读中';
    }
}
```

在上面的代码中，看构造方法那里，「$this」代表刚刚新建的对象，「$this->name」表示这个对象的属性，然后把传递进来的姓名赋值给这个新建对象的 name 属性，这样新建的对象 name 属性就有值了，那些没有赋值的属性就依然是 null。

有了构造方法而构造方法又有参数的时候，该怎么新建对象呢，请看

```php
$zhangsan = new Student('张三');
```

就是这样，new 的时候，在类名后面接一个小括号，小括号里的参数会自动传递到构造方法对应位置上。

## 总结

* 程序中的类，也是生活中的类的概念。
* 用一个变量表示类的属性。
* 用一个函数表示类的方法。
* 属性可以赋一个默认值。
* 构造方法是在实例化的过程中自动触发的一个魔术函数，它的名字是「__construct」，通过编写构造方法的函数体逻辑，可以指定怎样初始化一个实例。
* 访问属性和方法是通过一个箭头「->」来完成的。