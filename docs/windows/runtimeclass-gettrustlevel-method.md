---
title: RuntimeClass::GetTrustLevel, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetTrustLevel
dev_langs:
- C++
helpviewer_keywords:
- GetTrustLevel method
ms.assetid: bd90407e-6dd7-41c3-9ea0-c402c276014a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 98bd73d2c067e6d5bbb4425782de594bbaa47bc1
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606627"
---
# <a name="runtimeclassgettrustlevel-method"></a>RuntimeClass::GetTrustLevel — Metoda

Pobiera bieżący poziom zaufania **RuntimeClass** obiektu.

## <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>Parametry

*trustLvl*  
Po zakończeniu tej operacji, bieżący poziom zaufania **RuntimeClass** obiektu.

## <a name="return-value"></a>Wartość zwracana

Zawsze S_OK.

## <a name="remarks"></a>Uwagi

Błąd potwierdzenia jest emitowane, jeśli &#95; &#95;WRL_STRICT&#95; &#95; lub &#95; &#95;WRL_FORCE_INSPECTABLE_CLASS_MACRO&#95; &#95; nie jest zdefiniowany.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też
 [RuntimeClass, klasa](../windows/runtimeclass-class.md)