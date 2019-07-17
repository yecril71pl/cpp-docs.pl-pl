---
title: '&lt;Mapa&gt; funkcji'
ms.date: 11/04/2016
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
ms.openlocfilehash: e7876b37bfc006eaecf2f1e36273c5ae8689dad4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243286"
---
# <a name="ltmapgt-functions"></a>&lt;Mapa&gt; funkcji

## <a name="swap_multimap"></a> swap (map)

Zamienia elementy z dwóch map.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    map<Key, Traits, Compare, Alloctor>& left,
    map<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Parametry

*po prawej stronie*\
Mapa zawierająca elementy, które mają być zamienione lub mapy, w której elementy są wymieniane z tymi mapy *po lewej stronie*.

*po lewej stronie*\
Mapy, w której elementy są wymieniane z tymi mapy *prawo*.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm przeznaczone na mapie klasy kontenera na wykonanie funkcji elementu członkowskiego `left`.[ wymiany](../standard-library/map-class.md#swap)( `right`). To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonu przeciążone są w sposób dopasowania szablonu za pomocą wywołania funkcji nie jest unikatowa, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólne wersję funkcji szablonu **szablonu** \< **klasa T**> **void wymiany**( **T &** , **T &** ), w algorytmie klasy działa przez przypisanie a wolne działanie. Specjalizowanej wersji w każdym kontenerze jest znacznie szybsza, ponieważ może współpracować z reprezentacji wewnętrznej klasy kontenera.

### <a name="example"></a>Przykład

Zobacz przykład kodu dla funkcji członkowskiej [map::swap](../standard-library/map-class.md#swap) przykład, który używa szablonu wersji `swap`.

## <a name="swap"></a> swap (multimap)

Zamienia elementy z dwóch multimaps.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,
    multimap<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Parametry

*po prawej stronie*\
Multimap, zawierająca elementy, które mają być zamienione lub multimap, której elementy są wymieniane z tymi Mapa wielokrotna *po lewej stronie*.

*po lewej stronie*\
Multimap, której elementy są wymieniane z tymi Mapa wielokrotna *prawo*.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm przeznaczone na mapie klasy kontenera do wykonania na multimap klasy kontenera na wykonanie funkcji elementu członkowskiego `left`.[ wymiany](../standard-library/multimap-class.md#swap) (`right`). To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonu przeciążone są w sposób dopasowania szablonu za pomocą wywołania funkcji nie jest unikatowa, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólne wersję funkcji szablonu **szablonu** \< **klasa T**> **void wymiany**( **T &** , **T &** ), w algorytmie klasy działa przez przypisanie a wolne działanie. Specjalizowanej wersji w każdym kontenerze jest znacznie szybsza, ponieważ może współpracować z reprezentacji wewnętrznej klasy kontenera.

### <a name="example"></a>Przykład

Zobacz przykład kodu dla funkcji członkowskiej [multimap::swap](../standard-library/multimap-class.md#swap) przykład, który używa szablonu wersji `swap`.
