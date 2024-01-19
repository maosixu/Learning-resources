# 零、前言

为什么使用Kotlin，在官方中是这样描述的，因为其具有一下优点：

* 简单的
* 异步的
* 面向对象的
* 功能性的
* 适合测试

同时使用 `Kotlin Multiplatform` 简化跨平台项目的开发。它减少了为不同平台编写和维护相同代码所花费的时间，同时保留了本机编程的灵活性和优势。`Kotlin` 应用程序将在不同的操作系统上运行，例如 `iOS`、`Android`、`macOS`、`Windows`、`Linux`、`watchOS` 等。

共享的 `Kotlin` 代码编译成平台二进制文件，无缝集成到任何项目中。除了允许您利用特定于平台的 `API` 的语言功能之外，您不再需要在本机开发和跨平台开发之间做出选择。您可以同时拥有两全其美！

# 一、基础知识

下面是一段`Kotlin`代码：

```kotlin
fun main() {
  	println("Hello, world!")
  	// Hello, world!
}
```

在Kotlin中：

- `fun` 用于声明函数
- `main()` 函数是你的程序的起始点
- 函数体是写在大括号 `{}` 里的
- `println()` 和 `print()` 函数将它们的参数打印到标准输出

函数在下面详细讨论，现在我们先使用`main`函数

## 1.1 变量

`val`：声明一个不可变的变量。对应`Java`的`final`。

`var`：用来声明一个可变变量。

> 编译器通过类型推导机制分析变量的类型。
>
> 同时，`kotlin`每一行代码的结尾不用加分号。

```kotlin
fun main(args: Array<String>) {
  	val a = 8	//此处推导出类型为Int
  	println("a = " + a)
}
```

当我们需要延迟对变量进行赋值时，就需要显式地声明类型变量类型。

```kotlin
fun main(args: Array<String>) {
  	val a:Int
  	a = 7
  	println(a)
}
```

`Kotlin`中`Int`的首字母是大写，`Java`中的`int`首字母是小写的。这表示`Kotlin`已经完全抛弃了`Java`中的基本数据类型，全部使用了对象数据类型。在`Java`中`int`是关键字，而在`Kotlin`中`Int`变成了一个类，它拥有自己的方法和继承结构。

下表列出了`Java`中的每一个基本数据类型对应`Kotlin`中的对象数据类型

| Java基本数据类型 | Kotlin对象数据类型 | 数据类型说明                                                 |
| ---------------- | ------------------ | ------------------------------------------------------------ |
| int              | Int                | 整形（-2^31~2^31-1）                                         |
| long             | Long               | 长整型（-2^63~^63 - 1）                                      |
| short            | Short              | 短整型（-2^15~2^15 - 1）                                     |
| float            | Float              | 单精度浮点型**正值**：float 类型的最小正标准值是 1.4E-45。**最大正值**：float 类型的最大正标准值是 3.4028235E38。**最小负值**：float 类型的最小负标准值是 -1.4E-45。**最大负值**：float 类型的最大负标准值是 -3.4028235E38。 |
| double           | Double             | 双精度浮点型**最小正值**：double 类型的最小正标准值大约是 4.9E-324。**最大正值**：double 类型的最大正标准值大约是 1.7976931348623157E308。**最小负值**：double 类型的最小负标准值大约是 -4.9E-324。**最大负值**：double 类型的最大负标准值大约是 -1.7976931348623157E308 |
| boolean          | Boolean            | 布尔型                                                       |
| char             | Char               | 字符型                                                       |
| byte             | Byte               | 字节型                                                       |

可以在程序开始时，也就是在主函数 `main()` 外部定义变量。这种方式定义的变量我们通常称之为**顶层变量**。

## 1.2 字符串模板

模板表达式可以获取变量和其他对象中存储的数据，并将其转换为字符串。模板表达式则总是以美元符号 `$` 作为开头

```kotlin
val customers = 10
println("这里有 $customers 顾客")
// 这里有 10 顾客

println("这里有 ${customers + 1} 顾客")
// 这里有 11 顾客
```

# 二、程序的逻辑控制

在 `Kotlin` 中，我们可以使用 `if` 和 `when` 这两个关键字来进行条件判断。

## 2.1 if条件语句

`kotlin`中的`if`语句和Java中的`if`语句几乎没有任何区别，下面通过简单例子了解一下。

```kotlin
val d: Int
val check = true

if (check) {
  	d = 1
} else {
  	d = 2
}

println(d)	// 1
```

与`Java`中`if`的不同之处在于`Kotlin` 语言中并没有` condition ? then : else `这样的三元运算符。取而代之的是，我们可以把 `if` 用作表达式。在这种情况下，我们就不需要使用大括号 `{}` 了：

```kotlin
fun main() { 
  	val a = 1
  	val b = 2

  	println(if (a > b) a else b) // 输出值为: 2
}
```

## 2.2 When条件语句

当你的条件表达式有多个分支时，你可以使用 `when`。`when` 可以被当作语句或者表达式。

下面这个例子，展示如何将 `when` **作为语句使用**：

- 你需要把条件表达式放在小括号` ()` 里，然后把对应的动作放在大括号 `{} `里。
- 在每个分支里，我们用 `->` 来区分条件和对应的动作。

```kotlin
fun main() {
  	val obj = "Hello"
  	when (obj) {
    	"1" -> println("One")
    	"Hello" -> println("Greeting")
    	else -> println("Unknown")    
  	}
  	// Greeting
}
```

注意，所有的分支条件都会按顺序检查，直到其中一个满足为止。只有第一个符合条件的分支会被执行.

下面这个例子，展示如何将 `when` **作为表达式**使用。这里的 `when` 结构被立即赋值给一个变量：

```kotlin
fun main() {
  	val obj = "Hello"    
  	val result = when (obj) {
    	"1" -> "One"
    	"Hello" -> "Greeting"
    	else -> "Unknown"
  	}
  	println(result)	// Greeting
}
```

如果把 `when` 用作表达式，那么必须要有 `else` 分支，**除非编译器能确定所有可能的情况都已经在分支条件里面考虑到了**(下面会有例子)。

前面的例子展示了当我们需要匹配一个变量时，`when` 是多么的有用。当你需要检查一连串的布尔表达式时，`when` 同样很实用，这也是`when`的一种不带参数的使用方法：

```kotlin
fun main() {
  val temp = 18

  val description = when {
    temp < 0 -> "very cold"
    temp < 10 -> "a bit cold"
    temp < 20 -> "warm"
    else -> "hot"             
  }
  println(description)	// warm
}
```

除了精确匹配之外，`when`语句还允许进行类型匹配。如下：

```kotlin
fun checkNumber(num: Number) = when (num) {
  is Int -> println("number is Int")
  is Double -> println("number is Double")
  else -> println("number not support")
}
```

上述代码中`is`关键字就是类型匹配的核心，相当于Java中的`Instanceof`关键字。

可能无参数的`when`语句写起来比较冗余，但有些场景必须使用这种写法才可实现。

例如：假设所有名字以`Tom`开头的人，他的分数都是86分，这种场景如果用有参数的`when`就无法实现，而使用不带参数的`when`就可以实现。

```kotlin
fun getScore(name: String) = when {
		name.startWith("Tom") -> 86
  	name == "Jim" -> 77
  	name == "Jack" -> 95
  	name == "Lily" -> 100
  	else -> 0
}
```

Kotlin中判断字符串或对象是否相等可以直接使用`==`关键字。

> ==和===的区别
>
> 1. == (结构相等)
>    * 在 Kotlin 中，`==` 用于比较两个对象的内容或值是否相等。
>    * 当使用 `==` 比较两个对象时，实际上是调用了 `equals()` 方法来判断两个对象的内容是否一致。
>    * 如果没有重写 `equals()` 方法，则比较的是对象的成员属性是否都相等。
> 2. === (引用相等)
>    * `===` 用于比较两个对象的引用是否完全相同，即它们是否指向同一个对象实例。
>    * 使用 `===` 时，即使两个对象内容完全一样，但它们在内存中的地址不同，也会返回 `false`。
>    * 该操作符检查对象的引用地址，而不涉及任何类型的转换或内容比较。

例子如下：

```kotlin
fun main() {
    val a = Integer(100)
    val b = Integer(100)
    println(a == b)	//true
    println(a === b)	//false
}
```

我们可以通过`tools -> kotlin -> show kotlin bytecode`查看`Kotlin`字节码，上述创建`a`,`b`常量的字节码如下：

```kotlin
	L0
    LINENUMBER 5 L0	//为调试目的而存在。它将源代码中的行号（在这个例子中是 5）与字节码中的一个指令位置（标签 L0）相关联。这允许调试器和其他工具将运行时发生的事件（如断点、异常等）映射回源代码的具体行。
    NEW java/lang/Integer	//创建了一个新的 Integer 类实例。
    DUP	//复制栈顶值
    BIPUSH 100	//将一个 byte 大小的常量值 (100) 推送至栈顶。
    INVOKESPECIAL java/lang/Integer.<init> (I)V	//调用 Integer 类的构造方法 <init>，该方法接受一个 int 类型的参数，并用之前推送的 100 进行初始化。
    ASTORE 0	//将栈顶的 Integer 对象引用存储到局部变量表的索引 0 的位置
   L1
    LINENUMBER 6 L1
    NEW java/lang/Integer
    DUP
    BIPUSH 100
    INVOKESPECIAL java/lang/Integer.<init> (I)V
    ASTORE 1
   L2
```

对比与下面这段代码的字节码

```kotlin
fun main() {
    val a = Integer(100)
    val b = a
    println(a == b)	//true
    println(a === b)	//true
}
```

字节码如下：

```kotlin
LINENUMBER 5 L0
    NEW java/lang/Integer
    DUP
    BIPUSH 100
    INVOKESPECIAL java/lang/Integer.<init> (I)V
    ASTORE 0
   L1
    LINENUMBER 6 L1
    ALOAD 0	//加载局部变量表中第 0 个槽位的对象引用（即之前存储的 Integer 对象）到栈顶。
    ASTORE 1
   L2
```

## 2.3 范围

在我们开始讨论循环之前，先了解一下如何构建循环迭代所需的范围是很有帮助的。

在 `Kotlin` 中，创建范围最常见的方式是使用 `..` 运算符。比如，`1..4` 就等同于 `1, 2, 3, 4`。

如果你想声明一个不包括结束值的范围，就使用` ..<` 运算符。例如，`1..<4` 就等同于 `1, 2, 3`。

如果你想声明一个逆序的范围，就使用 `downTo`。例如，`4 downTo 1` 就等同于 `4, 3, 2, 1`。

如果你想声明一个步长不为 1 的范围，就使用 `step` 和你想要的增量值。例如，`1..5 step 2` 就等同于 `1, 3, 5`。

你也可以对字符范围进行同样的操作：

- `'a'..'d'` 就等同于` 'a', 'b', 'c', 'd'`
- `'z' downTo 's' step 2` 就等同于 `'z', 'x', 'v', 't'`

## 2.3 循环语句

### 2.3.1 While循环

与`Java`中的`While`循环没有任何区别。

### 2.3.2 for循环

`Java`中最常用的`for - i`循环在`Kotlin`中直接被舍弃了，而`Java`中的另一种方式`for - each`循环则被`kotlin`进行了大幅的加强，变成了`for - in`循环，所以我们只需学习`for - in`循环即可。

例如：

```kotlin
fun main() {
    val range = 0..10
    for (i in range) {
        println(i)
      	//0,1,2,3,4,5,6,7,8,9,10
    }
}
```

我们可通过`until`关键字来创建一个左闭右开的区间，如下所示

```kotlin
val range = 0 until 10  //相当于[0,10)
fun main() {
		for (i in 0 until 10 step 2) {
    		println(i)
      	//0,2,4,6,8
    }
}
```

```kotlin
fun main() {
		for(i in 10 downTo 1) {
    		println(i)
      	//10,9,8,7,6,5,4,3,2,1
    }
}
```

降序区间也可结合`step`关键字跳过区间中的某些元素。

# 三、集合

`Kotlin`有以下集合用于分组项目:

| Collection  type | Description                                       |
| ---------------- | ------------------------------------------------- |
| Lists            | 有序集合                                          |
| Sets             | 唯一无序集合                                      |
| Maps             | 键-值对的集合，其中键是唯一的，并且只映射到一个值 |

## 3.1 List 

```kotlin
// 只读列表
val readOnlyShapes = listOf("triangle", "square", "circle")
println(readOnlyShapes)	// [triangle, square, circle]

// 具有显式类型声明的可变列表
val shapes: MutableList<String> = mutableListOf("triangle", "square", "circle")
println(shapes)	// [triangle, square, circle]
```

为了防止不必要的修改，您可以通过将可变列表分配给以下方式来获取可变列表的只读视图List：

```kotlin
val shapes: MutableList<String> = mutableListOf("triangle", "square", "circle")
val shapesLocked: List<String> = shapes
```

这也称为**铸造**。

列表是有序的，因此要访问列表中的项目，请使用[索引访问运算符](https://kotlinlang.org/docs/operator-overloading.html#indexed-access-operator) `[]`：

```kotlin
    val readOnlyShapes = listOf("三角形", "正方形", "圆形")
    println("列表中的第一项是: ${readOnlyShapes[0]}")
    // 列表中的第一项是: 三角形
```

要获取列表中的第一项或最后一项，请分别使用[.first()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/first.html)和[.last()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/last.html)函数：

```kotlin
val readOnlyShapes = listOf("三角形", "正方形", "圆形")
println("列表中的第一项: ${readOnlyShapes.first()}")
// 列表中的第一项: 三角形
```

要获取列表中的项目数，请使用以下[.count()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/count.html)函数：

```kotlin
val readOnlyShapes = listOf("三角形", "正方形", "圆形")
println("列表一共包含 ${readOnlyShapes.count()} 项")
// 列表一共包含3项
```

要检查某个项目是否在列表中，请使用[in运算符](https://kotlinlang.org/docs/operator-overloading.html#in-operator)：

```kotlin
val readOnlyShapes = listOf("三角形", "正方形", "圆形")
println("圆形" in readOnlyShapes)
// true
```

要从可变列表中添加或删除项目，请分别使用[.add()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-list/add.html)和[.remove()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/remove.html)函数：

```kotlin
val shapes: MutableList<String> = mutableListOf("三角形", "正方形", "圆形")
// 添加 "五角形" 进列表
shapes.add("五角形") 
println(shapes)  
// [三角形, 正方形, 圆形, 五角形]

// 从列表中删除第一个 "五角形"
shapes.remove("五角形") 
println(shapes)  
// [三角形, 正方形, 圆形]
```

## 3.2 Set

列表是有序的，允许重复的项目，而集合是无序的，只存储唯一的项目。 

要创建一个只读集`set`，使用`setOf()`函数。 

要创建可变集`MutableSet`，请使用`mutableSetOf()`函数。 

在创建集合时，`Kotlin`可以推断存储项的类型。要显式声明类型，请在`set`声明后的尖括号`<>`中添加类型:

```kotlin
// 只读
val readOnlyFruit = setOf("apple", "banana", "cherry", "cherry")
// 具有显示声明的可变集
val fruit: MutableSet<String> = mutableSetOf("apple", "banana", "cherry", "cherry")

println(readOnlyFruit)
// [apple, banana, cherry]
```

为了防止不必要的修改，通过将可变集强制转换为`Set`来获得它们的只读视图:

```kotlin
val fruit: MutableSet<String> = mutableSetOf("apple", "banana", "cherry", "cherry")
val fruitLocked: Set<String> = fruit
```

由于集合是无序的，所以不能访问特定索引处的项。但是获取长度以及增加和删除元素的方法是和`List`一致。

## 3.3 Map

要创建只读映射`Map`，请使用该`mapOf()`函数。

要创建可变映射`MutableMap`，请使用该`mutableMapOf`函数。

创建映射时，`Kotlin` 可以推断存储的项目的类型。`<>`要显式声明类型，请在映射声明后的尖括号内添加键和值的类型。例如：`MutableMap<String, Int>`。键具有 `type String`，值具有` type Int`。

`to`创建映射的最简单方法是在每个键及其相关值之间使用：

```kotlin
// 只读
val readOnlyJuiceMenu = mapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
println(readOnlyJuiceMenu)
// {apple=100, kiwi=190, orange=100}

// 显示声明可变的Map
val juiceMenu: MutableMap<String, Int> = mutableMapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
println(juiceMenu)
// {apple=100, kiwi=190, orange=100}
```

为了防止不必要的修改，我们也可以通过将可变映射转换为以下方式来获取可变映射的只读视图Map

要访问映射中的值，请使用[索引访问运算符](https://kotlinlang.org/docs/operator-overloading.html#indexed-access-operator) `[]`及其键：

```kotlin
val readOnlyJuiceMenu = mapOf("苹果" to 100, "奇异果" to 190, "橘子" to 100)
println("苹果对应的价格为: ${readOnlyJuiceMenu["苹果"]}")
// 苹果对应的价格为: 100
```

要获取`Map`中的项目数，使用[.count()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/count.html)函数

要从可变映射中添加或删除项目，请分别使用[.put()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-map/put.html)和[.remove()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/remove.html)函数

```kotlin
val juiceMenu: MutableMap<String, Int> = mutableMapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
juiceMenu.put("coconut", 150)
println(juiceMenu)
// {apple=100, kiwi=190, orange=100, coconut=150}

juiceMenu.remove("orange")
println(juiceMenu)
// {apple=100, kiwi=190, coconut=150}
```

要检查特定键是否已包含在映射中，请使用以下[.containsKey()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/contains-key.html)函数

要获取映射的键或值的集合，请分别使用[keys](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-map/keys.html)和[values](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-map/values.html)属性：

```kotlin
val readOnlyJuiceMenu = mapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
println(readOnlyJuiceMenu.keys)
// [apple, kiwi, orange]
println(readOnlyJuiceMenu.values)
// [100, 190, 100]
```

# 四、函数

使用`fun`关键字声明函数

```kotlin
fun hello() {
  	return println("Hello, world!")
}

fun main() {
  	hello()	//Hello,world!
}
```

在`Kotlin`中：

- 方法参数写在`()`内部

- 每个参数必须指定类型，多个参数必须通过逗号`，`分离

- 返回类型需要写在方法的`()`后面，通过冒号`：`分离

- 函数体需要写在花括号内`{}`

- `return`关键字用于结束函数，或者从函数中返回某个值。

  如果一个函数并不需要返回任何有用的值，那么我们可以不写返回类型和 `return` 关键字。

例子：

- `x`和`y`是函数的参数
- `x`和`y`的参数类型为`Int`
- 函数返回类型为`Int`
- 函数返回`x`和`y`的和

```kotlin
fun sum(x: Int, y: Int): Int {
    return x + y
}

fun main() {
    println(sum(1, 2))	// 3
}
```

## 4.1 默认参数值

你可以为函数参数设定默认值。当调用函数时，任何设置了默认值的参数都可以不用写出来。要设定默认值，只需在参数类型后面用等号`=`赋值即可。

```kotlin
fun printMessageWithPrefix(message: String, name: String = "李四") {
    println("[$name]: $message")
}

fun main() {
    printMessageWithPrefix("你好", "张三")	//[张三]: 你好
    
    printMessageWithPrefix("你好")	//[李四]: 你好
    
    printMessageWithPrefix(name = "王五", message = "你好")	//[王五]: 你好
}
```

重写的方法会使用基础方法设定的默认参数值。重写一个设有默认参数值的方法时，这些默认值在新的方法签名中必须被省略：

```kotlin
open class A {
    open fun foo(i: Int = 10) { /*...*/ }
}

class B : A() {
    override fun foo(i: Int) { println(i) }  // No default value is allowed.
}

fun main() {
  	val obj = B()
  	obj.foo()	//10
  	obj.foo(1)	//1
}
```

如果一个设有默认值的参数位于没有默认值的参数之前，那么只有在使用命名参数调用函数时，这个默认值才会被使用：

```kotlin
fun foo(
    bar: Int = 0,
    baz: Int,
) { println("bar = $bar, baz = $baz") }

fun main() {
  	foo(baz = 1) // bar = 0, baz = 1
  	foo(1)	//No value passed for parameter 'baz'
}
```

如果在默认参数之后的最后一个参数是一个 lambda 函数，你既可以将其作为一个具名参数来传递，也可以将其放在括号之外来传递：

```kotlin
fun foo(
    bar: Int = 0,
    baz: Int = 1,
    qux: () -> String,
) {
    println("bar = $bar, baz = $baz, qux = ${qux()}")
}

fun main() {
    foo { "hello" }            // bar = 0, baz = 1, qux = hello
    foo(1) { "hello" }     // bar = 1, baz = 1, qux = hello
    foo(qux = { "hello" })     // bar = 0, baz = 1, qux = hello
}
```

## 4.2 命名参数

如果你想让代码更简洁，调用函数时就不需要包含参数名称。但是，包含参数名称可以让你的代码更易于阅读，这种方式被称为使用命名参数。如果你选择使用参数名称，那么参数的顺序就不再固定，可以随意排列。

```kotlin
fun printMessageWithPrefix(message: String, prefix: String) {
    println("[$prefix] $message")
}

fun main() {
    printMessageWithPrefix(prefix = "Log", message = "Hello")	// [Log] Hello
}
```

在调用函数时，你可以为一个或多个函数的参数命名。这在函数有很多参数，且难以将某个值与特定参数对应起来时，特别有用，尤其是当参数是布尔值或空值的情况。

在函数调用中使用命名参数时，你可以自由地调整它们的排列顺序。如果你想使用参数的默认值，那么你可以直接忽略这些参数。

以 `reformat()` 函数为例，它有 4 个带有默认值的参数。

```kotlin
fun reformat(
    str: String,
    normalizeCase: Boolean = true,
    upperCaseFirstLetter: Boolean = true,
    divideByCamelHumps: Boolean = false,
    wordSeparator: Char = ' ',
) { /*...*/ }
```

调用这个函数时，你并不需要为所有参数都命名：

```kotlin
reformat(
    "String!",
    false,
    upperCaseFirstLetter = false,
    divideByCamelHumps = true,
    '_'
)
```

也可以忽略所有带有默认值的参数：

```kotlin
reformat("This is a long String!")
```

也可以选择性地忽略具有默认值的一些参数，而不是全部省略。一旦你跳过了一个参数，那么你必须为之后的所有参数都命名：

```kotlin
reformat("This is a short String!", upperCaseFirstLetter = false, wordSeparator = '_')
```

也可以利用扩展运算符传递带有名称的不定数量的参数`vararg`：

```kotlin
fun <T> asList(vararg ts: T): List<T> {
    val result = ArrayList<T>()
    for (t in ts) // ts is an Array
        result.add(t)
    return result
}

fun main() {
    val list = asList(1, 2, 3,"ok")
}
```

> 注意：当你在 `JVM` 上执行 `Java` 函数时，由于 `Java` 字节码并不总是会保存函数参数的名称，所以你不能使用命名参数的语法。

在函数内部，类型为 `T` 的变长参数`vararg`会被视作 `T` 类型的数组，就像上述例子中，`ts` 变量被视作 `Array<out T>` 类型。 

这里解释一下``Array<out T>` `。

1. 协变：在解释它之前我们需要先明白一个概念**协变**，在泛型编程中，协变描述了一个关系，其中一个类可以接受另一个类或其子类作为泛型参数。这意味着如果 `B` 是 `A` 的子类型，那么 `Container<B>` 也可以被视为 `Container<A>` 的子类型。
2. **`out` 关键字**
   * 在 `Kotlin` 中，`out` 关键字用于指定一个泛型类型参数是协变的。这意味着泛型类型参数只能作为返回值，而不能作为函数的入参。可以把 `out` 理解为“只能输出，不能输入”的含义。

`Array<out T>` 类型

1. **使用场景**
   - `Array<out T>` 是一个使用 `out` 修饰符声明的数组，它表明这个数组可以安全地持有给定类型 `T` 或其任何子类型的元素。这种用法在需要传递一个数组，而数组元素类型是某个类的子类型时特别有用。
2. **协变数组的特点**
   - 由于 `out` 修饰符的限制，`Array<out T>` 只能被用来从数组中读取 `T` 类型的数据，而不能用来写入 `T` 类型的数据。这是为了保证类型安全，防止将错误类型的对象放入数组中。
3. **类型安全**
   - 这种限制确保了类型安全，因为你可以确信从 `Array<out T>` 中读取的每个元素都是 `T` 类型或其子类型。这样就不会出现类型转换异常。

上述示例代码中，在 `main` 函数中调用 `asList` 时，传递了整数和字符串作为参数。`Kotlin` 编译器会根据传递的参数推断泛型 `T` 的类型。在这个例子中，由于参数列表包含不同类型，`T` 的推断类型将是它们的最近公共祖先，在 `Kotlin` 中是 `Any` 类型。

只有一个参数可以被标记为变长参数。如果变长参数不是参数列表中的最后一个，那么后续参数的值可以通过命名参数语法传递，或者，如果参数是函数类型，可以通过在括号外部传递 `lambda` 表达式。

当你调用一个变长参数的函数时，你可以逐个传递参数，例如 `asList(1, 2, 3)`。如果你已经有一个数组并想将其内容传递给函数，那么就使用扩展运算符（在数组前加 `*`）：

```kotlin
val a = arrayOf(1, 2, 3)
val list = asList(-1, 0, *a, 4)
```

如果你需要将基本类型的数组传入变长参数，你需要用 `toTypedArray()` 函数将其转化为常规的（有类型的）数组：

```kotlin
val a = intArrayOf(1, 2, 3) // IntArray is a primitive type array
val list = asList(-1, 0, *a.toTypedArray(), 4)
```

## 4.3 没有返回值的函数

函数不需要返回任何具体的值，那么它的返回类型就是 `Unit`。`Unit` 是一个只有一个值的类型，那就是 `Unit` 自己。在编写函数时，你并不需要显式地声明函数返回 `Unit`。也就是说，你不需要使用 `return` 关键字，也不需要声明返回类型：

```kotlin
fun printMessage(message: String) {
    println(message)	// `return Unit` or `return` is optional
}

fun main() {
    printMessage("Hello")	// Hello
}
```

## 4.4 中缀表示法

标记为 `infix` 关键字的函数也可以使用中缀表示法进行调用（调用时省略点和括号）。中缀函数需要满足以下条件：

* 函数必须是成员函数或者是扩展函数。
* 函数只能有一个参数。
* 参数不能接收可变数量的参数，也不能设置默认值。

```kotlin
infix fun Int.shle(x: Int): Int {
    return x
}

fun main() {
    println(1 shle 2)
    1.shle(2) //和上面等价
}
```

> 注意：
>
> 中缀函数调用的优先级比算术运算符、类型转换和 `rangeTo` 运算符的优先级要低。以下的表达式是相等的：
>
> * `1 shl 2 + 3` 和 `1 shl (2 + 3)` 是等同的
> * `0 until n * 2` 和 `0 until (n * 2)` 是等同的
>
> * `xs union ys as Set<*>` 和 `xs union (ys as Set<*>)` 是等同的
>
> 另一方面，中缀函数调用的优先级比布尔运算符 `&&` 和 `||`，`is-` 和 `in-`检查，以及一些其他运算符的优先级要高。以下的表达式也是相等的：
>
> * `a && b xor c` 和 `a && (b xor c)` 是等同的
>
> * `a xor b in c` 和 `(a xor b) in c` 是等同的

需要注意的是，中缀函数总是需要明确指定接收者和参数。当你想要在当前接收者上使用中缀表示法调用方法时，需要显式地使用 `this`。这样做是为了确保解析的无歧义性。

```kotlin
class MyStringCollection {
    infix fun add(s: String) { /*...*/ }

    fun build() {
        this add "abc"   // Correct
        add("abc")       // Correct
        //add "abc"        // Incorrect: the receiver must be specified
    }
}
```

## 4.5 函数表达式

确保代码更加简洁，我们可以使用函数表达式，例如我们可以将`sum`函数简化:

```kotlin
//简化前
fun sum(x: Int, y: Int): Int {
  	return x + y
}
//简化后
//你可以不使用大括号 {} ，而是用等号 = 来定义函数的内容。
//并且，因为 Kotlin 有类型推断功能，你甚至可以不写返回类型。这样，sum() 函数就可以简化为一行代码：
fun sum(x: Int, y: Int) = x + y

fun main() {
  	println(sum(1, 2)) //3
}
```

## 4.6 高阶函数

高阶函数是指可以将函数作为参数，或者将函数作为返回结果的函数。

一个典型的高阶函数例子是用于集合的函数式编程惯用法 `fold`。这个函数接受一个初始的累加值和一个组合函数，然后通过连续地将当前的累加值和每一个集合元素进行组合并替换累加值，从而构建出返回值。

```kotlin
fun <T, R> Collection<T>.fold(
    initial: R,
    combine: (acc: R, nextElement: T) -> R
): R {
    var accumulator: R = initial
    for (element: T in this) {
        accumulator = combine(accumulator, element)
    }
    return accumulator
}
```

在上面的代码中，`combine` 参数的函数类型是 `(R, T) -> R`，这意味着它接受一个函数，这个函数接收两个类型为 `R` 和 `T` 的参数，并返回一个类型为 `R` 的值。这个函数在 `for` 循环中被调用，然后返回值被赋给了累加器。

要调用 `fold`，你需要将一个函数类型的实例作为参数传给它。在高阶函数的调用中，`lambda` 表达式（下面会有更详细的描述）被广泛用于这个目的：

```kotlin
fun main() {
    val items = listOf(1, 2, 3, 4, 5)

    // Lambda 表达式就是被大括号包围的代码段。
    items.fold(0, { 
        // 当一个 lambda 表达式有参数时，参数会先写出来，然后跟着 '->' 符号
        acc: Int, i: Int -> 
        print("acc = $acc, i = $i, ") 
        val result = acc + i
        println("result = $result")
        // 在 lambda 表达式中，最后一个表达式会被视为返回值。
        result
    })

    // 在 lambda 表达式中，如果参数类型可以被推断出来，那么参数类型就不是必需的。
    val joinedToString = items.fold("Elements:", { acc, i -> acc + " " + i })

    // 我们也可以使用函数引用来进行高阶函数的调用。
    val product = items.fold(1, Int::times)

    println("joinedToString = $joinedToString")
  	//joinedToString = Elements: 1 2 3 4 5
    println("product = $product")
  	//product = 120
}
```

## 4.7 Lambda 表达式

在 `Kotlin` 中，你可以使用` lambda `表达式来让函数的代码更加简洁。

比如，下面这个 `uppercaseString() `函数：

```kotlin
fun uppercaseString(string: String): String {
    return string.uppercase()
}

fun main() {
    println(uppercaseString("hello"))
    // HELLO
}
```

写成`lambda`表达式以后

```kotlin
fun main() {
    println({ string: String -> string.uppercase() }("hello"))
    // HELLO
}
```

`Lambda` 表达式一看上去可能有些复杂，所以我们来一步步解析。`Lambda` 表达式是写在大括号 `{}` 中的。

在 `lambda` 表达式中，你需要这样写：

- 先写参数，然后是一个` ->`。

- 在 `->` 后面写函数的主体。

在之前的例子中：

- `string` 是一个函数的参数。

- `string` 的类型是 `String`。

- 函数返回的是 `string` 上调用的 `.uppercase()` 函数的结果。

如果你定义的 `lambda` 表达式没有参数，那么就无需使用 `->`。比如说：

```kotlin
{ println("Log message") }
```

`Lambda` 表达式的使用方式多种多样。你可以：

- 把一个 `lambda` 表达式赋值给一个变量，之后再调用这个变量
- 把一个 `lambda` 表达式作为参数，传给另一个函数
- 在一个函数中返回一个 `lambda` 表达式
- 直接调用一个 `lambda` 表达式

### 4.7.1 赋值给变量

```kotlin
fun main() {
    val upperCaseString = { string: String -> string.uppercase() }
    println(upperCaseString("hello"))	// HELLO
}
```

### 4.7.2 传递给另外一个函数

在数据集合上使用 `.filter()` 函数：

```kotlin
fun main() {
    val numbers = listOf(1, -2, 3, -4, 5, -6)
    val positives = numbers.filter { x -> x > 0 }
    val negatives = numbers.filter { x -> x < 0 }
    println(positives)	// [1, 3, 5]
    println(negatives)	// [-2, -4, -6]
}
```

`.filter()` 函数会接收一个 `lambda` 表达式作为条件：

- `{ x -> x > 0 }` 这个表达式会检查列表中的每个元素，只保留那些大于零的。
- `{ x -> x < 0 }` 这个表达式会检查列表中的每个元素，只保留那些小于零的。

如果 `lambda` 表达式是函数的唯一参数，你可以省去函数的括号 `()`。这就是我们所说的**尾随 `lambda`**，我们会在最后进行更详细的讨论。

还有一个很好的例子，就是用` .map() `函数来改变集合中的元素：

```kotlin
fun main() {
    val numbers = listOf(1, -2, 3, -4, 5, -6)
    val doubled = numbers.map { x -> x * 2 }
    val tripled = numbers.map { x -> x * 3 }
    println(doubled)	// [2, -4, 6, -8, 10, -12]
    println(tripled)	// [3, -6, 9, -12, 15, -18]
}
```

`.map()` 函数会接受一个 `lambda` 表达式作为转换函数：

- `{ x -> x * 2 }` 会把列表中的每个元素都乘以 2。
- `{ x -> x * 3 }` 会把列表中的每个元素都乘以 3。

### 4.7.3 函数类型

在你能从函数中返回 `lambda` 表达式之前，你得先理解什么是函数类型。

你已经学过了基础类型，但是函数本身也有类型。`Kotlin` 的类型推断可以从参数类型推断出函数的类型。但有时候你可能需要明确指定函数类型。编译器需要知道函数类型，以便知道什么是该函数允许的，什么是不允许的。

函数类型的语法包括：

- 每个参数的类型都写在括号` ()` 内，并用逗号 , 分隔。
- 返回类型写在` ->` 之后。

例如：`(String) -> String` 或 `(Int, Int) -> Int`。

如果为 `upperCaseString()` 定义了函数类型，那么 `lambda` 表达式就会是这样的：

```kotlin
val upperCaseString: (String) -> String = { string -> string.uppercase() }

fun main() {
    println(upperCaseString("hello"))	// HELLO
}
```

如果你的 `lambda` 表达式没有参数，那么你就留空括号 `()`。例如：`() -> Unit`

要表明一个函数类型是可空的，可以这样使用括号：`((Int, Int) -> Int)?`。

函数类型也可以用括号进行组合：`(Int) -> ((Int) -> Unit)`。

箭头表示法是右关联的，`(Int) -> (Int) -> Unit` 和前面的例子等价，但与` ((Int) -> (Int)) -> Unit `不等价。

也可以通过使用类型别名给函数类型提供一个替代名称：

```kotlin
typealias ClickHandler = (Button, ClickEvent) -> Unit
```

#### 实例化函数类型

有几种方法可以获得函数类型的实例：

* 在函数字面量中使用代码块，可以采取以下形式：

  * 一个 `lambda` 表达式：`{ a, b -> a + b }`，
  * 一个匿名函数：`fun(s: String): Int { return s.toIntOrNull() ?: 0 }`

  带有接收器的函数字面量可以用作带有接收器的函数类型的值。

* 使用现有声明的可调用引用：

  * 顶级、局部、成员或扩展函数：`::isOdd, String::toInt`，
  * 顶级、成员或扩展属性：`List<Int>::size`，
  * 构造函数：`::Regex`

  这些包括绑定到特定实例成员的可调用引用：`foo::toString`。

* 使用实现了函数类型接口的自定义类的实例：

```kotlin
class IntTransformer: (Int) -> Int {
    override operator fun invoke(x: Int): Int = TODO()
}

val intFunction: (Int) -> Int = IntTransformer()
```

如果有足够的信息，编译器可以推断变量的函数类型：

```kotlin
val a = { i: Int -> i + 1 } // 推断出的类型为：(Int) -> Int
```

无论是带有接收器还是不带接收器的函数类型，只要不是文字值，都可以互相替换。也就是说，接收器可以作为第一个参数，反过来也一样。比如，我们可以在需要 `A.(B) -> C` 类型的地方，传递或赋值 `(A, B) -> C` 类型的值，反之亦然：

```kotlin
fun main() {
    val repeatFun: String.(Int) -> String = { times -> this.repeat(times) }
    val twoParameters: (String, Int) -> String = repeatFun // OK

    fun runTransformation(f: (String, Int) -> String): String {
        return f("hello", 3)
    }
    val result = runTransformation(repeatFun) // OK

    println("result = $result")
  	//result = hellohellohello
}
```

#### 调用函数类型的实例

函数类型的值可以通过使用它的 `invoke(...)` 操作符进行调用，比如：`f.invoke(x)` 或者简单地使用 `f(x)`。

如果这个值有一个接收器类型，那么接收器对象应当作为第一个参数传入。另外，如果一个函数类型的值有接收器，我们还可以通过在它前面添加接收器对象的方式来调用它，就像它是一个扩展函数一样，例如：`1.foo(2)`。

例如：

```kotlin
fun main() {
    val stringPlus: (String, String) -> String = String::plus
    val intPlus: Int.(Int) -> Int = Int::plus

    println(stringPlus.invoke("<-", "->"))	//<-->
    println(stringPlus("Hello, ", "world!"))	//Hello, world!

    println(intPlus.invoke(1, 1))	//2
    println(intPlus(1, 2))	//3
    println(2.intPlus(3)) // 5

}
```

### 4.7.4 返回lambda表达式

你可以从函数中返回 `Lambda` 表达式。为了让编译器明白返回的 `Lambda` 表达式的类型，你需要声明一个函数类型。

在下面的例子中，`toSeconds()` 函数的类型是 `(Int) -> Int`，因为它总是返回一个接受 `Int` 类型参数并返回 `Int` 类型结果的 `Lambda` 表达式。

这个例子使用了 `when` 表达式来决定在调用 `toSeconds()` 时返回哪个 `Lambda` 表达式：

```kotlin
fun toSeconds(time: String): (Int) -> Int = when (time) {
    "hour" -> { value -> value * 60 * 60 }
    "minute" -> { value -> value * 60 }
    "second" -> { value -> value }
    else -> { value -> value }
}

fun main() {
    val timesInMinutes = listOf(2, 10, 15, 1)
    val min2sec = toSeconds("minute")
    val totalTimeInSeconds = timesInMinutes.map(min2sec).sum()
    println("Total time is $totalTimeInSeconds secs")
    // Total time is 1680 secs
}
```

### 4.7.5 立即调用

你可以通过在大括号 `{}` 后面加上圆括号` ()`，并把参数放在圆括号里面，来立即调用 `Lambda` 表达式：

```kotlin
fun main() {
    println({ string: String -> string.uppercase() }("hello"))	// HELLO
}
```

### 4.7.6 尾部的 `Lambda` 表达式 

如你所见，如果 `Lambda` 表达式是函数的唯一参数，你可以省略函数的圆括号` ()`。如果 `Lambda` 表达式作为函数的最后一个参数，那么这个表达式可以写在函数的圆括号` ()` 外面。在这两种情况下，这种语法被称为尾部的 `Lambda`。

举个例子，`.fold() `函数需要一个初始值和一个操作：

```kotlin
// 初始值为0.
// 这个操作会把初始值和列表中的每一个元素逐一相加.
println(listOf(1, 2, 3).fold(0, { x, item -> x + item })) // 6

// 或者，用尾部 Lambda 的方式
println(listOf(1, 2, 3).fold(0) { x, item -> x + item })  // 6
```

## 4.8 函数作用域

在 `Kotlin` 中，函数可以在文件的最顶端声明，这就意味着你无需像在 `Java`、`C#` 和 `Scala`（`Scala 3` 开始支持顶层定义）等语言中那样，需要创建一个类来承载函数。除了顶层函数，`Kotlin` 还允许在本地声明函数作为成员函数和扩展函数。

本地函数

`Kotlin` 支持本地函数，这些函数是嵌套在其他函数内部的：

```kotlin
fun dfs(graph: Graph) {
    fun dfs(current: Vertex, visited: MutableSet<Vertex>) {
        if (!visited.add(current)) return
        for (v in current.neighbors)
            dfs(v, visited)
    }

    dfs(graph.vertices[0], HashSet())
}
```

本地函数可以访问外层函数的本地变量（也就是闭包）。在下面的例子中，`visited` 就可以是一个本地变量：

```kotlin
fun dfs(graph: Graph) {
    val visited = HashSet<Vertex>()
    fun dfs(current: Vertex) {
        if (!visited.add(current)) return
        for (v in current.neighbors)
            dfs(v)
    }

    dfs(graph.vertices[0])
}
```

## 4.9 泛型函数

函数可以有泛型参数，这些参数在函数名称前使用尖括号指定

```kotlin
fun <T> singletonList(item: T): List<T> { /*...*/ }
```

## 4.10 尾部递归函数

`kotlin` 支持一种叫做尾递归的函数式编程方式。对于一些通常会使用循环的算法，你可以选择使用递归函数，而不必担心栈溢出的风险。当一个函数被标记为 `tailrec` 修饰符并满足一定的形式条件时，编译器会把递归部分优化掉，替换为一个快速且高效的循环版本：

```kotlin
val eps = 1E-10 // "good enough", could be 10^-15

tailrec fun findFixPoint(x: Double = 1.0): Double =
    if (Math.abs(x - Math.cos(x)) < eps) x else findFixPoint(Math.cos(x))
```

这段代码是计算余弦函数的不动点，这是一个数学常量。它简单地从1.0开始反复调用 `Math.cos`，直到结果不再变化，对于给定的 `eps` 精度，得到的结果是0.7390851332151611。最后生成的代码和以下这种更常见的编程风格是等价的：

```kotlin
val eps = 1E-10 // "good enough", could be 10^-15

private fun findFixPoint(): Double {
    var x = 1.0
    while (true) {
        val y = Math.cos(x)
        if (Math.abs(x - y) < eps) return x
        x = Math.cos(x)
    }
}
```

要使用 `tailrec` 修饰符，函数必须在其执行的最后一步调用自身。如果在递归调用后还有其他代码，或者在 `try/catch/finally` 代码块中，或者在开放函数中使用，都不能使用尾递归。目前，`Kotlin` 支持 `JVM` 和 `Kotlin/Native` 的尾递归。

## 4.11 闭包

`Lambda` 表达式或者匿名函数（还有局部函数和对象表达式）能够访问它的闭包，这个闭包包含了在外部作用域声明的变量。在闭包中被捕获的变量可以在 `lambda` 表达式中被修改：

```kotlin
var sum = 0
ints.filter { it > 0 }.forEach {
    sum += it
}
print(sum)
```

## 4.12 带接收者的函数字面量

 像 `A.(B) -> C` 这样带接收者的函数类型，可以用一种特殊的函数字面量——带接收者的函数字面量来实例化。

如前所述，`Kotlin` 提供了在给出接收者对象的同时调用带接收者的函数类型实例的能力。

在函数字面量的主体中，传递给调用的接收者对象变成了隐式的 `this`，所以你可以无需任何额外的限定符就可以访问该接收者对象的成员，或者使用` this` 表达式来访问接收者对象。

这种行为和扩展函数的行为相似，扩展函数也允许你在函数体内访问接收者对象的成员。

下面是一个带接收者的函数字面量及其类型的例子，在这个例子中，`plus` 是在接收者对象上被调用的：

```kotlin
val sum: Int.(Int) -> Int = { other -> plus(other) }
```

匿名函数的语法让你可以直接设定函数字面量的接收者类型。如果你需要声明一个带有接收者类型的函数变量，然后在后面的代码中使用它，这个功能会非常实用。

```kotlin
val sum = fun Int.(other: Int): Int = this + other
```

当接收者类型可以从上下文中推断出来时，`Lambda` 表达式可以作为带接收者的函数字面量使用。它们的一个最重要的应用实例就是类型安全的构建器：

```kotlin
class HTML {
    fun body() { ... }
}

fun html(init: HTML.() -> Unit): HTML {
    val html = HTML()  // 创建接收者对象
    html.init()        // 把接收者传递给lambda表达式
    return html
}

html {       // 带有接收者的 lambda 表达式从这里开始
    body()   // 对接收者对象执行方法调用
}
```

##  4.13 内联函数

使用高级函数会有一些运行时的代价：每个函数都是一个对象，并且它会捕获一个闭包。闭包是可以在函数体内被访问的一组变量。为函数对象和类进行内存分配，以及进行虚拟调用，都会产生运行时的额外开销。

然而，似乎在许多情况下，这种开销可以通过内联 `lambda `表达式来消除。下面展示的函数就是这种情况的很好例子。`lock() `函数可以轻松地在调用处进行内联。考虑以下情况：

```kotlin
lock(l) { foo() }
```

编译器可以输出以下代码，而不是创建一个函数对象作为参数并生成一个调用：

```kotlin
l.lock()
try {
    foo()
} finally {
    l.unlock()
}
```

要让编译器这样做，就要给 `lock()` 函数加上 `inline` 修饰符：

```kotlin
inline fun <T> lock(lock: Lock, body: () -> T): T {
  	lock.lock()
    try {
        return body()
    } finally {
        lock.unlock()
    }
}    
// 使用示例
val result = lock(myLock) {
    // ... 执行一些操作
}
```

`inline` 修饰符不仅影响函数本身，还影响传给它的 `lambda` 表达式：所有这些都会被嵌入到调用位置。

虽然内联可能会让生成的代码变大。但是，如果你能合理地使用它（避免对大函数进行内联），它会在性能上带来回报，尤其是在循环中的 `"megamorphic"` 调用位置。

### noinline修饰符

如果你不想让所有传给 `inline` 函数的 `lambda` 表达式都被嵌入，那就在你的一些函数参数上加上 `noinline` 修饰符：

```kotlin
inline fun foo(inlined: () -> Unit, noinline notInlined: () -> Unit) { ... }
```

只有在 `inline` 函数中或作为可内联参数的情况下，才能调用可内联的 `lambda `表达式。但是，对于 `noinline` 的 `lambda` 表达式，你可以随心所欲地操作它们，包括将它们存储在字段中或者传递。

> 如果一个 `inline` 函数既没有可内联的函数参数，也没有实化的类型参数，编译器会发出警告，因为这种情况下的函数内联很可能无法带来任何益处（如果你确信这个函数需要内联，你可以使用 `@Suppress("NOTHING_TO_INLINE")` 注解来消除这个警告）。

### 非局部返回 

在 `Kotlin` 中，你只能在命名函数或匿名函数中使用普通的、没有限定的 `return` 来退出函数。要从 `lambda` 表达式中退出，你需要使用一个标签。在 `lambda` 表达式内部，禁止使用裸露的 `return`，因为 `lambda` 表达式不能让包围它的函数返回：

```kotlin
fun ordinaryFunction(block: () -> Unit) {
    println("hi!")
}
fun foo() {
    ordinaryFunction {
        return // ERROR: cannot make `foo` return here
    }
}
fun main() {
    foo()
}
```

但是，如果把 `lambda` 传递给的函数进行了内联处理，`return` 也可以进行内联处理。因此，这是被允许的：

```kotlin
fun ordinaryFunction(block: () -> Unit) {
    println("hi!")
}
fun foo() {
    inline {
        return // OK: the lambda is inlined
    }
}
fun main() {
    foo()
}
```

这种在 `lambda` 中但退出封闭函数的返回被称为非局部返回。这种情况通常在循环中出现，而这些循环经常包含内联函数：

```kotlin
fun hasZeros(ints: List<Int>): Boolean {
  	ints.forEach {
      if (it == 0) return true
    }
  return false
}
```

注意，一些内联函数可能不是直接从函数体调用作为参数传递给它们的 `lambda`，而是从另一个执行上下文，如本地对象或嵌套函数。在这种情况下，`lambda` 中也不允许非局部控制流。为了指示内联函数的 `lambda` 参数不能使用非局部返回，用 `crossinline` 修饰符标记 `lambda` 参数：

```kotlin
inline fun f(crossinline body: () -> Unit) {
    val f = object: Runnable {
        override fun run() = body() //这里的body不允许使用非局部返回
    }
    // ...
}
//使用示例
f {
  	//...执行一些操作，但不能包含return@f这样的非局部返回
}
```

> 在内联 `lambda` 中，`break` 和 `continue` 目前还不能使用，但我们也计划要支持这两个功能。

### 具体化的类型参数

有时候，你需要获取作为参数传递的类型：

```kotlin
fun <T> TreeNode.findParentOfType(clazz: Class<T>): T? {
    var p = parent
  	//检查当前父节点 p 是否是目标类型 T 的实例。
    while (p != null && !clazz.isInstance(p)) {
        p = p.parent
    }
  	//用于告诉 Kotlin 编译器忽略接下来的未检查转换警告
    @Suppress("UNCHECKED_CAST")
    return p as T?
}
```

在这里，你需要沿着树形结构向上遍历，并用反射来检查一个节点是否是某种特定类型。虽然这样做是可行的，但是调用的代码看起来并不是很优雅：

```kotlin
treeNode.findParentOfType(MyTreeNode::class.java)
```

一个更好的解决方案是直接把类型传递给这个函数。你可以像下面这样调用它：

```kotlin
treeNode.findParentOfType<MyTreeNode>()
```

为了实现这个功能，内联函数支持具体化的类型参数，这就意味着你可以写出如下的代码：

```kotlin
inline fun <reified T> TreeNode.findParentOfType(): T? {
  	var p = parent
  	while (p != null && p !is T) {
      	p = p.parent
    }
  	return p as T?
}
```

上面的代码通过 `reified` 修饰符来明确类型参数，让它在函数内部可以被访问，就像一个普通类一样。由于函数是内联的，所以不需要反射，像 `!is` 和 `as` 这样的常规操作符都可以用。还有，你可以像上面那样调用函数：`myTree.findParentOfType<MyTreeNodeType>()`。

虽然在很多情况下你可能不需要用到反射，但在具体化的类型参数中，你仍然可以使用反射：

```kotlin
inline fun <reified T> membersOf() = T::class.members

fun main(s: Array<String>) {
  	println(membersOf<StringBuilder>().joinToString("\n"))
}
```

在 `Kotlin` 中，泛型类型参数在运行时是被擦除的，这意味着你在编译时可以知道这些类型参数，但在运行时你不能。因此，普通函数（未标记为 `inline`）不能有具体化的类型参数。具体化的类型参数是指在函数内部你能够知道这些类型参数具体是什么类型，并且能够对其进行操作，例如使用 `is` 检查或者 `as` 转换。此外，由于 `Nothing` 和其他非具体化的类型参数在运行时没有具体的表示，它们不能用作具体化类型参数的参数。

### 内联属性

内联修饰符可以用于没有后备字段的属性的访问器。你可以对单个属性访问器进行注解：

```kotlin
val foo: Foo
    inline get() = Foo()

var bar: Bar
    get() = ...
    inline set(v) { ... }
```

你也可以对整个属性进行标注，这样就会将其两个存取器都标记为内联：

```kotlin
inline var bar: Bar
    get() = ...
    set(v) { ... }
```

在调用的位置，内联的存取器就像常规的内联函数一样被内联。

### 公共 API 内联函数的限制

当一个内联函数是公开或受保护的，但并非私有或内部声明的组成部分时，它被认为是模块的公共 `API`。它可以在其他模块中被调用，并在这样的调用点进行内联。

这种情况带来了一定的风险，即如果在更改后没有重新编译调用模块，那么在声明内联函数的模块中进行的更改可能导致二进制不兼容。

为了消除由于模块的非公共 `AP`I 的更改引入的这种不兼容性的风险，公共 `API` 的内联函数不允许在其主体中使用非公共 `API` 的声明，即私有和内部声明以及它们的组成部分。

可以使用 `@PublishedApi` 注解来标注一个内部声明，这样就允许它在公共 `API` 的内联函数中使用。当一个内部内联函数被标记为 `@PublishedApi `时，其主体也会被检查，就好像它是公开的一样。

# 五、类

`Kotlin` 支持面向对象编程，可以创建类和对象。如果要定义一个类，就使用 `class` 关键字：

```kotlin
class Customer
```

类的对象的特性可以通过属性来声明。

- 可以在类中声明属性：

  ```kotlin
  class Contact(val id: Int, var email: String)
  ```

- 可以在类的主体中声明

  ```kotlin
  class Contact(val id: Int, var email: String) {
    	val category: String = "" //推荐将属性设置为只读（val），除非该属性在未来会被更改。
  }
  ```

  你也可以在括号内不用 `val` 或 `var` 来声明属性，但是一旦实例创建后，这些属性就无法访问了。

  括号 `()` 里的内容我们通常称之为类的头部。

  在定义类的属性时，你可以在最后一个属性后加上逗号。

- 类属性也可以设置默认值，这一点与函数参数很相似：

  ```kotlin
  class Contact(val id: Int, var email: String = "example@gmail.com") {
      val category: String = "work"
  }
  ```

## 5.1 创建实例

在 `Kotlin` 中，系统会自动为你创建一个构造函数，这个构造函数的参数就是你在类定义时在类头部声明的参数。

```kotlin
class Contact(val id: Int, var email: String)

fun main() {
    val contact = Contact(1, "mary@gmail.com")
}
```

在 `Kotlin` 中，一个类可以有多个构造函数，这些构造函数中包括你自定义的。

在 `Kotlin` 中，一个类会有一个主要的构造函数，可能还会有一个或者多个次级的构造函数。主要的构造函数是在类的头部声明的，位于类名和可能存在的类型参数之后。

```kotlin
class Person constructor(firstName: String) { /*...*/ }
```

如果主要的构造函数没有任何的注解或者可见性的修饰，那么构造函数的关键字就可以省略。

```kotlin
class Person(firstName: String) { /*...*/ }
```

主构造函数会在类的头部初始化类实例和它的属性，但是类的头部是不能包含任何可以运行的代码的。如果你在对象创建的时候想要运行一些代码，你可以在类的主体中使用初始化块。初始化块是以 `init` 关键字开头，后面跟着一对大括号。你可以在大括号内写下你想要运行的代码。

在一个实例初始化的过程中，初始化块会按照它们在类体中出现的顺序执行，这个过程会和属性初始化器的过程交错进行：

```kotlin
class InitOrderDemo(name: String) {
    val firstProperty = "First property: $name".also(::println)
    
    init {
        println("First initializer block that prints $name")
    }
    
    val secondProperty = "Second property: ${name.length}".also(::println)
    
    init {
        println("Second initializer block that prints ${name.length}")
    }
}

fun main() {
    InitOrderDemo("hello")
}
// First property: hello
// First initializer block that prints hello
// Second property: 5
// Second initializer block that prints 5
```

你也可以在类体中声明的属性初始化器中使用这些参数：

```kotlin
class Customer(name: String) {
    val customerKey = name.uppercase()
}
```

如果你的构造函数有注解或者可见性修饰符，那么你需要使用构造函数关键字，并且这些修饰符要放在关键字前面：

```kotlin
class Customer public @Inject constructor(name: String) { /*...*/ }
```

一个类也可以声明次级构造函数，这些构造函数都以"`constructor`"关键字作为前缀：

```kotlin
class Person(val pets: MutableList<Pet> = mutableListOf())

class Pet {
    constructor(owner: Person) {
        owner.pets.add(this) // adds this pet to the list of its owner's pets
    }
}
```

如果这个类有一个主构造函数，那么每个次级构造函数都需要直接或者通过其他次级构造函数间接地委托给主构造函数。在同一类中，我们可以使用"`this`"关键字来委托给另一个构造函数：

```kotlin
class Person(val name: String) {
    val children: MutableList<Person> = mutableListOf()
    constructor(name: String, parent: Person) : this(name) {
        parent.children.add(this)
    }
}
```

初始化块中的代码实际上就是主构造函数的一部分。当我们开始执行次级构造函数的第一条语句时，就会开始委托给主构造函数。所以，**所有的初始化块和属性初始化的代码都会在次级构造函数的主体执行之前被执行**。

即使这个类没有主构造函数，委托操作仍然会自动进行，而且初始化块也会被执行:

```kotlin
class Constructors {
    init {
        println("Init block")
    }

    constructor(i: Int) {
        println("Constructor $i")
    }
}

fun main() {
    Constructors(1)
}
// 结果：
// Init block
// Constructor 1
```

如果一个非抽象类没有声明任何构造函数（无论是主构造函数还是次级构造函数），那么它将自动生成一个无参数的主构造函数。这个构造函数的可见性将设为公开。

如果你不想让你的类有一个公开的构造函数，那就声明一个非默认可见性的空主构造函数：

```kotlin
class DontCreateMe private constructor() { /*...*/ }
```

在 JVM 中，如果主构造函数的所有参数都设定了默认值，编译器就会生成一个附加的无参数构造函数，这个构造函数会使用这些默认值。这样做是为了方便在使用如 `Jackson` 或 `JPA` 这类通过无参数构造函数创建类实例的库时，能更轻松地使用 `Kotlin`。

## 5.2 属性访问

在实例名后面加上一个点，然后再写上属性名：

```kotlin
class Contact(val id: Int, var email: String)

fun main() {
    val contact = Contact(1, "mary@gmail.com")
    
    println(contact.email)           
    // mary@gmail.com

    contact.email = "jane@gmail.com"
    
    println(contact.email)           
    // jane@gmail.com
}
```

## 5.3 成员方法

可以通过定义成员函数来规定对象的行为。

在 `Kotlin` 语言中，所有的成员函数都需要在类体内部声明。如果你想在一个实例上调用成员函数，你需要在实例名后面加上一个点，然后再写上函数名。例如：

```kotlin
class Contact(val id: Int, var email: String) {
    fun printId() {
        println(id)
    }
}

fun main() {
    val contact = Contact(1, "mary@gmail.com")
    contact.printId()           
    // 1
}
```

## 5.4 内嵌类和内部类

类可以被嵌套在另一个类里：

```kotlin
class Outer {
    private val bar: Int = 1
    class Nested {
        fun foo() = 2
    }
}

val demo = Outer.Nested().foo() // == 2
```

你也可以在嵌套结构中使用接口。类和接口可以以任何方式组合：你可以将接口嵌套在类中，将类嵌套在接口中，或者将接口嵌套在另一个接口中。

```kotlin
interface OuterInterface {
    class InnerClass
    interface InnerInterface
}

class OuterClass {
    class InnerClass
    interface InnerInterface
}
```

被定义为内部的嵌套类可以访问其所在的外部类的成员。内部类会持有一个外部类对象的引用：

```kotlin
class Outer {
    private val bar: Int = 1
    inner class Inner {
        fun foo() = bar
    }
}

val demo = Outer().Inner().foo() // == 1
```

我们通过对象表达式来创建匿名内部类的实例：

```kotlin
window.addMouseListener(object : MouseAdapter() {

    override fun mouseClicked(e: MouseEvent) { ... }

    override fun mouseEntered(e: MouseEvent) { ... }
})
```

对象表达式用于创建匿名类的对象，也就是那些没有通过类声明明确定义的类。这种类型的类对于一次性使用非常实用。你可以从零开始定义它们，从已有的类继承，或者实现接口。由于这些匿名类的实例是由表达式定义的，而不是名字，所以它们也被称为匿名对象。

## 5.5 对象表达式

### 5.5.1 创建匿名对象

对象表达式的开头是`object`关键字。

如果你只需要一个没有复杂超类的对象，那么就把它的成员写在 `object` 关键字后面的大括号里。

```kotlin
fun main() {
    val helloWorld = object {
        val hello = "Hello"
        val world = "World"
        // 对象表达式是 Any 的扩展，因此需要在 toString() 方法上使用 override 关键字。
        override fun toString() = "$hello $world"
    }

    print(helloWorld)
}
```

### 5.5.2 从上级类型继承匿名对象

如果上级类型有构造函数，就向它传递合适的构造参数。你可以在冒号后面用逗号分隔的列表来指定多个上级类型：

```kotlin
open class A(x: Int) {
    public open val y: Int = x
}

interface B { /*...*/ }

val ab: A = object : A(1), B {
    override val y = 15
}
```

### 5.5.3 使用匿名对象作为返回值和变量类型

当我们在局部或私有声明（但不是内联声明）中使用匿名对象作为类型时，我们可以通过这个函数或属性来访问该匿名对象的所有成员：

```kotlin
class C {
    private fun getObject() = object {
        val x: String = "x"
    }

    fun printX() {
        println(getObject().x)
    }
}
```

如果这个函数或属性是公开的或者是私有的内联，那么它的实际类型将是：

- 如果匿名对象没有明确声明的超类型，那么其实际类型就是 `Any`
- 如果匿名对象只有一个明确声明的超类型，那么其实际类型就是这个超类型
- 如果匿名对象有多个明确声明的超类型，那么其实际类型就是明确声明的类型

在所有这些情况下，你都无法访问到匿名对象中新添加的成员。但是，如果你在函数或属性的实际类型中声明了被重写的成员，那么你就可以访问这些成员：

```kotlin
interface A {
    fun funFromA() {}
}
interface B

class C {
    // 返回的数据类型是 Any，而变量 x 是无法访问的。
    fun getObject() = object {
        val x: String = "x"
    }

    // 返回类型为A; x 不可访问
    fun getObjectA() = object: A {
        override fun funFromA() {}
        val x: String = "x"
    }

    // 返回类型是B; funFromA() 和 x 补课访问
    fun getObjectB(): B = object: A, B { // explicit return type is required
        override fun funFromA() {}
        val x: String = "x"
    }
}
```

### 5.5.4 访问匿名对象中的变量

对象表达式中的代码可以获取到其外部作用域中的变量：

```kotlin
fun countClicks(window: JComponent) {
    var clickCount = 0
    var enterCount = 0

    window.addMouseListener(object : MouseAdapter() {
        override fun mouseClicked(e: MouseEvent) {
            clickCount++
        }

        override fun mouseEntered(e: MouseEvent) {
            enterCount++
        }
    })
    // ...
}
```

## 5.6 对象声明

单例模式在许多场景下都很实用，而 Kotlin 提供了便捷的方式来创建单例：

```kotlin
object DataProviderManager {
    fun registerDataProvider(provider: DataProvider) {
        // ...
    }

    val allDataProviders: Collection<DataProvider>
        get() = // ...
}
```

这就是所谓的对象声明，它总是在 `object` 关键字后接一个名称。就像变量声明那样，对象声明并不是一个表达式，因此不能放在赋值语句的右边。

对象声明的初始化过程是线程安全的，只有在第一次访问时才会进行。

如果你想引用这个对象，直接使用它的名字就可以了：

```kotlin
DataProviderManager.registerDataProvider(...)
```

对象也可以具有上级类型：

```kotlin
object DefaultListener : MouseAdapter() {
    override fun mouseClicked(e: MouseEvent) { ... }

    override fun mouseEntered(e: MouseEvent) { ... }
}
```

对象的声明不能在函数内部（也就是说，不能直接放在函数里面），但是可以放在其他对象声明或者非内部类里面。

```kotlin
// 文件级别的对象声明
object Singleton {
    val property = "I am a singleton"
}

class OuterClass {
    // 非内部类内的对象声明
    object StaticNestedSingleton {
        val property = "I am nested in OuterClass"
    }
}

object OuterObject {
    // 其他对象声明内的对象声明
    object NestedSingleton {
        val property = "I am nested in OuterObject"
    }
}

fun someFunction() {
    // 这是非法的，不能在函数内部声明对象
    // object LocalSingleton {
    //     val property = "I am local"
    // }
}
```

### 5.6.1 数据对象

当你在 `Kotlin` 中输出一个基础对象声明时，你会看到的字符串包含了该对象的名字和哈希值：

```kotlin
object MyObject

fun main() {
    println(MyObject) // MyObject@1f32e575
}
```

就像数据类一样，你可以用数据关键字来标记一个对象声明。这样做会让编译器为你的对象生成一些函数：

- `toString() `返回数据对象的名称

- `equals()/hashCode()` 

  你不用为数据对象提供定制的 `equals` 或 `hashCode` 的实现方式。

数据对象的 `toString() `方法会返回对象的名字：

```kotlin
data object MyDataObject {
    val x: Int = 3
}

fun main() {
    println(MyDataObject) // MyDataObject
}
```

数据对象的 `equals()` 函数确保所有类型与你的数据对象相同的对象被认为是相等的。在大部分情况下，你在运行时只会有一个你的数据对象的实例（毕竟，一个数据对象就是声明了一个单例）。但是，在那些边缘情况下，如果在运行时生成了另一个相同类型的对象（比如，通过使用` java.lang.reflect` 进行平台反射或者一个在底层使用这个 `API` 的 `JVM` 序列化库），这就确保了这些对象被视为相等。

```kotlin
import java.lang.reflect.Constructor

data object MySingleton

fun main() {
    val evilTwin = createInstanceViaReflection()

    println(MySingleton) // MySingleton
    println(evilTwin) // MySingleton

    println(MySingleton == evilTwin) // true

    println(MySingleton === evilTwin) // false
}

fun createInstanceViaReflection(): MySingleton {
    return (MySingleton.javaClass.declaredConstructors[0].apply { isAccessible = true } as Constructor<MySingleton>).newInstance()
}
```

生成的 `hashCode() `函数的行为与 `equals() `函数保持一致，这样一来，所有数据对象在运行时的实例都会有相同的哈希码。

**数据对象与数据类的不同之处**

尽管数据对象和数据类声明经常一起使用并且有一些相似之处，但是有一些函数不会为数据对象生成：

- 没有 `copy()` 函数。数据对象声明的初衷是作为单例对象使用，因此不会生成 `copy()` 函数。单例模式只允许一个类有一个实例，如果允许复制这个实例，就会违反这个规则。
- 没有 `componentN() `函数。与数据类不同，数据对象并没有任何数据属性。试图解构一个没有数据属性的对象是没有意义的，因此不会生成 `componentN()` 函数。

**在密封的层级结构中使用数据对象**

数据对象声明在密封的层级结构中特别有用，比如密封类或密封接口，因为它们可以让你保持与你可能已经定义的数据类的一致性：

```kotlin
sealed interface ReadResult
data class Number(val number: Int) : ReadResult
data class Text(val text: String) : ReadResult
data object EndOfFile : ReadResult

fun printReadResult(r: ReadResult) {
    when(r) {
        is Number -> println("Num(${r.number}")
        is Text -> println("Txt(${r.text}")
        is EndOfFile -> println("EOF")
    }
}

fun main() {
    printReadResult(EndOfFile) // EOF
}
```

`sealed`关键字的作用主要体现在以下几个方面：

- **限制继承**：只有在同一个文件中定义的类可以继承密封类或实现密封接口，防止在其他地方被继承或实现。
- **使用场景**：`sealed`类和接口通常用于表示受限的类层次结构，例如在定义一组固定的状态或操作时。
- **更安全的when表达式**：使用密封类作为`when`表达式的条件可以保证处理所有可能的情况，不需要提供一个`else`分支，因为编译器能够检测出所有的情况是否都被处理了。

在上述示例中，`ReadResult`是一个密封接口，它有三种可能的实现：`Number`、`Text`和`EndOfFile`。所有这些实现都定义在同一个文件中。`printReadResult`函数使用`when`表达式来处理不同类型的`ReadResult`，而且不需要`else`分支，因为编译器知道所有可能的子类型都已经被处理了。

### 5.6.2 伴生对象

在类中，你可以用 `companion` 关键字来标记一个对象声明：

```kotlin
class MyClass {
    companion object Factory {
        fun create(): MyClass = MyClass()
    }
}
```

伴生对象的名字可以不写，如果省略的话，就会默认使用 "`Companion`" 这个名字：

```kotlin
class MyClass {
    companion object { }
}

val x = MyClass.Companion
```

类里面的成员可以访问对应伴生对象的私有属性和方法。

一个类的名字单独使用（不作为其他名字的修饰词）时，它就是指向这个类的伴生对象的引用（不管这个伴生对象有没有名字）：

```kotlin
class MyClass1 {
    companion object Named { }
}

val x = MyClass1

class MyClass2 {
    companion object { }
}

val y = MyClass2
```

需要注意的是，虽然伴生对象的成员在其他编程语言中看起来像是静态成员，但在程序运行时，这些仍然是实际对象的实例成员，比如，它们可以实现接口功能：

```kotlin
interface Factory<T> {
    fun create(): T
}

class MyClass {
    companion object : Factory<MyClass> {
        override fun create(): MyClass = MyClass()
    }
}

val f: Factory<MyClass> = MyClass
```

但是，在 JVM 中，如果你使用 `@JvmStatic` 注释，你可以将伴生对象的成员生成为实际的静态方法和字段

对象表达式和声明在语义上的不同之处:

- 对象表达式在它们被使用的地方立即执行（并初始化）。
- 对象声明在第一次被访问时才会懒加载初始化。
- 伴生对象在相应的类被加载（解析）时初始化，这与 `Java` 的静态初始化器的语义是一致的。

## 5.7 数据类

`Kotlin` 提供了一种特殊的类，叫做数据类，它非常适合用来存储数据。数据类和普通类的功能是一样的，但是它自带了一些额外的成员函数。这些成员函数可以帮你轻松地将实例转换为可读的输出，比较不同实例，复制实例等等。由于这些函数是自动提供的，所以你不需要为每一个类都写一遍这些重复的代码。

声明一个数据类，使用`data`关键字

```kotlin
data class User(val name: String, val id: Int)
```

数据类中预设的一些非常实用的成员函数包括：

| Function    | Description                                                |
| ----------- | ---------------------------------------------------------- |
| .toString() | 将类实例及其属性转化为易读的字符串并打印出来。             |
| .equals()   | 对类的不同实例进行比较。                                   |
| .copy()     | 通过复制已有的类实例并对某些属性进行修改来创建新的类实例。 |

例子如下：

- 如果你想打印出数据类实例的可读字符串，你可以直接调用 `.toString() `函数，或者使用会自动帮你调用 `.toString() `的打印函数，比如 `println()` 和 `print()`：

  ```kotlin
  data class User(val name: String, val id: Int)
  
  fun main() {
      val user = User("Alex", 1)
      
      // 系统会自动调用 toString() 函数，使输出结果更加清晰易读。
      println(user)            
      // User(name=Alex, id=1)
  
  }
  ```

- 去比较两个数据类的实例，通过使用`==`操作符

  ```kotlin
  data class User(val name: String, val id: Int)
  
  fun main() {
      val user = User("Alex", 1)
      val secondUser = User("Alex", 1)
      val thirdUser = User("Max", 2)
  
      println("user == secondUser: ${user == secondUser}") 
      // user == secondUser: true
  
      println("user == thirdUser: ${user == thirdUser}")   
      // user == thirdUser: false
  }
  ```

- 创建一个数据类实例的完全复制版，你可以在该实例上调用 `.copy()` 函数。

  如果你想复制一个数据类实例并修改其中一些属性，你可以在实例上调用 `.copy()` 函数，并在函数参数中添加你想要替换的属性值。

  ```kotlin
  data class User(val name: String, val id: Int)
  
  fun main() {
      val user = User("Alex", 1)
      val secondUser = User("Alex", 1)
      val thirdUser = User("Max", 2)
  
      // 创建user的副本。
      println(user.copy())       
      // User(name=Alex, id=1)
  
      // 复制一份用户，并将其name为 "Max"
      println(user.copy("Max"))  
      // User(name=Max, id=1)
  
      // 复制一份用户，并将其id为 3
      println(user.copy(id = 3)) 
      // User(name=Alex, id=3)
  }
  ```

  复制一个实例比直接修改原始实例更为安全，因为这样做不会影响到任何依赖于原始实例的代码。

## 5.8 抽象类

一个类可以被声明为抽象类，它的部分或全部成员也可以是抽象的。抽象成员在它所在的类中是没有具体实现的。你不需要给抽象类或函数加上 `open` 注解。

```kotlin
abstract class Polygon {
    abstract fun draw()
}

class Rectangle : Polygon() {
    override fun draw() {
        //...
    }
}
```

你可以用抽象成员来覆盖非抽象的开放成员

```kotlin
open class Polygon {
    open fun draw() {
        //...
    }
}

abstract class WildShape : Polygon() {
   //那些继承了 WildShape 的类需要自行实现 draw 方法，而不能直接使用 Polygon 中的默认实现。
    abstract override fun draw()
}
```

# 六、空指针安全性

在 `Kotlin` 语言中，空值是可以存在的。为了防止你的程序中出现空值相关的问题，`Kotlin` 设有空安全机制。这种机制可以在编译阶段，而非运行阶段，就检测出可能的空值问题。

空安全其实是一系列的功能，它们可以让你：

- 在程序中明确标明何时可以有空值。
- 进行空值检查。
- 对可能含有空值的属性或函数进行安全的调用。
- 在检测到空值时，明确规定应该采取的行动。

`Kotlin` 的类型系统的目标是消除空引用的危险，这也被称为"十亿美元的错误"。

在许多编程语言中，包括 `Java`，最常见的问题之一是访问空引用的成员会导致空引用异常。在 `Java` 中，这就是 `NullPointerException`，或简称 `NPE`。

在 `Kotlin` 中，可能导致 `NPE` 的唯一原因有：

- 明确地调用 `throw NullPointerException()`。
- 使用下面将要描述的` !! `运算符。
- 与初始化有关的数据不一致，例如：

- 在构造函数中未初始化的 `this` 被传递并在其他地方使用（"泄漏的 `this`"）。
- 超类构造函数调用一个开放成员，但在派生类中的实现使用了未初始化的状态。

Java 交互：

- 试图访问平台类型的空引用的成员；
- 与用于 `Java` 交互的泛型类型的可空性有关的问题。例如，一段 `Java` 代码可能会在 `Kotlin` `MutableList<String> `中添加` null`，因此需要 `MutableList<String?>` 来处理它。
- 由外部 Java 代码引起的其他问题。

## 6.1 可空类型

`Kotlin` 语言支持可空类型，这意味着你声明的数据类型是可以接受空值的。但默认情况下，数据类型是不接受空值的。如果你想让某个数据类型可以接受空值，你需要在声明该数据类型时，在类型后面加上一个问号`?`

例如：

```kotlin
fun main() {
    // 不可为null的String类型
    var neverNull: String = "This can't be null"

    // 抛出编译异常
    neverNull = null

    // nullable是一个可以为空的字符串类型。
    var nullable: String? = "You can keep a null here"

    // 可以设置为null 
    nullable = null

    // 默认情况下，不接受空值。
    var inferredNonNull = "The compiler assumes non-nullable"

    // 抛出编译异常
    inferredNonNull = null

    // notNull 不接受空值
    fun strLength(notNull: String): Int {                 
        return notNull.length
    }

    println(strLength(neverNull)) // 18
    println(strLength(nullable))  // 抛出编译异常
}
```

## 6.2 空值检验

你可以通过条件表达式来检查是否存在空值。比如在下面的例子中，`describeString()` 这个函数里就有一个 `if `语句，它的作用就是检查 `maybeString` 这个变量是否为空，以及它的长度是否大于零：

```kotlin
fun describeString(maybeString: String?): String {
    if (maybeString != null && maybeString.length > 0) {
        return "String of length ${maybeString.length}"
    } else {
        return "Empty or null string"
    }
}

fun main() {
    var nullString: String? = null
    println(describeString(nullString))
    // Empty or null string
}
```

## 6.3 安全调用

如果你想安全地获取一个可能含有空值的对象的属性，你可以使用安全调用操作符` ?..`。如果对象的属性是空的，这个操作符就会返回一个空值。这对于你想避免空值在代码中引发错误的情况非常有帮助。

在下面的例子中，`lengthString() `函数运用了安全调用，返回的结果是字符串的长度或者是一个空值：

```kotlin
fun lengthString(maybeString: String?): Int? = maybeString?.length

fun main() { 
    var nullString: String? = null
    println(lengthString(nullString))
    // null
}
```

你可以将安全调用进行链式操作，这样如果一个对象的任何属性含有空值，那么就会返回一个空值，而不会引发错误。例如：

```kotlin
person.company?.address?.country
```

你也可以使用安全调用运算符来安全地调用扩展或者成员函数。在这种情况下，会在函数调用之前进行空值检查。如果检测到空值，那么就会跳过这次调用，直接返回一个空值。

```kotlin
fun main() {
    var nullString: String? = null
    println(nullString?.uppercase())
    // null
}
```

## 6.4 使用Elvis运算符 

可以通过使用 `Elvis` 运算符` ?: `来设定一个默认值，这样一来，如果检测到空值，就会返回这个默认值。

在 `Elvis` 运算符的左边写下需要检查是否为空值的内容。在 `Elvis` 运算符的右边写下如果检测到空值应该返回的内容。

在接下来的示例中，`nullString` 是空的，因此安全地调用访问长度属性会返回一个空值。结果，`Elvis` 运算符返回了`0`：

```kotlin
fun main() {
    var nullString: String? = null
    println(nullString?.length ?: 0) // 0
}
```

## 6.5 !! 操作符

第三个选项是为那些喜欢 `NPE` 的人设计的：非空断言运算符（`!!`）可以将任何值转换为非空类型，如果值是 `null`，它会抛出一个异常。你可以写 `b!!`，这将返回 `b` 的非空值（例如，在我们的示例中是一个 `String`）或者如果 `b` 是 `null`，它会抛出一个 `NPE`：

```kotlin
val l = b!!.length
```

所以，如果你想要一个 `NPE`，你可以得到它，但你必须特别地去要求它，它不会无缘无故地出现。

## 6.6 安全转型

通常的类型转换可能会导致 `ClassCastException`，如果对象并非目标类型。另一个选择是使用安全的类型转换，如果转换尝试失败，它将返回 null：

```kotlin
val aInt: Int? = a as? Int
```

## 6.7 可空类型集合

如果你的集合中的元素类型是可空的，而你想要筛选出非空的元素，你可以通过使用 `filterNotNull` 函数来实现：

```kotlin
val nullableList: List<Int?> = listOf(1, 2, null, 4)
val intList: List<Int> = nullableList.filterNotNull()
```

`open`关键字的主要作用是：

1. 允许继承：在类声明前加上关键字，表示这个类可以被其他类继承。
2. 允许重写：在类成员（方法、属性等）前加上关键字，表示这些成员可以在子类中被重写。

# 六、泛型

