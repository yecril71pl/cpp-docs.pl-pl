---
title: "sync_none — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::sync_none
- allocators/stdext::sync_none::allocate
- allocators/stdext::sync_none::deallocate
- allocators/stdext::sync_none::equals
dev_langs: C++
helpviewer_keywords:
- stdext::sync_none
- stdext::sync_none [C++], allocate
- stdext::sync_none [C++], deallocate
- stdext::sync_none [C++], equals
ms.assetid: f7473cee-14f3-4fe1-88bc-68cd085e59e1
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6b4c21cc7788bdfa6511e93873bf64bcfe796e2a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="syncnone-class"></a>sync_none — Klasa
W tym artykule opisano [filtr synchronizacji](../standard-library/allocators-header.md) zapewnia ma synchronizacji.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Cache>  
class sync_none
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Cache`|Typ pamięci podręcznej skojarzone z filtrem synchronizacji. Może to być [cache_chunklist —](../standard-library/cache-chunklist-class.md), [cache_freelist —](../standard-library/cache-freelist-class.md), lub [cache_suballoc —](../standard-library/cache-suballoc-class.md).|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[Przydziel](#allocate)|Przydziela bloku pamięci.|  
|[cofnięcie przydziału](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu rozpoczynający się od określonej pozycji.|  
|[równa się](#equals)|Porównuje dwa pamięci podręcznych pod kątem równości.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<allocators — >  
  
 **Namespace:** stdext —  
  
##  <a name="allocate"></a>sync_none::allocate  
 Przydziela bloku pamięci.  
  
```
void *allocate(std::size_t count);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`count`|Liczba elementów w tablicy do przydzielenia.|  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca `cache.allocate(count)`, gdzie `cache` obiektu pamięci podręcznej.  
  
##  <a name="deallocate"></a>sync_none::deallocate  
 Zwalnia określoną liczbę obiektów z magazynu rozpoczynający się od określonej pozycji.  
  
```
void deallocate(void* ptr, std::size_t count);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ptr`|Wskaźnik do pierwszego obiektu do cofnięcia alokacji z magazynu.|  
|`count`|Liczba obiektów do cofnięcia alokacji z magazynu.|  
  
### <a name="remarks"></a>Uwagi  
 Wywołania funkcji Członkowskich `cache.deallocate(ptr, count)`, gdzie `cache` reprezentuje buforowany obiekt.  
  
##  <a name="equals"></a>sync_none::Equals  
 Porównuje dwa pamięci podręcznych pod kątem równości.  
  
```
bool equals(const sync<Cache>& Other) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Cache`|Buforowany obiekt filtr synchronizacji.|  
|`Other`|Buforowany obiekt do porównania równości.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Funkcja członkowska zawsze zwraca `true`.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [\<allocators — >](../standard-library/allocators-header.md)



