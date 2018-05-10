---
title: Module::RegisterWinRTObject — metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 097bf70ebd280d9494ff70ea1d80f53615f3d898
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="moduleregisterwinrtobject-method"></a>Module::RegisterWinRTObject — Metoda
Rejestruje co najmniej jeden obiekt środowiska wykonawczego systemu Windows, więc inne aplikacje mogą łączyć się z nimi.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RegisterWinRTObject(const wchar_t* serverName,  
   wchar_t** activatableClassIds,  
   WINRT_REGISTRATION_COOKIE* cookie,  
   unsigned int count)  
```  
  
#### <a name="parameters"></a>Parametry  
 `serverName`  
 Nazwa, która określa podzbiór obiektów przez tę operację.  
  
 `activatableClassIds`  
 Tablica aktywowalnej CLSID do zarejestrowania.  
  
 `cookie`  
 Wartość, która identyfikuje obiektów klasy, które zostały zarejestrowane. Ta wartość jest używana później na odwołanie rejestracji.  
  
 `count`  
 Liczba obiektów do zarejestrowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie błąd HRESULT, takich jak CO_E_OBJISREG, która wskazuje przyczynę działanie nie powiodło się.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —
 
 ## <a name="see-also"></a>Zobacz też
 [Klasa modułu](../windows/module-class.md)