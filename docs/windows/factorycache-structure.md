---
title: Factorycache — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
dev_langs:
- C++
helpviewer_keywords:
- FactoryCache structure
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 04356316b67f3c341fe1dd1821750fcd3136aa40
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
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