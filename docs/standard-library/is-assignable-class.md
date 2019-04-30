---
title: is_assignable Class
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_assignable
helpviewer_keywords:
- is_assignable
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
ms.openlocfilehash: b1357bf8c5ad4dfd5035855e34a8fd6a7ed73d15
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391013"
---
# <a name="isassignable-class"></a>is_assignable Class

Sprawdza, czy wartość `From` typu mogą być przypisane do `To` typu.

## <a name="syntax"></a>Składnia

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Parametry

*To*<br/>
Typ obiektu, który odbiera przypisania.

*From*<br/>
Typ obiektu, który zawiera wartość.

## <a name="remarks"></a>Uwagi

Wyrażenie nieobliczonym `declval<To>() = declval<From>()` musi być poprawnie sformułowany. Zarówno `From` i `To` muszą być typami pełnymi **void**, lub tablic nieznany powiązane z.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
