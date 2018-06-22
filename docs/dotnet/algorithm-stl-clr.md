---
title: Algorytm (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 71399d254b2b47b33959695a00227e316c04a008
ms.sourcegitcommit: 301bb19056e5bae84ff50f7d1df1e546efe225ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2018
ms.locfileid: "36305803"
---
# <a name="algorithm-stlclr"></a>algorithm (STL/CLR)
Definiuje funkcje szablonu kontenera STL/CLR, wykonujących algorytmów.  
  
## <a name="syntax"></a>Składnia  
  
```  
#include <cliext/algorithm>  
```  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/algorytm >  
  
 **Namespace:** cliext  
    
## <a name="functions"></a>Funkcje  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[adjacent_find (STL/CLR)](#adjacent_find)|Wyszukuje dwóch sąsiadujących ze sobą elementów, które są takie same.|  
|[binary_search (STL/CLR)](#binary_search)|Sprawdza, czy sortowane sekwencja zawiera podanej wartości.|  
|[copy (STL/CLR)](#copy)|Kopiuje wartości z zakresu źródła docelowy zakres iteracja w kierunku do przodu.|  
|[copy_backward (STL/CLR)](#copy_backward)|Kopiuje wartości z zakresu źródła docelowy zakres iteracja w kierunku do tyłu.|  
|[count (STL/CLR)](#count)|Zwraca liczbę elementów w zakresie, których wartości pasują do określonej wartości.|  
|[count_if (STL/CLR)](#count_if)|Zwraca liczbę elementów w zakresie, których wartości pasują do określonego warunku.|  
|[equal (STL/CLR)](#equal)|Porównuje dwa zakresy, elementów.|  
|[equal_range (STL/CLR)](#equal_range)|Wyszukuje uporządkowana sekwencja wartości i zwraca dwie pozycje ograniczających podsekwencji wartości, które są równe do danego elementu.|  
|[fill (STL/CLR)](#fill)|Przypisuje tę samą nową wartość każdemu elementowi w określonym zakresie.|  
|[fill_n (STL/CLR)](#fill_n)|Przypisuje nową wartość do określonej liczby elementów na początku zakresu z określonym elementem.|  
|[find (STL/CLR)](#find)|Zwraca pozycję pierwszego wystąpienia określonej wartości.|  
|[find_end (STL/CLR)](#find_end)|Zwraca ostatni podsekwencji zakresu, który jest taka sama jak określona sekwencja.|  
|[find_first_of (STL/CLR)](#find_first_of)|Wyszukuje zakresu dla pierwszego wystąpienia jednego z danego zakresu elementów.|  
|[find_if (STL/CLR)](#find_if)|Zwraca pozycję pierwszego elementu w sekwencji wartości, jeśli element spełnia określony warunek.|  
|[for_each (STL/CLR)](#for_each)|Stosuje obiektu o określonej funkcji do każdego elementu w sekwencji wartości i zwraca obiekt funkcji.|  
|[generate (STL/CLR)](#generate)|Przypisuje wartości generowanych przez obiekt funkcji do każdego elementu w sekwencji wartości.|  
|[generate_n (STL/CLR)](#generate_n)|Przypisuje wartości generowanych przez obiekt funkcji do określonej liczby elementów.|  
|[includes (STL/CLR)](#includes)|Sprawdza, czy jeden zakres posortowane zawiera wszystkie elementy w drugiego zakresu posortowane.|  
|[inplace_merge (STL/CLR)](#inplace_merge)|Łączy elementy z dwóch kolejnych zakresów posortowane w jednym zakresem posortowane.|  
|[iter_swap (STL/CLR)](#iter_swap)|Wymienia dwie wartości, do których odnosi się para określonych iteratorów.|  
|[lexicographical_compare (STL/CLR)](#lexicographical_compare)|Porównuje dwie sekwencje, elementów, identyfikowanie, które sekwencja jest mniejszy z dwóch.|  
|[lower_bound (STL/CLR)](#lower_bound)|Odnajduje położenie pierwszego elementu w uporządkowanej kolejności wartości ma wartość większa niż lub równa określonej wartości.|  
|[make_heap (STL/CLR)](#make_heap)|Konwertuje sterty, gdzie pierwszy element na stosie jest największy elementy z określonego zakresu.|  
|[MAX (STL/CLR)](#max))|Porównuje dwa obiekty i zwraca większa niż dwa.|  
|[max_element (STL/CLR)](#max_element)|Wyszukuje największy element w kolejności określonej wartości.|  
|[merge (STL/CLR)](#merge))|Łączy wszystkie elementy z dwóch posortowane zakresów w zasięgu pojedynczego, posortowane docelowym.|  
|[min (STL/CLR)](#min)|Porównuje dwa obiekty i zwraca mniejszy z dwóch.|  
|[min_element (STL/CLR)](#min_element)|Wyszukuje najmniejszy element w kolejności określonej wartości.|  
|[mismatch (STL/CLR)](#mismatch)|Porównuje dwa zakresy elementów i zwraca pierwszą pozycję, gdzie występuje różnica.|  
|[next_permutation (STL/CLR)](#next_permutation)|Zmienia kolejność elementów w zakresie, dzięki czemu oryginalnego kolejność zostało zastąpione przez lexicographically dalej permutacji większa, jeśli istnieje.|  
|[nth_element (STL/CLR)](#nth_element)|Partycje sekwencję elementów poprawnie lokalizowanie `n`element th sekwencji, aby wszystkie elementy przed nim mniejsza lub równa i wszystkie elementy, których przestrzeganie są większe niż lub równą jej.|  
|[partial_sort (STL/CLR)](#partial_sort)|Rozmieszcza określoną liczbę mniejsze elementy w zakresie nondescending kolejności.|  
|[partial_sort_copy (STL/CLR)](#partial_sort_copy)|Kopiuje elementy z zakresu źródła do zakresu docelowego taki sposób, że elementy z zakresu źródła są uporządkowane.|  
|[partition (STL/CLR)](#partition)|Rozmieszcza elementy w zakresie w taki sposób, że te elementy, które spełniają predykat jednoargumentowy poprzedzać te, które nie spełniają jej.|  
|[pop_heap (STL/CLR)](#pop_heap)|Przenosi największy element z przodu sterty na końcu i następnie tworzy nowy sterty od pozostałych elementów.|  
|[prev_permutation (STL/CLR)](#prev_permutation)|Zmienia kolejność sekwencję elementów, dzięki czemu oryginalnego kolejność zostało zastąpione przez lexicographically poprzedniego permutacji większa, jeśli istnieje.|  
|[push_heap (STL/CLR)](#push_heap)|Dodaje element znajdujący się na końcu zakresu do istniejącej sterty, która składa się z poprzednich elementów w zakresie.|  
|[random_shuffle (STL/CLR)](#random_shuffle)|Rozmieszcza sekwencji `N` elementy w zakresie do jednego z `N`! możliwości ustalenia losowo wybrany.|  
|[remove (STL/CLR)](#remove)|Usuwa określoną wartość z danego zakresu bez zakłócania kolejność pozostałych elementów i zwraca koniec nowy zakres wolne od określonej wartości.|  
|[remove_copy (STL/CLR)](#remove_copy)|Kopiuje elementy z zakresu źródła do zakresu docelowego z tą różnicą, że nie są kopiowane elementy określoną wartość, bez zakłócania kolejność pozostałych elementów.|  
|[remove_copy_if (STL/CLR)](#remove_copy_if)|Kopiuje elementy z zakresu źródła zakres docelowy, z wyjątkiem tych, które spełniają predykatu, bez zakłócania kolejność pozostałych elementów.|  
|[remove_if (STL/CLR)](#remove_if)|Usuwa elementy, które spełniają predykat z danego zakresu bez zakłócania kolejność pozostałych elementów. .|  
|[replace (STL/CLR)](#replace)|Zastępuje elementy w zakresie zgodne z określoną wartość z nową wartością.|  
|[replace_copy (STL/CLR)](#replace_copy)|Kopiuje elementy z zakresu źródła zakresu docelowego, zastępując elementy, które pasują do określonej wartości z nową wartością.|  
|[replace_copy_if (STL/CLR)](#replace_copy_if)|Sprawdza każdy element w zakresie źródłowym i zastępuje go, jeśli spełnia określony predykat, jednocześnie kopiując wynik do nowego zakresu docelowego.|  
|[replace_if (STL/CLR)](#replace_if)|Sprawdza każdy element w zakresie i zastępuje go, jeśli spełnia określony predykat.|  
|[reverse (STL/CLR)](#reverse)|Odwraca kolejność elementów w obrębie zakresu.|  
|[reverse_copy (STL/CLR)](#reverse_copy)|Odwraca kolejność elementów w zakresie źródła podczas kopiowania ich do zakresu docelowego.|  
|[rotate (STL/CLR)](#rotate)|Wymienia elementy znajdujące się w dwóch sąsiednich zakresach.|  
|[rotate_copy (STL/CLR)](#rotate_copy)|Wymienia elementy w dwóch sąsiednich zakresach w ramach zakresu źródłowego i kopiuje wynik do zakresu docelowego.|  
|[search (STL/CLR)](#search_)|Wyszukuje pierwsze wystąpienie sekwencji w zakresie docelowym, której elementy są równe tym w danej sekwencji elementów lub której elementy są równoważne w sensie określonym przez predykat binarny dla elementów w danej sekwencji.|  
|[search_n (STL/CLR)](#search_n)|Wyszukuje pierwszą podsekwencję w zakresie, w której określona liczba elementów ma określoną wartość lub relację do tej wartości określoną przez predykat binarny.|  
|[set_difference (STL/CLR)](#set_difference)|Łączy w sobie wszystkie elementy, które należą do jednego posortowanego zakresu źródłowego, ale nie do drugiego posortowanego zakresu źródłowego, w pojedynczy, posortowany zakres docelowy, gdzie kryterium sortowania może być określone przez predykat binarny.|  
|[set_intersection (STL/CLR)](#set_intersection)|Łączy w sobie wszystkie elementy, które należą do obu posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.|  
|[set_symmetric_difference (STL/CLR)](#set_symmetric_difference)|Łączy w sobie wszystkie elementy, które należą do jednego z, ale nie obu posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.|  
|[set_union — (STL/CLR)](#set_union))|Łączy w sobie wszystkie elementy, które należą do przynajmniej jednego z dwóch posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.|  
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
 

## <a name="adjacent_find"></a> adjacent_find — (STL/CLR)
Wyszukuje dwa sąsiadujące elementy, które są równe lub spełniają określony warunek.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt> inline  
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last);  
template<class _FwdIt, class _Pr> inline  
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `adjacent_find`. Aby uzyskać więcej informacji, zobacz [adjacent_find —](../standard-library/algorithm-functions.md#adjacent_find).

## <a name="binary_search"></a> binary_search — (STL/CLR)
Testuje, czy w sortowanym zakresie istnieje element, który jest równy określonej wartości lub który jest odpowiednikiem w sensie określonym przez predykat binarny.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt, class _Ty> inline  
    bool binary_search(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    bool binary_search(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `binary_search`. Aby uzyskać więcej informacji, zobacz [binary_search —](../standard-library/algorithm-functions.md#binary_search).  
  
## <a name="copy"></a> Kopiowanie (STL/CLR)
Przypisuje wartości elementów z zakresu źródłowego do zakresu docelowego, iterując przez sekwencję źródłową elementów oraz przypisując im nowe pozycje w kierunku do przodu.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt copy(_InIt _First, _InIt _Last, _OutIt _Dest);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `copy`. Aby uzyskać więcej informacji, zobacz [kopiowania](http://msdn.microsoft.com/Library/f1fec7da-e01b-40f1-b5bd-6b81e304cae1). 

## <a name="copy_backward"></a> copy_backward — (STL/CLR)
Przypisuje wartości elementów z zakresu źródłowego do zakresu docelowego, iterując przez sekwencję źródłową elementów oraz przypisując im nowe pozycje w kierunku do tyłu.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _BidIt1, class _BidIt2> inline  
    _BidIt2 copy_backward(_BidIt1 _First, _BidIt1 _Last,  
        _BidIt2 _Dest);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `copy_backward`. Aby uzyskać więcej informacji, zobacz [copy_backward —](../standard-library/algorithm-functions.md#copy_backward).  

## <a name="count"></a> Count (STL/CLR)
Zwraca liczbę elementów w zakresie, których wartości pasują do określonej wartości.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt, class _Ty> inline  
    typename iterator_traits<_InIt>::difference_type  
        count(_InIt _First, _InIt _Last, const _Ty% _Val);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `count`. Aby uzyskać więcej informacji, zobacz [liczba](../standard-library/algorithm-functions.md#count). 

## <a name="count_if"></a> count_if (STL/CLR)
Zwraca liczbę elementów w zakresie, których wartości pasują do określonego warunku.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt, class _Pr> inline  
    typename iterator_traits<_InIt>::difference_type  
        count_if(_InIt _First, _InIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `count_if`. Aby uzyskać więcej informacji, zobacz [count_if](../standard-library/algorithm-functions.md#count_if).  
  
## <a name="equal"></a> równości (STL/CLR)
Porównuje dwa zakresy element po elemencie, pod względem równości lub równoważności w sensie określonym przez predykat binarny.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt1, class _InIt2> inline  
    bool equal(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);  
template<class _InIt1, class _InIt2, class _Pr> inline  
    bool equal(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
        _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `equal`. Aby uzyskać więcej informacji, zobacz [równy](../standard-library/algorithm-functions.md#equal).  

## <a name="equal_range"></a> equal_range (STL/CLR)
Wyszukuje parę pozycji w uporządkowanym zakresie, pierwszą mniejszą lub równoważną położeniu określonego elementu, a drugą większą niż pozycja elementu, gdzie sens równoważności lub szeregowania używany do ustanawiania pozycji w sekwencji może zostać określony przez predykat binarny.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt, class _Ty> inline  
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `equal_range`. Aby uzyskać więcej informacji, zobacz [equal_range](../standard-library/algorithm-functions.md#equal_range).  

## <a name="fill"></a> Fill (STL/CLR)
Przypisuje tę samą nową wartość każdemu elementowi w określonym zakresie.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt, class _Ty> inline  
    void fill(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `fill`. Aby uzyskać więcej informacji, zobacz [wypełnienia](../standard-library/algorithm-functions.md#fill). 

## <a name="fill_n"></a> fill_n (STL/CLR)
Przypisuje nową wartość do określonej liczby elementów na początku zakresu z określonym elementem.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _OutIt, class _Diff, class _Ty> inline  
    void fill_n(_OutIt _First, _Diff _Count, const _Ty% _Val);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `fill_n`. Aby uzyskać więcej informacji, zobacz [fill_n](../standard-library/algorithm-functions.md#fill_n).  

## <a name="find"></a> Find (STL/CLR)
Lokalizuje pozycję pierwszego wystąpienia elementu w zakresie, który ma określoną wartość.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt, class _Ty> inline  
    _InIt find(_InIt _First, _InIt _Last, const _Ty% _Val);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `find`. Aby uzyskać więcej informacji, zobacz [znaleźć](../standard-library/algorithm-functions.md#find). 

## <a name="find_end"></a> find_end — (STL/CLR)
Wyszukuje w zakresie ostatnią podsekwencję, która jest identyczna z określoną sekwencją lub jest równoważna w sensie określonym przez predykat binarny.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt1, class _FwdIt2> inline  
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2);  
template<class _FwdIt1, class _FwdIt2, class _Pr> inline  
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `find_end`. Aby uzyskać więcej informacji, zobacz [find_end —](../standard-library/algorithm-functions.md#find_end).  

## <a name="find_first_of"></a> find_first_of — (STL/CLR)
Wyszukuje pierwsze wystąpienie którejś z kilku wartości w zakresie docelowym lub pierwsze wystąpienie któregoś z kilku elementów, które są równoważne w sensie określonym przez predykat binarny dla określonego zestawu elementów.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt1, class _FwdIt2> inline  
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2);  
template<class _FwdIt1, class _FwdIt2, class _Pr> inline  
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `find_first_of`. Aby uzyskać więcej informacji, zobacz [find_first_of](../standard-library/algorithm-functions.md#find_first_of).  

## <a name="find_if"></a> find_if (STL/CLR)
Lokalizuje pozycję pierwszego wystąpienia elementu w zakresie, który spełnia określony warunek.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt, class _Pr> inline  
    _InIt find_if(_InIt _First, _InIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `find_if`. Aby uzyskać więcej informacji, zobacz [find_if](../standard-library/algorithm-functions.md#find_if). 

## <a name="for_each"></a> for_each (STL/CLR)
Stosuje określony obiekt funkcji do każdego elementu w kolejności do przodu w zakresie i zwraca obiekt funkcji.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt, class _Fn1> inline  
    _Fn1 for_each(_InIt _First, _InIt _Last, _Fn1 _Func);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `for_each`. Aby uzyskać więcej informacji, zobacz [for_each](../standard-library/algorithm-functions.md#for_each).  

## <a name="generate"></a> Generowanie (STL/CLR)
Przypisuje wartości generowane przez obiekt funkcji do każdego elementu w zakresie.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt, class _Fn0> inline  
    void generate(_FwdIt _First, _FwdIt _Last, _Fn0 _Func);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `generate`. Aby uzyskać więcej informacji, zobacz [Generowanie](../standard-library/algorithm-functions.md#generate).  

## <a name="generate_n"></a> generate_n (STL/CLR)
Przypisuje wartości generowane przez obiekt funkcji określonej liczbie elementów w zakresie i wraca do jednej pozycji poza ostatnią przypisaną wartością.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _OutIt, class _Diff, class _Fn0> inline  
    void generate_n(_OutIt _Dest, _Diff _Count, _Fn0 _Func);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `generate_n`. Aby uzyskać więcej informacji, zobacz [generate_n](../standard-library/algorithm-functions.md#generate_n).  
 
## <a name="includes"></a> obejmuje (STL/CLR)
Sprawdza, czy jeden posortowany zakres zawiera wszystkie elementy zawarte w drugim posortowanym zakresie, gdzie kryterium szeregowania lub równoważności między elementami może zostać określone przez predykat binarny.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt1, class _InIt2> inline  
    bool includes(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2);  
template<class _InIt1, class _InIt2, class _Pr> inline  
    bool includes(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `includes`. Aby uzyskać więcej informacji, zobacz [obejmuje](../standard-library/algorithm-functions.md#includes).  

## <a name="inplace_merge"></a> inplace_merge — (STL/CLR)
Łączy elementy z dwóch następujących po sobie posortowanych zakresów w pojedynczy posortowany zakres, gdzie kryterium szeregowania może być określone przez predykat binarny.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _BidIt> inline  
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last);  
template<class _BidIt, class _Pr> inline  
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last,  
        _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `inplace_merge` uzyskać więcej informacji, zobacz [inplace_merge —](../standard-library/algorithm-functions.md#inplace_merge).  
  
## <a name="iter_swap"></a> iter_swap — (STL/CLR)
Wymienia dwie wartości, do których odnosi się para określonych iteratorów.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt1, class _FwdIt2> inline  
    void iter_swap(_FwdIt1 _Left, _FwdIt2 _Right);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `iter_swap`. Aby uzyskać więcej informacji, zobacz [iter_swap —](../standard-library/algorithm-functions.md#iter_swap).  

## <a name="lexicographical_compare"></a> lexicographical_compare — (STL/CLR)
Porównuje dwie sekwencje element po elemencie, aby określić, która z nich jest mniejsza.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt1, class _InIt2> inline  
    bool lexicographical_compare(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2);  
template<class _InIt1, class _InIt2, class _Pr> inline  
    bool lexicographical_compare(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `lexicographical_compare`. Aby uzyskać więcej informacji, zobacz [lexicographical_compare —](../standard-library/algorithm-functions.md#lexicographical_compare).  

## <a name="lower_bound"></a> lower_bound (STL/CLR)
Znajduje położenie pierwszego elementu w uporządkowanego, który ma wartość mniejszą lub równoważnego określoną wartość, której można określić kryterium porządkowania binarne predykat.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt, class _Ty> inline  
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `lower_bound`. Aby uzyskać więcej informacji, zobacz [lower_bound](../standard-library/algorithm-functions.md#lower_bound).  

## <a name="make_heap"></a> make_heap — (STL/CLR)
Konwertuje elementy z określonego zakresu na stertę, w której pierwszy element jest największy i dla której kryterium sortowania może być określone przez predykat binarny.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _RanIt> inline  
    void make_heap(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void make_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `make_heap`. Aby uzyskać więcej informacji, zobacz [make_heap —](../standard-library/algorithm-functions.md#make_heap).  
  
## <a name="max"></a> MAX (STL/CLR)
Porównuje dwa obiekty i zwraca większy z nich, gdzie kryterium sortowania może być określone przez predykat binarny.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _Ty> inline  
    const _Ty max(const _Ty% _Left, const _Ty% _Right);  
template<class _Ty, class _Pr> inline  
    const _Ty max(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `max`. Aby uzyskać więcej informacji, zobacz [max](../standard-library/algorithm-functions.md#max).  

## <a name="max_element"></a> max_element (STL/CLR)
Znajduje pierwsze wystąpienie największego elementu w określonym zakresie, gdzie kryterium sortowania może być określone przez predykat binarny.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt> inline  
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last);  
template<class _FwdIt, class _Pr> inline  
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `max_element`. Aby uzyskać więcej informacji, zobacz [max_element](../standard-library/algorithm-functions.md#max_element).  

## <a name="merge"></a> merge (STL/CLR)
Łączy wszystkie elementy z dwóch następujących po sobie posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt1, class _InIt2, class _OutIt> inline  
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);  
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline  
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `merge`. Aby uzyskać więcej informacji, zobacz [scalania](../standard-library/algorithm-functions.md#merge).  

## <a name="min"></a> min (STL/CLR)
Porównuje dwa obiekty i zwraca mniejszy z nich, gdzie kryterium sortowania może być określone przez predykat binarny.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _Ty> inline  
    const _Ty min(const _Ty% _Left, const _Ty% _Right);  
template<class _Ty, class _Pr> inline  
    const _Ty min(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `min`. Aby uzyskać więcej informacji, zobacz [min](../standard-library/algorithm-functions.md#min).  

## <a name="min_element"></a> min_element (STL/CLR)
Znajduje pierwsze wystąpienie najmniejszego elementu w określonym zakresie, gdzie kryterium sortowania może być określone przez predykat binarny.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt> inline  
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last);  
template<class _FwdIt, class _Pr> inline  
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `min_element`. Aby uzyskać więcej informacji, zobacz [min_element](../standard-library/algorithm-functions.md#min_element).  
  
## <a name="mismatch"></a> Niezgodność (STL/CLR)
Porównuje dwa zakresy element po elemencie pod względem równości lub odpowiedniości w sensie określonym przez predykat binarny i lokalizuje pierwsze miejsce, w którym występuje różnica.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt1, class _InIt2> inline  
    _PAIR_TYPE(_InIt1)  
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);  
template<class _InIt1, class _InIt2, class _Pr> inline  
    _PAIR_TYPE(_InIt1)  
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
            _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `mismatch`. Aby uzyskać więcej informacji, zobacz [niezgodność](../standard-library/algorithm-functions.md#mismatch).  

## <a name="next_permutation"></a> next_permutation (STL/CLR)
Zmienia kolejność elementów w zakresie, tak że oryginalna kolejność jest zastąpiona przez leksykograficznie kolejną większą permutację, o ile takowa istnieje, gdzie sens „kolejna” może być określony przez predykat binarny.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _BidIt> inline  
    bool next_permutation(_BidIt _First, _BidIt _Last);  
template<class _BidIt, class _Pr> inline  
    bool next_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `next_permutation`. Aby uzyskać więcej informacji, zobacz [next_permutation](../standard-library/algorithm-functions.md#next_permutation).  
  
## <a name="nth_element"></a> nth_element (STL/CLR)
Partycje zakresu elementów poprawnie lokalizowanie `n`element th sekwencji w zakresie tak, aby wszystkie elementy przed nim są mniejsze niż lub równe go i wszystkie elementy, które po nim w sekwencji są większe niż lub równą jej.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _RanIt> inline  
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last,  
        _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `nth_element`. Aby uzyskać więcej informacji, zobacz [nth_element](../standard-library/algorithm-functions.md#nth_element).  

## <a name="partial_sort"></a> partial_sort (STL/CLR)
Rozmieszcza określoną liczbę mniejszych elementów w zakresie w niemalejącej kolejności, lub według kryteriów sortowania określonych przez binarny predykat.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _RanIt> inline  
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last,  
        _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `partial_sort`. Aby uzyskać więcej informacji, zobacz [partial_sort](../standard-library/algorithm-functions.md#partial_sort). 

## <a name="partial_sort_copy"></a> partial_sort_copy (STL/CLR)
Kopiuje elementy z zakresu źródłowego do zakresu docelowego, gdzie elementy źródłowe są uporządkowane według albo zasady mniejszy niż, albo innego określonego predykatu binarnego.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt, class _RanIt> inline  
    _RanIt partial_sort_copy(_InIt _First1, _InIt _Last1,  
        _RanIt _First2, _RanIt _Last2);  
template<class _InIt, class _RanIt, class _Pr> inline  
    _RanIt partial_sort_copy(_InIt _First1, _InIt _Last1,  
        _RanIt _First2, _RanIt _Last2, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `partial_sort_copy`. Aby uzyskać więcej informacji, zobacz [partial_sort_copy](../standard-library/algorithm-functions.md#partial_sort_copy).  
  
## <a name="partition"></a> partition (STL/CLR)
Klasyfikuje elementy w zakresie na dwa rozłączne zestawy, z elementami spełniającymi predykat unarny poprzedzającymi te, które go nie spełniają.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _BidIt, class _Pr> inline  
    _BidIt partition(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `partition`. Aby uzyskać więcej informacji, zobacz [partycji](../standard-library/algorithm-functions.md#partition).  

## <a name="pop_heap"></a> pop_heap — (STL/CLR)
Usuwa największy element z przodu sterty do przedostatniej pozycji w zakresie, a następnie tworzy nową stertę z pozostałych elementów.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _RanIt> inline  
    void pop_heap(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void pop_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `pop_heap`. Aby uzyskać więcej informacji, zobacz [pop_heap —](../standard-library/algorithm-functions.md#pop_heap).  

## <a name="prev_permutation"></a> prev_permutation (STL/CLR)
Zmienia kolejność elementów w zakresie, tak że oryginalna kolejność jest zastąpiona przez leksykograficznie kolejną większą permutację, o ile takowa istnieje, gdzie sens „kolejna” może być określony przez predykat binarny.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _BidIt> inline  
    bool prev_permutation(_BidIt _First, _BidIt _Last);  
template<class _BidIt, class _Pr> inline  
    bool prev_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `prev_permutation`. Aby uzyskać więcej informacji, zobacz [prev_permutation](../standard-library/algorithm-functions.md#prev_permutation).  

## <a name="push_heap"></a> push_heap — (STL/CLR)
Dodaje element znajdujący się na końcu zakresu do istniejącej sterty, która składa się z poprzednich elementów w zakresie.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _RanIt> inline  
    void push_heap(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void push_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `push_heap`. Aby uzyskać więcej informacji, zobacz [push_heap —](../standard-library/algorithm-functions.md#push_heap).  

## <a name="random_shuffle"></a> random_shuffle (STL/CLR)
Rozmieszcza sekwencji `N` elementy w zakresie do jednego z `N`! możliwości ustalenia losowo wybrany.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _RanIt> inline  
    void random_shuffle(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Fn1> inline  
    void random_shuffle(_RanIt _First, _RanIt _Last, _Fn1% _Func);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `random_shuffle`. Aby uzyskać więcej informacji, zobacz [random_shuffle](../standard-library/algorithm-functions.md#random_shuffle). 

## <a name="remove"></a> Usuń (STL/CLR)
Eliminuje określoną wartość z danego zakresu bez zakłócania kolejności pozostałych elementów i zwracania końca nowego zakresu wolnego od określonej wartości.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt, class _Ty> inline  
    _FwdIt remove(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `remove`. Aby uzyskać więcej informacji, zobacz [Usuń](http://msdn.microsoft.com/Library/77e2585c-441e-448d-bd1d-c893d1356ed8).  

## <a name="remove_copy"></a> remove_copy (STL/CLR)
Kopiuje elementy z zakresu źródłowego do zakresu docelowego, z tym wyjątkiem, że elementy o określonej wartości nie są kopiowane, bez naruszania kolejności pozostałych elementów i zwracania końca nowego zakresu docelowego.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt, class _OutIt, class _Ty> inline  
    _OutIt remove_copy(_InIt _First, _InIt _Last,  
        _OutIt _Dest, const _Ty% _Val);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `remove_copy`. Aby uzyskać więcej informacji, zobacz [remove_copy](../standard-library/algorithm-functions.md#remove_copy).  

## <a name="remove_copy_if"></a> remove_copy_if (STL/CLR)
Kopiuje elementy z zakresu źródłowego do zakresu docelowego, z tym wyjątkiem, że elementy spełniające predykat nie są kopiowane, bez naruszania kolejności pozostałych elementów i zwracania końca nowego zakresu docelowego.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt, class _OutIt, class _Pr> inline  
    _OutIt remove_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,  
        _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `remove_copy_if`. Aby uzyskać więcej informacji, zobacz [remove_copy_if](../standard-library/algorithm-functions.md#remove_copy_if).  
  
## <a name="remove_if"></a> remove_if (STL/CLR)
Eliminuje elementy, które spełniają predykat, z danego zakresu bez zakłócania kolejności pozostałych elementów i zwracania końca nowego zakresu wolnego od określonej wartości.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt, class _Pr> inline  
    _FwdIt remove_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `remove_if`. Aby uzyskać więcej informacji, zobacz [remove_if](../standard-library/algorithm-functions.md#remove_if).  
  
## <a name="replace"></a> replace (STL/CLR)
Sprawdza każdy element w zakresie i zastępuje go, jeśli odpowiada określonej wartości.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt, class _Ty> inline  
    void replace(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Oldval, const _Ty% _Newval);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `replace`. Aby uzyskać więcej informacji, zobacz [Zastąp](../standard-library/algorithm-functions.md#replace).

## <a name="replace_copy"></a> replace_copy (STL/CLR)
Sprawdza każdy element w zakresie źródłowym i zastępuje go, jeśli odpowiada określonej wartości, jednocześnie kopiując wynik do nowego zakresu docelowego.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt, class _OutIt, class _Ty> inline  
    _OutIt replace_copy(_InIt _First, _InIt _Last, _OutIt _Dest,  
        const _Ty% _Oldval, const _Ty% _Newval);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `replace_copy`. Aby uzyskać więcej informacji, zobacz [replace_copy](../standard-library/algorithm-functions.md#replace_copy).  

## <a name="replace_copy_if"></a> replace_copy_if (STL/CLR)
Sprawdza każdy element w zakresie źródłowym i zastępuje go, jeśli spełnia określony predykat, jednocześnie kopiując wynik do nowego zakresu docelowego.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt, class _OutIt, class _Pr, class _Ty> inline  
    _OutIt replace_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,  
        _Pr _Pred, const _Ty% _Val);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `replace_copy_if`. Aby uzyskać więcej informacji, zobacz [replace_copy_if](../standard-library/algorithm-functions.md#replace_copy_if).  
  
## <a name="replace_if"></a> replace_if (STL/CLR)
Sprawdza każdy element w zakresie i zastępuje go, jeśli spełnia określony predykat.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt, class _Pr, class _Ty> inline  
    void replace_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred,  
        const _Ty% _Val);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `replace_if`. Aby uzyskać więcej informacji, zobacz [replace_if](../standard-library/algorithm-functions.md#replace_if).  

## <a name="reverse"></a> reverse (STL/CLR)
Odwraca kolejność elementów w obrębie zakresu.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _BidIt> inline  
    void reverse(_BidIt _First, _BidIt _Last);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `reverse`. Aby uzyskać więcej informacji, zobacz [odwrotnej](../standard-library/algorithm-functions.md#reverse).  

## <a name="reverse_copy"></a> reverse_copy (STL/CLR)
Odwraca kolejność elementów w zakresie źródła podczas kopiowania ich do zakresu docelowego.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _BidIt, class _OutIt> inline  
    _OutIt reverse_copy(_BidIt _First, _BidIt _Last, _OutIt _Dest);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `reverse_copy`. Aby uzyskać więcej informacji, zobacz [reverse_copy](../standard-library/algorithm-functions.md#reverse_copy).  
  
## <a name="rotate"></a> rotate (STL/CLR)
Wymienia elementy znajdujące się w dwóch sąsiednich zakresach.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt> inline  
    void rotate(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `rotate`. Aby uzyskać więcej informacji, zobacz [Obróć](../standard-library/algorithm-functions.md#rotate).  

## <a name="rotate_copy"></a> rotate_copy (STL/CLR)
Wymienia elementy w dwóch sąsiednich zakresach w ramach zakresu źródłowego i kopiuje wynik do zakresu docelowego.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt, class _OutIt> inline  
    _OutIt rotate_copy(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last,  
        _OutIt _Dest);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `rotate_copy`. Aby uzyskać więcej informacji, zobacz [rotate_copy](../standard-library/algorithm-functions.md#rotate_copy).  
  
## <a name="search_"></a> Wyszukiwanie (STL/CLR)
Wyszukuje pierwsze wystąpienie sekwencji w zakresie docelowym, której elementy są równe tym w danej sekwencji elementów lub której elementy są równoważne w sensie określonym przez predykat binarny dla elementów w danej sekwencji.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt1, class _FwdIt2> inline  
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2);  
template<class _FwdIt1, class _FwdIt2, class _Pr> inline  
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `search`. Aby uzyskać więcej informacji, zobacz [wyszukiwania](../standard-library/algorithm-functions.md#search).  

## <a name="search_n"></a> search_n — (STL/CLR)
Wyszukuje pierwszą podsekwencję w zakresie, w której określona liczba elementów ma określoną wartość lub relację do tej wartości określoną przez predykat binarny.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt1, class _Diff2, class _Ty> inline  
    _FwdIt1 search_n(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _Diff2 _Count, const _Ty& _Val);  
template<class _FwdIt1, class _Diff2, class _Ty, class _Pr> inline  
    _FwdIt1 search_n(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _Diff2 _Count, const _Ty& _Val, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `search_n`. Aby uzyskać więcej informacji, zobacz [search_n —](../standard-library/algorithm-functions.md#search_n).  

## <a name="set_difference"></a> set_difference — (STL/CLR)
Łączy w sobie wszystkie elementy, które należą do jednego posortowanego zakresu źródłowego, ale nie do drugiego posortowanego zakresu źródłowego, w pojedynczy, posortowany zakres docelowy, gdzie kryterium sortowania może być określone przez predykat binarny.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt1, class _InIt2, class _OutIt> inline  
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2,_OutIt _Dest);  
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline  
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `set_difference`. Aby uzyskać więcej informacji, zobacz [set_difference —](../standard-library/algorithm-functions.md#set_difference).

## <a name="set_intersection"></a> set_intersection — (STL/CLR)
Łączy w sobie wszystkie elementy, które należą do obu posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt1, class _InIt2, class _OutIt> inline  
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);  
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline  
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `set_intersection`. Aby uzyskać więcej informacji, zobacz [set_intersection —](../standard-library/algorithm-functions.md#set_intersection). 

## <a name="set_symmetric_difference"></a> set_symmetric_difference — (STL/CLR)
Łączy w sobie wszystkie elementy, które należą do jednego z, ale nie obu posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt1, class _InIt2, class _OutIt> inline  
    _OutIt set_symmetric_difference(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);  
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline  
    _OutIt set_symmetric_difference(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `set_symmetric_difference`. Aby uzyskać więcej informacji, zobacz [set_symmetric_difference —](../standard-library/algorithm-functions.md#set_symmetric_difference).  

## <a name="set_union"></a> set_union — (STL/CLR)
Łączy w sobie wszystkie elementy, które należą do przynajmniej jednego z dwóch posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt1, class _InIt2, class _OutIt> inline  
    _OutIt set_union(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);  
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline  
    _OutIt set_union(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `set_union`. Aby uzyskać więcej informacji, zobacz [set_union —](../standard-library/algorithm-functions.md#set_union).  

## <a name="sort"></a> Sortowanie (STL/CLR)
Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryteriów sortowania określonych przez binarny predykat.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _RanIt> inline  
    void sort(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void sort(_RanIt _First, _RanIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `sort`. Aby uzyskać więcej informacji, zobacz [sortowania](../mfc/reference/cmfclistctrl-class.md#sort).  

## <a name="sort_heap"></a> sort_heap — (STL/CLR)
Konwertuje stertę na sortowany zakres.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _RanIt> inline  
    void sort_heap(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void sort_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `sort_heap`. Aby uzyskać więcej informacji, zobacz [sort_heap —](../standard-library/algorithm-functions.md#sort_heap).  

## <a name="stable_partition"></a> stable_partition — (STL/CLR)
Klasyfikuje elementy w zakresie na dwa rozłączne zestawy, z elementami spełniającymi predykat unarny poprzedzającymi te, które go nie spełniają, zachowując względną kolejność elementów równoważnych.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _BidIt, class _Pr> inline  
    _BidIt stable_partition(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `stable_partition`. Aby uzyskać więcej informacji, zobacz [stable_partition —](../standard-library/algorithm-functions.md#stable_partition).  

## <a name="stable_sort"></a> stable_sort — (STL/CLR)
Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryterium sortowania określonego przez binarny predykat i zachowuje względną kolejność elementów równoważnych.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _BidIt> inline  
    void stable_sort(_BidIt _First, _BidIt _Last);  
template<class _BidIt, class _Pr> inline  
    void stable_sort(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `stable_sort`. Aby uzyskać więcej informacji, zobacz [stable_sort —](../standard-library/algorithm-functions.md#stable_sort).  
  
## <a name="swap"></a> swap (STL/CLR)
Wymienia wartości elementów między dwoma typami obiektów, przypisując zawartość pierwszego obiektu do drugiego obiektu, a zawartość drugiego do pierwszego.  
  
### <a name="syntax"></a>Składnia  
  
```  
<class _Ty> inline  
    void swap(_Ty% _Left, _Ty% _Right);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `swap`. Aby uzyskać więcej informacji, zobacz [wymiany](http://msdn.microsoft.com/Library/b471a2de-035e-4aff-b1c7-345d85d93972).  

## <a name="swap_ranges"></a> swap_ranges — (STL/CLR)
Zamienia elementy jednego zakresu przez elementy innego zakresu, zakresy mają równe wielkości.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt1, class _FwdIt2> inline  
    _FwdIt2 swap_ranges(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `swap_ranges`. Aby uzyskać więcej informacji, zobacz [swap_ranges —](../standard-library/algorithm-functions.md#swap_ranges).  

## <a name="transform"></a> transform (STL/CLR)
Stosuje określony obiekt funkcji dla każdego elementu w zakresie sortowania lub dla pary elementów z dwóch zakresów sortowania i kopiuje zwracane wartości obiektu funkcji do zakresu docelowego.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt, class _OutIt, class _Fn1> inline  
    _OutIt transform(_InIt _First, _InIt _Last, _OutIt _Dest,  
        _Fn1 _Func);  
template<class _InIt1, class _InIt2, class _OutIt, class _Fn2> inline  
    _OutIt transform(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
        _OutIt _Dest, _Fn2 _Func);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `transform`. Aby uzyskać więcej informacji, zobacz [przekształcenie](../standard-library/algorithm-functions.md#transform).  

## <a name="unique"></a> Unikatowy (STL/CLR)
Usuwa zduplikowane elementy, które sąsiadują ze sobą w określonym zakresie.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt> inline  
    _FwdIt unique(_FwdIt _First, _FwdIt _Last);  
template<class _FwdIt, class _Pr> inline  
    _FwdIt unique(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `unique`. Aby uzyskać więcej informacji, zobacz [unikatowy](../standard-library/algorithm-functions.md#unique).  
  
## <a name="unique_copy"></a> unique_copy — (STL/CLR)
Kopiuje elementy z zakresu źródłowego do zakresu docelowego z wyjątkiem zduplikowanych elementów, które ze sobą sąsiadują.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Pr> inline  
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest,  
        _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `unique_copy`. Aby uzyskać więcej informacji, zobacz [unique_copy —](../standard-library/algorithm-functions.md#unique_copy).  

## <a name="upper_bound"></a> upper_bound (STL/CLR)
Znajduje pozycję pierwszego elementu w uporządkowanym zakresie, który ma wartość większą niż określona wartość, gdzie kryterium sortowania może być określone przez predykat binarny.  
  
### <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt, class _Ty> inline  
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `upper_bound`. Aby uzyskać więcej informacji, zobacz [upper_bound](../standard-library/algorithm-functions.md#upper_bound). 
