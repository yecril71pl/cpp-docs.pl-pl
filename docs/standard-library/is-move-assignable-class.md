---
title: is_move_assignable Class
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_move_assignable
helpviewer_keywords:
- is_move_assignable
ms.assetid: f33137f2-0639-4912-8745-bc0f9fd18d28
ms.openlocfilehash: da4734507bac14ecf0278117deb7668518305be0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351069"
---
# <a name="ismoveassignable-class"></a>is_move_assignable Class

Sprawdza, czy typ może być przejście przypisane.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Typ jest możliwy do przypisania przeniesienia, jeśli odwołania rvalue do tego typu mogą być przypisane do odwołanie do typu. Predykat typów jest odpowiednikiem `is_assignable<T&, T&&>`. Przenieś można przypisać typy obejmują którego można się odwoływać typów skalarnych i typów klasy, które mają generowanych przez kompilator lub zdefiniowanych przez użytkownika operatorów przypisania przenoszenia.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
