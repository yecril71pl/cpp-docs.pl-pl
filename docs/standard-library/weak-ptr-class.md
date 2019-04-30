---
title: weak_ptr — Klasa
ms.date: 11/04/2016
f1_keywords:
- memory/std::weak_ptr
- memory/std::weak_ptr::element_type
- memory/std::weak_ptr::expired
- memory/std::weak_ptr::lock
- memory/std::weak_ptr::owner_before
- memory/std::weak_ptr::reset
- memory/std::weak_ptr::swap
- memory/std::weak_ptr::use_count
- memory/std::weak_ptr::operator=
helpviewer_keywords:
- std::weak_ptr [C++]
- std::weak_ptr [C++], element_type
- std::weak_ptr [C++], expired
- std::weak_ptr [C++], lock
- std::weak_ptr [C++], owner_before
- std::weak_ptr [C++], reset
- std::weak_ptr [C++], swap
- std::weak_ptr [C++], use_count
- std::weak_ptr [C++], element_type
- std::weak_ptr [C++], expired
- std::weak_ptr [C++], lock
- std::weak_ptr [C++], owner_before
- std::weak_ptr [C++], reset
- std::weak_ptr [C++], swap
- std::weak_ptr [C++], use_count
ms.assetid: 2db4afb2-c7be-46fc-9c20-34ec2f8cc7c2
ms.openlocfilehash: e2efb5d534ad43e2492ac4fb0bf76db402dca272
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410864"
---
# <a name="weakptr-class"></a>weak_ptr — Klasa

Otacza słabo połączony wskaźnik.

## <a name="syntax"></a>Składnia

```cpp
template<class _Ty>
   class weak_ptr {
public:
   typedef Ty element_type;
   weak_ptr();
   weak_ptr(const weak_ptr&);
   template <class Other>
      weak_ptr(const weak_ptr<Other>&);
   template <class Other>
      weak_ptr(const shared_ptr<Other>&);
   weak_ptr& operator=(const weak_ptr&);
   template <class Other>
      weak_ptr& operator=(const weak_ptr<Other>&);
   template <class Other>
      weak_ptr& operator=(shared_ptr<Other>&);
   void swap(weak_ptr&);
   void reset();
   long use_count() const;
   bool expired() const;
   shared_ptr<Ty> lock() const;
   };
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ kontrolowany przez wskaźnik słabe.

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje obiekt, który wskazuje na zasób, który jest zarządzany przez co najmniej jeden [shared_ptr — klasa](../standard-library/shared-ptr-class.md) obiektów. `weak_ptr` Obiektów, które wskazują na zasób nie ma wpływu na liczbę odwołań do zasobu. Dlatego, gdy ostatni `shared_ptr` niszczony jest obiekt, który zarządza tego zasobu zasób zostanie zwolniony, nawet jeśli występują `weak_ptr` obiektów wskazujące do tego zasobu. Jest to istotne w celu uniknięcia cyklów w strukturach danych.

A `weak_ptr` obiektu wskazuje na zasób, jeśli został zbudowany z `shared_ptr` obiekt, który jest właścicielem tego zasobu, jeśli został zbudowany z `weak_ptr` obiektu, który wskazuje ten zasób, czy tego zasobu została przydzielona do niego za pomocą [ operator =](#op_eq). Element `weak_ptr` obiektu nie zapewnia bezpośredni dostęp do zasobu, który wskazuje. Kod, który musi używać zasobów jest więc za pośrednictwem `shared_ptr` obiekt, który jest właścicielem tego zasobu, tworzone przez wywołanie funkcji elementu członkowskiego [blokady](#lock). A `weak_ptr` obiektu wygasł po zwolnieniu zasób, który wskazuje on, ponieważ wszystkie `shared_ptr` zniszczeniu obiektów, które są właścicielami zasobu. Wywoływanie `lock` na `weak_ptr` obiektu, który wygasł tworzy obiekt shared_ptr puste.

Weak_ptr — pusty obiekt nie wskazuje wszystkie zasoby i ma nie bloku sterowania. Jej funkcji członkowskiej `lock` zwraca obiekt shared_ptr puste.

Cykl występuje, gdy dwa lub więcej zasobów w wartości clientauthtrustmode `shared_ptr` obiekty przechowywania wzajemnie odwołujące się do `shared_ptr` obiektów. Na przykład cykliczne połączonej listy za pomocą trzech elementów ma węzła głównego `N0`; ten węzeł zawiera `shared_ptr` obiektu, który jest właścicielem kolejnego węzła `N1`; ten węzeł zawiera `shared_ptr` obiektu, który jest właścicielem kolejnego węzła `N2`; tego węzła w Włącz przechowuje `shared_ptr` obiektu, który jest właścicielem węzła głównego, `N0`, cyklu zamykania. W takiej sytuacji żadne liczbę odwołań nigdy nie stanie się zero, a węzły w cyklu nie zostanie zwolniona. Aby wyeliminować cyklu ostatniego węzła `N2` mają być przechowywane w `weak_ptr` wskazujące `N0` zamiast `shared_ptr` obiektu. Ponieważ `weak_ptr` obiektu nie jest właścicielem `N0` nie wpływa na `N0`firmy odwoływać się do liczby, a kiedy niszczony jest ostatnie odwołanie tego programu z węzłem głównym węzłów na liście również zostaną usunięte.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[weak_ptr](#weak_ptr)|Konstruuje `weak_ptr`.|

### <a name="methods"></a>Metody

|||
|-|-|
|[element_type](#element_type)|Typ elementu.|
|[expired](#expired)|Sprawdza, czy własność utracił ważność.|
|[lock](#lock)|Uzyskuje wyłącznego prawa własności do zasobów.|
|[owner_before](#owner_before)|Zwraca **true** Jeśli `weak_ptr` był zamówiony przed (lub mniej niż) podany wskaźnik.|
|[Resetuj](#reset)|Wersje posiadane zasoby.|
|[swap](#swap)|Zamień dwa `weak_ptr` obiektów.|
|[use_count](#use_count)|Wyznaczony numer liczby `shared_ptr` obiektów.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Zamienia posiadane zasoby.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<pamięci >

**Namespace:** standardowe

## <a name="element_type"></a>  ELEMENT_TYPE

Typ elementu.

```cpp
typedef Ty element_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Ty`.

### <a name="example"></a>Przykład

```cpp
// std__memory__weak_ptr_element_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(5));
    std::weak_ptr<int> wp0(sp0);
    std::weak_ptr<int>::element_type val = *wp0.lock();

    std::cout << "*wp0.lock() == " << val << std::endl;

    return (0);
    }
```

```Output
*wp0.lock() == 5
```

## <a name="expired"></a>  Wygasła

Sprawdza, czy własność utracił ważność.

```cpp
bool expired() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca **true** Jeśli `*this` wygasł, w przeciwnym razie **false**.

### <a name="example"></a>Przykład

```cpp
// std__memory__weak_ptr_expired.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int(10));
        wp = sp;
        std::cout << "wp.expired() == " << std::boolalpha
            << wp.expired() << std::endl;
        std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    }

    // check expired after sp is destroyed
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;
    std::cout << "(bool)wp.lock() == " << std::boolalpha
        << (bool)wp.lock() << std::endl;

    return (0);
}
```

```Output
wp.expired() == false
*wp.lock() == 10
wp.expired() == true
(bool)wp.lock() == false
```

## <a name="lock"></a>  Blokady

Uzyskuje wyłącznego prawa własności do zasobów.

```cpp
shared_ptr<Ty> lock() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca obiekt shared_ptr puste, jeśli `*this` upłynął; w przeciwnym razie zwraca [shared_ptr — klasa](../standard-library/shared-ptr-class.md)\<Ty > obiekt, który jest właścicielem zasobu `*this` wskazuje.

### <a name="example"></a>Przykład

```cpp
// std__memory__weak_ptr_lock.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int(10));
        wp = sp;
        std::cout << "wp.expired() == " << std::boolalpha
            << wp.expired() << std::endl;
        std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    }

    // check expired after sp is destroyed
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;
    std::cout << "(bool)wp.lock() == " << std::boolalpha
        << (bool)wp.lock() << std::endl;

    return (0);
}
```

```Output
wp.expired() == false
*wp.lock() == 10
wp.expired() == true
(bool)wp.lock() == false
```

## <a name="op_eq"></a>  operator =

Zamienia posiadane zasoby.

```cpp
weak_ptr& operator=(const weak_ptr& wp);

template <class Other>
weak_ptr& operator=(const weak_ptr<Other>& wp);

template <class Other>
weak_ptr& operator=(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

*Inne*<br/>
Typ kontrolowany przez wskaźnik argumentu udostępnione słabych.

*WP*<br/>
Słaby wskaźnik do skopiowania.

*SP*<br/>
Wspólny wskaźnik do skopiowania.

### <a name="remarks"></a>Uwagi

Wszystkie operatory zwolnienia zasobów wskazywana aktualnie przez `*this` i Przypisz własność zasobu o nazwie określonej przez sekwencję operandów na `*this`. Jeśli operator nie pozostawia `*this` bez zmian.

### <a name="example"></a>Przykład

```cpp
// std__memory__weak_ptr_operator_as.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::weak_ptr<int> wp0(sp0);
    std::cout << "*wp0.lock() == " << *wp0.lock() << std::endl;

    std::shared_ptr<int> sp1(new int(10));
    wp0 = sp1;
    std::cout << "*wp0.lock() == " << *wp0.lock() << std::endl;

    std::weak_ptr<int> wp1;
    wp1 = wp0;
    std::cout << "*wp1.lock() == " << *wp1.lock() << std::endl;

    return (0);
}
```

```Output
*wp0.lock() == 5
*wp0.lock() == 10
*wp1.lock() == 10
```

## <a name="owner_before"></a>  owner_before —

Zwraca **true** Jeśli `weak_ptr` był zamówiony przed (lub mniej niż) podany wskaźnik.

```cpp
template <class Other>
bool owner_before(const shared_ptr<Other>& ptr);

template <class Other>
bool owner_before(const weak_ptr<Other>& ptr);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
`lvalue` Odwołanie do albo `shared_ptr` lub `weak_ptr`.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego szablonu zwraca **true** Jeśli `*this` jest `ordered before` `ptr`.

## <a name="reset"></a>  Resetuj

Wersje posiadane zasoby.

```cpp
void reset();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwalnia zasób wskazywany przez `*this` i konwertuje `*this` do obiektu weak_ptr puste.

### <a name="example"></a>Przykład

```cpp
// std__memory__weak_ptr_reset.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp(new int(5));
    std::weak_ptr<int> wp(sp);
    std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;

    wp.reset();
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;

    return (0);
}
```

```Output
*wp.lock() == 5
wp.expired() == false
wp.expired() == true
```

## <a name="swap"></a>  swap

Zamień dwa `weak_ptr` obiektów.

```cpp
void swap(weak_ptr& wp);
```

### <a name="parameters"></a>Parametry

*WP*<br/>
Słaby wskaźnik do wymiany.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego pozostawia zasobów pierwotnie wskazywany przez `*this` później wskazywany przez *wp*i zasobów pierwotnie wskazywany przez *wp* później wskazywany przez `*this`. Funkcja nie zmienia zliczanie odwołań, zasobów i nie generuje żadnych wyjątków.

### <a name="example"></a>Przykład

```cpp
// std__memory__weak_ptr_swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::shared_ptr<int> sp2(new int(10));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    sp1.swap(sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;

    swap(sp1, sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << std::endl;

    std::weak_ptr<int> wp1(sp1);
    std::weak_ptr<int> wp2(sp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    wp1.swap(wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    swap(wp1, wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    return (0);
}
```

```Output
*sp1 == 5
*sp1 == 10
*sp1 == 5

*wp1 == 5
*wp1 == 10
*wp1 == 5
```

## <a name="use_count"></a>  use_count —

Wyznaczony numer liczby `shared_ptr` obiektów.

```cpp
long use_count() const;
```

### <a name="remarks"></a>Uwagi

Element członkowski funkcji zwraca liczbę `shared_ptr` obiekty, które są właścicielami zasobu wskazywanego przez `*this`.

### <a name="example"></a>Przykład

```cpp
// std__memory__weak_ptr_use_count.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::weak_ptr<int> wp(sp1);
    std::cout << "wp.use_count() == "
        << wp.use_count() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "wp.use_count() == "
        << wp.use_count() << std::endl;

    return (0);
}
```

```Output
wp.use_count() == 1
wp.use_count() == 2
```

## <a name="weak_ptr"></a>  weak_ptr —

Konstruuje `weak_ptr`.

```cpp
weak_ptr();

weak_ptr(const weak_ptr& wp);

template <class Other>
weak_ptr(const weak_ptr<Other>& wp);

template <class Other>
weak_ptr(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

*Inne*<br/>
Typ kontrolowany przez wskaźnik argumentu udostępnione słabych.

*WP*<br/>
Słaby wskaźnik do skopiowania.

*SP*<br/>
Wspólny wskaźnik do skopiowania.

### <a name="remarks"></a>Uwagi

Konstruktory każdego skonstruować obiekt, który wskazuje na zasób o nazwie określonej przez sekwencję operandów.

### <a name="example"></a>Przykład

```cpp
// std__memory__weak_ptr_construct.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp0;
    std::cout << "wp0.expired() == " << std::boolalpha
        << wp0.expired() << std::endl;

    std::shared_ptr<int> sp1(new int(5));
    std::weak_ptr<int> wp1(sp1);
    std::cout << "*wp1.lock() == "
        << *wp1.lock() << std::endl;

    std::weak_ptr<int> wp2(wp1);
    std::cout << "*wp2.lock() == "
        << *wp2.lock() << std::endl;

    return (0);
}
```

```Output
wp0.expired() == true
*wp1.lock() == 5
*wp2.lock() == 5
```

## <a name="see-also"></a>Zobacz także

[shared_ptr, klasa](../standard-library/shared-ptr-class.md)<br/>
