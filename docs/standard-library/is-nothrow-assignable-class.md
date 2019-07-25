---
title: Klasa is_nothrow_assignable
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_assignable
helpviewer_keywords:
- is_nothrow_assignable
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
ms.openlocfilehash: 9ee8b5f97c92b6eb378db40f93696e5e6c554205
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456018"
---
# <a name="isnothrowassignable-class"></a>Klasa is_nothrow_assignable

Testuje, czy wartość typu *from* może być przypisana *do typu,* a przypisanie jest nieznane.

## <a name="syntax"></a>Składnia

```cpp
template <class To, class From>
struct is_nothrow_assignable;
```

### <a name="parameters"></a>Parametry

*Do*\
Typ obiektu, który odbiera przypisanie.

*Wniosek*\
Typ obiektu, który zawiera wartość.

## <a name="remarks"></a>Uwagi

Wyrażenie `declval<To>() = declval<From>()` musi być poprawnie sformułowane i musi być znane kompilatorowi, aby nie zgłaszać. Oba elementy *od* i *do* muszą być pełnymi typami, **void**lub tablicami nieznanego powiązania.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
