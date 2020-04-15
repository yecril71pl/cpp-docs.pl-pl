---
title: klasa default_searcher
ms.date: 08/03/2019
f1_keywords:
- functional/std::default_searcher
helpviewer_keywords:
- std::default_searcher [C++]
ms.openlocfilehash: 2c8b93b83b271f787c993f789e1a68f84a60f016
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368922"
---
# <a name="default_searcher-class"></a>Klasa default_searcher

A `default_searcher` jest typem obiektu funkcji dla operacji, które wyszukują sekwencję określoną w konstruktorze obiektu. Wyszukiwanie odbywa się w ramach innej sekwencji dostarczone do operatora wywołania funkcji obiektu. Wywoływania `default_searcher` [std::search,](algorithm-functions.md#search) aby wykonać wyszukiwanie.

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
| **Konstruktor** | |
| [default_searcher](#default-searcher-constructor) | |
| **Operatory** | |
| [Operator()](#operator-call) | |

## <a name="default_searcher-constructor"></a><a name="default-searcher-constructor"></a>default_searcher konstruktor

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
Predykat porównania opcjonalnej równości dla elementów sekwencji. Jeśli typ porównania równości nie jest określony, wartością domyślną jest `std::equal_to`.

### <a name="remarks"></a>Uwagi

Zgłasza wyjątek zgłoszony przez konstruktora kopii *binarypredicate* lub *ForwardIterator* typów.

Ta klasa jest nowa w języku C++17. C++20 wykonał konstruktor `constexpr`.

## <a name="operator"></a><a name="operator-call"></a>Operator()

Operator wywołania operatora funkcji. Przeszukuje w `[first, last)` sekwencji argumentów sekwencji określonych do konstruktora.

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

*Pierwszym*\
Początkowy element sekwencji do wyszukiwania w obrębie.

*Ostatnio*\
Koniec sekwencji do wyszukiwania w obrębie.

### <a name="remarks"></a>Uwagi

Zwraca parę iteratorów. Początkowy iterator *i* jest skutecznym wynikiem:

`std::search( first, last, pat_first, pat_last, pred )`.

Drugi iterator pary jest *ostatni,* jeśli *** jest *ostatni*. W przeciwnym razie jest to skuteczny wynik:

`std::next( i, std::distance( pat_first, pat_last ))`.

Ta klasa jest nowa w języku C++17. C++20 wykonał operator `constexpr`połączenia .

## <a name="see-also"></a>Zobacz też

[\<>funkcjonalne](functional.md)\
[funkcje algorytmu](algorithm-functions.md)\
[std::wyszukiwanie](algorithm-functions.md#search)
