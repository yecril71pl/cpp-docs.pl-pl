---
title: Funkcja obiektów w standardowej bibliotece C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- functors
- C++ Standard Library, functors
- C++ Standard Library, function objects
- function objects
ms.assetid: 85f8a735-2c7b-4f10-9c4d-95c666ec4192
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09123f4b8d0200d133ae04244d38b615640f7d30
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964930"
---
# <a name="function-objects-in-the-c-standard-library"></a>Obiekty funkcji w standardowej bibliotece C++

A *obiektu funkcyjnego*, lub *funktor*, jest dowolny typ, który implementuje operator(). Ten operator jest określany jako *operator wywołania* lub czasami *operatora aplikacji*. Standardowa biblioteka C++ używa obiektów funkcyjnych, przede wszystkim jako kryteria dla kontenerów i algorytmów sortowania.

Obiekty funkcyjne zapewniają dwie główne korzyści wywoływanej funkcji proste. Pierwsza to, że obiekt funkcji może zawierać stanu. Drugim jest, że obiektu funkcyjnego jest typem i dlatego może służyć jako parametr szablonu.

## <a name="creating-a-function-object"></a>Tworzenie obiektu — funkcja

Aby utworzyć obiekt funkcji, Utwórz typ i zaimplementować operator(), takich jak:

```cpp
class Functor
{
public:
    int operator()(int a, int b)
    {
        return a < b;
    }
};
```

Ostatni wiersz `main` funkcji pokazuje, jak wywołać obiekt funkcji. Tego wywołania wygląda wywołanie do funkcji, ale faktycznie dzwoni operator() typu Funktor. Podobieństwo wywołanie obiektu funkcji i funkcji jest jak obiekt funkcji, który termin dostarczone.

## <a name="function-objects-and-containers"></a>Funkcja obiektów i kontenerów

Standardowa biblioteka C++ zawiera kilka obiektów funkcyjnych w [ \<funkcjonalności >](../standard-library/functional.md) pliku nagłówka. Jest jednym z tych obiektów funkcyjnych zastosowań jako kryterium sortowania dla kontenerów. Na przykład `set` kontenera jest zadeklarowana w następujący sposób:

```cpp
template <class Key,
    class Traits=less<Key>,
    class Allocator=allocator<Key>>
class set
```

Typ drugiego argumentu szablonu jest obiektem funkcji `less`. Ta funkcja zwraca **true** czy pierwszy parametr przekazany do jest mniejszy niż drugi parametr przekazany. Ponieważ niektóre kontenery sortowanie swoich elementów, kontener musi sposób porównywania dwóch elementów, a jest to realizowane przy użyciu obiektu funkcji. Można zdefiniować własne sortowanie kryteria dla kontenerów, tworząc obiekt funkcji, a następnie określając jej na liście szablonów dla kontenera.

## <a name="function-objects-and-algorithms"></a>Obiekty funkcji i algorytmy

Innym zastosowaniem obiektów funkcjonalności jest algorytmów. Na przykład `remove_if` algorytm jest zadeklarowana w następujący sposób:

```cpp
template <class ForwardIterator, class Predicate>
ForwardIterator remove_if(
    ForwardIterator first,
    ForwardIterator last,
    Predicate pred);
```

Ostatni argument `remove_if` jest obiektem funkcji, która zwraca wartość logiczną ( *predykatu*). Jeśli wynik obiekt funkcji, który jest **true**, a następnie element zostanie usunięty z kontenera, w której uzyskuje dostęp przez Iteratory `first` i `last`. Można użyć dowolnego z obiektów funkcyjnych, zadeklarowany w [ \<funkcjonalności >](../standard-library/functional.md) nagłówka dla argumentu `pred` lub możesz utworzyć swój własny.

## <a name="see-also"></a>Zobacz także

[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
