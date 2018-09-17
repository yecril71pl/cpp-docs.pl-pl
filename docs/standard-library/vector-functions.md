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
ms.openlocfilehash: 71594b225c950714d8b9aba169e68804033c93a2
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700755"
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
