---
title: "Modulebase — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase
dev_langs:
- C++
helpviewer_keywords:
- ModuleBase class
ms.assetid: edce7591-6893-46f7-94a7-382827775548
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b02efe3ee61234b2439c1cbbae07827d6a879b2a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="modulebase-class"></a>ModuleBase — Klasa
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
class ModuleBase;  
```  
  
## <a name="remarks"></a>Uwagi  
 Reprezentuje klasę podstawową [modułu](../windows/module-class.md) klasy.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ModuleBase::ModuleBase, konstruktor](../windows/modulebase-modulebase-constructor.md)|Inicjuje wystąpienie klasy modułu.|  
|[ModuleBase::~ModuleBase, destruktor](../windows/modulebase-tilde-modulebase-destructor.md)|Deinitializes bieżącego wystąpienia klasy modułu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ModuleBase::DecrementObjectCount, metoda](../windows/modulebase-decrementobjectcount-method.md)|Po zaimplementowaniu, zmniejsza liczbę obiektów śledzone przez moduł.|  
|[ModuleBase::IncrementObjectCount, metoda](../windows/modulebase-incrementobjectcount-method.md)|Po zaimplementowaniu, zwiększa liczbę obiektów śledzone przez moduł.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ModuleBase`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)