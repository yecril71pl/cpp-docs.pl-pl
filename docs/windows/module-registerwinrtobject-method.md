---
title: Module::RegisterWinRTObject, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterWinRTObject
dev_langs:
- C++
helpviewer_keywords:
- RegisterWinRTObject method
ms.assetid: a2782c9c-b9c5-4e4b-9c8d-ef513aea20c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 42ec736126e2381b00542bf71afca0b9db187df7
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603760"
---
# <a name="moduleregisterwinrtobject-method"></a>Module::RegisterWinRTObject — Metoda
Rejestruje co najmniej jeden obiekt środowiska wykonawczego Windows, dzięki czemu inne aplikacje mogą łączyć się z nimi.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RegisterWinRTObject(const wchar_t* serverName,  
   wchar_t** activatableClassIds,  
   WINRT_REGISTRATION_COOKIE* cookie,  
   unsigned int count)  
```  
  
### <a name="parameters"></a>Parametry  
 *serverName*  
 Nazwa, która określa podzbiór obiektów wpływ tej operacji.  
  
 *activatableClassIds*  
 Tablica aktywowalnej CLSID do zarejestrowania.  
  
 *Plik cookie*  
 Wartość, która identyfikuje obiektów klas, które zostały zarejestrowane. Ta wartość jest używana później, aby można było odwołać rejestracji.  
  
 *Liczba*  
 Liczba obiektów do zarejestrowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie błąd HRESULT, takich jak CO_E_OBJISREG, która wskazuje przyczynę operacja nie powiodła się.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Zobacz też
 [Klasa modułu](../windows/module-class.md)