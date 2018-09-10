---
title: '&lt;hash_set —&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: 5c96ac897d870e1f8dc153847797379b6720dc7b
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103249"
---
# <a name="lthashsetgt-functions"></a>&lt;hash_set —&gt; funkcji

|||
|-|-|
|[swap](#swap)|[swap (hash_multiset)](#swap_hash_multiset)|

## <a name="swap"></a>  swap

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Zamienia elementy z dwóch hash_sets.

```cpp
void swap(
    hash_set <Key, Traits, Allocator>& left,
    hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Hash_set — zawierająca elementy, które mają być zamienione lub hash_set, której elementy są wymieniane z tymi hash_set *po lewej stronie*.

*left*<br/>
Hash_set, której elementy są wymieniane z tymi hash_set *prawo*.

### <a name="remarks"></a>Uwagi

`swap` Funkcji szablonu jest algorytm przeznaczone na hash_set — klasa kontenera na wykonanie funkcji elementu członkowskiego `left.` [wymiany](../standard-library/hash-set-class.md#swap)(`right`). To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonu przeciążone są w sposób dopasowania szablonu za pomocą wywołania funkcji nie jest unikatowa, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólne wersję funkcji szablonu

**Szablon \<klasa T > void swap (T &, T &),**

w algorytmie klasa działa przez przypisanie i jest wolne działanie. Specjalizowanej wersji w każdym kontenerze jest znacznie szybsza, ponieważ może współpracować z reprezentacji wewnętrznej klasy kontenera.

### <a name="example"></a>Przykład

Zobacz przykład kodu klasy członkowskiej [hash_set::swap](../standard-library/hash-set-class.md#swap) przykład, który używa szablonu wersji `swap`.

## <a name="swap_hash_multiset"></a>  swap (hash_multiset)

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set, klasa](../standard-library/unordered-set-class.md).

Zamienia elementy z dwóch hash_multisets.

```cpp
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Hash_multiset — zawierająca elementy, które mają być zamienione lub hash_multiset, której elementy są wymieniane z tymi hash_multiset *po lewej stronie*.

*left*<br/>
Hash_multiset, której elementy są wymieniane z tymi hash_multiset *prawo*.

### <a name="remarks"></a>Uwagi

`swap` Funkcji szablonu jest algorytm przeznaczone na hash_multiset — klasa kontenera na wykonanie funkcji elementu członkowskiego `left.` [wymiany](../standard-library/hash-multiset-class.md#swap)(`right`). To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonu przeciążone są w sposób dopasowania szablonu za pomocą wywołania funkcji nie jest unikatowa, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólne wersję funkcji szablonu

**Szablon \<klasa T > void swap (T &, T &),**

w algorytmie klasa działa przez przypisanie i jest wolne działanie. Specjalizowanej wersji w każdym kontenerze jest znacznie szybsza, ponieważ może współpracować z reprezentacji wewnętrznej klasy kontenera.

### <a name="example"></a>Przykład

Zobacz przykład kodu klasy członkowskiej [hash_multiset::swap](../standard-library/hash-multiset-class.md#swap) przykład, który używa szablonu wersji `swap`.

## <a name="see-also"></a>Zobacz także

[<hash_set>](../standard-library/hash-set.md)<br/>
