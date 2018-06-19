---
title: integral_constant — klasa, bool_constant klasy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::integral_constant
- XTR1COMMON/std::integral_constant
- type_traits/std::bool_constant
- XTR1COMMON/std::bool_constant
dev_langs:
- C++
helpviewer_keywords:
- std::integral_constant [C++]
- std::bool_constant [C++]
ms.assetid: 11c002c6-4d31-4042-9341-f2543f43e108
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d59c994cba47cf609c13a1d35fbc7fed60fc531f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33844539"
---
# <a name="integralconstant-class-boolconstant-class"></a>integral_constant — klasa, bool_constant — klasa

Sprawia, że typem całkowitym stałej od typu i wartości.

## <a name="syntax"></a>Składnia

```cpp
template<class T, T v>
struct integral_constant {
   static constexpr T value = v;
   typedef T value_type;
   typedef integral_constant<T, v> type;
   constexpr operator value_type() const noexcept;
   constexpr value_type operator()() const noexcept;
   };
```

### <a name="parameters"></a>Parametry

*T* typu stałej.

*v* wartość stałej.

## <a name="remarks"></a>Uwagi

`integral_constant` Klasy szablonu, gdy specjalizowany z typem całkowitym *T* i wartość *v* tego typu reprezentuje obiekt przechowujący stałą tego typu całkowitego na określoną wartość. Element członkowski o nazwie `type` jest aliasem typ wygenerowanego szablonu specjalizacji i `value` elementu członkowskiego zawiera wartość *v* pozwala utworzyć specjalizacji.

`bool_constant` Jawna specjalizacja częściowa jest szablon klasy `integral_constant` używającą `bool` jako *T* argumentu.

## <a name="example"></a>Przykład

```cpp
// std__type_traits__integral_constant.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "integral_constant<int, 5> == "
        << std::integral_constant<int, 5>::value << std::endl;
    std::cout << "integral_constant<bool, false> == " << std::boolalpha
        << std::integral_constant<bool, false>::value << std::endl;

    return (0);
    }

```

```Output
integral_constant<int, 5> == 5
integral_constant<bool, false> == false
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[false_type](../standard-library/type-traits-typedefs.md#false_type)<br/>
[true_type](../standard-library/type-traits-typedefs.md#true_type)<br/>
