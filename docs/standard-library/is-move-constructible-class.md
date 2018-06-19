---
title: Klasa is_move_constructible | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d87eac720b205560993a7d6995be8a8fe6ad6194
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843525"
---
# <a name="ismoveconstructible-class"></a>is_move_constructible — klasa

Sprawdza, czy typ ma konstruktora przenoszenia.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Parametry

Typ T, ma zostać obliczone

## <a name="remarks"></a>Uwagi

Predykat typów, która daje w wyniku wartość true, jeśli typ `T` może być skonstruowany przy użyciu operacji przenoszenia. Odpowiada to predykatu `is_constructible<T, T&&>`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
