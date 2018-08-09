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
ms.openlocfilehash: 8a09128bd334fc6e0987e39eaf51c19aadce34ea
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647550"
---
# <a name="factorycache-structure"></a>FactoryCache — Struktura
Obsługuje infrastrukturę Biblioteka szablonów C++ środowiska wykonawczego Windows i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
struct FactoryCache;  
```  
  
## <a name="remarks"></a>Uwagi  
 Zawiera lokalizację fabryki klas i wartość, która identyfikuje zarejestrowany wrt lub obiekt klasy COM.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[FactoryCache::cookie, składowa danych](../windows/factorycache-cookie-data-member.md)|Zawiera wartość, która identyfikuje zarejestrowanych obiektu klasy środowiska wykonawczego Windows lub COM i jest później używany do wyrejestrowania obiektu.|  
|[FactoryCache::factory, składowa danych](../windows/factorycache-factory-data-member.md)|Wskazuje fabrykę klas Windows Runtime lub COM.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `FactoryCache`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)