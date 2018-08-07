---
title: Modulebase — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase
dev_langs:
- C++
helpviewer_keywords:
- ModuleBase class
ms.assetid: edce7591-6893-46f7-94a7-382827775548
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b298bcab4c2b3547f2b285fe21d4967f4696fb9d
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605061"
---
# <a name="modulebase-class"></a>ModuleBase — Klasa
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
class ModuleBase;  
```  
  
## <a name="remarks"></a>Uwagi  
 Reprezentuje klasę bazową [modułu](../windows/module-class.md) klasy.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ModuleBase::ModuleBase, konstruktor](../windows/modulebase-modulebase-constructor.md)|Inicjuje wystąpienie `Module` klasy.|  
|[ModuleBase::~ModuleBase, destruktor](../windows/modulebase-tilde-modulebase-destructor.md)|Deinicjuje bieżące wystąpienie `Module` klasy.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ModuleBase::DecrementObjectCount, metoda](../windows/modulebase-decrementobjectcount-method.md)|Po wdrożeniu, zmniejsza liczbę obiektów śledzone przez moduł.|  
|[ModuleBase::IncrementObjectCount, metoda](../windows/modulebase-incrementobjectcount-method.md)|Po wdrożeniu, zwiększa liczbę obiektów śledzonych przez moduł.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ModuleBase`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)