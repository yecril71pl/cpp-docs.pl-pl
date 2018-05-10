---
title: Module::UnregisterCOMObject — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterCOMObject
dev_langs:
- C++
helpviewer_keywords:
- UnregisterCOMObject method
ms.assetid: 5d377525-0385-482a-a215-6e8a1f032861
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: de4cc44d88f59e18f2c1644e9b27a9214ad32962
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
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