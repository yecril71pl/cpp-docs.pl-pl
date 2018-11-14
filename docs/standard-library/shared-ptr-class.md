---
title: shared_ptr — Klasa
ms.date: 11/04/2016
f1_keywords:
- memory/std::shared_ptr
- memory/std::shared_ptr::element_type
- memory/std::shared_ptr::get
- memory/std::shared_ptr::owner_before
- memory/std::shared_ptr::reset
- memory/std::shared_ptr::swap
- memory/std::shared_ptr::unique
- memory/std::shared_ptr::use_count
- memory/std::shared_ptr::operator boolean-type
- memory/std::shared_ptr::operator*
- memory/std::shared_ptr::operator=
- memory/std::shared_ptr::operator->
helpviewer_keywords:
- std::shared_ptr [C++]
- std::shared_ptr [C++], element_type
- std::shared_ptr [C++], get
- std::shared_ptr [C++], owner_before
- std::shared_ptr [C++], reset
- std::shared_ptr [C++], swap
- std::shared_ptr [C++], unique
- std::shared_ptr [C++], use_count
- std::shared_ptr [C++], element_type
- std::shared_ptr [C++], get
- std::shared_ptr [C++], owner_before
- std::shared_ptr [C++], reset
- std::shared_ptr [C++], swap
- std::shared_ptr [C++], unique
- std::shared_ptr [C++], use_count
ms.assetid: 1469fc51-c658-43f1-886c-f4530dd84860
ms.openlocfilehash: 791a18461b3a0ee8237dec47c87f9d441221141d
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519363"
---
# <a name="sharedptr-class"></a>shared_ptr — Klasa

Otacza inteligentny wskaźnik zliczonych odwołań wokół obiektu przydzielanego dynamicznie.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
class shared_ptr;
```

## <a name="remarks"></a>Uwagi

Shared_ptr — klasa opisująca obiekt, który używa zliczania odniesień, by można było zarządzać zasobami. A `shared_ptr` obiekt skutecznie mieści wskaźnik do zasobu, który posiada lub mieści wskaźnik o wartości null. Zasób może być własnością więcej niż jedną `shared_ptr` obiektu podczas ostatniego `shared_ptr` niszczony jest obiekt, który posiada określony zasób, zasób zostanie zwolniony.

A `shared_ptr` zatrzymuje posiadanie zasobu gdy jest ponownie przypisywany ani resetowany.

Argument szablonu `T` może być niekompletnym typem wyjątku jak wspomniano dla niektórych funkcji elementów członkowskich.

Gdy `shared_ptr<T>` obiekt jest wykonany z zasobu wskaźnika typu `G*` lub `shared_ptr<G>`, typ wskaźnika `G*` musi być konwertowany na `T*`. Jeśli nie jest, kod nie zostanie skompilowany. Na przykład:

```cpp
#include <memory>
using namespace std;

class F {};
class G : public F {};

shared_ptr<G> sp0(new G);   // okay, template parameter G and argument G*
shared_ptr<G> sp1(sp0);     // okay, template parameter G and argument shared_ptr<G>
shared_ptr<F> sp2(new G);   // okay, G* convertible to F*
shared_ptr<F> sp3(sp0);     // okay, template parameter F and argument shared_ptr<G>
shared_ptr<F> sp4(sp2);     // okay, template parameter F and argument shared_ptr<F>
shared_ptr<int> sp5(new G); // error, G* not convertible to int*
shared_ptr<int> sp6(sp2);   // error, template parameter int and argument shared_ptr<F>
```

A `shared_ptr` obiekt posiada zasób:

- Jeśli został wykonany ze wskaźnikiem do tego zasobu

- Jeśli został zbudowany z `shared_ptr` obiekt, który jest właścicielem tego zasobu

- Jeśli został zbudowany z [weak_ptr, klasa](../standard-library/weak-ptr-class.md) obiekt, który wskazuje ten zasób lub

- Jeśli własność tego zasobu została przydzielona do niego, albo za pomocą [shared_ptr::operator =](#op_eq) lub przez wywołanie funkcji elementu członkowskiego [shared_ptr::reset](#reset).

`shared_ptr` Obiekty, które są właścicielami zasobu dzielą się blokiem kontroli. Blok sterowania posiada:

- Liczba `shared_ptr` obiekty, które są właścicielami zasobu,

- Liczba `weak_ptr` obiektów, które wskazują na zasoby

- deleter dla tego zasobu, jeśli taki istnieje,

- niestandardowy alokator bloku kontroli jeśli taki istnieje.

A `shared_ptr` obiekt, który jest inicjowany z użyciem wskaźnikiem typu null posiada blok sterowania i nie jest pusty. Po `shared_ptr` uwolnieniu zasobu przez obiekt, nie jest już właścicielem tego zasobu. Po `weak_ptr` uwolnieniu zasobu przez obiekt, nie wskazuje już tego zasobu.

Gdy liczba `shared_ptr` obiekty czy własny zasób staje się zerem, zasób zostanie zwolniony poprzez usunięcie lub przekazanie jego adresu do modułu usuwającego, w zależności od tego, jak został pierwotnie utworzony własność zasobu. Gdy liczba `shared_ptr` obiekty, które są właścicielami zasobu wynosi zero, a liczba `weak_ptr` obiektów, które wskazują, zasób wynosi zero, blok kontroli zostanie zwolniony, za pomocą niestandardowego zarządcy dla bloku sterowania, jeśli taki istnieje.

Pusta `shared_ptr` obiekt nie ma żadnych zasobów i ma nie bloku sterowania.

Deleter jest obiektem funkcji, która posiada funkcję członkowską `operator()`. Jego typ musi być kopią konstrukcyjną, a Konstruktor kopiujący i destruktor nie może zgłaszać wyjątki. Przyjmuje jeden parametr, obiekt do usunięcia.

Niektóre funkcje podejmują listy argumentów, która definiuje właściwości wynikające `shared_ptr<T>` lub `weak_ptr<T>` obiektu. Można określić taką listę argumentów na kilka sposobów:

bez argumentów--wynikowy obiekt jest pustym `shared_ptr` obiektu lub pusta `weak_ptr` obiektu.

`ptr` --wskaźnika typu `Other*` do zasobu, które mają być zarządzane. `T` musi być typem kompletnym. Jeśli funkcja zawiedzie (ponieważ nie można przydzielić bloku sterowania) ocenia wyrażenie `delete ptr`.

`ptr, dtor` --wskaźnika typu `Other*` zasobów, które mają być zarządzane i deleter dla tego zasobu. Jeśli funkcja zawiedzie (ponieważ nie można przydzielić bloku sterowania), wywołuje metodę `dtor(ptr)`, musi być dobrze zdefiniowane.

`ptr, dtor, alloc` --wskaźnika typu `Other*` do zasobów administrowanych, deleter dla tego zasobu i przydzielania do zarządzania magazynu musi być przydzielny i wolny. Jeśli funkcja zawiedzie (ponieważ nie można przydzielić bloku sterowania) wywoływanych przez nią `dtor(ptr)`, musi być dobrze zdefiniowane.

`sp` -- `shared_ptr<Other>` obiektu, który jest właścicielem zasobu, które mają być zarządzane.

`wp` -- `weak_ptr<Other>` obiekt, który wskazuje na zasób, które mają być zarządzane.

`ap` -- `auto_ptr<Other>` obiekt przechowujący wskaźnik do zasobu, które mają być zarządzane. Jeśli funkcja się powiedzie, wywołuje `ap.release()`; w przeciwnym razie pozostawia `ap` bez zmian.

We wszystkich przypadkach, typ wskaźnika `Other*` musi być konwertowany na `T*`.

## <a name="thread-safety"></a>Bezpieczeństwo wątków

Wiele wątków może odczytywać i zapisywać różne `shared_ptr` obiektów w tym samym czasie, nawet jeśli obiekty są kopiami, które dzielą prawo własności.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[shared_ptr](#shared_ptr)|Konstruuje `shared_ptr`.|
|[shared_ptr::~shared_ptr](#dtorshared_ptr)|Niszczy `shared_ptr`.|

### <a name="types"></a>Types

|Nazwa typu|Opis|
|-|-|
|[element_type](#element_type)|Typ elementu.|

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[get](#get)|Pobiera adres stanowiących własność zasobów.|
|[owner_before](#owner_before)|Zwraca wartość PRAWDA, jeśli `shared_ptr` był zamówiony przed (lub mniej niż) podany wskaźnik.|
|[Resetuj](#reset)|Zamień posiadane zasoby.|
|[swap](#swap)|Zamień dwa `shared_ptr` obiektów.|
|[unique](#unique)|Sprawdza, czy posiadane zasoby są unikatowe.|
|[use_count](#use_count)|Zlicza liczby właścicieli zasobu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[shared_ptr::operator bool](#op_bool)|Sprawdza, czy istnieją własne zasoby.|
|[shared_ptr::operator*](#op_star)|Pobiera wartość wyznaczoną.|
|[shared_ptr::operator=](#op_eq)|Zamienia posiadane zasoby.|
|[shared_ptr::operator-&gt;](#op_arrow)|Pobiera wskaźnik do wyznaczonej wartości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<pamięci >

**Namespace:** standardowe

## <a name="element_type"></a>  shared_ptr::ELEMENT_TYPE

Typ elementu.

```cpp
typedef T element_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `T`.

### <a name="example"></a>Przykład

```cpp
// std__memory__shared_ptr_element_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::shared_ptr<int>::element_type val = *sp0;

    std::cout << "*sp0 == " << val << std::endl;

    return (0);
}
```

```Output
*sp0 == 5
```

## <a name="get"></a>  shared_ptr::Get

Pobiera adres stanowiących własność zasobów.

```cpp
T *get() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca adres stanowiących własność zasobów. Jeśli obiekt nie jest właścicielem zasobu zwraca 0.

### <a name="example"></a>Przykład

```cpp
// std__memory__shared_ptr_get.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));

    std::cout << "sp0.get() == 0 == " << std::boolalpha
        << (sp0.get() == 0) << std::endl;
    std::cout << "*sp1.get() == " << *sp1.get() << std::endl;

    return (0);
}
```

```Output
sp0.get() == 0 == true
*sp1.get() == 5
```

## <a name="op_bool"></a>  shared_ptr::operator bool

Sprawdza, czy istnieją własne zasoby.

```cpp
explicit operator bool() const noexcept;
```

### <a name="remarks"></a>Uwagi

Operator zwraca wartość **true** podczas `get() != nullptr`, w przeciwnym razie **false**.

### <a name="example"></a>Przykład

```cpp
// std__memory__shared_ptr_operator_bool.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));

    std::cout << "(bool)sp0 == " << std::boolalpha
        << (bool)sp0 << std::endl;
    std::cout << "(bool)sp1 == " << std::boolalpha
        << (bool)sp1 << std::endl;

    return (0);
}
```

```Output
(bool)sp0 == false
(bool)sp1 == true
```

## <a name="op_star"></a>  shared_ptr::operator *

Pobiera wartość wyznaczoną.

```cpp
T& operator*() const;
```

### <a name="remarks"></a>Uwagi

Zwraca operatora pośredniego `*get()`. Dzięki temu przechowywany wskaźnik nie może być zerowy.

### <a name="example"></a>Przykład

```cpp
// std__memory__shared_ptr_operator_st.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));

    std::cout << "*sp0 == " << *sp0 << std::endl;

    return (0);
}
```

```Output
*sp0 == 5
```

## <a name="op_eq"></a>  shared_ptr::operator =

Zamienia posiadane zasoby.

```cpp
shared_ptr& operator=(const shared_ptr& sp);

template <class Other>
shared_ptr& operator=(const shared_ptr<Other>& sp);

template <class Other>
shared_ptr& operator=(auto_ptr<Other>& ap);

template <class Other>
shared_ptr& operator=(auto_ptr<Other>& ap);

template <class Other>
shared_ptr& operator=(auto_ptr<Other>&& ap);

template <class Other, class Deletor>
shared_ptr& operator=(unique_ptr<Other, Deletor>&& ap);
```

### <a name="parameters"></a>Parametry

*SP*<br/>
Wspólny wskaźnik do skopiowania.

*wschodni Region Azji i*<br/>
Wskaźnik auto do skopiowania.

### <a name="remarks"></a>Uwagi

Wszystkie operatory dekrementacji licznikiem odwołań do zasobów należących do aktualnie `*this` i Przypisz własność zasobu o nazwie określonej przez sekwencję operandów na `*this`. Jeśli licznik odwołań mieści się na zero, zasób jest zwalniany. Jeśli operator nie pozostawia `*this` bez zmian.

### <a name="example"></a>Przykład

```cpp
// std__memory__shared_ptr_operator_as.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));
    std::auto_ptr<int> ap(new int(10));

    sp0 = sp1;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    sp0 = ap;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    return (0);
}
```

```Output
*sp0 == 5
*sp0 == 10
```

## <a name="op_arrow"></a>  shared_ptr::operator-&gt;

Pobiera wskaźnik do wyznaczonej wartości.

```cpp
T * operator->() const;
```

### <a name="remarks"></a>Uwagi

Zwraca operatora wyboru `get()`, tak aby wyrażenie `sp->member` działa tak samo jak `(sp.get())->member` gdzie `sp` jest obiektem klasy `shared_ptr<T>`. Dzięki temu przechowywany wskaźnik nie może być null, i `T` musi być klasy, struktury lub Unii typu z członka `member`.

### <a name="example"></a>Przykład

```cpp
// std__memory__shared_ptr_operator_ar.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

typedef std::pair<int, int> Mypair;
int main()
{
    std::shared_ptr<Mypair> sp0(new Mypair(1, 2));

    std::cout << "sp0->first == " << sp0->first << std::endl;
    std::cout << "sp0->second == " << sp0->second << std::endl;

    return (0);
}
```

```Output
sp0->first == 1
sp0->second == 2
```

## <a name="owner_before"></a>  shared_ptr::owner_before

Zwraca wartość PRAWDA, jeśli `shared_ptr` był zamówiony przed (lub mniej niż) podany wskaźnik.

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

Szablon funkcji elementu członkowskiego zwraca wartość PRAWDA, jeśli `*this` jest `ordered before` `ptr`.

## <a name="reset"></a>  shared_ptr::reset

Zamień posiadane zasoby.

```cpp
void reset();

template <class Other>
void reset(Other *ptr;);

template <class Other, class D>
void reset(Other *ptr, D dtor);

template <class Other, class D, class A>
void reset(Other *ptr, D dtor, A alloc);
```

### <a name="parameters"></a>Parametry

*Inne*<br/>
Typ kontrolowany przez wskaźnik argumentu.

*D*<br/>
Typ deletera.

*ptr*<br/>
Wskaźnik do skopiowania.

*dtor*<br/>
Deleter do skopiowania.

*A*<br/>
Typ alokatora.

*Alokacji*<br/>
Alokator do skopiowania.

### <a name="remarks"></a>Uwagi

Wszystkie operatory dekrementacji licznikiem odwołań do zasobów należących do aktualnie `*this` i Przypisz własność zasobu o nazwie określonej przez sekwencję operandów na `*this`. Jeśli licznik odwołań mieści się na zero, zasób jest zwalniany. Jeśli operator nie pozostawia `*this` bez zmian.

### <a name="example"></a>Przykład

```cpp
// std__memory__shared_ptr_reset.cpp
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
    std::shared_ptr<int> sp(new int(5));

    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    sp.reset();
    std::cout << "(bool)sp == " << std::boolalpha
        << (bool)sp << std::endl;

    sp.reset(new int(10));
    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    sp.reset(new int(15), deleter());
    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    return (0);
}
```

```Output
*sp == 5
(bool)sp == false
*sp == 10
*sp == 15
```

## <a name="shared_ptr"></a>  shared_ptr::shared_ptr

Konstruuje `shared_ptr`.

```cpp
shared_ptr();

shared_ptr(nullptr_t);

shared_ptr(const shared_ptr& sp);

shared_ptr(shared_ptr&& sp);

template <class Other>
explicit shared_ptr(Other* ptr);

template <class Other, class D>
shared_ptr(Other* ptr, D dtor);

template <class D>
shared_ptr(nullptr_t ptr, D dtor);

template <class Other, class D, class A>
shared_ptr(Other* ptr, D dtor, A  alloc);

template <class D, class A>
shared_ptr(nullptr_t ptr, D dtor, A alloc);

template <class Other>
shared_ptr(const shared_ptr<Other>& sp);

template <class Other>
shared_ptr(const weak_ptr<Other>& wp);

template <class &>
shared_ptr(std::auto_ptr<Other>& ap);

template <class &>
shared_ptr(std::auto_ptr<Other>&& ap);

template <class Other, class D>
shared_ptr(unique_ptr<Other, D>&& up);

template <class Other>
shared_ptr(const shared_ptr<Other>& sp, T* ptr);

template <class Other, class D>
shared_ptr(const unique_ptr<Other, D>& up) = delete;
```

### <a name="parameters"></a>Parametry

*Inne*<br/>
Typ kontrolowany przez wskaźnik argumentu.

*ptr*<br/>
Wskaźnik do skopiowania.

*D*<br/>
Typ deletera.

*A*<br/>
Typ alokatora.

*dtor*<br/>
Deleter.

*aż operator*<br/>
Alokator.

*SP*<br/>
Inteligentny wskaźnik do skopiowania.

*WP*<br/>
Słaby wskaźnik.

*wschodni Region Azji i*<br/>
Wskaźnik auto do skopiowania.

### <a name="remarks"></a>Uwagi

Konstruktory każdego skonstruować obiekt, który jest właścicielem zasobu o nazwie określonej przez sekwencję operandów. Konstruktor `shared_ptr(const weak_ptr<Other>& wp)` zgłasza wyjątek obiektu typu [bad_weak_ptr, klasa](../standard-library/bad-weak-ptr-class.md) Jeśli `wp.expired()`.

### <a name="example"></a>Przykład

```cpp
// std__memory__shared_ptr_construct.cpp
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
    std::shared_ptr<int> sp0;
    std::cout << "(bool)sp0 == " << std::boolalpha
        << (bool)sp0 << std::endl;

    std::shared_ptr<int> sp1(new int(5));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    std::shared_ptr<int> sp2(new int(10), deleter());
    std::cout << "*sp2 == " << *sp2 << std::endl;

    std::shared_ptr<int> sp3(sp2);
    std::cout << "*sp3 == " << *sp3 << std::endl;

    std::weak_ptr<int> wp(sp3);
    std::shared_ptr<int> sp4(wp);
    std::cout << "*sp4 == " << *sp4 << std::endl;

    std::auto_ptr<int> ap(new int(15));
    std::shared_ptr<int> sp5(ap);
    std::cout << "*sp5 == " << *sp5 << std::endl;

    return (0);
}
```

```Output
(bool)sp0 == false
*sp1 == 5
*sp2 == 10
*sp3 == 10
*sp4 == 10
*sp5 == 15
```

## <a name="dtorshared_ptr"></a>  shared_ptr:: ~ shared_ptr

Niszczy `shared_ptr`.

```cpp
~shared_ptr();
```

### <a name="remarks"></a>Uwagi

Dekrementuje destruktor licznik odwołań dla zasobu będącymi własnością `*this`. Jeśli licznik odwołań mieści się na zero, zasób jest zwalniany.

### <a name="example"></a>Przykład

```cpp
// std__memory__shared_ptr_destroy.cpp
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
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << "use count == " << sp1.use_count() << std::endl;

    {
        std::shared_ptr<int> sp2(sp1);
        std::cout << "*sp2 == " << *sp2 << std::endl;
        std::cout << "use count == " << sp1.use_count() << std::endl;
    }

    // check use count after sp2 is destroyed
    std::cout << "use count == " << sp1.use_count() << std::endl;

    return (0);
}
```

```Output
*sp1 == 5
use count == 1
*sp2 == 5
use count == 2
use count == 1
```

## <a name="swap"></a>  shared_ptr::swap

Zamień dwa `shared_ptr` obiektów.

```cpp
void swap(shared_ptr& sp);
```

### <a name="parameters"></a>Parametry

*SP*<br/>
Wspólny wskaźnik do wymiany.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego pozostawia zasobów należących do pierwotnie `*this` później własnością *sp*i zasobów należących do pierwotnie *sp* później własnością `*this`. Funkcja nie zmienia zliczanie odwołań, zasobów i nie generuje żadnych wyjątków.

### <a name="example"></a>Przykład

```cpp
// std__memory__shared_ptr_swap.cpp
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

## <a name="unique"></a>  shared_ptr::UNIQUE

Sprawdza, czy posiadane zasoby są unikatowe.

```cpp
bool unique() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca **true** Jeśli żadne inne `shared_ptr` obiekt posiada zasób, który jest własnością `*this`, w przeciwnym razie **false**.

### <a name="example"></a>Przykład

```cpp
// std__memory__shared_ptr_unique.cpp
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
    std::cout << "sp1.unique() == " << std::boolalpha
        << sp1.unique() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "sp1.unique() == " << std::boolalpha
        << sp1.unique() << std::endl;

    return (0);
}
```

```Output
sp1.unique() == true
sp1.unique() == false
```

## <a name="use_count"></a>  shared_ptr::use_count

Zlicza liczby właścicieli zasobu.

```cpp
long use_count() const;
```

### <a name="remarks"></a>Uwagi

Element członkowski funkcji zwraca liczbę `shared_ptr` obiekty, które są właścicielami zasobu, który jest własnością `*this`.

### <a name="example"></a>Przykład

```cpp
// std__memory__shared_ptr_use_count.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "sp1.use_count() == "
        << sp1.use_count() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "sp1.use_count() == "
        << sp1.use_count() << std::endl;

    return (0);
}
```

```Output
sp1.use_count() == 1
sp1.use_count() == 2
```

## <a name="see-also"></a>Zobacz także

[weak_ptr, klasa](../standard-library/weak-ptr-class.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
