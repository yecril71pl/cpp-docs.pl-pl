---
title: '&lt;Ustaw&gt; funkcji'
ms.date: 11/04/2016
f1_keywords:
- set/std::swap (map)
- set/std::swap (multiset)
ms.assetid: d1277d14-8502-46c0-b820-bcda820f9406
ms.openlocfilehash: a3a63fb86caa3485b1ee14538c3eb1f1ff72923e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246411"
---
# <a name="ltsetgt-functions"></a>&lt;Ustaw&gt; funkcji

## <a name="swap"></a> swap (map)

Zamienia elementy z dwóch zestawów.

```cpp
template <class Key, class Traits, class Allocator>
void swap(set<Key, Traits, Allocator>& left, set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*po prawej stronie*\
Zestaw zawierająca elementy, które mają być zamienione lub zestawu, w której elementy są wymieniane z tymi zestawu *po lewej stronie*.

*po lewej stronie*\
Zestaw, w której elementy są wymieniane z tymi zestawu *prawo*.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm wyspecjalizowane klasy kontenera, ustaw na wykonanie funkcji elementu członkowskiego `left.` [wymiany](../standard-library/set-class.md#swap)(`right`). To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonu przeciążone są w sposób dopasowania szablonu za pomocą wywołania funkcji nie jest unikatowa, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólne wersję funkcji szablonu

`template` \< **classT**> **void wymiany**( **T &** , **T &** )

w algorytmie klasa działa przez przypisanie i jest wolne działanie. Specjalizowanej wersji w każdym kontenerze jest znacznie szybsza, ponieważ może współpracować z reprezentacji wewnętrznej klasy kontenera.

### <a name="example"></a>Przykład

Zobacz przykład kodu klasy członkowskiej [set::swap](../standard-library/set-class.md#swap) przykład korzystania z wersji szablonu `swap`.

## <a name="swap_multiset"></a> swap (multiset)

Zamienia elementy z dwóch multisets.

```cpp
template <class Key, class Traits, class Allocator>
void swap(multiset<Key, Traits, Allocator>& left, multiset<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*po prawej stronie*\
Zestaw wielokrotny, zawierająca elementy, które mają być zamienione lub multiset, której elementy są wymieniane z tymi zestaw wielokrotny *po lewej stronie*.

*po lewej stronie*\
Zestaw wielokrotny, której elementy są wymieniane z tymi zestaw wielokrotny *prawo*.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm przeznaczone na multiset klasy kontenera na wykonanie funkcji elementu członkowskiego `left.` [wymiany](../standard-library/multiset-class.md#swap)(`right`). To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonu przeciążone są w sposób dopasowania szablonu za pomocą wywołania funkcji nie jest unikatowa, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólne wersję funkcji szablonu

`template` \< **classT**> **void wymiany**( **T &** , **T &** )

w algorytmie klasa działa przez przypisanie i jest wolne działanie. Specjalizowanej wersji w każdym kontenerze jest znacznie szybsza, ponieważ może współpracować z reprezentacji wewnętrznej klasy kontenera.

### <a name="example"></a>Przykład

Zobacz przykład kodu klasy członkowskiej [multiset::swap](../standard-library/multiset-class.md#swap)przykład korzystania z wersji szablonu `swap`.
