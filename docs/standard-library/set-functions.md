---
title: '&lt;Ustaw&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- set/std::swap (map)
- set/std::swap (multiset)
ms.assetid: d1277d14-8502-46c0-b820-bcda820f9406
ms.openlocfilehash: 0baea9b63bb012396847c6408625bbcc62001d0d
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110295"
---
# <a name="ltsetgt-functions"></a>&lt;Ustaw&gt; funkcji

|||
|-|-|
|[swap (map)](#swap)|[swap (multiset)](#swap_multiset)|

## <a name="swap"></a>  swap (map)

Zamienia elementy z dwóch zestawów.

```cpp
template <class Key, class Traits, class Allocator>
void swap(set<Key, Traits, Allocator>& left, set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Zestaw zawierająca elementy, które mają być zamienione lub zestawu, w której elementy są wymieniane z tymi zestawu *po lewej stronie*.

*left*<br/>
Zestaw, w której elementy są wymieniane z tymi zestawu *prawo*.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm wyspecjalizowane klasy kontenera, ustaw na wykonanie funkcji elementu członkowskiego `left.` [wymiany](../standard-library/set-class.md#swap)(`right`). To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonu przeciążone są w sposób dopasowania szablonu za pomocą wywołania funkcji nie jest unikatowa, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólne wersję funkcji szablonu

`template` \< **classT**> **void wymiany**( **T &**, **T &**)

w algorytmie klasa działa przez przypisanie i jest wolne działanie. Specjalizowanej wersji w każdym kontenerze jest znacznie szybsza, ponieważ może współpracować z reprezentacji wewnętrznej klasy kontenera.

### <a name="example"></a>Przykład

Zobacz przykład kodu klasy członkowskiej [set::swap](../standard-library/set-class.md#swap) przykład korzystania z wersji szablonu `swap`.

## <a name="swap_multiset"></a>  swap (multiset)

Zamienia elementy z dwóch multisets.

```cpp
template <class Key, class Traits, class Allocator>
void swap(multiset<Key, Traits, Allocator>& left, multiset<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Zestaw wielokrotny, zawierająca elementy, które mają być zamienione lub multiset, której elementy są wymieniane z tymi zestaw wielokrotny *po lewej stronie*.

*left*<br/>
Zestaw wielokrotny, której elementy są wymieniane z tymi zestaw wielokrotny *prawo*.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm przeznaczone na multiset klasy kontenera na wykonanie funkcji elementu członkowskiego `left.` [wymiany](../standard-library/multiset-class.md#swap)(`right`). To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonu przeciążone są w sposób dopasowania szablonu za pomocą wywołania funkcji nie jest unikatowa, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólne wersję funkcji szablonu

`template` \< **classT**> **void wymiany**( **T &**, **T &**)

w algorytmie klasa działa przez przypisanie i jest wolne działanie. Specjalizowanej wersji w każdym kontenerze jest znacznie szybsza, ponieważ może współpracować z reprezentacji wewnętrznej klasy kontenera.

### <a name="example"></a>Przykład

Zobacz przykład kodu klasy członkowskiej [multiset::swap](../standard-library/multiset-class.md#swap)przykład korzystania z wersji szablonu `swap`.

## <a name="see-also"></a>Zobacz także

[\<Ustaw >](../standard-library/set.md)<br/>
