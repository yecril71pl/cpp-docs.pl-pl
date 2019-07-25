---
title: is_trivially_move_assignable Class
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_assignable
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
ms.openlocfilehash: 324e4a1f1bd3528f09f21c5e485ac814038b7517
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448383"
---
# <a name="istriviallymoveassignable-class"></a>is_trivially_move_assignable Class

Testuje, czy typ ma operator przypisania prostego przenoszenia.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parametry

*Br*\
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *ty* jest klasą, która ma operator przypisania prostego przenoszenia, w przeciwnym razie ma wartość false.

Operator przypisania przenoszenia dla klasy *ty* jest prosty, jeśli:

jest to niejawnie podane

Klasa *ty* nie ma żadnych funkcji wirtualnych

Klasa *ty* nie ma wirtualnych baz.

klasy wszystkich niestatycznych elementów członkowskich danych typu klasy mają operatory przypisania prostego przenoszenia

klasy wszystkich niestatycznych składowych danych typu Array klasy mają operatory przypisania prostego przenoszenia

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
