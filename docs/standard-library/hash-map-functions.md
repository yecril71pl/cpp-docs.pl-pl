---
title: '&lt;funkcje&gt; hash_map'
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
ms.openlocfilehash: efaa960d91c69d2157896adb4612c5dd36f00cff
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448745"
---
# <a name="lthashmapgt-functions"></a>&lt;funkcje&gt; hash_map

|||
|-|-|
|[swap](#swap)|[swap (hash_map)](#swap_hash_map)|

## <a name="swap_hash_map"></a>swap (hash_map)

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_map](../standard-library/unordered-map-class.md).

Wymienia elementy dwóch hash_maps.

```cpp
void swap(
    hash_map <Key, Type, Traits, Alloctor>& left,
    hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Hash_map, których elementy mają być wymieniane z pozostałymi elementami na mapie.

*lewym*\
Hash_map, których elementy mają być wymieniane z *prawami*mapy.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm wyspecjalizowany dla klasy kontenera hash_map do wykonywania operacji `left.` [swap](../standard-library/basic-ios-class.md#swap)funkcji składowej *(prawo*). Jest to wystąpienie częściowego porządkowania szablonów funkcji przez kompilator. Gdy funkcje szablonu są przeciążone w taki sposób, że dopasowanie szablonu z wywołaniem funkcji nie jest unikatowe, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólna wersja funkcji szablonu, **Klasa \<szablonu T > void swap (t &, t &)** w pliku nagłówka algorytmu działa przez przypisanie i jest operacją powolne. Wyspecjalizowana wersja w każdym kontenerze jest znacznie szybsza, ponieważ może pracować z wewnętrzną reprezentacją klasy Container.

## <a name="swap"></a>wymiany

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Wymienia elementy dwóch hash_multimaps.

```cpp
void swap(
    hash_multimap <Key, Type, Traits, Alloctor>& left,
    hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Hash_multimap, których elementy mają być wymieniane z pozostałymi elementami na mapie.

*lewym*\
Hash_multimap, których elementy mają być wymieniane z *prawami*mapy.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytmem wyspecjalizowanym dla `left.`klasy kontenera hash_multimap do wykonywania operacji [swap](../standard-library/hash-multimap-class.md#swap)funkcji składowej *(prawo*`)`. Jest to wystąpienie częściowego porządkowania szablonów funkcji przez kompilator. Gdy funkcje szablonu są przeciążone w taki sposób, że dopasowanie szablonu z wywołaniem funkcji nie jest unikatowe, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólna wersja funkcji szablonu, **Klasa \<szablonu T > void swap (t &, t &)** w pliku nagłówka algorytmu działa przez przypisanie i jest operacją powolne. Wyspecjalizowana wersja w każdym kontenerze jest znacznie szybsza, ponieważ może pracować z wewnętrzną reprezentacją klasy Container.

## <a name="see-also"></a>Zobacz także

[<hash_map>](../standard-library/hash-map.md)
