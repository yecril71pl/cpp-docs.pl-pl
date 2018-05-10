---
title: is_standard_layout — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_standard_layout
dev_langs:
- C++
helpviewer_keywords:
- is_standard_layout class
- is_standard_layout
ms.assetid: 15ccf111-f537-45ef-b552-59152a7ba312
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d899d9c56ecc8b27b18498de225bbba6f0d110d2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="isstandardlayout-class"></a>is_standard_layout — Klasa

Testy, jeśli typ jest standardowego układu.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_standard_layout;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`Ty`|Typ do zapytania|

## <a name="remarks"></a>Uwagi

Wystąpienia tego typu predykatu przechowuje wartość PRAWDA, jeśli typ `Ty` jest klasa, która ma układ standardowy wszystkich obiektów w pamięci, w przeciwnym razie posiada wartość false.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
