---
title: "Kotlin Getting Started - 1. Hello world"
date: 2023-08-25 21:54:00 +09:00 
# last_modified_at:
categories: [kotlin, basic]
tags: [kotlin, kotlin_basic]
---
다음 팀 프로젝트로 안드로이드 앱을 만들 것 같아서 코틀린 공식문서를 살펴보게 됐다. <br>
[코틀린 공식문서](https://kotlinlang.org/docs/getting-started.html)<br>
코틀린의 문법은 어떤지 찍먹해보자 !<br><br>
참고로 이 시리즈는 다른 언어를 배워본적 있다는 가정하에 간단하게 작성 하려고 한다.

## Hello World

```kotlin
fun main() {
    println("Hello, world!")
}
```
위 코드를 보면 코틀린에서는 
- fun 키워드로 함수를 선언한다.
- main() 함수는 프로그램의 시작점이다.

인 것을 알 수 있다. 다른 언어와 비슷해보인다.

## Variables
변수를 선언하는 키워드는 두가지가 있다. 
- val - read-only 변수
- var - mutable 변수

다른 언어에서 const int 이런식으로 선언하던 상수를 val로 표현하도록 했다.<br>
```kotlin
val readOnly = 2 // read-only
var mutableVariable = 3 // mutable

mutableVariable = 4
print(mutableVariable) // output: 4
```

## String templates
문자열은 \"\" 로 감싸야 하고 문자열 내에 변수의 값을 포함하려면 \$과 함께 변수명을 적으면 된다.<br>
이때, 표현식이 필요한 경우는 $\{\}로 감싸준다.<br>
```kotlin
val year = 2023
val month = "Aug"
println("$year/$month") // output: 2023/Aug
println("${year+1}/$month") // output: 2024/Aug 
```
js의 template literals과 같은 기능이다. 


<br><br>
위 예제에서는 변수를 선언할때 타입을 지정하지 않고 값을 그냥 대입해줬다.<br>
이게 가능한 이유는 코틀린에서는 대입되는 값을 보고 타입을 추론해주기 때문이다. <br>
변수의 타입을 명시적으로 선언해주는 방법도 있는데 그 방법은 다음글에서 알아보도록 하자