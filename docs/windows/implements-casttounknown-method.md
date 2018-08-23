---
title: Implements::CastToUnknown, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: ca3324f7-4136-406b-8698-7389f4f3d3c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 988580a34c030c84c50adfff2741408be4b249cd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42586361"
---
# <a name="implementscasttounknown-method"></a>Implements::CastToUnknown — Metoda

Pobiera wskaźnik do bazowego `IUnknown` interfejsu.

## <a name="syntax"></a>Składnia

```cpp
__forceinline IUnknown* CastToUnknown();
```

## <a name="return-value"></a>Wartość zwracana

Ta operacja zawsze powiedzie się i zwraca `IUnknown` wskaźnika.

## <a name="remarks"></a>Uwagi

Funkcja pomocnika wewnętrznego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Implements, struktura](../windows/implements-structure.md)