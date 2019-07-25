---
title: is_integral — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_integral
helpviewer_keywords:
- is_integral class
- is_integral
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
ms.openlocfilehash: a367bb06f49dd2c9c64f0c257a3573add5645efe
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456237"
---
# <a name="isintegral-class"></a>is_integral — Klasa

Testuje, czy typ jest całkowity.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_integral;
```

### <a name="parameters"></a>Parametry

*Br*\
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *ty* jest jednym z typów całkowitych lub `cv-qualified` postaci jednego z typów całkowitych, w przeciwnym razie ma wartość false.

Typem całkowitym jest jeden z wartości typu **bool**, **char**, unsigned char **, wchar_t**, **Short**, unsigned **Short**, **int**, unsigned **int**, **Long**i unsigned **Long**. Ponadto w przypadku kompilatorów, które je dostarczają, typem całkowitym może być jeden z wartości typu **Long**Long, unsigned long **Long**, **__int64**i unsigned **__int64**.

## <a name="example"></a>Przykład

```cpp
// std__type_traits__is_integral.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_integral<trivial> == " << std::boolalpha
        << std::is_integral<trivial>::value << std::endl;
    std::cout << "is_integral<int> == " << std::boolalpha
        << std::is_integral<int>::value << std::endl;
    std::cout << "is_integral<float> == " << std::boolalpha
        << std::is_integral<float>::value << std::endl;

    return (0);
    }
```

```Output
is_integral<trivial> == false
is_integral<int> == true
is_integral<float> == false
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[< type_traits >](../standard-library/type-traits.md)\
[Klasa is_enum](../standard-library/is-enum-class.md)\
[is_floating_point, klasa](../standard-library/is-floating-point-class.md)
