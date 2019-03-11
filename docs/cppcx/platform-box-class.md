---
title: Platform::Box, klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
ms.openlocfilehash: ca8c9229d0ef5fa654f462282f257b1684984102
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742941"
---
# <a name="platformbox-class"></a>Platform::Box, klasa

Umożliwia to typ wartości takie jak `Windows::Foundation::DateTime` lub typem skalarne, takie jak `int` mają być przechowywane w `Platform::Object` typu. Zazwyczaj nie jest konieczne użycie `Box` jawnie, ponieważ pakowania się stanie, niejawnie przypadku rzutowania typu wartości do `Object^`.

### <a name="syntax"></a>Składnia

```cpp
ref class Box abstract;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** vccorlib.h

**Namespace:** Platforma

### <a name="members"></a>Elementy członkowskie

|Element członkowski|Opis|
|------------|-----------------|
|[Box](#ctor) | Tworzy `Box` który umożliwiająca Hermetyzowanie wartość określonego typu. |
|[Operator pole&lt;const T&gt;^](#box-const-t) | Umożliwia konwersje boxing z `const` klasę wartości `T` lub `enum` klasy `T` do `Box<T>`. |
|[Operator pole&lt;const volatile T&gt;^](#box-const-volatile-t) | Umożliwia konwersje boxing z `const volatile` klasę wartości `T` lub `enum` typu `T` do `Box<T>`. |
|[Operator pole&lt;T&gt;^](#box-t) | Umożliwia konwersje boxing z klasą wartości `T` do `Box<T>`. |
|[Operator pole&lt;volatile T&gt;^](#box-volatile-t) | Umożliwia konwersje boxing z `volatile` klasę wartości `T` lub `enum` typu `T` do `Box<T>`. |
|[Box::operator T](#t) | Umożliwia konwersje boxing z klasą wartości `T` lub `enum` klasy `T` do `Box<T>`. |
|[Wartość właściwości](#value) | Zwraca wartość, która jest hermetyzowany w `Box` obiektu. |

## <a name="ctor"></a> Konstruktor Box::Box

Tworzy `Box` który umożliwiająca Hermetyzowanie wartość określonego typu.

### <a name="syntax"></a>Składnia

```cpp
Box(T valueArg);
```

### <a name="parameters"></a>Parametry

*valueArg*<br/>
Typ wartości, aby zostać opakowany — na przykład `int`, `bool`, `float64`, `DateTime`.

## <a name="box-const-t"></a> Pole Box::operator&lt;const T&gt;^ — Operator

Umożliwia konwersje boxing z `const` klasę wartości `T` lub `enum` klasy `T` do `Box<T>`.

### <a name="syntax"></a>Składnia

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Wszystkie wartości klasy, struktury wartości lub typu wyliczeniowego. Zawiera typy wbudowane w [domyślny obszar nazw](../cppcx/default-namespace.md).

### <a name="return-value"></a>Wartość zwracana

A `Platform::Box<T>^` wystąpienia, która reprezentuje wartość oryginalną opakowany w klasie ref.

## <a name="box-const-volatile-t"></a> Pole Box::operator&lt;const volatile T&gt;^ — Operator

Umożliwia konwersje boxing z `const volatile` klasę wartości `T` lub `enum` typu `T` do `Box<T>`.

### <a name="syntax"></a>Składnia

```cpp
operator Box<const volatile T>^(const volatile T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Dowolnego typu wyliczeniowego, wartość klasy lub struktury wartości. Zawiera typy wbudowane w [domyślny obszar nazw](../cppcx/default-namespace.md).

### <a name="return-value"></a>Wartość zwracana

A `Platform::Box<T>^` wystąpienia, która reprezentuje wartość oryginalną opakowany w klasie ref.

## <a name="box-t"></a> Pole Box::operator&lt;T&gt;^ — Operator

Umożliwia konwersje boxing z klasą wartości `T` do `Box<T>`.

### <a name="syntax"></a>Składnia

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Dowolnego typu wyliczeniowego, wartość klasy lub struktury wartości. Zawiera typy wbudowane w [domyślny obszar nazw](../cppcx/default-namespace.md).

### <a name="return-value"></a>Wartość zwracana

A `Platform::Box<T>^` wystąpienia, która reprezentuje wartość oryginalną opakowany w klasie ref.

## <a name="box-volatile-t"></a> Pole Box::operator&lt;volatile T&gt;^ — Operator

Umożliwia konwersje boxing z `volatile` klasę wartości `T` lub `enum` typu `T` do `Box<T>`.

### <a name="syntax"></a>Składnia

```cpp
operator Box<volatile T>^(volatile T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Dowolnego typu wyliczeniowego, wartość klasy lub struktury wartości. Zawiera typy wbudowane w [domyślny obszar nazw](../cppcx/default-namespace.md).

### <a name="return-value"></a>Wartość zwracana

A `Platform::Box<T>^` wystąpienia, która reprezentuje wartość oryginalną opakowany w klasie ref.

## <a name="t"></a>  Operator Box::operator T

Umożliwia konwersje boxing z klasą wartości `T` lub `enum` klasy `T` do `Box<T>`.

### <a name="syntax"></a>Składnia

```cpp
operator Box<T>^(T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Dowolnego typu wyliczeniowego, wartość klasy lub struktury wartości. Zawiera typy wbudowane w [domyślny obszar nazw](../cppcx/default-namespace.md).

### <a name="return-value"></a>Wartość zwracana

A `Platform::Box<T>^` wystąpienia, która reprezentuje wartość oryginalną opakowany w klasie ref.

## <a name="value"></a> Właściwość Box::Value

Zwraca wartość, która jest hermetyzowany w `Box` obiektu.

### <a name="syntax"></a>Składnia

```cpp
virtual property T Value{
   T get();
}
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartości spakowanej, za pomocą tego samego typu pierwotnie miała zanim został on ramce.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)<br/>
[Konwersja boxing](../cppcx/boxing-c-cx.md)
