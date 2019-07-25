---
title: aligned_union — klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::aligned_union
helpviewer_keywords:
- aligned_union
ms.assetid: 9931a44d-3a67-4f29-a0f6-d47a7cf560ac
ms.openlocfilehash: b9ffb4aff4d4d5667ab8d626ea13a21da94ca0c1
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456461"
---
# <a name="alignedunion-class"></a>aligned_union — klasa

Zapewnia, że typ na jest wystarczająco duży i odpowiednio wyrównany do przechowywania typu Unii i wymagany rozmiar.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Len, class... Types>
struct aligned_union;

template <std::size_t Len, class... Types>
using aligned_union_t = typename aligned_union<Len, Types...>::type;
```

### <a name="parameters"></a>Parametry

*Funkcja*\
Wartość wyrównania dla największego typu w Unii.

*Typ*\
Różne typy w podstawowym związku.

## <a name="remarks"></a>Uwagi

Użyj klasy Template, aby uzyskać wyrównanie i rozmiar wymagany do przechowywania Unii w niezainicjowanym magazynie. Element typedef `type` składa nazwy typu pod odpowiednie do przechowywania dowolnego typu wymienionego w *typach*; minimalny rozmiar to *len*. Statyczny element `alignment_value` członkowski typu `std::size_t` zawiera najdokładniejsze wyrównanie wymagane przez wszystkie typy wymienione w *typach*.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak użyć `aligned_union` do przydzielenia wyrównanego buforu stosu, aby umieścić Unię.

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

[< type_traits >](../standard-library/type-traits.md)\
[alignment_of, klasa](../standard-library/alignment-of-class.md)
