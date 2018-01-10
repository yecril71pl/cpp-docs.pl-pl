---
title: "rts_alloc — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::rts_alloc
- allocators/stdext::rts_alloc::allocate
- allocators/stdext::rts_alloc::deallocate
- allocators/stdext::rts_alloc::equals
dev_langs: C++
helpviewer_keywords:
- stdext::rts_alloc
- stdext::rts_alloc [C++], allocate
- stdext::rts_alloc [C++], deallocate
- stdext::rts_alloc [C++], equals
ms.assetid: ab41bffa-83d1-4a1c-87b9-5707d516931f
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2e4870edc0b54a92307ddf88d58dd96ca3fd331e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="rtsalloc-class"></a>rts_alloc — Klasa
Rts_alloc — klasa szablonu opisuje [filtru](../standard-library/allocators-header.md) zawierający tablicę pamięci podręcznej wystąpienia i określa, które wystąpienie na potrzeby alokacji i dezalokacji w czasie wykonywania, a nie w czasie kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Cache>  
class rts_alloc
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Cache`|Typ wystąpienia pamięci podręcznej zawartych w tablicy. Może to być [cache_chunklist — klasa](../standard-library/cache-chunklist-class.md), [cache_freelist —](../standard-library/cache-freelist-class.md), lub [cache_suballoc —](../standard-library/cache-suballoc-class.md).|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa szablonu zawiera blok wiele wystąpień programu przydzielania i określa, które wystąpienie na potrzeby alokacji lub dezalokacji w czasie wykonywania, a nie w czasie kompilacji. Jest ona używana z kompilatorów, których nie można skompilować ponownie Utwórz wiązanie.  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[allocate](#allocate)|Przydziela bloku pamięci.|  
|[cofnięcie przydziału](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu rozpoczynający się od określonej pozycji.|  
|[equals](#equals)|Porównuje dwa pamięci podręcznych pod kątem równości.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<allocators — >  
  
 **Namespace:** stdext —  
  
##  <a name="allocate"></a>rts_alloc::allocate  
 Przydziela bloku pamięci.  
  
```
void *allocate(std::size_t count);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`count`|Liczba elementów w tablicy do przydzielenia.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do przydzielonego obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca `caches[_IDX].allocate(count)`, gdzie indeks `_IDX` jest zależny od rozmiaru żądanego bloku `count`, lub jeśli `count` jest zbyt duży, zwraca `operator new(count)`. `cache`, która reprezentuje buforowany obiekt.  
  
##  <a name="deallocate"></a>rts_alloc::deallocate  
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
 Wywołania funkcji Członkowskich `caches[_IDX].deallocate(ptr, count)`, gdzie indeks `_IDX` jest zależny od rozmiaru żądanego bloku `count`, lub jeśli `count` jest zbyt duży, zwraca `operator delete(ptr)`.  
  
##  <a name="equals"></a>rts_alloc::Equals  
 Porównuje dwa pamięci podręcznych pod kątem równości.  
  
```
bool equals(const sync<_Cache>& _Other) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`_Cache`|Buforowany obiekt skojarzone z filtrem.|  
|`_Other`|Buforowany obiekt do porównania równości.|  
  
### <a name="remarks"></a>Uwagi  
 `true`Jeśli wynik `caches[0].equals(other.caches[0])`; w przeciwnym razie `false`. `caches`reprezentuje tablicę obiektów w pamięci podręcznej.  
  
## <a name="see-also"></a>Zobacz też  
 [ALLOCATOR_DECL —](../standard-library/allocators-functions.md#allocator_decl)   
 [\<allocators — >](../standard-library/allocators-header.md)



