---
title: aligned_union — klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::aligned_union
helpviewer_keywords:
- aligned_union
ms.assetid: 9931a44d-3a67-4f29-a0f6-d47a7cf560ac
ms.openlocfilehash: ae03802549f7791e51dccf1ea98a7b18929a4a4b
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72690105"
---
# <a name="aligned_union-class"></a>aligned_union — klasa

Zapewnia, że typ na jest wystarczająco duży i odpowiednio wyrównany do przechowywania typu Unii i wymagany rozmiar.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Len, class... Types>
struct aligned_union;

template <std::size_t Len, class... Types>
using aligned_union_t = typename aligned_union<Len, Types...>::type;
```

### <a name="parameters"></a>Parametry

*Len* \
Wartość wyrównania dla największego typu w Unii.

*Typy* \
Różne typy w podstawowym związku.

## <a name="remarks"></a>Uwagi

Użyj szablonu klasy, aby uzyskać wyrównanie i rozmiar wymagany do przechowywania Unii w niezainicjowanym magazynie. Element typedef składowej `type` nazwy typu POD odpowiednie do przechowywania dowolnego typu wymienionego w *typach*; minimalny rozmiar to *len*. Statyczny element członkowski `alignment_value` typu `std::size_t` zawiera najdokładniejsze wyrównanie wymagane przez wszystkie typy wymienione w *typach*.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać `aligned_union` do przydzielenia wyrównanego buforu stosu do złożenia.

```cpp
// std__type_traits__aligned_union.cpp
#include <iostream>
#include <type_traits>

union U_type
{
    int i;
    float f;
    double d;
    U_type(float e) : f(e) {}
};

typedef std::aligned_union<16, int, float, double>::type aligned_U_type;

int main()
{
    // allocate memory for a U_type aligned on a 16-byte boundary
    aligned_U_type au;
    // do placement new in the aligned memory on the stack
    U_type* u = new (&au) U_type(1.0f);
    if (nullptr != u)
    {
        std::cout << "value of u->i is " << u->i << std::endl;
        // must clean up placement objects manually!
        u->~U_type();
    }
}
```

```Output
value of u->i is 1065353216
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[< type_traits >](../standard-library/type-traits.md) \
[alignment_of, klasa](../standard-library/alignment-of-class.md)
