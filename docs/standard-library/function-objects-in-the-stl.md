---
title: Obiekty funkcji w standardowej bibliotece języka C++
ms.date: 03/15/2019
helpviewer_keywords:
- functors
- C++ Standard Library, functors
- C++ Standard Library, function objects
- function objects
ms.assetid: 85f8a735-2c7b-4f10-9c4d-95c666ec4192
ms.openlocfilehash: ed413b2bcdcda8f65794b10c792b10358564420a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215741"
---
# <a name="function-objects-in-the-c-standard-library"></a>Obiekty funkcji w standardowej bibliotece języka C++

*Obiekt Function*lub *Funktor*jest dowolnym typem, który implementuje operator (). Ten operator jest nazywany *operatorem wywołania* lub czasami *operatorem aplikacji*. Standardowa biblioteka języka C++ używa obiektów funkcyjnych głównie jako kryterium sortowania kontenerów i algorytmów.

Obiekty funkcyjne zapewniają dwie główne zalety wywołania funkcji prostych. Pierwszy polega na tym, że obiekt funkcji może zawierać stan. Drugim jest to, że obiekt funkcji jest typem i dlatego może być używany jako parametr szablonu.

## <a name="creating-a-function-object"></a>Tworzenie obiektu funkcji

Aby utworzyć obiekt funkcji, należy utworzyć typ i zaimplementować operatora (), takie jak:

```cpp
class Functor
{
public:
    int operator()(int a, int b)
    {
        return a < b;
    }
};

int main()
{
    Functor f;
    int a = 5;
    int b = 7;
    int ans = f(a, b);
}
```

Ostatni wiersz `main` funkcji pokazuje, jak wywołać obiekt Function. To wywołanie wygląda jak wywołanie funkcji, ale rzeczywiście wywołuje operator () typu Funktor. Ta podobieństwo między wywołaniem obiektu funkcyjnego a funkcją polega na tym, jak pochodziło na obiekt funkcji terminowej.

## <a name="function-objects-and-containers"></a>Obiekty funkcyjne i kontenery

Standardowa biblioteka języka C++ zawiera kilka obiektów funkcji w [\<functional>](../standard-library/functional.md) pliku nagłówkowym. Jednym z nich jest użycie tych obiektów funkcyjnych jako kryterium sortowania kontenerów. Na przykład `set` kontener jest zadeklarowany w następujący sposób:

```cpp
template <class Key,
    class Traits=less<Key>,
    class Allocator=allocator<Key>>
class set
```

Drugi argument szablonu jest obiektem funkcji `less` . Ten obiekt funkcji zwraca wartość **`true`** , jeśli pierwszy parametr jest mniejszy niż drugi parametr. Ponieważ niektóre kontenery są sortowane według ich elementów, kontener wymaga metody porównania dwóch elementów. Porównanie odbywa się przy użyciu obiektu Function. Można zdefiniować własne kryteria sortowania dla kontenerów, tworząc obiekt funkcji i określając go na liście szablonów dla kontenera.

## <a name="function-objects-and-algorithms"></a>Obiekty i algorytmy funkcji

Inne użycie obiektów funkcjonalnych jest w algorytmach. Na przykład `remove_if` algorytm jest zadeklarowany w następujący sposób:

```cpp
template <class ForwardIterator, class Predicate>
ForwardIterator remove_if(
    ForwardIterator first,
    ForwardIterator last,
    Predicate pred);
```

Ostatni argument `remove_if` jest obiektem funkcji, który zwraca wartość logiczną ( *predykatu*). Jeśli wynikiem obiektu funkcji jest **`true`** , element zostanie usunięty z kontenera, do którego uzyskuje dostęp Iteratory `first` i `last` . Można użyć dowolnego z obiektów funkcji zadeklarowanych w [\<functional>](../standard-library/functional.md) nagłówku dla argumentu lub można `pred` utworzyć własny.

## <a name="see-also"></a>Zobacz także

[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
