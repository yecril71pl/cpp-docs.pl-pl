---
title: Conditional — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::conditional
dev_langs:
- C++
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a553c2975dd5a58673bd4caa6e7c9ba25d33183
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106616"
---
# <a name="conditional-class"></a>conditional — Klasa

Wybiera jeden z dwóch typów, w zależności od określonego warunku.

## <a name="syntax"></a>Składnia

```cpp
template <bool B, class T1, class T2>
struct conditional;

template <bool _Test, class _T1, class _T2>
using conditional_t = typename conditional<_Test, _T1, _T2>::type;
```

### <a name="parameters"></a>Parametry

*B*<br/>
Wartość, która określa wybrany typ.

*T1*<br/>
Wynik typu, gdy B ma wartość true.

*T2*<br/>
Wynik typu, gdy B ma wartość false.

## <a name="remarks"></a>Uwagi

Szablon elementu członkowskiego typedef `conditional<B, T1, T2>::type` daje w wyniku *T1* podczas *B* daje w wyniku **true**i daje w wyniku *T2* podczas  *B* daje w wyniku **false**.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
