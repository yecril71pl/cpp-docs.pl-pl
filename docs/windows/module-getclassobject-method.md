---
title: "Module::GetClassObject — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GetClassObject
dev_langs:
- C++
helpviewer_keywords:
- GetClassObject method
ms.assetid: 95b0de1b-f728-4f96-9f44-f6ea71ce56e4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3f234b46da1a70ee0256a9a38ebb2ef7ae0bb5bb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="modulegetclassobject-method"></a>Module::GetClassObject — Metoda
Pobiera fabryki klas pamięci podręcznej.  
  
## <a name="syntax"></a>Składnia  
  
```  
 HRESULT GetClassObject(  
   REFCLSID clsid,  
   REFIID riid,  
   _Deref_out_ void **ppv,  
   wchar_t* serverName = nullptr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `clsid`  
 Identyfikator klasy.  
  
 `riid`  
 Interfejs identyfikator żądania.  
  
 `ppv`  
 Wskaźnik do zwrócony obiekt.  
  
 `serverName`  
 Nazwa serwera określona w albo `ActivatableClassWithFactory`, `ActivatableClassWithFactoryEx`, lub `ActivatableClass` makro; lub `nullptr` można pobrać domyślnej nazwy serwera.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Tej metody można użyć tylko dla modelu COM, nie środowiska uruchomieniowego systemu Windows. Ta metoda opisuje tylko IClassFactory metody.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —
 
 ## <a name="see-also"></a>Zobacz też
 [Klasa modułu](../windows/module-class.md)