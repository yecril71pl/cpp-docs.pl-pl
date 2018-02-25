---
title: '&lt;Ustaw&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- set/std::swap (map)
- set/std::swap (multiset)
ms.assetid: d1277d14-8502-46c0-b820-bcda820f9406
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: 65d3f4ef95ee3768323e3b727b9745a1a812f27c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ltsetgt-functions"></a>&lt;Ustaw&gt; funkcji
|||  
|-|-|  
|[swap (map)](#swap)|[swap (multiset)](#swap_multiset)|  
  
##  <a name="swap"></a>  swap (map)
 Zamienia elementy z dwóch zestawów.  
  
```
template <class Key, class Traits, class Allocator>  
void swap(set<Key, Traits, Allocator>& left, set<Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Zestaw, zapewniając elementy zamianę lub zestawu, w której elementy są wymienianych z tymi zestawu `left`.  
  
 `left`  
 Zestaw, której elementy są wymienianych z tymi zestawu `right`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu jest algorytm specjalizowany ustawioną wykonania funkcji członkowskiej klasy kontenera `left.` [wymiany](../standard-library/set-class.md#swap)( `right`). To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonów są przeciążone w taki sposób, dopasowania szablonu z wywołaniem funkcji nie jest unikatowa, kompilator wybierze najbardziej specjalna wersja funkcji szablonu. Ogólne wersji szablonu funkcji  
  
 `template` \< **classT**> **void wymiany**( **T &**, **T &**)  
  
 w algorytmie klasa działa przez przypisanie i jest wolne działanie. Specjalna wersja w poszczególnych kontenerach jest znacznie szybsze może współpracować z reprezentacji wewnętrznej klasy kontenera.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład kodu dla elementu członkowskiego klasy [set::swap](../standard-library/set-class.md#swap) na przykład użyj wersji szablonu `swap`.  
  
##  <a name="swap_multiset"></a>  swap (multiset)
 Zamienia multisets dwa elementy.  
  
```
template <class Key, class Traits, class Allocator>  
void swap(multiset<Key, Traits, Allocator>& left, multiset<Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Zestaw wielokrotny, zapewniając elementy zamianę lub zestaw wielokrotny, której elementy są wymienianych z tymi multiset `left`.  
  
 `left`  
 Zestaw wielokrotny, której elementy są wymienianych z tymi multiset `right`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu jest algorytm specjalizowany na multiset klasy kontenera do wykonywania funkcji członkowskiej `left.` [wymiany](../standard-library/multiset-class.md#swap)( `right`). To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonów są przeciążone w taki sposób, dopasowania szablonu z wywołaniem funkcji nie jest unikatowa, kompilator wybierze najbardziej specjalna wersja funkcji szablonu. Ogólne wersji szablonu funkcji  
  
 `template` \< **classT**> **void wymiany**( **T &**, **T &**)  
  
 w algorytmie klasa działa przez przypisanie i jest wolne działanie. Specjalna wersja w poszczególnych kontenerach jest znacznie szybsze może współpracować z reprezentacji wewnętrznej klasy kontenera.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład kodu dla elementu członkowskiego klasy [multiset::swap](../standard-library/multiset-class.md#swap)na przykład użyj wersji szablonu `swap`.  
  
## <a name="see-also"></a>Zobacz też  
 [\<Ustaw >](../standard-library/set.md)



