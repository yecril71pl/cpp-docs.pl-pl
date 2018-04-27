---
title: Klasa is_nothrow_assignable | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- type_traits/std::is_nothrow_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_assignable
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7f9b162ad4f0ff932314bcc8cb01183eb12a55f0
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="isnothrowassignable-class"></a>is_nothrow_assignable — klasa

Sprawdza, czy wartość `From` typu mogą być przypisane do `To` typu i przypisanie wiadomo, że nie throw.

## <a name="syntax"></a>Składnia

```cpp
template <class To, class From>
struct is_nothrow_assignable;
```

### <a name="parameters"></a>Parametry

Typ obiektu, który odbiera przypisania.

Z typu obiektu, który zawiera wartość.

## <a name="remarks"></a>Uwagi

Wyrażenie `declval<To>() = declval<From>()` musi być poprawnie sformułowany i musi być znane w kompilatorze nie throw. Zarówno `From` i `To` musi być ukończone typy `void`, lub tablic z nieznanym powiązaniem.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
