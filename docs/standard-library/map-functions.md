---
title: '&lt;Mapa&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
ms.openlocfilehash: 3c6cb7d0308e4bafc531fe0baf0c5d666228c3ec
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966371"
---
# <a name="ltmapgt-functions"></a>&lt;Mapa&gt; funkcji

|||
|-|-|
|[swap (map)](#swap)|[swap (multimap)](#swap_multimap)|

## <a name="swap_multimap"></a>  swap (map)

Zamienia elementy z dwóch map.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    map<Key, Traits, Compare, Alloctor>& left,
    map<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Parametry

*prawy* mapy zawierająca elementy, które mają być zamienione lub mapy, w której elementy są wymieniane z tymi mapy *po lewej stronie*.

*po lewej stronie* mapy, w której elementy są wymieniane z tymi mapy *prawo*.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm przeznaczone na mapie klasy kontenera na wykonanie funkcji elementu członkowskiego `left`.[ wymiany](../standard-library/map-class.md#swap)( `right`). To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonu przeciążone są w sposób dopasowania szablonu za pomocą wywołania funkcji nie jest unikatowa, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólne wersję funkcji szablonu **szablonu** \< **klasa T**> **void wymiany**( **T &**, **T &**), w algorytmie klasy działa przez przypisanie a wolne działanie. Specjalizowanej wersji w każdym kontenerze jest znacznie szybsza, ponieważ może współpracować z reprezentacji wewnętrznej klasy kontenera.

### <a name="example"></a>Przykład

Zobacz przykład kodu dla funkcji członkowskiej [map::swap](../standard-library/map-class.md#swap) przykład, który używa szablonu wersji `swap`.

## <a name="swap"></a>  swap (multimap)

Zamienia elementy z dwóch multimaps.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,
    multimap<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Parametry

*prawy* multimap zawierająca elementy, które mają być zamienione lub multimap, której elementy są wymieniane z tymi Mapa wielokrotna *po lewej stronie*.

*po lewej stronie* multimap, której elementy są wymieniane z tymi Mapa wielokrotna *prawo*.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm przeznaczone na mapie klasy kontenera do wykonania na multimap klasy kontenera na wykonanie funkcji elementu członkowskiego `left`.[ wymiany](../standard-library/multimap-class.md#swap) (`right`). To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonu przeciążone są w sposób dopasowania szablonu za pomocą wywołania funkcji nie jest unikatowa, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólne wersję funkcji szablonu **szablonu** \< **klasa T**> **void wymiany**( **T &**, **T &**), w algorytmie klasy działa przez przypisanie a wolne działanie. Specjalizowanej wersji w każdym kontenerze jest znacznie szybsza, ponieważ może współpracować z reprezentacji wewnętrznej klasy kontenera.

### <a name="example"></a>Przykład

Zobacz przykład kodu dla funkcji członkowskiej [multimap::swap](../standard-library/multimap-class.md#swap) przykład, który używa szablonu wersji `swap`.

## <a name="see-also"></a>Zobacz także

[\<Mapa >](../standard-library/map.md)<br/>
