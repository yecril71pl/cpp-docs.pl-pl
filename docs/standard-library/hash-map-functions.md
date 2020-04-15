---
title: '&lt;&gt; funkcje hash_map'
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
ms.openlocfilehash: 7cb2e46f19bd30e3eb313cde867c6a055cb8bca5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370616"
---
# <a name="lthash_mapgt-functions"></a>&lt;&gt; funkcje hash_map

|||
|-|-|
|[Wymiany](#swap)|[swap (hash_map)](#swap_hash_map)|

## <a name="swap-hash_map"></a><a name="swap_hash_map"></a>swap (hash_map)

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_map Klasa](../standard-library/unordered-map-class.md).

Wymienia elementy dwóch hash_maps.

```cpp
void swap(
    hash_map <Key, Type, Traits, Alloctor>& left,
    hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Hash_map, których elementy mają być wymieniane z elementami mapy *w lewo*.

*Lewej*\
Hash_map których elementy mają być wymieniane z elementami *mapy po prawej stronie.*

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytmem specjalizującym się w klasie `left.`kontenera hash_map do wykonywania [zamiany](../standard-library/basic-ios-class.md#swap)funkcji elementu członkowskiego *(po prawej).* Jest to wystąpienie częściowej kolejności szablonów funkcji przez kompilator. Gdy funkcje szablonu są przeciążone w taki sposób, że dopasowanie szablonu z wywołaniem funkcji nie jest unikatowe, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólna wersja funkcji szablonu, **klasy szablonu \<T> void swap(T&, T&)**, w pliku nagłówka algorytmu działa według przypisania i jest powolną operacją. Wyspecjalizowana wersja w każdym kontenerze jest znacznie szybsza, ponieważ może pracować z wewnętrzną reprezentacją klasy kontenera.

## <a name="swap"></a><a name="swap"></a>Wymiany

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_multimap Klasa](../standard-library/unordered-multimap-class.md).

Wymienia elementy dwóch hash_multimaps.

```cpp
void swap(
    hash_multimap <Key, Type, Traits, Alloctor>& left,
    hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Hash_multimap których elementy mają być wymieniane z elementami mapy *w lewo*.

*Lewej*\
Hash_multimap których elementy mają być wymieniane z elementami *mapy po prawej stronie.*

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytmem specjalizującym się w klasie kontenera hash_multimap do wykonywania `left.` [zamiany](../standard-library/hash-multimap-class.md#swap)funkcji elementu członkowskiego *(po prawej*`)`. Jest to wystąpienie częściowej kolejności szablonów funkcji przez kompilator. Gdy funkcje szablonu są przeciążone w taki sposób, że dopasowanie szablonu z wywołaniem funkcji nie jest unikatowe, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólna wersja funkcji szablonu, **klasy szablonu \<T> void swap(T&, T&)**, w pliku nagłówka algorytmu działa według przypisania i jest powolną operacją. Wyspecjalizowana wersja w każdym kontenerze jest znacznie szybsza, ponieważ może pracować z wewnętrzną reprezentacją klasy kontenera.

## <a name="see-also"></a>Zobacz też

[<hash_map>](../standard-library/hash-map.md)
