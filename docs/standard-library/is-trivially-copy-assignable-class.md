---
title: Klasa is_trivially_copy_assignable
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
ms.openlocfilehash: c0019257a032d3becc268513336ed59e58a2e1d5
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447996"
---
# <a name="istriviallycopyassignable-class"></a>Klasa is_trivially_copy_assignable

Testuje, czy typ ma operator przypisania prostego kopiowania.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Parametry

*&* \
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *T* jest klasą, która ma operator przypisania prostego kopiowania, w przeciwnym razie zawiera wartość false.

Konstruktor przypisania dla klasy *t* jest uproszczony, jeśli jest niejawnie określony, Klasa *t* nie ma żadnych funkcji wirtualnych, Klasa *t* nie ma żadnych wirtualnych podstaw, klasy wszystkich niestatycznych elementów członkowskich danych typu klasy mają proste przypisanie Operatory i klasy wszystkich niestatycznych elementów członkowskich danych typu Array klasy mają proste operatory przypisania.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
