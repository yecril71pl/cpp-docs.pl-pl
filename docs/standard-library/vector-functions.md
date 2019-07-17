---
title: '&lt;Wektor&gt; funkcji'
ms.date: 11/04/2016
f1_keywords:
- vector/std::swap
ms.assetid: 6cdcf043-eef6-4330-83f0-4596fb9f968a
helpviewer_keywords:
- std::swap [vector]
ms.openlocfilehash: cdf67b3cb34546f5d0dfcd9a4f3bd96500c18af9
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68241040"
---
# <a name="ltvectorgt-functions"></a>&lt;Wektor&gt; funkcji

## <a name="swap"></a> swap

Zamienia elementy z dwoma wektorami.

```cpp
template <class Type, class Allocator>
void swap(vector<Type, Allocator>& left, vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*po prawej stronie*\
Wektor zawierająca elementy, które mają być zamienione lub wektora, której elementy są wymieniane z tymi wektora *po lewej stronie*.

*po lewej stronie*\
Wektor, w której elementy są wymieniane z tymi wektora *prawo*.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm przeznaczone na wektor klasy kontenera na wykonanie funkcji elementu członkowskiego `left`. [Vector::swap](../standard-library/vector-class.md) *(prawy*). Są to wystąpień częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonu przeciążone są w sposób dopasowania szablonu za pomocą wywołania funkcji nie jest unikatowa, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólne wersję funkcji szablonu **szablonu** \< **klasa T**> **void wymiany**( **T &** , **T &** ), w algorytmie klasy działa przez przypisanie a wolne działanie. Specjalizowanej wersji w każdym kontenerze jest znacznie szybsza, ponieważ może współpracować z reprezentacji wewnętrznej klasy kontenera.

### <a name="example"></a>Przykład

Zobacz przykład kodu dla funkcji członkowskiej [vector::swap](../standard-library/vector-class.md) przykład, który używa szablonu wersji `swap`.
