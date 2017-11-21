---
title: "Module::RegisterWinRTObject — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::RegisterWinRTObject
dev_langs: C++
helpviewer_keywords: RegisterWinRTObject method
ms.assetid: a2782c9c-b9c5-4e4b-9c8d-ef513aea20c5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5893f1321b39c58ea399701e14c659a36304fce1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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