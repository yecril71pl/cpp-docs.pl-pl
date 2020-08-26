---
title: shared_ptr, klasa
ms.date: 07/29/2019
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
ms.openlocfilehash: e41c76e7bd3e77b34ad38d3998ee1d38cdc2fee4
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846215"
---
# <a name="shared_ptr-class"></a>shared_ptr, klasa

Otacza inteligentny wskaźnik zliczonych odwołań wokół obiektu przydzielanego dynamicznie.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
class shared_ptr;
```

## <a name="remarks"></a>Uwagi

`shared_ptr`Klasa opisuje obiekt, który używa zliczania odwołań do zarządzania zasobami. `shared_ptr`Obiekt efektywnie utrzymuje wskaźnik do zasobu, do którego należy, lub posiada wskaźnik o wartości null. Zasób może należeć do więcej niż jednego `shared_ptr` obiektu; gdy ostatni `shared_ptr` obiekt będący właścicielem określonego zasobu jest niszczony, zasób zostanie zwolniony.

`shared_ptr`Zamyka zasób, gdy jest on ponownie przypisywany lub resetowany.

Argument szablonu `T` może być niekompletnym typem, z wyjątkiem sytuacji, gdy jest zanotowany dla niektórych funkcji Członkowskich.

Gdy `shared_ptr<T>` obiekt jest konstruowany ze wskaźnika zasobów typu `G*` lub z `shared_ptr<G>` , typ wskaźnika `G*` musi być konwertowany na `T*` . Jeśli nie jest on konwertowany, kod nie zostanie skompilowany. Na przykład:

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

`shared_ptr`Obiekt jest właścicielem zasobu:

- Jeśli został skonstruowany ze wskaźnikiem do tego zasobu,

- Jeśli został skonstruowany z `shared_ptr` obiektu, który jest właścicielem tego zasobu,

- Jeśli został skonstruowany z obiektu [weak_ptr](weak-ptr-class.md) , który wskazuje na ten zasób, lub

- Jeśli własność tego zasobu została przypisana do niego przy użyciu [shared_ptr:: operator =](#op_eq) lub przez wywołanie funkcji składowej [shared_ptr:: Reset](#reset).

`shared_ptr`Obiekty, które są własnością zasobu, współużytkują blok sterowania. Blok sterowania zawiera:

- liczba `shared_ptr` obiektów, które są właścicielami zasobu,

- liczba `weak_ptr` obiektów, które wskazują na zasób,

- program do usuwania dla tego zasobu, jeśli go ma,

- niestandardowy Alokator dla bloku sterowania, jeśli taki ma.

`shared_ptr`Obiekt, który jest inicjowany za pomocą wskaźnika o wartości null, ma blok sterowania i nie jest pusty. Gdy `shared_ptr` obiekt zwalnia zasób, nie jest już właścicielem tego zasobu. Gdy `weak_ptr` obiekt zwalnia zasób, nie wskazuje już na ten zasób.

Gdy liczba `shared_ptr` obiektów, które są własnością zasobu, będzie równa zero, zasób jest zwalniany przez usunięcie lub przez przekazanie jego adresu do elementu usuwającego, w zależności od tego, jak własność zasobu została pierwotnie utworzona. Gdy liczba `shared_ptr` obiektów, które są własnością zasobu wynosi zero, a liczba `weak_ptr` obiektów, które wskazują na ten zasób wynosi zero, blok sterowania jest zwalniany przy użyciu niestandardowego alokatora dla bloku sterowania, jeśli go zawiera.

Pusty `shared_ptr` obiekt nie ma żadnych zasobów i nie ma bloku sterowania.

Element DELETE jest obiektem funkcji, który ma funkcję członkowską `operator()` . Jego typem musi być Copy konstrukcyjną, a jego Konstruktor kopiujący i destruktor nie mogą generować wyjątków. Akceptuje jeden parametr, obiekt, który ma zostać usunięty.

Niektóre funkcje przyjmują listę argumentów, która definiuje właściwości wyników `shared_ptr<T>` lub `weak_ptr<T>` obiektu. Można określić taką listę argumentów na kilka sposobów:

brak argumentów — obiekt otrzymany jest pustym `shared_ptr` obiektem lub pustym `weak_ptr` obiektem.

`ptr` --wskaźnika typu `Other*` do zasobu, który ma być zarządzany. `T` musi być kompletnym typem. Jeśli funkcja nie powiedzie się (ponieważ nie można przydzielić bloku sterowania), oblicza wyrażenie `delete ptr` .

`ptr, deleter` --wskaźnika typu `Other*` do zasobu, który ma być zarządzany, oraz do usuwania dla tego zasobu. Jeśli funkcja nie powiedzie się (ponieważ nie można przydzielić bloku sterowania), wywołuje `deleter(ptr)` , które musi być dobrze zdefiniowane.

`ptr, deleter, alloc` --wskaźnik typu `Other*` do zasobu, który ma być zarządzany, obiekt do usuwania dla tego zasobu oraz Alokator do zarządzania dowolnym magazynem, który musi zostać przydzielony i zwolniony. Jeśli funkcja nie powiedzie się (ponieważ nie można przydzielić bloku sterowania), wywołuje `deleter(ptr)` , które musi być dobrze zdefiniowane.

`sp` -- `shared_ptr<Other>` obiekt, który jest właścicielem zasobu, który ma być zarządzany.

`wp` --Obiekt wskazujący zasób, który `weak_ptr<Other>` ma być zarządzany.

`ap` -- `auto_ptr<Other>` obiekt, który przechowuje wskaźnik do zasobu, który ma być zarządzany. Jeśli funkcja się powiedzie, wywołuje `ap.release()` ; w przeciwnym razie pozostawia nie `ap` zmieniony.

We wszystkich przypadkach typ wskaźnika `Other*` musi być konwertowany na `T*` .

## <a name="thread-safety"></a>Bezpieczeństwo wątkowe

Wiele wątków może odczytywać i zapisywać różne `shared_ptr` obiekty w tym samym czasie, nawet gdy obiekty są kopiowane, które mają własność.

## <a name="members"></a>Elementy członkowskie

|Nazwa|Opis|
|-|-|
| **Konstruktory** | |
|[shared_ptr](#shared_ptr)|Konstruuje a `shared_ptr` .|
|[~ shared_ptr](#dtorshared_ptr)|Niszczy `shared_ptr` .|
| **Definicje typów** | |
|[element_type](#element_type)|Typ elementu.|
|[weak_type](#weak_type)|Typ słabego wskaźnika do elementu.|
| **Funkcje członkowskie** | |
|[get](#get)|Pobiera adres należącego zasobu.|
|[owner_before](#owner_before)|Zwraca wartość PRAWDA `shared_ptr` , jeśli jest ona uporządkowana przed (lub mniej niż) dostarczonym wskaźnikiem.|
|[zresetować](#reset)|Zamień własność zasobu.|
|[wymiany](#swap)|Zamienia dwa `shared_ptr` obiekty.|
|[unique](#unique)|Testuje, czy posiadany zasób jest unikatowy.|
|[use_count](#use_count)|Zlicza liczby właścicieli zasobów.|
| **Operatory** | |
|[wartość logiczna operatora](#op_bool)|Testuje, czy właścicielem istnieje zasób.|
|[zakład](#op_star)|Pobiera wydaną wartość.|
|[operator =](#op_eq)|Zamienia posiadane zasoby.|
|[zakład&gt;](#op_arrow)|Pobiera wskaźnik do wyoznaczonej wartości.|

## <a name="element_type"></a><a name="element_type"></a> element_type

Typ elementu.

```cpp
typedef T element_type;                  // before C++17
using element_type = remove_extent_t<T>; // C++17
```

### <a name="remarks"></a>Uwagi

`element_type`Typ jest synonimem dla parametru szablonu `T` .

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

## <a name="get"></a><a name="get"></a> Pobierz

Pobiera adres należącego zasobu.

```cpp
element_type* get() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca adres należącego zasobu. Jeśli obiekt nie jest własnością zasobu, zwraca 0.

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

## <a name="operator-bool"></a><a name="op_bool"></a> wartość logiczna operatora

Testuje, czy właścicielem istnieje zasób.

```cpp
explicit operator bool() const noexcept;
```

### <a name="remarks"></a>Uwagi

Operator zwraca wartość **`true`** when `get() != nullptr` , w przeciwnym razie **`false`** .

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

## <a name="operator"></a><a name="op_star"></a> zakład

Pobiera wydaną wartość.

```cpp
T& operator*() const noexcept;
```

### <a name="remarks"></a>Uwagi

Operator pośredni zwraca wartość `*get()` . W związku z tym, składowany wskaźnik nie może mieć wartości null.

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

## <a name="operator"></a><a name="op_eq"></a> operator =

Zamienia posiadane zasoby.

```cpp
shared_ptr& operator=(const shared_ptr& sp) noexcept;

shared_ptr& operator=(shared_ptr&& sp) noexcept;

template <class Other>
shared_ptr& operator=(const shared_ptr<Other>& sp) noexcept;

template <class Other>
shared_ptr& operator=(shared_ptr<Other>&& sp) noexcept;

template <class Other>
shared_ptr& operator=(auto_ptr<Other>&& ap);    // deprecated in C++11, removed in C++17

template <class Other, class Deleter>
shared_ptr& operator=(unique_ptr<Other, Deleter>&& up);
```

### <a name="parameters"></a>Parametry

*requirement*\
Udostępniony wskaźnik do kopiowania lub przenoszenia.

*rachunk*\
Wskaźnik Autotekstu do przeniesienia. `auto_ptr`Przeciążenie jest przestarzałe w c++ 11 i usunięte w języku c++ 17.

*Konfigurowanie*\
Unikatowy wskaźnik do obiektu, do którego ma zostać przyjęty własność. nie *jest to* obiekt po wywołaniu.

*Różnych*\
Typ obiektu wskazywanego przez *SP*, *AP*lub w *górę*.

*Deleter*\
Typ operacji usuwania obiektu będącego właścicielem, który jest przechowywany do późniejszego usunięcia obiektu.

### <a name="remarks"></a>Uwagi

Operatory zmniejszają liczbę odwołań dla zasobu będącego własnością **`*this`** i przypisują własność zasobu o nazwie przez sekwencję operandu do **`*this`** . Jeśli liczba odwołań jest równa zero, zasób zostanie wydaną. Jeśli operator zakończy się niepowodzeniem, pozostaje **`*this`** niezmieniony.

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
    std::unique_ptr<int> up(new int(10));

    sp0 = sp1;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    sp0 = up;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    return (0);
}
```

```Output
*sp0 == 5
*sp0 == 10
```

## <a name="operator-"></a><a name="op_arrow"></a> operator — >

Pobiera wskaźnik do wyoznaczonej wartości.

```cpp
T* operator->() const noexcept;
```

### <a name="remarks"></a>Uwagi

Operator wyboru zwraca `get()` , tak że wyrażenie `sp->member` zachowuje się tak samo, jak `(sp.get())->member` gdzie `sp` jest obiektem klasy `shared_ptr<T>` . W związku z tym, składowany wskaźnik nie może mieć wartości null i `T` musi być klasą, strukturą lub typem Unii z elementem członkowskim `member` .

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

## <a name="owner_before"></a><a name="owner_before"></a> owner_before

Zwraca wartość PRAWDA `shared_ptr` , jeśli jest ona uporządkowana przed (lub mniej niż) dostarczonym wskaźnikiem.

```cpp
template <class Other>
bool owner_before(const shared_ptr<Other>& ptr) const noexcept;

template <class Other>
bool owner_before(const weak_ptr<Other>& ptr) const noexcept;
```

### <a name="parameters"></a>Parametry

*PTR*\
Odwołanie lvalue do `shared_ptr` lub `weak_ptr` .

### <a name="remarks"></a>Uwagi

Funkcja członkowska szablonu zwraca wartość true, jeśli **`*this`** jest uporządkowana przed `ptr` .

## <a name="reset"></a><a name="reset"></a> zresetować

Zamień własność zasobu.

```cpp
void reset() noexcept;

template <class Other>
void reset(Other *ptr);

template <class Other, class Deleter>
void reset(
    Other *ptr,
    Deleter deleter);

template <class Other, class Deleter, class Allocator>
void reset(
    Other *ptr,
    Deleter deleter,
    Allocator alloc);
```

### <a name="parameters"></a>Parametry

*Różnych*\
Typ kontrolowany przez wskaźnik argumentu.

*Deleter*\
Typ obiektu do usuwania.

*PTR*\
Wskaźnik do skopiowania.

*Deleter*\
Usuwanie, które ma zostać skopiowane.

*Alokator*\
Typ alokatora.

*alokacj*\
Program przydzielający do kopiowania.

### <a name="remarks"></a>Uwagi

Operatory zmniejszają liczbę odwołań dla zasobu będącego własnością **`*this`** i przypisują własność zasobu o nazwie przez sekwencję operandu do **`*this`** . Jeśli liczba odwołań jest równa zero, zasób zostanie wydaną. Jeśli operator zakończy się niepowodzeniem, pozostaje **`*this`** niezmieniony.

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

## <a name="shared_ptr"></a><a name="shared_ptr"></a> shared_ptr

Konstruuje a `shared_ptr` .

```cpp
constexpr shared_ptr() noexcept;

constexpr shared_ptr(nullptr_t) noexcept : shared_ptr() {}

shared_ptr(const shared_ptr& sp) noexcept;

shared_ptr(shared_ptr&& sp) noexcept;

template <class Other>
explicit shared_ptr(Other* ptr);

template <class Other, class Deleter>
shared_ptr(
    Other* ptr,
    Deleter deleter);

template <class Deleter>
shared_ptr(
    nullptr_t ptr,
    Deleter deleter);

template <class Other, class Deleter, class Allocator>
shared_ptr(
    Other* ptr,
    Deleter deleter,
    Allocator alloc);

template <class Deleter, class Allocator>
shared_ptr(
    nullptr_t ptr,
    Deleter deleter,
    Allocator alloc);

template <class Other>
shared_ptr(
    const shared_ptr<Other>& sp) noexcept;

template <class Other>
explicit shared_ptr(
    const weak_ptr<Other>& wp);

template <class &>
shared_ptr(
    std::auto_ptr<Other>& ap);

template <class &>
shared_ptr(
    std::auto_ptr<Other>&& ap);

template <class Other, class Deleter>
shared_ptr(
    unique_ptr<Other, Deleter>&& up);

template <class Other>
shared_ptr(
    const shared_ptr<Other>& sp,
    element_type* ptr) noexcept;

template <class Other>
shared_ptr(
    shared_ptr<Other>&& sp,
    element_type* ptr) noexcept;

template <class Other, class Deleter>
shared_ptr(
    const unique_ptr<Other, Deleter>& up) = delete;
```

### <a name="parameters"></a>Parametry

*Różnych*\
Typ kontrolowany przez wskaźnik argumentu.

*PTR*\
Wskaźnik do skopiowania.

*Deleter*\
Typ obiektu do usuwania.

*Alokator*\
Typ alokatora.

*Deleter*\
Usuwanie.

*alokacj*\
Program przydzielający.

*requirement*\
Inteligentny wskaźnik do skopiowania.

*dokumenty*\
Słaby wskaźnik.

*rachunk*\
Wskaźnik Autotekstu do skopiowania.

### <a name="remarks"></a>Uwagi

Konstruktory każdy konstruują obiekt będący właścicielem zasobu o nazwie przez sekwencję operandu. Konstruktor `shared_ptr(const weak_ptr<Other>& wp)` zgłasza obiekt wyjątku typu [bad_weak_ptr](bad-weak-ptr-class.md) , jeśli `wp.expired()` .

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

## <a name="shared_ptr"></a><a name="dtorshared_ptr"></a> ~ shared_ptr

Niszczy `shared_ptr` .

```cpp
~shared_ptr();
```

### <a name="remarks"></a>Uwagi

Destruktor zmniejsza liczbę odwołań dla zasobu, którego właścicielem jest aktualnie **`*this`** . Jeśli liczba odwołań jest równa zero, zasób zostanie wydaną.

### <a name="example"></a>Przykład

```cpp
// std__memory__shared_ptr_destroy.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

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

## <a name="swap"></a><a name="swap"></a> wymiany

Zamienia dwa `shared_ptr` obiekty.

```cpp
void swap(shared_ptr& sp) noexcept;
```

### <a name="parameters"></a>Parametry

*requirement*\
Wspólny wskaźnik do zamiany za pomocą.

### <a name="remarks"></a>Uwagi

Funkcja członkowska pozostawia zasób początkowo należący do firmy **`*this`** *SP*, a zasób oryginalny należał do firmy *SP* **`*this`** . Funkcja nie zmienia liczby odwołań dla dwóch zasobów i nie generuje żadnych wyjątków.

### <a name="example"></a>Przykład

```cpp
// std__memory__shared_ptr_swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

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

## <a name="unique"></a><a name="unique"></a> unikatowy

Testuje, czy posiadany zasób jest unikatowy. Ta funkcja była przestarzała w języku C++ 17 i została usunięta w języku C++ 20.

```cpp
bool unique() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca **`true`** , jeśli żaden inny `shared_ptr` obiekt nie jest właścicielem zasobu, którego właścicielem jest **`*this`** , w przeciwnym razie **`false`** .

### <a name="example"></a>Przykład

```cpp
// std__memory__shared_ptr_unique.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

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

## <a name="use_count"></a><a name="use_count"></a> use_count

Zlicza liczby właścicieli zasobów.

```cpp
long use_count() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca liczbę `shared_ptr` obiektów, których właścicielem jest zasób **`*this`** .

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

## <a name="weak_type"></a><a name="weak_type"></a> weak_type

Typ słabego wskaźnika do elementu.

```cpp
using weak_type = weak_ptr<T>; // C++17
```

### <a name="remarks"></a>Uwagi

`weak_type`Definicja została dodana w języku c++ 17.

## <a name="see-also"></a>Zobacz też

[Dokumentacja plików nagłówkowych](cpp-standard-library-header-files.md)\
[\<memory>](memory.md)\
[unique_ptr](unique-ptr-class.md)\
[weak_ptr — Klasa](weak-ptr-class.md)
