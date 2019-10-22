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
ms.openlocfilehash: 9577ce51d4b0773f7b309fe3dc6dcb5820693dcb
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689536"
---
# <a name="integral_constant-class-bool_constant-class"></a>Klasa integral_constant, Klasa bool_constant

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

*T* \
Typ stałej.

\ *v*
Wartość stałej.

## <a name="remarks"></a>Uwagi

Szablon klasy `integral_constant`, gdy jest wyspecjalizowany dla typu całkowitego *t* i wartość *v* tego typu, reprezentuje obiekt, który przechowuje stałą tego typu całkowitego z określoną wartością. Element członkowski o nazwie `type` jest aliasem dla wygenerowanego typu specjalizacji szablonu, a element członkowski `value` przechowuje wartość *v* używaną do tworzenia specjalizacji.

Szablon klasy `bool_constant` jest jawnym częściową specjalizacją `integral_constant`, która używa **bool** jako argumentu *t* .

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

[< type_traits >](../standard-library/type-traits.md) \
[false_type](../standard-library/type-traits-typedefs.md#false_type) \
[true_type](../standard-library/type-traits-typedefs.md#true_type)
