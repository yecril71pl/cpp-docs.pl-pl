---
title: Klasa is_trivially_assignable
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_assignable
helpviewer_keywords:
- is_trivially_assignable
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
ms.openlocfilehash: 14a3ee638bd6df3b52e7327ca6e3c77f4a0e8b71
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224867"
---
# <a name="is_trivially_assignable-class"></a>Klasa is_trivially_assignable

Testuje, czy wartość `From` typu może być przypisana do `To` typu

## <a name="syntax"></a>Składnia

```cpp
template <class To, class From>
struct is_trivially_assignable;
```

### <a name="parameters"></a>Parametry

*Do*\
Typ obiektu, który odbiera przypisanie.

*Wniosek*\
Typ obiektu, który zawiera wartość.

## <a name="remarks"></a>Uwagi

Wyrażenie `declval<To>() = declval<From>()` musi być poprawnie sformułowane i musi być znane kompilatorowi, aby nie wymagało nieuproszczonych operacji. Oba `From` i `To` muszą być pełnymi typami **`void`** lub tablicami nieznanego powiązania.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<type_traits>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
