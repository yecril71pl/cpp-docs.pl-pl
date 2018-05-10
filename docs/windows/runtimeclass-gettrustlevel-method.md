---
title: RuntimeClass::GetTrustLevel — metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: bc588950cc8752a7c2b8e1ddf00b2193aaf0f395
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="runtimeclassgettrustlevel-method"></a>RuntimeClass::GetTrustLevel — Metoda

Pobiera bieżący obiekt runtimeclass — poziom zaufania.

## <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>Parametry

*trustLvl*  
Po tej operacji zakończeniu bieżącego obiektu runtimeclass — poziom zaufania.

## <a name="return-value"></a>Wartość zwracana

Zawsze S_OK.

## <a name="remarks"></a>Uwagi

Błąd potwierdzenia jest emitowany Jeśli &#95; &#95;WRL_STRICT&#95; &#95; lub &#95; &#95;WRL_FORCE_INSPECTABLE_CLASS_MACRO&#95; &#95; nie jest zdefiniowany.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl —

## <a name="see-also"></a>Zobacz też

[RuntimeClass, klasa](../windows/runtimeclass-class.md)