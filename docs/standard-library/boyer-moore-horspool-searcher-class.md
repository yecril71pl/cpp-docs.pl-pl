---
title: Klasa boyer_moore_horspool_searcher
ms.date: 08/03/2019
f1_keywords:
- functional/std::boyer_moore_horspool_searcher
helpviewer_keywords:
- std::boyer_moore_horspool_searcher [C++]
ms.openlocfilehash: 1eb1f099ca2976dd4b0ea80ebdfb93a8b5c61f70
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039836"
---
# <a name="boyer_moore_horspool_searcher-class"></a>Klasa boyer_moore_horspool_searcher

`boyer_moore_horspool_searcher`Klasa jest typem obiektu funkcji, który używa algorytmu Boyer-Moore-Horspool, aby wyszukać sekwencję określoną w konstruktorze obiektu. Wyszukiwanie jest wykonywane w innej sekwencji dostarczonej do operatora wywołania funkcji obiektu. Ta klasa jest przenoszona jako parametr do jednego z przeciążeń [std:: Search](algorithm-functions.md#search).

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

| Członek | Opis |
| - | - |
| **Konstruktor** | |
| [boyer_moore_horspool_searcher](#boyer-moore-horspool-searcher-constructor) | Tworzy wystąpienie elementu Searcher. |
| **Operatory** | |
| [operator ()](#operator-call) | Wywołuje operację na sekwencji. |

## <a name="boyer_moore_horspool_searcher-constructor"></a><a name="boyer-moore-horspool-searcher-constructor"></a> Konstruktor boyer_moore_horspool_searcher

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
Opcjonalny predykat porównania równości dla elementów sekwencji. Jeśli typ porównania równości nie jest określony, wartość domyślna to `std::equal_to` .

### <a name="remarks"></a>Uwagi

Zgłasza każdy wyjątek zgłoszony przez Konstruktor kopiujący typów *BinaryPredicate*, *hash*lub *RandomAccessIterator* lub operator wywołania *BinaryPredicate* lub *hash*.

Ta klasa jest nowa w języku C++ 17.

## <a name="operator"></a><a name="operator-call"></a> operator ()

Operator wywołania obiektu Function. Wyszukuje w sekwencji argumentów `[first, last)` dla sekwencji określonej dla konstruktora.

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

Jeśli wzorzec wyszukiwania `[pat_first, pat_last)` jest pusty, zwraca `make_pair(first, first)` . Jeśli nie odnaleziono wzorca wyszukiwania, zwraca `make_pair(last, last)` . W przeciwnym razie zwraca parę iteratorów na początku i na końcu sekwencji, tak samo jak w przypadku `[first, last)` `[pat_first, pat_last)` predykatu *pred*.

Ta klasa jest nowa w języku C++ 17.

## <a name="see-also"></a>Zobacz także

[\<functional>](functional.md)\
[funkcje algorytmu](algorithm-functions.md)\
[Klasa boyer_moore_searcher](boyer-moore-searcher-class.md)\
[std:: Search](algorithm-functions.md#search)
