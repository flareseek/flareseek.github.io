---
title: "Kotlin Getting Started - 6. Classes"
date: 2023-08-31 22:34:00 +09:00 
# last_modified_at:
categories: [kotlin, basic]
tags: [kotlin, kotlin_basic]
---
# Classes
클래스 선언 방법이다.<br>
```kotlin
class Customer
```

## Properties
속성을 선언하는 방법은 두가지가 있다. <br>
```kotlin
class Contact(val id: Int, var email: String) {
    val category: String = ""
}
```
클래스 헤더에 넣거나, 클래스 바디의 안에 선언해주면 된다.

### Create instance
객체를 생성하는 방법이다. <br>
```kotlin
class Contact(val id: Int, var email: String)

fun main() {
    val contact = Contact(1, "mary@gmail.com")
}
```
특이한점은 `new` 키워드 없이 객체를 생성한다는 점이다. <br>

primary constructor는 위와 같이 `class Contact()` 처럼 적어주면 되고 <br>
여러 생성자를 만들어 주려면 `class Contect constructor(val id)` 같이 클래스명 뒤에 `constructor` 키워드를 사용해주면 된다.<br>

### Access properties
속성에 접근하는 방법이다.<br>
```kotlin
class Contact(val id: Int, var email: String)

fun main() {
    val contact = Contact(1, "mary@gmail.com")

    println(contact.email) // output: mary@gmail.com

    contact.email = "jane@gmail.com"

    println(contact.email) // output: jane@gmail.com
}
```
getter, setter 지정할 필요 없이 맴버 변수 접근이 가능하다.<br>

### Data classes
`data class`는 class들이 자주 사용하는 메서드들을 자동으로 포함하는 class를 말한다.
```kotlin
data class User(val name: String, val age: Int)
fun main(){
    val user = User("Sam", 21)
    println(user.toString()) // output: User(name=Sam, age=21)
}
```
`toString()` 말고도 제공해주는 함수들이 많다. 더 자세한 내용은 [문서](https://kotlinlang.org/docs/data-classes.html)를 참고하자! <br>
