---
title: algorithm (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/algorithm>
- cliext::adjacent_find
- cliext::binary_search
- cliext::copy
- cliext::copy_backward
- cliext::count
- cliext::count_if
- cliext::equal
- cliext::equal_range
- cliext::fill
- cliext::fill_n
- cliext::find
- cliext::find_end
- cliext::find_first_of
- cliext::find_if
- cliext::for_each
- cliext::generate
- cliext::generate_n
- cliext::includes
- cliext::inplace_merge
- cliext::iter_swap
- cliext::lexicographical_compare
- cliext::lower_bound
- cliext::make_heap
- cliext::max
- cliext::max_element
- cliext::merge
- cliext::min
- cliext::min_element
- cliext::mismatch
- cliext::next_permutation
- cliext::nth_element
- cliext::partial_sort
- cliext::partial_sort_copy
- cliext::partition
- cliext::pop_heap
- cliext::prev_permutation
- cliext::push_heap
- cliext::random_shuffle
- cliext::remove
- cliext::remove_copy
- cliext::remove_copy_if
- cliext::remove_if
- cliext::replace
- cliext::replace_copy
- cliext::replace_copy_if
- cliext::replace_if
- cliext::reverse
- cliext::reverse_copy
- cliext::rotate
- cliext::rotate_copy
- cliext::search
- cliext::search_n
- cliext::set_difference
- cliext::set_intersection
- cliext::set_symmetric_difference
- cliext::set_union
- cliext::sort
- cliext::sort_heap
- cliext::stable_partition
- cliext::stable_sort
- cliext::swap
- cliext::swap_ranges
- cliext::transform
- cliext::unique
- cliext::unique_copy
- cliext::upper_bound
helpviewer_keywords:
- algorithm functions [STL/CLR]
- <algorithm> header [STL/CLR]
- <cliext/algorithm> header [STL/CLR]
- adjacent_find function
- binary_search function [STL/CLR]
- copy function [STL/CLR]
- copy_backward function [STL/CLR]
- count function [STL/CLR]
- count_if function [STL/CLR]
- equal function [STL/CLR]
- equal_range function [STL/CLR]
- fill function
- fill_n function
- find function [STL/CLR]
- find_end function [STL/CLR]
- find_first_of function [STL/CLR]
- find_if function [STL/CLR]
- for_each function [STL/CLR]
- generate function [STL/CLR]
- generate_n function [STL/CLR]
- includes function [STL/CLR]
- inplace_merge function [STL/CLR]
- iter_swap function [STL/CLR]
- lexicographical_compare function [STL/CLR]
- lower_bound function [STL/CLR]
- make_heap function [STL/CLR]
- max function [STL/CLR]
- max_element function [STL/CLR]
- merge function [STL/CLR]
- min function [STL/CLR]
- min_element function [STL/CLR]
- mismatch function [STL/CLR]
- next_permutation function [STL/CLR]
- nth_element function [STL/CLR]
- partial_sort function [STL/CLR]
- partial_sort_copy function [STL/CLR]
- partition function [STL/CLR]
- pop_heap function [STL/CLR]
- prev_permutation function [STL/CLR]
- push_heap function [STL/CLR]
- random_shuffle function [STL/CLR]
- remove function [STL/CLR]
- remove_copy function [STL/CLR]
- remove_copy_if function [STL/CLR]
- remove_if function [STL/CLR]
- replace function [STL/CLR]
- replace_copy function [STL/CLR]
- replace_copy_if function [STL/CLR]
- replace_if function [STL/CLR]
- reverse function [STL/CLR]
- reverse_copy function [STL/CLR]
- rotate function [STL/CLR]
- rotate_copy function [STL/CLR]
- search function [STL/CLR]
- search_n function [STL/CLR]
- set_difference function [STL/CLR]
- set_intersection function [STL/CLR]
- set_symmetric_difference function [STL/CLR]
- set_union function [STL/CLR]
- sort function [STL/CLR]
- sort_heap function [STL/CLR]
- stable_partition function [STL/CLR]
- stable_sort function [STL/CLR]
- swap function [STL/CLR]
- swap_ranges function [STL/CLR]
- transform function [STL/CLR]
- unique function [STL/CLR]
- unique_copy function [STL/CLR]
- upper_bound function [STL/CLR]
ms.assetid: ee2718dc-a98d-40b8-8341-593fe7d2ac15
ms.openlocfilehash: 4abd7eaa640bb89fd97c1787bf2fd692610212fb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208954"
---
# <a name="algorithm-stlclr"></a>algorithm (STL/CLR)

Definiuje funkcje szablonu kontenera STL/CLR, które wykonują algorytmy.

## <a name="syntax"></a>Składnia

```cpp
#include <cliext/algorithm>
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<cliext/algorytm >

**Przestrzeń nazw:** cliext

## <a name="declarations"></a>Deklaracje

|Funkcja|Opis|
|--------------|-----------------|
|[adjacent_find (STL/CLR)](#adjacent_find)|Wyszukuje dwa sąsiadujące elementy, które są równe.|
|[binary_search (STL/CLR)](#binary_search)|Testuje, czy posortowana sekwencja zawiera daną wartość.|
|[copy (STL/CLR)](#copy)|Kopiuje wartości z zakresu źródłowego do zakresu docelowego, Iterowanie w kierunku do przodu.|
|[copy_backward (STL/CLR)](#copy_backward)|Kopiuje wartości z zakresu źródłowego do zakresu docelowego, Iterowanie w kierunku do tyłu.|
|[count (STL/CLR)](#count)|Zwraca liczbę elementów w zakresie, których wartości pasują do określonej wartości.|
|[count_if (STL/CLR)](#count_if)|Zwraca liczbę elementów w zakresie, których wartości pasują do określonego warunku.|
|[equal (STL/CLR)](#equal)|Porównuje dwa zakresy, element po elemencie.|
|[equal_range (STL/CLR)](#equal_range)|Przeszukuje uporządkowaną sekwencję wartości i zwraca dwie pozycje, które ograniczają podsekwencję wartości, które są równe podanemu elementowi.|
|[fill (STL/CLR)](#fill)|Przypisuje tę samą nową wartość każdemu elementowi w określonym zakresie.|
|[fill_n (STL/CLR)](#fill_n)|Przypisuje nową wartość do określonej liczby elementów w zakresie rozpoczynającym się od określonego elementu.|
|[find (STL/CLR)](#find)|Zwraca pozycję pierwszego wystąpienia określonej wartości.|
|[find_end (STL/CLR)](#find_end)|Zwraca ostatnią podsekwencję w zakresie, który jest identyczny z określoną sekwencją.|
|[find_first_of (STL/CLR)](#find_first_of)|Wyszukuje zakres pierwszego wystąpienia jednego z danego zakresu elementów.|
|[find_if (STL/CLR)](#find_if)|Zwraca pozycję pierwszego elementu w sekwencji wartości, gdzie element spełnia określony warunek.|
|[for_each (STL/CLR)](#for_each)|Stosuje określony obiekt Function do każdego elementu w sekwencji wartości i zwraca obiekt Function.|
|[generate (STL/CLR)](#generate)|Przypisuje wartości generowane przez obiekt funkcji do każdego elementu w sekwencji wartości.|
|[generate_n (STL/CLR)](#generate_n)|Przypisuje wartości generowane przez obiekt funkcji do określonej liczby elementów.|
|[includes (STL/CLR)](#includes)|Testuje, czy jeden z posortowanego zakresu zawiera wszystkie elementy w drugim posortowanym zakresie.|
|[inplace_merge (STL/CLR)](#inplace_merge)|Łączy elementy z dwóch kolejnych posortowanych zakresów w pojedynczy posortowany zakres.|
|[iter_swap (STL/CLR)](#iter_swap)|Wymienia dwie wartości, do których odnosi się para określonych iteratorów.|
|[lexicographical_compare (STL/CLR)](#lexicographical_compare)|Porównuje dwie sekwencje elementu przez element, identyfikując, która sekwencja jest częścią obu.|
|[lower_bound (STL/CLR)](#lower_bound)|Znajduje pozycję pierwszego elementu w uporządkowanej sekwencji wartości, która ma wartość większą lub równą określonej wartości.|
|[make_heap (STL/CLR)](#make_heap)|Konwertuje elementy z określonego zakresu na stertę, w której pierwszy element sterty jest największy.|
|[Max (STL/CLR)](#max))|Porównuje dwa obiekty i zwraca większe z nich.|
|[max_element (STL/CLR)](#max_element)|Znajduje największy element w określonej sekwencji wartości.|
|[scalanie (STL/CLR)](#merge))|Łączy wszystkie elementy z dwóch posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy.|
|[min (STL/CLR)](#min)|Porównuje dwa obiekty i zwraca mniejsze z nich.|
|[min_element (STL/CLR)](#min_element)|Znajduje najmniejszy element w określonej sekwencji wartości.|
|[mismatch (STL/CLR)](#mismatch)|Porównuje dwa zakresy elementów przez element i zwraca pierwszą pozycję, w której występuje różnica.|
|[next_permutation (STL/CLR)](#next_permutation)|Zmienia kolejność elementów w zakresie, aby oryginalne porządkowanie zostało zastąpione przez lexicographically następną permutację, jeśli istnieje.|
|[nth_element (STL/CLR)](#nth_element)|Dzieli sekwencję elementów, poprawnie lokalizując `n`element sekwencji, tak aby wszystkie elementy przed nim były mniejsze lub równe, a wszystkie elementy, które po niej znajdują się, są większe lub równe.|
|[partial_sort (STL/CLR)](#partial_sort)|Rozmieszcza określoną liczbę mniejszych elementów w zakresie w kolejności niemalejącej.|
|[partial_sort_copy (STL/CLR)](#partial_sort_copy)|Kopiuje elementy z zakresu źródłowego do zakresu docelowego w taki sposób, że elementy z zakresu źródłowego są uporządkowane.|
|[partition (STL/CLR)](#partition)|Rozmieszcza elementy w zakresie w taki sposób, że te elementy, które spełniają predykat jednoargumentowy, poprzedzają te, które nie spełniają tego warunku.|
|[pop_heap (STL/CLR)](#pop_heap)|Przenosi największy element z przodu sterty na koniec, a następnie tworzy nową stertę z pozostałych elementów.|
|[prev_permutation (STL/CLR)](#prev_permutation)|Zmienia kolejność elementów tak, aby oryginalne porządkowanie zostało zastąpione przez lexicographically poprzednią permutację, jeśli istnieje.|
|[push_heap (STL/CLR)](#push_heap)|Dodaje element znajdujący się na końcu zakresu do istniejącej sterty, która składa się z poprzednich elementów w zakresie.|
|[random_shuffle (STL/CLR)](#random_shuffle)|Zmienia kolejność `N` elementów w zakresie na jedną z `N`. możliwe rozwiązania wybrane losowo.|
|[remove (STL/CLR)](#remove)|Usuwa określoną wartość z danego zakresu bez zakłócania kolejności pozostałych elementów i zwraca koniec nowego zakresu wolnej od określonej wartości.|
|[remove_copy (STL/CLR)](#remove_copy)|Kopiuje elementy z zakresu źródłowego do zakresu docelowego, z tą różnicą, że elementy określonej wartości nie są kopiowane, bez zakłócania kolejności pozostałych elementów.|
|[remove_copy_if (STL/CLR)](#remove_copy_if)|Kopiuje elementy z zakresu źródłowego do zakresu docelowego, z wyjątkiem tych, które spełniają predykat, bez zakłócania kolejności pozostałych elementów.|
|[remove_if (STL/CLR)](#remove_if)|Usuwa elementy, które spełniają predykat z danego zakresu bez zakłócania kolejności pozostałych elementów. .|
|[replace (STL/CLR)](#replace)|Zamienia elementy w zakresie, który pasuje do określonej wartości z nową wartością.|
|[replace_copy (STL/CLR)](#replace_copy)|Kopiuje elementy z zakresu źródłowego do zakresu docelowego, zastępując elementy, które pasują do określonej wartości nową wartością.|
|[replace_copy_if (STL/CLR)](#replace_copy_if)|Sprawdza każdy element w zakresie źródłowym i zastępuje go, jeśli spełnia określony predykat, jednocześnie kopiując wynik do nowego zakresu docelowego.|
|[replace_if (STL/CLR)](#replace_if)|Sprawdza każdy element w zakresie i zastępuje go, jeśli spełnia określony predykat.|
|[reverse (STL/CLR)](#reverse)|Odwraca kolejność elementów w obrębie zakresu.|
|[reverse_copy (STL/CLR)](#reverse_copy)|Odwraca kolejność elementów w zakresie źródłowym, kopiując je do zakresu docelowego.|
|[rotate (STL/CLR)](#rotate)|Wymienia elementy znajdujące się w dwóch sąsiednich zakresach.|
|[rotate_copy (STL/CLR)](#rotate_copy)|Wymienia elementy w dwóch sąsiednich zakresach w ramach zakresu źródłowego i kopiuje wynik do zakresu docelowego.|
|[search (STL/CLR)](#search_)|Wyszukuje pierwsze wystąpienie sekwencji w zakresie docelowym, której elementy są równe tym w danej sekwencji elementów lub której elementy są równoważne w sensie określonym przez predykat binarny dla elementów w danej sekwencji.|
|[search_n (STL/CLR)](#search_n)|Wyszukuje pierwszą podsekwencję w zakresie, w której określona liczba elementów ma określoną wartość lub relację do tej wartości określoną przez predykat binarny.|
|[set_difference (STL/CLR)](#set_difference)|Łączy w sobie wszystkie elementy, które należą do jednego posortowanego zakresu źródłowego, ale nie do drugiego posortowanego zakresu źródłowego, w pojedynczy, posortowany zakres docelowy, gdzie kryterium sortowania może być określone przez predykat binarny.|
|[set_intersection (STL/CLR)](#set_intersection)|Łączy w sobie wszystkie elementy, które należą do obu posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.|
|[set_symmetric_difference (STL/CLR)](#set_symmetric_difference)|Łączy w sobie wszystkie elementy, które należą do jednego z, ale nie obu posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.|
|[set_union (STL/CLR)](#set_union))|Łączy w sobie wszystkie elementy, które należą do przynajmniej jednego z dwóch posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.|
|[sort (STL/CLR)](#sort)|Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryteriów sortowania określonych przez binarny predykat.|
|[sort_heap (STL/CLR)](#sort_heap)|Konwertuje stertę na sortowany zakres.|
|[stable_partition (STL/CLR)](#stable_partition)|Klasyfikuje elementy w zakresie na dwa rozłączne zestawy, z elementami spełniającymi predykat unarny poprzedzającymi te, które go nie spełniają, zachowując względną kolejność elementów równoważnych.|
|[stable_sort (STL/CLR)](#stable_sort)|Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryterium sortowania określonego przez binarny predykat i zachowuje względną kolejność elementów równoważnych.|
|[swap (STL/CLR)](#swap)|Wymienia wartości elementów między dwoma typami obiektów, przypisując zawartość pierwszego obiektu do drugiego obiektu, a zawartość drugiego do pierwszego.|
|[swap_ranges (STL/CLR)](#swap_ranges)|Zamienia elementy jednego zakresu przez elementy innego zakresu, zakresy mają równe wielkości.|
|[transform (STL/CLR)](#transform)|Stosuje określony obiekt funkcji dla każdego elementu w zakresie sortowania lub dla pary elementów z dwóch zakresów sortowania i kopiuje zwracane wartości obiektu funkcji do zakresu docelowego.|
|[unique (STL/CLR)](#unique)|Usuwa zduplikowane elementy, które sąsiadują ze sobą w określonym zakresie.|
|[unique_copy (STL/CLR)](#unique_copy)|Kopiuje elementy z zakresu źródłowego do zakresu docelowego z wyjątkiem zduplikowanych elementów, które ze sobą sąsiadują.|
|[upper_bound (STL/CLR)](#upper_bound)|Znajduje pozycję pierwszego elementu w uporządkowanym zakresie, który ma wartość większą niż określona wartość, gdzie kryterium sortowania może być określone przez predykat binarny.|

## <a name="members"></a>Members

## <a name="adjacent_find-stlclr"></a><a name="adjacent_find"></a>adjacent_find (STL/CLR)

Wyszukuje dwa sąsiadujące elementy, które są równe lub spełniają określony warunek.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt> inline
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `adjacent_find`. Aby uzyskać więcej informacji, zobacz [adjacent_find](../standard-library/algorithm-functions.md#adjacent_find).

## <a name="binary_search-stlclr"></a><a name="binary_search"></a>binary_search (STL/CLR)

Testuje, czy w sortowanym zakresie istnieje element, który jest równy określonej wartości lub który jest odpowiednikiem w sensie określonym przez predykat binarny.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt, class _Ty> inline
    bool binary_search(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    bool binary_search(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `binary_search`. Aby uzyskać więcej informacji, zobacz [binary_search](../standard-library/algorithm-functions.md#binary_search).

## <a name="copy-stlclr"></a><a name="copy"></a>Kopiuj (STL/CLR)

Przypisuje wartości elementów z zakresu źródłowego do zakresu docelowego, iterując przez sekwencję źródłową elementów oraz przypisując im nowe pozycje w kierunku do przodu.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt copy(_InIt _First, _InIt _Last, _OutIt _Dest);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `copy`. Aby uzyskać więcej informacji, zobacz [Kopiuj](../standard-library/algorithm-functions.md#copy).

## <a name="copy_backward-stlclr"></a><a name="copy_backward"></a>copy_backward (STL/CLR)

Przypisuje wartości elementów z zakresu źródłowego do zakresu docelowego, iterując przez sekwencję źródłową elementów oraz przypisując im nowe pozycje w kierunku do tyłu.

### <a name="syntax"></a>Składnia

```cpp
template<class _BidIt1, class _BidIt2> inline
    _BidIt2 copy_backward(_BidIt1 _First, _BidIt1 _Last,
        _BidIt2 _Dest);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `copy_backward`. Aby uzyskać więcej informacji, zobacz [copy_backward](../standard-library/algorithm-functions.md#copy_backward).

## <a name="count-stlclr"></a><a name="count"></a>Count (STL/CLR)

Zwraca liczbę elementów w zakresie, których wartości pasują do określonej wartości.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt, class _Ty> inline
    typename iterator_traits<_InIt>::difference_type
        count(_InIt _First, _InIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `count`. Aby uzyskać więcej informacji, zobacz [Count](../standard-library/algorithm-functions.md#count).

## <a name="count_if-stlclr"></a><a name="count_if"></a>count_if (STL/CLR)

Zwraca liczbę elementów w zakresie, których wartości pasują do określonego warunku.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt, class _Pr> inline
    typename iterator_traits<_InIt>::difference_type
        count_if(_InIt _First, _InIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `count_if`. Aby uzyskać więcej informacji, zobacz [count_if](../standard-library/algorithm-functions.md#count_if).

## <a name="equal-stlclr"></a><a name="equal"></a>równe (STL/CLR)

Porównuje dwa zakresy element po elemencie, pod względem równości lub równoważności w sensie określonym przez predykat binarny.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt1, class _InIt2> inline
    bool equal(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);
template<class _InIt1, class _InIt2, class _Pr> inline
    bool equal(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `equal`. Aby uzyskać więcej informacji, zobacz [równa](../standard-library/algorithm-functions.md#equal)się.

## <a name="equal_range-stlclr"></a><a name="equal_range"></a>equal_range (STL/CLR)

Wyszukuje parę pozycji w uporządkowanym zakresie, pierwszą mniejszą lub równoważną położeniu określonego elementu, a drugą większą niż pozycja elementu, gdzie sens równoważności lub szeregowania używany do ustanawiania pozycji w sekwencji może zostać określony przez predykat binarny.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt, class _Ty> inline
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `equal_range`. Aby uzyskać więcej informacji, zobacz [equal_range](../standard-library/algorithm-functions.md#equal_range).

## <a name="fill-stlclr"></a><a name="fill"></a>Wypełnienie (STL/CLR)

Przypisuje tę samą nową wartość każdemu elementowi w określonym zakresie.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt, class _Ty> inline
    void fill(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `fill`. Aby uzyskać więcej informacji, zobacz [Wypełnij](../standard-library/algorithm-functions.md#fill).

## <a name="fill_n-stlclr"></a><a name="fill_n"></a>fill_n (STL/CLR)

Przypisuje nową wartość do określonej liczby elementów w zakresie rozpoczynającym się od określonego elementu.

### <a name="syntax"></a>Składnia

```cpp
template<class _OutIt, class _Diff, class _Ty> inline
    void fill_n(_OutIt _First, _Diff _Count, const _Ty% _Val);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `fill_n`. Aby uzyskać więcej informacji, zobacz [fill_n](../standard-library/algorithm-functions.md#fill_n).

## <a name="find-stlclr"></a><a name="find"></a>Znajdź (STL/CLR)

Lokalizuje pozycję pierwszego wystąpienia elementu w zakresie, który ma określoną wartość.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt, class _Ty> inline
    _InIt find(_InIt _First, _InIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `find`. Aby uzyskać więcej informacji, zobacz [Znajdowanie](../standard-library/algorithm-functions.md#find).

## <a name="find_end-stlclr"></a><a name="find_end"></a>find_end (STL/CLR)

Wyszukuje w zakresie ostatnią podsekwencję, która jest identyczna z określoną sekwencją lub jest równoważna w sensie określonym przez predykat binarny.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2);
template<class _FwdIt1, class _FwdIt2, class _Pr> inline
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `find_end`. Aby uzyskać więcej informacji, zobacz [find_end](../standard-library/algorithm-functions.md#find_end).

## <a name="find_first_of-stlclr"></a><a name="find_first_of"></a>find_first_of (STL/CLR)

Wyszukuje pierwsze wystąpienie którejś z kilku wartości w zakresie docelowym lub pierwsze wystąpienie któregoś z kilku elementów, które są równoważne w sensie określonym przez predykat binarny dla określonego zestawu elementów.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2);
template<class _FwdIt1, class _FwdIt2, class _Pr> inline
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `find_first_of`. Aby uzyskać więcej informacji, zobacz [find_first_of](../standard-library/algorithm-functions.md#find_first_of).

## <a name="find_if-stlclr"></a><a name="find_if"></a>find_if (STL/CLR)

Lokalizuje pozycję pierwszego wystąpienia elementu w zakresie, który spełnia określony warunek.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt, class _Pr> inline
    _InIt find_if(_InIt _First, _InIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `find_if`. Aby uzyskać więcej informacji, zobacz [find_if](../standard-library/algorithm-functions.md#find_if).

## <a name="for_each-stlclr"></a><a name="for_each"></a>for_each (STL/CLR)

Stosuje określony obiekt funkcji do każdego elementu w kolejności do przodu w zakresie i zwraca obiekt funkcji.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt, class _Fn1> inline
    _Fn1 for_each(_InIt _First, _InIt _Last, _Fn1 _Func);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `for_each`. Aby uzyskać więcej informacji, zobacz [for_each](../standard-library/algorithm-functions.md#for_each).

## <a name="generate-stlclr"></a><a name="generate"></a>Generuj (STL/CLR)

Przypisuje wartości generowane przez obiekt funkcji do każdego elementu w zakresie.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt, class _Fn0> inline
    void generate(_FwdIt _First, _FwdIt _Last, _Fn0 _Func);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `generate`. Aby uzyskać więcej informacji, zobacz [generowanie](../standard-library/algorithm-functions.md#generate).

## <a name="generate_n-stlclr"></a><a name="generate_n"></a>generate_n (STL/CLR)

Przypisuje wartości generowane przez obiekt funkcji określonej liczbie elementów w zakresie i wraca do jednej pozycji poza ostatnią przypisaną wartością.

### <a name="syntax"></a>Składnia

```cpp
template<class _OutIt, class _Diff, class _Fn0> inline
    void generate_n(_OutIt _Dest, _Diff _Count, _Fn0 _Func);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `generate_n`. Aby uzyskać więcej informacji, zobacz [generate_n](../standard-library/algorithm-functions.md#generate_n).

## <a name="includes-stlclr"></a><a name="includes"></a>includes (STL/CLR)

Sprawdza, czy jeden posortowany zakres zawiera wszystkie elementy zawarte w drugim posortowanym zakresie, gdzie kryterium szeregowania lub równoważności między elementami może zostać określone przez predykat binarny.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt1, class _InIt2> inline
    bool includes(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2);
template<class _InIt1, class _InIt2, class _Pr> inline
    bool includes(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `includes`. Aby uzyskać więcej informacji, zobacz [zawiera](../standard-library/algorithm-functions.md#includes).

## <a name="inplace_merge-stlclr"></a><a name="inplace_merge"></a>inplace_merge (STL/CLR)

Łączy elementy z dwóch następujących po sobie posortowanych zakresów w pojedynczy posortowany zakres, gdzie kryterium szeregowania może być określone przez predykat binarny.

### <a name="syntax"></a>Składnia

```cpp
template<class _BidIt> inline
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last,
        _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `inplace_merge` Aby uzyskać więcej informacji, zobacz [inplace_merge](../standard-library/algorithm-functions.md#inplace_merge).

## <a name="iter_swap-stlclr"></a><a name="iter_swap"></a>iter_swap (STL/CLR)

Wymienia dwie wartości, do których odnosi się para określonych iteratorów.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    void iter_swap(_FwdIt1 _Left, _FwdIt2 _Right);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `iter_swap`. Aby uzyskać więcej informacji, zobacz [iter_swap](../standard-library/algorithm-functions.md#iter_swap).

## <a name="lexicographical_compare-stlclr"></a><a name="lexicographical_compare"></a>lexicographical_compare (STL/CLR)

Porównuje dwie sekwencje element po elemencie, aby określić, która z nich jest mniejsza.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt1, class _InIt2> inline
    bool lexicographical_compare(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2);
template<class _InIt1, class _InIt2, class _Pr> inline
    bool lexicographical_compare(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `lexicographical_compare`. Aby uzyskać więcej informacji, zobacz [lexicographical_compare](../standard-library/algorithm-functions.md#lexicographical_compare).

## <a name="lower_bound-stlclr"></a><a name="lower_bound"></a>lower_bound (STL/CLR)

Znajduje pozycję pierwszego elementu w uporządkowanym zakresie, który ma wartość mniejszą lub równą określonej wartości, gdzie kryterium sortowania może być określone przez Predykat binarny.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt, class _Ty> inline
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `lower_bound`. Aby uzyskać więcej informacji, zobacz [lower_bound](../standard-library/algorithm-functions.md#lower_bound).

## <a name="make_heap-stlclr"></a><a name="make_heap"></a>make_heap (STL/CLR)

Konwertuje elementy z określonego zakresu na stertę, w której pierwszy element jest największy i dla której kryterium sortowania może być określone przez predykat binarny.

### <a name="syntax"></a>Składnia

```cpp
template<class _RanIt> inline
    void make_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void make_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `make_heap`. Aby uzyskać więcej informacji, zobacz [make_heap](../standard-library/algorithm-functions.md#make_heap).

## <a name="max-stlclr"></a><a name="max"></a>Max (STL/CLR)

Porównuje dwa obiekty i zwraca większy z nich, gdzie kryterium sortowania może być określone przez predykat binarny.

### <a name="syntax"></a>Składnia

```cpp
template<class _Ty> inline
    const _Ty max(const _Ty% _Left, const _Ty% _Right);
template<class _Ty, class _Pr> inline
    const _Ty max(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `max`. Aby uzyskać więcej informacji, zobacz [Max](../standard-library/algorithm-functions.md#max).

## <a name="max_element-stlclr"></a><a name="max_element"></a>max_element (STL/CLR)

Znajduje pierwsze wystąpienie największego elementu w określonym zakresie, gdzie kryterium sortowania może być określone przez predykat binarny.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt> inline
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `max_element`. Aby uzyskać więcej informacji, zobacz [max_element](../standard-library/algorithm-functions.md#max_element).

## <a name="merge-stlclr"></a><a name="merge"></a>Scalanie (STL/CLR)

Łączy wszystkie elementy z dwóch następujących po sobie posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `merge`. Aby uzyskać więcej informacji, zobacz [scalanie](../standard-library/algorithm-functions.md#merge).

## <a name="min-stlclr"></a><a name="min"></a>min (STL/CLR)

Porównuje dwa obiekty i zwraca mniejszy z nich, gdzie kryterium sortowania może być określone przez predykat binarny.

### <a name="syntax"></a>Składnia

```cpp
template<class _Ty> inline
    const _Ty min(const _Ty% _Left, const _Ty% _Right);
template<class _Ty, class _Pr> inline
    const _Ty min(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `min`. Aby uzyskać więcej informacji, zobacz [min](../standard-library/algorithm-functions.md#min).

## <a name="min_element-stlclr"></a><a name="min_element"></a>min_element (STL/CLR)

Znajduje pierwsze wystąpienie najmniejszego elementu w określonym zakresie, gdzie kryterium sortowania może być określone przez predykat binarny.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt> inline
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `min_element`. Aby uzyskać więcej informacji, zobacz [min_element](../standard-library/algorithm-functions.md#min_element).

## <a name="mismatch-stlclr"></a><a name="mismatch"></a>niezgodność (STL/CLR)

Porównuje dwa zakresy element po elemencie pod względem równości lub odpowiedniości w sensie określonym przez predykat binarny i lokalizuje pierwsze miejsce, w którym występuje różnica.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt1, class _InIt2> inline
    _PAIR_TYPE(_InIt1)
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);
template<class _InIt1, class _InIt2, class _Pr> inline
    _PAIR_TYPE(_InIt1)
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
            _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `mismatch`. Aby uzyskać więcej informacji, zobacz [niezgodność](../standard-library/algorithm-functions.md#mismatch).

## <a name="next_permutation-stlclr"></a><a name="next_permutation"></a>next_permutation (STL/CLR)

Zmienia kolejność elementów w zakresie, tak że oryginalna kolejność jest zastąpiona przez leksykograficznie kolejną większą permutację, o ile takowa istnieje, gdzie sens „kolejna” może być określony przez predykat binarny.

### <a name="syntax"></a>Składnia

```cpp
template<class _BidIt> inline
    bool next_permutation(_BidIt _First, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    bool next_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `next_permutation`. Aby uzyskać więcej informacji, zobacz [next_permutation](../standard-library/algorithm-functions.md#next_permutation).

## <a name="nth_element-stlclr"></a><a name="nth_element"></a>nth_element (STL/CLR)

Dzieli zakres elementów przez poprawne lokalizowanie `n`tego elementu sekwencji w zakresie, tak aby wszystkie elementy przed nim były mniejsze lub równe, a wszystkie elementy, które podążają w sekwencji, są większe lub równe.

### <a name="syntax"></a>Składnia

```cpp
template<class _RanIt> inline
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last,
        _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `nth_element`. Aby uzyskać więcej informacji, zobacz [nth_element](../standard-library/algorithm-functions.md#nth_element).

## <a name="partial_sort-stlclr"></a><a name="partial_sort"></a>partial_sort (STL/CLR)

Rozmieszcza określoną liczbę mniejszych elementów w zakresie w niemalejącej kolejności, lub według kryteriów sortowania określonych przez binarny predykat.

### <a name="syntax"></a>Składnia

```cpp
template<class _RanIt> inline
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last,
        _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `partial_sort`. Aby uzyskać więcej informacji, zobacz [partial_sort](../standard-library/algorithm-functions.md#partial_sort).

## <a name="partial_sort_copy-stlclr"></a><a name="partial_sort_copy"></a>partial_sort_copy (STL/CLR)

Kopiuje elementy z zakresu źródłowego do zakresu docelowego, gdzie elementy źródłowe są uporządkowane według albo zasady mniejszy niż, albo innego określonego predykatu binarnego.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt, class _RanIt> inline
    _RanIt partial_sort_copy(_InIt _First1, _InIt _Last1,
        _RanIt _First2, _RanIt _Last2);
template<class _InIt, class _RanIt, class _Pr> inline
    _RanIt partial_sort_copy(_InIt _First1, _InIt _Last1,
        _RanIt _First2, _RanIt _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `partial_sort_copy`. Aby uzyskać więcej informacji, zobacz [partial_sort_copy](../standard-library/algorithm-functions.md#partial_sort_copy).

## <a name="partition-stlclr"></a><a name="partition"></a>partycja (STL/CLR)

Klasyfikuje elementy w zakresie na dwa rozłączne zestawy, z elementami spełniającymi predykat unarny poprzedzającymi te, które go nie spełniają.

### <a name="syntax"></a>Składnia

```cpp
template<class _BidIt, class _Pr> inline
    _BidIt partition(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `partition`. Aby uzyskać więcej informacji, zobacz [partycja](../standard-library/algorithm-functions.md#partition).

## <a name="pop_heap-stlclr"></a><a name="pop_heap"></a>pop_heap (STL/CLR)

Usuwa największy element z przodu sterty do przedostatniej pozycji w zakresie, a następnie tworzy nową stertę z pozostałych elementów.

### <a name="syntax"></a>Składnia

```cpp
template<class _RanIt> inline
    void pop_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void pop_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `pop_heap`. Aby uzyskać więcej informacji, zobacz [pop_heap](../standard-library/algorithm-functions.md#pop_heap).

## <a name="prev_permutation-stlclr"></a><a name="prev_permutation"></a>prev_permutation (STL/CLR)

Zmienia kolejność elementów w zakresie, tak że oryginalna kolejność jest zastąpiona przez leksykograficznie kolejną większą permutację, o ile takowa istnieje, gdzie sens „kolejna” może być określony przez predykat binarny.

### <a name="syntax"></a>Składnia

```cpp
template<class _BidIt> inline
    bool prev_permutation(_BidIt _First, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    bool prev_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `prev_permutation`. Aby uzyskać więcej informacji, zobacz [prev_permutation](../standard-library/algorithm-functions.md#prev_permutation).

## <a name="push_heap-stlclr"></a><a name="push_heap"></a>push_heap (STL/CLR)

Dodaje element znajdujący się na końcu zakresu do istniejącej sterty, która składa się z poprzednich elementów w zakresie.

### <a name="syntax"></a>Składnia

```cpp
template<class _RanIt> inline
    void push_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void push_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `push_heap`. Aby uzyskać więcej informacji, zobacz [push_heap](../standard-library/algorithm-functions.md#push_heap).

## <a name="random_shuffle-stlclr"></a><a name="random_shuffle"></a>random_shuffle (STL/CLR)

Zmienia kolejność `N` elementów w zakresie na jedną z `N`. możliwe rozwiązania wybrane losowo.

### <a name="syntax"></a>Składnia

```cpp
template<class _RanIt> inline
    void random_shuffle(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Fn1> inline
    void random_shuffle(_RanIt _First, _RanIt _Last, _Fn1% _Func);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `random_shuffle`. Aby uzyskać więcej informacji, zobacz [random_shuffle](../standard-library/algorithm-functions.md#random_shuffle).

## <a name="remove-stlclr"></a><a name="remove"></a>Usuń (STL/CLR)

Eliminuje określoną wartość z danego zakresu bez zakłócania kolejności pozostałych elementów i zwracania końca nowego zakresu wolnego od określonej wartości.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt, class _Ty> inline
    _FwdIt remove(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `remove`. Aby uzyskać więcej informacji, zobacz [Remove](../standard-library/algorithm-functions.md#remove).

## <a name="remove_copy-stlclr"></a><a name="remove_copy"></a>remove_copy (STL/CLR)

Kopiuje elementy z zakresu źródłowego do zakresu docelowego, z tym wyjątkiem, że elementy o określonej wartości nie są kopiowane, bez naruszania kolejności pozostałych elementów i zwracania końca nowego zakresu docelowego.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt, class _OutIt, class _Ty> inline
    _OutIt remove_copy(_InIt _First, _InIt _Last,
        _OutIt _Dest, const _Ty% _Val);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `remove_copy`. Aby uzyskać więcej informacji, zobacz [remove_copy](../standard-library/algorithm-functions.md#remove_copy).

## <a name="remove_copy_if-stlclr"></a><a name="remove_copy_if"></a>remove_copy_if (STL/CLR)

Kopiuje elementy z zakresu źródłowego do zakresu docelowego, z tym wyjątkiem, że elementy spełniające predykat nie są kopiowane, bez naruszania kolejności pozostałych elementów i zwracania końca nowego zakresu docelowego.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt, class _OutIt, class _Pr> inline
    _OutIt remove_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `remove_copy_if`. Aby uzyskać więcej informacji, zobacz [remove_copy_if](../standard-library/algorithm-functions.md#remove_copy_if).

## <a name="remove_if-stlclr"></a><a name="remove_if"></a>remove_if (STL/CLR)

Eliminuje elementy, które spełniają predykat, z danego zakresu bez zakłócania kolejności pozostałych elementów i zwracania końca nowego zakresu wolnego od określonej wartości.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt, class _Pr> inline
    _FwdIt remove_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `remove_if`. Aby uzyskać więcej informacji, zobacz [remove_if](../standard-library/algorithm-functions.md#remove_if).

## <a name="replace-stlclr"></a><a name="replace"></a>Replace (STL/CLR)

Sprawdza każdy element w zakresie i zastępuje go, jeśli odpowiada określonej wartości.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt, class _Ty> inline
    void replace(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Oldval, const _Ty% _Newval);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `replace`. Aby uzyskać więcej informacji, zobacz [Zastąp](../standard-library/algorithm-functions.md#replace).

## <a name="replace_copy-stlclr"></a><a name="replace_copy"></a>replace_copy (STL/CLR)

Sprawdza każdy element w zakresie źródłowym i zastępuje go, jeśli odpowiada określonej wartości, jednocześnie kopiując wynik do nowego zakresu docelowego.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt, class _OutIt, class _Ty> inline
    _OutIt replace_copy(_InIt _First, _InIt _Last, _OutIt _Dest,
        const _Ty% _Oldval, const _Ty% _Newval);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `replace_copy`. Aby uzyskać więcej informacji, zobacz [replace_copy](../standard-library/algorithm-functions.md#replace_copy).

## <a name="replace_copy_if-stlclr"></a><a name="replace_copy_if"></a>replace_copy_if (STL/CLR)

Sprawdza każdy element w zakresie źródłowym i zastępuje go, jeśli spełnia określony predykat, jednocześnie kopiując wynik do nowego zakresu docelowego.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt, class _OutIt, class _Pr, class _Ty> inline
    _OutIt replace_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Pr _Pred, const _Ty% _Val);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `replace_copy_if`. Aby uzyskać więcej informacji, zobacz [replace_copy_if](../standard-library/algorithm-functions.md#replace_copy_if).

## <a name="replace_if-stlclr"></a><a name="replace_if"></a>replace_if (STL/CLR)

Sprawdza każdy element w zakresie i zastępuje go, jeśli spełnia określony predykat.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt, class _Pr, class _Ty> inline
    void replace_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred,
        const _Ty% _Val);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `replace_if`. Aby uzyskać więcej informacji, zobacz [replace_if](../standard-library/algorithm-functions.md#replace_if).

## <a name="reverse-stlclr"></a><a name="reverse"></a>Odwróć (STL/CLR)

Odwraca kolejność elementów w obrębie zakresu.

### <a name="syntax"></a>Składnia

```cpp
template<class _BidIt> inline
    void reverse(_BidIt _First, _BidIt _Last);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `reverse`. Aby uzyskać więcej informacji, zobacz [odwracanie](../standard-library/algorithm-functions.md#reverse).

## <a name="reverse_copy-stlclr"></a><a name="reverse_copy"></a>reverse_copy (STL/CLR)

Odwraca kolejność elementów w zakresie źródłowym, kopiując je do zakresu docelowego.

### <a name="syntax"></a>Składnia

```cpp
template<class _BidIt, class _OutIt> inline
    _OutIt reverse_copy(_BidIt _First, _BidIt _Last, _OutIt _Dest);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `reverse_copy`. Aby uzyskać więcej informacji, zobacz [reverse_copy](../standard-library/algorithm-functions.md#reverse_copy).

## <a name="rotate-stlclr"></a><a name="rotate"></a>Obróć (STL/CLR)

Wymienia elementy znajdujące się w dwóch sąsiednich zakresach.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt> inline
    void rotate(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `rotate`. Aby uzyskać więcej informacji, zobacz [Obróć](../standard-library/algorithm-functions.md#rotate).

## <a name="rotate_copy-stlclr"></a><a name="rotate_copy"></a>rotate_copy (STL/CLR)

Wymienia elementy w dwóch sąsiednich zakresach w ramach zakresu źródłowego i kopiuje wynik do zakresu docelowego.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt, class _OutIt> inline
    _OutIt rotate_copy(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last,
        _OutIt _Dest);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `rotate_copy`. Aby uzyskać więcej informacji, zobacz [rotate_copy](../standard-library/algorithm-functions.md#rotate_copy).

## <a name="search-stlclr"></a><a name="search_"></a>Wyszukaj (STL/CLR)

Wyszukuje pierwsze wystąpienie sekwencji w zakresie docelowym, której elementy są równe tym w danej sekwencji elementów lub której elementy są równoważne w sensie określonym przez predykat binarny dla elementów w danej sekwencji.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2);
template<class _FwdIt1, class _FwdIt2, class _Pr> inline
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `search`. Aby uzyskać więcej informacji, zobacz [Wyszukiwanie](../standard-library/algorithm-functions.md#search).

## <a name="search_n-stlclr"></a><a name="search_n"></a>search_n (STL/CLR)

Wyszukuje pierwszą podsekwencję w zakresie, w której określona liczba elementów ma określoną wartość lub relację do tej wartości określoną przez predykat binarny.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt1, class _Diff2, class _Ty> inline
    _FwdIt1 search_n(_FwdIt1 _First1, _FwdIt1 _Last1,
        _Diff2 _Count, const _Ty& _Val);
template<class _FwdIt1, class _Diff2, class _Ty, class _Pr> inline
    _FwdIt1 search_n(_FwdIt1 _First1, _FwdIt1 _Last1,
        _Diff2 _Count, const _Ty& _Val, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `search_n`. Aby uzyskać więcej informacji, zobacz [search_n](../standard-library/algorithm-functions.md#search_n).

## <a name="set_difference-stlclr"></a><a name="set_difference"></a>set_difference (STL/CLR)

Łączy w sobie wszystkie elementy, które należą do jednego posortowanego zakresu źródłowego, ale nie do drugiego posortowanego zakresu źródłowego, w pojedynczy, posortowany zakres docelowy, gdzie kryterium sortowania może być określone przez predykat binarny.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2,_OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `set_difference`. Aby uzyskać więcej informacji, zobacz [set_difference](../standard-library/algorithm-functions.md#set_difference).

## <a name="set_intersection-stlclr"></a><a name="set_intersection"></a>set_intersection (STL/CLR)

Łączy w sobie wszystkie elementy, które należą do obu posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `set_intersection`. Aby uzyskać więcej informacji, zobacz [set_intersection](../standard-library/algorithm-functions.md#set_intersection).

## <a name="set_symmetric_difference-stlclr"></a><a name="set_symmetric_difference"></a>set_symmetric_difference (STL/CLR)

Łączy w sobie wszystkie elementy, które należą do jednego z, ale nie obu posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_symmetric_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_symmetric_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `set_symmetric_difference`. Aby uzyskać więcej informacji, zobacz [set_symmetric_difference](../standard-library/algorithm-functions.md#set_symmetric_difference).

## <a name="set_union-stlclr"></a><a name="set_union"></a>set_union (STL/CLR)

Łączy w sobie wszystkie elementy, które należą do przynajmniej jednego z dwóch posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_union(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_union(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `set_union`. Aby uzyskać więcej informacji, zobacz [set_union](../standard-library/algorithm-functions.md#set_union).

## <a name="sort-stlclr"></a><a name="sort"></a>Sort (STL/CLR)

Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryteriów sortowania określonych przez binarny predykat.

### <a name="syntax"></a>Składnia

```cpp
template<class _RanIt> inline
    void sort(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void sort(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `sort`. Aby uzyskać więcej informacji, zobacz [sort](../mfc/reference/cmfclistctrl-class.md#sort).

## <a name="sort_heap-stlclr"></a><a name="sort_heap"></a>sort_heap (STL/CLR)

Konwertuje stertę na sortowany zakres.

### <a name="syntax"></a>Składnia

```cpp
template<class _RanIt> inline
    void sort_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void sort_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `sort_heap`. Aby uzyskać więcej informacji, zobacz [sort_heap](../standard-library/algorithm-functions.md#sort_heap).

## <a name="stable_partition-stlclr"></a><a name="stable_partition"></a>stable_partition (STL/CLR)

Klasyfikuje elementy w zakresie na dwa rozłączne zestawy, z elementami spełniającymi predykat unarny poprzedzającymi te, które go nie spełniają, zachowując względną kolejność elementów równoważnych.

### <a name="syntax"></a>Składnia

```cpp
template<class _BidIt, class _Pr> inline
    _BidIt stable_partition(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `stable_partition`. Aby uzyskać więcej informacji, zobacz [stable_partition](../standard-library/algorithm-functions.md#stable_partition).

## <a name="stable_sort-stlclr"></a><a name="stable_sort"></a>stable_sort (STL/CLR)

Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryterium sortowania określonego przez binarny predykat i zachowuje względną kolejność elementów równoważnych.

### <a name="syntax"></a>Składnia

```cpp
template<class _BidIt> inline
    void stable_sort(_BidIt _First, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    void stable_sort(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `stable_sort`. Aby uzyskać więcej informacji, zobacz [stable_sort](../standard-library/algorithm-functions.md#stable_sort).

## <a name="swap-stlclr"></a><a name="swap"></a>swap (STL/CLR)

Wymienia wartości elementów między dwoma typami obiektów, przypisując zawartość pierwszego obiektu do drugiego obiektu, a zawartość drugiego do pierwszego.

### <a name="syntax"></a>Składnia

```cpp
<class _Ty> inline
    void swap(_Ty% _Left, _Ty% _Right);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `swap`. Aby uzyskać więcej informacji, zobacz [swap](../standard-library/algorithm-functions.md#swap).

## <a name="swap_ranges-stlclr"></a><a name="swap_ranges"></a>swap_ranges (STL/CLR)

Zamienia elementy jednego zakresu przez elementy innego zakresu, zakresy mają równe wielkości.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt2 swap_ranges(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `swap_ranges`. Aby uzyskać więcej informacji, zobacz [swap_ranges](../standard-library/algorithm-functions.md#swap_ranges).

## <a name="transform-stlclr"></a><a name="transform"></a>transformacja (STL/CLR)

Stosuje określony obiekt funkcji dla każdego elementu w zakresie sortowania lub dla pary elementów z dwóch zakresów sortowania i kopiuje zwracane wartości obiektu funkcji do zakresu docelowego.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt, class _OutIt, class _Fn1> inline
    _OutIt transform(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Fn1 _Func);
template<class _InIt1, class _InIt2, class _OutIt, class _Fn2> inline
    _OutIt transform(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `transform`. Aby uzyskać więcej informacji, zobacz [transformacja](../standard-library/algorithm-functions.md#transform).

## <a name="unique-stlclr"></a><a name="unique"></a>unikatowy (STL/CLR)

Usuwa zduplikowane elementy, które sąsiadują ze sobą w określonym zakresie.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt> inline
    _FwdIt unique(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt unique(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `unique`. Aby uzyskać więcej informacji, zobacz [unikatowy](../standard-library/algorithm-functions.md#unique).

## <a name="unique_copy-stlclr"></a><a name="unique_copy"></a>unique_copy (STL/CLR)

Kopiuje elementy z zakresu źródłowego do zakresu docelowego z wyjątkiem zduplikowanych elementów, które ze sobą sąsiadują.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest);
template<class _InIt, class _OutIt, class _Pr> inline
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `unique_copy`. Aby uzyskać więcej informacji, zobacz [unique_copy](../standard-library/algorithm-functions.md#unique_copy).

## <a name="upper_bound-stlclr"></a><a name="upper_bound"></a>upper_bound (STL/CLR)

Znajduje pozycję pierwszego elementu w uporządkowanym zakresie, który ma wartość większą niż określona wartość, gdzie kryterium sortowania może być określone przez predykat binarny.

### <a name="syntax"></a>Składnia

```cpp
template<class _FwdIt, class _Ty> inline
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak C++ standardowa funkcja biblioteki `upper_bound`. Aby uzyskać więcej informacji, zobacz [upper_bound](../standard-library/algorithm-functions.md#upper_bound).
