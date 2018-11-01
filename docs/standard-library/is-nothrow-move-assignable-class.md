---
title: is_nothrow_move_assignable, klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_move_assignable
helpviewer_keywords:
- is_nothrow_move_assignable
ms.assetid: 000baa02-cbba-49de-9870-af730033348e
ms.openlocfilehash: eb1ddcace7a68bf60154a15117a1c16a438d263d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535931"
---
# <a name="isnothrowmoveassignable-class"></a>is_nothrow_move_assignable, klasa

Sprawdza, czy typ ma **nothrow** przenoszący operator przypisania.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *Ty* ma nothrow operator przypisania przenoszenia, w przeciwnym razie przechowuje wartość false.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
