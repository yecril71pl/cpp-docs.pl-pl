---
title: "sync_per_thread — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/stdext::sync_per_thread
- allocators/stdext::sync_per_thread::allocate
- allocators/stdext::sync_per_thread::deallocate
- allocators/stdext::sync_per_thread::equals
dev_langs:
- C++
helpviewer_keywords:
- stdext::sync_per_thread
- stdext::sync_per_thread [C++], allocate
- stdext::sync_per_thread [C++], deallocate
- stdext::sync_per_thread [C++], equals
ms.assetid: 47bf75f8-5b02-4760-b1d3-3099d08fe14c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f5ddaee26ba4a28a50920a4b71f91e284356b40d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="syncperthread-class"></a>sync_per_thread — Klasa
W tym artykule opisano [filtr synchronizacji](../standard-library/allocators-header.md) zapewnia obiektu osobne dla każdego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Cache>  
class sync_per_thread
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Cache`|Typ pamięci podręcznej skojarzone z filtrem synchronizacji. Może to być [cache_chunklist —](../standard-library/cache-chunklist-class.md), [cache_freelist —](../standard-library/cache-freelist-class.md), lub [cache_suballoc —](../standard-library/cache-suballoc-class.md).|  
  
## <a name="remarks"></a>Uwagi  
 Allocators —, które używają `sync_per_thread` można porównać takie same, mimo że bloki przydzielone w jednym wątku nie można cofnąć alokacji z innego wątku. Kiedy przy użyciu jednej z tych bloków pamięci allocators — przydzielone w jednym wątku nie należy widoczne dla innych wątków. W praktyce oznacza to, że kontener, który korzysta z jednego z tych allocators — powinni mieć dostęp tylko przez pojedynczy wątek.  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[allocate](#allocate)|Przydziela bloku pamięci.|  
|[Cofnięcie przydziału](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu rozpoczynający się od określonej pozycji.|  
|[equals](#equals)|Porównuje dwa pamięci podręcznych pod kątem równości.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<allocators — >  
  
 **Namespace:** stdext —  
  
##  <a name="allocate"></a>  sync_per_thread::allocate  
 Przydziela bloku pamięci.  
  
```
void *allocate(std::size_t count);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`count`|Liczba elementów w tablicy do przydzielenia.|  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca wynik wywołania `cache::allocate(count)` obiektu pamięci podręcznej należących do bieżącego wątku. Jeśli żaden obiekt pamięci podręcznej została przydzielona dla bieżącego wątku, najpierw przydzielania jeden.  
  
##  <a name="deallocate"></a>  sync_per_thread::deallocate  
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
 Wywołania funkcji Członkowskich `deallocate` obiektu pamięci podręcznej należących do bieżącego wątku. Jeśli żaden obiekt pamięci podręcznej została przydzielona dla bieżącego wątku, najpierw przydzielania jeden.  
  
##  <a name="equals"></a>  sync_per_thread::Equals  
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
 `false` Jeśli żaden obiekt pamięci podręcznej została przydzielona dla tego obiektu lub `Other` w bieżącym wątku. W przeciwnym razie zwraca wynik zastosowania `operator==` do dwóch obiektów w pamięci podręcznej.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [\<allocators>](../standard-library/allocators-header.md)



