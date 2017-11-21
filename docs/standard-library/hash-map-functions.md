---
title: "&lt;hash_map —&gt; funkcje | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
caps.latest.revision: "9"
manager: ghogen
ms.openlocfilehash: 4b98135f1b72c66938d00f16649d011a27369473
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="lthashmapgt-functions"></a>&lt;hash_map —&gt; funkcji
|||  
|-|-|  
|[swap](#swap)|[swap (hash_map)](#swap_hash_map)|  
  
##  <a name="swap_hash_map"></a>swap (hash_map)  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map — klasa](../standard-library/unordered-map-class.md).  
  
 Zamienia hash_maps dwa elementy.  
  
```
void swap(
    hash_map <Key, Type, Traits, Alloctor>& left,
    hash_map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Hash_map —, której elementy są wymienianych z tymi mapy `left`.  
  
 `left`  
 Hash_map —, której elementy są wymienianych z tymi mapy `right`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu jest algorytm specjalizowany na hash_map — klasa kontenera do wykonywania funkcji członkowskiej `left.` [wymiany](../standard-library/basic-ios-class.md#swap)*(prawo*). To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonów są przeciążone w taki sposób, dopasowania szablonu z wywołaniem funkcji nie jest unikatowa, kompilator wybierze najbardziej specjalna wersja funkcji szablonu. Ogólne wersja funkcji szablonu **szablonu \<klasy T > wymiany void (T &, T &)**, w algorytmie pliku nagłówka działa przez przypisanie i jest wolne działanie. Specjalna wersja w poszczególnych kontenerach jest znacznie szybsze może współpracować z reprezentacji wewnętrznej klasy kontenera.  
  
##  <a name="swap"></a>swap  
  
> [!NOTE]
>  Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md).  
  
 Zamienia hash_multimaps dwa elementy.  
  
```
void swap(
    hash_multimap <Key, Type, Traits, Alloctor>& left,
    hash_multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Hash_multimap —, której elementy są wymienianych z tymi mapy `left`.  
  
 `left`  
 Hash_multimap —, której elementy są wymienianych z tymi mapy `right`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu jest algorytm specjalizowany na hash_multimap — klasa kontenera do wykonywania funkcji członkowskiej `left.` [wymiany](../standard-library/hash-multimap-class.md#swap)*(prawo*`)`. To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonów są przeciążone w taki sposób, dopasowania szablonu z wywołaniem funkcji nie jest unikatowa, kompilator wybierze najbardziej specjalna wersja funkcji szablonu. Ogólne wersja funkcji szablonu **szablonu \<klasy T > wymiany void (T &, T &)**, w algorytmie pliku nagłówka działa przez przypisanie i jest wolne działanie. Specjalna wersja w poszczególnych kontenerach jest znacznie szybsze może współpracować z reprezentacji wewnętrznej klasy kontenera.  
  
## <a name="see-also"></a>Zobacz też  
 [< hash_map >](../standard-library/hash-map.md)



