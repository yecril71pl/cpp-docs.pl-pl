---
title: Klasa is_assignable
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_assignable
helpviewer_keywords:
- is_assignable
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
ms.openlocfilehash: 33b0ce6112119c935ff70e5d619b284acc6ee8c2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456667"
---
# <a name="isassignable-class"></a>Klasa is_assignable

Testuje, `To` czy wartość `From` typu może być przypisana do typu.

## <a name="syntax"></a>Składnia

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Parametry

*Do*\
Typ obiektu, który odbiera przypisanie.

*Wniosek*\
Typ obiektu, który zawiera wartość.

## <a name="remarks"></a>Uwagi

Wyrażenie `declval<To>() = declval<From>()` nieoceniane musi być poprawnie sformułowane. Oba `From` i`To` muszą być pełnymi typami, **void**lub tablicami nieznanego powiązania.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
