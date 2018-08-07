---
title: RuntimeClass::GetRuntimeClassName, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetRuntimeClassName
dev_langs:
- C++
helpviewer_keywords:
- GetRuntimeClassName method
ms.assetid: f6388163-fe65-4948-a4bc-ae6826f480e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7706a16a860cf554068dd3416e7c1f8b1fcea311
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608777"
---
# <a name="runtimeclassgetruntimeclassname-method"></a>RuntimeClass::GetRuntimeClassName — Metoda

Pobiera nazwę klasy środowiska uruchomieniowego bieżącego **RuntimeClass** obiektu.

## <a name="syntax"></a>Składnia

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>Parametry

*runtimeName*  
Po zakończeniu tej operacji, nazwa klasy środowiska uruchomieniowego.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="remarks"></a>Uwagi

Błąd potwierdzenia jest emitowane, jeśli &#95; &#95;WRL_STRICT&#95; &#95; lub &#95; &#95;WRL_FORCE_INSPECTABLE_CLASS_MACRO&#95; &#95; nie jest zdefiniowany.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też
 [RuntimeClass, klasa](../windows/runtimeclass-class.md)