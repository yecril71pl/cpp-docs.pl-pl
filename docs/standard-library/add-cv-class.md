---
title: add_cv — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_cv
helpviewer_keywords:
- add_cv class
- add_cv
ms.assetid: a5572c78-a097-45d7-b476-ed4876889dea
ms.openlocfilehash: 37001815710b197ec77ed0d45a16ea971ad1edce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613210"
---
# <a name="addcv-class"></a>add_cv — Klasa

Sprawia, że **const volatile** typu z typu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct add_cv;

template <class T>
using add_cv_t = typename add_cv<T>::type;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ do modyfikacji.

## <a name="remarks"></a>Uwagi

Wystąpienie typu zmodyfikowane `add_cv<T>` ma `type` elementu członkowskiego **— typedef** odpowiednikiem *T* zmodyfikowane przez oba [add_volatile —](../standard-library/add-volatile-class.md) i [ add_const —](../standard-library/add-const-class.md), chyba że *T* już zawiera kwalifikatory cv, jest odwołaniem lub jest funkcją.

`add_cv_t<T>` Pomocnika typ jest skrótem do `add_cv<T>` elementu członkowskiego typedef `type`.

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

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_const, klasa](../standard-library/remove-const-class.md)<br/>
[remove_volatile, klasa](../standard-library/remove-volatile-class.md)<br/>
