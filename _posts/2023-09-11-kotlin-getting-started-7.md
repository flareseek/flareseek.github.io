---
title: "Kotlin Getting Started - 7. Null safety"
date: 2023-09-11 22:19:00 +09:00
# last_modified_at:
categories: [kotlin, basic]
tags: [kotlin, kotlin_basic]
---

# Null safety

kotlin에서는 `null`값을 지원하는데, `null` 값으로 생기는 이슈들을 방지하기 위해서 `null safety`를 지원한다고 한다.<br>

## Nullable types

kotlin에서 그냥 타입을 선언하면 기본적으로 null이 허용되지 않는다.<br>
null값을 허용하려면 타입뒤에 `?` 를 추가하면 된다<br>

```kotlin
var neverNull: String = "ABCD"
neverNull = null // 컴파일 에러

var nullable: String? = "ABCD"
nullable = null // 문제 없음

var inferredNonNull = "ABCD"
inferredNonNull = null // 컴파일 에러 (기본 타입은 null 허용X)
```

## Use safe calls

`null` 값을 가질 수 있는 타입들은 `?.`나 `!!.` 연산자를 이용하여 사용해야 한다.<br>
`?.` 연산자는 객체가 `null` 값을때 더 이상 해당 객체의 값을 확인하지 않고 `null`을 반환한다.<br>
`!!.` 연산자는 객체가 절대 `null`값이 아님을 명시적으로 선언해주는 연산자다.<br>

```kotlin
fun main() {
   var str: String? = null
   println(str?.uppercase()) // output: null
//   println(str!!.uppercase()) // runtime error
}
```

## User Elvis operator
`?:` 연산자를 통해 해당 값이 `null` 일 경우 반환할 값을 설정한다. <br>

```kotlin
fun main() {
    var nullString: String? = null
    println(nullString?.length ?: 0) // output: 0
}
```

<br><br><br>
코틀린 Getting Started 문서를 간단하게 정리해봤다. <br>
읽으면서 느꼈던게 코틀린 언어가 타입을 선언할때 불변성 타입으로 선언하는것을 권장한다든지, `?.` 같은 옵셔널 체이닝을 지원하여 `null` 값에 접근하는것을 방지해주는 문법을 보면 프로그래머가 실수하지 않도록 설계한 언어라는 생각이 들었다.<br>
뭔가 느낌이 C#과 비슷하게 suger syntax가 많아 보이는데... JVM 기반이기도 하고, 구글에서도 밀어주고 있으니 깊게 파볼만 하지 않을까 싶다.<br>
