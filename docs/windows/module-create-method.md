---
title: Module::Create — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Create
dev_langs:
- C++
helpviewer_keywords:
- Create method
ms.assetid: bfa97fd7-5226-4604-92a5-3b9697053e64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 99ede64c239909956f1f767db34a2a6a14c02314
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874892"
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

 