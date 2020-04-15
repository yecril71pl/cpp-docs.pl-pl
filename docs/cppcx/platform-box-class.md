---
title: Platforma::Klasa box
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
ms.openlocfilehash: 7484bcda3f05a8a9e56a33222d0630d4597e1219
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354760"
---
# <a name="platformbox-class"></a>Platforma::Klasa box

Włącza typ wartości, `Windows::Foundation::DateTime` takich jak lub `int` typu skalarnego, takich jak mają być przechowywane w typie. `Platform::Object` Zwykle nie jest konieczne `Box` jawne używanie, ponieważ boks odbywa `Object^`się niejawnie podczas rzutowanie typu wartości do .

### <a name="syntax"></a>Składnia

```cpp
ref class Box abstract;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** vccorlib.h

**Obszar nazw:** Platformy

### <a name="members"></a>Elementy członkowskie

|Członek|Opis|
|------------|-----------------|
|[Box](#ctor) | Tworzy, `Box` który może hermetyzować wartość określonego typu. |
|[operator&lt;Skrzynka const T&gt;^](#box-const-t) | Włącza konwersje bokserskie `T` z `enum` `T` klasy `Box<T>` `const` wartości lub klasy do . |
|[operator&lt;Box const volatile T&gt;^](#box-const-volatile-t) | Włącza konwersje bokserskie `T` z `enum` `T` klasy `Box<T>` `const volatile` wartości lub typu do . |
|[ramka&lt;operatora T&gt;^](#box-t) | Włącza konwersje bokserskie `T` z `Box<T>`klasy wartości do . |
|[operator&lt;Box volatile T&gt;^](#box-volatile-t) | Włącza konwersje bokserskie `T` z `enum` `T` klasy `Box<T>` `volatile` wartości lub typu do . |
|[Pole::operator T](#t) | Włącza konwersje bokserskie `T` z `enum` `T` klasy `Box<T>`wartości lub klasy do . |
|[Value — Właściwość](#value) | Zwraca wartość, która jest hermetyzowana w `Box` obiekcie. |

## <a name="boxbox-constructor"></a><a name="ctor"></a>Pole::Konstruktor pól

Tworzy, `Box` który może hermetyzować wartość określonego typu.

### <a name="syntax"></a>Składnia

```cpp
Box(T valueArg);
```

### <a name="parameters"></a>Parametry

*wartośćArg*<br/>
Typ wartości, która ma być zapakowana `bool` `float64`— `DateTime`na przykład `int`, , , .

## <a name="boxoperator-boxltconst-tgt-operator"></a><a name="box-const-t"></a>Pole::operator&lt;Pole const T&gt;^ Operator

Włącza konwersje bokserskie `T` z `enum` `T` klasy `Box<T>` `const` wartości lub klasy do .

### <a name="syntax"></a>Składnia

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Dowolna klasa wartości, struktura wartości lub typ wyliczenia. Zawiera wbudowane typy w [domyślnej przestrzeni nazw](../cppcx/default-namespace.md).

### <a name="return-value"></a>Wartość zwracana

Wystąpienie, `Platform::Box<T>^` które reprezentuje oryginalną wartość w klasie ref.

## <a name="boxoperator-boxltconst-volatile-tgt-operator"></a><a name="box-const-volatile-t"></a>Pole::operator&lt;Pole const&gt;volatile T ^ Operator

Włącza konwersje bokserskie `T` z `enum` `T` klasy `Box<T>` `const volatile` wartości lub typu do .

### <a name="syntax"></a>Składnia

```cpp
operator Box<const volatile T>^(const volatile T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Dowolny typ wyliczenia, klasa wartości lub struktura wartości. Zawiera wbudowane typy w [domyślnej przestrzeni nazw](../cppcx/default-namespace.md).

### <a name="return-value"></a>Wartość zwracana

Wystąpienie, `Platform::Box<T>^` które reprezentuje oryginalną wartość w klasie ref.

## <a name="boxoperator-boxlttgt-operator"></a><a name="box-t"></a>Pole::operator&lt;Box&gt;T ^ Operator

Włącza konwersje bokserskie `T` z `Box<T>`klasy wartości do .

### <a name="syntax"></a>Składnia

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Dowolny typ wyliczenia, klasa wartości lub struktura wartości. Zawiera wbudowane typy w [domyślnej przestrzeni nazw](../cppcx/default-namespace.md).

### <a name="return-value"></a>Wartość zwracana

Wystąpienie, `Platform::Box<T>^` które reprezentuje oryginalną wartość w klasie ref.

## <a name="boxoperator-boxltvolatile-tgt-operator"></a><a name="box-volatile-t"></a>Pole::operator&lt;Pole&gt;volatile T ^ Operator

Włącza konwersje bokserskie `T` z `enum` `T` klasy `Box<T>` `volatile` wartości lub typu do .

### <a name="syntax"></a>Składnia

```cpp
operator Box<volatile T>^(volatile T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Dowolny typ wyliczenia, klasa wartości lub struktura wartości. Zawiera wbudowane typy w [domyślnej przestrzeni nazw](../cppcx/default-namespace.md).

### <a name="return-value"></a>Wartość zwracana

Wystąpienie, `Platform::Box<T>^` które reprezentuje oryginalną wartość w klasie ref.

## <a name="boxoperator-t-operator"></a><a name="t"></a>Pole::operator T Operator

Włącza konwersje bokserskie `T` z `enum` `T` klasy `Box<T>`wartości lub klasy do .

### <a name="syntax"></a>Składnia

```cpp
operator Box<T>^(T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Dowolny typ wyliczenia, klasa wartości lub struktura wartości. Zawiera wbudowane typy w [domyślnej przestrzeni nazw](../cppcx/default-namespace.md).

### <a name="return-value"></a>Wartość zwracana

Wystąpienie, `Platform::Box<T>^` które reprezentuje oryginalną wartość w klasie ref.

## <a name="boxvalue-property"></a><a name="value"></a>Pole::Właściwość value

Zwraca wartość, która jest hermetyzowana w `Box` obiekcie.

### <a name="syntax"></a>Składnia

```cpp
virtual property T Value{
   T get();
}
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość pudełkową o tym samym typie, który był pierwotnie wcześniej, zanim został zapakowany.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)<br/>
[Boxing](../cppcx/boxing-c-cx.md)
