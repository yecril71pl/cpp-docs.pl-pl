---
title: '&lt;hash_set —&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: 083d928198d8d83d8a56d8a74a6204e94c86aa67
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846288"
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
