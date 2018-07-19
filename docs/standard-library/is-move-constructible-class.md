---
title: is_move_constructible, klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 979e726e1374ac37844472d9e2f9ae8ddd5ddf4d
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965805"
---
# <a name="ismoveconstructible-class"></a>is_move_constructible, klasa

Sprawdza, czy typ ma konstruktora przenoszącego.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Parametry

*T* typu, który ma zostać obliczone

## <a name="remarks"></a>Uwagi

Predykat typów, które daje w wyniku wartość true, jeśli typ *T* można skonstruować przy użyciu operacji przenoszenia. Ten predykat jest odpowiednikiem `is_constructible<T, T&&>`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
