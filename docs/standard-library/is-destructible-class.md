---
title: Klasa is_destructible
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_destructible
helpviewer_keywords:
- is_destructible
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
ms.openlocfilehash: 80592a6fca274533a798b2f5a2459d336ee2c301
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452732"
---
# <a name="isdestructible-class"></a>Klasa is_destructible

Testuje, czy typem jest zniszczalnych.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_destructible;
```

### <a name="parameters"></a>Parametry

*&* \
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *T* jest typem zniszczalnych, w przeciwnym razie zawiera wartość false. Typy zniszczalnych to typy odwołań, typy obiektów i typy, w których dla niektórych `U` typów, `remove_all_extents_t<T>` które są równe nieocenianego operandu `std::declval<U&>.~U()` , są poprawnie sformułowane. Inne typy, w tym niekompletne typy, **void**i typy funkcji, nie są typami zniszczalnych.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
