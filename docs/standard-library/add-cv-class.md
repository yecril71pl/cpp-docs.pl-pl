---
title: add_cv — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_cv
helpviewer_keywords:
- add_cv class
- add_cv
ms.assetid: a5572c78-a097-45d7-b476-ed4876889dea
ms.openlocfilehash: 0afeea71daf8358b2aeeefe8d368c135a54a6ad6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222631"
---
# <a name="add_cv-class"></a>add_cv — Klasa

Tworzy **`const volatile`** Typ z typu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct add_cv;

template <class T>
using add_cv_t = typename add_cv<T>::type;
```

### <a name="parameters"></a>Parametry

*&*\
Typ do modyfikacji.

## <a name="remarks"></a>Uwagi

Wystąpienie zmodyfikowanego typu `add_cv<T>` ma `type` element członkowski, **`typedef`** który jest odpowiednikiem *T* modyfikowany przez obie [Add_volatile](add-volatile-class.md) i [add_const](add-const-class.md), chyba że *T* ma już kwalifikatory CV, jest odwołaniem lub jest funkcją.

`add_cv_t<T>`Typ pomocnika to skrót umożliwiający dostęp do `add_cv<T>` elementu członkowskiego typedef `type` .

## <a name="example"></a>Przykład

```cpp
// add_cv.cpp
// compile by using: cl /EHsc /W4 add_cv.cpp
#include <type_traits>
#include <iostream>

struct S {
    void f() {
        std::cout << "invoked non-cv-qualified S.f()" << std::endl;
    }
    void f() const {
        std::cout << "invoked const S.f()" << std::endl;
    }
    void f() volatile {
        std::cout << "invoked volatile S.f()" << std::endl;
    }
    void f() const volatile {
        std::cout << "invoked const volatile S.f()" << std::endl;
    }
};

template <class T>
void invoke() {
    T t;
    ((T *)&t)->f();
}

int main()
{
    invoke<S>();
    invoke<std::add_const<S>::type>();
    invoke<std::add_volatile<S>::type>();
    invoke<std::add_cv<S>::type>();
}
```

```Output
invoked non-cv-qualified S.f()
invoked const S.f()
invoked volatile S.f()
invoked const volatile S.f()
```

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<type_traits>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](type-traits.md)\
[Klasa remove_const](remove-const-class.md)\
[Klasa remove_volatile](remove-volatile-class.md)
