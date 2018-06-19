---
title: SimpleActivationFactory::ActivateInstance — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance
dev_langs:
- C++
helpviewer_keywords:
- ActivateInstance method
ms.assetid: 4f836e51-5a6c-4bad-b871-9f25199298b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5af4bfd22302b7694b9bafbc1452d636b19cb3c7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889426"
---
# <a name="simpleactivationfactoryactivateinstance-method"></a>SimpleActivationFactory::ActivateInstance — Metoda

Tworzy wystąpienie określonego interfejsu.

## <a name="syntax"></a>Składnia

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

### <a name="parameters"></a>Parametry

*ppvObject*  
Po zakończeniu tej operacji, wskaźnik do wystąpienia obiektu określonego przez `Base` parametr szablonu klasy.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="remarks"></a>Uwagi

Jeśli &#95; &#95;WRL_STRICT&#95; &#95; jest zdefiniowany, błędu potwierdzenia jest emitowany Jeśli nie jest pochodną klasy podstawowej określonej w parametrze szablonu klasy [runtimeclass —](../windows/runtimeclass-class.md), lub nie jest skonfigurowany z WinRt lub WinRtClassicComMix [runtimeclasstype —](../windows/runtimeclasstype-enumeration.md) wartość wyliczenia.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::wrl —

## <a name="see-also"></a>Zobacz też

[SimpleActivationFactory, klasa](../windows/simpleactivationfactory-class.md)