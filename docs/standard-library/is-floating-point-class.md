---
title: is_floating_point — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_floating_point
helpviewer_keywords:
- is_floating_point class
- is_floating_point
ms.assetid: 070679c1-115b-4ee4-8ab7-f52e5d9e157f
ms.openlocfilehash: 242c55cfa6b62e49aa5b73de0aa1a353c16827f9
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51517738"
---
# <a name="isfloatingpoint-class"></a>is_floating_point — Klasa

Sprawdza, czy typ jest liczba zmiennoprzecinkowa.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_floating_point;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *Ty* jest zmiennoprzecinkowy typu punktu lub `cv-qualified` typu formularza zmiennoprzecinkowej, w przeciwnym razie przechowuje wartość false.

A punktem typu zmiennoprzecinkowego jest jednym z **float**, **double**, lub **typu long double**.

## <a name="example"></a>Przykład

```cpp
// std__type_traits__is_floating_point.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_floating_point<trivial> == " << std::boolalpha
        << std::is_floating_point<trivial>::value << std::endl;
    std::cout << "is_floating_point<int> == " << std::boolalpha
        << std::is_floating_point<int>::value << std::endl;
    std::cout << "is_floating_point<float> == " << std::boolalpha
        << std::is_floating_point<float>::value << std::endl;

    return (0);
    }
```

```Output
is_floating_point<trivial> == false
is_floating_point<int> == false
is_floating_point<float> == true
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_integral, klasa](../standard-library/is-integral-class.md)<br/>
