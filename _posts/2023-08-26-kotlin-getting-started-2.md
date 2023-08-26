---
title: "Kotlin Getting Started - 2. Basic types"
date: 2023-08-26 22:06:00 +09:00 
# last_modified_at:
categories: [kotlin, basic]
tags: [kotlin, kotlin_basic]
---

## Basic types
코틀린의 기본 타입은 다른 언어와 비슷하다. <br>

|Category|Basic types|
|:---|:---|
|Integers|`Byte`, `Short`, `Int`, `Long`|
|Unsigned integers|`UByte`, `UShort`, `UInt`, `ULong`|
|Floating-point numbers|`Float`, `Double`|
|Booleans|`Boolean`|
|Characters|`Char`|
|Strings|`String`|

리터럴 상수 표현 또한 비슷하다. <br>
Decimals: `111` <br>
Long type: `111L`<br>
Hexadecimals: `0x0F` <br>
Binaries: `0b00001011` <br>
<br>
Unsigned 타입도 지원한다. <br>
`Ubyte`, `UShort`, `Uint`, `Ulong` <br>
Unsigned 타입은 변수에 대입할때 접미어 `u`를 붙여야 한다.<br>
``` kotlin
val D: UInt = 123u
```

Unsigned arrays 도 지원한다.<br>
`UByteArray`, `UshortArray`, `UIntArray`, `ULongArray`


## Explicit type declaration
지난 포스트에서 코틀린에서는 대입되는 값을 보고 변수의 타입을 자동으로 추론해주는걸 알았다.<br>
만약 변수를 초기화 없이 선언하거나 타입을 명확하게 써주고 싶을때는 어떻게 해야 할까?<br><br>
변수명 뒤에 `:Int`처럼 `:타입명`을 적어주면 된다.<br>

```kotlin
val A: Int // 초기화 없이 선언 
A = 10
print(A) // output: 10

val S: String = "ASDF" // 명시적으로 선언
```