---
title: klasa boyer_moore_horspool_searcher
ms.date: 08/03/2019
f1_keywords:
- functional/std::boyer_moore_horspool_searcher
helpviewer_keywords:
- std::boyer_moore_horspool_searcher [C++]
ms.openlocfilehash: 4d404b414ad632e02be5f4e9fad0e22cefb86ce2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366777"
---
# <a name="boyer_moore_horspool_searcher-class"></a>klasa boyer_moore_horspool_searcher

Klasa `boyer_moore_horspool_searcher` jest typem obiektu funkcji, który używa algorytmu Boyer-Moore-Horspool do wyszukiwania sekwencji określonej w konstruktorze obiektu. Wyszukiwanie odbywa się w ramach innej sekwencji dostarczone do operatora wywołania funkcji obiektu. Ta klasa jest przekazywana jako parametr do jednego z przeciążeń [std::search](algorithm-functions.md#search).

## <a name="syntax"></a>Składnia

```cpp
template <
    class RandomAccessIterator,
    class Hash = hash<typename iterator_traits<RandomAccessIterator>::value_type>,
    class BinaryPredicate = equal_to<>>
class boyer_moore_horspool_searcher
{
    boyer_moore_horspool_searcher(
        RandomAccessIterator pat_first,
        RandomAccessIterator pat_last,
        Hash hf = Hash(),
        BinaryPredicate pred = BinaryPredicate());

    template <class RandomAccessIterator2>
    pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
        RandomAccessIterator2 first,
        RandomAccessIterator2 last) const;
};
```

## <a name="members"></a>Elementy członkowskie

| | |
| - | - |
| **Konstruktor** | |
| [boyer_moore_horspool_searcher](#boyer-moore-horspool-searcher-constructor) | |
| **Operatory** | |
| [Operator()](#operator-call) | |

## <a name="boyer_moore_horspool_searcher-constructor"></a><a name="boyer-moore-horspool-searcher-constructor"></a>boyer_moore_horspool_searcher konstruktor

Konstruuje `boyer_moore_horspool_searcher` obiekt funkcji przy użyciu sekwencji do wyszukiwania, obiekt funkcji mieszania i predykatu równości.

```cpp
boyer_moore_horspool_searcher(
    RandomAccessIterator pat_first,
    RandomAccessIterator pat_last,
    Hash hf = Hash(),
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>Parametry

*pat_first*\
Początkowy element sekwencji do wyszukania.

*pat_last*\
Koniec sekwencji do wyszukania.

*Hf*\
Wywoływany obiekt, używany do mieszania elementów sekwencji.

*pred*\
Predykat porównania opcjonalnej równości dla elementów sekwencji. Jeśli typ porównania równości nie jest określony, wartością domyślną jest `std::equal_to`.

### <a name="remarks"></a>Uwagi

Zgłasza dowolny wyjątek zgłoszony przez konstruktora kopii typów *BinaryPredicate*, *Hash*, lub *RandomAccessIterator* lub operator wywołania *BinaryPredicate* lub *Hash*.

Ta klasa jest nowa w języku C++17.

## <a name="operator"></a><a name="operator-call"></a>Operator()

Operator wywołania obiektu funkcji. Przeszukuje w `[first, last)` sekwencji argumentów sekwencji określonych do konstruktora.

```cpp
template <class ForwardIterator2>   // C++17
pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
    RandomAccessIterator2 first,
    RandomAccessIterator2 last) const;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Początkowy element sekwencji do wyszukiwania w obrębie.

*Ostatnio*\
Koniec sekwencji do wyszukiwania w obrębie.

### <a name="remarks"></a>Uwagi

Jeśli wzorzec `[pat_first, pat_last)` wyszukiwania `make_pair(first, first)`jest pusty, zwraca program . Jeśli wzorzec wyszukiwania nie `make_pair(last, last)`zostanie znaleziony, zwraca wartość . W przeciwnym razie zwraca parę iteratorów na początku `[first, last)` i na końcu `[pat_first, pat_last)` sekwencji, która jest równa zgodnie z predykatem *przed .*

Ta klasa jest nowa w języku C++17.

## <a name="see-also"></a>Zobacz też

[\<>funkcjonalne](functional.md)\
[funkcje algorytmu](algorithm-functions.md)\
[klasa boyer_moore_searcher](boyer-moore-searcher-class.md)\
[std::wyszukiwanie](algorithm-functions.md#search)
