---
title: '&lt;funkcje&gt; hash_set'
ms.date: 11/04/2016
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: 2fbc05c16ba6629397bbb07bab30cb9315a16e1f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448594"
---
# <a name="lthashsetgt-functions"></a>&lt;funkcje&gt; hash_set

|||
|-|-|
|[swap](#swap)|[swap (hash_multiset)](#swap_hash_multiset)|

## <a name="swap"></a>wymiany

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_set](../standard-library/unordered-set-class.md).

Wymienia elementy dwóch hash_sets.

```cpp
void swap(
    hash_set <Key, Traits, Allocator>& left,
    hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Hash_set udostępniający elementy, które mają zostać zamienione, lub hash_set, których elementy mają być wymieniane z pozostałymi hash_set .

*lewym*\
Hash_set, których elementy mają być wymieniane z tymi z *prawej*strony hash_set.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm wyspecjalizowany dla klasy kontenera hash_set do wykonywania `left.`operacji [swap](../standard-library/hash-set-class.md#swap)funkcji składowej (`right`). `swap` Jest to wystąpienie częściowego porządkowania szablonów funkcji przez kompilator. Gdy funkcje szablonu są przeciążone w taki sposób, że dopasowanie szablonu z wywołaniem funkcji nie jest unikatowe, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólna wersja funkcji szablonu

**szablon \<klasy T > void swap (t &, t &),**

w klasie algorytmu działa przez przypisanie i jest operacją powolnej. Wyspecjalizowana wersja w każdym kontenerze jest znacznie szybsza, ponieważ może pracować z wewnętrzną reprezentacją klasy Container.

### <a name="example"></a>Przykład

Zobacz przykład kodu dla klasy składowej [hash_set:: swap](../standard-library/hash-set-class.md#swap) dla przykładu korzystającego z wersji `swap`szablonu.

## <a name="swap_hash_multiset"></a>swap (hash_multiset)

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [Klasa unordered_set](../standard-library/unordered-set-class.md).

Wymienia elementy dwóch hash_multisets.

```cpp
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Hash_multiset udostępniający elementy, które mają zostać zamienione, lub hash_multiset, których elementy mają być wymieniane z pozostałymi hash_multiset .

*lewym*\
Hash_multiset, których elementy mają być wymieniane z tymi z *prawej*strony hash_multiset.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm wyspecjalizowany dla klasy kontenera hash_multiset do wykonywania `left.`operacji [swap](../standard-library/hash-multiset-class.md#swap)funkcji składowej (`right`). `swap` Jest to wystąpienie częściowego porządkowania szablonów funkcji przez kompilator. Gdy funkcje szablonu są przeciążone w taki sposób, że dopasowanie szablonu z wywołaniem funkcji nie jest unikatowe, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólna wersja funkcji szablonu

**szablon \<klasy T > void swap (t &, t &),**

w klasie algorytmu działa przez przypisanie i jest operacją powolnej. Wyspecjalizowana wersja w każdym kontenerze jest znacznie szybsza, ponieważ może pracować z wewnętrzną reprezentacją klasy Container.

### <a name="example"></a>Przykład

Zobacz przykład kodu dla klasy składowej [hash_multiset:: swap](../standard-library/hash-multiset-class.md#swap) dla przykładu korzystającego z wersji `swap`szablonu.

## <a name="see-also"></a>Zobacz także

[<hash_set>](../standard-library/hash-set.md)
