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
ms.openlocfilehash: 6223151acbce299178101735db05f7b4bd516f2f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965516"
---
# <a name="isstandardlayout-class"></a>is_standard_layout — Klasa

Sprawdza, czy typ jest standardowego układu.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_standard_layout;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Ty*|Typ do zapytania|

## <a name="remarks"></a>Uwagi

Wystąpienie tego typu predykatu ma wartość true, jeśli typ *Ty* to klasa, która ma standardowy układ obiektów w pamięci w przeciwnym razie przechowuje wartość false.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
