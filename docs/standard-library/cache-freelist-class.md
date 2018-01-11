---
title: "cache_freelist — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::cache_freelist
- allocators/stdext::cache_freelist::allocate
- allocators/stdext::cache_freelist::deallocate
dev_langs: C++
helpviewer_keywords:
- stdext::cache_freelist
- stdext::cache_freelist [C++], allocate
- stdext::cache_freelist [C++], deallocate
ms.assetid: 840694de-36ba-470f-8dae-2b723d5a8cd9
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c971a4aebcd0f0a7c0baa59a445059f681f7e8af
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cachefreelist-class"></a>cache_freelist — Klasa
Definiuje [zablokować alokatora](../standard-library/allocators-header.md) przydziela i zwalnia bloki pamięci o rozmiarze pojedynczego.  
  
## <a name="syntax"></a>Składnia  
  
```
template <std::size_t Sz, class Max>  
class cache_freelist
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Sz`|Liczba elementów w tablicy do przydzielenia.|  
|`Max`|Max Klasa reprezentująca maksymalny rozmiar wolnego listy. Może to być [max_fixed_size —](../standard-library/max-fixed-size-class.md), [max_none —](../standard-library/max-none-class.md), [max_unbounded —](../standard-library/max-unbounded-class.md), lub [max_variable_size —](../standard-library/max-variable-size-class.md).|  
  
## <a name="remarks"></a>Uwagi  
 Cache_freelist — klasa szablonu prowadzi listę wolnego bloki pamięci o rozmiarze `Sz`. Po zapełnieniu listy wolnego używa `operator delete` można cofnąć alokacji pamięci bloki. Gdy wolnego lista jest pusta używa `operator new` można przydzielić nowego bloki pamięci. Maksymalny rozmiar wolnego listy jest określany przez klasy przekazano max klasy `Max` parametru.  
  
 Każdy blok pamięci przechowuje `Sz` w bajtach dostępnej pamięci i danych który `operator new` i `operator delete` wymagają.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[cache_freelist —](#cache_freelist)|Tworzy obiekt typu `cache_freelist`.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[allocate](#allocate)|Przydziela bloku pamięci.|  
|[cofnięcie przydziału](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu rozpoczynający się od określonej pozycji.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<allocators — >  
  
 **Namespace:** stdext —  
  
##  <a name="allocate"></a>cache_freelist::allocate  
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
  
##  <a name="cache_freelist"></a>cache_freelist::cache_freelist  
 Tworzy obiekt typu `cache_freelist`.  
  
```
cache_freelist();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="deallocate"></a>cache_freelist::deallocate  
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
  
## <a name="see-also"></a>Zobacz też  
 [\<allocators — >](../standard-library/allocators-header.md)



