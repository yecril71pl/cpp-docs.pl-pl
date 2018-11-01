---
title: is_trivially_move_assignable, klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_assignable
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
ms.openlocfilehash: b25d16658def4e3cf620ab707d2dabacb2620f33
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435546"
---
# <a name="istriviallymoveassignable-class"></a>is_trivially_move_assignable, klasa

Sprawdza, czy typ ma operator przypisania przenoszenia prosta.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *Ty* to klasa, która ma proste operator przypisania przenoszenia, w przeciwnym razie przechowuje wartość false.

Operator przypisania przenoszenia dla klasy *Ty* jest proste jeśli:

Domyślnie jest ona udostępniana

Klasa *Ty* ma żadnych funkcji wirtualnych

Klasa *Ty* ma nie baz wirtualnych

klasy wszystkie składowe danych niestatycznych typu klasy mają trivial przenoszące operatory przypisania

klasy wszystkie składowe danych niestatycznych typu tablicowego klasy mają trivial przenoszące operatory przypisania

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
