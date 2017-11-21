---
title: "cache_suballoc — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::cache_suballoc
- allocators/stdext::cache_suballoc::allocate
- allocators/stdext::cache_suballoc::deallocate
dev_langs: C++
helpviewer_keywords:
- stdext::cache_suballoc
- stdext::cache_suballoc [C++], allocate
- stdext::cache_suballoc [C++], deallocate
ms.assetid: 9ea9c5e9-1dcc-45d0-b3a7-a56a93d88898
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f835efbe84b05359a9a835f3afbdccf5839fc31c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cachesuballoc-class"></a>cache_suballoc — Klasa
Definiuje [zablokować alokatora](../standard-library/allocators-header.md) przydziela i zwalnia bloki pamięci o rozmiarze pojedynczego.  
  
## <a name="syntax"></a>Składnia  
  
```
template <std::size_t Sz, size_t Nelts = 20>  
class cache_suballoc
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Sz`|Liczba elementów w tablicy do przydzielenia.|  
  
## <a name="remarks"></a>Uwagi  
 Cache_suballoc — klasa szablonu przechowuje bloki pamięci deallocated wolnego liście o długości niepowiązany przy użyciu `freelist<sizeof(Type), max_unbounded>`i suballocates bloki pamięci z większą fragmentu przydzielonych za pomocą `operator new` po wolnego lista jest pusta.  
  
 Przechowuje każdego fragmentu `Sz * Nelts` w bajtach dostępnej pamięci i danych który `operator new` i `operator delete` wymagają. Nigdy nie są zwalniane przydzielone fragmentów.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[cache_suballoc —](#cache_suballoc)|Tworzy obiekt typu `cache_suballoc`.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[Przydziel](#allocate)|Przydziela bloku pamięci.|  
|[cofnięcie przydziału](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu rozpoczynający się od określonej pozycji.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<allocators — >  
  
 **Namespace:** stdext —  
  
##  <a name="allocate"></a>cache_suballoc::allocate  
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
  
##  <a name="cache_suballoc"></a>cache_suballoc::cache_suballoc  
 Tworzy obiekt typu `cache_suballoc`.  
  
```
cache_suballoc();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="deallocate"></a>cache_suballoc::deallocate  
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



