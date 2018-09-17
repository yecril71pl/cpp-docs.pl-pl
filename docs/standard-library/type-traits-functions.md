---
title: '&lt;type_traits&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- type_traits/std::is_assignable
- type_traits/std::is_copy_assignable
- type_traits/std::is_copy_constructible
- type_traits/std::is_default_constructible
- type_traits/std::is_move_assignable
- type_traits/std::is_move_constructible
- type_traits/std::is_nothrow_move_assignable
- type_traits/std::is_trivially_copy_assignable
- type_traits/std::is_trivially_move_assignable
- type_traits/std::is_trivially_move_constructible
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
ms.openlocfilehash: 551282b6d99491e49a185bab2ede2f775bb55498
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707827"
---
# <a name="lttypetraitsgt-functions"></a>&lt;type_traits&gt; funkcji

||||
|-|-|-|
|[is_assignable](#is_assignable)|[is_copy_assignable](#is_copy_assignable)|[is_copy_constructible](#is_copy_constructible)|
|[is_default_constructible](#is_default_constructible)|[is_move_assignable](#is_move_assignable)|[is_move_constructible](#is_move_constructible)|
|[is_nothrow_move_assignable](#is_nothrow_move_assignable)|[is_trivially_copy_assignable](#is_trivially_copy_assignable)|[is_trivially_move_assignable](#is_trivially_move_assignable)|
|[is_trivially_move_constructible](#is_trivially_move_constructible)|

## <a name="is_assignable"></a>  is_assignable

Sprawdza, czy wartość *z* typu mogą być przypisane do *do* typu.

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Parametry

*To*<br/>
Typ obiektu, który odbiera przypisania.

*From*<br/>
Typ obiektu, który zawiera wartość.

### <a name="remarks"></a>Uwagi

Wyrażenie nieobliczonym `declval<To>() = declval<From>()` musi być poprawnie sformułowany. Zarówno *z* i *do* muszą być typami pełnymi **void**, lub tablic nieznany powiązane z.

## <a name="is_copy_assignable"></a>  is_copy_assignable

Testy czy typ ma można kopiować przypisania.

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *Ty* to klasa, która zawiera operator przypisania kopii, w przeciwnym razie przechowuje wartość false. Odpowiednikiem is_assignable\<Ty & const Ty & >.

## <a name="is_copy_constructible"></a>  is_copy_constructible

Sprawdza, czy typ ma konstruktora kopiującego.

```cpp
template <class Ty>
struct is_copy_constructible;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *Ty* to klasa, która ma Konstruktor kopiujący w przeciwnym razie przechowuje wartość false.

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

## <a name="is_default_constructible"></a>  is_default_constructible

Sprawdza, czy typ ma konstruktora domyślnego.

```cpp
template <class Ty>
struct is_default_constructible;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *T* jest typu klasy, która ma Konstruktor domyślny w przeciwnym razie przechowuje wartość false. Jest to równoważne do predykatu `is_constructible<T>`. Typ *T* musi być typem kompletnym **void**, lub tablicę nieznany powiązane z.

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

## <a name="is_move_assignable"></a>  is_move_assignable

Sprawdza, czy typ może być przejście przypisane.

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Typ jest możliwy do przypisania przeniesienia, jeśli odwołania rvalue do tego typu mogą być przypisane do odwołanie do typu. Predykat typów jest odpowiednikiem `is_assignable<T&, T&&>`. Przenieś można przypisać typy obejmują którego można się odwoływać typów skalarnych i typów klasy, które mają generowanych przez kompilator lub zdefiniowanych przez użytkownika operatorów przypisania przenoszenia.

## <a name="is_move_constructible"></a>  is_move_constructible

Sprawdza, czy typ ma konstruktora przenoszącego.

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, który ma zostać obliczone

### <a name="remarks"></a>Uwagi

Predykat typów, które daje w wyniku wartość true, jeśli typ *T* można skonstruować przy użyciu operacji przenoszenia. Ten predykat jest odpowiednikiem `is_constructible<T, T&&>`.

## <a name="is_nothrow_move_assignable"></a>  is_nothrow_move_assignable

Sprawdza, czy typ ma **nothrow** przenoszący operator przypisania.

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *Ty* ma nothrow operator przypisania przenoszenia, w przeciwnym razie przechowuje wartość false.

## <a name="is_trivially_copy_assignable"></a>  is_trivially_copy_assignable

Sprawdza, czy typ ma operator przypisania kopiowania prosta.

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *T* to klasa, która ma proste operatora przypisanej kopii, w przeciwnym razie przechowuje wartość false.

Konstruktor przypisania dla klasy *T* jest proste, jeśli jest niejawnie podany, klasa *T* ma żadnych funkcji wirtualnych klasy *T* ma nie baz wirtualnych klas Wszyscy członkowie danych niestatycznych typu klasy mają operatory przypisania proste, a klasy wszystkie składowe danych niestatycznych tablicy typu klasy mieć operatory przypisania prosta.

## <a name="is_trivially_move_assignable"></a>  is_trivially_move_assignable

Sprawdza, czy typ ma operator przypisania przenoszenia prosta.

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *Ty* to klasa, która ma proste operator przypisania przenoszenia, w przeciwnym razie przechowuje wartość false.

Operator przypisania przenoszenia dla klasy *Ty* jest proste jeśli:

Domyślnie jest ona udostępniana

Klasa *Ty* ma żadnych funkcji wirtualnych

Klasa *Ty* ma nie baz wirtualnych

klasy wszystkie składowe danych niestatycznych typu klasy mają trivial przenoszące operatory przypisania

klasy wszystkie składowe danych niestatycznych typu tablicowego klasy mają trivial przenoszące operatory przypisania

## <a name="is_trivially_move_constructible"></a>  is_trivially_move_constructible

Konstruktor przenoszący sprawdza, czy typ ma proste.

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

### <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *Ty* to klasa, która ma Konstruktor przenoszący prosta w przeciwnym razie przechowuje wartość false.

Konstruktor przenoszący dla klasy *Ty* jest proste jeśli:

jest niejawnie zadeklarowana

jego typy parametrów są równoważne do tych deklaracji niejawnej

Klasa *Ty* ma żadnych funkcji wirtualnych

Klasa *Ty* ma nie baz wirtualnych

Klasa nie ma danych niestatycznych elementów członkowskich

wszystkie bezpośrednio baz klasy *Ty* ma konstruktorów przenoszących prosta

klasy wszystkie składowe danych niestatycznych typu klasy ma konstruktorów przenoszących prosta

klasy wszystkie składowe danych niestatycznych typu tablicowego klasy ma konstruktorów przenoszących prosta

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
