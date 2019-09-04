---
title: Klasa default_searcher
ms.date: 08/03/2019
f1_keywords:
- functional/std::default_searcher
helpviewer_keywords:
- std::default_searcher [C++]
ms.openlocfilehash: f2b1fe83b5223bbb60e9e32149c101e6379f93c3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "68268001"
---
# <a name="default_searcher-class"></a>Klasa default_searcher

A `default_searcher` jest typem obiektu funkcji dla operacji, które wyszukują sekwencję określoną w konstruktorze obiektu. Wyszukiwanie jest wykonywane w innej sekwencji dostarczonej do operatora wywołania funkcji obiektu. Wywołanie std [:: Search](algorithm-functions.md#search) w celu przeprowadzenia wyszukiwania. `default_searcher`

## <a name="syntax"></a>Składnia

```cpp
template <class ForwardIterator, class BinaryPredicate = equal_to<>>
class default_searcher
{
    default_searcher(
        ForwardIterator pat_first,
        ForwardIterator pat_last,
        BinaryPredicate pred = BinaryPredicate());

    template <class ForwardIterator2>
    pair<ForwardIterator2, ForwardIterator2> operator()(
        ForwardIterator2 first,
        ForwardIterator2 last) const;
};
```

## <a name="members"></a>Elementy członkowskie

| | |
| - | - |
| **Konstruktora** | |
| [default_searcher](#default-searcher-constructor) | |
| **Operatory** | |
| [operator()](#operator-call) | |

## <a name="default-searcher-constructor"></a>Konstruktor default_searcher

Konstruuje `default_searcher` obiekt funkcji przy użyciu sekwencji do wyszukiwania i predykatu równości.

```cpp
default_searcher(                   // C++17
    ForwardIterator pat_first,
    ForwardIterator pat_last,
    BinaryPredicate pred = BinaryPredicate());

constexpr default_searcher(         // C++20
    ForwardIterator pat_first,
    ForwardIterator pat_last,
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>Parametry

*pat_first*\
Początkowy element sekwencji do wyszukania.

*pat_last*\
Koniec sekwencji do wyszukania.

*pred*\
Opcjonalny predykat porównania równości dla elementów sekwencji. Jeśli typ porównania równości nie jest określony, wartość domyślna to `std::equal_to`.

### <a name="remarks"></a>Uwagi

Zgłasza każdy wyjątek zgłoszony przez Konstruktor kopiujący typów *BinaryPredicate* lub *ForwardIterator* .

Ta klasa jest nowa w języku C++ 17. C++ 20 wykonał konstruktora `constexpr`.

## <a name="operator-call"></a>operator ()

Operator wywołania operatora funkcji. Wyszukuje w sekwencji `[first, last)` argumentów dla sekwencji określonej dla konstruktora.

```cpp
template <class ForwardIterator2>   // C++17
pair<ForwardIterator2, ForwardIterator2> operator()(
    ForwardIterator2 first,
    ForwardIterator2 last) const;

template <class ForwardIterator2>   // C++20
constexpr pair<ForwardIterator2, ForwardIterator2> operator()(
    ForwardIterator2 first,
    ForwardIterator2 last) const;
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Początkowy element sekwencji do przeszukania.

*ostatniego*\
Koniec sekwencji do przeszukania.

### <a name="remarks"></a>Uwagi

Zwraca parę iteratorów. Iterator początkowy *i* jest skuteczny wynik:

`std::search( first, last, pat_first, pat_last, pred )`.

Drugi iterator pary jest *ostatni* , jeśli *i** jest *Last*. W przeciwnym razie jest to skuteczny wynik:

`std::next( i, std::distance( pat_first, pat_last ))`.

Ta klasa jest nowa w języku C++ 17. C++ 20 wykonał operator `constexpr`wywołania.

## <a name="see-also"></a>Zobacz także

[\<functional>](functional.md)\
[funkcje algorytmu](algorithm-functions.md)\
[std:: Search](algorithm-functions.md#search)
