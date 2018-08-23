---
title: WeakRef::operator&amp; Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::operator&
dev_langs:
- C++
helpviewer_keywords:
- operator& operator
ms.assetid: 900afb73-3801-4d08-9b41-2e6a62011ccd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f8bb81ca1591fc398b1d0814fca918309169e82c
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600987"
---
# <a name="weakrefoperatoramp-operator"></a>WeakRef::operator&amp; — Operator

Zwraca `ComPtrRef` obiekt, który reprezentuje bieżący **WeakRef** obiektu.

## <a name="syntax"></a>Składnia

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()  
```

## <a name="return-value"></a>Wartość zwracana

A `ComPtrRef` obiekt, który reprezentuje bieżący **WeakRef** obiektu.

## <a name="remarks"></a>Uwagi

Jest to wewnętrzny pomocnika operatora, który nie jest przeznaczona do użycia w kodzie.

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[WeakRef, klasa](../windows/weakref-class.md)