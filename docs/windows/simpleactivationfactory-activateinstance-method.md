---
title: SimpleActivationFactory::ActivateInstance, metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: fe1342c3927183ae5eec30c8dd0a40ee95f37277
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646565"
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
Po zakończeniu tej operacji, wskaźnik do wystąpienia obiektu określonego przez `Base` parametru szablonu klasy.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="remarks"></a>Uwagi

Jeśli &#95; &#95;WRL_STRICT&#95; &#95; jest zdefiniowany, błąd potwierdzenia jest emitowane, jeśli nie jest pochodną klasy bazowej, określona w parametrze szablonu klasy [RuntimeClass](../windows/runtimeclass-class.md), lub nie jest skonfigurowany z WinRt lub WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) wartość wyliczenia.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też
 [SimpleActivationFactory, klasa](../windows/simpleactivationfactory-class.md)