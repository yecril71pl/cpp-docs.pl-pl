---
title: HString::Operator&lt; Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator<
dev_langs:
- C++
ms.assetid: 48a051cb-4609-42be-b48c-d35fc99d1eab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fa4a10235f37a3ea174965ad56f63d078e3cbde2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403594"
---
# <a name="hstringoperatorlt-operator"></a>HString::Operator&lt; — Operator

Wskazuje, czy pierwszy parametr jest mniejszy od drugiego parametru.

## <a name="syntax"></a>Składnia

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()  
```

### <a name="parameters"></a>Parametry

*Lewa strona reguły przepisywania*<br/>
Pierwszy parametr do porównania. *Lewa strona reguły przepisywania* może być odwołaniem do **HString**.

*RHS*<br/>
Drugi parametr do porównania. *RHS* może być odwołaniem do **HString**.

## <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli *lhs* parametr jest mniejsza niż *rhs* parametru; w przeciwnym razie **false**.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[HString, klasa](../windows/hstring-class.md)