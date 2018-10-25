---
title: '&lt;Wektor&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vector/std::swap
ms.assetid: 6cdcf043-eef6-4330-83f0-4596fb9f968a
helpviewer_keywords:
- std::swap [vector]
ms.openlocfilehash: c93f535bb02cbaa1f688fba84f15d832381156c6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079321"
---
# <a name="ltvectorgt-functions"></a>&lt;Wektor&gt; funkcji

## <a name="swap"></a>  swap

Zamienia elementy z dwoma wektorami.

```cpp
template <class Type, class Allocator>
void swap(vector<Type, Allocator>& left, vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Wektor zawierająca elementy, które mają być zamienione lub wektora, której elementy są wymieniane z tymi wektora *po lewej stronie*.

*left*<br/>
Wektor, w której elementy są wymieniane z tymi wektora *prawo*.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm przeznaczone na wektor klasy kontenera na wykonanie funkcji elementu członkowskiego `left`. [Vector::swap](../standard-library/vector-class.md) *(prawy*). Są to wystąpień częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonu przeciążone są w sposób dopasowania szablonu za pomocą wywołania funkcji nie jest unikatowa, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólne wersję funkcji szablonu **szablonu** \< **klasa T**> **void wymiany**( **T &**, **T &**), w algorytmie klasy działa przez przypisanie a wolne działanie. Specjalizowanej wersji w każdym kontenerze jest znacznie szybsza, ponieważ może współpracować z reprezentacji wewnętrznej klasy kontenera.

### <a name="example"></a>Przykład

Zobacz przykład kodu dla funkcji członkowskiej [vector::swap](../standard-library/vector-class.md) przykład, który używa szablonu wersji `swap`.

## <a name="see-also"></a>Zobacz także

[\<Wektor >](../standard-library/vector.md)<br/>
