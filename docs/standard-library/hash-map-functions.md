---
title: '&lt;hash_map —&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
ms.openlocfilehash: d8ae3102091b9057f45f6b0072e0c272dfb27458
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958556"
---
# <a name="lthashmapgt-functions"></a>&lt;hash_map —&gt; funkcji

|||
|-|-|
|[swap](#swap)|[swap (hash_map)](#swap_hash_map)|

## <a name="swap_hash_map"></a>  swap (hash_map)

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map, klasa](../standard-library/unordered-map-class.md).

Zamienia elementy z dwóch hash_maps.

```cpp
void swap(
    hash_map <Key, Type, Traits, Alloctor>& left,
    hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*prawy* hash_map, której elementy są wymieniane z tymi mapy *po lewej stronie*.

*po lewej stronie* hash_map, której elementy są wymieniane z tymi mapy *prawo*.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm przeznaczone na hash_map — klasa kontenera na wykonanie funkcji elementu członkowskiego `left.` [wymiany](../standard-library/basic-ios-class.md#swap)*(prawy*). To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonu przeciążone są w sposób dopasowania szablonu za pomocą wywołania funkcji nie jest unikatowa, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólne wersję funkcji szablonu **szablonu \<klasa T > void swap (T &, T &)**, w algorytmie plik nagłówkowy działa przez przypisanie a wolne działanie. Specjalizowanej wersji w każdym kontenerze jest znacznie szybsza, ponieważ może współpracować z reprezentacji wewnętrznej klasy kontenera.

## <a name="swap"></a>  swap

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md).

Zamienia elementy z dwóch hash_multimaps.

```cpp
void swap(
    hash_multimap <Key, Type, Traits, Alloctor>& left,
    hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*prawy* hash_multimap, której elementy są wymieniane z tymi mapy *po lewej stronie*.

*po lewej stronie* hash_multimap, której elementy są wymieniane z tymi mapy *prawo*.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm przeznaczone na hash_multimap — klasa kontenera na wykonanie funkcji elementu członkowskiego `left.` [wymiany](../standard-library/hash-multimap-class.md#swap)*(prawy*`)`. To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonu przeciążone są w sposób dopasowania szablonu za pomocą wywołania funkcji nie jest unikatowa, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólne wersję funkcji szablonu **szablonu \<klasa T > void swap (T &, T &)**, w algorytmie plik nagłówkowy działa przez przypisanie a wolne działanie. Specjalizowanej wersji w każdym kontenerze jest znacznie szybsza, ponieważ może współpracować z reprezentacji wewnętrznej klasy kontenera.

## <a name="see-also"></a>Zobacz także

[<hash_map>](../standard-library/hash-map.md)<br/>
