---
title: is_destructible, klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_destructible
helpviewer_keywords:
- is_destructible
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
ms.openlocfilehash: 1036a3756a736ee3916ed9fca84aa935bb0ba2cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62336832"
---
# <a name="isdestructible-class"></a>is_destructible, klasa

Sprawdza, czy typ jest zniszczalnych.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_destructible;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *T* jest zniszczalnych typu, w przeciwnym razie przechowuje wartość false. Zniszczalnych typy są typami odwołań, typów i typów obiektów gdzie dla pewnego typu `U` równa `remove_all_extents_t<T>` nieobliczonym operand `std::declval<U&>.~U()` jest poprawnie sformułowany. Innych typów, w tym niekompletnych typów **void**i typy funkcji, nie są typami zniszczalnych.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
