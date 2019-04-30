---
title: is_trivially_assignable Class
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_assignable
helpviewer_keywords:
- is_trivially_assignable
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
ms.openlocfilehash: eeef85a0b26c25eb745258c7e0e35394f0cab979
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413498"
---
# <a name="istriviallyassignable-class"></a>is_trivially_assignable Class

Sprawdza, czy wartość `From` typu mogą być w przypadku przypisane do `To` typu

## <a name="syntax"></a>Składnia

```cpp
template <class To, class From>
struct is_trivially_assignable;
```

### <a name="parameters"></a>Parametry

*To*<br/>
Typ obiektu, który odbiera przypisania.

*From*<br/>
Typ obiektu, który zawiera wartość.

## <a name="remarks"></a>Uwagi

Wyrażenie `declval<To>() = declval<From>()` musi być poprawnie sformułowany, a musi być znane w kompilatorze, będą musieli ma nieuproszczone operacji. Zarówno `From` i `To` muszą być typami pełnymi **void**, lub tablic nieznany powiązane z.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
