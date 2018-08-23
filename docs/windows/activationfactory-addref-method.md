---
title: ActivationFactory::AddRef, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::AddRef
dev_langs:
- C++
helpviewer_keywords:
- AddRef method
ms.assetid: dfe96189-ddbe-410a-9f8d-5d8ecc8cc7e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9b3790e0fb3d1b304359677ddedab2b65dcfe89d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42575744"
---
# <a name="activationfactoryaddref-method"></a>ActivationFactory::AddRef — Metoda

Zwiększa liczbę odwołań bieżącego **activationfactory —** obiektu.

## <a name="syntax"></a>Składnia

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który opisuje błąd.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[ActivationFactory, klasa](../windows/activationfactory-class.md)