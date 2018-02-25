---
title: "cache_chunklist — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/stdext::cache_chunklist
- allocators/stdext::cache_chunklist::allocate
- allocators/stdext::cache_chunklist::deallocate
dev_langs:
- C++
helpviewer_keywords:
- stdext::cache_chunklist
- stdext::cache_chunklist [C++], allocate
- stdext::cache_chunklist [C++], deallocate
ms.assetid: af19eccc-4ae7-4a34-bbb2-81e397424cb9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: acab7f835ac6bcbad61b4f9fe7157cbda953b2f9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cachechunklist-class"></a>cache_chunklist — Klasa
Definiuje [zablokować alokatora](../standard-library/allocators-header.md) przydziela i zwalnia bloki pamięci o rozmiarze pojedynczego.  
  
## <a name="syntax"></a>Składnia  
  
```
template <std::size_t Sz, std::size_t Nelts = 20>  
class cache_chunklist
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Sz`|Liczba elementów w tablicy do przydzielenia.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa szablonu używa `operator new` przydzielić fragmentów pamięci, suballocating blokuje Aby przydzielić magazyn do bloku pamięci, gdy jest wymagane; przechowuje bloki pamięci deallocated w osobnej listy wolne dla każdego fragmentu i używa `operator delete` można cofnąć alokacji fragmentów, gdy żaden z jego bloki pamięci nie jest w użyciu.  
  
 Każdy blok pamięci przechowuje `Sz` w bajtach dostępnej pamięci i wskaźnika do fragmentów, do którego on należy. Przechowuje każdego fragmentu `Nelts` bloki pamięci, wskaźniki trzy, int i dane który `operator new` i `operator delete` wymagają.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[cache_chunklist](#cache_chunklist)|Tworzy obiekt typu `cache_chunklist`.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[allocate](#allocate)|Przydziela bloku pamięci.|  
|[Cofnięcie przydziału](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu rozpoczynający się od określonej pozycji.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<allocators — >  
  
 **Namespace:** stdext —  
  
##  <a name="allocate"></a>  cache_chunklist::allocate  
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
  
##  <a name="cache_chunklist"></a>  cache_chunklist::cache_chunklist  
 Tworzy obiekt typu `cache_chunklist`.  
  
```
cache_chunklist();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="deallocate"></a>  cache_chunklist::deallocate  
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
 [\<allocators>](../standard-library/allocators-header.md)



