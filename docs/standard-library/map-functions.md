---
title: '&lt;Mapa&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
caps.latest.revision: 6
manager: ghogen
ms.openlocfilehash: 6a83feab5c477f222dc192c1c916e5cbb93e637d
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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

`right` Mapy, zapewniając elementy zamianę lub mapy, której elementy są wymienianych z tymi mapy `left`.

`left` Mapy, której elementy są wymienianych z tymi mapy `right`.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm specjalizowany na mapie klasy kontenera do wykonywania funkcji członkowskiej `left`.[ wymiany](../standard-library/map-class.md#swap)( `right`). To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonów są przeciążone w taki sposób, dopasowania szablonu z wywołaniem funkcji nie jest unikatowa, kompilator wybierze najbardziej specjalna wersja funkcji szablonu. Ogólne wersja funkcji szablonu **szablonu** \< **klasy T**> **void wymiany**( **T &**, **T &**), w algorytmie klasa działa przez przypisanie i jest wolne działanie. Specjalna wersja w poszczególnych kontenerach jest znacznie szybsze może współpracować z reprezentacji wewnętrznej klasy kontenera.

### <a name="example"></a>Przykład

Zobacz przykład kodu dla funkcji członkowskiej [map::swap](../standard-library/map-class.md#swap) na przykład, który używa wersji szablonu `swap`.

## <a name="swap"></a>  swap (multimap)

Zamienia multimaps dwa elementy.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,
    multimap<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Parametry

`right` Multimap dostarczanie elementy zamianę lub multimap, której elementy są wymienianych z tymi multimap `left`.

`left` Multimap, której elementy są wymienianych z tymi multimap `right`.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm specjalizowany na mapie klasy kontenera do wykonania na multimap klasy kontenera do wykonywania funkcji członkowskiej `left`.[ wymiany](../standard-library/multimap-class.md#swap) ( `right`). To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonów są przeciążone w taki sposób, dopasowania szablonu z wywołaniem funkcji nie jest unikatowa, kompilator wybierze najbardziej specjalna wersja funkcji szablonu. Ogólne wersja funkcji szablonu **szablonu** \< **klasy T**> **void wymiany**( **T &**, **T &**), w algorytmie klasa działa przez przypisanie i jest wolne działanie. Specjalna wersja w poszczególnych kontenerach jest znacznie szybsze może współpracować z reprezentacji wewnętrznej klasy kontenera.

### <a name="example"></a>Przykład

Zobacz przykład kodu dla funkcji członkowskiej [multimap::swap](../standard-library/multimap-class.md#swap) na przykład, który używa wersji szablonu `swap`.

## <a name="see-also"></a>Zobacz także

[\<Mapa >](../standard-library/map.md)<br/>
