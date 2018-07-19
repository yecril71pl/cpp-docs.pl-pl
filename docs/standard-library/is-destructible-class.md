---
title: is_destructible, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_destructible
dev_langs:
- C++
helpviewer_keywords:
- is_destructible
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5b2c9237c7f17217d28e489edef4ab65863b54b
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964119"
---
# <a name="isdestructible-class"></a>is_destructible, klasa

Sprawdza, czy typ jest zniszczalnych.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_destructible;
```

### <a name="parameters"></a>Parametry

*T* typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *T* jest zniszczalnych typu, w przeciwnym razie przechowuje wartość false. Zniszczalnych typy są typami odwołań, typów i typów obiektów gdzie dla pewnego typu `U` równa `remove_all_extents_t<T>` nieobliczonym operand `std::declval<U&>.~U()` jest poprawnie sformułowany. Innych typów, w tym niekompletnych typów **void**i typy funkcji, nie są typami zniszczalnych.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
