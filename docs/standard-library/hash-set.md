---
title: '&lt;hash_set —&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <hash_set>
- std::<hash_set>
dev_langs:
- C++
helpviewer_keywords:
- hash_set header
ms.assetid: 6b556967-c808-4869-9b4d-f9e030864435
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dccf608b9949ad9e1502b489a237adf60a4d50a6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845742"
---
# <a name="lthashsetgt"></a>&lt;hash_set —&gt;

> [!NOTE]
> Ten nagłówek jest przestarzała. Alternatywą jest [< unordered_set >](../standard-library/unordered-set.md).

Definiuje hash_set klasy szablonu kontenera i hash_multiset i ich obsługi szablonów.

## <a name="syntax"></a>Składnia

```cpp
#include <hash_set>

```

## <a name="remarks"></a>Uwagi

### <a name="operators"></a>Operatory

|Hash_set — wersja|Hash_multiset — wersja|Opis|
|-----------------------|----------------------------|-----------------|
|[Operator! = (hash_set)](../standard-library/hash-set-operators.md#op_neq)|[Operator! = (hash_multiset)](../standard-library/hash-set-operators.md#op_neq)|Testy, jeśli obiekt hash_set lub hash_multiset po lewej stronie operatora nie jest taki sam jak obiekt hash_set lub hash_multiset po prawej stronie.|
|[Operator == (hash_set)](../standard-library/hash-set-operators.md#op_eq_eq)|[Operator == (hash_multiset)](../standard-library/hash-set-operators.md#op_eq_eq)|Testy, jeśli obiekt hash_set lub hash_multiset po lewej stronie operatora jest taki sam jak obiekt hash_set lub hash_multiset po prawej stronie.|

### <a name="specialized-template-functions"></a>Specialized Template — Funkcje

|Hash_set — wersja|Hash_multiset — wersja|Opis|
|-----------------------|----------------------------|-----------------|
|[swap (hash_set)](../standard-library/hash-set-functions.md#swap)|[swap (hash_multiset)](../standard-library/hash-set-functions.md#swap_hash_multiset)|Zamienia elementy dwóch hash_sets lub hash_multisets.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[hash_compare, klasa](../standard-library/hash-compare-class.md)|Opisuje obiekt, który mogą być używane przez dowolny kontener asocjacyjna skrótu — hash_map hash_multimap, hash_set, lub hash_multiset — domyślnie **cech** obiektu parameter kolejność i wyznaczania wartości skrótu elementy zawierają.|
|[hash_set, klasa](../standard-library/hash-set-class.md)|Używany do przechowywania i szybkie pobieranie danych z kolekcji, w której wartości elementy zawarte są unikatowe i służyć jako wartości klucza.|
|[hash_multiset, klasa](../standard-library/hash-multiset-class.md)|Używany do przechowywania i szybkie pobieranie danych z kolekcji, w której wartości elementy zawarte są unikatowe i służyć jako wartości klucza.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
