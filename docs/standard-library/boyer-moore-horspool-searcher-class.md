---
title: Klasa boyer_moore_horspool_searcher
ms.date: 08/03/2019
f1_keywords:
- functional/std::boyer_moore_horspool_searcher
helpviewer_keywords:
- std::boyer_moore_horspool_searcher [C++]
ms.openlocfilehash: c7d24fee4a47fc588b00e527594682f1c4aadf76
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957162"
---
# <a name="boyer_moore_horspool_searcher-class"></a>Klasa boyer_moore_horspool_searcher

`boyer_moore_horspool_searcher` Klasa jest typem obiektu funkcji, który używa algorytmu Boyer-Moore-Horspool, aby wyszukać sekwencję określoną w konstruktorze obiektu. Wyszukiwanie jest wykonywane w innej sekwencji dostarczonej do operatora wywołania funkcji obiektu. Ta klasa jest przenoszona jako parametr do jednego z przeciążeń [std:: Search](algorithm-functions.md#search).

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
| **Konstruktora** | |
| [boyer_moore_horspool_searcher](#boyer-moore-horspool-searcher-constructor) | |
| **Operatory** | |
| [operator()](#operator-call) | |

## <a name="boyer-moore-horspool-searcher-constructor"></a>Konstruktor boyer_moore_horspool_searcher

Konstruuje `boyer_moore_horspool_searcher` obiekt funkcji przy użyciu sekwencji do wyszukiwania, obiektu funkcji hash i predykatu równości.

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

*HF*\
Obiekt, który można wywołać, używany do mieszania elementów sekwencji.

*pred*\
Opcjonalny predykat porównania równości dla elementów sekwencji. Jeśli typ porównania równości nie jest określony, wartość domyślna to `std::equal_to`.

### <a name="remarks"></a>Uwagi

Zgłasza każdy wyjątek zgłoszony przez Konstruktor kopiujący typów *BinaryPredicate*, *hash*lub *RandomAccessIterator* lub operator wywołania *BinaryPredicate* lub *hash*.

Ta klasa jest nowa w języku C++ 17.

## <a name="operator-call"></a>operator ()

Operator wywołania obiektu Function. Wyszukuje w sekwencji `[first, last)` argumentów dla sekwencji określonej dla konstruktora.

```cpp
template <class ForwardIterator2>   // C++17
pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
    RandomAccessIterator2 first,
    RandomAccessIterator2 last) const;
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Początkowy element sekwencji do przeszukania.

*ostatniego*\
Koniec sekwencji do przeszukania.

### <a name="remarks"></a>Uwagi

Jeśli wzorzec `[pat_first, pat_last)` wyszukiwania jest pusty, zwraca `make_pair(first, first)`. Jeśli nie odnaleziono wzorca wyszukiwania, zwraca `make_pair(last, last)`. W przeciwnym razie zwraca parę iteratorów na początku i na końcu sekwencji, tak `[first, last)` `[pat_first, pat_last)` samo jak w przypadku predykatu *pred*.

Ta klasa jest nowa w języku C++ 17.

## <a name="see-also"></a>Zobacz także

[\<functional>](functional.md)\
[funkcje algorytmu](algorithm-functions.md)\
[Klasa boyer_moore_searcher](boyer-moore-searcher-class.md)\
[std:: Search](algorithm-functions.md#search)
