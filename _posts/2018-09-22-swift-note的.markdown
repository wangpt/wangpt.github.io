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


## 后记

此文档会不断更新
