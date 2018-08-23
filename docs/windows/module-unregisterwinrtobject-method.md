---
title: Module::UnregisterWinRTObject, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterWinRTObject
dev_langs:
- C++
helpviewer_keywords:
- UnregisterWinRTObject method
ms.assetid: 32334aa7-2293-40d2-9a89-4b02e2e31f3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 88cafb7796ba0dfd1e37902821872e860ddc4baf
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592187"
---
# <a name="moduleunregisterwinrtobject-method"></a>Module::UnregisterWinRTObject — Metoda

Wyrejestrowuje co najmniej jeden obiekt środowiska wykonawczego Windows, tak aby inne aplikacje nie mogą nawiązać z nimi.

## <a name="syntax"></a>Składnia

```cpp
virtual HRESULT UnregisterWinRTObject(
   unsigned int,
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie
);
```

### <a name="parameters"></a>Parametry

*Plik cookie*  
Wskaźnik do wartość, która identyfikuje obiekt klasy, którego rejestracja ma zostać odwołane.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też
[Klasa modułu](../windows/module-class.md)