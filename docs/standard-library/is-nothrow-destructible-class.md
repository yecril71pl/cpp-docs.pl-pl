---
title: is_nothrow_destructible, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_destructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_destructible
ms.assetid: 0bbd8a28-e312-4d72-bd28-aac027f974d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee35bd9fd138dce5e9163fe1712083f5671caaa1
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964326"
---
# <a name="isnothrowdestructible-class"></a>is_nothrow_destructible, klasa

Sprawdza, czy typ jest zniszczalnych, destruktor wiadomo, kompilator nie zostać zgłoszony.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_nothrow_destructible;
```

### <a name="parameters"></a>Parametry

*T* typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *T* jest typem zniszczalnych i destruktor jest znany w kompilatorze nie zostać zgłoszony. W przeciwnym razie przechowuje wartość false.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
