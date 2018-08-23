---
title: RuntimeClass::GetWeakReference, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetWeakReference
dev_langs:
- C++
helpviewer_keywords:
- GetWeakReference method
ms.assetid: 26656ace-7f20-4364-87c9-4a75dd30912e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cc4d2e542afcd72426cb3b0aba57b7d7cbabad06
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583647"
---
# <a name="runtimeclassgetweakreference-method"></a>RuntimeClass::GetWeakReference — Metoda

Pobiera wskaźnik do obiektu słabe odwołanie dla bieżącego **RuntimeClass** obiektu.

## <a name="syntax"></a>Składnia

```cpp
STDMETHOD(
   GetWeakReference
)(_Deref_out_ IWeakReference **weakReference);
```

### <a name="parameters"></a>Parametry

*weakReference*  
Gdy ta operacja zostanie ukończone, wskaźnik do obiektu słabe odwołanie.

## <a name="return-value"></a>Wartość zwracana

Zawsze S_OK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[RuntimeClass, klasa](../windows/runtimeclass-class.md)