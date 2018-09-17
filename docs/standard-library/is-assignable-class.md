---
title: is_assignable, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_assignable
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 339b3cdb2e2470fea976ef8257e6a84f089d3dd9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712559"
---
# <a name="isassignable-class"></a>is_assignable, klasa

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
