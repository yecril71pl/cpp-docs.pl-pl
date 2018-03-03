---
title: "Factorycache — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
dev_langs:
- C++
helpviewer_keywords:
- FactoryCache structure
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0fc48c9a3651e8c5a6609886862c2f73c5707638
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="factorycache-structure"></a>FactoryCache — Struktura
Obsługuje infrastrukturę Biblioteka szablonów C++ środowiska wykonawczego systemu Windows i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct FactoryCache;  
```  
  
## <a name="remarks"></a>Uwagi  
 Zawiera lokalizację fabrykę klas i wartość, która identyfikuje zarejestrowaną activelocation lub modelu COM klasy obiektu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[FactoryCache::cookie, składowa danych](../windows/factorycache-cookie-data-member.md)|Zawiera wartość, która identyfikuje zarejestrowanego obiektu klasy środowiska wykonawczego systemu Windows lub COM i jest później używany do wyrejestrowania obiektu.|  
|[FactoryCache::factory, składowa danych](../windows/factorycache-factory-data-member.md)|Wskazuje fabrykę klas środowiska wykonawczego systemu Windows lub COM.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `FactoryCache`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)