---
title: "sync_per_container — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/stdext::sync_per_container
- allocators/stdext::sync_per_container::equals
dev_langs:
- C++
helpviewer_keywords:
- sync_per_container class
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2c98e8f7524864e5249c08e2b6f3d4a38ea8e4be
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="syncpercontainer-class"></a>sync_per_container — Klasa
W tym artykule opisano [filtr synchronizacji](../standard-library/allocators-header.md) zapewnia obiektu osobne dla każdego obiektu przydzielania.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Cache>  
class sync_per_container
 : public Cache
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Cache`|Typ pamięci podręcznej skojarzone z filtrem synchronizacji. Może to być [cache_chunklist —](../standard-library/cache-chunklist-class.md), [cache_freelist —](../standard-library/cache-freelist-class.md), lub [cache_suballoc —](../standard-library/cache-suballoc-class.md).|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[equals](#equals)|Porównuje dwa pamięci podręcznych pod kątem równości.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<allocators — >  
  
 **Namespace:** stdext —  
  
##  <a name="equals"></a>  sync_per_container::Equals  
 Porównuje dwa pamięci podręcznych pod kątem równości.  
  
```
bool equals(const sync_per_container<Cache>& Other) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Cache`|Buforowany obiekt filtr synchronizacji.|  
|`Other`|Buforowany obiekt do porównania równości.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Funkcja członkowska zawsze zwraca `false`.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [\<allocators>](../standard-library/allocators-header.md)



