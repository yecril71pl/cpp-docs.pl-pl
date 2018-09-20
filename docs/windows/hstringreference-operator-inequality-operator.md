---
title: HStringReference::Operator! = — Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator!=
dev_langs:
- C++
ms.assetid: 01ab6691-1fc7-4feb-85f0-fe795593a160
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 996ead81a72fb3cc58544576059a8347972e2a6b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429074"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator!= Operator

Wskazuje, czy dwa parametry nie są równe.

## <a name="syntax"></a>Składnia

```cpp
inline bool operator==(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()  
```

### <a name="parameters"></a>Parametry

*Lewa strona reguły przepisywania*<br/>
Pierwszy parametr do porównania. *Lewa strona reguły przepisywania* może być **HStringReference** obiektu lub dojścia HSTRING.

*RHS*<br/>
Drugi parametr do porównania.  *RHS* może być **HStringReference** obiektu lub dojścia HSTRING.

## <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli *lhs* i *rhs* parametry nie są równe; w przeciwnym razie **false**.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[HStringReference, klasa](../windows/hstringreference-class.md)