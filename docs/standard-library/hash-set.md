---
title: '&lt;hash_set &gt;'
ms.date: 11/04/2016
f1_keywords:
- <hash_set>
- std::<hash_set>
helpviewer_keywords:
- hash_set header
ms.assetid: 6b556967-c808-4869-9b4d-f9e030864435
ms.openlocfilehash: 00ca476816213d38b3c50c64e0978e65ac1a5ea1
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687946"
---
# <a name="lthash_setgt"></a>&lt;hash_set &gt;

> [!NOTE]
> Ten nagłówek jest przestarzały. Alternatywą jest [< unordered_set >](../standard-library/unordered-set.md).

Definiuje szablony klas kontenerów hash_set i hash_multiset oraz ich szablony pomocnicze.

## <a name="syntax"></a>Składnia

```cpp
#include <hash_set>
```

## <a name="remarks"></a>Uwagi

### <a name="operators"></a>Operatory

|Wersja hash_set|Wersja hash_multiset|Opis|
|-----------------------|----------------------------|-----------------|
|[operator! = (hash_set)](../standard-library/hash-set-operators.md#op_neq)|[operator! = (hash_multiset)](../standard-library/hash-set-operators.md#op_neq)|Testuje, czy obiekt hash_set lub hash_multiset po lewej stronie operatora nie jest równy obiektowi hash_set lub hash_multiset po prawej stronie.|
|[operator = = (hash_set)](../standard-library/hash-set-operators.md#op_eq_eq)|[operator = = (hash_multiset)](../standard-library/hash-set-operators.md#op_eq_eq)|Testuje, czy obiekt hash_set lub hash_multiset po lewej stronie operatora jest równy obiektowi hash_set lub hash_multiset po prawej stronie.|

### <a name="specialized-template-functions"></a>Specialized Template — Funkcje

|Wersja hash_set|Wersja hash_multiset|Opis|
|-----------------------|----------------------------|-----------------|
|[swap (hash_set)](../standard-library/hash-set-functions.md#swap)|[swap (hash_multiset)](../standard-library/hash-set-functions.md#swap_hash_multiset)|Wymienia elementy dwóch hash_sets lub hash_multisets.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[hash_compare, klasa](../standard-library/hash-compare-class.md)|Opisuje obiekt, który może być używany przez dowolny ze skrótów kontenerów asocjacyjnych — hash_map, hash_multimap, hash_set lub hash_multiset — jako domyślny obiekt parametru `Traits`, aby zamówić i skrócić elementy, które zawierają.|
|[hash_set, klasa](../standard-library/hash-set-class.md)|Służy do przechowywania i szybkiego pobierania danych z kolekcji, w której wartości zawartych elementów są unikatowe i służą jako wartości klucza.|
|[hash_multiset, klasa](../standard-library/hash-multiset-class.md)|Służy do przechowywania i szybkiego pobierania danych z kolekcji, w której wartości zawartych elementów są unikatowe i służą jako wartości klucza.|

## <a name="see-also"></a>Zobacz także

[Odwołania do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md) \
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
