---
title: '&lt;hash_set —&gt;'
ms.date: 11/04/2016
f1_keywords:
- <hash_set>
- std::<hash_set>
helpviewer_keywords:
- hash_set header
ms.assetid: 6b556967-c808-4869-9b4d-f9e030864435
ms.openlocfilehash: ba7716c1c84e8a74495a67f10a78eeaad2a6c3d7
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51517701"
---
# <a name="lthashsetgt"></a>&lt;hash_set —&gt;

> [!NOTE]
> Tego pliku nagłówkowego jest przestarzała. Alternatywą jest [< unordered_set >](../standard-library/unordered-set.md).

Definiuje hash_set klasy szablonu kontenera i hash_multiset i ich szablonów pomocniczych.

## <a name="syntax"></a>Składnia

```cpp
#include <hash_set>
```

## <a name="remarks"></a>Uwagi

### <a name="operators"></a>Operatory

|Hash_set — wersja|Hash_multiset — wersja|Opis|
|-----------------------|----------------------------|-----------------|
|[Operator! = (hash_set)](../standard-library/hash-set-operators.md#op_neq)|[Operator! = (hash_multiset)](../standard-library/hash-set-operators.md#op_neq)|Sprawdza, czy obiekt hash_set lub hash_multiset po lewej stronie operatora nie jest równy obiektowi hash_set lub hash_multiset po prawej stronie.|
|[Operator == (hash_set)](../standard-library/hash-set-operators.md#op_eq_eq)|[Operator == (hash_multiset)](../standard-library/hash-set-operators.md#op_eq_eq)|Sprawdza, czy obiekt hash_set lub hash_multiset po lewej stronie operatora jest równy obiektowi hash_set lub hash_multiset po prawej stronie.|

### <a name="specialized-template-functions"></a>Specialized Template — Funkcje

|Hash_set — wersja|Hash_multiset — wersja|Opis|
|-----------------------|----------------------------|-----------------|
|[swap (hash_set)](../standard-library/hash-set-functions.md#swap)|[swap (hash_multiset)](../standard-library/hash-set-functions.md#swap_hash_multiset)|Zamienia elementy z dwóch hash_sets lub hash_multisets.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[hash_compare, klasa](../standard-library/hash-compare-class.md)|Opisuje obiekt, który może służyć przez żaden z kontenerów asocjacyjnych wyznaczania wartości skrótu — hash_map hash_multimap, hash_set, lub hash_multiset — domyślnie `Traits` parametr obiektu do porządkowania i wyznaczania wartości skrótu elementy zawierają.|
|[hash_set, klasa](../standard-library/hash-set-class.md)|Używane do przechowywania i szybkiego pobierania danych z kolekcji, w której wartości zawartych elementów są unikatowe i służą jako wartości klucza.|
|[hash_multiset, klasa](../standard-library/hash-multiset-class.md)|Używane do przechowywania i szybkiego pobierania danych z kolekcji, w której wartości zawartych elementów są unikatowe i służą jako wartości klucza.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
