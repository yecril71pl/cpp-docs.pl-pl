---
title: "Factorycache — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Details::FactoryCache
dev_langs: C++
helpviewer_keywords: FactoryCache structure
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fbb6b32fbd34794c13d2f4b7dc75e242464bc7b9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|[Factorycache::cookie — członek danych](../windows/factorycache-cookie-data-member.md)|Zawiera wartość, która identyfikuje zarejestrowanego obiektu klasy środowiska wykonawczego systemu Windows lub COM i jest później używany do wyrejestrowania obiektu.|  
|[Factorycache::Factory — członek danych](../windows/factorycache-factory-data-member.md)|Wskazuje fabrykę klas środowiska wykonawczego systemu Windows lub COM.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `FactoryCache`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)