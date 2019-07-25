---
title: '&lt;hash_map&gt;'
ms.date: 01/18/2018
f1_keywords:
- <hash_map>
- std::<hash_map>
helpviewer_keywords:
- hash_map header
ms.openlocfilehash: cca38386892ce4df6bf9863e0cbac3dc16106d35
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448665"
---
# <a name="lthashmapgt"></a>&lt;hash_map&gt;

> [!NOTE]
> Ten nagłówek jest przestarzały. Alternatywą jest [ \<unordered_map >](unordered-map.md).

Definiuje klasy szablonu kontenera hash_map i hash_multimap oraz ich szablony pomocnicze.

## <a name="syntax"></a>Składnia

```
#include <hash_map>
```

### <a name="operators"></a>Operatory

|Wersja hash_map|Wersja hash_multimap|Opis|
|-----------------------|----------------------------|-----------------|
|[operator!= (hash_map)](hash-map-operators.md#op_neq)|[operator!=(hash_multimap)](hash-map-operators.md#op_neq_mm)|Testuje, czy obiekt hash_map lub hash_multimap po lewej stronie operatora nie jest równy obiektowi hash_map lub hash_multimap po prawej stronie.|
|[operator== (hash_map)](hash-map-operators.md#op_eq_eq)|[operator== (hash_multimap)](hash-map-operators.md#op_eq_eq_mm)|Testuje, czy obiekt hash_map lub hash_multimap po lewej stronie operatora jest równy obiektowi hash_map lub hash_multimap po prawej stronie.|

### <a name="specialized-template-functions"></a>Specialized Template — Funkcje

|Wersja hash_map|Wersja hash_multimap|Opis|
|-----------------------|----------------------------|-----------------|
|[swap (hash_map)](hash-map-class.md#swap)|[swap (hash_multimap)](hash-multimap-class.md#swap)|Wymienia elementy dwóch hash_maps lub hash_multimaps.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[hash_compare, klasa](hash-compare-class.md)|Opisuje obiekt, który może być używany przez dowolny kontener asocjacyjnych skrótów — hash_map, hash_multimap, hash_set lub hash_multiset — jako domyślny `Traits` obiekt parametru do porządkowania i mieszania elementów, które zawierają.|
|[value_compare, klasa](value-compare-class.md)|Udostępnia obiekt funkcji, który może porównać elementy hash_map przez porównanie wartości ich kluczy w celu określenia ich względnej kolejności w hash_map.|
|[hash_map, klasa](hash-map-class.md)|Służy do przechowywania i szybkiego pobierania danych z kolekcji, w której każdy element jest parą, która ma klucz sortowania, którego wartość jest unikatowa i skojarzona wartość danych.|
|[hash_multimap, klasa](hash-multimap-class.md)|Używany do przechowywania i szybkiego pobierania danych z kolekcji, w której każdy element jest parą, która ma klucz sortowania, którego wartość nie musi być unikatowa i skojarzona z nią wartość danych.|

## <a name="requirements"></a>Wymagania

**Header:** \<hash_map>

**Przestrzeń nazw:** stdext

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki C++](cpp-standard-library-reference.md)
