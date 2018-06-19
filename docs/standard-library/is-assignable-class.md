---
title: Klasa is_assignable | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: bd8b757ab46d462bd5d6a596f7dbbfdd18061a8d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843002"
---
# <a name="isassignable-class"></a>is_assignable — klasa

Sprawdza, czy wartość `From` typu mogą być przypisane do `To` typu.

## <a name="syntax"></a>Składnia

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Parametry

Typ obiektu, który odbiera przypisania.

Z typu obiektu, który zawiera wartość.

## <a name="remarks"></a>Uwagi

Wyrażenie, którego nie obliczono `declval<To>() = declval<From>()` musi być poprawnie sformułowany. Zarówno `From` i `To` musi być ukończone typy `void`, lub tablic z nieznanym powiązaniem.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
