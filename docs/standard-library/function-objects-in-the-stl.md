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
ms.openlocfilehash: aa2694e9f5bb477447d08ab976cac60634ef3b60
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="function-objects-in-the-c-standard-library"></a>Obiekty funkcji w standardowej bibliotece C++

A *obiekt funkcji*, lub *obiekt*, jest dowolnego typu, który implementuje operator(). Ten operator jest określany jako *operator wywołania* lub czasami *operatora aplikacji*. Standardowa biblioteka C++ używa funkcji obiektów głównie jako kryteria dla kontenerów i algorytmy sortowania.

Obiekty funkcji Podaj dwie główne zalety wywoływanej funkcji proste. Pierwsza to, że obiekt funkcji może zawierać stanu. Drugim jest obiektem funkcji jest typem oraz mogą być używane jako parametr szablonu.

## <a name="creating-a-function-object"></a>Tworzenie obiektu — funkcja

Aby utworzyć obiekt funkcji, tworzenie typu i implementować operator(), takich jak:

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

Ostatni wiersz `main` funkcja pokazuje, jak wywołać obiekt funkcji. To wywołanie wygląda wywołanie funkcji, ale faktycznie dzwoni operator() typu obiekt. Ta podobieństwa między wywoływania obiektem funkcji i funkcji jest jak obiekt funkcji termin pochodzi.

## <a name="function-objects-and-containers"></a>Funkcja obiektów i kontenerów

Standardowa biblioteka C++ zawiera kilka funkcji obiektów w [ \<funkcjonalności >](../standard-library/functional.md) pliku nagłówka. Jedno użycie tych obiektów funkcji jest jako kryterium sortowania dla kontenerów. Na przykład `set` kontenera jest zadeklarowany w następujący sposób:

```cpp
template <class Key,
    class Traits=less<Key>,
    class Allocator=allocator<Key>>
class set
```

Typ drugiego argumentu szablonu jest obiektem funkcji `less`. Ten obiekt funkcja zwraca `true` Jeśli pierwszy parametr przekazany do jest mniejsza niż drugi parametr przekazany. Ponieważ niektóre kontenery posortować ich elementów, kontener musi sposób porównywania dwóch elementów i odbywa się przy użyciu obiektu funkcji. Możesz definiować własne kryteria dla kontenerów sortowania tworzenia obiektu funkcji i określając go na liście szablonów dla kontenera.

## <a name="function-objects-and-algorithms"></a>Algorytmy i obiekty funkcji

Użyj innego funkcjonalności obiektów jest algorytmów. Na przykład `remove_if` algorytm jest zadeklarowany w następujący sposób:

```cpp
template <class ForwardIterator, class Predicate>
ForwardIterator remove_if(
    ForwardIterator first,
    ForwardIterator last,
    Predicate pred);
```

Ostatni argument `remove_if` jest obiektem funkcji, która zwraca wartość logiczną ( *predykatu*). Jeśli wynik obiekt funkcji jest `true`, a następnie element zostanie usunięty z kontenera, do której uzyskuje dostęp Iteratory `first` i `last`. Można użyć dowolnego z obiektów funkcja zadeklarowana w [ \<funkcjonalności >](../standard-library/functional.md) nagłówka dla argumentu `pred` lub Utwórz swój własny.

## <a name="see-also"></a>Zobacz także

[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
