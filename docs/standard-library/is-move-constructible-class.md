---
title: is_move_constructible, klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_move_constructible
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
ms.openlocfilehash: 1b1e450338a123c51b80f40f2369207c8b987cd6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508998"
---
# <a name="ismoveconstructible-class"></a>is_move_constructible, klasa

Sprawdza, czy typ ma konstruktora przenoszącego.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, który ma zostać obliczone

## <a name="remarks"></a>Uwagi

Predykat typów, które daje w wyniku wartość true, jeśli typ *T* można skonstruować przy użyciu operacji przenoszenia. Ten predykat jest odpowiednikiem `is_constructible<T, T&&>`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
