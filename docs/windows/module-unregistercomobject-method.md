---
title: Module::UnregisterCOMObject, metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c19e7b5388438b8c3c2359672360e4a2ee3001a3
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39602633"
---
# <a name="moduleunregistercomobject-method"></a>Module::UnregisterCOMObject — Metoda
Wyrejestrowuje jeden lub więcej obiektów COM, co uniemożliwia innych aplikacji na połączenie z nich.  
  
## <a name="syntax"></a>Składnia  
  
```  
virtual HRESULT UnregisterCOMObject(  
   const wchar_t* serverName,  
   DWORD* cookies,  
   unsigned int count  
```  
  
### <a name="parameters"></a>Parametry  
 *serverName*  
 (Nieużywane)  
  
 *Pliki cookie*  
 Tablica wskaźników do wartości, które identyfikują obiektów klasy do wyrejestrowania. Tablica został utworzony przez [registercomobject —](../windows/module-registercomobject-method.md) metody.  
  
 *Liczba*  
 Liczba klasy, aby wyrejestrować.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli operacja się powiedzie; w przeciwnym razie błąd HRESULT, która wskazuje przyczynę operacja nie powiodła się.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Zobacz też
 [Klasa modułu](../windows/module-class.md)