---
title: Module::GetClassObject — metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 9205b04fc27e1c6e0e6133a08c3c2f69ffdfc314
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878541"
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