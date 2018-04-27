---
title: Klasa is_trivially_assignable | Dokumentacja firmy Microsoft
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
- type_traits/std::is_trivially_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_assignable
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5b9ccc4937ec4f54756482fd8c3f7028506ca50d
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="istriviallyassignable-class"></a>is_trivially_assignable — klasa

Sprawdza, czy wartość `From` typu mogą być trivially przypisane do `To` typu

## <a name="syntax"></a>Składnia

```cpp
template <class To, class From>
struct is_trivially_assignable;
```

### <a name="parameters"></a>Parametry

Typ obiektu, który odbiera przypisania.

Z typu obiektu, który zawiera wartość.

## <a name="remarks"></a>Uwagi

Wyrażenie `declval<To>() = declval<From>()` musi być poprawnie sformułowany, a musi być znane w kompilatorze wymagające ma nieuproszczone operacji. Zarówno `From` i `To` musi być ukończone typy `void`, lub tablic z nieznanym powiązaniem.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
