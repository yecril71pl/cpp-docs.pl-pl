---
title: HString::Operator! = — Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator!=
dev_langs:
- C++
ms.assetid: dcdd2aca-e7d6-4bf1-b2de-03efbb430a93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 96131bc566271de9d99d1530ffb407c0870c71a7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604328"
---
# <a name="hstringoperator-operator"></a>HString::Operator!= Operator

Wskazuje, czy dwa parametry nie są równe.

## <a name="syntax"></a>Składnia

```cpp
inline bool operator!=( const HString& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HStringReference& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HStringReference& rhs) throw()

inline bool operator!=( const HSTRING& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HSTRING& rhs) throw()  
```

### <a name="parameters"></a>Parametry

*Lewa strona reguły przepisywania*  
Pierwszy parametr do porównania. *Lewa strona reguły przepisywania* może być **HString** lub `HStringReference` obiektu lub dojścia HSTRING.

*RHS*  
Drugi parametr do porównania. *rhs* może być **HString** lub `HStringReference` obiektu lub dojścia HSTRING.

## <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli *lhs* i *rhs* parametry nie są równe; w przeciwnym razie **false**.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[HString, klasa](../windows/hstring-class.md)