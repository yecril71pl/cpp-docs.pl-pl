---
title: is_nothrow_default_constructible, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_default_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_default_constructible
ms.assetid: c576fcc9-5be1-43aa-b93a-64d3f1848887
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38e076d5a8e552efa353be711d84485c96f6ffd3
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962991"
---
# <a name="isnothrowdefaultconstructible-class"></a>is_nothrow_default_constructible —  klasa

Sprawdza, czy typ ma niezgłaszające domyślnego konstruktora.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_nothrow_default_constructible;
```

### <a name="parameters"></a>Parametry

*Ty* typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *Ty* ma nothrow Konstruktor domyślny, w przeciwnym razie przechowuje wartość false. Wystąpienie typu predykatu jest odpowiednikiem `is_nothrow_constructible<Ty>`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
