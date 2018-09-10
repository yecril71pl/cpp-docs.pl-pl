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
ms.openlocfilehash: bd23064123513281099fa14a690679fa046657fe
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106631"
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
