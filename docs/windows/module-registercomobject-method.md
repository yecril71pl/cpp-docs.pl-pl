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
ms.openlocfilehash: 8c997b4221dee913a6eaad55f6f114b0ad9d820e
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606543"
---
# <a name="moduleregistercomobject-method"></a>Module::RegisterCOMObject — Metoda
Rejestruje jeden lub więcej obiektów COM, dzięki czemu inne aplikacje mogą łączyć się z nimi.  
  
## <a name="syntax"></a>Składnia  
  
```  
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