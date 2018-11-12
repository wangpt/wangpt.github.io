---
layout:     post
title:      "Swift学习笔记"
subtitle:   " \"Exmple for Swift\""
date:       2018-09-22 12:00:00
author:     "Wangpt"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - Notes
    - Swift

---

> “欢迎关注和分享 ”


## 简介
*Swift，苹果于2014年WWDC（苹果开发者大会）发布的新开发语言，可与Objective-C 共同运行于Mac OS和iOS平台，用于搭建基于苹果平台的应用程序*

---


### 知识储备

* [swift教程](https://swift.org)
* [the-swift-programming-language-in-chinese](https://github.com/numbbbbb/the-swift-programming-language-in-chinese)
* [其他参考](http://www.runoob.com/swift/swift-basic-syntax.html)


### 概览

###### 简单值
*使用 let来声明一个常量，用 var来声明一个变量*

```
var myVariable = 10
myVariable = 20
let myConstant = 10
```
*常量和变量必须拥有赋予的值相同的类型。如果初始值不能提供足够的信息，则需要用冒号分隔*

```
let myConstantInteger = 10
let myConstantFloat = 10.0
let myConstantDouble:Double = 10.0
```
*值不能隐形的转化为其他类型，如果需要将一个类型装好，则需要对应类型显性的声明* 

```
let text = "the width is "
let width = 20
let textWidth = text + String(width)
```

*也可以将值加入字符串：将值写在圆括号，前面再添加反斜杠*

```
let width = 20
let space = 10
let textWidth = "the width is \(width + space)"
```

*为字符串使用三个双引号（"""）来输入多行内容*

```
let width = 3
let height = 5
let quotation = """
view width is \(width)"
And height is \(height)"
"""
```

*使用方括号创建数组或字典，并使用放火好按序号或者键访问对应元素*

```
var colorList =  ["yellow", "red", "white", "blue"]
colorList[1] = "gray"

var personInfo = ["name":"小明",
                  "age":"18"]
personInfo["name"] = "小红"
personInfo["sex"] = "1"
```

*初始化空数组或者字典,也可以用[]来表示空数组，用[:]来表示空字典*

```
var emptyArray = [String]()
var emptyDictionary = [String: Float]()
emptyArray = []
emptyDictionary = [:]
```
###### 控制流
*学习使用if和switch做判段，使用for in ，while，repeat-while等做循环，其中括号可以省略，但花括号必不可少*

```
let items = [11,12,17,20,22]
for item in items {
    if (item < 15){
        print("<15的数字 \(item)");
    }else{
        print(">=15的数字 \(item)");
    }
}
```

*使用if let操作是可选项（Optional），判断后不需要解包（!），{ }内一定有值*

```
let name: String? = "老王"
let sex: String? = "男"
if let theName = name , let theSex = sex{
    print("name sex 有值 ，名字为\(theName) 性别为\(theSex)")
}else{
    print("name sex 无值")
}
let age :String? = nil
if let theAge = age {
    print("age 有值，为\(theAge)")
}else{
    print("age 无值")
}
```

*使用if var同上，只不过值可以进行修改*

```
let age :String? = "18"
if var theAge = age {
    theAge = "19"
    print("theAge 有值，为\(theAge)")
}else{
    print("age 无值")
}
```
*使用？？可以提供默认值，如果可选值为空，则显示为默认值*

```
let nickName: String? = nil
let fullName: String = "xiaoming"
let informalGreeting = "Hi \(nickName ?? fullName)"
print(informalGreeting);
```

*Switch 选择语句支持任意类型的数据和类型的比较*

```
let string = "hello world"
switch string {
case "hello":
    print("hello")
case "world", "swift":
    print("world")
case let x where x.hasSuffix("world"):
    print("\(string) swift")
default:
    print("no have string")
}
```
*使用 while来重复代码快直到条件改变, 使用repeat为先运行再判断，所以至少运行一次*

```
var i = 10
while i < 10 {
    i = i * 2
}
print(i)

var j = 10
repeat {
    j = j * 2
} while j < 10
print(j)
```
*可以使用 ..<来创建一个不包含最大值的区间,使用 ...来创造一个包含最大值和最小值的区间*

```
var total = 0
for i in 0..<4 {
    total += i
}
print(total)
var more = 0
for i in 0...4 {
    more += i
}
print(more)
```
###### 函数和闭包

*使用func声明函数，在名字后圆括号声明参数，使用->分隔参数和返回值的类型*

```
func greet(person: String, day: String) -> String {
    return "Hello \(person), today is \(day)."
}
print(greet(person: "Baby", day: "Sunday"))

```

*默认情况下，函数使用形参作为实际参数的标签，也可以使用_避免使用*

```
func greet(_ person: String, day: String) -> String {
    return "Hello \(person), today is \(day)."
}
print(greet("Baby", day: "Sunday"))

```
*函数可返回多个参数*

```
func calculateStatistics(scores: [Int]) -> (min: Int, max: Int, sum: Int) {
    var min = scores[0]
    var max = scores[0]
    var sum = 0
    
    for score in scores {
        if score > max {
            max = score
        } else if score < min {
            min = score
        }
        sum += score
    }
    
    return (min, max, sum)
}
let statistics = calculateStatistics(scores: [5, 3, 100, 3, 9])
print(statistics.0)
print(statistics.1)
print(statistics.sum)
```
*函数可接受多个参数*

```
func sumOf(numbers: Int...) -> Int {
    var sum = 0
    for number in numbers {
        sum += number
    }
    return sum
}
print(sumOf(numbers: 3,2,1))
```
*函数可以内嵌。内嵌的函数可以访问外部函数里的变量。你可以通过使用内嵌函数来组织代码，以避免某个函数太长或者太过复杂*

```
func matchMinMaxSum(numbers: Int...) -> Int{
    var y = 0;
    func calculateStatistics(scores: [Int]) -> (min: Int, max: Int) {
        var min = scores[0]
        var max = scores[0]
        for score in scores {
            if score > max {
                max = score
            } else if score < min {
                min = score
            }
        }
        return (min, max)
    }
    let statistics = calculateStatistics(scores: numbers)
    return statistics.min + statistics.max;
}
print(matchMinMaxSum(numbers: 100,30,50,120));
```

*可以把函数当返回值进行返回*

```
func makeIncrementer() -> ((Int) -> Int) {
    func addOne(number: Int) -> Int {
        return 1 + number
    }
    return addOne
}
var increment = makeIncrementer()
print(increment(7))

func number() -> ((Int)->Void) {
    func twoNumber(num:Int){
        print(num * 2)
    }
    return twoNumber
}
let numbers = number()
numbers(7)
```
*函数也可以把另外一个函数作为其自身的参数*

```
func hasAnyMatches(item: Int, condition: (Int) -> Bool) -> (number:Int, lessThanTen: Bool)  {
    if condition(item) {
        return (item , true)
    }else{
        return (item , false)
    }
}
func lessThanTen(number: Int) -> Bool {
    return number < 10
}
let matchs = hasAnyMatches(item: 9, condition: lessThanTen)
print("\(matchs.number),\(matchs.lessThanTen)")
```

*函数其实就是闭包的一种特殊形式：一段可以被随后调用的代码块。闭包中的代码可以访问其生效范围内的变量和函数，就算是闭包在它声明的范围之外被执行——你已经在内嵌函数的栗子上感受过了。你可以使用花括号（ {}）括起一个没有名字的闭包。在闭包中使用 in来分隔实际参数和返回类型。*

```
let numbers = [20, 19, 7, 12]
numbers.map({
    (number: Int) -> Int in
    let result = 3 * number
    print(result);
    return result
})
```
*你有更多的选择来把闭包写的更加简洁。当一个闭包的类型已经可知，比如说某个委托的回调，你可以去掉它的参数类型，它的返回类型，或者都去掉。*

```
let numbers = [20, 19, 7, 12]
let mappedNumbers = numbers.map({
    (number: Int) -> Int in
    let result = 3 * number
    return result
})
print(mappedNumbers)
```
*你有更多的选择来把闭包写的更加简洁。当一个闭包的类型已经可知，比如说某个委托的回调，你可以去掉它的参数类型，它的返回类型，或者都去掉。*

```
let mappedNumbers = numbers.map({ number in 3 * number })
print(mappedNumbers)
```
*你可以调用参数通过数字而非名字——这个特性在非常简短的闭包当中尤其有用。当一个闭包作为函数最后一个参数出入时，可以直接跟在圆括号后边。如果闭包是函数的唯一参数，你可以去掉圆括号直接写闭包*

```
let numbers = [20, 19, 7, 12]
let sortedNumbers = numbers.sorted { $0 < $1 }
print(sortedNumbers)
```
### 基础内容
*基础内容包含整型值的Int，浮点型的Double和Float，布尔值Bool，字符串值的String，同时还有特殊的集合类型Array，Set，Dictionary和元组等*

###### 常量和变量
*常量设置好后不能修改，而变量可以在之后进行修改*

```
let maximumNumberOfLoginAttempts = 0
var currentLoginAttempt = 0
currentLoginAttempt = 1
let x = 0.0, y = 0.0, z = 0.0
print("\(x) \(y) \(z)")
```

*类型标注*

```
var welcomeMessage: String
var x, y, z: Int
x = 10
y = 20
z = 30
print("\(x) \(y) \(z)")
```

*常量和变量的名字几乎可以使用任何字符，甚至包括 Unicode 字符*

```
let π = 3.14159
let 你好 = "你好世界"
let ?? = "dogcow"
```
###### 注释
*使用注释将不需执行的文本放到代码中，作为标记或者你自己的提醒*

```
// 这是一个单行注释

/*
   这是一个多行注释
 */

```

*你可以在多行注释中先开启一个注释块，接着再开启另一个注释块。然后关闭第二个注释块，再关闭第一个注释块*

```
/* 这是第一个多行注释的开头
/* 这是第二个嵌套在内的注释块 */
这是第一个注释块的结尾*/

```

###### 分号
*swift并不需要每一句代码后写分号(;)，如果添加也没有问题，但如果在一行写多句代码，则必须添加分号*

```
let cat = "?"; print(cat)
```
###### 整数
*指的是没有小数部分的数字，如12和-34等，整数分为有符号（正数、负数和0）以及无符号（正数和0。Swift 提供了 8，16，32 和 64 位编码的有符号和无符号整数。例如 8 位无符号整数的类型是 UInt8 ，32 位有符号整数的类型是 Int32*

```
let minValue = UInt8.min // 最小值是 0, 值的类型是 UInt8
let maxValue = UInt8.max // 最大值是 255, 值得类型是 UInt8
```

*在大多数情况不需为整型特意设置一个类型，直接使用Int即可，等同于与当前原生字相同的类型,在 32 位平台上， Int 的长度和 Int32 相同,在64位平台上， Int 的长度和 Int64 相同,即使在 32 位的平台上， Int 也可以存 -2,147,483,648 到 2,147,483,647 之间的任意值,对于大多数整数区间来说完全够用了*

```
let minValue = Int.min
let maxValue = Int.max
print("minValue:\(minValue),maxValue:\(maxValue)")
```

###### 浮点数
*浮点数是有小数的数字，比如 3.14159 , -273.15等，Double 有至少 15 位数字的精度，而 Float 的精度只有 6 位,在两种类型都可以的情况下，推荐使用 Double 类型。*

```swift
let value1 : Double = 0.5
let value2 : Float = -0.6
print("value1:\(value1),value2:\(value2)")
```

###### 类型安全和类型推断
*swift 是一门类型安全的语言，任何不匹配的类型，会标记错误，同时可以通过赋予的值进行推断出合适的类型*

```swift
let value1 = 0.5
print("默认为Double类型")
let anotherPi = 3 + 0.14159
print("默认为Double类型")
```

###### 数值型字面量
*数值型字面量也可以增加额外的格式使代码更加易读，整数和浮点数都可以添加额外的零或者添加下划线来增加代码的可读性。下面的这些格式都不会影响字面量的值*

```swift
let value1 = 000123.456
let value2 = 1_000_000
print("value1:\(value1),value2:\(value2)")
```
###### 数值类型转换
*类型的转换必须显式地指定类型*

```swift
let three = 3
let floatValue = 0.12
let pi = Double(three) + floatValue
```
###### 类型别名
*类型别名可以为已经存在的类型定义了一个新的可选名字。用 typealias 关键字定义类型别名。*

```
typealias AudioSample = UInt16
let value1 = AudioSample.max
print("value1:\(value1)")
```

###### 布尔值
*布尔量被作为逻辑值来引用，因为他的值只能是真或者假。Swift为布尔量提供了两个常量值， true 和 false*

```
let orangesAreOrange = true
let turnipsAreDelicious = false
```

###### 元组
*元组把多个值合并成单一的复合型的值。元组内的值可以是任何类型，而且可以不必是同一类型*

```
//在下面的示例中， (404, "Not Found") 是一个描述了 HTTP 状态代码 的元组
let http404Error = (404, "Not Found")
print("value1:\(http404Error.1)")
```

*任何类型的排列都可以被用来创建一个元组，他可以包含任意多的类型。例如 (Int, Int, Int) 或者 (String, Bool) ，实际上，任何类型的组合都是可以的。*

```
let http404Error = (404, "Not Found")
let (statusCode, statusMessage) = http404Error
print("The status code is \(statusCode),message is \(statusMessage)")
```
*当你分解元组的时候，如果只需要使用其中的一部分数据，不需要的数据可以用下滑线（ _ ）代替*

```
let http404Error = (404, "Not Found")
let (justTheStatusCode, _) = http404Error
print("The status code is \(justTheStatusCode)")
```

*你可以在定义元组的时候给其中的单个元素命名,在命名之后，你就可以通过访问名字来获取元素的值了*

```
let http200Status = (statusCode: 200, description: "OK")
print("The status code is \(http200Status.statusCode)")
print("The status message is \(http200Status.description)")
```

###### 可选项
*可以利用可选项来处理值可能缺失的情况*

```
var serverResponseCode: Int? = 404
serverResponseCode = nil
```

*如果你定义的可选变量没有提供一个默认值，变量会被自动设置成 nil,其中 Swift 中的 nil 和Objective-C 中的 nil 不同，在 Objective-C 中 nil 是一个指向不存在对象的指针。在 Swift中， nil 不是指针，他是值缺失的一种特殊类型，任何类型的可选项都可以设置成 nil 而不仅仅是对象类型。*

```
var surveyAnswer: String?
```

*你可以利用 if 语句通过比较 nil 来判断一个可选中是否包含值。利用相等运算符 （ == ）和不等运算符（ != ）。*

```
if convertedNumber != nil {
    print("convertedNumber contains some integer value.")
}
```

*一旦你确定可选中包含值，你可以在可选的名字后面加一个感叹号 （ ! ） 来获取值，感叹号的意思就是说“我知道这个可选项里边有值，展开吧。”这就是所谓的可选值的强制展开*

```
if convertedNumber != nil {
    print("convertedNumber has an integer value of \(convertedNumber!).")
}
```

###### 可选项绑定
*可以使用可选项绑定来判断可选项是否包含值，如果包含就把值赋给一个临时的常量或者变量。可选绑定可以与 if 和 while 的语句使用来检查可选项内部的值，并赋值给一个变量或常量*

```
var someOptional : String? = "hello"
if let constantName = someOptional {
    print(constantName);
}
```
*而不是强制展开来重写*

```
var someOptional : String? = "hello"
if  someOptional != nil  {
    print(someOptional!);
}else{
    print(no have value);
}
```

*你可以在同一个 if 语句中包含多可选项绑定，用逗号分隔即可*

```
if let firstNumber = Int("4"), let secondNumber = Int("42"), firstNumber < secondNumber && secondNumber < 100 {
    print("success first = \(firstNumber) seconde  =  \(secondNumber)");
}
```
*你可以使用guard let设置提前退出*

```
func doSomething(str: String?)
{
    guard str != nil else { return }
    print("hello")
}
```

###### 隐式展开可选项
*有时在一些程序结构中可选项一旦被设定值之后，就会一直拥有值。在这种情况下，就可以去掉检查的需求，也不必每次访问的时候都进行展开，因为它可以安全的确认每次访问的时候都有一个值。这种类型的可选项被定义为隐式展开可选项。*

```
let possibleString: String? = "An optional string."
let forcedString: String = possibleString!
print(forcedString)
let assumedString: String! = "An implicitly unwrapped optional string."
let implicitString: String = assumedString
print(implicitString)
```

###### 错误处理
*在程序执行阶段，你可以使用错误处理机制来为错误状况负责*

```
do {
    try canThrowAnError()
    // no error was thrown
} catch {
    // an error was thrown
}
```
*在函数声明过程当中加入 throws 关键字来表明这个函数会抛出一个错误。当你调用了一个可以抛出错误的函数时，需要在表达式前预置 try 关键字*

```
func canThrowAnError() throws {
    // this function may or may not throw an error
}
```
###### 断言和先决条件
*断言和先决条件用来检测运行时发生的事情。你可以使用它们来保证在执行后续代码前某必要条件是满足的。如果布尔条件在断言或先决条件中计算为 true ，代码就正常继续执行。如果条件计算为 false ，那么程序当前的状态就是非法的；代码执行结束，然后你的 app 终止*

```
let age = -3
assert(age >= 0, "A person's age cannot be less than zero")
        
```
*如果代码已经检查了条件，你可以使用 assertionFailure(_:file:line:) 函数来标明断言失败*

```
if age > 10 {
    print("You can ride the roller-coaster or the ferris wheel.")
} else if age > 0 {
    print("You can ride the ferris wheel.")
} else {
    assertionFailure("A person's age can't be less than zero.")
}
```
*在你代码中任何条件可能潜在为假但必须肯定为真才能继续执行的地方使用先决条件。比如说，使用先决条件来检测下标没有越界，或者检测函数是否收到了一个合法的值,通过调用 precondition(_:_:file:line:) 函数来写先决条件。给这个函数传入表达式计算为 true 或 false ，如果条件的结果是 false 信息就会显示出来。*

```
let index = -3
precondition(index > 0, "Index must be greater than zero.")
```

*值得注意的是precondition在release版本中依然奏效而Assert只在开发版本中奏效。*

```
let index = -3
precondition(index > 0, "Index must be greater than zero.")
assert(age >= 0, "A person's age cannot be less than zero")
```

## 后记

此文档会不断更新
