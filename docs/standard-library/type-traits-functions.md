---
title: '&lt;&gt;funkcje type_traits'
ms.date: 11/04/2016
ms.assetid: dce4492f-f3e4-4d5e-bdb4-5875321254ec
helpviewer_keywords:
- std::is_assignable
- std::is_copy_assignable
- std::is_copy_constructible
- std::is_default_constructible
- std::is_move_assignable
- std::is_move_constructible
- std::is_nothrow_move_assignable
- std::is_trivially_copy_assignable
- std::is_trivially_move_assignable
- std::is_trivially_move_constructible
ms.openlocfilehash: d330a1dcd819dd48713887db789371ed4a8fee35
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215533"
---
# <a name="lttype_traitsgt-functions"></a>&lt;&gt;funkcje type_traits

||||
|-|-|-|
|[is_assignable](#is_assignable)|[is_copy_assignable](#is_copy_assignable)|[is_copy_constructible](#is_copy_constructible)|
|[is_default_constructible](#is_default_constructible)|[is_move_assignable](#is_move_assignable)|[is_move_constructible](#is_move_constructible)|
|[is_nothrow_move_assignable](#is_nothrow_move_assignable)|[is_nothrow_swappable](#is_nothrow_swappable)|[is_nothrow_swappable_with](#is_nothrow_swappable_with)|
|[is_swappable](#is_swappable)|[is_swappable_with](#is_swappable_with)|[is_trivially_copy_assignable](#is_trivially_copy_assignable)|
|[is_trivially_move_assignable](#is_trivially_move_assignable)|[is_trivially_move_constructible](#is_trivially_move_constructible)|

## <a name="is_assignable"></a><a name="is_assignable"></a>is_assignable

Testuje, czy wartość typu *from* może być przypisana do typu *do* .

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Parametry

*Do*\
Typ obiektu, który odbiera przypisanie.

*Wniosek*\
Typ obiektu, który zawiera wartość.

### <a name="remarks"></a>Uwagi

Wyrażenie nieoceniane `declval<To>() = declval<From>()` musi być poprawnie sformułowane. Oba elementy *od* i *do* muszą być pełnymi typami **`void`** lub tablicami nieznanego powiązania.

## <a name="is_copy_assignable"></a><a name="is_copy_assignable"></a>is_copy_assignable

Testuje, czy typ ma być kopiowany podczas przypisywania.

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>Parametry

*Br*\
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *ty* jest klasą, która ma operator przypisania kopii, w przeciwnym razie ma wartość false. Równoważne is_assignable \<Ty&, const Ty&> .

## <a name="is_copy_constructible"></a><a name="is_copy_constructible"></a>is_copy_constructible

Testuje, czy typ ma Konstruktor kopiujący.

```cpp
template <class Ty>
struct is_copy_constructible;
```

### <a name="parameters"></a>Parametry

*Br*\
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *ty* jest klasą, która ma Konstruktor kopiujący, w przeciwnym razie ma wartość false.

### <a name="example"></a>Przykład

```cpp
#include <type_traits>
#include <iostream>

struct Copyable
{
    int val;
};

struct NotCopyable
{
   NotCopyable(const NotCopyable&) = delete;
   int val;

};

int main()
{
    std::cout << "is_copy_constructible<Copyable> == " << std::boolalpha
        << std::is_copy_constructible<Copyable>::value << std::endl;
    std::cout << "is_copy_constructible<NotCopyable> == " << std::boolalpha
        << std::is_copy_constructible<NotCopyable>::value << std::endl;

    return (0);
}
```

```Output
is_copy_constructible<Copyable> == true
is_copy_constructible<NotCopyable > == false
```

## <a name="is_default_constructible"></a><a name="is_default_constructible"></a>is_default_constructible

Testuje, czy typ ma konstruktora domyślnego.

```cpp
template <class Ty>
struct is_default_constructible;
```

### <a name="parameters"></a>Parametry

*&*\
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *T* jest typem klasy z konstruktorem domyślnym, w przeciwnym razie ma wartość false. Jest to odpowiednik predykatu `is_constructible<T>` . Typ *T* musi być kompletnym typem **`void`** lub tablicą nieznanego powiązania.

### <a name="example"></a>Przykład

```cpp
#include <type_traits>
#include <iostream>

struct Simple
{
    Simple() : val(0) {}
    int val;
};

struct Simple2
{
    Simple2(int v) : val(v) {}
    int val;
};

int main()
{
    std::cout << "is_default_constructible<Simple> == " << std::boolalpha
        << std::is_default_constructible<Simple>::value << std::endl;
    std::cout << "is_default_constructible<Simple2> == " << std::boolalpha
        << std::is_default_constructible<Simple2>::value << std::endl;

    return (0);
}
```

```Output
is_default_constructible<Simple> == true
is_default_constructible<Simple2> == false
```

## <a name="is_move_assignable"></a><a name="is_move_assignable"></a>is_move_assignable

Testuje, czy można przenieść typ.

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>Parametry

*&*\
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Typ jest przesuwany do przypisania, jeśli odwołanie rvalue do typu może zostać przypisane do odwołania do typu. Predykat typu jest równoważny z `is_assignable<T&, T&&>` . Przenieś typy z możliwością przypisania zawierają typy skalarne i typy klas, które mają zdefiniowane przez użytkownika operatory przypisania przenoszenia.

## <a name="is_move_constructible"></a><a name="is_move_constructible"></a>is_move_constructible

Testuje, czy typ ma Konstruktor przenoszenia.

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Parametry

*&*\
Typ, który ma zostać obliczony

### <a name="remarks"></a>Uwagi

Predykat typu, którego wynikiem jest wartość true, jeśli typ *T* może być skonstruowany przy użyciu operacji przenoszenia. Ten predykat jest odpowiednikiem `is_constructible<T, T&&>` .

## <a name="is_nothrow_move_assignable"></a><a name="is_nothrow_move_assignable"></a>is_nothrow_move_assignable

Testuje, czy typ ma **`nothrow`** operator przypisania przenoszenia.

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>Parametry

*Br*\
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *ty* ma operator przypisania operacji przenoszenia nothrow, w przeciwnym razie ma wartość false.

## <a name="is_nothrow_swappable"></a><a name="is_nothrow_swappable"></a>is_nothrow_swappable

```cpp
template <class T> struct is_nothrow_swappable;
```

## <a name="is_nothrow_swappable_with"></a><a name="is_nothrow_swappable_with"></a>is_nothrow_swappable_with

```cpp
template <class T, class U> struct is_nothrow_swappable_with;
```

## <a name="is_swappable"></a><a name="is_swappable"></a>is_swappable

```cpp
template <class T> struct is_swappable;
```

## <a name="is_swappable_with"></a><a name="is_swappable_with"></a>is_swappable_with

```cpp
template <class T, class U> struct is_swappable_with;
```

## <a name="is_trivially_copy_assignable"></a><a name="is_trivially_copy_assignable"></a>is_trivially_copy_assignable

Testuje, czy typ ma operator przypisania prostego kopiowania.

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Parametry

*&*\
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *T* jest klasą, która ma operator przypisania prostego kopiowania, w przeciwnym razie zawiera wartość false.

Konstruktor przypisania dla klasy *t* jest uproszczony, jeśli jest niejawnie określony, Klasa *t* nie ma żadnych funkcji wirtualnych, Klasa *t* nie ma żadnych wirtualnych podstaw, klasy wszystkich niestatycznych elementów członkowskich danych typu klasy mają proste operatory przypisania, a klasy wszystkich niestatycznych elementów członkowskich danych typu Array klasy mają proste operatory przypisania.

## <a name="is_trivially_move_assignable"></a><a name="is_trivially_move_assignable"></a>is_trivially_move_assignable

Testuje, czy typ ma operator przypisania prostego przenoszenia.

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parametry

*Br*\
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *ty* jest klasą, która ma operator przypisania prostego przenoszenia, w przeciwnym razie ma wartość false.

Operator przypisania przenoszenia dla klasy *ty* jest prosty, jeśli:

jest to niejawnie podane

Klasa *ty* nie ma żadnych funkcji wirtualnych

Klasa *ty* nie ma wirtualnych baz.

klasy wszystkich niestatycznych elementów członkowskich danych typu klasy mają operatory przypisania prostego przenoszenia

klasy wszystkich niestatycznych składowych danych typu Array klasy mają operatory przypisania prostego przenoszenia

## <a name="is_trivially_move_constructible"></a><a name="is_trivially_move_constructible"></a>is_trivially_move_constructible

Testuje, czy typ ma Konstruktor prostego przenoszenia.

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Parametry

*Br*\
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *ty* jest klasą, która ma prosty Konstruktor przenoszenia, w przeciwnym razie ma wartość false.

Konstruktor przenoszenia dla klasy *ty* jest prosty, jeśli:

jest on niejawnie zadeklarowany

jego typy parametrów są równoważne z niejawną deklaracją

Klasa *ty* nie ma żadnych funkcji wirtualnych

Klasa *ty* nie ma wirtualnych baz.

Klasa nie ma niestatycznych elementów członkowskich danych

wszystkie bezpośrednie bazy klasy *ty* mają konstruktorów prostego przenoszenia

klasy wszystkich niestatycznych składowych danych typu klasy mają konstruktorów prostych przenoszenia

klasy wszystkich niestatycznych składowych danych typu Array klasy mają konstruktorów prostego przenoszenia

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
