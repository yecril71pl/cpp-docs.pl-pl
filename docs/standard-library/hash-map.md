---
title: '&lt;hash_map&gt;'
ms.date: 01/18/2018
f1_keywords:
- <hash_map>
- std::<hash_map>
helpviewer_keywords:
- hash_map header
ms.openlocfilehash: 9e8d53e841c93c474d6f6b7da925c8f72f73a8a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561528"
---
# <a name="lthashmapgt"></a>&lt;hash_map&gt;

> [!NOTE]
> Tego pliku nagłówkowego jest przestarzała. Alternatywą jest [ \<unordered_map >](unordered-map.md).

Definiuje hash_map klasy szablonu kontenera i hash_multimap i ich szablonów pomocniczych.

## <a name="syntax"></a>Składnia

> #<a name="include-hashmap"></a>obejmują \<hash_map >

### <a name="operators"></a>Operatory

|Hash_map — wersja|Hash_multimap — wersja|Opis|
|-----------------------|----------------------------|-----------------|
|[operator!= (hash_map)](hash-map-operators.md#op_neq)|[operator!=(hash_multimap)](hash-map-operators.md#op_neq_mm)|Sprawdza, czy obiekt hash_map lub hash_multimap po lewej stronie operatora nie jest równy obiektowi hash_map lub hash_multimap po prawej stronie.|
|[operator== (hash_map)](hash-map-operators.md#op_eq_eq)|[operator== (hash_multimap)](hash-map-operators.md#op_eq_eq_mm)|Sprawdza, czy obiekt hash_map lub hash_multimap po lewej stronie operatora jest równy obiektowi hash_map lub hash_multimap po prawej stronie.|

### <a name="specialized-template-functions"></a>Specialized Template — Funkcje

|Hash_map — wersja|Hash_multimap — wersja|Opis|
|-----------------------|----------------------------|-----------------|
|[swap (hash_map)](hash-map-class.md#swap)|[swap (hash_multimap)](hash-multimap-class.md#swap)|Zamienia elementy z dwóch hash_maps lub hash_multimaps.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[hash_compare, klasa](hash-compare-class.md)|Opisuje obiekt, który może służyć przez żaden z kontenerów asocjacyjnych wyznaczania wartości skrótu — hash_map hash_multimap, hash_set, lub hash_multiset — domyślnie `Traits` parametr obiektu do porządkowania i wyznaczania wartości skrótu elementy zawierają.|
|[value_compare, klasa](value-compare-class.md)|Dostarcza obiekt funkcji, która może porównać elementów hash_map przez porównanie wartości ich klucze, aby określić ich względną kolejność w hash_map.|
|[hash_map, klasa](hash-map-class.md)|Używane do przechowywania i szybkie pobieranie danych z kolekcji, w której każdy element jest parą, która ma klucz sortowania, w której wartość jest unikatowa i skojarzone dane wartości.|
|[hash_multimap, klasa](hash-multimap-class.md)|Używane do przechowywania i szybkie pobieranie danych z kolekcji, w której każdy element jest parą, która ma klucz sortowania, którego wartość nie musi być unikatowa i skojarzone dane wartości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<hash_map >

**Namespace:** stdext

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](cpp-standard-library-reference.md)
