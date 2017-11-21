---
title: '&lt;Mapa&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
caps.latest.revision: "6"
manager: ghogen
ms.openlocfilehash: 7972ff0d03f0c7b2378f87c311db633dff2a5d13
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltmapgt-functions"></a>&lt;Mapa&gt; funkcji
|||  
|-|-|  
|[swap (map)](#swap)|[swap (multimap)](#swap_multimap)|  
  
##  <a name="swap_multimap"></a>swap (map)
 Zamienia elementy z dwóch map.  
  
```  
template <class key, class T, class _Pr, class _Alloc>  
void swap(
    map<Key, Traits, Compare, Alloctor>& left,  
    map<Key, Traits, Compare, Alloctor>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Mapy, zapewniając elementy zamianę lub mapy, której elementy są wymienianych z tymi mapy `left`.  
  
 `left`  
 Mapy, której elementy są wymienianych z tymi mapy `right`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu jest algorytm specjalizowany na mapie klasy kontenera do wykonywania funkcji członkowskiej `left`.[ wymiany](../standard-library/map-class.md#swap)( `right`). To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonów są przeciążone w taki sposób, dopasowania szablonu z wywołaniem funkcji nie jest unikatowa, kompilator wybierze najbardziej specjalna wersja funkcji szablonu. Ogólne wersja funkcji szablonu **szablonu** \< **klasy T**> **void wymiany**( **T &**, **T &**), w algorytmie klasa działa przez przypisanie i jest wolne działanie. Specjalna wersja w poszczególnych kontenerach jest znacznie szybsze może współpracować z reprezentacji wewnętrznej klasy kontenera.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład kodu dla funkcji członkowskiej [map::swap](../standard-library/map-class.md#swap) na przykład, który używa wersji szablonu `swap`.  
  
##  <a name="swap"></a>swap (multimap)
 Zamienia multimaps dwa elementy.  
  
```  
template <class key, class T, class _Pr, class _Alloc>  
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,  
    multimap<Key, Traits, Compare, Alloctor>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Multimap dostarczanie elementy zamianę lub multimap, której elementy są wymienianych z tymi multimap `left`.  
  
 `left`  
 Multimap, której elementy są wymienianych z tymi multimap `right`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu jest algorytm specjalizowany na mapie klasy kontenera do wykonania na multimap klasy kontenera do wykonywania funkcji członkowskiej `left`.[ wymiany](../standard-library/multimap-class.md#swap) ( `right`). To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonów są przeciążone w taki sposób, dopasowania szablonu z wywołaniem funkcji nie jest unikatowa, kompilator wybierze najbardziej specjalna wersja funkcji szablonu. Ogólne wersja funkcji szablonu **szablonu** \< **klasy T**> **void wymiany**( **T &**, **T &**), w algorytmie klasa działa przez przypisanie i jest wolne działanie. Specjalna wersja w poszczególnych kontenerach jest znacznie szybsze może współpracować z reprezentacji wewnętrznej klasy kontenera.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład kodu dla funkcji członkowskiej [multimap::swap](../standard-library/multimap-class.md#swap) na przykład, który używa wersji szablonu `swap`.  
  
## <a name="see-also"></a>Zobacz też  
 [\<Mapa >](../standard-library/map.md)
