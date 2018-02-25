---
title: '&lt;Wektor&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vector/std::swap
ms.assetid: 6cdcf043-eef6-4330-83f0-4596fb9f968a
helpviewer_keywords:
- std::swap [vector]
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: e752c3d39787466928b11ff8d644cf9a6558b656
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ltvectorgt-functions"></a>&lt;Wektor&gt; funkcji

  
##  <a name="swap"></a>  Swap  
 Zamienia elementy dwa wektory.  
  
```  
template <class Type, class Allocator>  
void swap(vector<Type, Allocator>& left, vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Wektor zapewnianie elementów zamianę lub wektora, której elementy są wymienianych z tymi wektora `left`.  
  
 `left`  
 Wektor, której elementy są wymienianych z tymi wektora `right`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu jest algorytm specjalizowany na wektor klasy kontenera do wykonywania funkcji członkowskiej `left`. [Vector::swap](../standard-library/vector-class.md) *(prawo*). Te są wystąpieniami klasy częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonów są przeciążone w taki sposób, dopasowania szablonu z wywołaniem funkcji nie jest unikatowa, kompilator wybierze najbardziej specjalna wersja funkcji szablonu. Ogólne wersja funkcji szablonu **szablonu** \< **klasy T**> **void wymiany**( **T &**, **T &**), w algorytmie klasa działa przez przypisanie i jest wolne działanie. Specjalna wersja w poszczególnych kontenerach jest znacznie szybsze może współpracować z reprezentacji wewnętrznej klasy kontenera.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład kodu dla funkcji członkowskiej [vector::swap](../standard-library/vector-class.md) na przykład, który używa wersji szablonu `swap`.  
  
## <a name="see-also"></a>Zobacz też  
 [\<Wektor >](../standard-library/vector.md)

