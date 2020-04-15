---
title: '&lt;&gt; funkcje type_traits'
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
ms.openlocfilehash: bc25c82629139c5bc2f6fa53d3555068374dca35
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367987"
---
# <a name="lttype_traitsgt-functions"></a>&lt;&gt; funkcje type_traits

||||
|-|-|-|
|[is_assignable](#is_assignable)|[is_copy_assignable](#is_copy_assignable)|[is_copy_constructible](#is_copy_constructible)|
|[is_default_constructible](#is_default_constructible)|[is_move_assignable](#is_move_assignable)|[is_move_constructible](#is_move_constructible)|
|[is_nothrow_move_assignable](#is_nothrow_move_assignable)|[is_nothrow_swappable](#is_nothrow_swappable)|[is_nothrow_swappable_with](#is_nothrow_swappable_with)|
|[is_swappable](#is_swappable)|[is_swappable_with](#is_swappable_with)|[is_trivially_copy_assignable](#is_trivially_copy_assignable)|
|[is_trivially_move_assignable](#is_trivially_move_assignable)|[is_trivially_move_constructible](#is_trivially_move_constructible)|

## <a name="is_assignable"></a><a name="is_assignable"></a>is_assignable

Sprawdza, czy wartość *od* typu można przypisać do *do* typu.

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Parametry

*Do*\
Typ obiektu, który odbiera przypisanie.

*Z*\
Typ obiektu, który zapewnia wartość.

### <a name="remarks"></a>Uwagi

Wyrażenie nieoceniowe `declval<To>() = declval<From>()` musi być dobrze sformułowane. Zarówno *od,* jak i *do* musi być pełne typy, **void**lub tablice nieznane powiązane.

## <a name="is_copy_assignable"></a><a name="is_copy_assignable"></a>is_copy_assignable

Sprawdza, czy typ może być kopiowany podczas przypisywania.

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>Parametry

*Ty (ty)*\
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *Ty* jest klasą, która ma operator przypisania kopii, w przeciwnym razie posiada false. Odpowiednik is_assignable\<Ty&, const Ty&>.

## <a name="is_copy_constructible"></a><a name="is_copy_constructible"></a>is_copy_constructible

Testy, jeśli typ ma konstruktora kopii.

```cpp
template <class Ty>
struct is_copy_constructible;
```

### <a name="parameters"></a>Parametry

*Ty (ty)*\
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *Ty* jest klasą, która ma konstruktora kopii, w przeciwnym razie posiada false.

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

Testy, jeśli typ ma domyślny konstruktor.

```cpp
template <class Ty>
struct is_default_constructible;
```

### <a name="parameters"></a>Parametry

*T*\
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *T* jest typem klasy, który ma domyślny konstruktor, w przeciwnym razie posiada false. Jest to równoważne z `is_constructible<T>`predykatem . Typ *T* musi być typem kompletnym, **void**lub tablicą o nieznanej granicy.

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

Sprawdza, czy typ można przenieść przypisane.

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>Parametry

*T*\
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Typ jest przesuwany, jeśli odwołanie rvalue do typu można przypisać do odwołania do typu. Predykat typu jest `is_assignable<T&, T&&>`odpowiednikiem . Przenieść przypisywane typy obejmują typy skalarne odniesienia i typy klas, które mają generowane przez kompilator lub zdefiniowane przez użytkownika operatory przypisania przenoszenia.

## <a name="is_move_constructible"></a><a name="is_move_constructible"></a>is_move_constructible

Sprawdza, czy typ ma konstruktora przenoszenia.

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Parametry

*T*\
Typ, który ma zostać oceniony

### <a name="remarks"></a>Uwagi

Predykat typu, który ocenia true, jeśli typ *T* mogą być konstruowane przy użyciu operacji przenoszenia. Ten predykat jest `is_constructible<T, T&&>`odpowiednikiem .

## <a name="is_nothrow_move_assignable"></a><a name="is_nothrow_move_assignable"></a>is_nothrow_move_assignable

Sprawdza, czy typ ma operator przypisania **przenoszenia niehrow.**

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>Parametry

*Ty (ty)*\
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *Ty* ma operator przypisania przenoszenia nothrow, w przeciwnym razie zawiera false.

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

Sprawdza, czy typ ma operator przypisywania kopii trywialne.

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Parametry

*T*\
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *T* jest klasą, która ma operator przypisania kopii trywialne, w przeciwnym razie posiada false.

Konstruktor przypisania dla klasy *T* jest trywialny, jeśli jest niejawnie pod warunkiem, klasa *T* nie ma funkcji wirtualnych, klasa *T* nie ma podstaw wirtualnych, klasy wszystkich niestatycznych elementów członkowskich danych typu klasy mają operatory przydziału trywialne, a klasy wszystkich niestatycznych elementów członkowskich danych klasy mają trywialne operatory przypisania.

## <a name="is_trivially_move_assignable"></a><a name="is_trivially_move_assignable"></a>is_trivially_move_assignable

Sprawdza, czy typ ma operator przydziału transferu trywialne.

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parametry

*Ty (ty)*\
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *Ty* jest klasą, która ma operator przypisania przeniesienia trywialne, w przeciwnym razie posiada false.

Operator przypisania przenoszenia dla klasy *Ty* jest trywialny, jeśli:

jest ona w sposób dorozumiany

klasa *Ty* nie ma funkcji wirtualnych

klasa *Ty* nie ma wirtualnych baz

klasy wszystkich niestatycznych elementów członkowskich danych typu klasy mają trywialne operatory przypisania przenoszenia

klasy wszystkich niestatycznych elementów członkowskich danych tablicy typów klasy mają trywialne operatory przypisania przenoszenia

## <a name="is_trivially_move_constructible"></a><a name="is_trivially_move_constructible"></a>is_trivially_move_constructible

Testy, jeśli typ ma konstruktora ruchu trywialne.

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Parametry

*Ty (ty)*\
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *Ty* jest klasą, która ma konstruktora ruchu trywialne, w przeciwnym razie posiada false.

Konstruktor przenoszenia dla klasy *Ty* jest trywialny, jeśli:

jest w sposób dorozumiany zadeklarowany

jego typy parametrów są równoważne z typami niejawnej deklaracji

klasa *Ty* nie ma funkcji wirtualnych

klasa *Ty* nie ma wirtualnych baz

klasa nie ma nietrwałych niestatycznych elementów członkowskich danych

wszystkie bezpośrednie podstawy klasy *Ty* mają trywialne konstruktory ruchu

klasy wszystkich niestatycznych elementów członkowskich danych typu klasy mają trywialne konstruktory przenoszenia

klasy wszystkich niestatycznych elementów członkowskich danych tablicy typu klasy mają trywialne konstruktory przenoszenia

## <a name="see-also"></a>Zobacz też

[<type_traits>](../standard-library/type-traits.md)
