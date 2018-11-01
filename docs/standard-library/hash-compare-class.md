---
title: hash_compare — Klasa
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_compare
helpviewer_keywords:
- hash_compare class
ms.assetid: d502bb59-de57-4585-beb9-00e3a998c0af
ms.openlocfilehash: f535122b67f854b8b204664b829ce9da5fe3c6a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575789"
---
# <a name="hashcompare-class"></a>hash_compare — Klasa

Klasa szablonu opisuje obiekt, który może służyć przez żaden z kontenerów asocjacyjnych wyznaczania wartości skrótu — hash_map hash_multimap, hash_set, lub hash_multiset — domyślnie **cech** parametr obiektu do porządkowania i wyznaczania wartości skrótu elementy zawierają .

## <a name="syntax"></a>Składnia

hash_compare — klasa {comp cech; public: const size_t bucket_size — = 4; const size_t min_buckets = 8 hash_compare() hash_compare — (cechy pred); size_t operator() (const Key & klucza) const; bool operator() (const Key & klucz1, const Key & klucz2) const;};

## <a name="remarks"></a>Uwagi

Każdy kontener asocjacyjny wyznaczania wartości skrótu są przechowywane obiektu skrótu cech typu `Traits` (parametr szablonu). Klasy mogą dziedziczyć specjalizacja hash_compare — w celu selektywnego przesłaniania pewne funkcje i obiekty, lub możesz podać własną wersję tej klasy, które spełniają określone wymagania minimalne. W szczególności dla hash_comp obiektu typu `hash_compare<Key, Traits>`, następujące zachowanie jest wymagana przez powyższe kontenerów:

- Dla wszystkich wartości `key` typu `Key`, wywołanie **hash_comp**(`key`) służy jako funkcji wyznaczania wartości skrótu, która daje w wyniku rozkład wartości typu `size_t`. Funkcja dostarczonych przez hash_compare — zwraca `key`.

- Dla dowolnej wartości `key1` typu `Key` , który poprzedza `key2` w sekwencji i ma taką samą wartość (wartość zwrócona przez funkcję skrótu), skrótu **hash_comp**(`key2`, `key1`) ma wartość false. Funkcja musi nakładają łącznie porządkowanie dla wartości typu `Key`. Funkcja dostarczonych przez hash_compare — zwraca *comp*(`key2`, `key1`) `,` gdzie *comp* jest przechowywany obiekt typu `Traits` , możesz określić, kiedy użytkownik Skonstruuj hash_comp obiektu. Dla domyślnego `Traits` typ parametru `less<Key>`, klucze sortowania nigdy nie spadek wartości.

- Stała całkowita `bucket_size` określa średnią liczbę elementów na "zasobnik" (wpis w tabeli skrótów) kontenera nie należy próbować przekracza. Musi być większa od zera. Wartość dostarczona przez hash_compare — to 4.

- Stała całkowita `min_buckets` określa minimalną liczbę zasobników, aby zachować w tabeli wyznaczania wartości skrótu. Musi być potęgą liczby dwa i większa od zera. Wartość dostarczona przez hash_compare — jest 8.

## <a name="example"></a>Przykład

Zobacz przykłady dla [hash_map::hash_map](../standard-library/hash-map-class.md#hash_map), [hash_multimap::hash_multimap](../standard-library/hash-multimap-class.md#hash_multimap), [hash_set::hash_set](../standard-library/hash-set-class.md#hash_set), i [hash_multiset::hash_multiset](../standard-library/hash-multiset-class.md#hash_multiset), przykładów dotyczących sposobów na zadeklarowanie i użyj hash_compare —.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<hash_map >

**Namespace:** stdext

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
