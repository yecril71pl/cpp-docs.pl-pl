---
title: is_integral — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_integral
dev_langs:
- C++
helpviewer_keywords:
- is_integral class
- is_integral
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 531ee45aed64daa19f818bc5c8480a9c1b032d30
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="isintegral-class"></a>is_integral — Klasa

Testy, jeśli typ jest integralną częścią.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_integral;
```

### <a name="parameters"></a>Parametry

`Ty` Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu posiada wartość true Jeśli typ `Ty` jest jednym z typów całkowitych lub `cv-qualified` postaci jednego z typów całkowitych, w przeciwnym razie posiada wartość false.

Typ całkowity jest jednym z `bool`, `char`, `unsigned char`, `signed char`, `wchar_t`, `short`, `unsigned short`, `int`, `unsigned int`, `long`, i `unsigned long`. Ponadto z kompilatorów, które zapewniają im typ całkowity może być jedną z `long long`, `unsigned long long`, `__int64`, i `unsigned __int64`.

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

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_enum, klasa](../standard-library/is-enum-class.md)<br/>
[is_floating_point, klasa](../standard-library/is-floating-point-class.md)<br/>
