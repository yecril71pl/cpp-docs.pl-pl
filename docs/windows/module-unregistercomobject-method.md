---
title: "Module::UnregisterCOMObject — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::UnregisterCOMObject
dev_langs: C++
helpviewer_keywords: UnregisterCOMObject method
ms.assetid: 5d377525-0385-482a-a215-6e8a1f032861
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 43ea6ab8f3990316be7bce27c06b3aee0df8fbf4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="moduleunregistercomobject-method"></a>Module::UnregisterCOMObject — Metoda
Wyrejestrowuje co najmniej jeden obiekt COM, co zapobiega inne aplikacje połączyć się z nimi.  
  
## <a name="syntax"></a>Składnia  
  
```  
virtual HRESULT UnregisterCOMObject(  
   const wchar_t* serverName,  
   DWORD* cookies,  
   unsigned int count  
```  
  
#### <a name="parameters"></a>Parametry  
 `serverName`  
 (I nieużywanych)  
  
 `cookies`  
 Tablica wskaźnikami do wartości, które identyfikują obiektów klasy do wyrejestrowania. Tablica został utworzony przez [RegisterCOMObject](../windows/module-registercomobject-method.md) metody.  
  
 `count`  
 Liczba klas wyrejestrować.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli operacja zakończy się pomyślnie; w przeciwnym razie błąd HRESULT, która wskazuje przyczynę działanie nie powiodło się.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —
 
 ## <a name="see-also"></a>Zobacz też
 [Klasa modułu](../windows/module-class.md)