---
title: "Kotlin Getting Started - 3. Collections"
date: 2023-08-27 20:14:00 +09:00 
# last_modified_at:
categories: [kotlin, basic]
tags: [kotlin, kotlin_basic]
---

# Collections
데이터를 그룹화 하여 사용할때 유용하게 사용될 자료구조들이다.<br>
`Lists`, `Sets`, `Maps` <br>
위 타입들은 전부 불변성을 유지하는 타입과 가변을 지원하는 타입 두개를 지원한다.<br><br>
list, set, map은 다른 언어에서도 많이 사용하는 자료구조이므로 간략하게만 알아보자.

## List
불변성을 유지하려면 List 타입을 사용해야 하고 listOf() 를 사용하여 데이터를 생성한다.<br>
수정 가능하게 만들려면 MutableList 타입을 사용해야 하고 mutableListof() 를 사용하여 데이터를 생성한다.

||Type|Create a data|
|---|---|---|
|Immutable|List|listOf()|
|Mutable|MutableList|mutableListOf()|

```kotlin
val immutableList = listOf("123", "1234", "2323") 
// 명시적으로 타입을 선언해 주려면  List<T> 를 선언해주면 된다.
// val immutableList: List<String> = listOf("123", "1234", "2323")

println(immutableList) // output: [123, 1234, 2323]
// immutableList[0] = "123" -> 컴파일 에러 발생

val mutableList = mutableListOf("321", "4321", "2342")
// List와 마찬가지로 명시적으로 타입을 선언해 주려면  MutableList<T> 를 선언해주면 된다.
// val mutableList: MutableList<String> = mutableListOf("321", "4321", "2342")

println(mutableList) // output: [321, 4321, 2342]
mutableList[0] = "000" // OK
println(mutableList) // output: [000, 4321, 2342]
```

mutableList를 immutableList로 캐스팅 하는것도 지원한다.<br>
```kotlin
val mutableList = mutableListOf("321", "4321", "2342")
val immutableList: List<String> = mutableList
```
위 코드에도 적혀 있는데 list의 데이터에 접근하려면 배열처럼 `[index]` 를 사용하여 접근하면 된다.<br>
``` kotlin
val immutableList: List<String> = listOf("123", "1234", "2323")
println(immutableList[0]) // output: 123
```
`first()`나 `last()` 메서드로 list의 첫번째나 마지막 값을 불러올 수 있고<br>
`count()` 메서드로 list의 사이즈를 알 수 있다.<br>
```kotlin
val immutableList: List<String> = listOf("123", "1234", "2323")
print("fist: ${immutableList.first()}, last: ${immutableList.last()}, ")
println("count: ${immutableList.count()}")
// output: fist: 123, last: 2323, count: 3 
```

`in` 연산자로 해당 값이 list에 포함돼 있는지 확인할 수 있다. <br>
```kotlin
val immutableList: List<String> = listOf("123", "1234", "2323")
println("1" in immutableList) // output: false
```
mutable list에 데이터를 추가하려면 `add()` 메서드를, 해당 데이터를 삭제하려면 `remove()` 메서드를 사용하면 된다.<br>

```kotlin
val mutableList: MutableList<String> = mutableListOf("321", "4321", "2342")
mutableList.add("1010")
mutableList.remove("321")
println(mutableList) // output: [4321, 2342, 1010]
```

## Set

||Type|Create a data|
|---|---|---|
|Immutable|Set|setOf()|
|Mutable|MutableSet|mutableSetOf()|

```kotlin
// immutable
val immutableSet: Set<String> = setOf("BC", "AB", "ABCD", "AB")
println(immutableSet) // output: [BC, AB, ABCD]

//mutable
val mutableSet: MutableSet<String> = mutableSetOf("123", "1234", "12", "123")
println(mutableSet) // output: [123, 1234, 12]
```
Set도 List와 동일하게 mutable set을 immutable set으로 캐스팅 가능하고 <br>
`in` 연산자, `count()`, `add()`, `remove()` 메서드를 지원한다.

## Map

||Type|Create a data|
|---|---|---|
|Immutable|Map|mapOf()|
|Mutable|MutableMap|mutableMapOf()|

데이터를 생성할때 key to value 로 key value 쌍을 선언한다.
```kotlin
//immutable
val immutableMap: Map<String, Int> = mapOf("A" to 0, "B" to 1, "C" to 10)
println(immutableMap) // output: {A=0, B=1, C=10}

//mutable
val mutableMap: MutableMap<String, Int> = mutableMapOf("D" to 0, "E" to 1, "T" to 40)
println(mutableMap) // output: {D=0, E=1, T=40}
```
Map 또한 mutable map을 immutable map으로 캐스팅 가능하다.<br>

<br>
데이터에 접근하려면 [key] 로 접근 가능하다. <br>

```kotlin
val mutableMap: MutableMap<String, Int> = mutableMapOf("D" to 0, "E" to 1, "T" to 40)
println(mutableMap["D"]) // output: 0
```

`count()` 메서드로 사이즈 확인이 가능하고 `put(key, value)`로 데이터 추가, `remove(key)`로 삭제가 가능하다.<br>
그리고 `containsKey()` 메서드로 키가 포함돼 있는지 확인 가능하다.

```kotlin
val mutableMap: MutableMap<String, Int> = mutableMapOf("D" to 0, "E" to 1, "T" to 40)
mutableMap.put("F", 22)
mutableMap.remove("D")
println(mutableMap) // output: {E=1, T=40, F=22}
println(mutableMap.containsKey("E")) // output: true
```

`keys`와 `value` 속성으로 해당 값들을 collection으로 받아올 수 있다.<br>
```kotlin
val mutableMap: MutableMap<String, Int> = mutableMapOf("D" to 0, "E" to 1, "T" to 40)
println(mutableMap.keys) // output: [D, E, T]
println(mutableMap.values) // output: [0, 1, 40]
//collection 이므로 in 연산자를 사용할 수도 있다.
println("E" in mutableMap.keys) // output: true
```