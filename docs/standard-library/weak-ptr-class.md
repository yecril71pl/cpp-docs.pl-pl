---
title: weak_ptr — Klasa
ms.date: 07/29/2019
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
ms.openlocfilehash: d4ba30f737bc570a4ee700b3a317b5feebe8a50a
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682410"
---
# <a name="weakptr-class"></a>weak_ptr — Klasa

Otacza słabo połączony wskaźnik.

## <a name="syntax"></a>Składnia

```cpp
template<class T> class weak_ptr;
```

### <a name="parameters"></a>Parametry

*&* \
Typ kontrolowany przez słaby wskaźnik.

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje obiekt, który wskazuje na zasób, który jest zarządzany przez jeden lub więcej obiektów [shared_ptr](shared-ptr-class.md) . `weak_ptr` Obiekty wskazujące na zasób nie wpływają na liczbę odwołań zasobu. Gdy ostatni `shared_ptr` obiekt zarządzający tym zasobem zostanie zniszczony, zasób zostanie zwolniony, nawet jeśli `weak_ptr` istnieją obiekty wskazujące na ten zasób. Takie zachowanie jest niezbędne w przypadku unikania cykli w strukturach danych.

Obiekt wskazuje na zasób, jeśli został skonstruowany `shared_ptr` z obiektu, który jest właścicielem tego zasobu, jeśli został skonstruowany z `weak_ptr` obiektu, który wskazuje na ten zasób, lub jeśli ten zasób został przypisany do niego przy użyciu [operatora =](#op_eq). `weak_ptr` `weak_ptr` Obiekt nie zapewnia bezpośredniego dostępu do zasobu, do którego wskazuje. Kod, który musi korzystać z zasobu, odbywa się za `shared_ptr` pomocą obiektu, który jest właścicielem tego zasobu, przez wywołanie [blokady](#lock)funkcji składowej. Obiekt wygasł, gdy zasób, który wskazuje w, został zwolniony, ponieważ wszystkie `shared_ptr` obiekty należące do zasobu zostały zniszczone. `weak_ptr` Wywołanie `lock`obiektu,który wygasł,powodujeutworzeniepustegoobiektushared_ptr.`weak_ptr`

Pusty obiekt weak_ptr nie wskazuje żadnych zasobów i nie ma bloku sterowania. Funkcja `lock` członkowska zwraca pusty obiekt shared_ptr.

Cykl występuje, gdy co najmniej dwa zasoby kontrolowane przez `shared_ptr` obiekty wzajemnie odwołują `shared_ptr` się do obiektów. Na przykład cykliczna lista połączona z trzema `N0`elementami ma węzeł główny; ten węzeł `shared_ptr` zawiera obiekt, który jest właścicielem następnego węzła, `N1`a ten węzeł zawiera `shared_ptr` obiekt, który jest właścicielem następnego węzła `N2`; ten węzeł, w z kolei utrzymuje `shared_ptr` obiekt będący właścicielem `N0`węzła głównego, zamykający cykl. W tej sytuacji liczby odwołań nigdy nie staną się zerami, a węzły w cyklu nigdy nie są zwalniane. Aby wyeliminować cykl, ostatni `N2` węzeł powinien `weak_ptr` przechowywać obiekt `shared_ptr` wskazujący `N0` zamiast obiektu. Ponieważ obiekt nie jest jego `N0` własnością, nie `N0`ma to wpływu na liczbę odwołań i gdy ostatnie odwołanie programu do węzła głównego jest niszczone, węzły na liście również zostaną zniszczone. `weak_ptr`

## <a name="members"></a>Elementy członkowskie

|||
|-|-|
| **Konstruktory** | |
|[weak_ptr](#weak_ptr)|Konstruuje `weak_ptr`a.|
| **Destruktory** | |
|[~ weak_ptr](#tilde-weak_ptr)|Konstruuje `weak_ptr`a.|
| **Definicje typów** | |
|[element_type](#element_type)|Typ elementu.|
| **Funkcje członkowskie** | |
|[przeterminowanych](#expired)|Testuje, czy własność wygasła.|
|[lock](#lock)|Uzyskuje wyłączną własność zasobu.|
|[owner_before](#owner_before)|Zwraca **wartość PRAWDA** , `weak_ptr` jeśli jest ona uporządkowana przed (lub mniej niż) dostarczonym wskaźnikiem.|
|[zresetować](#reset)|Przynależność do zasobów.|
|[swap](#swap)|Zamienia dwa `weak_ptr` obiekty.|
|[use_count](#use_count)|Liczy liczbę `shared_ptr` obiektów.|
| **Operatory** | |
|[operator=](#op_eq)|Zamienia posiadane zasoby.|

## <a name="element_type"></a>element_type

Typ elementu.

```cpp
typedef T element_type; // through C++17
using element_type = remove_extent_t<T>; // C++20
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru `T`szablonu.

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

## <a name="expired"></a>przeterminowanych

Testuje, czy własność wygasła, to oznacza, że obiekt, do którego istnieje odwołanie, został usunięty.

```cpp
bool expired() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca **wartość true** , jeśli `*this` wygasła, w przeciwnym razie **false**.

### <a name="example"></a>Przykład

```cpp
// std__memory__weak_ptr_expired.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

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

## <a name="lock"></a>skręt

Uzyskuje udział `shared_ptr` , który współużytkuje własność zasobu.

```cpp
shared_ptr<T> lock() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca pusty obiekt [shared_ptr](shared-ptr-class.md) , jeśli `*this` wygasł; `shared_ptr<T>` w przeciwnym razie zwraca obiekt, który jest właścicielem zasobu, `*this` który wskazuje. Zwraca wartość odpowiadającą niepodzielnym wykonywaniu `expired() ? shared_ptr<T>() : shared_ptr<T>(*this)`.

### <a name="example"></a>Przykład

```cpp
// std__memory__weak_ptr_lock.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

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

## <a name="op_eq"></a>operator =

Zamienia posiadane zasoby.

```cpp
weak_ptr& operator=(const weak_ptr& ptr) noexcept;

template <class Other>
weak_ptr& operator=(const weak_ptr<Other>& ptr) noexcept;

template <class Other>
weak_ptr& operator=(const shared_ptr<Other>& ptr) noexcept;
```

### <a name="parameters"></a>Parametry

*Różnych*\
Typ kontrolowany przez wspólny lub słaby wskaźnik argumentu.

*PTR*\
Słaby wskaźnik lub udostępniony wskaźnik do skopiowania.

### <a name="remarks"></a>Uwagi

Operatory wszystkie zwalniają aktualnie wskazywane przez siebie `*this` zasoby i przypisują własność zasobu o nazwie *PTR* do. `*this` Jeśli operator zakończy się niepowodzeniem `*this` , pozostaje niezmieniony. Każdy operator ma efekt równoważny z `weak_ptr(ptr).swap(*this)`.

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

## <a name="owner_before"></a>owner_before

Zwraca **wartość PRAWDA** , `weak_ptr` jeśli jest ona uporządkowana przed (lub mniej niż) dostarczonym wskaźnikiem.

```cpp
template <class Other>
bool owner_before(const shared_ptr<Other>& ptr) const noexcept;

template <class Other>
bool owner_before(const weak_ptr<Other>& ptr) const noexcept;
```

### <a name="parameters"></a>Parametry

*PTR*\
Odwołanie lvalue do `shared_ptr` `weak_ptr`lub.

### <a name="remarks"></a>Uwagi

Funkcja członkowska szablonu zwraca **wartość true** , jeśli `*this` jest uporządkowana przed *PTR*.

## <a name="reset"></a>zresetować

Zwalnia posiadane zasoby.

```cpp
void reset() noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwalnia zasób wskazywany przez `*this` i konwertuje `*this` do pustego `weak_ptr` obiektu.

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

## <a name="swap"></a>wymiany

Zamienia dwa `weak_ptr` obiekty.

```cpp
void swap(weak_ptr& wp) noexcept;
```

Obejmuje również specjalizację:

```cpp
template<class T>
void swap(weak_ptr<T>& a, weak_ptr<T>& b) noexcept;
```

### <a name="parameters"></a>Parametry

*dokumenty*\
Słaby wskaźnik do zamiany na.

### <a name="remarks"></a>Uwagi

`*this` `*this`Po, zasób początkowo wskazywany przez program jest wskazywany przez WP, a zasób początkowo wskazywany przez WP jest wskazywany przez. `swap` Funkcja nie zmienia liczby odwołań dla dwóch zasobów i nie generuje żadnych wyjątków. Efekt specjalizacji szablonu jest odpowiednikiem `a.swap(b)`.

### <a name="example"></a>Przykład

```cpp
// std__memory__weak_ptr_swap.cpp
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

## <a name="use_count"></a>use_count

`shared_ptr` Zlicza obiekty należące do zasobu udostępnionego.

```cpp
long use_count() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca liczbę `shared_ptr` obiektów należących do zasobu wskazywanego przez. `*this`

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

## <a name="weak_ptr"></a>weak_ptr

Konstruuje `weak_ptr`a.

```cpp
constexpr weak_ptr() noexcept;

weak_ptr(const weak_ptr& wp) noexcept;

weak_ptr(weak_ptr&& wp) noexcept;

template <class Other>
weak_ptr(const weak_ptr<Other>& wp) noexcept;

template <class Other>
weak_ptr(weak_ptr<Other>&& sp) noexcept;

template <class Other>
weak_ptr(const shared_ptr<Other>& sp) noexcept;
```

### <a name="parameters"></a>Parametry

*Różnych*\
Typ kontrolowany przez argument Shared/słaby wskaźnik. Konstruktory te nie uczestniczą w rozpoznawaniu przeciążenia, chyba `element_type*`że _inne\*_  są zgodne z programem.

*dokumenty*\
Słaby wskaźnik do skopiowania.

*requirement*\
Udostępniony wskaźnik do skopiowania.

### <a name="remarks"></a>Uwagi

Konstruktor domyślny konstruuje pusty `weak_ptr` obiekt. Konstruktory przyjmujące argument każdy konstruują pusty `weak_ptr` obiekt, jeśli wskaźnik argumentu jest pusty. W przeciwnym razie konstruuje `weak_ptr` obiekt, który wskazuje na zasób o nazwie przez argument. Liczba odwołań do obiektu udostępnionego nie została zmieniona.

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

## <a name="tilde-weak_ptr"></a>~ weak_ptr

`weak_ptr`Niszczy.

```cpp
~weak_ptr();
```

### <a name="remarks"></a>Uwagi

Destruktor niszczy ten `weak_ptr` sposób, ale nie ma wpływu na liczbę odwołań obiektu, w którym znajdują się punkty wskaźnika.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](cpp-standard-library-header-files.md)\
[\<memory>](memory.md)\
[Klasa shared_ptr](shared-ptr-class.md)
