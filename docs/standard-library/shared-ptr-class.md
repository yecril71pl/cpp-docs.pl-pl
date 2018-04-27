---
title: shared_ptr — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 28
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a6d00fe34a03c33faa92f481e7eece69e586eeea
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="sharedptr-class"></a>shared_ptr — Klasa

Otacza inteligentny wskaźnik zliczonych odwołań wokół obiektu przydzielanego dynamicznie.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
class shared_ptr;
```

## <a name="remarks"></a>Uwagi

Shared_ptr — klasa opisuje obiekt, który używa zliczanie do zarządzania zasobami. A `shared_ptr` obiekt skutecznie zawiera wskaźnik do zasobu jest właścicielem lub posiada pustego wskaźnika. Zasób może należeć do więcej niż jeden `shared_ptr` obiekt; podczas ostatniego `shared_ptr` obiektu, który jest właścicielem określonego zasobu, zasób zostanie zwolniona.

A `shared_ptr` zatrzymuje będący właścicielem zasobu, jeśli jest ponownie przypisywane lub zresetować.

Argument szablonu `T` może być niekompletnego typu z wyjątkiem przypadków wymienionych dla niektórych funkcji Członkowskich.

Gdy `shared_ptr<T>` obiekt jest tworzony z wskaźnik zasobu typu `G*` lub `shared_ptr<G>`, typ wskaźnika `G*` musi być możliwe do przekonwertowania na `T*`. Jeśli nie, ten kod nie zostanie skompilowany. Na przykład:

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

A `shared_ptr` obiektu jest właścicielem zasobu:

- Jeśli został skonstruowany za pomocą wskaźnika do tego zasobu

- Jeśli została zbudowana z `shared_ptr` obiektu, który jest właścicielem tego zasobu

- Jeśli została zbudowana z [weak_ptr — klasa](../standard-library/weak-ptr-class.md) obiekt, który wskazuje tego zasobu lub

- Jeśli prawo własności do tego zasobu została przypisana do niego, za pomocą [shared_ptr::operator =](#op_eq) , przez wywołanie funkcji członkowskiej [shared_ptr::reset](#reset).

`shared_ptr` Blok kontroli udostępniania obiektów, których właścicielem zasobu. Przechowuje bloku sterowania:

- Liczba `shared_ptr` obiektów zasobu

- Liczba `weak_ptr` obiektów, które wskazują zasobów,

- deleter dla tego zasobu, jeśli istnieje,

- niestandardowe przydzielania bloku kontroli, jeśli istnieje.

A `shared_ptr` obiekt, który został zainicjowany przy użyciu pustego wskaźnika ma blok kontroli i nie jest pusty. Po `shared_ptr` obiektu zwalnia zasobu, nie jest właścicielem tego zasobu. Po `weak_ptr` obiektu zwalnia zasobu, wskazuje już do tego zasobu.

Gdy liczba `shared_ptr` obiekty czy własnych zasobów wynosi zero, zasób zostanie zwolniona, usuwając je lub przez przekazanie jej adres do deleter, w zależności od tego, jak prawo własności do zasobu został pierwotnie utworzony. Gdy liczba `shared_ptr` obiektów, których właścicielem zasobu jest zero, a liczba `weak_ptr` obiektów, które wskaż, czy zasób jest zero, blok sterowania zostanie zwolniona, przy użyciu niestandardowego zarządcę dla bloków sterowania, jeśli ma ona.

Pusta `shared_ptr` obiekt nie ma żadnych zasobów i ma nie bloku sterowania.

Deleter jest obiektem funkcji z funkcją członkowską `operator()`. Umożliwia konstrukcji kopii musi być typu, a jego kopiowania Konstruktor i destruktor nie może zostać zwrócone wyjątków. Przyjmuje jeden parametr, obiektu, który ma zostać usunięty.

Niektóre funkcje pobierać listy argumentów, która definiuje właściwości powstałe w ten sposób `shared_ptr<T>` lub `weak_ptr<T>` obiektu. Lista argumentów można określić na kilka sposobów:

bez argumentów — wynikowy obiekt jest pusta `shared_ptr` obiektu lub pusta `weak_ptr` obiektu.

`ptr` --wskaźnika typu `Other*` do zasobu, które mają być zarządzane. `T` musi być typem ukończone. Jeśli funkcja nie powiedzie się (ponieważ nie można przydzielić bloku sterowania) daje wynik wyrażenia `delete ptr`.

`ptr, dtor` --wskaźnika typu `Other*` zasobów, które mają być zarządzane i deleter dla tego zasobu. Jeśli funkcja nie powiedzie się (ponieważ nie można przydzielić bloku sterowania), wywołuje metodę `dtor(ptr)`, które muszą być jasno określone.

`ptr, dtor, alloc` --wskaźnika typu `Other*` zasobów, które mają być zarządzane, deleter dla tego zasobu i przydzielania do zarządzania dowolny magazyn, który musi być przydzielona i zwolniony. Jeśli funkcja nie powiedzie się (ponieważ nie można przydzielić bloku sterowania) wywołuje `dtor(ptr)`, które muszą być jasno określone.

`sp` -- `shared_ptr<Other>` obiektu, który jest właścicielem zasobu, które mają być zarządzane.

`wp` -- `weak_ptr<Other>` obiekt, który wskazuje zasobów, które mają być zarządzane.

`ap` -- `auto_ptr<Other>` obiekt przechowujący wskaźnik do zasobów, które mają być zarządzane. Jeśli funkcja pomyślnie wywołania `ap.release()`; w przeciwnym razie pozostawia `ap` bez zmian.

We wszystkich przypadkach, typ wskaźnika `Other*` musi być możliwe do przekonwertowania na `T*`.

## <a name="thread-safety"></a>Bezpieczeństwo wątków

Wiele wątków można odczytu i zapisu różnych `shared_ptr` obiektów w tym samym czasie, nawet jeśli obiekty są kopie, które mają prawo własności.

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
|[get](#get)|Pobiera adres należących do zasobu.|
|[owner_before](#owner_before)|Zwraca wartość PRAWDA, jeśli `shared_ptr` jest umieszczane przed (lub mniej niż) podany wskaźnik.|
|[Resetowanie](#reset)|Zastąp należących do zasobu.|
|[swap](#swap)|Zamienia dwa `shared_ptr` obiektów.|
|[unique](#unique)|Testy, jeśli należących do zasobu jest unikatowe.|
|[use_count](#use_count)|Zlicza liczby właścicieli zasobów.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[wartość logiczna shared_ptr::operator](#op_bool)|Testy, jeśli istnieje zasób należące do firmy.|
|[shared_ptr::operator*](#op_star)|Pobiera wartość wyznaczonych.|
|[shared_ptr::operator=](#op_eq)|Zastępuje należących do zasobu.|
|[shared_ptr::operator-&gt;](#op_arrow)|Pobiera wskaźnik do wyznaczonej wartości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<pamięci >

**Namespace:** Standard

## <a name="element_type"></a>  shared_ptr::ELEMENT_TYPE

Typ elementu.

```cpp
typedef T element_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu `T`.

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

Pobiera adres należących do zasobu.

```cpp
T *get() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca adres należących do zasobu. Jeśli obiekt nie jest właścicielem zasobu zwraca wartość 0.

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

## <a name="op_bool"></a>  wartość logiczna shared_ptr::operator

Testy, jeśli istnieje zasób należące do firmy.

```cpp
explicit operator bool() const noexcept;
```

### <a name="remarks"></a>Uwagi

Zwraca wartość `true` podczas `get() != nullptr`, w przeciwnym razie `false`.

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

Pobiera wartość wyznaczonych.

```cpp
T& operator*() const;
```

### <a name="remarks"></a>Uwagi

Operator pośredni zwraca `*get()`. W związku z tym przechowywanych wskaźnika nie może mieć wartości null.

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

Zastępuje należących do zasobu.

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

`sp` Udostępniony wskaźnik do skopiowania.

`ap` Wskaźnik automatycznie do skopiowania.

### <a name="remarks"></a>Uwagi

Wszystkie operatory dekrementacji liczba odwołań dla zasobu będącymi własnością `*this` i Przypisz własność zasobów o nazwie sekwencja operand `*this`. Gdy liczba odwołań spadnie do zera, zasób jest zwalniany. Jeśli operator nie pozostawia `*this` bez zmian.

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

Zwraca operatorem wyboru `get()`, dzięki czemu wyrażenie `sp->member` działa tak samo jak `(sp.get())->member` gdzie `sp` jest obiektem klasy `shared_ptr<T>`. W związku z tym przechowywanych wskaźnika nie może być pusta, i `T` musi być klasą, strukturą lub typu union z elementem członkowskim `member`.

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

Zwraca wartość PRAWDA, jeśli `shared_ptr` jest umieszczane przed (lub mniej niż) podany wskaźnik.

```cpp
template <class Other>
bool owner_before(const shared_ptr<Other>& ptr);

template <class Other>
bool owner_before(const weak_ptr<Other>& ptr);
```

### <a name="parameters"></a>Parametry

`ptr` `lvalue` Odwołania do albo `shared_ptr` lub `weak_ptr`.

### <a name="remarks"></a>Uwagi

Funkcja członkowska szablonu zwraca wartość PRAWDA, jeśli `*this` jest `ordered before` `ptr`.

## <a name="reset"></a>  shared_ptr::reset

Zastąp należących do zasobu.

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

`Other` Typ kontrolowane przez wskaźnik argumentu.

`D` Typ deleter.

`ptr` Wskaźnik do skopiowania.

`dtor` Deleter do skopiowania.

`A` Typ programu przydzielania.

`alloc` Program przydzielania do skopiowania.

### <a name="remarks"></a>Uwagi

Wszystkie operatory dekrementacji liczba odwołań dla zasobu będącymi własnością `*this` i Przypisz własność zasobów o nazwie sekwencja operand `*this`. Gdy liczba odwołań spadnie do zera, zasób jest zwalniany. Jeśli operator nie pozostawia `*this` bez zmian.

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

`Other` Typ kontrolowane przez wskaźnik argumentu.

`ptr` Wskaźnik do skopiowania.

`D` Typ deleter.

`A` Typ programu przydzielania.

`dtor` Deleter.

`ator` Program przydzielania.

`sp` Wskaźnik inteligentny do skopiowania.

`wp` Słabe wskaźnika.

`ap` Wskaźnik automatycznie do skopiowania.

### <a name="remarks"></a>Uwagi

Konstruktory każdego utworzenia obiektu, który jest właścicielem zasobu o nazwie przez sekwencję argument. Konstruktor `shared_ptr(const weak_ptr<Other>& wp)` zgłasza wyjątek typu obiektu [bad_weak_ptr — klasa](../standard-library/bad-weak-ptr-class.md) Jeśli `wp.expired()`.

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

## <a name="dtorshared_ptr"></a>  shared_ptr —:: ~ shared_ptr

Niszczy `shared_ptr`.

```cpp
~shared_ptr();
```

### <a name="remarks"></a>Uwagi

Zmniejsza destruktora liczba odwołań dla zasobu będącymi własnością `*this`. Gdy liczba odwołań spadnie do zera, zasób jest zwalniany.

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

Zamienia dwa `shared_ptr` obiektów.

```cpp
void swap(shared_ptr& sp);
```

### <a name="parameters"></a>Parametry

`sp` Udostępniony wskaźnik do wymiany.

### <a name="remarks"></a>Uwagi

Funkcja członkowska pozostawia zasobów należących do pierwotnie `*this` następnie właścicielem `sp`i zasobów należących do pierwotnie `sp` następnie właścicielem `*this`. Funkcja nie ulega zmianie liczby odwołań zasobów i generują żadnych wyjątków.

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

Testy, jeśli należących do zasobu jest unikatowe.

```cpp
bool unique() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca `true` Jeśli żaden inny `shared_ptr` obiektu jest właścicielem zasobu, którego właścicielem jest `*this`, w przeciwnym razie `false`.

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

Zlicza liczby właścicieli zasobów.

```cpp
long use_count() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca liczbę `shared_ptr` obiektów, których właścicielem zasobu, którego właścicielem jest `*this`.

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
