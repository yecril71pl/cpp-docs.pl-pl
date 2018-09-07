---
title: aligned_union, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::aligned_union
dev_langs:
- C++
helpviewer_keywords:
- aligned_union
ms.assetid: 9931a44d-3a67-4f29-a0f6-d47a7cf560ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4017fceab100689847ea99df80016aaba2fbd10f
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107669"
---
# <a name="alignedunion-class"></a>aligned_union — klasa

Zawiera typ POD wystarczająco duże i odpowiednio wyrównany do przechowywania typu złożenia i rozmiarem wymaganym.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Len, class... Types>
struct aligned_union;

template <std::size_t Len, class... Types>
using aligned_union_t = typename aligned_union<Len, Types...>::type;
```

### <a name="parameters"></a>Parametry

*Len*<br/>
Wartość wyrównania największego typu w Unii.

*Typy*<br/>
Różne typy w podstawowej Unii.

## <a name="remarks"></a>Uwagi

Użyj klasy szablonu, aby pobrać niezbędne do przechowywania Unii w magazynie niezainicjowanej wielkości i. Element TypeDef stanowi element członkowski `type` nazwy ZASOBNIK, wpisz odpowiednie do przechowywania dowolnego typu na liście *typy*; minimalny rozmiar to *Len*. Statyczny element członkowski `alignment_value` typu `std::size_t` zawiera najbardziej rygorystyczne wyrównanie wymagane przez wszystkie typy, które są wymienione w *typy*.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać `aligned_union` można przydzielić bufora stosu wyrównane do umieszczenia Unii.

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

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[alignment_of, klasa](../standard-library/alignment-of-class.md)<br/>
