---
title: '&lt;&gt; funkcje hash_set'
ms.date: 11/04/2016
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: d7df6b3c5dc0d0d493d17b3e9995bc4758ffd6d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370583"
---
# <a name="lthash_setgt-functions"></a>&lt;&gt; funkcje hash_set

|||
|-|-|
|[Wymiany](#swap)|[swap (hash_multiset)](#swap_hash_multiset)|

## <a name="swap"></a><a name="swap"></a>Wymiany

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Wymienia elementy dwóch hash_sets.

```cpp
void swap(
    hash_set <Key, Traits, Allocator>& left,
    hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Hash_set dostarczenie elementów do wymiany, lub hash_set, których elementy mają być wymieniane z elementami hash_set *lewej*.

*Lewej*\
Hash_set, których elementy mają być wymieniane z elementami prawa *hash_set.*

### <a name="remarks"></a>Uwagi

Funkcja `swap` szablonu jest algorytmem wyspecjalizowanym w klasie kontenera `left.`hash_set`right`do wykonywania [zamiany](../standard-library/hash-set-class.md#swap)funkcji elementu członkowskiego ( ). Jest to wystąpienie częściowej kolejności szablonów funkcji przez kompilator. Gdy funkcje szablonu są przeciążone w taki sposób, że dopasowanie szablonu z wywołaniem funkcji nie jest unikatowe, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólna wersja funkcji szablonu

**klasa \<szablonu T> zamiana otężki (T&, T&),**

w klasie algorytmu działa według przypisania i jest powolna operacja. Wyspecjalizowana wersja w każdym kontenerze jest znacznie szybsza, ponieważ może pracować z wewnętrzną reprezentacją klasy kontenera.

### <a name="example"></a>Przykład

Zobacz przykład kodu dla klasy członkowskiej [hash_set::swap](../standard-library/hash-set-class.md#swap) na przykład, który `swap`używa wersji szablonu .

## <a name="swap-hash_multiset"></a><a name="swap_hash_multiset"></a>swap (hash_multiset)

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set Klasa](../standard-library/unordered-set-class.md).

Wymienia elementy dwóch hash_multisets.

```cpp
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
hash_multiset zapewniając elementy, które mają być zamienione, lub hash_multiset których elementy mają być wymieniane z elementami hash_multiset *lewej*.

*Lewej*\
Hash_multiset, których elementy mają być wymieniane z elementami prawa *hash_multiset.*

### <a name="remarks"></a>Uwagi

Funkcja `swap` szablonu jest algorytmem wyspecjalizowanym w klasie kontenera `left.`hash_multiset`right`do wykonywania [zamiany](../standard-library/hash-multiset-class.md#swap)funkcji elementu członkowskiego ( ). Jest to wystąpienie częściowej kolejności szablonów funkcji przez kompilator. Gdy funkcje szablonu są przeciążone w taki sposób, że dopasowanie szablonu z wywołaniem funkcji nie jest unikatowe, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólna wersja funkcji szablonu

**klasa \<szablonu T> zamiana otężki (T&, T&),**

w klasie algorytmu działa według przypisania i jest powolna operacja. Wyspecjalizowana wersja w każdym kontenerze jest znacznie szybsza, ponieważ może pracować z wewnętrzną reprezentacją klasy kontenera.

### <a name="example"></a>Przykład

Zobacz przykład kodu dla klasy członkowskiej [hash_multiset::swap](../standard-library/hash-multiset-class.md#swap) na przykład, który `swap`używa wersji szablonu .

## <a name="see-also"></a>Zobacz też

[<hash_set>](../standard-library/hash-set.md)
