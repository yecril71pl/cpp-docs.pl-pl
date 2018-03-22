---
title: Module::Create — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Create
dev_langs:
- C++
helpviewer_keywords:
- Create method
ms.assetid: bfa97fd7-5226-4604-92a5-3b9697053e64
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e566b34140c0b82072c8469cd8d965f807e244ec
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="modulecreate-method"></a>Module::Create — Metoda
Tworzy wystąpienie modułu.  
  
## <a name="syntax"></a>Składnia  
  
```  
WRL_NOTHROW static Module& Create();  
template<typename T>  
WRL_NOTHROW static Module& Create(  
   T callback  
);  
template<typename T>  
WRL_NOTHROW static Module& Create(  
   _In_ T* object,  
   _In_ void (T::* method)()  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ modułu.  
  
 `callback`  
 Wywołuje się po zwolnieniu ostatniego wystąpienia obiektu modułu.  
  
 `object`  
 `object` i `method` parametry są używane w połączeniu. Wskazuje ostatni obiekt wystąpienia po zwolnieniu ostatniego wystąpienia obiektu w module.  
  
 `method`  
 `object` i `method` parametry są używane w połączeniu. Wskazuje metodę ostatniego wystąpienia obiektu po zwolnieniu ostatniego wystąpienia obiektu w module.  
  
## <a name="return-value"></a>Wartość zwracana  
 Odwołanie do modułu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
[Klasa modułu](../windows/module-class.md)

 