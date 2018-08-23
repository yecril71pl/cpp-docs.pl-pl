---
title: Module::RegisterCOMObject, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterCOMObject
dev_langs:
- C++
helpviewer_keywords:
- RegisterCOMObject method
ms.assetid: 59f223dc-03c6-429d-95da-b74b3f73b702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: abbe93f5359171c88134ff61759e9edc63db2451
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610436"
---
# <a name="moduleregistercomobject-method"></a>Module::RegisterCOMObject — Metoda

Rejestruje jeden lub więcej obiektów COM, dzięki czemu inne aplikacje mogą łączyć się z nimi.

## <a name="syntax"></a>Składnia

```cpp
WRL_NOTHROW virtual HRESULT RegisterCOMObject(
   const wchar_t* serverName,
   IID* clsids,
   IClassFactory** factories,
   DWORD* cookies,
   unsigned int count);

```

### <a name="parameters"></a>Parametry

*serverName*  
W pełni kwalifikowaną nazwę serwera.

*CLSID*  
Tablica CLSID do zarejestrowania.

*fabryki*  
Tablica interfejsów IUnknown typów obiektów klas, których udostępnienie jest on publikowany.

*Pliki cookie*  
Po zakończeniu operacji, tablicę wskaźników do wartości, które identyfikują klasy obiektów, które zostały zarejestrowane. Wartości te są później używane odwołać rejestracji.

*Liczba*  
Liczba CLSID do zarejestrowania.

## <a name="return-value"></a>Wartość zwracana

S_OK Jeśli okaż; w przeciwnym razie wartość HRESULT takich jak CO_E_OBJISREG, która wskazuje przyczynę operacja nie powiodła się.

## <a name="remarks"></a>Uwagi

Obiekty COM są zarejestrowane w usłudze modułu wyliczającego CLSCTX_LOCAL_SERVER CLSCTX wyliczenia.

Typ połączenia, aby zarejestrowane obiekty jest określony przy użyciu kombinacji bieżącego *comflag* parametrem szablonu i moduł wyliczający REGCLS_SUSPENDED REGCLS wyliczenia.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też
[Klasa modułu](../windows/module-class.md)