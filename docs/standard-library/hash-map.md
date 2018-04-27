---
title: '&lt;hash_map —&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 01/18/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <hash_map>
- std::<hash_map>
dev_langs:
- C++
helpviewer_keywords:
- hash_map header
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 177afaca1ddad1145c9465dc6b71863c846b6b5c
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="lthashmapgt"></a>&lt;hash_map&gt;

> [!NOTE]
> Ten nagłówek jest przestarzała. Alternatywą jest [ \<unordered_map >](unordered-map.md).

Definiuje hash_map klasy szablonu kontenera i hash_multimap i ich obsługi szablonów.

## <a name="syntax"></a>Składnia

> #<a name="include-hashmap"></a>obejmują < hash_map >

### <a name="operators"></a>Operatory

|Hash_map — wersja|Hash_multimap — wersja|Opis|
|-----------------------|----------------------------|-----------------|
|[operator!= (hash_map)](hash-map-operators.md#op_neq)|[operator!=(hash_multimap)](hash-map-operators.md#op_neq_mm)|Testy, jeśli obiekt hash_map lub hash_multimap po lewej stronie operatora nie jest taki sam jak obiekt hash_map lub hash_multimap po prawej stronie.|
|[operator== (hash_map)](hash-map-operators.md#op_eq_eq)|[operator== (hash_multimap)](hash-map-operators.md#op_eq_eq_mm)|Testy, jeśli obiekt hash_map lub hash_multimap po lewej stronie operatora jest taki sam jak obiekt hash_map lub hash_multimap po prawej stronie.|

### <a name="specialized-template-functions"></a>Specialized Template — Funkcje

|Hash_map — wersja|Hash_multimap — wersja|Opis|
|-----------------------|----------------------------|-----------------|
|[swap (hash_map)](hash-map-class.md#swap)|[swap (hash_multimap)](hash-multimap-class.md#swap)|Zamienia elementy dwóch hash_maps lub hash_multimaps.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[hash_compare, klasa](hash-compare-class.md)|Opisuje obiekt, który mogą być używane przez dowolny kontener asocjacyjna skrótu — hash_map hash_multimap, hash_set, lub hash_multiset — domyślnie **cech** obiektu parameter kolejność i wyznaczania wartości skrótu elementy zawierają.|
|[value_compare, klasa](value-compare-class.md)|Udostępnia obiekt funkcji, który można porównać elementów hash_map porównując wartości ich kluczy, aby określić ich kolejność względne w hash_map.|
|[hash_map, klasa](hash-map-class.md)|Używany do przechowywania i szybkie pobieranie danych z kolekcji, w którym każdy element jest parę klucza sortowania, którego wartość jest unikatowa i skojarzone dane wartości.|
|[hash_multimap, klasa](hash-multimap-class.md)|Używany do przechowywania i szybkie pobieranie danych z kolekcji, w którym każdy element jest parę klucza sortowania, którego wartość nie musi być unikatowa i skojarzone dane wartości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<hash_map >

**Namespace:** stdext —

## <a name="see-also"></a>Zobacz także

[Pliki nagłówkowe odwołanie](cpp-standard-library-header-files.md)
[bezpieczeństwo wątku w standardowej bibliotece C++](thread-safety-in-the-cpp-standard-library.md)
[odwołanie do biblioteki C++ Standard](cpp-standard-library-reference.md)
