---
title: hash_compare — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- hash_set/stdext::hash_compare
dev_langs:
- C++
helpviewer_keywords:
- hash_compare class
ms.assetid: d502bb59-de57-4585-beb9-00e3a998c0af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb1e42bf61c1fa70ee74063cd6857d842ee87de7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="hashcompare-class"></a>hash_compare — Klasa

Obiekt, który mogą być używane przez dowolny kontener asocjacyjna skrótu opisano klasy szablonu — hash_map hash_multimap, hash_set, lub hash_multiset — domyślnie **cech** obiektu parameter kolejność i wyznaczania wartości skrótu elementy zawierają .

## <a name="syntax"></a>Składnia

hash_compare — klasa {komp cech; public: const size_t bucket_size = 4; const size_t min_buckets = 8; hash_compare(); hash_compare — (cech pred) size_t operator() (const klucza & klucz) const; bool operator() (const klucza & klucz1, klucz const & klucz2) const;};

## <a name="remarks"></a>Uwagi

Każdego kontenera asocjacyjna skrótu przechowuje obiektu skrótu cech typu **cech** (parametr szablonu). Klasy mogą dziedziczyć po specjalizacja hash_compare — Aby selektywnie zastąpić pewne funkcje i obiekty, lub możesz podać własne wersja tej klasy, które spełniają określone wymagania minimalne. W szczególności dla obiekt hash_comp typu **hash_compare —\<klawisz, cechy >**, następujące działania jest wymagany przez kontenery powyżej:

- Dla wszystkich wartości `key` typu **klucza**, wywołanie **hash_comp**( `key`) służy jako funkcji wyznaczania wartości skrótu, która daje w wyniku podziału wartości typu **size_t**. Funkcja dostarczonych przez hash_compare — zwraca `key`.

- Dla dowolnej wartości `key1` typu **klucza** czy poprzedza `key2` w sekwencji i ma tę samą wartość (wartość zwrócona przez funkcję skrótu), skrótu **hash_comp**( `key2`, `key1`) ma wartość false. Funkcja musi nałożyć łącznie porządkowanie dla wartości typu **klucza**. Funkcja dostarczonych przez hash_compare — zwraca *kompozycji*( `key2`, `key1`) `,` gdzie *kompozycji* jest przechowywane obiektu typu **cech** który można określić podczas tworzenia obiektu hash_comp. Dla domyślnej **cech** typ parametru **mniej\<klucza >**, klucze sortowania nigdy nie spadek wartości.

- Stała całkowita **bucket_size** określa średnia liczba elementów na "zasobnika" (wpis tablicy skrótów) który kontenera nie należy próbować przekracza. Musi być większa niż zero. Wartość dostarczona przez hash_compare — to 4.

- Stała całkowita **min_buckets** określa minimalną liczbę zasobników, aby zachować w tablicy skrótów. Musi być potęgą liczby dwa i większa od zera. Wartość dostarczona przez hash_compare — jest 8.

## <a name="example"></a>Przykład

Przykłady dla [hash_map::hash_map](../standard-library/hash-map-class.md#hash_map), [hash_multimap::hash_multimap](../standard-library/hash-multimap-class.md#hash_multimap), [hash_set::hash_set](../standard-library/hash-set-class.md#hash_set), i [hash_multiset::hash_multiset](../standard-library/hash-multiset-class.md#hash_multiset), przykłady deklarowanie i użycie hash_compare —.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<hash_map >

**Namespace:** stdext —

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
