---
title: "Kotlin Getting Started - 5. Functions"
date: 2023-08-29 22:20:00 +09:00 
# last_modified_at:
categories: [kotlin, basic]
tags: [kotlin, kotlin_basic]
---
## Functions
매개변수를 선언할때 var 키워드를 생략한다.<br>
```kotlin
fun sum(x: Int, y: Int): Int {
    return x + y
}
```

## Named arguments
함수를 호출하여 인자값을 넣을때 파라미터 이름에 대입하여 코드를  직관적으로 작성할 수 있다. <br>

## Default parameter values
파라미터의 기본값을 작성할 수 있다.<br>

## Functions without return
함수가 반환할 값이 없을때는 `Unit` 타입으로 반환한다. <br>
`Unit` 타입은 함수에 명시적으로 작성하지 않아도 되고<br>
`return Unit`으로 작성하거나 `return` 키워드를 사용하지 않아도 된다.

```kotlin
// Named arguments, Default parameter values, Functions without return 예제
fun printMessage(msg: String, prefix: String = "Info", suffix: String = "!!") {
    println("[$prefix] $msg $suffix")
    // return Unit
}

fun main() {
    printMessage(prefix = "Log") // output: [Log] Hello !!
}
```
## Single-expression functions
함수 내용이 단일 표현식이라면 `{}` 대신 `=` 로 간단하게 작성할 수 있다. <br>
```kotlin
fun sum(x: Int, y: Int) = x + y
fun main() {
    print(sum(1, 2)) // output: 3
}
```
> 함수의 반환타입을 생략하는 경우는 위와 같은 `{}`가 없는 Single-expression functions 일 경우에만 가능하다.

## Lambda expression
람다 표현식은 다음과 같이 작성할 수 있다.<br>
``` kotlin
println({ str: String -> str.uppercase() }("hello")) // output: HELLO
```
`->` 뒤에 오는 표현식이 반환값이 된다. <br>
parameter가 없는 람다식이라면 `->` 없이 body만 작성해 주면 된다. <br>
```kotlin
fun main() {
	println({"hello"}()) // output: hello
}
```
람다 표현식은 다양하게 사용할 수 있다.<br>

- 변수에 할당
- 다른 함수에 람다식 전달
- 반환값을 람다식으로 전달

## Function types
함수의 타입을 선언하는 방법이다. <br>
`(String, Int) -> Int`  parameter의 타입과 반환값의 타입을 적어줘야 한다. <br>

```kotlin
fun main() {
    // 변수에 할당하여 사용
    val upperLambda = { str: String -> str.uppercase() }
    println(upperLambda("hello")) // output: HELLO

    // 다른 함수에 람다식 전달
    val numbers = listOf(1, 2, 3, 4, 5)
    val even = numbers.filter { i -> i%2 == 0}
    println(even) // output: [2, 4]

    val min = toSeconds("minute")
    // 3분을 초로 변환
    println(min(3)) // output: 180

}
// 반환을 람다식으로
fun toSeconds(time: String): (Int) -> Int = when (time) {
    "hour" -> { value -> value * 60 * 60 }
    "minute" -> { value -> value * 60 }
    "second" -> { value -> value }
    else -> { value -> value}
}
```

## Trailing lambdas
함수에 parameter가 람다 표현식만 있을때는 `()`를 생략하고 `{}` 만 작성해도 되고, 제일 마지막 parameter가 람다 표현식일 경우 `()` 작성 후 `{}` 로 람다 표현식을 작성할 수 있다.

```kotlin
fun trailing(lam: (String) -> String) {
    println(lam("hello"))
}
fun trailing2(prefix: String, lam: (String) -> String) {
    println("$prefix ${lam("hello")}")
}

fun main() {
    trailing{ str -> str.uppercase() } // output: HELLO
    trailing2("!!") { str -> str.uppercase() } // output: !! HELLO
}

```