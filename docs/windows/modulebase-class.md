---
title: "Modulebase — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::ModuleBase
dev_langs: C++
helpviewer_keywords: ModuleBase class
ms.assetid: edce7591-6893-46f7-94a7-382827775548
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fe24bd4995acb7a36f6aa50378a03b519c8d8e3e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|[Modulebase::modulebase — Konstruktor](../windows/modulebase-modulebase-constructor.md)|Inicjuje wystąpienie klasy modułu.|  
|[ModuleBase:: ~ ModuleBase — destruktor](../windows/modulebase-tilde-modulebase-destructor.md)|Deinitializes bieżącego wystąpienia klasy modułu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ModuleBase::DecrementObjectCount — metoda](../windows/modulebase-decrementobjectcount-method.md)|Po zaimplementowaniu, zmniejsza liczbę obiektów śledzone przez moduł.|  
|[ModuleBase::IncrementObjectCount — metoda](../windows/modulebase-incrementobjectcount-method.md)|Po zaimplementowaniu, zwiększa liczbę obiektów śledzone przez moduł.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ModuleBase`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)