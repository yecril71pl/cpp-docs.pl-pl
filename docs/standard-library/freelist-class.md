---
title: "FreeList — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/stdext::freelist
- allocators/stdext::freelist::pop
- allocators/stdext::freelist::push
dev_langs:
- C++
helpviewer_keywords:
- stdext::freelist
- stdext::freelist [C++], pop
- stdext::freelist [C++], push
ms.assetid: 8ad7e35c-4c80-4479-8ede-1a2497b06d71
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2f0e85e247346e71093df393a69b91b579236e2f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="freelist-class"></a>freelist — Klasa
Zarządza listą bloki pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```
template <std::size_t Sz, class Max>  
class freelist
 : public Max
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Sz`|Liczba elementów w tablicy do przydzielenia.|  
|`Max`|Max Klasa reprezentująca maksymalną liczbę elementów, które mają być przechowywane w liście wolne. Max klasa może być [max_none —](../standard-library/max-none-class.md), [max_unbounded —](../standard-library/max-unbounded-class.md), [max_fixed_size —](../standard-library/max-fixed-size-class.md), lub [max_variable_size —](../standard-library/max-variable-size-class.md).|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa szablonu zarządza listą bloki pamięci o rozmiarze `Sz` z maksymalną długość listy określony przez klasę max przekazano `Max`.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[freelist](#freelist)|Tworzy obiekt typu `freelist`.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[POP](#pop)|Usuwa pierwszy blok pamięci z wolnego listy.|  
|[push](#push)|Dodaje blok pamięci do listy.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<allocators — >  
  
 **Namespace:** stdext —  
  
##  <a name="freelist"></a>  FreeList::FreeList  
 Tworzy obiekt typu `freelist`.  
  
```
freelist();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="pop"></a>  FreeList::POP  
 Usuwa pierwszy blok pamięci z wolnego listy.  
  
```
void *pop();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do bloku pamięci usunięty z listy.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca `NULL` Jeśli lista jest pusta. W przeciwnym razie pierwszy blok pamięci usuwa z listy.  
  
##  <a name="push"></a>  FreeList::push  
 Dodaje blok pamięci do listy.  
  
```
bool push(void* ptr);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ptr`|Wskaźnik do bloku pamięci do dodania do listy wolne.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli `full` zwraca funkcja max klasy `false`; w przeciwnym razie `push` funkcja zwraca `false`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `full` zwraca funkcja max klasy `false`, funkcji członkowskiej dodaje blok pamięci wskazywanej przez `ptr` nagłówek listy.  
  
## <a name="see-also"></a>Zobacz też  
 [\<allocators>](../standard-library/allocators-header.md)



