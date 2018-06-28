---
title: SimpleClassFactory::CreateInstance — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- CreateInstance method
ms.assetid: 17b7947a-2608-49d9-b730-fef76501c9bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8a31d364a6464962b8243cfaced03131a20f9324
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892751"
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

Jeśli &#95; &#95;WRL_STRICT&#95; &#95; jest zdefiniowany, błędu potwierdzenia jest emitowany Jeśli nie jest pochodną klasy podstawowej określonej w parametrze szablonu klasy [runtimeclass —](../windows/runtimeclass-class.md), lub nie jest skonfigurowany z ClassicCom lub WinRtClassicComMix [runtimeclasstype —](../windows/runtimeclasstype-enumeration.md) wartość wyliczenia.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::wrl —

## <a name="see-also"></a>Zobacz też

[SimpleClassFactory, klasa](../windows/simpleclassfactory-class.md)