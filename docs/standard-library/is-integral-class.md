---
title: is_integral — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_integral
helpviewer_keywords:
- is_integral class
- is_integral
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
ms.openlocfilehash: 89655517c73f7c84f48f8b85a1c119674950ebeb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556627"
---
# <a name="isintegral-class"></a>is_integral — Klasa

Sprawdza, czy typ jest integralną częścią.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_integral;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *Ty* jest jednym z typów całkowitych lub `cv-qualified` postaci jednego z typów całkowitych, w przeciwnym razie przechowuje wartość false.

Przykładem jest typem całkowitym **bool**, **char**, **unsigned char**, **podpisany char**, **wchar_t**, **krótki**, **typ unsigned short**, **int**, **unsigned int**, **długie**i **unsigned long**. Ponadto za pomocą kompilatorów, które zapewniają ich typ całkowity może być jednym z **long long**, **unsigned long long**, **__int64**, i **unsigned __int64**.

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

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_enum, klasa](../standard-library/is-enum-class.md)<br/>
[is_floating_point, klasa](../standard-library/is-floating-point-class.md)<br/>
