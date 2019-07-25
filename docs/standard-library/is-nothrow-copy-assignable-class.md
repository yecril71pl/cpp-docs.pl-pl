---
title: is_nothrow_copy_assignable Class
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_copy_assignable
helpviewer_keywords:
- is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
ms.openlocfilehash: 330c97cd945e161d2bf47deb377dd732bf53b3c9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455982"
---
# <a name="isnothrowcopyassignable-class"></a>is_nothrow_copy_assignable Class

Testuje, czy typ ma operator przypisania kopiowania, który jest znany przez kompilator, aby nie zgłaszać.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_nothrow_copy_assignable;
```

### <a name="parameters"></a>Parametry

*&* \
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true dla typu referencyjnego *T* , gdzie `is_nothrow_assignable<T&, const T&>` ma wartość true; w przeciwnym razie ma wartość false.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[< type_traits >](../standard-library/type-traits.md)\
[is_nothrow_assignable, klasa](../standard-library/is-nothrow-assignable-class.md)
