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
ms.openlocfilehash: bfee0c0cd7ff7bd7f4525a291184f08f1e2898e5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878739"
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