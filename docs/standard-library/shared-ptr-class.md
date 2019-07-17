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
ms.openlocfilehash: ca427bd364a5ab66112f23e0a920598ad8ba190b
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246375"
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

|||
|-|-|
|[shared_ptr](#shared_ptr)|Konstruuje `shared_ptr`.|
|[~ shared_ptr](#dtorshared_ptr)|Niszczy `shared_ptr`.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[element_type](#element_type)|Typ elementu.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[allocate_shared](#allocate_shared)||
|[const_pointer_cast](#const_pointer_cast)||
|[dynamic_pointer_cast](#dynamic_pointer_cast)||
|[get](#get)|Pobiera adres stanowiących własność zasobów.|
|[get_deleter](#get_deleter)||
|[make_shared](#make_shared)||
|[owner_before](#owner_before)|Zwraca wartość PRAWDA, jeśli `shared_ptr` był zamówiony przed (lub mniej niż) podany wskaźnik.|
|[reinterpret_pointer_cast](#reinterpret_pointer_cast)||
|[Resetuj](#reset)|Zamień posiadane zasoby.|
|[static_pointer_cast](#static_pointer_cast)||
|[swap](#swap)|Zamień dwa `shared_ptr` obiektów.|
|[unique](#unique)|Sprawdza, czy posiadane zasoby są unikatowe.|
|[use_count](#use_count)|Zlicza liczby właścicieli zasobu.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[bool — operator](#op_bool)|Sprawdza, czy istnieją własne zasoby.|
|[operator *](#op_star)|Pobiera wartość wyznaczoną.|
|[operator=](#op_eq)|Zamienia posiadane zasoby.|
|[operator-&gt;](#op_arrow)|Pobiera wskaźnik do wyznaczonej wartości.|
|[Operator&lt;&lt;](#op_arrowarrow)||

### <a name="allocate_shared"></a> allocate_shared

```cpp
template<class T, class A, class... Args>
    shared_ptr<T> allocate_shared(const A& a, Args&&... args);
```

### <a name="const_pointer_cast"></a> const_pointer_cast —

```cpp
template<class T, class U>
    shared_ptr<T> const_pointer_cast(const shared_ptr<U>& r) noexcept;
```

### <a name="dynamic_pointer_cast"></a> dynamic_pointer_cast —

```cpp
template<class T, class U>
    shared_ptr<T> dynamic_pointer_cast(const shared_ptr<U>& r) noexcept;
```

### <a name="element_type"></a> ELEMENT_TYPE

Typ elementu.

```cpp
typedef T element_type;
```

#### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `T`.

#### <a name="example"></a>Przykład

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

### <a name="get"></a> Pobierz

Pobiera adres stanowiących własność zasobów.

```cpp
T *get() const;
```

#### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca adres stanowiących własność zasobów. Jeśli obiekt nie jest właścicielem zasobu zwraca 0.

#### <a name="example"></a>Przykład

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

### <a name="get_deleter"></a> get_deleter —

```cpp
template<class D, class T>
    D* get_deleter(const shared_ptr<T>& p) noexcept;
```

### <a name="make_shared"></a> make_shared

```cpp
template<class T, class... Args>
    shared_ptr<T> make_shared(Args&&... args);
```

### <a name="op_bool"></a> bool — operator

Sprawdza, czy istnieją własne zasoby.

```cpp
explicit operator bool() const noexcept;
```

#### <a name="remarks"></a>Uwagi

Operator zwraca wartość **true** podczas `get() != nullptr`, w przeciwnym razie **false**.

#### <a name="example"></a>Przykład

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

### <a name="op_star"></a> operator *

Pobiera wartość wyznaczoną.

```cpp
T& operator*() const;
```

#### <a name="remarks"></a>Uwagi

Zwraca operatora pośredniego `*get()`. Dzięki temu przechowywany wskaźnik nie może być zerowy.

#### <a name="example"></a>Przykład

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

### <a name="op_eq"></a> operator =

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

#### <a name="parameters"></a>Parametry

*SP*\
Wspólny wskaźnik do skopiowania.

*wschodni Region Azji i*\
Wskaźnik auto do skopiowania.

#### <a name="remarks"></a>Uwagi

Wszystkie operatory dekrementacji licznikiem odwołań do zasobów należących do aktualnie `*this` i Przypisz własność zasobu o nazwie określonej przez sekwencję operandów na `*this`. Jeśli licznik odwołań mieści się na zero, zasób jest zwalniany. Jeśli operator nie pozostawia `*this` bez zmian.

#### <a name="example"></a>Przykład

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

### <a name="op_arrow"></a> operator-&gt;

Pobiera wskaźnik do wyznaczonej wartości.

```cpp
T * operator->() const;
```

#### <a name="remarks"></a>Uwagi

Zwraca operatora wyboru `get()`, tak aby wyrażenie `sp->member` działa tak samo jak `(sp.get())->member` gdzie `sp` jest obiektem klasy `shared_ptr<T>`. Dzięki temu przechowywany wskaźnik nie może być null, i `T` musi być klasy, struktury lub Unii typu z członka `member`.

#### <a name="example"></a>Przykład

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

### <a name="op_arrowarrow"></a> Operator&lt;&lt;

```cpp
template<class E, class T, class Y>
    basic_ostream<E, T>& operator<< (basic_ostream<E, T>& os, const shared_ptr<Y>& p);
```

### <a name="owner_before"></a> owner_before —

Zwraca wartość PRAWDA, jeśli `shared_ptr` był zamówiony przed (lub mniej niż) podany wskaźnik.

```cpp
template <class Other>
    bool owner_before(const shared_ptr<Other>& ptr);

template <class Other>
    bool owner_before(const weak_ptr<Other>& ptr);
```

#### <a name="parameters"></a>Parametry

*PTR*\
`lvalue` Odwołanie do albo `shared_ptr` lub `weak_ptr`.

#### <a name="remarks"></a>Uwagi

Szablon funkcji elementu członkowskiego zwraca wartość PRAWDA, jeśli `*this` jest `ordered before` `ptr`.

### <a name="reinterpret_pointer_cast"></a> reinterpret_pointer_cast

```cpp
template<class T, class U>
    shared_ptr<T> reinterpret_pointer_cast(const shared_ptr<U>& r) noexcept;
```

### <a name="reset"></a> Resetuj

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

#### <a name="parameters"></a>Parametry

*Inne*\
Typ kontrolowany przez wskaźnik argumentu.

*D*\
Typ deletera.

*PTR*\
Wskaźnik do skopiowania.

*dtor*\
Deleter do skopiowania.

*ELEMENT*\
Typ alokatora.

*Alokacji*\
Alokator do skopiowania.

#### <a name="remarks"></a>Uwagi

Wszystkie operatory dekrementacji licznikiem odwołań do zasobów należących do aktualnie `*this` i Przypisz własność zasobu o nazwie określonej przez sekwencję operandów na `*this`. Jeśli licznik odwołań mieści się na zero, zasób jest zwalniany. Jeśli operator nie pozostawia `*this` bez zmian.

#### <a name="example"></a>Przykład

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

### <a name="shared_ptr"></a> shared_ptr

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

#### <a name="parameters"></a>Parametry

*Inne*\
Typ kontrolowany przez wskaźnik argumentu.

*PTR*\
Wskaźnik do skopiowania.

*D*\
Typ deletera.

*ELEMENT*\
Typ alokatora.

*dtor*\
Deleter.

*aż operator*\
Alokator.

*SP*\
Inteligentny wskaźnik do skopiowania.

*WP*\
Słaby wskaźnik.

*wschodni Region Azji i*\
Wskaźnik auto do skopiowania.

#### <a name="remarks"></a>Uwagi

Konstruktory każdego skonstruować obiekt, który jest właścicielem zasobu o nazwie określonej przez sekwencję operandów. Konstruktor `shared_ptr(const weak_ptr<Other>& wp)` zgłasza wyjątek obiektu typu [bad_weak_ptr, klasa](../standard-library/bad-weak-ptr-class.md) Jeśli `wp.expired()`.

#### <a name="example"></a>Przykład

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

### <a name="dtorshared_ptr"></a> ~ shared_ptr

Niszczy `shared_ptr`.

```cpp
~shared_ptr();
```

#### <a name="remarks"></a>Uwagi

Dekrementuje destruktor licznik odwołań dla zasobu będącymi własnością `*this`. Jeśli licznik odwołań mieści się na zero, zasób jest zwalniany.

#### <a name="example"></a>Przykład

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

### <a name="static_pointer_cast"></a> static_pointer_cast —

```cpp
template<class T, class U>
shared_ptr<T> static_pointer_cast(const shared_ptr<U>& r) noexcept;
```

### <a name="swap"></a> swap

Zamień dwa `shared_ptr` obiektów.

```cpp
void swap(shared_ptr& sp);
```

#### <a name="parameters"></a>Parametry

*SP*\
Wspólny wskaźnik do wymiany.

#### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego pozostawia zasobów należących do pierwotnie `*this` później własnością *sp*i zasobów należących do pierwotnie *sp* później własnością `*this`. Funkcja nie zmienia zliczanie odwołań, zasobów i nie generuje żadnych wyjątków.

#### <a name="example"></a>Przykład

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

### <a name="unique"></a> unikatowe

Sprawdza, czy posiadane zasoby są unikatowe.

```cpp
bool unique() const;
```

#### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca **true** Jeśli żadne inne `shared_ptr` obiekt posiada zasób, który jest własnością `*this`, w przeciwnym razie **false**.

#### <a name="example"></a>Przykład

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

### <a name="use_count"></a> use_count —

Zlicza liczby właścicieli zasobu.

```cpp
long use_count() const;
```

#### <a name="remarks"></a>Uwagi

Element członkowski funkcji zwraca liczbę `shared_ptr` obiekty, które są właścicielami zasobu, który jest własnością `*this`.

#### <a name="example"></a>Przykład

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
