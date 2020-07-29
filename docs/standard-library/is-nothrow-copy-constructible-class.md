---
title: is_nothrow_copy_constructible — klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_copy_constructible
helpviewer_keywords:
- is_nothrow_copy_constructible
ms.assetid: f13a0bea-63b1-492a-9a45-d445df35c282
ms.openlocfilehash: ff88eacc8b692436bc5c7dfa3a01340527862809
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222358"
---
# <a name="is_nothrow_copy_constructible-class"></a>is_nothrow_copy_constructible — klasa

Testuje, czy typ ma **`nothrow`** Konstruktor kopiujący.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_nothrow_copy_constructible;
```

### <a name="parameters"></a>Parametry

*Br*\
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *ty* ma Konstruktor kopiujący nothrow, w przeciwnym razie ma wartość false.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<type_traits>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
