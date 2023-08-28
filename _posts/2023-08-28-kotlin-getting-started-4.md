---
title: "Kotlin Getting Started - 4. Control flow"
date: 2023-08-28 18:01:00 +09:00 
# last_modified_at:
categories: [kotlin, basic]
tags: [kotlin, kotlin_basic]
---

# Control flow
코틀린에서는 데이터를 어떻게 제어하는지 알아보자.<br>

## Conditinal expressions
`if`와 `when` 으로 분기문을 작성할 수 있다. <br>

### If
다른 언어와 사용 방법은 같다. 
```kotlin
val isCheck = false
if (check) {
    println("참")
} else {
    println("거짓")
}
```
코틀린에는 삼항 연산자가 없다. <br>
대신 if문을 `{}` 없이 사용 한다면 표현식으로 사용할 수 있고 이를 삼항 연산자 대신 사용할 수도 있다.<br>
```kotlin
val isCheck = true
println(if (isCheck) 10 else 20) // output: 10
```

### When
`when`은 다른 언어의 switch 처럼 사용할 수 있다. <br>
`->`를 사용하여 분기 처리 한다.

```kotlin
val i = 123
when (i) {
    1 -> println("A")
    12 -> println("B")
    123 -> println("C")
    else -> println("Z")
} // output: C
```
참고로 switch 처럼 break를 쓰지 않으면 다음 분기로 넘어가는것이 아니라 `if` 처럼 하나의 조건이 만족할 경우 해당 분기만 실행한다.

`when`도  `if`처럼 표현식으로 작성할 수 있다.<br>
```kotlin
val i = 1
val result = when (i) {
    1 -> "One"
    2 -> "Two"
    3 -> "Three"
    else -> "X"
}
println(result) // output: One
```
이렇게 표현식으로 작성할때는 else가 반드시 있어야 한다. <br>
<br>
위 예제 처럼 `when`은 특정 변수를 매칭하는데 유용하기도 하지만 if문의 분기를 보기 쉽게 표현할 수도 있다. <br>

```kotlin
val n = 5

val p = when {
    n < 4 -> "< 4"
    n < 5 -> "< 5" 
    n < 10 -> "< 10"
    else -> "else"
}
println(p) // output: "< 10"

```

## Ranges
숫자의 특정 범위를 구성하려면 `..` 연산자를 이용한다.<br>
`1..4` 인 경우 `1, 2, 3, 4`가 범위가 된다. <br>
`..<` 연산자로 마지막 수는 포함되지 않게 만들수도 있다.<br>
`1..<4` ->  `1, 2, 3`<br>
내림차순으로 범위를 구성하려면 `downTo`를 사용한다.<br>
`4 downTo 1` -> `4, 3, 2, 1` <br>
기본으로 1씩 증가하거나 감소하는 범위인데 증/감 하는 수치를 변경하려면 `step` 을 사용한다.<br>
`1..10  step 2` -> `1, 3, 5, 7, 9`<br>

`Char` 또한 정수 타입이므로 범위 지정이 가능하다. <br>
`'a'..'d'` -> `'a', 'b', 'c', 'd'` <br>

## Loops
반복문은 다른언어와 똑같이 `for` 과 `while`이 있다. <br>

### For
위의 Ranges를 이용하는 방법이 있다.<br>
```kotlin
for(i in 1..5)
    print(i)
// output: 12345
```

또는 collection 값을 반복할 수도 있다.<br>
```kotlin
val words = listOf("dog", "cat", "rabbit")
for (word in words)
    println(word)
/*
output:
dog
cat
rabbit
*/
```

### While
다른 언어와 똑같이 `while` 과 `do-while`이 있다. <br>
문법도 자바와 같다. <br>
```kotlin
var i = 0
while(i < 5) {
    print(i)
    i ++
} // output: 01234

i = 0
do {
    print(i)
    i++
} while(i < 0) // output: 0

```







