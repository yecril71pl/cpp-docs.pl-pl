---
title: "SimpleClassFactory::CreateInstance — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- CreateInstance method
ms.assetid: 17b7947a-2608-49d9-b730-fef76501c9bc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 68778eb1b5421cfcf22261d8b1c1efd99bc32c50
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="simpleclassfactorycreateinstance-method"></a>SimpleClassFactory::CreateInstance — Metoda

Tworzy wystąpienie określonego interfejsu.

## <a name="syntax"></a>Składnia

```cpp
STDMETHOD( CreateInstance )(
   _Inout_opt_ IUnknown* pUnkOuter,
   REFIID riid,
   _Deref_out_ void** ppvObject
);
```

### <a name="parameters"></a>Parametry

*Parametr pUnkOuter*  
Musi być `nullptr`; w przeciwnym razie wartość zwracana jest CLASS_E_NOAGGREGATION.

Simpleclassfactory — nie obsługuje agregacji. Jeśli są obsługiwane agregacji i tworzony obiekt został część agregacji, `pUnkOuter` jest wskaźnik do sterującego interfejsu IUnknown agregacji.

*Parametr riid*  
Identyfikator obiektu do tworzenia interfejsu.

*ppvObject*  
Po zakończeniu tej operacji, wskaźnik do wystąpienia obiektu określonego przez `riid` parametru.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="remarks"></a>Uwagi

Jeśli &#95; &#95; WRL_STRICT &#95; &#95; jest zdefiniowany, błędu potwierdzenia jest emitowany Jeśli nie jest pochodną klasy podstawowej określonej w parametrze szablonu klasy [runtimeclass —](../windows/runtimeclass-class.md), lub nie jest skonfigurowana z ClassicCom lub WinRtClassicComMix [runtimeclasstype — ](../windows/runtimeclasstype-enumeration.md) wartość wyliczenia.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::wrl —

## <a name="see-also"></a>Zobacz też

[SimpleClassFactory, klasa](../windows/simpleclassfactory-class.md)