---
title: is_integral — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_integral
helpviewer_keywords:
- is_integral class
- is_integral
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
ms.openlocfilehash: a3d618b77d69f5d80736ac20304c9184c5963b25
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217769"
---
# <a name="is_integral-class"></a>is_integral — Klasa

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

Typ całkowity to jeden z,,,,,,,,, **`bool`** **`char`** **`unsigned char`** **`signed char`** **`wchar_t`** **`short`** **`unsigned short`** **`int`** **`unsigned int`** **`long`** , i **`unsigned long`** . Ponadto w przypadku kompilatorów, które je dostarczają, typem całkowitym może być jeden z **`long long`** , **`unsigned long long`** , **`__int64`** , i **unsigned __int64**.

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

**Nagłówek:**\<type_traits>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)\
[Klasa is_enum](../standard-library/is-enum-class.md)\
[Klasa is_floating_point](../standard-library/is-floating-point-class.md)
