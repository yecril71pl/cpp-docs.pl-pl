---
title: Klasa integral_constant, Klasa bool_constant
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::integral_constant
- XTR1COMMON/std::integral_constant
- type_traits/std::bool_constant
- XTR1COMMON/std::bool_constant
helpviewer_keywords:
- std::integral_constant [C++]
- std::bool_constant [C++]
ms.assetid: 11c002c6-4d31-4042-9341-f2543f43e108
ms.openlocfilehash: c85da1f3be7821f8d82cd2b19dab2a5864426a5a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452046"
---
# <a name="integralconstant-class-boolconstant-class"></a>Klasa integral_constant, Klasa bool_constant

Tworzy całkowitą stałą na podstawie typu i wartości.

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

*&* \
Typ stałej.

*v*\
Wartość stałej.

## <a name="remarks"></a>Uwagi

Klasa szablonu, gdy jest wyspecjalizowany dla typu całkowitego *T* i wartość v tego typu, reprezentuje obiekt, który przechowuje stałą tego typu całkowitego z określoną wartością.  `integral_constant` Element członkowski o `type` nazwie jest aliasem dla wygenerowanego typu specjalizacji szablonu, `value` a składowa zawiera wartość *v* użytą do utworzenia specjalizacji.

Klasa szablonu jest jawną specjalizacją `integral_constant` częściową, która używa **bool** jako argumentu *T.* `bool_constant`

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

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[< type_traits >](../standard-library/type-traits.md)\
[false_type](../standard-library/type-traits-typedefs.md#false_type)\
[true_type](../standard-library/type-traits-typedefs.md#true_type)
