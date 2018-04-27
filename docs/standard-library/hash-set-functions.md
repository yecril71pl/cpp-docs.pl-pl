---
title: '&lt;hash_set —&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
caps.latest.revision: 7
manager: ghogen
ms.openlocfilehash: d9dc03b6ea4e6ed90a6eda433faf6710b6982bb3
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="lthashsetgt-functions"></a>&lt;hash_set —&gt; funkcji

|||
|-|-|
|[swap](#swap)|[swap (hash_multiset)](#swap_hash_multiset)|

## <a name="swap"></a>  Swap

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).

Zamienia hash_sets dwa elementy.

```cpp
void swap(
    hash_set <Key, Traits, Allocator>& left,
    hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`right` Hash_set dostarczanie elementy zamianę lub hash_set, której elementy są wymienianych z tymi hash_set `left`.

`left` Hash_set —, której elementy są wymienianych z tymi hash_set `right`.

### <a name="remarks"></a>Uwagi

`swap` Funkcji szablonu jest algorytm specjalizowany na hash_set — klasa kontenera do wykonywania funkcji członkowskiej `left.` [wymiany](../standard-library/hash-set-class.md#swap)( `right`). To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonów są przeciążone w taki sposób, dopasowania szablonu z wywołaniem funkcji nie jest unikatowa, kompilator wybierze najbardziej specjalna wersja funkcji szablonu. Ogólne wersji szablonu funkcji

**Szablon \<klasy T > wymiany void (T &, T &),**

w algorytmie klasa działa przez przypisanie i jest wolne działanie. Specjalna wersja w poszczególnych kontenerach jest znacznie szybsze może współpracować z reprezentacji wewnętrznej klasy kontenera.

### <a name="example"></a>Przykład

Zobacz przykład kodu dla elementu członkowskiego klasy [hash_set::swap](../standard-library/hash-set-class.md#swap) na przykład, który używa wersji szablonu `swap`.

## <a name="swap_hash_multiset"></a>  swap (hash_multiset)

> [!NOTE]
> Ten interfejs API jest nieaktualny. Alternatywą jest [unordered_set — klasa](../standard-library/unordered-set-class.md).

Zamienia hash_multisets dwa elementy.

```cpp
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`right` Hash_multiset dostarczanie elementy zamianę lub hash_multiset, której elementy są wymienianych z tymi hash_multiset `left`.

`left` Hash_multiset —, której elementy są wymienianych z tymi hash_multiset `right`.

### <a name="remarks"></a>Uwagi

`swap` Funkcji szablonu jest algorytm specjalizowany na hash_multiset — klasa kontenera do wykonywania funkcji członkowskiej `left.` [wymiany](../standard-library/hash-multiset-class.md#swap)( `right`). To wystąpienie częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonów są przeciążone w taki sposób, dopasowania szablonu z wywołaniem funkcji nie jest unikatowa, kompilator wybierze najbardziej specjalna wersja funkcji szablonu. Ogólne wersji szablonu funkcji

**Szablon \<klasy T > wymiany void (T &, T &),**

w algorytmie klasa działa przez przypisanie i jest wolne działanie. Specjalna wersja w poszczególnych kontenerach jest znacznie szybsze może współpracować z reprezentacji wewnętrznej klasy kontenera.

### <a name="example"></a>Przykład

Zobacz przykład kodu dla elementu członkowskiego klasy [hash_multiset::swap](../standard-library/hash-multiset-class.md#swap) na przykład, który używa wersji szablonu `swap`.

## <a name="see-also"></a>Zobacz także

[<hash_set>](../standard-library/hash-set.md)<br/>
