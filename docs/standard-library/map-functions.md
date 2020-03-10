---
title: '&lt;mapowanie funkcji&gt;'
ms.date: 11/04/2016
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
ms.openlocfilehash: e7876b37bfc006eaecf2f1e36273c5ae8689dad4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883966"
---
# <a name="ltmapgt-functions"></a>&lt;mapowanie funkcji&gt;

## <a name="swap_multimap"></a>Zamień (mapa)

Zamienia elementy z dwóch map.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    map<Key, Traits, Compare, Alloctor>& left,
    map<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Mapa dostarczająca elementy, które mają zostać zamienione, lub mapę, której elementy mają być wymieniane z *pozostałymi*elementami mapy.

\ *lewo*
Mapa, której elementy są wymieniane z *prawami*mapy.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm wyspecjalizowany dla mapy klasy kontenera, aby wykonać funkcję członkowską `left`. [Zamień](../standard-library/map-class.md#swap)(`right`). Jest to wystąpienie częściowego porządkowania szablonów funkcji przez kompilator. Gdy funkcje szablonu są przeciążone w taki sposób, że dopasowanie szablonu z wywołaniem funkcji nie jest unikatowe, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólna wersja funkcji szablonu, **szablonu** \< **Class t**> **void swap**( **t &** , **t &** ), w klasie algorytmu działa przez przypisanie i jest operacją powolne. Wyspecjalizowana wersja w każdym kontenerze jest znacznie szybsza, ponieważ może pracować z wewnętrzną reprezentacją klasy Container.

### <a name="example"></a>Przykład

Zobacz przykład kodu dla mapy funkcji składowej [:: swap](../standard-library/map-class.md#swap) dla przykładu korzystającego z wersji szablonu `swap`.

## <a name="swap"></a>swap (multimap)

Wymienia elementy dwóch map.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,
    multimap<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Multimap udostępniający elementy, które mają zostać zamienione, lub multimap, których elementy mają być wymieniane z *pozostałymi*multimap.

\ *lewo*
Multimap, których elementy mają być wymieniane z tymi z *prawej*strony multimap.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm wyspecjalizowany na mapie klasy kontenera do wykonania na klasie kontenera multimap, aby wykonać funkcję członkowską `left`. [Zamień](../standard-library/multimap-class.md#swap) (`right`). Jest to wystąpienie częściowego porządkowania szablonów funkcji przez kompilator. Gdy funkcje szablonu są przeciążone w taki sposób, że dopasowanie szablonu z wywołaniem funkcji nie jest unikatowe, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólna wersja funkcji szablonu, **szablonu** \< **Class t**> **void swap**( **t &** , **t &** ), w klasie algorytmu działa przez przypisanie i jest operacją powolne. Wyspecjalizowana wersja w każdym kontenerze jest znacznie szybsza, ponieważ może pracować z wewnętrzną reprezentacją klasy Container.

### <a name="example"></a>Przykład

Zobacz przykład kodu dla funkcji składowej [multimap:: swap](../standard-library/multimap-class.md#swap) dla przykładu korzystającego z wersji szablonu `swap`.
