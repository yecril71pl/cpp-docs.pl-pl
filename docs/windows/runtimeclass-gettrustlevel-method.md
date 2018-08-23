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
ms.openlocfilehash: c714f37a53e111c90333352610fd73532ac86fe7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599835"
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

Błąd potwierdzenia jest emitowane, jeśli `__WRL_STRICT__` lub `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` nie jest zdefiniowany.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[RuntimeClass, klasa](../windows/runtimeclass-class.md)