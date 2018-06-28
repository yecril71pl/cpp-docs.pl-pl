---
title: RuntimeClass::GetRuntimeClassName — metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 3cfe3cc4a8a304bbd04fde9e6c38e2b9170e2e73
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892442"
---
# <a name="runtimeclassgetruntimeclassname-method"></a>RuntimeClass::GetRuntimeClassName — Metoda

Pobiera bieżący obiekt runtimeclass — Nazwa klasy środowiska wykonawczego.

## <a name="syntax"></a>Składnia

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>Parametry

*runtimeName*  
Po zakończeniu wykonywania tej operacji, nazwa klasy środowiska uruchomieniowego.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="remarks"></a>Uwagi

Błąd potwierdzenia jest emitowany Jeśli &#95; &#95;WRL_STRICT&#95; &#95; lub &#95; &#95;WRL_FORCE_INSPECTABLE_CLASS_MACRO&#95; &#95; nie jest zdefiniowany.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl —

## <a name="see-also"></a>Zobacz też

[RuntimeClass, klasa](../windows/runtimeclass-class.md)