---
title: 'Platform:: Box — Klasa'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
ms.openlocfilehash: 6afc12dbc3f6980bb7fd42d7f0a8fdc9e6d0e284
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232173"
---
# <a name="platformbox-class"></a>Platform:: Box — Klasa

Włącza typ wartości, taki jak `Windows::Foundation::DateTime` lub typ skalarny, taki jak, **`int`** który ma być przechowywany w `Platform::Object` typie. Zwykle nie jest to konieczne użycie `Box` jawnie, ponieważ opakowanie jest niejawnie wykonywane podczas rzutowania typu wartości na `Object^` .

### <a name="syntax"></a>Składnia

```cpp
ref class Box abstract;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** vccorlib. h

**Przestrzeń nazw:** Platformach

### <a name="members"></a>Elementy członkowskie

|Członek|Opis|
|------------|-----------------|
|[Box](#ctor) | Tworzy obiekt `Box` , który może hermetyzować wartość określonego typu. |
|[Pole operatora &lt; const T&gt;^](#box-const-t) | Włącza konwersje pakujące z **`const`** klasy wartości `T` lub **`enum`** klasy `T` do `Box<T>` . |
|[Pole operatora &lt; const volatile T&gt;^](#box-const-volatile-t) | Włącza konwersje pakujące z **`const volatile`** klasy wartości `T` lub **`enum`** typu `T` do `Box<T>` . |
|[Pole operatora &lt; T&gt;^](#box-t) | Włącza konwersje pakujące z klasy wartości `T` do `Box<T>` . |
|[Pole operatora &lt; unvolatile T&gt;^](#box-volatile-t) | Włącza konwersje pakujące z **`volatile`** klasy wartości `T` lub **`enum`** typu `T` do `Box<T>` . |
|[Box:: operator T](#t) | Włącza konwersje pakujące z klasy wartości `T` lub **`enum`** klasy `T` do `Box<T>` . |
|[Value — Właściwość](#value) | Zwraca wartość, która jest hermetyzowana w `Box` obiekcie. |

## <a name="boxbox-constructor"></a><a name="ctor"></a>Box:: Box — Konstruktor

Tworzy obiekt `Box` , który może hermetyzować wartość określonego typu.

### <a name="syntax"></a>Składnia

```cpp
Box(T valueArg);
```

### <a name="parameters"></a>Parametry

*valueArg*<br/>
Typ wartości, która ma być opakowany — na przykład,,, **`int`** **`bool`** `float64` `DateTime` .

## <a name="boxoperator-boxltconst-tgt-operator"></a><a name="box-const-t"></a>Box:: operator — pole &lt; const T &gt; ^ — operator

Włącza konwersje pakujące z **`const`** klasy wartości `T` lub **`enum`** klasy `T` do `Box<T>` .

### <a name="syntax"></a>Składnia

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Dowolna klasa wartości, struktura wartości lub typ wyliczeniowy. Zawiera wbudowane typy w [domyślnej przestrzeni nazw](../cppcx/default-namespace.md).

### <a name="return-value"></a>Wartość zwracana

`Platform::Box<T>^`Wystąpienie, które reprezentuje oryginalną wartość opakowaną w klasie ref.

## <a name="boxoperator-boxltconst-volatile-tgt-operator"></a><a name="box-const-volatile-t"></a>Box:: operator Box &lt; const volatile T &gt; ^ operator

Włącza konwersje pakujące z **`const volatile`** klasy wartości `T` lub **`enum`** typu `T` do `Box<T>` .

### <a name="syntax"></a>Składnia

```cpp
operator Box<const volatile T>^(const volatile T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Dowolny typ wyliczenia, Klasa wartości lub struktura wartości. Zawiera wbudowane typy w [domyślnej przestrzeni nazw](../cppcx/default-namespace.md).

### <a name="return-value"></a>Wartość zwracana

`Platform::Box<T>^`Wystąpienie, które reprezentuje oryginalną wartość opakowaną w klasie ref.

## <a name="boxoperator-boxlttgt-operator"></a><a name="box-t"></a>Box:: operator Box &lt; T &gt; ^

Włącza konwersje pakujące z klasy wartości `T` do `Box<T>` .

### <a name="syntax"></a>Składnia

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Dowolny typ wyliczenia, Klasa wartości lub struktura wartości. Zawiera wbudowane typy w [domyślnej przestrzeni nazw](../cppcx/default-namespace.md).

### <a name="return-value"></a>Wartość zwracana

`Platform::Box<T>^`Wystąpienie, które reprezentuje oryginalną wartość opakowaną w klasie ref.

## <a name="boxoperator-boxltvolatile-tgt-operator"></a><a name="box-volatile-t"></a>Box:: operator — &lt; nietrwały &gt; operator T ^

Włącza konwersje pakujące z **`volatile`** klasy wartości `T` lub **`enum`** typu `T` do `Box<T>` .

### <a name="syntax"></a>Składnia

```cpp
operator Box<volatile T>^(volatile T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Dowolny typ wyliczenia, Klasa wartości lub struktura wartości. Zawiera wbudowane typy w [domyślnej przestrzeni nazw](../cppcx/default-namespace.md).

### <a name="return-value"></a>Wartość zwracana

`Platform::Box<T>^`Wystąpienie, które reprezentuje oryginalną wartość opakowaną w klasie ref.

## <a name="boxoperator-t-operator"></a><a name="t"></a>Box:: operator T — operator

Włącza konwersje pakujące z klasy wartości `T` lub **`enum`** klasy `T` do `Box<T>` .

### <a name="syntax"></a>Składnia

```cpp
operator Box<T>^(T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Dowolny typ wyliczenia, Klasa wartości lub struktura wartości. Zawiera wbudowane typy w [domyślnej przestrzeni nazw](../cppcx/default-namespace.md).

### <a name="return-value"></a>Wartość zwracana

`Platform::Box<T>^`Wystąpienie, które reprezentuje oryginalną wartość opakowaną w klasie ref.

## <a name="boxvalue-property"></a><a name="value"></a>Box:: Value — właściwość

Zwraca wartość, która jest hermetyzowana w `Box` obiekcie.

### <a name="syntax"></a>Składnia

```cpp
virtual property T Value{
   T get();
}
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość opakowaną tego samego typu, który pierwotnie miał przed zapisaniem.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)<br/>
[Boxing](../cppcx/boxing-c-cx.md)
