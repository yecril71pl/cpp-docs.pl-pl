---
title: Module::GetClassObject, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GetClassObject
dev_langs:
- C++
helpviewer_keywords:
- GetClassObject method
ms.assetid: 95b0de1b-f728-4f96-9f44-f6ea71ce56e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 90a1b527d12e581c42fc9519e56d453f845e0b63
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419725"
---
# <a name="modulegetclassobject-method"></a>Module::GetClassObject — Metoda

Retreives pamięci podręcznej fabryki klas.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetClassObject(
   REFCLSID clsid,
   REFIID riid,
   _Deref_out_ void **ppv,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parametry

*Identyfikator klasy*<br/>
Identyfikator klasy.

*Parametr riid*<br/>
Identyfikator interfejsu, który w przypadku żądania.

*ppv*<br/>
Wskaźnik zwracany obiekt.

*serverName*<br/>
Nazwa serwera, który jest określony w jednej `ActivatableClassWithFactory`, `ActivatableClassWithFactoryEx`, lub `ActivatableClass` — makro; lub **nullptr** można pobrać domyślną nazwę serwera.

## <a name="return-value"></a>Wartość zwracana

## <a name="remarks"></a>Uwagi

Użyj tej metody tylko dla modelu COM, nie środowiska wykonawczego Windows. Ta metoda ujawnia tylko `IClassFactory` metody.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Klasa modułu](../windows/module-class.md)