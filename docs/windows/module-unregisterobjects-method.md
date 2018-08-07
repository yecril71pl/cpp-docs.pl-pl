---
title: Module::UnregisterObjects, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterObjects
dev_langs:
- C++
helpviewer_keywords:
- UnregisterObjects method
ms.assetid: 3d8119a7-991d-45e9-b8c5-ed36c0be0332
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bb477b2d5c0a6eabf1e3304c0cadcb34d3910fe5
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39607443"
---
# <a name="moduleunregisterobjects-method"></a>Module::UnregisterObjects — Metoda
Wyrejestrowuje obiektów w określonym module, tak aby inne aplikacje nie mogą nawiązać z nimi.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT UnregisterObjects(  
   ModuleBase* module,  
   const wchar_t* serverName);  
```  
  
### <a name="parameters"></a>Parametry  
 *Moduł*  
 Wskaźnik do modułu.  
  
 *serverName*  
 Kwalifikującym się nazwa, która określa podzbiór obiektów wpływ tej operacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli operacja się powiedzie; w przeciwnym razie błąd HRESULT, która wskazuje przyczynę tej operacji nie powiodło się.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Zobacz też
 [Klasa modułu](../windows/module-class.md)