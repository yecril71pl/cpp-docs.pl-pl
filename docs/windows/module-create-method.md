---
title: Module::CREATE, metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c0d49a6f0b5172b0971f755fc61b7767f0f4427d
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603306"
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
  
### <a name="parameters"></a>Parametry  
 *T*  
 Typ modułu.  
  
 *Wywołanie zwrotne*  
 Wywołuje się, gdy ostatni obiekt wystąpienia modułu jest zwalniany.  
  
 *object*  
 *Obiektu* i *metoda* parametry są używane w połączeniu. Wskazuje ostatni obiekt wystąpienia po udostępnieniu ostatni obiekt wystąpienia w module.  
  
 *— Metoda*  
 *Obiektu* i *metoda* parametry są używane w połączeniu. Wskazuje metodę ostatniego wystąpienia obiektu po udostępnieniu ostatni obiekt wystąpienia w module.  
  
## <a name="return-value"></a>Wartość zwracana  
 Odwołanie do modułu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
[Klasa modułu](../windows/module-class.md)