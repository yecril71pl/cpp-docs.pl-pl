---
title: RuntimeClass::GetIids, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetIids
dev_langs:
- C++
helpviewer_keywords:
- GetIids method
ms.assetid: 826a67d1-ebc4-4940-b5d5-7cd66885e4a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d3c16d54b08d0c687b33381107eb17be351e9d6f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589485"
---
# <a name="runtimeclassgetiids-method"></a>RuntimeClass::GetIids — Metoda

Pobiera tablicę, która może zawierać interfejsu identyfikatory implementowane przez bieżącą **RuntimeClass** obiektu.

## <a name="syntax"></a>Składnia

```cpp
STDMETHOD(
   GetIids
)  
   (_Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Parametry

*iidCount*  
Po zakończeniu tej operacji, całkowita liczba elementów w tablicy *IID*.

*IID*  
Gdy ta operacja zostanie ukończone, wskaźnik do tablicy identyfikatorów interfejsu.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie E_OUTOFMEMORY.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[RuntimeClass, klasa](../windows/runtimeclass-class.md)