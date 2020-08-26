---
title: '&lt;&gt;funkcje hash_map'
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
ms.openlocfilehash: a29254d32954556ad3a2fbedb89fb3556533ff1f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841197"
---
# <a name="lthash_mapgt-functions"></a>&lt;&gt;funkcje hash_map

[wymiany](#swap)\
[Zamień (hash_map)](#swap_hash_map)

## <a name="swap-hash_map"></a><a name="swap_hash_map"></a> Zamień (hash_map)

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_map](../standard-library/unordered-map-class.md).

Wymienia elementy dwóch hash_maps.

```cpp
void swap(
    hash_map <Key, Type, Traits, Alloctor>& left,
    hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Hash_map, których elementy mają być wymieniane z *pozostałymi*elementami na mapie.

*lewym*\
Hash_map, których elementy mają być wymieniane z *prawami*mapy.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytmem wyspecjalizowanym dla klasy kontenera hash_map do wykonywania operacji swap funkcji składowej `left.` [swap](../standard-library/basic-ios-class.md#swap)*(prawo*). Jest to wystąpienie częściowego porządkowania szablonów funkcji przez kompilator. Gdy funkcje szablonu są przeciążone w taki sposób, że dopasowanie szablonu z wywołaniem funkcji nie jest unikatowe, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólna wersja funkcji szablonu, **szablonu \<class T> void swap (t&, t&)** w pliku nagłówka algorytmu działa przez przypisanie i jest operacją powolnej. Wyspecjalizowana wersja w każdym kontenerze jest znacznie szybsza, ponieważ może pracować z wewnętrzną reprezentacją klasy Container.

## <a name="swap"></a><a name="swap"></a> wymiany

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [klasa unordered_multimap](../standard-library/unordered-multimap-class.md).

Wymienia elementy dwóch hash_multimaps.

```cpp
void swap(
    hash_multimap <Key, Type, Traits, Alloctor>& left,
    hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Hash_multimap, których elementy mają być wymieniane z *pozostałymi*elementami na mapie.

*lewym*\
Hash_multimap, których elementy mają być wymieniane z *prawami*mapy.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytmem wyspecjalizowanym dla klasy kontenera hash_multimap do wykonywania operacji swap funkcji składowej `left.` [swap](../standard-library/hash-multimap-class.md#swap)*(prawo* `)` . Jest to wystąpienie częściowego porządkowania szablonów funkcji przez kompilator. Gdy funkcje szablonu są przeciążone w taki sposób, że dopasowanie szablonu z wywołaniem funkcji nie jest unikatowe, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólna wersja funkcji szablonu, **szablonu \<class T> void swap (t&, t&)** w pliku nagłówka algorytmu działa przez przypisanie i jest operacją powolnej. Wyspecjalizowana wersja w każdym kontenerze jest znacznie szybsza, ponieważ może pracować z wewnętrzną reprezentacją klasy Container.

## <a name="see-also"></a>Zobacz też

[<hash_map>](../standard-library/hash-map.md)
