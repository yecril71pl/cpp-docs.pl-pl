---
title: is_trivially_assignable, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_assignable
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd0a8bbffd3a6e0f03635b659dd3743e12c9f077
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700768"
---
# <a name="istriviallyassignable-class"></a>is_trivially_assignable, klasa

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
