---
title: '&lt;hash_map —&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
ms.openlocfilehash: 12ceb799ccf0944b8f0e8d48975da25c39f22505
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100953"
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

*right*<br/>
Hash_map, której elementy są wymieniane z tymi mapy *po lewej stronie*.

*left*<br/>
Hash_map, której elementy są wymieniane z tymi mapy *prawo*.

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

*right*<br/>
Hash_multimap, której elementy są wymieniane z tymi mapy *po lewej stronie*.

*left*<br/>
Hash_multimap, której elementy są wymieniane z tymi mapy *prawo*.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm przeznaczone na hash_multimap — klasa kontenera na wykonanie funkcji elementu członkowskiego `left.` [wymiany](../standard-library/hash-multimap-class.md#swap)*(prawy*`)`. To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonu przeciążone są w sposób dopasowania szablonu za pomocą wywołania funkcji nie jest unikatowa, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólne wersję funkcji szablonu **szablonu \<klasa T > void swap (T &, T &)**, w algorytmie plik nagłówkowy działa przez przypisanie a wolne działanie. Specjalizowanej wersji w każdym kontenerze jest znacznie szybsza, ponieważ może współpracować z reprezentacji wewnętrznej klasy kontenera.

## <a name="see-also"></a>Zobacz także

[<hash_map>](../standard-library/hash-map.md)<br/>
