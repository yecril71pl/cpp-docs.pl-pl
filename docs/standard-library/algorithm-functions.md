---
title: '&lt;Algorytm&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- algorithm/std::adjacent_find
- algorithm/std::all_of
- algorithm/std::any_of
- algorithm/std::binary_search
- algorithm/std::copy
- algorithm/std::copy_backward
- algorithm/std::copy_if
- algorithm/std::copy_n
- algorithm/std::equal
- algorithm/std::equal_range
- algorithm/std::fill
- algorithm/std::fill_n
- algorithm/std::find
- algorithm/std::find_end
- algorithm/std::find_first_of
- algorithm/std::find_if
- algorithm/std::find_if_not
- algorithm/std::for_each
- algorithm/std::generate
- algorithm/std::generate_n
- algorithm/std::includes
- algorithm/std::inplace_merge
- algorithm/std::is_heap
- algorithm/std::is_heap_until
- algorithm/std::is_partitioned
- algorithm/std::is_permutation
- algorithm/std::is_sorted
- algorithm/std::is_sorted_until
- algorithm/std::iter_swap
- algorithm/std::lexicographical_compare
- algorithm/std::lower_bound
- algorithm/std::make_heap
- algorithm/std::max
- algorithm/std::max_element
- algorithm/std::merge
- algorithm/std::min
- algorithm/std::minmax
- algorithm/std::minmax_element
- algorithm/std::min_element
- algorithm/std::mismatch
- algorithm/std::move
- algorithm/std::move_backward
- algorithm/std::next_permutation
- algorithm/std::none_of
- algorithm/std::nth_element
- algorithm/std::partial_sort
- algorithm/std::partial_sort_copy
- algorithm/std::partition
- algorithm/std::partition_point
- algorithm/std::pop_heap
- algorithm/std::prev_permutation
- algorithm/std::push_heap
- algorithm/std::random_shuffle
- algorithm/std::remove
- algorithm/std::remove_copy
- algorithm/std::remove_copy_if
- algorithm/std::remove_if
- algorithm/std::replace
- algorithm/std::replace_copy
- algorithm/std::replace_copy_if
- algorithm/std::replace_if
- algorithm/std::reverse
- algorithm/std::reverse_copy
- algorithm/std::rotate
- algorithm/std::rotate_copy
- algorithm/std::search
- algorithm/std::search_n
- algorithm/std::set_difference
- algorithm/std::set_intersection
- algorithm/std::set_symmetric_difference
- algorithm/std::set_union
- algorithm/std::shuffle
- algorithm/std::sort
- algorithm/std::sort_heap
- algorithm/std::stable_partition
- algorithm/std::stable_sort
- algorithm/std::swap_ranges
- algorithm/std::transform
- algorithm/std::unique
- algorithm/std::unique_copy
- algorithm/std::upper_bound
- xutility/std::copy
- xutility/std::copy_backward
- xutility/std::copy_n
- xutility/std::count
- xutility/std::equal
- xutility/std::fill
- xutility/std::fill_n
- xutility/std::find
- xutility/std::is_permutation
- xutility/std::lexicographical_compare
- xutility/std::move
- xutility/std::move_backward
- xutility/std::reverse
- xutility/std::rotate
- algorithm/std::count_if
- algorithm/std::partition_copy
- algorithm/std::swap
dev_langs:
- C++
ms.assetid: c10b0c65-410c-4c83-abf8-8b7f61bba8d0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::adjacent_find [C++]
- std::all_of [C++]
- std::any_of [C++]
- std::binary_search [C++]
- std::copy [C++]
- std::copy_backward [C++]
- std::copy_if [C++]
- std::copy_n [C++]
- std::equal [C++]
- std::equal_range [C++]
- std::fill [C++]
- std::fill_n [C++]
- std::find [C++]
- std::find_end [C++]
- std::find_first_of [C++]
- std::find_if [C++]
- std::find_if_not [C++]
- std::for_each [C++]
- std::generate [C++]
- std::generate_n [C++]
- std::includes [C++]
- std::inplace_merge [C++]
- std::is_heap [C++]
- std::is_heap_until [C++]
- std::is_partitioned [C++]
- std::is_permutation [C++]
- std::is_sorted [C++]
- std::is_sorted_until [C++]
- std::iter_swap [C++]
- std::lexicographical_compare [C++]
- std::lower_bound [C++]
- std::make_heap [C++]
- std::max [C++]
- std::max_element [C++]
- std::merge [C++]
- std::min [C++]
- std::minmax [C++]
- std::minmax_element [C++]
- std::min_element [C++]
- std::mismatch [C++]
- std::move [C++]
- std::move_backward [C++]
- std::next_permutation [C++]
- std::none_of [C++]
- std::nth_element [C++]
- std::partial_sort [C++]
- std::partial_sort_copy [C++]
- std::partition [C++]
- std::partition_point [C++]
- std::pop_heap [C++]
- std::prev_permutation [C++]
- std::push_heap [C++]
- std::random_shuffle [C++]
- std::remove [C++]
- std::remove_copy [C++]
- std::remove_copy_if [C++]
- std::remove_if [C++]
- std::replace [C++]
- std::replace_copy [C++]
- std::replace_copy_if [C++]
- std::replace_if [C++]
- std::reverse [C++]
- std::reverse_copy [C++]
- std::rotate [C++]
- std::rotate_copy [C++]
- std::search [C++]
- std::search_n [C++]
- std::set_difference [C++]
- std::set_intersection [C++]
- std::set_symmetric_difference [C++]
- std::set_union [C++]
- std::shuffle [C++]
- std::sort [C++]
- std::sort_heap [C++]
- std::stable_partition [C++]
- std::stable_sort [C++]
- std::swap_ranges [C++]
- std::transform [C++]
- std::unique [C++]
- std::unique_copy [C++]
- std::upper_bound [C++]
- std::copy [C++]
- std::copy_backward [C++]
- std::copy_n [C++]
- std::count [C++]
- std::equal [C++]
- std::fill [C++]
- std::fill_n [C++]
- std::find [C++]
- std::is_permutation [C++]
- std::lexicographical_compare [C++]
- std::move [C++]
- std::move_backward [C++]
- std::reverse [C++]
- std::rotate [C++]
- std::count_if [C++]
- std::partition_copy [C++]
- std::swap [C++]
ms.workload:
- cplusplus
ms.openlocfilehash: eb5b068f30703119d0771725a9cb9980a1ca65ea
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="ltalgorithmgt-functions"></a>&lt;Algorytm&gt; funkcji
||||  
|-|-|-|  
|[Przenieś](#alg_move)|[adjacent_find](#adjacent_find)|[all_of](#all_of)|  
|[any_of](#any_of)|[binary_search](#binary_search)|[copy](#copy)|  
|[copy_backward](#copy_backward)|[copy_if](#copy_if)|[copy_n](#copy_n)|  
|[Liczba](#count)|[count_if](#count_if)|[equal](#equal)|  
|[equal_range](#equal_range)|[wypełnienia](#fill)|[fill_n](#fill_n)|  
|[Znajdź](#find)|[find_end —](#find_end)|[find_first_of](#find_first_of)|  
|[find_if](#find_if)|[find_if_not](#find_if_not)|[for_each](#for_each)|  
|[Generowanie](#generate)|[generate_n](#generate_n)|[Zawiera](#includes)|  
|[inplace_merge](#inplace_merge)|[is_heap](#is_heap)|[is_heap_until](#is_heap_until)|  
|[is_partitioned](#is_partitioned)|[is_permutation](#is_permutation)|[is_sorted](#is_sorted)|  
|[is_sorted_until](#is_sorted_until)|[iter_swap](#iter_swap)|[lexicographical_compare —](#lexicographical_compare)|  
|[lower_bound](#lower_bound)|[make_heap](#make_heap)|[max](#max)|  
|[max_element](#max_element)|[merge](#merge)|[min](#min)|  
|[min_element](#min_element)|[minmax](#minmax)|[minmax_element](#minmax_element)|  
|[mismatch](#mismatch)|[move_backward](#move_backward)|[next_permutation](#next_permutation)|  
|[none_of](#none_of)|[nth_element](#nth_element)|[partial_sort](#partial_sort)|  
|[partial_sort_copy](#partial_sort_copy)|[Partycji](#partition)|[partition_copy](#partition_copy)|  
|[partition_point](#partition_point)|[pop_heap](#pop_heap)|[prev_permutation](#prev_permutation)|  
|[push_heap](#push_heap)|[random_shuffle](#random_shuffle)|[remove](#remove)|  
|[remove_copy](#remove_copy)|[remove_copy_if](#remove_copy_if)|[remove_if](#remove_if)|  
|[Zamień](#replace)|[replace_copy](#replace_copy)|[replace_copy_if](#replace_copy_if)|  
|[replace_if](#replace_if)|[Reverse](#reverse)|[reverse_copy](#reverse_copy)|  
|[Obróć](#rotate)|[rotate_copy](#rotate_copy)|[Wyszukiwanie](#search)|  
|[search_n](#search_n)|[set_difference](#set_difference)|[set_intersection —](#set_intersection)|  
|[set_symmetric_difference](#set_symmetric_difference)|[set_union](#set_union)|[sort](#sort)|  
|[sort_heap](#sort_heap)|[stable_partition](#stable_partition)|[stable_sort](#stable_sort)|  
|[shuffle](#shuffle)|[swap](#swap)|[swap_ranges](#swap_ranges)|  
|[transform](#transform)|[unique](#unique)|[unique_copy](#unique_copy)|  
|[upper_bound](#upper_bound)|  
  
##  <a name="adjacent_find"></a>  adjacent_find  
 Wyszukuje dwa sąsiadujące elementy, które są równe lub spełniają określony warunek.  
  
```  
template<class ForwardIterator>  
    ForwardIterator adjacent_find(  
        ForwardIterator first,   
        ForwardIterator last);
  
template<class ForwardIterator , class BinaryPredicate>  
    ForwardIterator adjacent_find(  
        ForwardIterator first,   
        ForwardIterator last,   
        BinaryPredicate comp);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterator do przodu adresowania położenie pierwszego elementu w zakresie do wyszukania.  
  
 `last`  
 Iterator do przodu adresowania pozycji w jednym ostatniego elementu w zakresie do wyszukania.  
  
 `comp`  
 Predykat binarne nadanie warunku muszą być spełnione przez wartości elementy sąsiednie w zakresie, w którym wykonywane jest wyszukiwanie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Do przodu iteratora pierwszy element pary sąsiadujących ze sobą, które są ze sobą równe (w pierwszej wersji) lub które spełniają warunek przez predykat binarne (w wersji drugi), pod warunkiem, że znajduje się dwa elementy. W przeciwnym razie iteratora wskazujący `last` jest zwracany.  
  
### <a name="remarks"></a>Uwagi  
 `adjacent_find` Algorytm jest algorytm nonmutating sekwencji. Zakres do wyszukania musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać. Złożoność czasu algorytm jest liniowa w liczbę elementów zawartych w zakresie.  
  
 `operator==` Używany do określenia dopasowania między elementami musi nałożyć równoważność stosunek argumentów.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_adj_fnd.cpp  
// compile with: /EHsc  
#include <list>  
#include <algorithm>  
#include <iostream>  
  
// Returns whether second element is twice the first  
bool twice (int elem1, int elem2 )  
{  
   return elem1 * 2 == elem2;  
}  
  
int main()   
{  
   using namespace std;  
   list <int> L;  
   list <int>::iterator Iter;  
   list <int>::iterator result1, result2;  
  
   L.push_back( 50 );  
   L.push_back( 40 );  
   L.push_back( 10 );  
   L.push_back( 20 );  
   L.push_back( 20 );  
  
   cout << "L = ( " ;  
   for ( Iter = L.begin( ) ; Iter != L.end( ) ; Iter++ )  
      cout << *Iter << " ";  
   cout << ")" << endl;  
  
   result1 = adjacent_find( L.begin( ), L.end( ) );  
   if ( result1 == L.end( ) )  
      cout << "There are not two adjacent elements that are equal."  
           << endl;  
   else  
      cout << "There are two adjacent elements that are equal."  
           << "\n They have a value of "  
           <<  *( result1 ) << "." << endl;  
  
   result2 = adjacent_find( L.begin( ), L.end( ), twice );  
   if ( result2 == L.end( ) )  
      cout << "There are not two adjacent elements where the "  
           << " second is twice the first." << endl;  
   else  
      cout << "There are two adjacent elements where "  
           << "the second is twice the first."  
           << "\n They have values of " << *(result2++);  
      cout << " & " << *result2 << "." << endl;  
}  
```  
  
```Output  
L = ( 50 40 10 20 20 )  
There are two adjacent elements that are equal.  
 They have a value of 20.  
There are two adjacent elements where the second is twice the first.  
 They have values of 10 & 20.  
```  
  
##  <a name="all_of"></a>  all_of  
 Zwraca `true` po warunek musi być obecny przy każdym elemencie podanego zakresu.  
  
```  
template<class InputIterator, class Predicate>  
    bool all_of(  
        InputIterator first,   
        InputIterator last,   
        BinaryPredicatecomp);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Wejściowy iteratora, która wskazuje, gdzie można uruchomić sprawdzić stan. Iterator oznacza w przypadku, gdy zakres uruchamia elementów.  
  
 `last`  
 Iterację wejściowych wskazuje koniec zakresu elementów, aby sprawdzić stan.  
  
 `comp`  
 Warunek do sprawdzenia. Jest to obiekt zdefiniowane przez użytkownika funkcja predykatu, który definiuje warunek muszą być spełnione przez element sprawdzany. Predykat pobiera jeden argument i zwraca `true` lub `false`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `true` po wykryciu stanu każdego elementu w zakresie wskazanych i `false` Jeśli warunek nie wykryto co najmniej jeden raz.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu `true` tylko wtedy, gdy dla każdego `N` w zakresie `[0,Last - first)`, predykat `comp(*(_First + N))` jest `true`.  
  
##  <a name="any_of"></a>  any_of  
 Zwraca `true` gdy warunek ma co najmniej raz w określonym zakresie elementów.  
  
```  
template<class InputIterator, class UnaryPredicate>  
    bool any_of(  
        InputIterator first,   
        InputIterator last,   
        UnaryPredicate comp);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Wejściowy iteratora, która wskazuje, gdzie można rozpocząć sprawdzania zakresu elementów w warunku.  
  
 `last`  
 Iterację wejściowych wskazuje koniec zakresu elementów, aby sprawdzić stan.  
  
 `comp`  
 Warunek do sprawdzenia. To jest udostępniana przez obiekt zdefiniowane przez użytkownika funkcja predykatu. Predykat definiuje warunek muszą być spełnione przez element testowana. Predykat pobiera jeden argument i zwraca `true` lub `false`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `true` Jeśli warunek wykryto co najmniej raz w zakresie wskazanych `false` Jeśli warunek nie zostanie wykryta.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu `true` tylko wtedy, gdy dla niektórych `N` w zakresie  
  
 `[0, last - first)`, predykat `comp(*(first + N))` ma wartość true.  
  
##  <a name="binary_search"></a>  binary_search —  
 Testuje, czy w sortowanym zakresie istnieje element, który jest równy określonej wartości lub który jest odpowiednikiem w sensie określonym przez predykat binarny.  
  
```  
template<class ForwardIterator, class Type>      
    bool binary_search(
        ForwardIterator first, 
        ForwardIterator last, 
        const Type& value);  
  
template<class ForwardIterator,  class Type,  class BinaryPredicate>  
    bool binary_search(
        ForwardIterator first, 
        ForwardIterator last, 
        const Type& value, 
        BinaryPredicate comp);  
  
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Iterator do przodu adresowania położenie pierwszego elementu w zakresie do wyszukania.  
  
 `last`  
 Iterator do przodu adresowania pozycji w jednym ostatniego elementu w zakresie do wyszukania.  
  
 `value`  
 Wymagana wartość do dopasowania przez wartość elementu lub które muszą spełniać warunek o wartości element określony przez predykat binarnego.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje znaczeniu, w której jeden element jest mniejsza niż innym. Predykat binarne przyjmuje dwa argumenty i zwraca `true` po spełnieniu i `false` gdy nie są spełnione.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli element znajduje się w zakresie, który jest taki sam, lub równoważne z podaną wartością; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Zakres źródła posortowane odwołuje się do musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i, w ramach sekwencji ostatniej pozycji musi być dostępny z pierwszego przez przyrostowo zmieniać.  
  
 Posortowane zakresu musi być ustawione jako warunek wstępny stosowania `binary_search` algorytm zgodnie z tej samej kolejności jak ma być używany przez algorytm sortowania połączonych zakresów.  
  
 Zakresów nie są modyfikowane przez `binary_search`.  
  
 Typy wartości iteratorów do przodu musi być mniejsza-niż porównywalne może zostać określona, tak, aby dane dwa elementy, można ustalić czy są równoważne (w tym sensie, że nie jest mniejsza niż drugi) albo że jeden jest mniejsza niż innych. Powoduje to kolejność między elementami nonequivalent  
  
 Złożoność algorytm jest logarytmiczna dla Iteratory dostęp losowy i liniowej, w przeciwnym razie wartość o liczbie kroków proporcjonalny do ( `last`  -  `first`).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_bin_srch.cpp  
// compile with: /EHsc  
#include <list>  
#include <vector>  
#include <algorithm>  
#include <functional>      // greater<int>( )  
#include <iostream>  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser( int elem1, int elem2 )  
{  
    if (elem1 < 0)  
        elem1 = - elem1;  
    if (elem2 < 0)  
        elem2 = - elem2;  
    return elem1 < elem2;  
}  
  
int main( )  
{  
    using namespace std;  
  
    list <int> List1;  
  
    List1.push_back( 50 );  
    List1.push_back( 10 );  
    List1.push_back( 30 );  
    List1.push_back( 20 );  
    List1.push_back( 25 );  
    List1.push_back( 5 );  
  
    List1.sort();  
  
    cout << "List1 = ( " ;  
    for ( auto Iter : List1 )  
        cout << Iter << " ";  
    cout << ")" << endl;  
  
    // default binary search for 10  
    if( binary_search(List1.begin(), List1.end(), 10) )  
        cout << "There is an element in list List1 with a value equal to 10."  
        << endl;  
    else  
        cout << "There is no element in list List1 with a value equal to 10."  
        << endl;  
  
    // a binary_search under the binary predicate greater  
    List1.sort(greater<int>());  
    if( binary_search(List1.begin(), List1.end(), 10, greater<int>()) )  
        cout << "There is an element in list List1 with a value greater than 10 "  
        << "under greater than." << endl;  
    else  
        cout << "No element in list List1 with a value greater than 10 "  
        << "under greater than." << endl;  
  
    // a binary_search under the user-defined binary predicate mod_lesser  
    vector<int> v1;  
  
    for( auto i = -2; i <= 4; ++i )  
    {  
        v1.push_back(i);  
    }  
  
    sort(v1.begin(), v1.end(), mod_lesser);  
  
    cout << "Ordered using mod_lesser, vector v1 = ( " ;  
    for( auto Iter : v1 )  
        cout << Iter << " ";  
    cout << ")" << endl;  
  
    if( binary_search(v1.begin(), v1.end(), -3, mod_lesser) )  
        cout << "There is an element with a value equivalent to -3 "  
        << "under mod_lesser." << endl;  
    else  
        cout << "There is not an element with a value equivalent to -3 "  
        << "under mod_lesser." << endl;  
}   
```  
  
##  <a name="copy"></a>  Kopiuj  
 Przypisuje wartości elementów z zakresu źródłowego do zakresu docelowego, iterując przez sekwencję źródłową elementów oraz przypisując im nowe pozycje w kierunku do przodu.  
  
```  
template<class InputIterator, class OutputIterator>  
    OutputIterator copy(
        InputIterator first, 
        InputIterator last, 
        OutputIterator destBeg);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Wejściowy iteratora adresowania położenie pierwszego elementu w zakresie źródłowym.  
  
 `last`  
 Wejściowy iteratora adresowania pozycji, która jest poza ostatniego elementu w zakresie źródłowym.  
  
 *destBeg*  
 Dane wyjściowe iteratora adresowania położenie pierwszego elementu w zakresie docelowym.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dane wyjściowe iteratora adresowania pozycji, która jest jedną poza ostatniego elementu w zakresie docelowego, który jest, adresy iteratora `result` + ( `last`  -   `first` ).  
  
### <a name="remarks"></a>Uwagi  
 Zakres źródłowy musi być prawidłowy i musi być wystarczająco dużo miejsca w miejscu przeznaczenia, aby pomieścić wszystkie elementy kopiowane.  
  
 Ponieważ algorytm kopiuje elementy źródłowe w kolejności od pierwszego elementu, mogą nakładać się na zakres docelowy o zakresie źródła podane `last` pozycji zakres źródłowy nie znajduje się w zakresie docelowym. **Kopiuj** służy do przesunięcia elementy do lewej strony, ale nie po prawej stronie, jeśli nie istnieje żadne nakładania się zakresów źródłowym i docelowym. Przesunięcie w prawo dowolną liczbę pozycji, użyj [copy_backward —](../standard-library/algorithm-functions.md#copy_backward) algorytmu.  
  
 **Kopiowania** algorytm modyfikuje tylko wartości wskazywanej przez Iteratory, przypisywania wartości nowe elementy w zakresie docelowym. Nie może służyć do tworzenia nowych elementów i nie może bezpośrednio wstawiać elementów do pustego kontenera.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_copy.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main() {  
   using namespace std;  
   vector <int> v1, v2;  
   vector <int>::iterator Iter1, Iter2;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
      v1.push_back( 10 * i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 10 ; ii++ )  
      v2.push_back( 3 * ii );  
  
   cout << "v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // To copy the first 3 elements of v1 into the middle of v2  
   copy( v1.begin( ), v1.begin( ) + 3, v2.begin( ) + 4 );  
  
   cout << "v2 with v1 insert = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // To shift the elements inserted into v2 two positions  
   // to the left  
   copy( v2.begin( )+4, v2.begin( ) + 7, v2.begin( ) + 2 );  
  
   cout << "v2 with shifted insert = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
}  
```  
  
```Output  
v1 = ( 0 10 20 30 40 50 )  
v2 = ( 0 3 6 9 12 15 18 21 24 27 30 )  
v2 with v1 insert = ( 0 3 6 9 0 10 20 21 24 27 30 )  
v2 with shifted insert = ( 0 3 0 10 20 10 20 21 24 27 30 )  
```  
  
##  <a name="copy_backward"></a>  copy_backward —  
 Przypisuje wartości elementów z zakresu źródłowego do zakresu docelowego, iterując przez sekwencję źródłową elementów oraz przypisując im nowe pozycje w kierunku do tyłu.  
  
```  
template<class BidirectionalIterator1, class BidirectionalIterator2>  
    BidirectionalIterator2 copy_backward(
        BidirectionalIterator1 first, 
        BidirectionalIterator1 last, 
        BidirectionalIterator2 destEnd);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterator dwukierunkowy odnoszący się do pozycji pierwszego elementu w zakresie źródłowym.  
  
 `last`  
 Iterator dwukierunkowy odnoszący się do pierwszej pozycji po elemencie końcowym w zakresie źródłowym.  
  
 `destEnd`  
 Iterator dwukierunkowy odnoszący się do pierwszej pozycji po elemencie końcowym w zakresie docelowym.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dane wyjściowe iteratora adresowania pozycji, która jest jedną poza ostatniego elementu w zakresie docelowego, który jest, adresy iteratora `destEnd` -( `last`  -   `first` ).  
  
### <a name="remarks"></a>Uwagi  
 Zakres źródłowy musi być prawidłowy i musi być wystarczająco dużo miejsca w miejscu przeznaczenia, aby pomieścić wszystkie elementy kopiowane.  
  
 `copy_backward` Algorytmu nakłada bardziej rygorystycznych wymagań niż algorytm kopiowania. Oba iteratory, wejściowy i wyjściowy muszą być dwukierunkowe.  
  
 `copy_backward` i [move_backward](../standard-library/algorithm-functions.md#move_backward) algorytmy są tylko algorytmy standardowa biblioteka C++ wyznaczenie zakres danych wyjściowych z iteratora wskazujące na końcu zakresu docelowego.  
  
 Ponieważ algorytm kopiuje elementy źródłowe w kolejności od ostatniego elementu, mogą nakładać się na zakres docelowy o zakresie źródła podane `first` pozycji zakres źródłowy nie znajduje się w zakresie docelowym. `copy_backward` może służyć do przesunięcia elementy w prawo, ale nie po lewej stronie, chyba, że nie bez nakładania się zakresów źródłowym i docelowym. Przesunięcie w lewo dowolną liczbę pozycji, użyj [kopiowania](../standard-library/algorithm-functions.md#copy) algorytmu.  
  
 `copy_backward` Algorytmu modyfikuje tylko wartości wskazywanej przez Iteratory, przypisywania wartości nowe elementy w zakresie docelowym. Nie może służyć do tworzenia nowych elementów i nie może bezpośrednio wstawiać elementów do pustego kontenera.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_copy_bkwd.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main() {  
   using namespace std;  
   vector <int> v1, v2;  
   vector <int>::iterator Iter1, Iter2;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; ++i )  
      v1.push_back( 10 * i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 10 ; ++ii )  
      v2.push_back( 3 * ii );  
  
   cout << "v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; ++Iter1 )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // To copy_backward the first 3 elements of v1 into the middle of v2  
   copy_backward( v1.begin( ), v1.begin( ) + 3, v2.begin( ) + 7 );  
  
   cout << "v2 with v1 insert = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // To shift the elements inserted into v2 two positions  
   // to the right  
   copy_backward( v2.begin( )+4, v2.begin( ) + 7, v2.begin( ) + 9 );  
  
   cout << "v2 with shifted insert = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
}  
```  
  
##  <a name="copy_if"></a>  copy_if  
 W zakresie elementów kopiuje elementy, które są `true` dla określonego warunku.  
  
```  
template<class InputIterator, class OutputIterator, class BinaryPredicate>  
    OutputIterator copy_if(  
        InputIterator first,   
        InputIterator last,  
        OutputIterator dest,  
        Predicate pred);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterację wejściowych wskazuje początek zakresu, aby sprawdzić stan.  
  
 `last`  
 Iterację wejściowych wskazuje koniec zakresu.  
  
 `dest`  
 Iterator danych wyjściowych, który wskazuje lokalizację docelową dla skopiowane elementy.  
  
 `_Pred`  
 Warunek, do którego dla każdego elementu w zakresie jest testowana. Ten stan jest udostępniana przez obiekt zdefiniowane przez użytkownika funkcja predykatu. Predykat przyjmuje jeden argument i zwraca `true` lub `false`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dane wyjściowe iteratora równą `dest` zwiększany raz dla każdego elementu, który spełnia warunek. Innymi słowy, zwracana wartość minus `dest` jest równa liczbie skopiowane elementy.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu  
  
 `if (_Pred(*_First + N)) * dest++ = *(_First + N))`  
  
 tylko jeden raz dla każdego `N` w zakresie `[0, last - first)`, ściśle zwiększenia wartości `N` uruchamianie o najniższej wartości. Jeśli `dest` i `first` wyznaczyć regiony pamięci masowej, `dest` nie może być w zakresie `[ first, last )`.  
  
##  <a name="copy_n"></a>  copy_n  
 Kopiuje określoną liczbę elementów.  
  
```  
template<class InputIterator, class Size, class OutputIterator>  
    OutputIterator copy_n(
        InputIterator first, 
        Size count, 
        OutputIterator dest);  
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Wejściowy iteratora, która wskazuje, gdzie skopiować elementy z.  
  
 `count`  
 Podpisem lub unsigned integer — typ określająca liczbę elementów do skopiowania.  
  
 `dest`  
 Iterator danych wyjściowych, która wskazuje, gdzie można skopiować elementów do.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca iterację dane wyjściowe, gdy elementy zostały skopiowane do. Jest taka sama jak wartość trzeci parametr `dest`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu `*(dest + N) = *(first + N))` raz dla każdego `N` w zakresie `[0, count)`, ściśle zwiększenia wartości `N` uruchamianie o najniższej wartości. Następnie zwraca `dest + N`. Jeśli `dest` i `first` wyznaczyć regiony pamięci masowej, `dest` nie może być w zakresie `[first, last)`.  
  
##  <a name="count"></a>  Liczba  
 Zwraca liczbę elementów w zakresie, których wartości pasują do określonej wartości.  
  
```  
template<class InputIterator, class Type> 
    typename iterator_traits<InputIterator>::difference_type count(
        InputIterator first, 
        InputIterator last, 
        const Type& val);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iteratora wejściowych adresowania położenie pierwszego elementu w zakresie do można przechodzić.  
  
 `last`  
 Iteratora wejściowych adresowania pozycji w jednym ostatniego elementu w zakresie do można przechodzić.  
  
 `val`  
 Wartość elementów do zliczenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Typ różnica **InputIterator** które zlicza liczbę elementów w zakresie [ `first`, `last` ) mają wartość `val`.  
  
### <a name="remarks"></a>Uwagi  
 `operator==` Używany do określenia pasuje do elementu i określona wartość musi nałożyć równoważność stosunek argumentów.  
  
 Ten algorytm uogólniony do liczby elementów, które spełniają wszystkie predykatu za pomocą funkcji szablonu [count_if](../standard-library/algorithm-functions.md#count_if).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_count.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    vector<int> v1;  
    vector<int>::iterator Iter;  
  
    v1.push_back(10);  
    v1.push_back(20);  
    v1.push_back(10);  
    v1.push_back(40);  
    v1.push_back(10);  
  
    cout << "v1 = ( " ;  
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)  
        cout << *Iter << " ";  
    cout << ")" << endl;  
  
    vector<int>::iterator::difference_type result;  
    result = count(v1.begin(), v1.end(), 10);  
    cout << "The number of 10s in v2 is: " << result << "." << endl;  
}  
```  
  
```Output  
v1 = ( 10 20 10 40 10 )  
The number of 10s in v2 is: 3.  
```  
  
##  <a name="count_if"></a>  count_if  
 Zwraca liczbę elementów w zakresie, w których wartości spełniają określony warunek.  
  
```  
template<class InputIterator, class Predicate>
    typename iterator_traits<InputIterator>::difference_type count_if(
        InputIterator first, 
        InputIterator last, 
        Predicate pred);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iteratora wejściowych adresowania położenie pierwszego elementu w zakresie do wyszukania.  
  
 `last`  
 Iteratora wejściowych adresowania pozycji w jednym ostatniego elementu w zakresie do wyszukania.  
  
 `_Pred`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje warunek muszą być spełnione, jeśli element ma być traktowane. Predykat przyjmuje jeden argument i zwraca **true** lub **false**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów, które spełniają warunek określony przez predykat.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja szablonu jest generalizacji algorytmu [liczby](../standard-library/algorithm-functions.md#count), zastępowanie predykat "jest równa określonej wartości" z dowolnym predykatu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_count_if.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
bool greater10(int value)  
{  
    return value >10;  
}  
  
int main()  
{  
    using namespace std;  
    vector<int> v1;  
    vector<int>::iterator Iter;  
  
    v1.push_back(10);  
    v1.push_back(20);  
    v1.push_back(10);  
    v1.push_back(40);  
    v1.push_back(10);  
  
    cout << "v1 = ( ";  
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)  
        cout << *Iter << " ";  
    cout << ")" << endl;  
  
    vector<int>::iterator::difference_type result1;  
    result1 = count_if(v1.begin(), v1.end(), greater10);  
    cout << "The number of elements in v1 greater than 10 is: "  
         << result1 << "." << endl;  
}  
```  
  
```Output  
v1 = ( 10 20 10 40 10 )  
The number of elements in v1 greater than 10 is: 2.  
```  
  
##  <a name="equal"></a>  Równości  
 Porównuje dwa zakresy elementów równości lub korelacji w znaczeniu, określony przez predykat binarnego.  
  
 Użyj `std::equal` podczas porównywania elementów w różne typy kontenera (na przykład `vector` i `list`) lub podczas porównywania typów różnych elementów lub gdy chcesz porównać zakresy podrzędne kontenerów. W przeciwnym razie podczas porównywania elementów tego samego typu w tym samym typie kontenera, użyj niebędący elementem członkowskim `operator==` dostarczanym dla każdego kontenera.  
  
 Użyj podwójnego range overloads w języku C ++ 14 kodu, ponieważ przeciążeń, które przyjmuje tylko jednego iteratora drugiego zakresu nie wykrywa różnice, jeśli drugi zakres jest dłuższa niż pierwszy zakres i spowoduje niezdefiniowane zachowanie, jeśli drugi zakres jest krótszy od pierwszego zakresu.  
  
```  
template<class InputIterator1, class InputIterator2>  
bool equal(  
    InputIterator1  First1,  
    InputIterator1  Last1,  
    InputIterator2  First2);   
  
template<class InputIterator1, class InputIterator2, class BinaryPredicate>  
bool equal(  
    InputIterator1  First1,  
    InputIterator1  Last1,  
    InputIterator2  First2,  
    BinaryPredicate Comp); // C++14  
  
template<class InputIterator1, class InputIterator2>  
bool equal(  
    InputIterator1  First1,  
    InputIterator1  Last1,  
    InputIterator2  First2,  
    InputIterator2  Last2);  
  
template<class InputIterator1, class InputIterator2, class BinaryPredicate>  
bool equal(  
    InputIterator1  First1,  
    InputIterator1  Last1,  
    InputIterator2  First2,  
    InputIterator2  Last2,  
    BinaryPredicate Comp);  
```  
  
### <a name="parameters"></a>Parametry  
 `First1`  
 Iteratora wejściowych adresowania położenie pierwszego elementu w zakresie od pierwszego do sprawdzenia.  
  
 `Last1`  
 Iteratora wejściowych adresowania jedną pozycję po ostatnim elementem w pierwszy zakres do sprawdzenia.  
  
 `First2`  
 Iteratora wejściowych adresowania położenie pierwszego elementu w drugi zakres do sprawdzenia.  
  
 `First2`  
 Iteratora wejściowych adresowania pozycja jednego po ostatnim elementem w drugi zakres do sprawdzenia.  
  
 `Comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje warunek muszą być spełnione, jeśli dwa elementy mają zostać pobrane jako równoważne. Predykat binarne przyjmuje dwa argumenty i zwraca **true** po spełnieniu i **false** gdy nie są spełnione.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** tylko wtedy, gdy zakresy są identyczne lub równoważne w binarne predykatu w porównaniu z elementów; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Zakres do wyszukania musi być prawidłowym; Iteratory wszystkie muszą być dereferenceable i ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Jeśli dwa zakresy są takie same długości, złożoności czasu algorytm jest liniowy w liczbę elementów zawartych w zakresie. W przeciwnym razie funkcja natychmiast zwraca `false`.  
  
 Ani `operator==` ani predykatu zdefiniowane przez użytkownika jest wymagana do nałożyć relacji równoważność to symetrycznego, zwrotnej i przechodnie między argumentów.  
  
### <a name="example"></a>Przykład  
  
```cpp  
#include <iostream>  
#include <vector>  
#include <algorithm>  
  
using namespace std;  
  
int main()  
{  
    vector<int> v1 { 0, 5, 10, 15, 20, 25 };  
    vector<int> v2 { 0, 5, 10, 15, 20, 25 };  
    vector<int> v3 { 0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50 };  
  
    // Using range-and-a-half equal:  
    bool b = equal(v1.begin(), v1.end(), v2.begin());  
    cout << "v1 and v2 are equal: "  
       << b << endl; // true, as expected  
  
    b = equal(v1.begin(), v1.end(), v3.begin());  
    cout << "v1 and v3 are equal: "  
       << b << endl; // true, surprisingly  
  
    // Using dual-range equal:  
    b = equal(v1.begin(), v1.end(), v3.begin(), v3.end());  
    cout << "v1 and v3 are equal with dual-range overload: "  
       << b << endl; // false  
  
    return 0;  
}  
  
```  
  
##  <a name="equal_range"></a>  equal_range  
 Podany zakres uporządkowanej znajduje Podzakres, w którym wszystkie elementy są równoważne z danej wartości.  
  
```  
template<class ForwardIterator, class Type>  
pair<ForwardIterator, ForwardIterator> equal_range(  
    ForwardIterator first,  
    ForwardIterator last,   
    const Type& val);

template<class ForwardIterator, class Type, class Predicate>  
pair<ForwardIterator, ForwardIterator> equal_range(  
    ForwardIterator first,  
    ForwardIterator last,   
    const Type& val,   
    Predicate comp);  
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Iterator do przodu adresowania położenie pierwszego elementu w zakresie do wyszukania.  
  
 `last`  
 Iterator do przodu adresowania pozycji w jednym ostatniego elementu w zakresie do wyszukania.  
  
 `val`  
 Wartość wyszukane w zakresie uporządkowanej.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje znaczeniu, w której jeden element jest mniejsza niż innym.  
  
### <a name="return-value"></a>Wartość zwracana  
 Para do przodu Iteratory określające Podzakres, zawartych w zakresie wyszukiwana, w których wszystkie elementy są równoważne `val` w tym sensie, zdefiniowany przez predykat binarny używany (albo `comp` lub wartość domyślną, mniej-niż).  
  
 Jeśli nie elementy w zakresie są równoważne `val`, para zwrócony do przodu Iteratory są takie same i określ punkt gdzie `val` może zostać wstawiony bez zakłócania kolejności zakresu.  
  
### <a name="remarks"></a>Uwagi  
 Jest pierwszym iteratora pary zwrócona przez algorytm [lower_bound](../standard-library/algorithm-functions.md#lower_bound), a drugi iteratora jest [upper_bound](../standard-library/algorithm-functions.md#upper_bound).  
  
 Zakres muszą być posortowane według predykatu dostarczony do `equal_range`. Na przykład, jeśli zamierzasz użyć-niż predykatu, zakres muszą być posortowane w kolejności malejącej.  
  
 Elementy w Podzakres prawdopodobnie pusta, zdefiniowane przez pary Iteratory zwrócony przez `equal_range` odpowiada `val` w tym sensie, zdefiniowany przez predykat używane.  
  
 Złożoność algorytm jest logarytmiczna dla Iteratory dostęp losowy i liniowej, w przeciwnym razie wartość o liczbie kroków proporcjonalny do ( `last`  -  `first`).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_equal_range.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // greater<int>()  
#include <iostream>  
#include <string>  
using namespace std;  
  
template<class T> void dump_vector( const vector<T>& v, pair< typename vector<T>::iterator, typename vector<T>::iterator > range )  
{  
    // prints vector v with range delimited by [ and ]  
  
    for( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )  
    {  
        if( i == range.first )  
        {  
            cout << "[ ";  
        }  
        if( i == range.second )  
        {  
            cout << "] ";  
        }  
  
        cout << *i << " ";  
    }  
    cout << endl;  
}  
  
template<class T> void equal_range_demo( const vector<T>& original_vector, T val )  
{  
    vector<T> v(original_vector);  
  
    sort( v.begin(), v.end() );  
    cout << "Vector sorted by the default binary predicate <:" << endl << '\t';  
    for( vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )  
    {  
        cout << *i << " ";  
    }  
    cout << endl << endl;  
  
    pair< vector<T>::iterator, vector<T>::iterator > result  
        = equal_range( v.begin(), v.end(), val );  
  
    cout << "Result of equal_range with val = " << val << ":" << endl << '\t';  
    dump_vector( v, result );  
    cout << endl;  
}  
  
template<class T, class F> void equal_range_demo( const vector<T>& original_vector, T val, F pred, string predname )  
{  
    vector<T> v(original_vector);  
  
    sort( v.begin(), v.end(), pred );  
    cout << "Vector sorted by the binary predicate " << predname << ":" << endl << '\t';  
    for( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )  
    {  
        cout << *i << " ";  
    }  
    cout << endl << endl;  
  
    pair< typename vector<T>::iterator, typename vector<T>::iterator > result  
        = equal_range( v.begin(), v.end(), val, pred );  
  
    cout << "Result of equal_range with val = " << val << ":" << endl << '\t';  
    dump_vector( v, result );  
    cout << endl;  
}  
  
// Return whether absolute value of elem1 is less than absolute value of elem2  
bool abs_lesser( int elem1, int elem2 )  
{  
    return abs(elem1) < abs(elem2);  
}  
  
// Return whether string l is shorter than string r  
bool shorter_than(const string& l, const string& r)  
{  
    return l.size() < r.size();  
}  
  
int main()  
{  
    vector<int> v1;  
  
    // Constructing vector v1 with default less than ordering  
    for( int i = -1; i <= 4; ++i )  
    {  
        v1.push_back(i);  
    }  
  
    for( int i =-3; i <= 0; ++i )  
    {  
        v1.push_back( i );  
    }  
  
    equal_range_demo( v1, 3 );  
    equal_range_demo( v1, 3, greater<int>(), "greater" );  
    equal_range_demo( v1, 3, abs_lesser, "abs_lesser" );  
  
    vector<string> v2;  
  
    v2.push_back("cute");  
    v2.push_back("fluffy");  
    v2.push_back("kittens");  
    v2.push_back("fun");  
    v2.push_back("meowmeowmeow");  
    v2.push_back("blah");  
  
    equal_range_demo<string>( v2, "fred" );  
    equal_range_demo<string>( v2, "fred", shorter_than, "shorter_than" );  
}  
  
```  
  
##  <a name="fill"></a>  wypełnienia  
 Przypisuje tę samą nową wartość każdemu elementowi w określonym zakresie.  
  
```  
template<class ForwardIterator, class Type>  
void fill(
    ForwardIterator first, 
    ForwardIterator last, 
    const Type& val);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterator do przodu adresowania położenie pierwszego elementu w zakresie do można przechodzić.  
  
 `last`  
 Iterator do przodu adresowania pozycji w jednym ostatniego elementu w zakresie do można przechodzić.  
  
 `val`  
 Wartość do przypisania do elementów w zakresie [ `first`, `last`).  
  
### <a name="remarks"></a>Uwagi  
 Zakres docelowy musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać. Złożoność jest liniowa o rozmiarze z zakresu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_fill.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
  
   cout << "Vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // Fill the last 5 positions with a value of 2  
   fill( v1.begin( ) + 5, v1.end( ), 2 );  
  
   cout << "Modified v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
```Output  
Vector v1 = ( 0 5 10 15 20 25 30 35 40 45 )  
Modified v1 = ( 0 5 10 15 20 2 2 2 2 2 )  
```  
  
##  <a name="fill_n"></a>  fill_n  
 Przypisuje nową wartość do określonej liczby elementów na początku zakresu z określonym elementem.  
  
```  
template<class OutputIterator, class Size, class Type>  
OutputIterator fill_n(
    OutputIterator First, 
    Size Count, 
    const Type& Val);   
```  
  
### <a name="parameters"></a>Parametry  
 `First`  
 Iterator dane wyjściowe adresowania położenie pierwszego elementu w zakresie można przypisać wartość `Val`.  
  
 `Count`  
 Podpisem lub unsigned integer — typ określająca liczbę elementów do przypisania wartości.  
  
 `Val`  
 Wartość do przypisania do elementów w zakresie [ `First`, *pierwszy + liczba*).  
  
### <a name="return-value"></a>Wartość zwracana  
 Wypełnione iteratora do elementu poniżej ostatniego elementu, jeśli `Count` > zero, w przeciwnym razie pierwszy element.  
  
### <a name="remarks"></a>Uwagi  
 Zakres docelowy musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać. Złożoność jest liniowa o rozmiarze z zakresu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_fill_n.cpp  
// compile using /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main()   
{  
    using namespace std;  
    vector <int> v;  
  
    for ( auto i = 0 ; i < 9 ; ++i )  
        v.push_back( 0 );  
  
    cout << "  vector v = ( " ;  
    for ( const auto &w : v )  
        cout << w << " ";  
    cout << ")" << endl;  
  
    // Fill the first 3 positions with a value of 1, saving position.  
    auto pos = fill_n( v.begin(), 3, 1 );  
  
    cout << "modified v = ( " ;  
    for ( const auto &w : v )  
        cout << w << " ";  
    cout << ")" << endl;  
  
    // Fill the next 3 positions with a value of 2, using last position.  
    fill_n( pos, 3, 2 );  
  
    cout << "modified v = ( " ;  
    for ( const auto &w : v )  
        cout << w << " ";  
    cout << ")" << endl;  
  
    // Fill the last 3 positions with a value of 3, using relative math.  
    fill_n( v.end()-3, 3, 3 );  
  
    cout << "modified v = ( " ;  
    for ( const auto &w : v )  
        cout << w << " ";  
    cout << ")" << endl;  
}  
  
```  
  
##  <a name="find"></a>  Znajdź  
 Lokalizuje pozycję pierwszego wystąpienia elementu w zakresie, który ma określoną wartość.  
  
```  
template<class InputIterator, class T>  
InputIterator find(
    InputIterator first, 
    InputIterator last,   
    const T& val);  
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Iteratora wejściowych adresowania położenie pierwszego elementu w zakresie mają być wyszukiwane określonej wartości.  
  
 `last`  
 Iteratora wejściowych adresowania jedną pozycję poza ostatniego elementu w zakresie mają być wyszukiwane określonej wartości.  
  
 `val`  
 Wartość, które mają być wyszukiwane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wejściowy iteratora adresowania pierwszego wystąpienia określonej wartości zakresu, w którym wykonywane jest wyszukiwanie. Jeśli element nie zostanie znaleziony o równoważnej wartości, zwraca `last`.  
  
### <a name="remarks"></a>Uwagi  
 `operator==` Używany do określenia pasuje do elementu i określona wartość musi nałożyć równoważność stosunek argumentów.  
  
 Dla przykładu kodu za pomocą `find()`, zobacz [find_if](../standard-library/algorithm-functions.md#find_if).  
  
##  <a name="find_end"></a>  find_end —  
 Wyszukuje w zakresie ostatnią podsekwencję, która jest identyczna z określoną sekwencją lub jest równoważna w sensie określonym przez predykat binarny.  
  
```  
template<class ForwardIterator1, class ForwardIterator2>  
ForwardIterator1 find_end(  
    ForwardIterator1 First1,   
    ForwardIterator1 Last1,  
    ForwardIterator2 First2,   
    ForwardIterator2 Last2);  

template<class ForwardIterator1, class ForwardIterator2, class Pred>  
ForwardIterator1 find_end(  
    ForwardIterator1 First1,   
    ForwardIterator1 Last1,  
    ForwardIterator2 First2,   
    ForwardIterator2 Last2,  
    Pred Comp);  
```  
  
### <a name="parameters"></a>Parametry  
 `First1`  
 Iterator do przodu adresowania położenie pierwszego elementu w zakresie do wyszukania.  
  
 `Last1`  
 Iterator do przodu adresowania pozycji w jednym ostatniego elementu w zakresie do wyszukania.  
  
 `First2`  
 Iterator do przodu adresowania położenie pierwszego elementu w zakresie do wyszukania.  
  
 `Last2`  
 Iterator do przodu adresowania pozycji w jednym ostatniego elementu w zakresie do wyszukania.  
  
 `Comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje warunek muszą być spełnione, jeśli dwa elementy mają zostać pobrane jako równoważne. Predykat binarne przyjmuje dwa argumenty i zwraca **true** po spełnieniu i **false** gdy nie są spełnione.  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator do przodu, adresowania położenie pierwszego elementu ostatniego podsekwencji w [First1, Last1) odpowiadającego podanej sekwencji [First2, Nazwisko2).  
  
### <a name="remarks"></a>Uwagi  
 `operator==` Używany do określenia pasuje do elementu i określona wartość musi nałożyć równoważność stosunek argumentów.  
  
 Zakresy odwołania musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i, w ramach każdej sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_find_end.cpp  
// compile with: /EHsc  
#include <vector>  
#include <list>  
#include <algorithm>  
#include <iostream>  
  
// Return whether second element is twice the first  
bool twice ( int elem1, int elem2 )  
{  
   return 2 * elem1 == elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1, v2;  
   list <int> L1;  
   vector <int>::iterator Iter1, Iter2;  
   list <int>::iterator L1_Iter, L1_inIter;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
  
   int ii;  
   for ( ii = 1 ; ii <= 4 ; ii++ )  
   {  
      L1.push_back( 5 * ii );  
   }  
  
   int iii;  
   for ( iii = 2 ; iii <= 4 ; iii++ )  
   {  
      v2.push_back( 10 * iii );  
   }  
  
   cout << "Vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "List L1 = ( " ;  
   for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )  
      cout << *L1_Iter << " ";  
   cout << ")" << endl;  
  
   cout << "Vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
      cout << ")" << endl;  
  
   // Searching v1 for a match to L1 under identity  
   vector <int>::iterator result1;  
   result1 = find_end ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );  
  
   if ( result1 == v1.end( ) )  
      cout << "There is no match of L1 in v1."  
           << endl;  
   else  
      cout << "There is a match of L1 in v1 that begins at "  
           << "position "<< result1 - v1.begin( ) << "." << endl;  
  
   // Searching v1 for a match to L1 under the binary predicate twice  
   vector <int>::iterator result2;  
   result2 = find_end ( v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );  
  
   if ( result2 == v1.end( ) )  
      cout << "There is no match of L1 in v1."  
           << endl;  
   else  
      cout << "There is a sequence of elements in v1 that "  
           << "are equivalent to those\n in v2 under the binary "  
           << "predicate twice and that begins at position "  
           << result2 - v1.begin( ) << "." << endl;  
}  
```  
  
```Output  
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )  
List L1 = ( 5 10 15 20 )  
Vector v2 = ( 20 30 40 )  
There is a match of L1 in v1 that begins at position 7.  
There is a sequence of elements in v1 that are equivalent to those  
 in v2 under the binary predicate twice and that begins at position 8.  
```  
  
##  <a name="find_first_of"></a>  find_first_of —  
 Wyszukuje pierwsze wystąpienie którejś z kilku wartości w zakresie docelowym lub pierwsze wystąpienie któregoś z kilku elementów, które są równoważne w sensie określonym przez predykat binarny dla określonego zestawu elementów.  
  
```  
template<class ForwardIterator1, class ForwardIterator2>  
ForwardIterator1 find_first_of(    
    ForwardIterator1  first1,  
    ForwardIterator1 Last1,  
    ForwardIterator2  first2,  
    ForwardIterator2 Last2);  
  
template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>  
ForwardIterator1 find_first_of(  
    ForwardIterator1  first1,  
    ForwardIterator1 Last1,  
    ForwardIterator2  first2,  
    ForwardIterator2 Last2,  
    BinaryPredicate  comp);  
```  
  
### <a name="parameters"></a>Parametry  
  `first1`  
 Iterator do przodu adresowania położenie pierwszego elementu w zakresie do wyszukania.  
  
 `last1`  
 Iterator do przodu adresowania pozycji w jednym ostatniego elementu w zakresie do wyszukania.  
  
  `first2`  
 Iterator do przodu adresowania położenie pierwszego elementu w zakresie do dopasowania.  
  
 `last2`  
 Iterator do przodu adresowania pozycji w jednym ostatniego elementu w zakresie do dopasowania.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje warunek muszą być spełnione, jeśli dwa elementy mają zostać pobrane jako równoważne. Predykat binarne przyjmuje dwa argumenty i zwraca **true** po spełnieniu i **false** gdy nie są spełnione.  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator do przodu, adresowania położenie pierwszego elementu pierwszy podsekwencji, odpowiadający określonej sekwencji lub jest równoważna w znaczeniu, określony przez predykat binarnego.  
  
### <a name="remarks"></a>Uwagi  
 `operator==` Używany do określenia pasuje do elementu i określona wartość musi nałożyć równoważność stosunek argumentów.  
  
 Zakresy odwołania musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i, w ramach każdej sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_find_first_of.cpp  
// compile with: /EHsc  
#include <vector>  
#include <list>  
#include <algorithm>  
#include <iostream>  
  
// Return whether second element is twice the first  
bool twice ( int elem1, int elem2 )  
{  
   return 2 * elem1 == elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1, v2;  
   list <int> L1;  
   vector <int>::iterator Iter1, Iter2;  
   list <int>::iterator L1_Iter, L1_inIter;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
  
   int ii;  
   for ( ii = 3 ; ii <= 4 ; ii++ )  
   {  
      L1.push_back( 5 * ii );  
   }  
  
   int iii;  
   for ( iii = 2 ; iii <= 4 ; iii++ )  
   {  
      v2.push_back( 10 * iii );  
   }  
  
   cout << "Vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "List L1 = ( " ;  
   for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )  
      cout << *L1_Iter << " ";  
   cout << ")" << endl;  
  
   cout << "Vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
      cout << ")" << endl;  
  
   // Searching v1 for first match to L1 under identity  
   vector <int>::iterator result1;  
   result1 = find_first_of ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );  
  
   if ( result1 == v1.end( ) )  
      cout << "There is no match of L1 in v1."  
           << endl;  
   else  
      cout << "There is at least one match of L1 in v1"  
           << "\n and the first one begins at "  
           << "position "<< result1 - v1.begin( ) << "." << endl;  
  
   // Searching v1 for a match to L1 under the binary predicate twice  
   vector <int>::iterator result2;  
   result2 = find_first_of ( v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );  
  
   if ( result2 == v1.end( ) )  
      cout << "There is no match of L1 in v1."  
           << endl;  
   else  
      cout << "There is a sequence of elements in v1 that "  
           << "are equivalent\n to those in v2 under the binary "  
           << "predicate twice\n and the first one begins at position "  
           << result2 - v1.begin( ) << "." << endl;  
}  
```  
  
```Output  
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )  
List L1 = ( 15 20 )  
Vector v2 = ( 20 30 40 )  
There is at least one match of L1 in v1  
 and the first one begins at position 3.  
There is a sequence of elements in v1 that are equivalent  
 to those in v2 under the binary predicate twice  
 and the first one begins at position 2.  
```  
  
##  <a name="find_if"></a>  find_if  
 Lokalizuje pozycję pierwszego wystąpienia elementu w zakresie, który spełnia określony warunek.  
  
```  
template<class InputIterator, class Predicate>  
InputIterator find_if(
    InputIterator first, 
    InputIterator last, 
    Predicate pred);  
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Iteratora wejściowych adresowania położenie pierwszego elementu w zakresie do wyszukania.  
  
 `last`  
 Iteratora wejściowych adresowania pozycji w jednym ostatniego elementu w zakresie do wyszukania.  
  
 `pred`  
 Obiekt zdefiniowane przez użytkownika funkcji predykatu lub [wyrażenia lambda](../cpp/lambda-expressions-in-cpp.md) definiujący warunek muszą być spełnione przez element wyszukane. Predykat przyjmuje jeden argument i zwraca `true` (spełnione) lub `false` (nie zostały spełnione). Podpis `pred` musi być skutecznie `bool pred(const T& arg);`, gdzie `T` jest typem, do którego `InputIterator` można niejawnie przekonwertować podczas wyłuskiwany. `const` — Słowo kluczowe jest wyświetlany tylko w celu zilustrowania czy obiekt funkcji lub lambda nie należy modyfikować argument.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wejściowy iteratora odnoszący się do pierwszego elementu w zakresie spełnia warunek określony przez predykat (predykat powoduje `true`). Jeśli element nie zostanie znaleziony do zaspokojenia predykatu, zwraca `last`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja szablonu jest generalizacji algorytmu [znaleźć](../standard-library/algorithm-functions.md#find), zastępowanie predykat "jest równa określonej wartości" z dowolnym predykatu. Logiczne przeciwne (Znajdź pierwszy element, który nie spełnia predykat), można znaleźć [find_if_not —](../standard-library/algorithm-functions.md#find_if_not).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cl.exe /W4 /nologo /EHsc /MTd  
#include <vector>  
#include <algorithm>  
#include <iostream>  
#include <string>  
  
using namespace std;  
  
template <typename S> void print(const S& s) {  
    for (const auto& p : s) {  
        cout << "(" << p << ") ";  
    }  
    cout << endl;  
}  
  
// Test std::find()  
template <class InputIterator, class T>  
void find_print_result(InputIterator first, InputIterator last, const T& value) {  
  
    // call <algorithm> std::find()  
    auto p = find(first, last, value);  
  
    cout << "value " << value;  
    if (p == last) {  
        cout << " not found." << endl;  
    } else {  
        cout << " found." << endl;  
    }  
}  
  
// Test std::find_if()  
template <class InputIterator, class Predicate>  
void find_if_print_result(InputIterator first, InputIterator last,  
    Predicate Pred, const string& Str) {  
  
    // call <algorithm> std::find_if()  
    auto p = find_if(first, last, Pred);  
  
    if (p == last) {  
        cout << Str << " not found." << endl;  
    } else {  
        cout << "first " << Str << " found: " << *p << endl;  
    }  
}  
  
// Function to use as the UnaryPredicate argument to find_if() in this example  
bool is_odd_int(int i) {  
    return ((i % 2) != 0);  
}  
  
int main()  
{  
    // Test using a plain old array.  
    const int x[] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };  
    cout << "array x[] contents: ";  
    print(x);  
    // Using non-member std::begin()/std::end() to get input iterators for the plain old array.  
    cout << "Test std::find() with array..." << endl;  
    find_print_result(begin(x), end(x), 10);  
    find_print_result(begin(x), end(x), 42);  
    cout << "Test std::find_if() with array..." << endl;  
    find_if_print_result(begin(x), end(x), is_odd_int, "odd integer"); // function name  
    find_if_print_result(begin(x), end(x), // lambda  
        [](int i){ return ((i % 2) == 0); }, "even integer");  
  
    // Test using a vector.  
    vector<int> v;  
    for (int i = 0; i < 10; ++i) {  
        v.push_back((i + 1) * 10);  
    }  
    cout << endl << "vector v contents: ";  
    print(v);  
    cout << "Test std::find() with vector..." << endl;  
    find_print_result(v.begin(), v.end(), 20);  
    find_print_result(v.begin(), v.end(), 12);  
    cout << "Test std::find_if() with vector..." << endl;  
    find_if_print_result(v.begin(), v.end(), is_odd_int, "odd integer");  
    find_if_print_result(v.begin(), v.end(), // lambda  
        [](int i){ return ((i % 2) == 0); }, "even integer");  
}  
  
```  
  
##  <a name="find_if_not"></a>  find_if_not —  
 Zwraca pierwszy element we wskazanym zakresie, który nie spełnia warunku.  
  
```  
template<class InputIterator, class Predicate>  
InputIterator find_if_not(
    InputIterator first, 
    InputIterator last,   
    Predicate pred);  
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Iteratora wejściowych adresowania położenie pierwszego elementu w zakresie do wyszukania.  
  
 `last`  
 Iteratora wejściowych adresowania pozycji w jednym ostatniego elementu w zakresie do wyszukania.  
  
 `pred`  
 Obiekt zdefiniowane przez użytkownika funkcji predykatu lub [wyrażenia lambda](../cpp/lambda-expressions-in-cpp.md) definiuje warunku nie można spełnić przez element wyszukane. Predykat przyjmuje jeden argument i zwraca `true` (spełnione) lub `false` (nie zostały spełnione). Podpis `pred` musi być skutecznie `bool pred(const T& arg);`, gdzie `T` jest typem, do którego `InputIterator` można niejawnie przekonwertować podczas wyłuskiwany. `const` — Słowo kluczowe jest wyświetlany tylko w celu zilustrowania czy obiekt funkcji lub lambda nie należy modyfikować argument.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wejściowy iteratora odnoszący się do pierwszego elementu w zakresie, który nie spełnia warunek określony przez predykat (predykat powoduje `false`). Jeśli wszystkie elementy spełniają predykat (predykat powoduje `true` dla każdego elementu), zwraca `last`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja szablonu jest generalizacji algorytmu [znaleźć](../standard-library/algorithm-functions.md#find), zastępowanie predykat "jest równa określonej wartości" z dowolnym predykatu. Logiczne przeciwne (Znajdź pierwszy element, który spełnia predykat), można znaleźć [find_if](../standard-library/algorithm-functions.md#find_if).  
  
 W przykładzie kodu łatwo pasujący do `find_if_not()`, zobacz [find_if](../standard-library/algorithm-functions.md#find_if).  
  
##  <a name="for_each"></a>  for_each  
 Stosuje określony obiekt funkcji do każdego elementu w kolejności do przodu w zakresie i zwraca obiekt funkcji.  
  
```  
template<class InputIterator, class Function>  
Function for_each(
    InputIterator first, 
    InputIterator last, 
    Function _Func);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Adresowanie położenie pierwszego elementu w zakresie działały na iteratora wejściowego.  
  
 `last`  
 Wejściowy iteratora adresowania pozycji w jednym ostatniego elementu w zakresie zasilaniu.  
  
 `_Func`  
 Obiekt funkcji zdefiniowanej przez użytkownika, który jest stosowany do każdego elementu w zakresie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Kopia obiekt funkcji po zastosowaniu do wszystkich elementów w zakresie.  
  
### <a name="remarks"></a>Uwagi  
 Algorytm `for_each` jest bardzo elastyczne, umożliwiając modyfikacja każdego elementu w zakresie w sposób inny, określone przez użytkownika. Funkcje przechowywaną może ponownie w postaci zmodyfikowane przez przekazanie innych parametrów. Funkcje zdefiniowane przez użytkownika mogą się gromadzić informacje w stan wewnętrzny, który algorytm może zwrócić po przetworzeniu wszystkich elementów w zakresie.  
  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i, w ramach sekwencji ostatniej pozycji musi być dostępny z pierwszego przez przyrostowo zmieniać.  
  
 Złożoność jest liniowa z co najwyżej ( `last`  -   `first`) porównania.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_for_each.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
// The function object multiplies an element by a Factor  
template <class Type>  
class MultValue  
{  
private:  
   Type Factor;   // The value to multiply by  
public:  
   // Constructor initializes the value to multiply by  
   MultValue ( const Type& val ) : Factor ( val ) {  
   }  
  
   // The function call for the element to be multiplied  
   void operator ( ) ( Type& elem ) const  
   {  
      elem *= Factor;  
   }  
};  
  
// The function object to determine the average  
class Average  
{  
private:  
   long num;      // The number of elements  
   long sum;      // The sum of the elements  
public:  
   // Constructor initializes the value to multiply by  
   Average ( ) : num ( 0 ) , sum ( 0 )  
   {  
   }  
  
   // The function call to process the next elment  
   void operator ( ) ( int elem ) \  
   {  
      num++;      // Increment the element count  
      sum += elem;   // Add the value to the partial sum  
   }  
  
   // return Average  
   operator double ( )  
   {  
      return  static_cast <double> (sum) /  
      static_cast <double> (num);  
   }  
};  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   // Constructing vector v1  
   int i;  
   for ( i = -4 ; i <= 2 ; i++ )  
   {  
      v1.push_back(  i );  
   }  
  
   cout << "Original vector  v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Using for_each to multiply each element by a Factor  
   for_each ( v1.begin ( ) , v1.end ( ) , MultValue<int> ( -2 ) );  
  
   cout << "Multiplying the elements of the vector v1\n "  
        <<  "by the factor -2 gives:\n v1mod1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // The function object is templatized and so can be  
   // used again on the elements with a different Factor  
   for_each (v1.begin ( ) , v1.end ( ) , MultValue<int> (5 ) );  
  
   cout << "Multiplying the elements of the vector v1mod\n "  
        <<  "by the factor 5 gives:\n v1mod2 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // The local state of a function object can accumulate  
   // information about a sequence of actions that the  
   // return value can make available, here the Average  
   double avemod2 = for_each ( v1.begin ( ) , v1.end ( ) ,  
      Average ( ) );  
   cout << "The average of the elements of v1 is:\n Average ( v1mod2 ) = "  
        << avemod2 << "." << endl;  
}  
```  
  
```Output  
Original vector  v1 = ( -4 -3 -2 -1 0 1 2 ).  
Multiplying the elements of the vector v1  
 by the factor -2 gives:  
 v1mod1 = ( 8 6 4 2 0 -2 -4 ).  
Multiplying the elements of the vector v1mod  
 by the factor 5 gives:  
 v1mod2 = ( 40 30 20 10 0 -10 -20 ).  
The average of the elements of v1 is:  
 Average ( v1mod2 ) = 10.  
```  
  
##  <a name="generate"></a>  Generowanie  
 Przypisuje wartości generowane przez obiekt funkcji do każdego elementu w zakresie.  
  
```  
template<class ForwardIterator, class Generator>  
void generate(
    ForwardIterator first, 
    ForwardIterator last, 
    Generator _Gen);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Adresowanie położenie pierwszego elementu w zakresie, do którego mają można przypisać wartości do przodu iteratora.  
  
 `last`  
 Adresowanie jedną pozycję poza ostatniego elementu w zakresie, do którego mają zostać przypisane wartości do przodu iteratora.  
  
 `_Gen`  
 Funkcja obiekt, który jest wywołać bez argumentów służący do generowania wartości do przypisania do poszczególnych elementów w zakresie.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt funkcja jest wywoływana dla każdego elementu w zakresie i zwracają taką samą wartość za każdym razem, gdy jest to nie jest konieczne. Może, na przykład Odczyt z pliku ani dotyczą i modyfikowania stanu lokalnego. Typ wyniku generator musi być możliwe do przekonwertowania na typ wartości do przodu Iteratory w zakresie.  
  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i, w ramach sekwencji ostatniej pozycji musi być dostępny z pierwszego przez przyrostowo zmieniać.  
  
 Złożoność jest liniowa, z dokładnie ( `last`  -   `first`) wywołań generator są wymagane.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_generate.cpp  
// compile with: /EHsc  
#include <vector>  
#include <deque>  
#include <algorithm>  
#include <iostream>  
#include <ostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Assigning random values to vector integer elements  
   vector <int> v1 ( 5 );  
   vector <int>::iterator Iter1;  
   deque <int> deq1 ( 5 );  
   deque <int>::iterator d1_Iter;  
  
   generate ( v1.begin ( ), v1.end ( ) , rand );  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Assigning random values to deque integer elements  
   generate ( deq1.begin ( ), deq1.end ( ) , rand );  
  
   cout << "Deque deq1 is ( " ;  
   for ( d1_Iter = deq1.begin( ) ; d1_Iter != deq1.end( ) ; d1_Iter++ )  
      cout << *d1_Iter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
Vector v1 is ( 41 18467 6334 26500 19169 ).  
Deque deq1 is ( 15724 11478 29358 26962 24464 ).  
```  
  
##  <a name="generate_n"></a>  generate_n  
 Przypisuje wartości generowanych przez obiekt funkcji do określonej liczby elementów w zakresie, a następnie przywraca pozycji w jednym ostatniego przypisaną wartość.  
  
```  
template<class OutputIterator, class Diff, class Generator>  
void generate_n( 
    OutputIterator First, 
    Diff Count, 
    Generator Gen);  
```  
  
### <a name="parameters"></a>Parametry  
 `First`  
 Dane wyjściowe iteratora adresowania położenie pierwszego elementu w zakresie, do którego mają zostać przypisane wartości.  
  
 `Count`  
 Podpisem lub bez typ całkowity określająca liczbę elementów do przypisania wartości przez funkcję generatora.  
  
 `Gen`  
 Funkcja obiekt, który jest wywołać bez argumentów służący do generowania wartości do przypisania do poszczególnych elementów w zakresie.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt funkcja jest wywoływana dla każdego elementu w zakresie i zwracają taką samą wartość za każdym razem, gdy jest to nie jest konieczne. Może, na przykład Odczyt z pliku ani dotyczą i modyfikowania stanu lokalnego. Typ wyniku generator musi być możliwe do przekonwertowania na typ wartości do przodu Iteratory w zakresie.  
  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i, w ramach sekwencji ostatniej pozycji musi być dostępny z pierwszego przez przyrostowo zmieniać.  
  
 Złożoność jest liniowa, z dokładnie `Count` wywołania do generatora są wymagane.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cl.exe /EHsc /nologo /W4 /MTd  
#include <vector>  
#include <deque>  
#include <iostream>  
#include <string>  
#include <algorithm>  
#include <random>  
  
using namespace std;  
  
template <typename C> void print(const string& s, const C& c) {  
    cout << s;  
  
    for (const auto& e : c) {  
        cout << e << " ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    const int elemcount = 5;  
    vector<int> v(elemcount);  
    deque<int> dq(elemcount);  
  
    // Set up random number distribution  
    random_device rd;  
    mt19937 engine(rd());  
    uniform_int_distribution<int> dist(-9, 9);  
  
    // Call generate_n, using a lambda for the third parameter  
    generate_n(v.begin(), elemcount, [&](){ return dist(engine); });  
    print("vector v is: ", v);  
  
    generate_n(dq.begin(), elemcount, [&](){ return dist(engine); });  
    print("deque dq is: ", dq);  
}  
  
```  
  
##  <a name="includes"></a>  Zawiera  
 Sprawdza, czy jeden posortowany zakres zawiera wszystkie elementy zawarte w drugim posortowanym zakresie, gdzie kryterium szeregowania lub równoważności między elementami może zostać określone przez predykat binarny.  
  
```  
template<class InputIterator1, class InputIterator2>  
bool includes(  
    InputIterator1 first1,  
    InputIterator1 last1,  
    InputIterator2 first2,  
    InputIterator2 last2);  
  
template<class InputIterator1, class InputIterator2, class BinaryPredicate>  
bool includes(  
    InputIterator1 first1,  
    InputIterator1 last1,  
    InputIterator2 first2,  
    InputIterator2 last2,  
    BinaryPredicate comp );  
```  
  
### <a name="parameters"></a>Parametry  
  `first1`  
 Wejściowy iteratora adresowania położenie pierwszego elementu w pierwszym dwa zakresy posortowane źródła do sprawdzenia dla tego, czy wszystkie elementy drugiego znajdują się w pierwszym.  
  
 `last1`  
 Iteratora wejściowych adresowania pozycja jeden po ostatnim elementem w pierwszym dwa zakresy posortowane źródła pod kątem tego, czy wszystkie elementy drugiego znajdują się w pierwszym.  
  
  `first2`  
 Wejściowy iteratora adresowania położenie pierwszego elementu w drugim dwóch kolejnych sortowane zakresów pod kątem tego, czy wszystkie elementy drugiego znajdują się w pierwszym.  
  
 `last2`  
 Wejściowy iteratora adresowania ostatnich pozycji, co ostatnim elementem w drugim dwóch kolejnych sortowane zakresów pod kątem tego, czy wszystkie elementy drugiego znajdują się w pierwszym.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje znaczeniu, w której jeden element jest mniejsza niż innym. Predykat binarne przyjmuje dwa argumenty i zwraca **true** po spełnieniu i **false** gdy nie są spełnione.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli pierwszy zakres posortowane zawiera wszystkie elementy w drugiego zakresu posortowane; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Innym sposobem traktować ten test jest on ustalić, czy drugiego zakresu źródła jest podzbiorem zakresu pierwszego źródła.  
  
 Posortowane zakresów odwołania musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i, w ramach każdej sekwencji ostatniej pozycji musi być dostępny z pierwszego przez przyrostowo zmieniać.  
  
 Jest posortowane zakresy muszą być ustawione jako warunek wstępny stosowanie algorytmu obejmuje zgodnie z tej samej porządkowanie jako źródła do użycia przez algorytm sortowania połączonych zakresów.  
  
 Zakresów nie są modyfikowane przez algorytm **scalania**.  
  
 Typy wartości wejściowych Iteratory musi być mniejsza-niż porównywalne może zostać określona, tak, aby dane dwa elementy, można ustalić czy są równoważne (w tym sensie, że nie jest mniejsza niż drugi) albo że jeden jest mniejsza niż innych. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Mówiąc ściślej algorytm sprawdza, czy wszystkie elementy w zakresie posortowane pierwszy pod określony predykat binarne mają równoważne kolejności tych drugiego zakresu posortowane.  
  
 Złożoność algorytm jest liniowa z maksymalnie 2 \* (( *Nazwisko1 - first1*)-(* Nazwisko2 - first2 *)) - 1 porównań niepustym zakresów.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_includes.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // For greater<int>( )  
#include <iostream>  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser (int elem1, int elem2 )  
{  
   if ( elem1 < 0 )   
      elem1 = - elem1;  
   if ( elem2 < 0 )   
      elem2 = - elem2;  
   return elem1 < elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1a, v1b;  
   vector <int>::iterator Iter1a,  Iter1b;  
  
   // Constructing vectors v1a & v1b with default less-than ordering  
   int i;  
   for ( i = -2 ; i <= 4 ; i++ )  
   {  
      v1a.push_back(  i );  
   }  
  
   int ii;  
   for ( ii =-2 ; ii <= 3 ; ii++ )  
   {  
      v1b.push_back(  ii  );  
   }  
  
   cout << "Original vector v1a with range sorted by the\n "  
        << "binary predicate less than is v1a = ( " ;  
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )  
      cout << *Iter1a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v1b with range sorted by the\n "  
        <<  "binary predicate less than is v1b = ( " ;  
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )  
      cout << *Iter1b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v2a & v2b with ranges sorted by greater  
   vector <int> v2a ( v1a ) , v2b ( v1b );  
   vector <int>::iterator Iter2a,  Iter2b;  
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );  
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );  
   v2a.pop_back ( );  
  
   cout << "Original vector v2a with range sorted by the\n "  
        <<  "binary predicate greater is v2a = ( " ;  
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )  
      cout << *Iter2a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v2b with range sorted by the\n "  
        <<  "binary predicate greater is v2b = ( " ;  
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )  
      cout << *Iter2b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser  
   vector <int> v3a ( v1a ), v3b ( v1b ) ;  
   vector <int>::iterator Iter3a, Iter3b;  
   reverse (v3a.begin( ), v3a.end( ) );  
   v3a.pop_back ( );  
   v3a.pop_back ( );  
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );  
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser );  
  
   cout << "Original vector v3a with range sorted by the\n "  
        <<  "binary predicate mod_lesser is v3a = ( " ;  
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )  
      cout << *Iter3a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v3b with range sorted by the\n "  
        <<  "binary predicate mod_lesser is v3b = ( " ;  
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )  
      cout << *Iter3b << " ";  
   cout << ")." << endl;  
  
   // To test for inclusion under an asscending order  
   // with the default binary predicate less <int> ( )  
   bool Result1;  
   Result1 = includes ( v1a.begin ( ) , v1a.end ( ) ,  
      v1b.begin ( ) , v1b.end ( ) );  
   if ( Result1 )  
      cout << "All the elements in vector v1b are "  
           << "contained in vector v1a." << endl;  
   else  
      cout << "At least one of the elements in vector v1b "  
           << "is not contained in vector v1a." << endl;  
  
   // To test for inclusion under descending  
   // order specify binary predicate greater<int>( )  
   bool Result2;  
   Result2 = includes ( v2a.begin ( ) , v2a.end ( ) ,  
      v2b.begin ( ) , v2b.end ( ) , greater <int> ( ) );  
   if ( Result2 )  
      cout << "All the elements in vector v2b are "  
           << "contained in vector v2a." << endl;  
   else  
      cout << "At least one of the elements in vector v2b "  
           << "is not contained in vector v2a." << endl;  
  
   // To test for inclusion under a user  
   // defined binary predicate mod_lesser  
   bool Result3;  
   Result3 = includes ( v3a.begin ( ) , v3a.end ( ) ,  
      v3b.begin ( ) , v3b.end ( ) , mod_lesser );  
   if ( Result3 )  
      cout << "All the elements in vector v3b are "  
           << "contained under mod_lesser in vector v3a."  
           << endl;  
   else  
      cout << "At least one of the elements in vector v3b is "  
           << " not contained under mod_lesser in vector v3a."   
           << endl;  
}  
```  
  
```Output  
Original vector v1a with range sorted by the  
 binary predicate less than is v1a = ( -2 -1 0 1 2 3 4 ).  
Original vector v1b with range sorted by the  
 binary predicate less than is v1b = ( -2 -1 0 1 2 3 ).  
Original vector v2a with range sorted by the  
 binary predicate greater is v2a = ( 4 3 2 1 0 -1 ).  
Original vector v2b with range sorted by the  
 binary predicate greater is v2b = ( 3 2 1 0 -1 -2 ).  
Original vector v3a with range sorted by the  
 binary predicate mod_lesser is v3a = ( 0 1 2 3 4 ).  
Original vector v3b with range sorted by the  
 binary predicate mod_lesser is v3b = ( 0 -1 1 -2 2 3 ).  
All the elements in vector v1b are contained in vector v1a.  
At least one of the elements in vector v2b is not contained in vector v2a.  
At least one of the elements in vector v3b is  not contained under mod_lesser in vector v3a.  
```  
  
##  <a name="inplace_merge"></a>  inplace_merge —  
 Łączy elementy z dwóch następujących po sobie posortowanych zakresów w pojedynczy posortowany zakres, gdzie kryterium szeregowania może być określone przez predykat binarny.  
  
```  
template<class BidirectionalIterator>  
void inplace_merge(      
    BidirectionalIterator first,   
    BidirectionalIterator middle,  
    BidirectionalIterator last);  
  
template<class BidirectionalIterator, class Predicate>  
void inplace_merge(  
    BidirectionalIterator first,   
    BidirectionalIterator middle,  
    BidirectionalIterator last,  
    Predicate comp);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterator dwukierunkowego, adresowania położenie pierwszego elementu w pierwszym z dwóch kolejnych sortowane zakresów można łączyć i posortowane w pojedynczy zakres.  
  
 `middle`  
 Iterator dwukierunkowego, adresowania położenie pierwszego elementu w ciągu sekundy dwóch kolejnych sortowane zakresów można łączyć i posortowane w pojedynczy zakres.  
  
 `last`  
 Iterator dwukierunkowego, adresowania jedną pozycję po ostatnim elementem w ciągu sekundy dwóch kolejnych sortowane zakresów można łączyć i posortowane w pojedynczy zakres.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje znaczeniu, w której jeden element jest większa niż innym. Predykat binarne przyjmuje dwa argumenty i powinna zostać zwrócona **true** po pierwszym elementem jest mniejszy od drugiego elementu i **false** inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Posortowane kolejnych zakresów odwołuje się do musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i, w ramach każdej sekwencji ostatniej pozycji musi być dostępny z pierwszego przez przyrostowo zmieniać.  
  
 Posortowane kolejnych zakresów muszą być ustawione jako warunek wstępny stosowania `inplace_merge` algorytm zgodnie z tej samej kolejności jak ma być używany przez algorytm sortowania połączonych zakresów. Operacja jest stabilna jako względną kolejność elementów w obrębie każdego zakresu są zachowywane. Gdy w obu zakresów źródła równoważny elementy, element jest pierwszy zakres poprzedza element od drugiego w zakresie połączone.  
  
 Złożoność zależy ilość dostępnej pamięci, zgodnie z algorytm przydziela pamięć do buforu tymczasowego. Jeśli jest dostępna wystarczająca ilość pamięci, najlepiej jest liniowej z (* ostatni — najpierw*) - 1 porównań; Jeśli brak pamięci pomocniczy jest dostępna, jest najgorszego *N* dziennika *(N)*, gdzie  *N* = (* ostatni — najpierw*).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_inplace_merge.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      //For greater<int>( )  
#include <iostream>  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser ( int elem1, int elem2 )  
{  
   if ( elem1 < 0 )   
      elem1 = - elem1;  
   if ( elem2 < 0 )   
      elem2 = - elem2;  
   return elem1 < elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1, Iter2, Iter3;  
  
   // Constructing vector v1 with default less-than ordering  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   int ii;  
   for ( ii =-5 ; ii <= 0 ; ii++ )  
   {  
      v1.push_back(  ii  );  
   }  
  
   cout << "Original vector v1 with subranges sorted by the\n "  
        <<  "binary predicate less than is  v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // Constructing vector v2 with ranges sorted by greater  
   vector <int> v2 ( v1 );  
   vector <int>::iterator break2;  
   break2 = find ( v2.begin ( ) , v2.end ( ) , -5 );  
   sort ( v2.begin ( ) , break2 , greater<int> ( ) );  
   sort ( break2 , v2.end ( ) , greater<int> ( ) );  
   cout << "Original vector v2 with subranges sorted by the\n "  
        << "binary predicate greater is v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // Constructing vector v3 with ranges sorted by mod_lesser  
   vector <int> v3 ( v1 );  
   vector <int>::iterator break3;  
   break3 = find ( v3.begin ( ) , v3.end ( ) , -5 );  
   sort ( v3.begin ( ) , break3 , mod_lesser );  
   sort ( break3 , v3.end ( ) , mod_lesser );  
   cout << "Original vector v3 with subranges sorted by the\n "  
        << "binary predicate mod_lesser is v3 = ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")" << endl;  
  
   vector <int>::iterator break1;  
   break1 = find (v1.begin ( ) , v1.end ( ) , -5 );  
   inplace_merge ( v1.begin( ), break1, v1.end( ) );  
   cout << "Merged inplace with default order,\n vector v1mod = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To merge inplace in descending order, specify binary   
   // predicate greater<int>( )  
   inplace_merge ( v2.begin( ), break2 , v2.end( ) , greater<int>( ) );  
   cout << "Merged inplace with binary predicate greater specified,\n "  
        << "vector v2mod = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // Applying a user defined (UD) binary predicate mod_lesser  
   inplace_merge ( v3.begin( ), break3, v3.end( ), mod_lesser );  
   cout << "Merged inplace with binary predicate mod_lesser specified,\n "  
        << "vector v3mod = ( " ; ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")" << endl;  
}  
```  
  
```Output  
Original vector v1 with subranges sorted by the  
 binary predicate less than is  v1 = ( 0 1 2 3 4 5 -5 -4 -3 -2 -1 0 )  
Original vector v2 with subranges sorted by the  
 binary predicate greater is v2 = ( 5 4 3 2 1 0 0 -1 -2 -3 -4 -5 )  
Original vector v3 with subranges sorted by the  
 binary predicate mod_lesser is v3 = ( 0 1 2 3 4 5 0 -1 -2 -3 -4 -5 )  
Merged inplace with default order,  
 vector v1mod = ( -5 -4 -3 -2 -1 0 0 1 2 3 4 5 )  
Merged inplace with binary predicate greater specified,  
 vector v2mod = ( 5 4 3 2 1 0 0 -1 -2 -3 -4 -5 )  
Merged inplace with binary predicate mod_lesser specified,  
 vector v3mod = ( 0 0 1 -1 2 -2 3 -3 4 -4 5 -5 )  
```  
  
##  <a name="is_heap"></a>  is_heap  
 Zwraca `true` Jeśli sterty tworzą elementów w określonym zakresie.  
  
```  
template<class RandomAccessIterator>  
bool is_heap(  
    RandomAccessIterator first,  
    RandomAccessIterator last);  

template<class RandomAccessIterator, class BinaryPredicate>  
bool is_heap(  
    RandomAccessIterator first,  
    RandomAccessIterator last,  
    BinaryPredicate comp);   
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iteratora dostępie swobodnym, która wskazuje początek zakresu, aby wyszukać sterty.  
  
 `last`  
 Iteratora dostępie, które wskazuje koniec zakresu.  
  
 `comp`  
 Warunek do testowania na kolejność elementów. Predykat binarne pobiera jeden argument i zwraca `true` lub `false`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `true` Jeśli elementów w określonym zakresie tworzą sterty, `false` czy nie.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca pierwszy funkcji szablonu [is_heap_until —](../standard-library/algorithm-functions.md#is_heap_until) `(` `first ,` `last ) ==` `last`.  
  
 Drugi argument funkcji szablonu  
  
 `is_heap_until` `(`  `first` `,`  `last` `,`  `comp` `) ==`  `last`.  
  
##  <a name="is_heap_until"></a>  is_heap_until —  
 Zwraca iteratora znajduje się w pierwszym elementem w zakresie [ `begin`, `end`) nie spełnia sterty porządkowanie warunku, lub `end` Jeśli zakres formularzy stosu.  
  
```  
template<class RandomAccessIterator>  
RandomAccessIterator is_heap_until(  
    RandomAccessIterator begin,   
    RandomAccessIterator end);  
    
template<class RandomAccessIterator, class BinaryPredicate>   
RandomAccessIterator is_heap_until(  
    RandomAccessIterator begin,   
    RandomAccessIterator end,   
    BinaryPredicate compare);  
```  
  
### <a name="parameters"></a>Parametry  
 `begin`  
 Iterator dostępie swobodnym określająca pierwszy element zakres, sprawdź, czy stosu.  
  
 `end`  
 Iterator dostępie swobodnym, który określa koniec zakresu, aby wyszukać sterty.  
  
 `compare`  
 Predykat binarny określający strict niska, kolejność warunek, który definiuje stosu. Wartość domyślna predykat, gdy `compare` nie określono jest `std::less<>`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `end` określony zakres formularzy sterty lub zawiera jeden lub mniej elementów. W przeciwnym razie zwraca wartość iteratora dla pierwszego elementu znalezione nie spełnia warunku stosu.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy funkcji szablonu zwraca ostatni iteratora `next` w `[ begin , end ]` gdzie `[ begin , next)` jest sterty uporządkowanych według obiekt funkcji `std::less<>`. Jeśli odległość `end - begin < 2`, funkcja zwraca `end`.  
  
 Drugi funkcji szablonu działa tak samo jako pierwszy, z wyjątkiem tego, że używa predykatu `compare` zamiast `std::less<>` jako sterty porządkowanie warunku.  
  
##  <a name="is_partitioned"></a>  is_partitioned  
 Zwraca `true` wszystkie elementy w danym zakresie który należy przetestować `true` dla warunku występować przed elementów, które test `false`.  
  
```  
template<class InputIterator, class BinaryPredicate>  
bool is_partitioned(  
    InputIterator first,   
    InputIterator last,  
    BinaryPredicate comp);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Wejściowy iteratora, który wskazuje, gdzie zaczyna się zakres do sprawdzenia, czy warunek.  
  
 `last`  
 Iterację wejściowych wskazuje koniec zakresu.  
  
 `comp`  
 Warunek do sprawdzenia. To jest udostępniana przez obiekt zdefiniowane przez użytkownika funkcja predykatu, który definiuje warunek muszą być spełnione przez element wyszukane. Predykat pobiera jeden argument i zwraca `true` lub `false`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true, gdy wszystkie elementy z danego zakresu testujące `true` dla warunku występować przed elementów, które test `false`, a w przeciwnym razie zwraca `false`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu `true` tylko wtedy, gdy wszystkie elementy w `[` `first ,` `last )` są podzielone na partycje według `comp`; oznacza to, że wszystkie elementy `X` w `[` `first ,` `last )` dla które `comp (X)` jest PRAWDA wystąpić przed wszystkie elementy `Y` dla którego `comp (Y)` jest `false`.  
  
##  <a name="is_permutation"></a>  is_permutation  
 Zwraca wartość PRAWDA, jeśli oba zakresy zawierają te same elementy, czy elementy są w tej samej kolejności. Użyj podwójnego range overloads w języku C ++ 14 kodu, ponieważ przeciążeń, które przyjmuje tylko jednego iteratora drugiego zakresu nie wykrywa różnice, jeśli drugi zakres jest dłuższa niż pierwszy zakres i spowoduje niezdefiniowane zachowanie, jeśli drugi zakres jest krótszy od pierwszego zakresu.  
  
```  
template<class ForwardIterator1, class ForwardIterator2>  
bool is_permutation(
    ForwardIterator1 First1, 
    ForwardIterator1 Last1, 
    ForwardIterator2 First2);

template<class ForwardIterator1, class ForwardIterator2, class Predicate>  
bool is_permutation(
    ForwardIterator1 First1, 
    ForwardIterator1 Last1, 
    ForwardIterator2 First2, 
    Predicate Pred);

// C++14  
template<class ForwardIterator1, class ForwardIterator2>  
bool is_permutation(
    ForwardIterator1 First1, 
    ForwardIterator1 Last1, 
    ForwardIterator2 First2, 
    ForwardIterator2 Last2);

template<class ForwardIterator1, class ForwardIterator2, class Predicate>  
bool is_permutation(
    ForwardIterator1 First1, 
    ForwardIterator1 Last1, 
    ForwardIterator2 First2, 
    ForwardIterator2 Last2, 
    Predicate Pred);  
```  
  
### <a name="parameters"></a>Parametry  
 `First1`  
 Iterator do przodu, odnoszący się do pierwszego elementu obiektu zakresu.  
  
 `Last1`  
 Iterator do przodu odnoszący po ostatnim elemencie zakresu.  
  
 `First2`  
 Iterator do przodu, odnoszący się do pierwszego elementu obiektu drugiego zakresu, używana na potrzeby porównania.  
  
 `Last2`  
 Iterator do przodu, odnoszący się do jednego po ostatnim elemencie drugiego zakresu, używana na potrzeby porównania.  
  
 `Pred`  
 Predykat testów do pełnienia roli równoważnika i zwraca `bool`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` gdy zakresy można przestawiać tak, aby były identyczne zgodnie z komparatora predykatu; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 `is_permutation` ma złożoność kwadratową w najgorszym przypadku.  
  
 Pierwszy funkcji szablonu zakłada, że są dowolną liczbę elementów w zakres rozpoczynający się od `First2` jest w zasięgu wyznaczonym przez [ `First1`, `Last1`). Jeśli istnieje więcej elementów z drugiego zakresu, są ignorowane. Jeśli są mniejsze, niezdefiniowane zachowanie zostanie przeprowadzona. Trzeci funkcji szablonu (C ++ 14 i nowszych) nie powoduje to założeń.  Obie zwracają `true` tylko wtedy, gdy dla każdego elementu X zakres wskazywany przez [ `First1`, `Last1`) w tym zakresie x, które są dowolną liczbę elementów Y == Y, ponieważ istnieją w początek zakresu w `First2` lub [ `First2, Last2).` tutaj, `operator==` należy wykonać parowania porównanie argumentów.  
  
 Drugi i czwarty szablon funkcje działają tak samo, z wyjątkiem tego, że zastępują one `operator==(X, Y)` z `Pred(X, Y)`. Będzie działać prawidłowo, predykat muszą być symetryczne, zwrotnej i przechodnie.  
  
### <a name="example"></a>Przykład  
  Poniższy przykład przedstawia użycie `is_permutation`:  
  
```cpp  
#include <vector>  
#include <iostream>  
#include <algorithm>  
#include <string>  
  
using namespace std;  
  
int main()  
{  
    vector<int> vec_1{ 2, 3, 0, 1, 4, 5 };  
    vector<int> vec_2{ 5, 4, 0, 3, 1, 2 };  
  
    vector<int> vec_3{ 4, 9, 13, 3, 6, 5 };  
    vector<int> vec_4{ 7, 4, 11, 9, 2, 1 };  
  
    cout << "(1) Compare using built-in == operator: ";  
    cout << boolalpha << is_permutation(vec_1.begin(), vec_1.end(),  
        vec_2.begin(), vec_2.end()) << endl; // true  
  
    cout << "(2) Compare after modifying vec_2: ";  
    vec_2[0] = 6;  
    cout << is_permutation(vec_1.begin(), vec_1.end(),  
        vec_2.begin(), vec_2.end()) << endl; // false  
  
    // Define equivalence as "both are odd or both are even"  
    cout << "(3) vec_3 is a permutation of vec_4: ";  
    cout << is_permutation(vec_3.begin(), vec_3.end(),  
        vec_4.begin(), vec_4.end(),  
        [](int lhs, int rhs) { return lhs % 2 == rhs % 2; }) << endl; // true  
  
    // Initialize a vector using the 's' string literal to specify a std::string  
    vector<string> animals_1{ "dog"s, "cat"s, "bird"s, "monkey"s };  
    vector<string> animals_2{ "donkey"s, "bird"s, "meerkat"s, "cat"s };  
  
    // Define equivalence as "first letters are equal":  
    bool is_perm = is_permutation(animals_1.begin(), animals_1.end(), animals_2.begin(), animals_2.end(),  
        [](const string& lhs, const string& rhs)  
    {  
        return lhs[0] == rhs[0]; //std::string guaranteed to have at least a null terminator  
    });  
  
    cout << "animals_2 is a permutation of animals_1: " << is_perm << endl; // true  
  
    cout << "Press a letter" << endl;  
    char c;  
    cin >> c;  
  
    return 0;  
}  
  
```  
  
##  <a name="is_sorted"></a>  is_sorted  
 Zwraca `true` Jeśli elementów w określonym zakresie są posortowane.  
  
```  
template<class ForwardIterator>  
bool is_sorted(  
    ForwardIterator first,   
    ForwardIterator last);

template<class ForwardIterator, class BinaryPredicate>  
bool is_sorted(  
    ForwardIterator first,   
    ForwardIterator last,   
    BinaryPredicate comp);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterator do przodu, wskazującą, w którym rozpoczyna się zakres do sprawdzenia.  
  
 `last`  
 Iterator do przodu, który wskazuje koniec zakresu.  
  
 `comp`  
 Warunek do sprawdzenia, aby określić kolejność między dwoma elementami. Predykat pobiera jeden argument i zwraca `true` lub `false`. Spowoduje to wykonanie tych samych zadań `operator<`.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca pierwszy funkcji szablonu [is_sorted_until —](http://msdn.microsoft.com/en-us/bbad99d0-deaa-4fe6-ae58-eb5b3e4dded0)`( first, last ) == last`. `operator<` Funkcja wykonuje porównywanie kolejności.  
  
 Zwraca drugie funkcji szablonu `is_sorted_until( first, last , comp ) == last`. `comp` Funkcji predykatu wykonuje porównywanie kolejności.  
  
##  <a name="is_sorted_until"></a>  is_sorted_until —  
 Zwraca `ForwardIterator` ustawiono który ostatni element, który jest posortowane z określonego zakresu.  
  
 Druga wersja pozwala zapewnić `BinaryPredicate` funkcja, która zwraca `true` po dwa elementy danego są posortowane, i `false` inaczej.  
  
```  
template<class ForwardIterator>  
    ForwardIterator is_sorted_until(  
        ForwardIterator first,   
        ForwardIterator last  
    );  
template<class ForwardIterator, class BinaryPredicate>  
    ForwardIterator is_sorted_until(  
        ForwardIterator first,   
        ForwardIterator last,   
        BinaryPredicate comp  
    );  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterator do przodu, która wskazuje, gdzie zaczyna się zakres do sprawdzenia.  
  
 `last`  
 Iterator do przodu, który wskazuje koniec zakresu.  
  
 `comp`  
 Warunek do sprawdzenia, aby określić kolejność między dwoma elementami. Predykat pobiera jeden argument i zwraca `true` lub `false`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `ForwardIterator` ustawiona na ostatni element posortowane. Posortowane ciąg rozpoczyna się od `first`.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy funkcji szablonu zwraca ostatni iteratora `next` w `[` `first ,` `last ]` , aby `[` `first , next)` jest posortowana sekwencji uporządkowanych według `operator<`. Jeśli `distance()` `< 2` funkcja zwraca `last`.  
  
 Drugi funkcji szablonu działa tak samo, z wyjątkiem tego, że zastępuje `operator<(X, Y)` z `comp (X, Y)`.  
  
##  <a name="iter_swap"></a>  iter_swap —  
 Wymienia dwie wartości, do których odnosi się para określonych iteratorów.  
  
```  
template<class ForwardIterator1, class ForwardIterator2>  
void iter_swap( ForwardIterator1 left, ForwardIterator2 right );  
  
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Jeden z Iteratory do przodu, którego wartość ma być wymieniane.  
  
 `right`  
 Sekundę iteratorów do przodu, którego wartość ma być wymieniane.  
  
### <a name="remarks"></a>Uwagi  
 `swap` należy używać preference celu i **ter_swap**, która została uwzględniona w standardu C++ dla zgodności z poprzednimi wersjami. Jeśli `Fit1` i `Fit2` są następnie do przodu Iteratory `iter_swap` ( `Fit1`, `Fit2` ), jest odpowiednikiem `swap` (* `Fit1`, \* `Fit2` ).  
  
 Typy wartości wejściowych Iteratory do przodu musi mieć taką samą wartość.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_iter_swap.cpp  
// compile with: /EHsc  
#include <vector>  
#include <deque>  
#include <algorithm>  
#include <iostream>  
#include <ostream>  
  
using namespace std;  
class CInt;  
ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
class CInt  
{  
public:  
   CInt( int n = 0 ) : m_nVal( n ){}  
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}  
   CInt&   operator=( const CInt& rhs ) { m_nVal =  
   rhs.m_nVal; return *this; }  
   bool operator<( const CInt& rhs ) const  
      { return ( m_nVal < rhs.m_nVal );}  
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
private:  
   int m_nVal;  
};  
  
inline ostream& operator<<( ostream& osIn, const CInt& rhs )  
{  
   osIn << "CInt(" << rhs.m_nVal << ")";  
   return osIn;  
}  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser ( int elem1, int elem2 )  
{  
   if ( elem1 < 0 )  
      elem1 = - elem1;  
   if ( elem2 < 0 )  
      elem2 = - elem2;  
   return elem1 < elem2;  
};  
  
int main( )  
{  
   CInt c1 = 5, c2 = 1, c3 = 10;  
   deque<CInt> deq1;  
   deque<CInt>::iterator d1_Iter;  
  
   deq1.push_back ( c1 );  
   deq1.push_back ( c2 );  
   deq1.push_back ( c3 );  
  
   cout << "The original deque of CInts is deq1 = (";  
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )  
      cout << " " << *d1_Iter << ",";  
   d1_Iter = --deq1.end( );  
   cout << " " << *d1_Iter << " )." << endl;  
  
   // Exchanging first and last elements with iter_swap  
   iter_swap ( deq1.begin ( ) , --deq1.end ( ) );  
  
   cout << "The deque of CInts with first & last elements swapped is:\n deq1 = (";  
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )  
      cout << " " << *d1_Iter << ",";  
   d1_Iter = --deq1.end( );  
   cout << " " << *d1_Iter << " )." << endl;  
  
   // Swapping back first and last elements with swap  
   swap ( *deq1.begin ( ) , *(deq1.end ( ) -1 ) );  
  
   cout << "The deque of CInts with first & last elements swapped back is:\n deq1 = (";  
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )  
      cout << " " << *d1_Iter << ",";  
   d1_Iter = --deq1.end( );  
   cout << " " << *d1_Iter << " )." << endl;  
  
   // Swapping a vector element with a deque element  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
   deque <int> deq2;  
   deque <int>::iterator d2_Iter;  
  
   int i;  
   for ( i = 0 ; i <= 3 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   int ii;  
   for ( ii = 4 ; ii <= 5 ; ii++ )  
   {  
      deq2.push_back( ii );  
   }  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   cout << "Deque deq2 is ( " ;  
   for ( d2_Iter = deq2.begin( ) ; d2_Iter != deq2.end( ) ; d2_Iter++ )  
      cout << *d2_Iter << " ";  
   cout << ")." << endl;  
  
   iter_swap ( v1.begin ( ) , deq2.begin ( ) );  
  
   cout << "After exchanging first elements,\n vector v1 is: v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl << " & deque deq2 is: deq2 = ( ";  
   for ( d2_Iter = deq2.begin( ) ; d2_Iter != deq2.end( ) ; d2_Iter++ )  
      cout << *d2_Iter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The original deque of CInts is deq1 = ( CInt(5), CInt(1), CInt(10) ).  
The deque of CInts with first & last elements swapped is:  
 deq1 = ( CInt(10), CInt(1), CInt(5) ).  
The deque of CInts with first & last elements swapped back is:  
 deq1 = ( CInt(5), CInt(1), CInt(10) ).  
Vector v1 is ( 0 1 2 3 ).  
Deque deq2 is ( 4 5 ).  
After exchanging first elements,  
 vector v1 is: v1 = ( 4 1 2 3 ).  
 & deque deq2 is: deq2 = ( 0 5 ).  
```  
  
##  <a name="lexicographical_compare"></a>  lexicographical_compare —  
 Porównuje dwie sekwencje element po elemencie, aby określić, która z nich jest mniejsza.  
  
```  
template<class InputIterator1, class InputIterator2>  
 bool lexicographical_compare(  
     InputIterator1  first1,  
     InputIterator1 Last1,  
     InputIterator2  first2,  
     InputIterator2 Last2  );  
  
template<class InputIterator1, class InputIterator2, class BinaryPredicate>  
bool lexicographical_compare(  
     InputIterator1  first1,  
     InputIterator1 Last1,  
     InputIterator2  first2,  
     InputIterator2 Last2,  
     BinaryPredicate  comp  );  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first1`  
 Iteratora wejściowych adresowania położenie pierwszego elementu w zakresie od pierwszego do porównania.  
  
 `last1`  
 Iteratora wejściowych adresowania poza ostatniego elementu w zakresie pierwszej pozycji, co ma zostać porównane.  
  
  `first2`  
 Iteratora wejściowych położenie pierwszego elementu w drugi zakres adresów do porównania.  
  
 `last2`  
 Iteratora wejściowych adresowania poza ostatniego elementu w drugi zakres pozycji, co ma zostać porównane.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje znaczeniu, w której jeden element jest mniejsza niż innym. Predykat binarne przyjmuje dwa argumenty i zwraca **true** po spełnieniu i **false** gdy nie są spełnione.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** w przypadku pierwszego zakresu lexicographically mniej niż drugiego zakresu; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Lexicographical porównanie sekwencji porównuje je elementów do:  
  
-   Znajduje dwa elementy odpowiednie w nierówne i pochodzi wynik ich porównanie wyniku porównania sekwencji.  
  
-   Nierówności nie zostaną znalezione, ale jeden sekwencja zawiera więcej elementów niż drugi i krótszy sekwencji jest uznawany za mniej niż dłużej sekwencji.  
  
-   Zostaną znalezione nie nierówności i sekwencje mają taką samą liczbę elementów, dlatego sekwencje są takie same i wynik porównania ma wartość false.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_lex_comp.cpp  
// compile with: /EHsc  
#include <vector>  
#include <list>  
#include <algorithm>  
#include <iostream>  
  
// Return whether second element is twice the first  
bool twice ( int elem1, int elem2 )  
{  
   return 2 * elem1 < elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1, v2;  
   list <int> L1;  
   vector <int>::iterator Iter1, Iter2;  
   list <int>::iterator L1_Iter, L1_inIter;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
   int ii;  
   for ( ii = 0 ; ii <= 6 ; ii++ )  
   {  
      L1.push_back( 5 * ii );  
   }  
  
   int iii;  
   for ( iii = 0 ; iii <= 5 ; iii++ )  
   {  
      v2.push_back( 10 * iii );  
   }  
  
   cout << "Vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "List L1 = ( " ;  
   for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )  
      cout << *L1_Iter << " ";  
   cout << ")" << endl;  
  
   cout << "Vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
      cout << ")" << endl;  
  
   // Self lexicographical_comparison of v1 under identity  
   bool result1;  
   result1 = lexicographical_compare (v1.begin( ), v1.end( ),  
                  v1.begin( ), v1.end( ) );  
   if ( result1 )  
      cout << "Vector v1 is lexicographically_less than v1." << endl;  
   else  
      cout << "Vector v1 is not lexicographically_less than v1." << endl;  
  
   // lexicographical_comparison of v1 and L2 under identity  
   bool result2;  
   result2 = lexicographical_compare (v1.begin( ), v1.end( ),  
                  L1.begin( ), L1.end( ) );  
   if ( result2 )  
      cout << "Vector v1 is lexicographically_less than L1." << endl;  
   else  
      cout << "Vector v1 is lexicographically_less than L1." << endl;  
  
   bool result3;  
   result3 = lexicographical_compare (v1.begin( ), v1.end( ),  
                  v2.begin( ), v2.end( ), twice );  
   if ( result3 )  
      cout << "Vector v1 is lexicographically_less than v2 "  
           << "under twice." << endl;  
   else  
      cout << "Vector v1 is not lexicographically_less than v2 "  
           << "under twice." << endl;  
}  
```  
  
```Output  
Vector v1 = ( 0 5 10 15 20 25 )  
List L1 = ( 0 5 10 15 20 25 30 )  
Vector v2 = ( 0 10 20 30 40 50 )  
Vector v1 is not lexicographically_less than v1.  
Vector v1 is lexicographically_less than L1.  
Vector v1 is not lexicographically_less than v2 under twice.  
```  
  
##  <a name="lower_bound"></a>  lower_bound —  
 Znajduje pozycję pierwszego elementu w uporządkowanym zakresie, który ma wartość większą niż lub równoważną określonej wartości, gdzie kryterium szeregowania może być określone przez predykat binarny.  
  
```  
 template<class ForwardIterator, class Type>  
 ForwardIterator lower_bound(  
     ForwardIterator first,  
     ForwardIterator last,  
     const Type& value );  
  
template<class ForwardIterator, class Type, class BinaryPredicate>  
ForwardIterator lower_bound(   
     ForwardIterator first,  
     ForwardIterator last,  
     const Type& value,  
     BinaryPredicate comp );  
  
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Iterator do przodu adresowania położenie pierwszego elementu w zakresie do wyszukania.  
  
 `last`  
 Iterator do przodu adresowania pozycji w jednym ostatniego elementu w zakresie do wyszukania.  
  
 `value`  
 Wartość, której pierwszą pozycję lub możliwe pierwszą pozycję są wyszukiwane w zakresie uporządkowanej.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje znaczeniu, w której jeden element jest mniejsza niż innym. Predykat binarne przyjmuje dwa argumenty i zwraca **true** po spełnieniu i **false** gdy nie są spełnione.  
  
### <a name="return-value"></a>Wartość zwracana  
 Do przodu iteratora w pozycji pierwszego elementu w uporządkowanego z wartością, która jest mniejsza niż odpowiednikiem określoną wartość określoną równoważność z predykatem binarnego.  
  
### <a name="remarks"></a>Uwagi  
 Zakres źródła posortowane odwołuje się do musi być prawidłowym; Iteratory wszystkie muszą być dereferenceable i w obrębie sekwencji ostatniej pozycji musi być dostępny z pierwszego przez przyrostowo zmieniać.  
  
 Posortowane zakres jest warunkiem wstępnym użycia `lower_bound` i gdzie kolejność jest taki sam jak określony przez z binarnej predykatu.  
  
 Zakres nie jest modyfikowany przez algorytm `lower_bound`.  
  
 Typy wartości iteratorów do przodu musi być mniejsza-niż porównywalne może zostać określona, tak, aby dane dwa elementy, można ustalić czy są równoważne (w tym sensie, że nie jest mniejsza niż drugi) albo że jeden jest mniejsza niż innych. Powoduje to kolejność między elementami nonequivalent  
  
 Złożoność algorytm jest logarytmiczna dla Iteratory dostęp losowy i liniowej, w przeciwnym razie wartość o liczbie kroków proporcjonalny do ( `last - first`).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_lower_bound.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // greater<int>( )  
#include <iostream>  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser( int elem1, int elem2 )  
{  
    if ( elem1 < 0 )  
        elem1 = - elem1;  
    if ( elem2 < 0 )  
        elem2 = - elem2;  
    return elem1 < elem2;  
}  
  
int main( )  
{  
    using namespace std;  
  
    vector<int> v1;  
    // Constructing vector v1 with default less-than ordering  
    for ( auto i = -1 ; i <= 4 ; ++i )  
    {  
        v1.push_back(  i );  
    }  
  
    for ( auto ii =-3 ; ii <= 0 ; ++ii )  
    {  
        v1.push_back(  ii  );  
    }  
  
    cout << "Starting vector v1 = ( " ;  
    for (const auto &Iter : v1)  
        cout << Iter << " ";  
    cout << ")." << endl;  
  
    sort(v1.begin(), v1.end());  
    cout << "Original vector v1 with range sorted by the\n "  
        << "binary predicate less than is v1 = ( " ;  
    for (const auto &Iter : v1)  
        cout << Iter << " ";  
    cout << ")." << endl;  
  
    // Constructing vector v2 with range sorted by greater  
    vector<int> v2(v1);  
  
    sort(v2.begin(), v2.end(), greater<int>());  
  
    cout << "Original vector v2 with range sorted by the\n "  
        << "binary predicate greater is v2 = ( " ;  
    for (const auto &Iter : v2)  
        cout << Iter << " ";  
    cout << ")." << endl;  
  
    // Constructing vectors v3 with range sorted by mod_lesser  
    vector<int> v3(v1);  
    sort(v3.begin(), v3.end(), mod_lesser);  
  
    cout << "Original vector v3 with range sorted by the\n "  
        <<  "binary predicate mod_lesser is v3 = ( " ;  
    for (const auto &Iter : v3)  
        cout << Iter << " ";  
    cout << ")." << endl;  
  
    // Demonstrate lower_bound  
  
    vector<int>::iterator Result;  
  
    // lower_bound of 3 in v1 with default binary predicate less<int>()  
    Result = lower_bound(v1.begin(), v1.end(), 3);  
    cout << "The lower_bound in v1 for the element with a value of 3 is: "  
        << *Result << "." << endl;  
  
    // lower_bound of 3 in v2 with the binary predicate greater<int>( )  
    Result = lower_bound(v2.begin(), v2.end(), 3, greater<int>());  
    cout << "The lower_bound in v2 for the element with a value of 3 is: "  
        << *Result << "." << endl;  
  
    // lower_bound of 3 in v3 with the binary predicate  mod_lesser  
    Result = lower_bound(v3.begin(), v3.end(), 3,  mod_lesser);  
    cout << "The lower_bound in v3 for the element with a value of 3 is: "  
        << *Result << "." << endl;  
}  
  
```  
  
##  <a name="make_heap"></a>  make_heap —  
 Konwertuje elementy z określonego zakresu na stertę, w której pierwszy element jest największy i dla której kryterium sortowania może być określone przez predykat binarny.  
  
```  
 template<class RandomAccessIterator>  
 void make_heap(  
     RandomAccessIterator first,  
     RandomAccessIterator last );  
  
template<class RandomAccessIterator, class BinaryPredicate>   
void make_heap(   
     RandomAccessIterator first,  
     RandomAccessIterator last,  
     BinaryPredicate comp );  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterator dostępie swobodnym, adresowania położenie pierwszego elementu w zakresie ma zostać przekonwertowany do stosu.  
  
 `last`  
 Iterator dostępie swobodnym, adresowania jedną pozycję poza ostatniego elementu w zakresie ma zostać przekonwertowany do stosu.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje znaczeniu, w której jeden element jest mniejsza niż innym. Predykat binarne przyjmuje dwa argumenty i zwraca **true** po spełnieniu i **false** gdy nie są spełnione.  
  
### <a name="remarks"></a>Uwagi  
 Stosów ma dwie właściwości:  
  
-   Pierwszy element zawsze jest największy.  
  
-   Elementy może dodać lub usunąć w czasie logarytmicznych.  
  
 Stosów są idealne sposób implementowania priorytet kolejek i ich użycia w implementacji karty kontenera standardowa biblioteka C++ [priority_queue — klasa](../standard-library/priority-queue-class.md).  
  
 Złożoność jest liniowa, wymaganie 3 \* (* ostatni — najpierw *) porównania.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_make_heap.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main() {  
   using namespace std;  
   vector <int> v1, v2;  
   vector <int>::iterator Iter1, Iter2;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   random_shuffle( v1.begin( ), v1.end( ) );  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Make v1 a heap with default less than ordering  
   make_heap ( v1.begin( ), v1.end( ) );  
   cout << "The heaped version of vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Make v1 a heap with greater than ordering  
   make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );  
   cout << "The greater-than heaped version of v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="max"></a>  Maksymalna  
 Porównuje dwa obiekty i zwraca większy z nich, gdzie kryterium sortowania może być określone przez predykat binarny.  
  
```  
template<class Type>  
    const Type& max(  
        const Type& left,   
        const Type& right  
    );  
template<class Type, class Pr>  
    const Type& max(  
        const Type& left,   
        const Type& right,  
        BinaryPredicate comp  
    );  
template<class Type>   
    Type& max (  
        initializer_list<Type> _Ilist  
    );  
template<class Type, class Pr>   
    Type& max(  
        initializer_list<Type> _Ilist,   
        BinaryPredicate comp  
    );  
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Pierwszy dwa obiekty są porównywane.  
  
 `right`  
 Drugi dwa obiekty są porównywane.  
  
 `comp`  
 Predykat binarne użyty do porównania dwóch obiektów.  
  
 `_IList`  
 Lista inicjatora, który zawiera obiekty, które ma zostać porównane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Większa niż dwa obiekty, chyba że nie będzie większa; w takim przypadku zwraca pierwszy z dwóch obiektów. W przypadku initializer_list Zwraca największy obiektów na liście.  
  
### <a name="remarks"></a>Uwagi  
 `max` Algorytm jest rzadko używana w mających obiektów przekazywane jako parametry. Większość algorytmów standardowa biblioteka C++ działają w zakresie elementów, których pozycja jest określona przez Iteratory przekazywane jako parametry. Jeśli potrzebujesz funkcji, która działa w zakresie elementów, użyj [max_element](../standard-library/algorithm-functions.md#max_element) zamiast tego.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_max.cpp  
// compile with: /EHsc  
#include <vector>  
#include <set>  
#include <algorithm>  
#include <iostream>  
#include <ostream>  
  
using namespace std;  
class CInt;  
ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
class CInt  
{  
public:  
   CInt( int n = 0 ) : m_nVal( n ){}  
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}  
   CInt&   operator=( const CInt& rhs ) {m_nVal =   
   rhs.m_nVal; return *this;}  
   bool operator<( const CInt& rhs ) const   
      {return ( m_nVal < rhs.m_nVal );}  
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
private:  
   int m_nVal;  
};  
  
inline ostream& operator<<( ostream& osIn, const CInt& rhs )  
{  
   osIn << "CInt( " << rhs.m_nVal << " )";   
   return osIn;  
}  
  
// Return whether absolute value of elem1 is greater than   
// absolute value of elem2  
bool abs_greater ( int elem1, int elem2 )  
{  
   if ( elem1 < 0 )   
      elem1 = -elem1;  
   if ( elem2 < 0 )   
      elem2 = -elem2;  
   return elem1 < elem2;  
};  
  
int main( )  
{  
   int a = 6, b = -7;  
   // Return the integer with the larger absolute value  
   const int& result1 = max(a, b, abs_greater);  
   // Return the larger integer  
   const int& result2 = max(a, b);  
  
   cout << "Using integers 6 and -7..." << endl;  
   cout << "The integer with the greater absolute value is: "   
        << result1 << "." << endl;  
   cout << "The integer with the greater value is: "   
        << result2 << "." << endl;  
   cout << endl;  
  
// Comparing the members of an initializer_list  
const int& result3 = max({ a, b });  
const int& result4 = max({ a, b }, abs_greater);  
  
cout << "Comparing the members of an initializer_list..." << endl;  
cout << "The member with the greater value is: " << result3 << endl;  
cout << "The integer with the greater absolute value is: " << result4 << endl;  
  
   // Comparing set containers with elements of type CInt   
   // using the max algorithm  
   CInt c1 = 1, c2 = 2, c3 = 3;  
   set<CInt> s1, s2, s3;  
   set<CInt>::iterator s1_Iter, s2_Iter, s3_Iter;  
  
   s1.insert ( c1 );  
   s1.insert ( c2 );  
   s2.insert ( c2 );  
   s2.insert ( c3 );  
  
   cout << "s1 = (";  
   for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )  
      cout << " " << *s1_Iter << ",";  
   s1_Iter = --s1.end( );  
   cout << " " << *s1_Iter << " )." << endl;  
  
   cout << "s2 = (";  
   for ( s2_Iter = s2.begin( ); s2_Iter != --s2.end( ); s2_Iter++ )  
      cout << " " << *s2_Iter << ",";  
   s2_Iter = --s2.end( );  
   cout << " " << *s2_Iter << " )." << endl;  
  
   s3 = max ( s1, s2 );  
   cout << "s3 = max ( s1, s2 ) = (";  
   for ( s3_Iter = s3.begin( ); s3_Iter != --s3.end( ); s3_Iter++ )  
      cout << " " << *s3_Iter << ",";  
   s3_Iter = --s3.end( );  
   cout << " " << *s3_Iter << " )." << endl << endl;  
  
   // Comparing vectors with integer elements using the max algorithm  
   vector <int> v1, v2, v3, v4, v5;  
   vector <int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;  
  
   int i;  
   for ( i = 0 ; i <= 2 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   int ii;  
   for ( ii = 0 ; ii <= 2 ; ii++ )  
   {  
      v2.push_back( ii );  
   }  
  
   int iii;  
   for ( iii = 0 ; iii <= 2 ; iii++ )  
   {  
      v3.push_back( 2 * iii );  
   }  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   cout << "Vector v2 is ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   cout << "Vector v3 is ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")." << endl;  
  
   v4 = max ( v1, v2 );  
   v5 = max ( v1, v3 );  
  
   cout << "Vector v4 = max (v1,v2) is ( " ;  
   for ( Iter4 = v4.begin( ) ; Iter4 != v4.end( ) ; Iter4++ )  
      cout << *Iter4 << " ";  
   cout << ")." << endl;  
  
   cout << "Vector v5 = max (v1,v3) is ( " ;  
   for ( Iter5 = v5.begin( ) ; Iter5 != v5.end( ) ; Iter5++ )  
      cout << *Iter5 << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
Using integers 6 and -7...  
The integer with the greater absolute value is: -7  
The integer with the greater value is: 6.  
Comparing the members of an initializer_list...The member with the greater value is: 6The integer wiht the greater absolute value is: -7  
s1 = ( CInt( 1 ), CInt( 2 ) ).  
s2 = ( CInt( 2 ), CInt( 3 ) ).  
s3 = max ( s1, s2 ) = ( CInt( 2 ), CInt( 3 ) ).  
  
Vector v1 is ( 0 1 2 ).  
Vector v2 is ( 0 1 2 ).  
Vector v3 is ( 0 2 4 ).  
Vector v4 = max (v1,v2) is ( 0 1 2 ).  
Vector v5 = max (v1,v3) is ( 0 2 4 ).  
```  
  
##  <a name="max_element"></a>  max_element —  
 Znajduje pierwsze wystąpienie największego elementu w określonym zakresie, gdzie kryterium sortowania może być określone przez predykat binarny.  
  
```  
template<class ForwardIterator>  
ForwardIterator max_element(ForwardIterator first, ForwardIterator last );  
  
template<class ForwardIterator, class BinaryPredicate>  
ForwardIterator max_element(ForwardIterator first, ForwardIterator last, BinaryPredicate comp );  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterator do przodu adresowania położenie pierwszego elementu w zakresie mają być wyszukiwane największy element.  
  
 `last`  
 Iterator do przodu adresowania jedną pozycję poza ostatniego elementu w zakresie mają być wyszukiwane największy element.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje znaczeniu, w której jeden element jest większa niż innym. Predykat binarne przyjmuje dwa argumenty i powinna zostać zwrócona **true** po pierwszym elementem jest mniejszy od drugiego elementu i **false** inaczej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator do przodu, adresowania położenie pierwszego wystąpienia największy element w zakresie przeszukiwane.  
  
### <a name="remarks"></a>Uwagi  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w ramach każdej sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Złożoność jest liniowa: ( `last`  -   `first`) - 1 porównania są wymagane dla zakresu niepusty.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_max_element.cpp  
// compile with: /EHsc  
#include <vector>  
#include <set>  
#include <algorithm>  
#include <iostream>  
#include <ostream>  
  
using namespace std;  
class CInt;  
ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
class CInt  
{  
public:  
   CInt( int n = 0 ) : m_nVal( n ){}  
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}  
   CInt& operator=( const CInt& rhs ) {m_nVal =   
   rhs.m_nVal; return *this;}  
   bool operator<( const CInt& rhs ) const   
      {return ( m_nVal < rhs.m_nVal );}  
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
private:  
   int m_nVal;  
};  
  
inline ostream& operator<<(ostream& osIn, const CInt& rhs)  
{  
   osIn << "CInt( " << rhs.m_nVal << " )";   
   return osIn;  
}  
  
// Return whether modulus of elem1 is greater than modulus of elem2  
bool mod_lesser ( int elem1, int elem2 )  
{  
   if ( elem1 < 0 )   
      elem1 = - elem1;  
   if ( elem2 < 0 )   
      elem2 = - elem2;  
   return elem1 < elem2;  
};  
  
int main( )  
{  
   // Searching a set container with elements of type CInt   
   // for the maximum element   
   CInt c1 = 1, c2 = 2, c3 = -3;  
   set<CInt> s1;  
   set<CInt>::iterator s1_Iter, s1_R1_Iter, s1_R2_Iter;  
  
   s1.insert ( c1 );  
   s1.insert ( c2 );  
   s1.insert ( c3 );  
  
   cout << "s1 = (";  
   for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )  
      cout << " " << *s1_Iter << ",";  
   s1_Iter = --s1.end( );  
   cout << " " << *s1_Iter << " )." << endl;  
  
   s1_R1_Iter = max_element ( s1.begin ( ) , s1.end ( ) );  
  
   cout << "The largest element in s1 is: " << *s1_R1_Iter << endl;  
   cout << endl;  
  
   // Searching a vector with elements of type int for the maximum  
   // element under default less than & mod_lesser binary predicates  
   vector <int> v1;  
   vector <int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;  
  
   int i;  
   for ( i = 0 ; i <= 3 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   int ii;  
   for ( ii = 1 ; ii <= 4 ; ii++ )  
   {  
      v1.push_back( - 2 * ii );  
   }  
  
   cout << "Vector v1 is ( " ;  
   for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )  
      cout << *v1_Iter << " ";  
   cout << ")." << endl;  
  
   v1_R1_Iter = max_element ( v1.begin ( ) , v1.end ( ) );  
   v1_R2_Iter = max_element ( v1.begin ( ) , v1.end ( ), mod_lesser);  
  
   cout << "The largest element in v1 is: " << *v1_R1_Iter << endl;  
   cout << "The largest element in v1 under the mod_lesser"  
        << "\n binary predicate is: " << *v1_R2_Iter << endl;  
}  
```  
  
##  <a name="merge"></a>  Scalania  
 Scala wszystkie elementy z dwóch posortowane zakresów w zakresu docelowego jednej, posortowane, gdzie kryterium porządkowania można określić predykat binarnego.  
  
```  
template<class InputIterator1, class InputIterator2, class OutputIterator>  
 OutputIterator merge(   
     InputIterator1 first1,   
     InputIterator1 last1,   
     InputIterator2 first2,   
     InputIterator2 last2,   
     OutputIterator result );   
  
template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>  
OutputIterator merge(   
     InputIterator1 first1,   
     InputIterator1 last1,   
     InputIterator2 first2,   
     InputIterator2 last2,   
     OutputIterator result,  
     BinaryPredicate comp );  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first1`  
 Wejściowy iteratora adresowania położenie pierwszego elementu w pierwszym dwa zakresy posortowane źródła można łączyć i posortowane w pojedynczy zakres.  
  
 `last1`  
 Wejściowy iteratora adresowania pozycja jeden po ostatnim elementem w pierwszym dwa zakresy posortowane źródła można łączyć i posortowane w pojedynczy zakres.  
  
  `first2`  
 Wejściowy iteratora adresowania położenie pierwszego elementu w drugim dwóch kolejnych sortowane zakresów można łączyć i posortowane w pojedynczy zakres.  
  
 `last2`  
 Wejściowy iteratora adresowania ostatnich pozycji, co ostatnim elementem w drugim dwóch kolejnych sortowane zakresów można łączyć i posortowane w pojedynczy zakres.  
  
 `result`  
 Pozycja pierwszego elementu w zakres docelowy, na którym mają być łączone w pojedynczy zakres posortowane dwóch zakresów adresów iteratora danych wyjściowych.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje znaczeniu, w której jeden element jest większa niż innym. Predykat binarne przyjmuje dwa argumenty i powinna zostać zwrócona **true** po pierwszym elementem jest mniejszy od drugiego elementu i **false** inaczej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dane wyjściowe iteratora adresowania jedną pozycję po ostatnim elementem w zakres docelowy posortowane.  
  
### <a name="remarks"></a>Uwagi  
 Posortowane zakresów odwołania musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w ramach każdej sekwencji ostatniej pozycji musi być dostępny z pierwszego przez przyrostowo zmieniać.  
  
 Zakres docelowy nie powinien zachodzić albo zakresów i powinien być wystarczająco duży, ma zakres docelowy.  
  
 Posortowane zakresów muszą być ustawione jako warunek wstępny stosowania **scalania** algorytm zgodnie z tej samej kolejności jak ma być używany przez algorytm sortowania połączonych zakresów.  
  
 Operacja jest stabilna jako względną kolejność elementów w obrębie każdego zakresu jest zachowywana w zakresie docelowym. Zakresów nie są modyfikowane przez algorytm **scalania**.  
  
 Typy wartości wejściowych Iteratory musi być mniejsza-niż porównywalne może zostać określona, tak, aby dane dwa elementy, można ustalić czy są równoważne (w tym sensie, że nie jest mniejsza niż drugi) albo że jeden jest mniejsza niż innych. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Gdy w obu zakresów źródła równoważny elementów, elementy w zakresie pierwszy poprzedzać elementy z drugiego zakresu źródła w zakresie docelowym.  
  
 Złożoność algorytm jest liniowa z co najwyżej (* Nazwisko1 - first1*)-(* Nazwisko2 - first2*) - 1 porównania.  
  
 [List — klasa](../standard-library/list-class.md) zawiera funkcji członkowskiej "merge" scalenie elementów listy.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_merge.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>   // For greater<int>( )  
#include <iostream>  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser ( int elem1, int elem2 ) {  
   if (elem1 < 0)   
      elem1 = - elem1;  
   if (elem2 < 0)   
      elem2 = - elem2;  
   return elem1 < elem2;  
}  
  
int main() {  
   using namespace std;  
   vector <int> v1a, v1b, v1 ( 12 );  
   vector <int>::iterator Iter1a,  Iter1b, Iter1;  
  
   // Constructing vector v1a and v1b with default less than ordering  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
      v1a.push_back(  i );  
  
   int ii;  
   for ( ii =-5 ; ii <= 0 ; ii++ )  
      v1b.push_back(  ii  );  
  
   cout << "Original vector v1a with range sorted by the\n "  
        << "binary predicate less than is  v1a = ( " ;  
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )  
      cout << *Iter1a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v1b with range sorted by the\n "  
        << "binary predicate less than is  v1b = ( " ;  
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )  
      cout << *Iter1b << " ";  
   cout << ")." << endl;  
  
   // Constructing vector v2 with ranges sorted by greater  
   vector <int> v2a ( v1a ) , v2b ( v1b ) ,  v2 ( v1 );  
   vector <int>::iterator Iter2a,  Iter2b, Iter2;  
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );  
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );  
  
   cout << "Original vector v2a with range sorted by the\n "  
        <<  "binary predicate greater is   v2a =  ( " ;  
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )  
      cout << *Iter2a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v2b with range sorted by the\n "  
        <<  "binary predicate greater is   v2b =  ( " ;  
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )  
      cout << *Iter2b << " ";  
   cout << ")." << endl;  
  
   // Constructing vector v3 with ranges sorted by mod_lesser  
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );  
   vector <int>::iterator Iter3a,  Iter3b, Iter3;  
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );  
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser );  
  
   cout << "Original vector v3a with range sorted by the\n "  
        << "binary predicate mod_lesser is   v3a =  ( " ;  
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )  
      cout << *Iter3a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v3b with range sorted by the\n "  
        << "binary predicate mod_lesser is   v3b =  ( " ;  
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )  
      cout << *Iter3b << " ";  
   cout << ")." << endl;  
  
   // To merge inplace in ascending order with default binary   
   // predicate less <int> ( )  
   merge ( v1a.begin ( ) , v1a.end ( ) , v1b.begin ( ) , v1b.end ( ) , v1.begin ( ) );  
   cout << "Merged inplace with default order,\n vector v1mod =  ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // To merge inplace in descending order, specify binary   
   // predicate greater<int>( )  
   merge ( v2a.begin ( ) , v2a.end ( ) , v2b.begin ( ) , v2b.end ( ) ,  
       v2.begin ( ) ,  greater <int> ( ) );  
   cout << "Merged inplace with binary predicate greater specified,\n "  
        << "vector v2mod  = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   // Applying A user-defined (UD) binary predicate mod_lesser  
   merge ( v3a.begin ( ) , v3a.end ( ) , v3b.begin ( ) , v3b.end ( ) ,  
       v3.begin ( ) ,  mod_lesser );  
   cout << "Merged inplace with binary predicate mod_lesser specified,\n "  
        << "vector v3mod  = ( " ; ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="min"></a>  min  
 Porównuje dwa obiekty i zwraca mniejszy z nich, gdzie kryterium sortowania może być określone przez predykat binarny.  
  
```  
template<class Type>  
    const Type& min(  
        const Type& left,   
        const Type& right  
    );  
template<class Type, class Pr>  
    const Type& min(  
        const Type& left,   
        const Type& right,  
        BinaryPredicate comp  
    );  
template<class Type>   
    Type min ( initializer_list<Type> _Ilist  
    );  
template<class Type, class Pr>    Type min (  
        initializer_list<Type> _Ilist,   
        BinaryPredicate comp  
    );  
  
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Pierwszy dwa obiekty są porównywane.  
  
 `right`  
 Drugi dwa obiekty są porównywane.  
  
 `comp`  
 Predykat binarne użyty do porównania dwóch obiektów.  
  
 `_IList`  
 Initializer_list, który zawiera elementy członkowskie, które można porównać.  
  
### <a name="return-value"></a>Wartość zwracana  
 Mniejszy z dwóch obiektów, chyba że nie będzie mniejsza; w takim przypadku zwraca pierwszy z dwóch obiektów. W przypadku initializer_list zwraca najmniejszą obiektów na liście.  
  
### <a name="remarks"></a>Uwagi  
 `min` Algorytm jest rzadko używana w mających obiektów przekazywane jako parametry. Większość algorytmów standardowa biblioteka C++ działają w zakresie elementów, których pozycja jest określona przez Iteratory przekazywane jako parametry. Jeśli potrzebujesz funkcji, która używa zakresu elementów, użyj [min_element](../standard-library/algorithm-functions.md#min_element).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_min.cpp  
// compile with: /EHsc  
#include <vector>  
#include <set>  
#include <algorithm>  
#include <iostream>  
#include <ostream>  
  
using namespace std;  
class CInt;  
ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
class CInt  
{  
public:  
    CInt( int n = 0 ) : m_nVal( n ){}  
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}  
    CInt& operator=( const CInt& rhs ) {m_nVal =   
    rhs.m_nVal; return *this;}  
    bool operator<( const CInt& rhs ) const   
        {return ( m_nVal < rhs.m_nVal );}  
    friend ostream& operator<<(ostream& osIn, const CInt& rhs);  
  
private:  
    int m_nVal;  
};  
  
inline ostream& operator<<( ostream& osIn, const CInt& rhs )  
{  
    osIn << "CInt( " << rhs.m_nVal << " )";   
       return osIn;  
}  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser ( int elem1, int elem2 )  
{  
    if ( elem1 < 0 )   
        elem1 = - elem1;  
    if ( elem2 < 0 )   
        elem2 = - elem2;  
    return elem1 < elem2;  
};  
  
int main( )  
{  
    // Comparing integers directly using the min algorithm with  
    // binary predicate mod_lesser & with default less than  
    int a = 6, b = -7, c = 7 ;  
    const int& result1 = min ( a, b, mod_lesser );  
    const int& result2 = min ( b, c );  
  
    cout << "The mod_lesser of the integers 6 & -7 is: "   
        << result1 << "." << endl;  
     cout << "The lesser of the integers -7 & 7 is: "   
        << result2 << "." << endl;  
    cout << endl;  
  
// Comparing the members of an initializer_list  
    const int& result3 = min({ a, c });  
    const int& result4 = min({ a, b }, mod_lesser);  
  
    cout << "The lesser of the integers 6 & 7 is: "  
        << result3 << "." << endl;  
    cout << "The mod_lesser of the integers 6 & -7 is: "  
        << result4 << "." << endl;  
    cout << endl;  
  
    // Comparing set containers with elements of type CInt   
       // using the min algorithm  
    CInt c1 = 1, c2 = 2, c3 = 3;  
    set<CInt> s1, s2, s3;  
    set<CInt>::iterator s1_Iter, s2_Iter, s3_Iter;  
  
    s1.insert ( c1 );  
    s1.insert ( c2 );  
    s2.insert ( c2 );  
    s2.insert ( c3 );  
  
    cout << "s1 = (";  
    for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )  
        cout << " " << *s1_Iter << ",";  
    s1_Iter = --s1.end( );  
        cout << " " << *s1_Iter << " )." << endl;  
  
    cout << "s2 = (";  
    for ( s2_Iter = s2.begin( ); s2_Iter != --s2.end( ); s2_Iter++ )  
        cout << " " << *s2_Iter << ",";  
    s2_Iter = --s2.end( );  
    cout << " " << *s2_Iter << " )." << endl;  
  
    s3 = min ( s1, s2 );  
    cout << "s3 = min ( s1, s2 ) = (";  
    for ( s3_Iter = s3.begin( ); s3_Iter != --s3.end( ); s3_Iter++ )  
        cout << " " << *s3_Iter << ",";  
    s3_Iter = --s3.end( );  
    cout << " " << *s3_Iter << " )." << endl << endl;  
  
    // Comparing vectors with integer elements using min algorithm  
    vector <int> v1, v2, v3, v4, v5;  
    vector <int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;  
  
    int i;  
    for ( i = 0 ; i <= 2 ; i++ )  
    {  
        v1.push_back( i );  
    }  
  
    int ii;  
    for ( ii = 0 ; ii <= 2 ; ii++ )  
    {  
        v2.push_back( ii );  
    }  
  
    int iii;  
    for ( iii = 0 ; iii <= 2 ; iii++ )  
    {  
        v3.push_back( 2 * iii );  
    }  
  
    cout << "Vector v1 is ( " ;  
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
        cout << *Iter1 << " ";  
    cout << ")." << endl;  
  
    cout << "Vector v2 is ( " ;  
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
        cout << *Iter2 << " ";  
    cout << ")." << endl;  
  
    cout << "Vector v3 is ( " ;  
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
        cout << *Iter3 << " ";  
    cout << ")." << endl;  
  
    v4 = min ( v1, v2 );  
    v5 = min ( v1, v3 );  
  
    cout << "Vector v4 = min ( v1,v2 ) is ( " ;  
    for ( Iter4 = v4.begin( ) ; Iter4 != v4.end( ) ; Iter4++ )  
        cout << *Iter4 << " ";  
    cout << ")." << endl;  
  
    cout << "Vector v5 = min ( v1,v3 ) is ( " ;  
    for ( Iter5 = v5.begin( ) ; Iter5 != v5.end( ) ; Iter5++ )  
        cout << *Iter5 << " ";  
    cout << ")." << endl;  
}  
```  
  
```Output  
The mod_lesser of the integers 6 & -7 is: 6.  
The lesser of the integers -7 & 7 is: -7.  
The lesser of the integers 6 & 7 is: 6.The mod_lesser of the integers 6 & -7 is: 6.  
s1 = ( CInt( 1 ), CInt( 2 ) ).  
s2 = ( CInt( 2 ), CInt( 3 ) ).  
s3 = min ( s1, s2 ) = ( CInt( 1 ), CInt( 2 ) ).  
  
Vector v1 is ( 0 1 2 ).  
Vector v2 is ( 0 1 2 ).  
Vector v3 is ( 0 2 4 ).  
Vector v4 = min ( v1,v2 ) is ( 0 1 2 ).  
Vector v5 = min ( v1,v3 ) is ( 0 1 2 ).  
```  
  
##  <a name="min_element"></a>  min_element —  
 Znajduje pierwsze wystąpienie najmniejszego elementu w określonym zakresie, gdzie kryterium sortowania może być określone przez predykat binarny.  
  
```  
 template<class ForwardIterator>  
 ForwardIterator min_element(ForwardIterator first, ForwardIterator last );  
  
template<class ForwardIterator, class BinaryPredicate>  
ForwardIterator min_element(ForwardIterator first, ForwardIterator last, BinaryPredicate comp);  
  
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Iterator do przodu adresowania położenie pierwszego elementu w zakresie mają być wyszukiwane najmniejszy element.  
  
 `last`  
 Iterator do przodu adresowania jedną pozycję poza ostatniego elementu w zakresie mają być wyszukiwane najmniejszy element.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje znaczeniu, w której jeden element jest większa niż innym. Predykat binarne przyjmuje dwa argumenty i powinna zostać zwrócona **true** po pierwszym elementem jest mniejszy od drugiego elementu i **false** inaczej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator do przodu, adresowania położenie pierwszego wystąpienia najmniejszy element w zakresie przeszukiwane.  
  
### <a name="remarks"></a>Uwagi  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w ramach każdej sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Złożoność jest liniowa: ( `last`  -  `first`) - 1 porównania są wymagane dla zakresu niepusty.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_min_element.cpp  
// compile with: /EHsc  
#include <vector>  
#include <set>  
#include <algorithm>  
#include <iostream>  
#include <ostream>  
  
using namespace std;  
class CInt;  
ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
class CInt  
{  
public:  
   CInt( int n = 0 ) : m_nVal( n ){}  
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}  
   CInt& operator=( const CInt& rhs ) {m_nVal =   
   rhs.m_nVal; return *this;}  
   bool operator<( const CInt& rhs ) const   
      {return ( m_nVal < rhs.m_nVal );}  
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
private:  
   int m_nVal;  
};  
  
inline ostream& operator<<( ostream& osIn, const CInt& rhs )  
{  
   osIn << "CInt( " << rhs.m_nVal << " )";   
   return osIn;  
}  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser ( int elem1, int elem2 )  
{  
   if ( elem1 < 0 )   
      elem1 = - elem1;  
   if ( elem2 < 0 )   
      elem2 = - elem2;  
   return elem1 < elem2;  
};  
  
int main()  
{  
   // Searching a set container with elements of type CInt   
   // for the minimum element   
   CInt c1 = 1, c2 = 2, c3 = -3;  
   set<CInt> s1;  
   set<CInt>::iterator s1_Iter, s1_R1_Iter, s1_R2_Iter;  
  
   s1.insert ( c1 );  
   s1.insert ( c2 );  
   s1.insert ( c3 );  
  
   cout << "s1 = (";  
   for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )  
      cout << " " << *s1_Iter << ",";  
   s1_Iter = --s1.end( );  
   cout << " " << *s1_Iter << " )." << endl;  
  
   s1_R1_Iter = min_element ( s1.begin ( ) , s1.end ( ) );  
  
   cout << "The smallest element in s1 is: " << *s1_R1_Iter << endl;  
   cout << endl;  
  
   // Searching a vector with elements of type int for the maximum  
   // element under default less than & mod_lesser binary predicates  
   vector <int> v1;  
   vector <int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;  
  
   int i;  
   for ( i = 0 ; i <= 3 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   int ii;  
   for ( ii = 1 ; ii <= 4 ; ii++ )  
   {  
      v1.push_back( - 2 * ii );  
   }  
  
   cout << "Vector v1 is ( " ;  
   for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )  
      cout << *v1_Iter << " ";  
   cout << ")." << endl;  
  
   v1_R1_Iter = min_element ( v1.begin ( ) , v1.end ( ) );  
   v1_R2_Iter = min_element ( v1.begin ( ) , v1.end ( ), mod_lesser);  
  
   cout << "The smallest element in v1 is: " << *v1_R1_Iter << endl;  
   cout << "The smallest element in v1 under the mod_lesser"  
        << "\n binary predicate is: " << *v1_R2_Iter << endl;  
}  
```  
  
```Output  
s1 = ( CInt( -3 ), CInt( 1 ), CInt( 2 ) ).  
The smallest element in s1 is: CInt( -3 )  
  
Vector v1 is ( 0 1 2 3 -2 -4 -6 -8 ).  
The smallest element in v1 is: -8  
The smallest element in v1 under the mod_lesser  
 binary predicate is: 0  
```  
  
##  <a name="minmax_element"></a>  minmax_element  
 Wykonuje pracę z zastosowaniem `min_element` i `max_element` w jednym wywołaniu.  
  
```  
template<class ForwardIterator>  
    pair< ForwardIterator, ForwardIterator >  
        minmax_element(  
            ForwardIterator  first,   
            ForwardIterator Last  
                 );  
template<class ForwardIterator, class BinaryPredicate>  
    pair< ForwardIterator, ForwardIterator >  
        minmax_element(  
            ForwardIterator  first,   
            ForwardIterator Last,   
            BinaryPredicate  comp  
                );  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterator do przodu, który wskazuje początek zakresu.  
  
 `last`  
 Iterator do przodu, który wskazuje koniec zakresu.  
  
 `comp`  
 Opcjonalne test służy do kolejność elementów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca  
  
 `pair<ForwardIterator, ForwardIterator>`  
  
 `(` [min_element](../standard-library/algorithm-functions.md#min_element)`(first, last), `[max_element](../standard-library/algorithm-functions.md#max_element)`(first, last))`.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca pierwszy funkcji szablonu  
  
 `pair<ForwardIterator,ForwardIterator>`  
  
 `(min_element(_First,Last), max_element(_First,Last))`.  
  
 Drugi funkcji szablonu działa tak samo, z wyjątkiem tego, że zastępuje `operator<(X, Y)` z `comp (X, Y)`.  
  
 Jeśli sekwencja jest pusta, funkcja wykonuje co najwyżej `3 * (last - first - 1) / 2` porównania.  
  
##  <a name="minmax"></a>  minmax  
 Porównuje dwa parametry wejściowe i zwraca je jako pary, w kolejności mniejszym większej.  
  
```  
template<class Type>  
    pair<const Type&, const Type&>  
        minmax(  
            const Type& left,   
            const Type& right  
        );  
template<class Type, class BinaryPredicate>  
    pair<const Type&, const Type&>  
        minmax(  
            const Type& left,  
            const Type& right,  
            BinaryPredicate comp  
        );  
template<class Type>     pair<Type&, Type&>         minmax(  
            initializer_list<Type> _Ilist  
        );  
template<class Type, class BinaryPredicate>   
    pair<Type&, Type&>         minmax(  
            initializer_list<Type> _Ilist,   
            BinaryPredicate comp  
        );  
  
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Pierwszy dwa obiekty są porównywane.  
  
 `right`  
 Drugi dwa obiekty są porównywane.  
  
 `comp`  
 Predykat binarne użyty do porównania dwóch obiektów.  
  
 `_IList`  
 Initializer_list, który zawiera elementy członkowskie, które można porównać.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca pierwszy funkcji szablonu `pair<const Type&, const Type&>( right , left )` Jeśli `right` jest mniejsza niż `left`. W przeciwnym razie zwraca `pair<const Type&, const Type&>( left , right )`.  
  
 Drugi funkcji członkowskiej zwraca pary, gdzie pierwszy element jest mniejszy, a drugą jest wartość większa w porównaniu predykat `comp`.  
  
 Pozostałe funkcje szablonu działają tak samo, z wyjątkiem tego, że zastępują one `left` i `right` parametrów z `_IList`.  
  
 Funkcja wykonuje dokładnie jedno porównanie.  
  
##  <a name="mismatch"></a>  Niezgodność  
 Porównuje dwa zakresy elementów i lokalizuje pierwszą pozycję, gdzie występuje różnica.  
  
 Użyj podwójnego range overloads w języku C ++ 14 kodu, ponieważ przeciążeń, które przyjmuje tylko jednego iteratora drugiego zakresu nie wykrywa różnice, jeśli drugi zakres jest dłuższa niż pierwszy zakres i spowoduje niezdefiniowane zachowanie, jeśli drugi zakres jest krótszy od pierwszego zakresu.  
  
```  
 template<class InputIterator1, class InputIterator2> pair<InputIterator1, InputIterator2>>   
 mismatch(  
     InputIterator1 First1,  
     InputIterator1 Last1,  
     InputIterator2 First2 );   
  
template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>  
mismatch(  
     InputIterator1 First1,  
     InputIterator1 Last1,  
     InputIterator2 First2,  
     BinaryPredicate Comp );  
  
//C++14  
template<class InputIterator1, class InputIterator2> pair<InputIterator1, InputIterator2>>  
mismatch(  
    InputIterator1 First1,  
     InputIterator1 Last1,  
     InputIterator2 First2,  
     InputIterator2 Last2 );  
  
template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>  
mismatch(  
     InputIterator1 First1,  
     InputIterator1 Last1,  
     InputIterator2 First2,  
     InputIterator2 Last2,  
     BinaryPredicate Comp);  
```  
  
### <a name="parameters"></a>Parametry  
 `First1`  
 Iteratora wejściowych adresowania położenie pierwszego elementu w zakresie od pierwszego do sprawdzenia.  
  
 `Last1`  
 Iteratora wejściowych adresowania jedną pozycję po ostatnim elementem w pierwszy zakres do sprawdzenia.  
  
 `First2`  
 Iteratora wejściowych adresowania położenie pierwszego elementu w drugi zakres do sprawdzenia.  
  
 `Last2`  
 Iteratora wejściowych adresowania pozycja jednego po ostatnim elementem w drugi zakres do sprawdzenia.  
  
 `Comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiekt, który porównuje bieżący elementów w każdej zakresu i określa, czy są równoważne. Zwraca **true** po spełnieniu i **false** gdy nie są spełnione.  
  
### <a name="return-value"></a>Wartość zwracana  
 Para Iteratory adresowania pozycji niezgodność w dwa zakresy, pierwszy iteratora składnik do pozycji w zakresie pierwszego i drugiego iteratora składnik do pozycji drugiego zakresu. Nie ma żadnej różnicy między elementami w zakresach porównaniu lub binarne predykatu w druga wersja jest spełnione przez wszystkie pary elementu z dwa zakresy, następnie pierwszy iteratora składnika wskazuje pozycji w jednym ostatniego elementu w pierwszym zakres i drugi iteratora składnik do pozycji w jednym elemencie końcowego testowane w drugiego zakresu.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszej funkcji szablonu przyjęto założenie, że istnieją dowolną liczbę elementów w zakresie, rozpoczynając od first2, ponieważ w zasięgu wyznaczonym przez [first1, Nazwisko1). Jeśli istnieje więcej drugiego zakresu, są ignorowane. Jeśli są mniejsze, będą powodować niezdefiniowane zachowanie.  
  
 Zakres do wyszukania musi być prawidłowym; Iteratory wszystkie muszą być dereferenceable i ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Złożoność czasu algorytm jest liniowa w liczbę elementów zawartych w zakresie krótszy.  
  
 Predykat zdefiniowane przez użytkownika nie jest wymagane wprowadzenie relacji równoważność symetrycznego, zwrotnej i przechodnie swoich argumentów.  
  
### <a name="example"></a>Przykład  
  W poniższym przykładzie pokazano sposób użycia niezgodności. Przeciążenie 03 C ++ jest wyświetlany tylko w celu pokazują, jak można utworzyć nieoczekiwany wynik.  
  
```cpp  
#include <vector>  
#include <list>  
#include <algorithm>  
#include <iostream>  
#include <string>  
#include <utility>  
  
using namespace std;  
  
// Return whether first element is twice the second  
// Note that this is not a symmetric, reflexive and transitive equivalence.  
// mismatch and equal accept such predicates, but is_permutation does not.  
bool twice(int elem1, int elem2)  
{  
    return elem1 == elem2 * 2;  
}  
  
void PrintResult(const string& msg, const pair<vector<int>::iterator, vector<int>::iterator>& result,  
    const vector<int>& left, const vector<int>& right)  
{  
    // If either iterator stops before reaching the end of its container,  
    // it means a mismatch was detected.  
    if (result.first != left.end() || result.second != right.end())  
    {  
        string leftpos(result.first == left.end() ? "end" : to_string(*result.first));  
        string rightpos(result.second == right.end() ? "end" : to_string(*result.second));  
        cout << msg << "mismatch. Left iterator at " << leftpos  
            << " right iterator at " << rightpos << endl;  
    }  
    else  
    {  
        cout << msg << " match." << endl;  
    }  
}  
  
int main()  
{  
  
    vector<int> vec_1{ 0, 5, 10, 15, 20, 25 };  
    vector<int> vec_2{ 0, 5, 10, 15, 20, 25, 30 };  
  
    // Testing different length vectors for mismatch (C++03)  
    auto match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin());  
    bool is_mismatch = match_vecs.first != vec_1.end();  
    cout << "C++03: vec_1 and vec_2 are a mismatch: " << boolalpha << is_mismatch << endl;  
  
    // Using dual-range overloads:  
  
    // Testing different length vectors for mismatch (C++14)  
    match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin(), vec_2.end());  
    PrintResult("C++14: vec_1 and vec_2: ", match_vecs, vec_1, vec_2);  
  
    // Identify point of mismatch between vec_1 and modified vec_2.   
    vec_2[3] = 42;  
    match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin(), vec_2.end());  
    PrintResult("C++14 vec_1 v. vec_2 modified: ", match_vecs, vec_1, vec_2);  
  
    // Test vec_3 and vec_4 for mismatch under the binary predicate twice (C++14)    
    vector<int> vec_3{ 10, 20, 30, 40, 50, 60 };  
    vector<int> vec_4{ 5, 10, 15, 20, 25, 30 };  
    match_vecs = mismatch(vec_3.begin(), vec_3.end(), vec_4.begin(), vec_4.end(), twice);  
    PrintResult("vec_3 v. vec_4 with pred: ", match_vecs, vec_3, vec_4);  
  
    vec_4[5] = 31;  
    match_vecs = mismatch(vec_3.begin(), vec_3.end(), vec_4.begin(), vec_4.end(), twice);  
    PrintResult("vec_3 v. modified vec_4 with pred: ", match_vecs, vec_3, vec_4);  
  
    // Compare a vector<int> to a list<int>  
    list<int> list_1{ 0, 5, 10, 15, 20, 25 };  
    auto match_vec_list = mismatch(vec_1.begin(), vec_1.end(), list_1.begin(), list_1.end());  
    is_mismatch = match_vec_list.first != vec_1.end() || match_vec_list.second != list_1.end();  
    cout << "vec_1 and list_1 are a mismatch: " << boolalpha << is_mismatch << endl;  
  
    char c;  
    cout << "Press a key" << endl;  
    cin >> c;  
  
}  
  
/*  
Output:  
C++03: vec_1 and vec_2 are a mismatch: false  
C++14: vec_1 and vec_2: mismatch. Left iterator at end right iterator at 30  
C++14 vec_1 v. vec_2 modified: mismatch. Left iterator at 15 right iterator at 42  
C++14 vec_3 v. vec_4 with pred:  match.  
C++14 vec_3 v. modified vec_4 with pred: mismatch. Left iterator at 60 right iterator at 31  
C++14: vec_1 and list_1 are a mismatch: false  
Press a key  
*/  
  
```  
  
##  <a name="alg_move"></a>  &lt;alg&gt; Przenieś  
 Przenieś elementy związane z określonym zakresem.  
  
```  
template<class InputIterator, class OutputIterator>  
    OutputIterator move(  
        InputIterator first,   
        InputIterator last,  
        OutputIterator dest  
                  );  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Wejściowych iteratora, która wskazuje, gdzie rozpoczynać zakresu elementów, aby przenieść.  
  
 `last`  
 Iterację wejściowych wskazuje koniec zakresu elementów, aby przenieść.  
  
 `dest`  
 Iterator danych wyjściowych, zawierającego przeniesione elementy.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu `*(dest + N) = move(*(first + N))` raz dla każdego `N` w zakresie `[0, last - first)`, ściśle zwiększenia wartości `N` uruchamianie o najniższej wartości. Następnie zwraca `dest + N`. Jeśli `dest` i `first` wyznaczyć regiony pamięci masowej, `dest` nie może być w zakresie `[first, last)`.  
  
##  <a name="move_backward"></a>  move_backward  
 Przenosi elementy jednego iteratora do drugiego. Przeniesienie rozpoczyna się od ostatniego elementu w określonym zakresie, a kończy się na pierwszym elemencie w tym zakresie.  
  
```  
template<class BidirectionalIterator1, class BidirectionalIterator2>  
   BidirectionalIterator2 move_backward(  
       BidirectionalIterator1 first,   
       BidirectionalIterator1 last,  
       BidirectionalIterator2 destEnd);
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterator, która wskazuje początek zakresu można przenosić elementy z.  
  
 `last`  
 Iterację wskazuje koniec zakresu można przenosić elementy z. Ten element nie jest przenoszony.  
  
 `destEnd`  
 Iterator dwukierunkowy odnoszący się do pierwszej pozycji po elemencie końcowym w zakresie docelowym.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu `*(destEnd - N - 1) = move(*(last - N - 1))` raz dla każdego `N` w zakresie `[0, last - first)`, ściśle zwiększenia wartości `N` uruchamianie o najniższej wartości. Następnie zwraca `destEnd - (last - first)`. Jeśli `destEnd` i `first` wyznaczyć regiony pamięci masowej, `destEnd` nie może być w zakresie `[first, last)`.  
  
 `move` i `move_backward` jest funkcjonalnym odpowiednikiem przy użyciu `copy` i `copy_backward` z iteratora przenoszenia.  
  
##  <a name="next_permutation"></a>  next_permutation —  
 Zmienia kolejność elementów w zakresie, tak że oryginalna kolejność jest zastąpiona przez leksykograficznie kolejną większą permutację, o ile takowa istnieje, gdzie sens „kolejna” może być określony przez predykat binarny.  
  
```  
template<class BidirectionalIterator>  
bool next_permutation(BidirectionalIterator first, BidirectionalIterator last);  
  
template<class BidirectionalIterator, class BinaryPredicate>  
bool next_permutation(BidirectionalIterator first, BidirectionalIterator last, BinaryPredicate comp);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Dwukierunkowy iteratora wskazuje położenie pierwszego elementu w zakresie do cieniowania można.  
  
 `last`  
 Dwukierunkowy iteratora wskazujący pozycji w jednym ostatniego elementu w zakresie do cieniowania można.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje kryterium porównania muszą być spełnione przez kolejnych elementów w kolejności. Predykat binarne przyjmuje dwa argumenty i zwraca **true** po spełnieniu i **false** gdy nie są spełnione.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli lexicographically dalej permutacji istnieje i zastąpione oryginalnego porządkowanie zakresu; w przeciwnym razie **false**, w tym przypadku porządkowania jest przekształcana na najmniejszą lexicographically permutacji.  
  
### <a name="remarks"></a>Uwagi  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Predykat binarne domyślny jest mniejsza niż i elementów w zakresie musi być mniejsza niż porównywalne na ułatwieniu zapewnienia również zdefiniowano dalej permutacji.  
  
 Złożoność jest liniowa z co najwyżej (* ostatni — najpierw *) / zamienia 2.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_next_perm.cpp  
// compile with: /EHsc  
#include <vector>  
#include <deque>  
#include <algorithm>  
#include <iostream>  
#include <ostream>  
  
using namespace std;  
class CInt;  
ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
class CInt  
{  
public:  
   CInt( int n = 0 ) : m_nVal( n ){}  
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}  
   CInt&   operator=( const CInt& rhs ) {m_nVal =  
   rhs.m_nVal; return *this;}  
   bool operator<( const CInt& rhs ) const  
      { return ( m_nVal < rhs.m_nVal );}  
   friend   ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
private:  
   int m_nVal;  
};  
  
inline ostream& operator<<( ostream& osIn, const CInt& rhs )  
{  
   osIn << "CInt( " << rhs.m_nVal << " )";  
   return osIn;  
}  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser ( int elem1, int elem2 )  
{  
   if ( elem1 < 0 )  
      elem1 = - elem1;  
   if ( elem2 < 0 )  
      elem2 = - elem2;  
   return elem1 < elem2;  
};  
  
int main( )  
{  
   // Reordering the elements of type CInt in a deque  
   // using the prev_permutation algorithm  
   CInt c1 = 5, c2 = 1, c3 = 10;  
   bool deq1Result;  
   deque<CInt> deq1, deq2, deq3;  
   deque<CInt>::iterator d1_Iter;  
  
   deq1.push_back ( c1 );  
   deq1.push_back ( c2 );  
   deq1.push_back ( c3 );  
  
   cout << "The original deque of CInts is deq1 = (";  
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )  
      cout << " " << *d1_Iter << ",";  
   d1_Iter = --deq1.end( );  
   cout << " " << *d1_Iter << " )." << endl;  
  
   deq1Result = next_permutation ( deq1.begin ( ) , deq1.end ( ) );  
  
   if ( deq1Result )  
      cout << "The lexicographically next permutation "  
           << "exists and has\nreplaced the original "  
           << "ordering of the sequence in deq1." << endl;  
   else  
      cout << "The lexicographically next permutation doesn't "  
           << "exist\n and the lexicographically "  
           << "smallest permutation\n has replaced the "  
           << "original ordering of the sequence in deq1." << endl;  
  
   cout << "After one application of next_permutation,\n deq1 = (";  
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )  
      cout << " " << *d1_Iter << ",";  
   d1_Iter = --deq1.end( );  
   cout << " " << *d1_Iter << " )." << endl << endl;  
  
   // Permuting vector elements with binary function mod_lesser  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = -3 ; i <= 3 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   next_permutation ( v1.begin ( ) , v1.end ( ) , mod_lesser );  
  
   cout << "After the first next_permutation, vector v1 is:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   int iii = 1;  
   while ( iii <= 5 ) {  
      next_permutation ( v1.begin ( ) , v1.end ( ) , mod_lesser );  
      cout << "After another next_permutation of vector v1,\n v1 =   ( " ;  
      for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ;Iter1 ++ )  
         cout << *Iter1  << " ";  
      cout << ")." << endl;  
      iii++;  
   }  
}  
```  
  
```Output  
The original deque of CInts is deq1 = ( CInt( 5 ), CInt( 1 ), CInt( 10 ) ).  
The lexicographically next permutation exists and has  
replaced the original ordering of the sequence in deq1.  
After one application of next_permutation,  
 deq1 = ( CInt( 5 ), CInt( 10 ), CInt( 1 ) ).  
  
Vector v1 is ( -3 -2 -1 0 1 2 3 ).  
After the first next_permutation, vector v1 is:  
 v1 = ( -3 -2 -1 0 1 3 2 ).  
After another next_permutation of vector v1,  
 v1 =   ( -3 -2 -1 0 2 1 3 ).  
After another next_permutation of vector v1,  
 v1 =   ( -3 -2 -1 0 2 3 1 ).  
After another next_permutation of vector v1,  
 v1 =   ( -3 -2 -1 0 3 1 2 ).  
After another next_permutation of vector v1,  
 v1 =   ( -3 -2 -1 0 3 2 1 ).  
After another next_permutation of vector v1,  
 v1 =   ( -3 -2 -1 1 0 2 3 ).  
```  
  
##  <a name="nth_element"></a>  nth_element —  
 Partycje zakresu elementów poprawnie lokalizowanie *n*element th sekwencji w zakresie tak, aby wszystkie elementy przed nim są mniejsze niż lub równe go i wszystkie elementy, które po nim w sekwencji są większe th usługi lub jej równa.  
  
```  
template<class RandomAccessIterator>  
void nth_element( RandomAccessIterator first, RandomAccessIterator _Nth, RandomAccessIterator last);  
  
 template<class RandomAccessIterator, class BinaryPredicate>  
 void nth_element( RandomAccessIterator first, RandomAccessIterator _Nth, RandomAccessIterator last, BinaryPredicate comp);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Dostęp losowy iteratora adresowania położenie pierwszego elementu w zakresie do partycjonowania.  
  
 *_Nth*  
 Dostęp losowy iteratora adresowania położenie elementu umożliwiające prawidłowe sekwencjonowanie na granicy partycji.  
  
 `last`  
 Dostęp losowy iteratora adresowania jedną pozycję poza ostatniego elementu w zakresie do partycjonowania.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje kryterium porównania muszą być spełnione przez kolejnych elementów w kolejności. Predykat binarne przyjmuje dwa argumenty i zwraca **true** po spełnieniu i **false** gdy nie są spełnione.  
  
### <a name="remarks"></a>Uwagi  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 `nth_element` Algorytmu nie gwarantuje elementów w zakresy podrzędne albo strony z *n*th element są sortowane. W związku z tym że gwarancje mniej niż `partial_sort`, który Porządkuje elementy w zakresie poniżej niektórych wybrany element i może być używany jako szybsza do `partial_sort` podczas zamawiania dolna granica nie jest wymagana.  
  
 Elementy są równoważne, ale niekoniecznie równości, jeśli nie jest mniejsza niż innych.  
  
 Średnia złożoności sortowania jest liniowa w odniesieniu do * ostatni — najpierw *.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_nth_elem.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // For greater<int>( )  
#include <iostream>  
  
// Return whether first element is greater than the second  
bool UDgreater ( int elem1, int elem2 ) {  
   return elem1 > elem2;  
}  
  
int main() {  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
      v1.push_back( 3 * i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 5 ; ii++ )  
      v1.push_back( 3 * ii + 1 );  
  
   int iii;  
   for ( iii = 0 ; iii <= 5 ; iii++ )  
      v1.push_back( 3 * iii +2 );  
  
   cout << "Original vector:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   nth_element(v1.begin( ), v1.begin( ) + 3, v1.end( ) );  
   cout << "Position 3 partitioned vector:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in descending order, specify binary predicate  
   nth_element( v1.begin( ), v1.begin( ) + 4, v1.end( ),  
          greater<int>( ) );  
   cout << "Position 4 partitioned (greater) vector:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   random_shuffle( v1.begin( ), v1.end( ) );  
   cout << "Shuffled vector:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // A user-defined (UD) binary predicate can also be used  
   nth_element( v1.begin( ), v1.begin( ) + 5, v1.end( ), UDgreater );  
   cout << "Position 5 partitioned (UDgreater) vector:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
##  <a name="none_of"></a>  none_of  
 Zwraca `true` po warunek nigdy nie znajduje się między elementami w danym zakresie.  
  
```  
template<class InputIterator, class BinaryPredicate>  
bool none_of(InputIterator first, InputIterator last, BinaryPredicate comp);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterację wejściowych wskazuje, gdzie rozpoczynać do sprawdzania zakresu elementów w warunku.  
  
 `last`  
 Iterację wejściowych wskazuje koniec zakresu elementów.  
  
 `comp`  
 Warunek do sprawdzenia. To jest udostępniana przez obiekt zdefiniowane przez użytkownika funkcja predykatu, który definiuje warunek. Predykat pobiera jeden argument i zwraca `true` lub `false`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `true` Jeśli warunek nie wykryto co najmniej raz w zakresie wskazanych i `false` w przypadku wykrycia warunku.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu `true` tylko wtedy, gdy dla niektórych `N` w zakresie `[0, last - first)`, predykat `comp(*(first + N))` jest zawsze `false`.  
  
##  <a name="partial_sort"></a>  partial_sort —  
 Rozmieszcza określoną liczbę mniejszych elementów w zakresie w niemalejącej kolejności, lub według kryteriów sortowania określonych przez binarny predykat.  
  
```  
template<class RandomAccessIterator>  
   void partial_sort(  
      RandomAccessIterator first,   
      RandomAccessIterator sortEnd,  
      RandomAccessIterator last);
  
template<class RandomAccessIterator, class BinaryPredicate>  
   void partial_sort(  
      RandomAccessIterator first,   
      RandomAccessIterator sortEnd,  
      RandomAccessIterator last  
      BinaryPredicate comp);
  
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Dostęp losowy iteratora adresowania położenie pierwszego elementu w zakresie ma zostać posortowana.  
  
 `sortEnd`  
 Dostęp losowy iteratora adresowania poza ostatniego elementu w Podzakres pozycji, co ma zostać posortowana.  
  
 `last`  
 Dostęp losowy iteratora adresowania pozycji w jednym ostatniego elementu w zakresie częściowo sortowania.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje kryterium porównania muszą być spełnione przez kolejnych elementów w kolejności. Predykat binarne przyjmuje dwa argumenty i zwraca **true** po spełnieniu i **false** gdy nie są spełnione.  
  
### <a name="remarks"></a>Uwagi  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Elementy są równoważne, ale niekoniecznie równości, jeśli nie jest mniejsza niż innych. **Sortowania** algorytmu nie jest trwały i nie gwarantuje, że zostaną zachowane względne uporządkowanie równoważne elementów. Algorytm `stable_sort` zachować oryginalne porządkowania.  
  
 Złożoność średni częściowe sortowania jest *O*(( `last` -  `first`) dziennika ( `sortEnd` -  `first`)).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_partial_sort.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // For greater<int>( )  
#include <iostream>  
  
// Return whether first element is greater than the second  
bool UDgreater ( int elem1, int elem2 )  
{  
   return elem1 > elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 2 * i );  
   }  
  
   int ii;  
   for ( ii = 0 ; ii <= 5 ; ii++ )  
   {  
      v1.push_back( 2 * ii +1 );  
   }  
  
   cout << "Original vector:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   partial_sort(v1.begin( ), v1.begin( ) + 6, v1.end( ) );  
   cout << "Partially sorted vector:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To partially sort in descending order, specify binary predicate  
   partial_sort(v1.begin( ), v1.begin( ) + 4, v1.end( ), greater<int>( ) );  
   cout << "Partially resorted (greater) vector:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // A user-defined (UD) binary predicate can also be used  
   partial_sort(v1.begin( ), v1.begin( ) + 8, v1.end( ),   
 UDgreater );  
   cout << "Partially resorted (UDgreater) vector:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
```Output  
Original vector:  
 v1 = ( 0 2 4 6 8 10 1 3 5 7 9 11 )  
Partially sorted vector:  
 v1 = ( 0 1 2 3 4 5 10 8 6 7 9 11 )  
Partially resorted (greater) vector:  
 v1 = ( 11 10 9 8 0 1 2 3 4 5 6 7 )  
Partially resorted (UDgreater) vector:  
 v1 = ( 11 10 9 8 7 6 5 4 0 1 2 3 )  
```  
  
##  <a name="partial_sort_copy"></a>  partial_sort_copy —  
 Kopiuje elementy z zakresu źródłowego do zakresu docelowego, gdzie elementy źródłowe są uporządkowane według albo zasady mniejszy niż, albo innego określonego predykatu binarnego.  
  
```  
 template<class InputIterator, class RandomAccessIterator>  
 RandomAccessIterator partial_sort_copy(  
    InputIterator first1,  
    InputIterator last1,  
    RandomAccessIterator first2,  
    RandomAccessIterator last2 );  
  
template<class InputIterator, class RandomAccessIterator, class BinaryPredicate>  
 RandomAccessIterator partial_sort_copy(  
     InputIterator first1,  
     InputIterator last1,  
     RandomAccessIterator first2,  
     RandomAccessIterator last2,  
     BinaryPredicate comp);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first1`  
 Wejściowy iteratora adresowania położenie pierwszego elementu w zakresie źródłowym.  
  
 `last1`  
 Wejściowy iteratora adresowania pozycji w jednym ostatniego elementu w zakresie źródłowym.  
  
  `first2`  
 Iterator dostępie swobodnym, adresowania położenie pierwszego elementu w zakresie posortowane docelowym.  
  
 `last2`  
 Iterator dostępie swobodnym, adresowania pozycji w jednym ostatniego elementu w zakresie posortowane docelowym.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje warunek muszą być spełnione, jeśli dwa elementy mają zostać pobrane jako równoważne. Predykat binarne przyjmuje dwa argumenty i zwraca `true` po spełnieniu i `false` gdy nie są spełnione.  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator dostępie swobodnym, element docelowy zakres jedną pozycję po ostatnim elemencie adresowania wstawiony z zakresu źródła.  
  
### <a name="remarks"></a>Uwagi  
 Zakresy źródłowy i docelowy nie może nakładać się i musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w ramach każdej sekwencji ostatniej pozycji musi być dostępny z pierwszego przez przyrostowo zmieniać.  
  
 Predykat binarnego musi dostarczyć strict niska, porządkowanie, tak aby elementy, które nie są równoważne są uporządkowane, ale nie są elementami, które są równoważne. Dwa elementy są równoważne w mniej niż, ale niekoniecznie równości, jeśli nie jest mniejsza niż innych.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_partial_sort_copy.cpp  
// compile with: /EHsc  
#include <vector>  
#include <list>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main() {  
    using namespace std;  
    vector<int> v1, v2;  
    list<int> list1;  
    vector<int>::iterator iter1, iter2;  
    list<int>::iterator list1_Iter, list1_inIter;  
  
    int i;  
    for (i = 0; i <= 9; i++)  
        v1.push_back(i);  
  
    random_shuffle(v1.begin(), v1.end());  
  
    list1.push_back(60);  
    list1.push_back(50);  
    list1.push_back(20);  
    list1.push_back(30);  
    list1.push_back(40);  
    list1.push_back(10);  
  
    cout << "Vector v1 = ( " ;  
    for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)  
        cout << *iter1 << " ";  
    cout << ")" << endl;  
  
    cout << "List list1 = ( " ;  
    for (list1_Iter = list1.begin();  
         list1_Iter!= list1.end();  
         list1_Iter++)  
        cout << *list1_Iter << " ";  
    cout << ")" << endl;  
  
    // Copying a partially sorted copy of list1 into v1  
    vector<int>::iterator result1;  
    result1 = partial_sort_copy(list1.begin(), list1.end(),  
             v1.begin(), v1.begin() + 3);  
  
    cout << "List list1 Vector v1 = ( " ;  
    for (iter1 = v1.begin() ; iter1 != v1.end() ; iter1++)  
        cout << *iter1 << " ";  
    cout << ")" << endl;  
    cout << "The first v1 element one position beyond"  
         << "\n the last L 1 element inserted was " << *result1  
         << "." << endl;  
  
    // Copying a partially sorted copy of list1 into v2  
    int ii;  
    for (ii = 0; ii <= 9; ii++)  
        v2.push_back(ii);  
  
    random_shuffle(v2.begin(), v2.end());  
    vector<int>::iterator result2;  
    result2 = partial_sort_copy(list1.begin(), list1.end(),  
             v2.begin(), v2.begin() + 6);  
  
    cout << "List list1 into Vector v2 = ( " ;  
    for (iter2 = v2.begin() ; iter2 != v2.end(); iter2++)  
        cout << *iter2 << " ";  
    cout << ")" << endl;  
    cout << "The first v2 element one position beyond"  
         << "\n the last L 1 element inserted was " << *result2  
         << "." << endl;  
}  
```  
  
##  <a name="partition"></a>  Partycji  
 Klasyfikuje elementy w zakresie na dwa rozłączne zestawy, z elementami spełniającymi predykat unarny poprzedzającymi te, które go nie spełniają.  
  
```  
template<class BidirectionalIterator, class Predicate>  
   BidirectionalIterator partition(  
      BidirectionalIterator first,   
      BidirectionalIterator last,   
      Predicate comp);
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Dwukierunkowy iteratora adresowania położenie pierwszego elementu w zakresie do partycjonowania.  
  
 `last`  
 Dwukierunkowy iteratora adresowania jedną pozycję poza ostatniego elementu w zakresie do partycjonowania.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje warunek muszą być spełnione, jeśli element ma być klasyfikowane. Predykat pobiera jeden argument i zwraca **true** lub **false**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dwukierunkowy iteratora adresowania położenie pierwszego elementu w zakresie do spełnia warunek predykatu.  
  
### <a name="remarks"></a>Uwagi  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Elementy *a* i *b* są równoważne, ale nie musi być równa, jeśli obie *Pr* ( *a*, *b*) ma wartość false i *Pr* ( *b*, *a*) w przypadku wartości FAŁSZ, gdy *Pr* jest określony parametr predykatu. **Partycji** algorytmu nie jest trwały i nie gwarantuje, że zostaną zachowane względne uporządkowanie równoważne elementów. Algorytm **partycji stable_** zachować oryginalne porządkowania.  
  
 Złożoność jest liniowa: Brak ( `last`  -   `first`) aplikacji `comp` i co najwyżej ( `last`  -   `first`) / zamienia 2.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_partition.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
bool greater5 ( int value ) {  
   return value >5;  
}  
  
int main( ) {  
   using namespace std;  
   vector <int> v1, v2;  
   vector <int>::iterator Iter1, Iter2;  
  
   int i;  
   for ( i = 0 ; i <= 10 ; i++ )  
   {  
      v1.push_back( i );  
   }  
   random_shuffle( v1.begin( ), v1.end( ) );  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Partition the range with predicate greater10  
   partition ( v1.begin( ), v1.end( ), greater5 );  
   cout << "The partitioned set of elements in v1 is: ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="partition_copy"></a>  partition_copy —  
 Kopiuje elementy, dla których jest warunek `true` do jednego miejsca docelowego i dla których jest warunek `false` na inny. Elementy muszą pochodzić z określonego zakresu.  
  
```  
template<class InputIterator, class OutputIterator1, class OutputIterator2, class Predicate>  
    pair<OutputIterator1, OutputIterator2>  
        partition_copy(  
            InputIterator first,   
            InputIterator last,  
            OutputIterator1 dest1,   
            OutputIterator2 dest2,   
            Predicate pred  
        );  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterację wejściowych wskazuje początek zakresu, aby sprawdzić stan.  
  
 `last`  
 Iterację wejściowych wskazuje koniec zakresu.  
  
 `dest1`  
 Umożliwia kopiowanie elementów, które zwracają wartość true dla warunku iteratora danych wyjściowych testowane za pomocą `_Pred`.  
  
 `dest2`  
 Umożliwia kopiowanie elementów, które zwracają wartość false dla warunku iteratora danych wyjściowych testowane za pomocą `_Pred`.  
  
 `_Pred`  
 Warunek do sprawdzenia. To jest udostępniana przez obiekt zdefiniowane przez użytkownika funkcja predykatu, który definiuje warunek do sprawdzenia. Predykat pobiera jeden argument i zwraca `true` lub `false`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu kopiuje każdy element `X` w `[first,last)` do `*dest1++` Jeśli `_Pred(X)` ma wartość true, lub do `*dest2++` , jeśli nie. Zwraca `pair<OutputIterator1, OutputIterator2>(dest1, dest2)`.  
  
##  <a name="partition_point"></a>  partition_point  
 Zwraca pierwszy element w danym zakresie, który nie spełnia warunku. Elementy są sortowane, aby te, które spełniają warunek, występowały przed tymi, które go nie spełniają.  
  
```  
template<class ForwardIterator, class Predicate>  
    ForwardIterator partition_point(  
        ForwardIterator first,   
        ForwardIterator last,  
        Predicate comp  
    );  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 A `ForwardIterator` wskazujące początek zakresu, aby sprawdzić stan.  
  
 `last`  
 A `ForwardIterator` wskazujące końcową wartością zakresu.  
  
 `comp`  
 Warunek do sprawdzenia. To jest udostępniana przez obiekt zdefiniowane przez użytkownika funkcja predykatu, który definiuje warunek muszą być spełnione przez element wyszukane. Predykat pobiera jeden argument i zwraca `true` lub `false`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `ForwardIterator` odwołujący się do pierwszego elementu, który nie spełnia warunku, sprawdzane pod kątem przez `comp`, lub zwraca `last` Jeśli nie można odnaleźć.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu znajduje pierwszy iteratora `it` w `[first, last)` dla którego `comp(*it)` jest `false`. Sekwencja musi zostać określona przez `comp`.  
  
##  <a name="pop_heap"></a>  pop_heap —  
 Usuwa największy element z przodu sterty do przedostatniej pozycji w zakresie, a następnie tworzy nową stertę z pozostałych elementów.  
  
```  
template<class RandomAccessIterator>  
void pop_heap( RandomAccessIterator first, RandomAccessIterator last);  
  
template<class RandomAccessIterator, class BinaryPredicate>  
void pop_heap(RandomAccessIterator first, RandomAccessIterator last, BinaryPredicate comp);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterator dostępie swobodnym, adresowania położenie pierwszego elementu w stosie.  
  
 `last`  
 Iterator dostępie swobodnym, adresowania pozycji w jednym ostatniego elementu w stosie.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje znaczeniu, w której jeden element jest mniejsza niż innym. Predykat binarne przyjmuje dwa argumenty i zwraca **true** po spełnieniu i **false** gdy nie są spełnione.  
  
### <a name="remarks"></a>Uwagi  
 `pop_heap` Algorytm to odwrotność działania wykonywane przez algorytm push_heap —, w którym element na pozycji dalej do ostatniego zakresu zostanie dodany do stosu składające się z wcześniejszych elementów w zakresie, w przypadku, gdy element dodawany do stos jest większy niż elementy już w stosie.  
  
 Stosów ma dwie właściwości:  
  
-   Pierwszy element zawsze jest największy.  
  
-   Elementy może dodać lub usunąć w czasie logarytmicznych.  
  
 Stosów są idealne sposób implementowania priorytet kolejek i ich użycia w implementacji karty kontenera standardowa biblioteka C++ [priority_queue — klasa](../standard-library/priority-queue-class.md).  
  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Z wyjątkiem nowo dodany element na końcu zakresu musi być stosu.  
  
 Złożoność jest logarytmiczna, co najwyżej wymagające dziennika (* ostatni — najpierw *) porównania.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_pop_heap.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main( )  {  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1, Iter2;  
  
   int i;  
   for ( i = 1 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   // Make v1 a heap with default less than ordering  
   random_shuffle( v1.begin( ), v1.end( ) );  
   make_heap ( v1.begin( ), v1.end( ) );  
   cout << "The heaped version of vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Add an element to the back of the heap  
   v1.push_back( 10 );  
   push_heap( v1.begin( ), v1.end( ) );  
   cout << "The reheaped v1 with 10 added is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Remove the largest element from the heap  
   pop_heap( v1.begin( ), v1.end( ) );  
   cout << "The heap v1 with 10 removed is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl << endl;  
  
   // Make v1 a heap with greater-than ordering with a 0 element  
   make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );  
   v1.push_back( 0 );  
   push_heap( v1.begin( ), v1.end( ), greater<int>( ) );  
   cout << "The 'greater than' reheaped v1 puts the smallest "  
        << "element first:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Application of pop_heap to remove the smallest element  
   pop_heap( v1.begin( ), v1.end( ), greater<int>( ) );  
   cout << "The 'greater than' heaped v1 with the smallest element\n "  
        << "removed from the heap is: ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="prev_permutation"></a>  prev_permutation  
 Zmienia kolejność elementów w zakresie, dzięki czemu oryginalnego kolejność zostało zastąpione przez lexicographically poprzedniego permutacji większa, jeśli istnieje, w którym można określić znaczeniu poprzedniego z predykatem binarne.  
  
```  
template<class BidirectionalIterator>  
   bool prev_permutation(  
      BidirectionalIterator first,   
      BidirectionalIterator last);
  
template<class BidirectionalIterator, class BinaryPredicate>  
   bool prev_permutation(  
      BidirectionalIterator first,   
      BidirectionalIterator last,  
      BinaryPredicate comp);
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Dwukierunkowy iteratora wskazuje położenie pierwszego elementu w zakresie do cieniowania można.  
  
 `last`  
 Dwukierunkowy iteratora wskazujący pozycji w jednym ostatniego elementu w zakresie do cieniowania można.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje kryterium porównania muszą być spełnione przez kolejnych elementów w kolejności. Predykat binarne przyjmuje dwa argumenty i zwraca `true` po spełnieniu i `false` gdy nie są spełnione.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli lexicographically poprzedniego permutacji istnieje i zastąpione oryginalnego porządkowanie zakresu; w przeciwnym razie `false`, w którym to przypadku porządkowania jest przekształcana na lexicographically największy permutacji.  
  
### <a name="remarks"></a>Uwagi  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Predykat binarne domyślny jest mniejsza niż i elementy w zakresie musi być mniejsza-niż porównywalne do zapewnienia, że poprzednie permutacji jasno określone.  
  
 Złożoność jest liniowa, o co najwyżej ( `last`  -   `first`) / zamienia 2.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_prev_perm.cpp  
// compile with: /EHsc  
#include <vector>  
#include <deque>  
#include <algorithm>  
#include <iostream>  
#include <ostream>  
  
using namespace std;  
class CInt;  
ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
class CInt {  
public:  
   CInt( int n = 0 ) : m_nVal( n ){}  
   CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}  
   CInt&   operator=( const CInt& rhs ) {m_nVal =  
   rhs.m_nVal; return *this;}  
   bool operator<( const CInt& rhs ) const  
      {return ( m_nVal < rhs.m_nVal );}  
   friend ostream& operator<<( ostream& osIn, const CInt& rhs );  
  
private:  
   int m_nVal;  
};  
  
inline ostream& operator<<( ostream& osIn, const CInt& rhs ) {  
   osIn << "CInt( " << rhs.m_nVal << " )";  
   return osIn;  
}  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser (int elem1, int elem2 ) {  
   if ( elem1 < 0 )  
      elem1 = - elem1;  
   if ( elem2 < 0 )  
      elem2 = - elem2;  
   return elem1 < elem2;  
};  
  
int main() {  
   // Reordering the elements of type CInt in a deque  
   // using the prev_permutation algorithm  
   CInt c1 = 1, c2 = 5, c3 = 10;  
   bool deq1Result;  
   deque<CInt> deq1, deq2, deq3;  
   deque<CInt>::iterator d1_Iter;  
  
   deq1.push_back ( c1 );  
   deq1.push_back ( c2 );  
   deq1.push_back ( c3 );  
  
   cout << "The original deque of CInts is deq1 = (";  
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )  
      cout << " " << *d1_Iter << ",";  
   d1_Iter = --deq1.end( );  
   cout << " " << *d1_Iter << " )." << endl;  
  
   deq1Result = prev_permutation ( deq1.begin ( ) , deq1.end ( ) );  
  
   if ( deq1Result )  
      cout << "The lexicographically previous permutation "  
           << "exists and has \nreplaced the original "  
           << "ordering of the sequence in deq1." << endl;  
   else  
      cout << "The lexicographically previous permutation doesn't "  
           << "exist\n and the lexicographically "  
           << "smallest permutation\n has replaced the "  
           << "original ordering of the sequence in deq1." << endl;  
  
   cout << "After one application of prev_permutation,\n deq1 = (";  
   for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )  
      cout << " " << *d1_Iter << ",";  
   d1_Iter = --deq1.end( );  
   cout << " " << *d1_Iter << " )." << endl << endl;  
  
   // Permutating vector elements with binary function mod_lesser  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = -3 ; i <= 3 ; i++ )  
      v1.push_back( i );  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   prev_permutation ( v1.begin ( ) , v1.end ( ) , mod_lesser );  
  
   cout << "After the first prev_permutation, vector v1 is:\n v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   int iii = 1;  
   while ( iii <= 5 ) {  
      prev_permutation ( v1.begin ( ) , v1.end ( ) , mod_lesser );  
      cout << "After another prev_permutation of vector v1,\n v1 =   ( " ;  
      for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ;Iter1 ++ )  
         cout << *Iter1  << " ";  
      cout << ")." << endl;  
      iii++;  
   }  
}  
```  
  
```Output  
The original deque of CInts is deq1 = ( CInt( 1 ), CInt( 5 ), CInt( 10 ) ).  
The lexicographically previous permutation doesn't exist  
 and the lexicographically smallest permutation  
 has replaced the original ordering of the sequence in deq1.  
After one application of prev_permutation,  
 deq1 = ( CInt( 10 ), CInt( 5 ), CInt( 1 ) ).  
  
Vector v1 is ( -3 -2 -1 0 1 2 3 ).  
After the first prev_permutation, vector v1 is:  
 v1 = ( -3 -2 0 3 2 1 -1 ).  
After another prev_permutation of vector v1,  
 v1 =   ( -3 -2 0 3 -1 2 1 ).  
After another prev_permutation of vector v1,  
 v1 =   ( -3 -2 0 3 -1 1 2 ).  
After another prev_permutation of vector v1,  
 v1 =   ( -3 -2 0 2 3 1 -1 ).  
After another prev_permutation of vector v1,  
 v1 =   ( -3 -2 0 2 -1 3 1 ).  
After another prev_permutation of vector v1,  
 v1 =   ( -3 -2 0 2 -1 1 3 ).  
```  
  
##  <a name="push_heap"></a>  push_heap —  
 Dodaje element znajdujący się na końcu zakresu do istniejącej sterty, która składa się z poprzednich elementów w zakresie.  
  
```  
template<class RandomAccessIterator>  
void push_heap( RandomAccessIterator first, RandomAccessIterator last );  
  
template<class RandomAccessIterator, class BinaryPredicate>  
void push_heap( RandomAccessIterator first, RandomAccessIterator last, BinaryPredicate comp);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterator dostępie swobodnym, adresowania położenie pierwszego elementu w stosie.  
  
 `last`  
 Iterator dostępie swobodnym, adresowania jedną pozycję poza ostatniego elementu w zakresie ma zostać przekonwertowany do stosu.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje znaczeniu, w której jeden element jest mniejsza niż innym. Predykat binarne przyjmuje dwa argumenty i zwraca **true** po spełnieniu i **false** gdy nie są spełnione.  
  
### <a name="remarks"></a>Uwagi  
 Element musi najpierw zostać przesunięta wstecz na końcu stosu istniejących, a następnie można dodać tego elementu do istniejącej sterty jest używany algorytm.  
  
 Stosów ma dwie właściwości:  
  
-   Pierwszy element zawsze jest największy.  
  
-   Elementy może dodać lub usunąć w czasie logarytmicznych.  
  
 Stosów są idealne sposób implementowania priorytet kolejek i ich użycia w implementacji karty kontenera standardowa biblioteka C++ [priority_queue — klasa](../standard-library/priority-queue-class.md).  
  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Z wyjątkiem nowo dodany element na końcu zakresu musi być stosu.  
  
 Złożoność jest logarytmiczna, co najwyżej wymagające dziennika ( *ostatni — najpierw*) porównania.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_push_heap.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main( ) {  
   using namespace std;  
   vector <int> v1, v2;  
   vector <int>::iterator Iter1, Iter2;  
  
   int i;  
   for ( i = 1 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   random_shuffle( v1.begin( ), v1.end( ) );  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Make v1 a heap with default less than ordering  
   make_heap ( v1.begin( ), v1.end( ) );  
   cout << "The heaped version of vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Add an element to the heap  
   v1.push_back( 10 );  
   cout << "The heap v1 with 10 pushed back is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   push_heap( v1.begin( ), v1.end( ) );  
   cout << "The reheaped v1 with 10 added is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl << endl;  
  
   // Make v1 a heap with greater than ordering  
   make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );  
   cout << "The greater-than heaped version of v1 is\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   v1.push_back(0);  
   cout << "The greater-than heap v1 with 11 pushed back is\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   push_heap( v1.begin( ), v1.end( ), greater<int>( ) );  
   cout << "The greater than reheaped v1 with 11 added is\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="random_shuffle"></a>  random_shuffle —  
 Funkcja std::random_shuffle() jest przestarzały, zastępuje [std::shuffle](../standard-library/algorithm-functions.md#shuffle). Przykładowy kod i uzyskać więcej informacji, zobacz [ \<losowe >](../standard-library/random.md) i publikowanie Stackoverflow [dlaczego są metody std::random_shuffle przestarzałe w języku C ++ 14?](http://go.microsoft.com/fwlink/p/?linkid=397954).  
  
##  <a name="remove"></a>  Usuń  
 Eliminuje określoną wartość z danego zakresu bez zakłócania kolejności pozostałych elementów i zwracania końca nowego zakresu wolnego od określonej wartości.  
  
```  
template<class ForwardIterator, class Type>  
 ForwardIterator remove(ForwardIterator first, ForwardIterator last, const Type& val);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Adresowanie położenie pierwszego elementu w zakresie, w którym są usuwane elementy do przodu iteratora.  
  
 `last`  
 Adresowanie jedną pozycję poza ostatniego elementu w zakresie, w którym są usuwane elementy do przodu iteratora.  
  
 `val`  
 Wartość, która ma zostać usunięty z zakresu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowa pozycja końcowa zakresu zmodyfikowane, jeden poza ostatniego elementu sekwencji niewykorzystany wolne od określonej wartości adresowania do przodu iteratora.  
  
### <a name="remarks"></a>Uwagi  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Kolejność elementów usunięte nie jest trwały.  
  
 `operator==` Używany do określenia równości między elementami musi nałożyć równoważność stosunek argumentów.  
  
 Złożoność jest liniowa; Brak ( `last`  -   `first`) porównania równości.  
  
 [List — klasa](../standard-library/list-class.md) ma efektywniejsze wersja funkcji Członkowskich z **Usuń**, które również relinks wskaźniki.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_remove.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( ) {  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1, Iter2, new_end;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 3 ; ii++ )  
      v1.push_back( 7 );  
  
   random_shuffle ( v1.begin( ), v1.end( ) );  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Remove elements with a value of 7  
   new_end = remove ( v1.begin( ), v1.end( ), 7 );  
  
   cout << "Vector v1 with value 7 removed is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // To change the sequence size, use erase  
   v1.erase (new_end, v1.end( ) );  
  
   cout << "Vector v1 resized with value 7 removed is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="remove_copy"></a>  remove_copy  
 Kopiuje elementy z zakresu źródłowego do zakresu docelowego, z tym wyjątkiem, że elementy o określonej wartości nie są kopiowane, bez naruszania kolejności pozostałych elementów i zwracania końca nowego zakresu docelowego.  
  
```  
template<class InputIterator, class OutputIterator, class Type>  
 OutputIterator remove_copy(InputIterator first, InputIterator last, OutputIterator result, const Type& val);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Adresowanie położenie pierwszego elementu w zakresie, w którym są usuwane elementy wejściowe iteratora.  
  
 `last`  
 Wejściowy iteratora adresowania jedną pozycję poza ostatniego elementu w zakresie, w którym są usuwane elementy.  
  
 `result`  
 Dane wyjściowe iteratora adresowania położenie pierwszego elementu w zakresie docelowego, do którego elementy są usuwane.  
  
 `val`  
 Wartość, która ma zostać usunięty z zakresu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Do przodu iteratora adresowania Nowa pozycja końcowa zakresu docelowego, jeden poza ostatniego elementu kopię sekwencji niewykorzystany wolne od określonej wartości.  
  
### <a name="remarks"></a>Uwagi  
 Odwołuje się do zakresów źródłowych i docelowych musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Zakres docelowy zawiera elementy niewykorzystany, które zostaną skopiowane, po usunięciu elementów określona wartość musi być wystarczająca ilość miejsca.  
  
 Kolejność elementów usunięte nie jest trwały.  
  
 `operator==` Używany do określenia równości między elementami musi nałożyć równoważność stosunek argumentów.  
  
 Złożoność jest liniowa; Brak ( `last`  -   `first`) porównania równości i Max ( `last`  -   `first`) przypisania.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_remove_copy.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main() {  
   using namespace std;  
   vector <int> v1, v2(10);  
   vector <int>::iterator Iter1, Iter2, new_end;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 3 ; ii++ )  
      v1.push_back( 7 );  
  
   random_shuffle (v1.begin( ), v1.end( ) );  
   cout << "The original vector v1 is:     ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Remove elements with a value of 7  
   new_end = remove_copy ( v1.begin( ), v1.end( ), v2.begin( ), 7 );  
  
   cout << "Vector v1 is left unchanged as ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   cout << "Vector v2 is a copy of v1 with the value 7 removed:\n ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="remove_copy_if"></a>  remove_copy_if  
 Kopiuje elementy z zakresu źródłowego do zakresu docelowego, z tym wyjątkiem, że elementy spełniające predykat nie są kopiowane, bez naruszania kolejności pozostałych elementów i zwracania końca nowego zakresu docelowego.  
  
```  
template<class InputIterator, class OutputIterator, class Predicate>  
OutputIterator remove_copy_if(InputIterator first, InputIterator Last, OutputIterator result, Predicate pred);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Adresowanie położenie pierwszego elementu w zakresie, w którym są usuwane elementy wejściowe iteratora.  
  
 `last`  
 Wejściowy iteratora adresowania jedną pozycję poza ostatniego elementu w zakresie, w którym są usuwane elementy.  
  
 `result`  
 Dane wyjściowe iteratora adresowania położenie pierwszego elementu w zakresie docelowego, do którego elementy są usuwane.  
  
 `_Pred`  
 Predykat jednoargumentowe, które muszą być spełnione jest wartość elementu ma zostać zastąpiony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Adresowanie Nowa pozycja końcowa zakresu docelowego, jeden poza ostatniego elementu sekwencji niewykorzystany bez pasującego do predykatu elementy do przodu iteratora.  
  
### <a name="remarks"></a>Uwagi  
 Zakres źródłowy odwołania musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Zakres docelowy zawiera elementy niewykorzystany, które zostaną skopiowane, po usunięciu elementów określona wartość musi być wystarczająca ilość miejsca.  
  
 Kolejność elementów usunięte nie jest trwały.  
  
 `operator==` Używany do określenia równości między elementami musi nałożyć równoważność stosunek argumentów.  
  
 Złożoność jest liniowa: Brak ( `last`  -   `first`) porównania równości i Max ( `last`  -   `first`) przypisania.  
  
 Aby uzyskać informacje na zachowanie tych funkcji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_remove_copy_if.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
bool greater6 ( int value ) {  
   return value >6;  
}  
  
int main() {  
   using namespace std;  
   vector <int> v1, v2(10);  
   vector <int>::iterator Iter1, Iter2, new_end;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 3 ; ii++ )  
      v1.push_back( 7 );  
  
   random_shuffle ( v1.begin( ), v1.end( ) );  
   cout << "The original vector v1 is:      ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Remove elements with a value greater than 6  
   new_end = remove_copy_if ( v1.begin( ), v1.end( ),   
      v2.begin( ), greater6 );  
  
   cout << "After the appliation of remove_copy_if to v1,\n "  
        << "vector v1 is left unchanged as ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   cout << "Vector v2 is a copy of v1 with values greater "  
        << "than 6 removed:\n ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != new_end ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="remove_if"></a>  remove_if  
 Eliminuje elementy, które spełniają predykat, z danego zakresu bez zakłócania kolejności pozostałych elementów i zwracania końca nowego zakresu wolnego od określonej wartości.  
  
```  
template<class ForwardIterator, class Predicate>  
 ForwardIterator remove_if(ForwardIterator first, ForwardIterator last, Predicate pred);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Wskazuje położenie pierwszego elementu w zakresie, w którym są usuwane elementy do przodu iteratora.  
  
 `last`  
 Wskazuje położenie jedną poza ostatniego elementu w zakresie, w którym są usuwane elementy do przodu iteratora.  
  
 `_Pred`  
 Predykat jednoargumentowe, które muszą być spełnione jest wartość elementu ma zostać zastąpiony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowa pozycja końcowa zakresu zmodyfikowane, jeden poza ostatniego elementu sekwencji niewykorzystany wolne od określonej wartości adresowania do przodu iteratora.  
  
### <a name="remarks"></a>Uwagi  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Kolejność elementów usunięte nie jest trwały.  
  
 `operator==` Używany do określenia równości między elementami musi nałożyć równoważność stosunek argumentów.  
  
 Złożoność jest liniowa: Brak ( `last`  -   `first`) porównania równości.  
  
 Listy ma wersję efektywniejsze funkcja elementu członkowskiego Usuń, które relinks wskaźników.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_remove_if.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
bool greater6 ( int value ) {  
   return value >6;  
}  
  
int main( ) {  
   using namespace std;  
   vector <int> v1, v2;  
   vector <int>::iterator Iter1, Iter2, new_end;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 3 ; ii++ )  
      v1.push_back( 7 );  
  
   random_shuffle ( v1.begin( ), v1.end( ) );  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Remove elements satisfying predicate greater6  
   new_end = remove_if (v1.begin( ), v1.end( ), greater6 );  
  
   cout << "Vector v1 with elements satisfying greater6 removed is\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // To change the sequence size, use erase  
   v1.erase (new_end, v1.end( ) );  
  
   cout << "Vector v1 resized elements satisfying greater6 removed is\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="replace"></a>  Zamień  
 Sprawdza każdy element w zakresie i zastępuje go, jeśli odpowiada określonej wartości.  
  
```  
template<class ForwardIterator, class Type>  
void replace(ForwardIterator first, ForwardIterator last, const Type& _OldVal, const Type& _NewVal);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Wskazuje położenie pierwszego elementu w zakresie, z którego są zastępowane elementy do przodu iteratora.  
  
 `last`  
 Wskazuje położenie jedną poza ostatniego elementu w zakresie, w którym elementy są zastępowane do przodu iteratora.  
  
 `_OldVal`  
 Stara wartość elementów figury geometrycznej.  
  
 `_NewVal`  
 Nowa wartość jest przypisywany do elementy stara wartość.  
  
### <a name="remarks"></a>Uwagi  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Kolejność elementów zastąpione nie jest trwały.  
  
 `operator==` Używany do określenia równości między elementami musi nałożyć równoważność stosunek argumentów.  
  
 Złożoność jest liniowa; Brak ( `last`  -   `first`) porównania równości i Max ( `last`  -   `first`) przypisania nowe wartości.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_replace.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( ) {  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 3 ; ii++ )  
      v1.push_back( 7 );  
  
   random_shuffle (v1.begin( ), v1.end( ) );  
   cout << "The original vector v1 is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Replace elements with a value of 7 with a value of 700  
   replace (v1.begin( ), v1.end( ), 7 , 700);  
  
   cout << "The vector v1 with a value 700 replacing that of 7 is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="replace_copy"></a>  replace_copy  
 Sprawdza każdy element w zakresie źródłowym i zastępuje go, jeśli odpowiada określonej wartości, jednocześnie kopiując wynik do nowego zakresu docelowego.  
  
```  
 template<class InputIterator, class OutputIterator, class Type>  
 OutputIterator replace_copy(   
     InputIterator first,  
     InputIterator last,  
     OutputIterator result,  
     const Type& _OldVal,  
     const Type& _NewVal);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Wskazuje położenie pierwszego elementu w zakresie, w którym elementy są zastępowane iteratora wejściowego.  
  
 `last`  
 Wejściowy iteratora wskazujący pozycji w jednym ostatniego elementu w zakresie, w którym elementy są zastępowane.  
  
 `result`  
 Dane wyjściowe iteratora wskazujące pierwszy element w zakresie docelowego, do którego skopiowane zmieniony sekwencję elementów.  
  
 `_OldVal`  
 Stara wartość elementów figury geometrycznej.  
  
 `_NewVal`  
 Nowa wartość jest przypisywany do elementy stara wartość.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskazuje pozycji w jednym ostatniego elementu w zakresie docelowego, do którego skopiowane zmieniony sekwencję elementów iteratora danych wyjściowych.  
  
### <a name="remarks"></a>Uwagi  
 Odwołuje się do zakresów źródłowych i docelowych musi nakłada się na i muszą być prawidłowe: wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Kolejność elementów zastąpione nie jest trwały.  
  
 `operator==` Używany do określenia równości między elementami musi nałożyć równoważność stosunek argumentów.  
  
 Złożoność jest liniowa: Brak ( `last`  -   `first`) porównania równości i co najwyżej ( `last`  -   `first`) przypisania nowe wartości.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_replace_copy.cpp  
// compile with: /EHsc  
#include <vector>  
#include <list>  
#include <algorithm>  
#include <iostream>  
  
int main( ) {  
   using namespace std;  
   vector <int> v1;  
   list <int> L1 (15);  
   vector <int>::iterator Iter1;  
   list <int>::iterator L_Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 3 ; ii++ )  
      v1.push_back( 7 );  
  
   random_shuffle ( v1.begin( ), v1.end( ) );  
  
   int iii;  
   for ( iii = 0 ; iii <= 15 ; iii++ )  
      v1.push_back( 1 );  
  
   cout << "The original vector v1 is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Replace elements in one part of a vector with a value of 7  
   // with a value of 70 and copy into another part of the vector  
   replace_copy ( v1.begin( ), v1.begin( ) + 14,v1.end( ) -15, 7 , 70);  
  
   cout << "The vector v1 with a value 70 replacing that of 7 is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Replace elements in a vector with a value of 70  
   // with a value of 1 and copy into a list  
   replace_copy ( v1.begin( ), v1.begin( ) + 14,L1.begin( ), 7 , 1);  
  
   cout << "The list copy L1 of v1 with the value 0 replacing "  
        << "that of 7 is:\n ( " ;  
   for ( L_Iter1 = L1.begin( ) ; L_Iter1 != L1.end( ) ; L_Iter1++ )  
      cout << *L_Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="replace_copy_if"></a>  replace_copy_if  
 Sprawdza każdy element w zakresie źródłowym i zastępuje go, jeśli spełnia określony predykat, jednocześnie kopiując wynik do nowego zakresu docelowego.  
  
```  
template<class InputIterator, class OutputIterator, class Predicate, class Type>  
OutputIterator replace_copy_if(  
    InputIterator first,  
    InputIterator last,  
    OutputIterator result,  
    Predicate pred,  
    const Type& val);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Wskazuje położenie pierwszego elementu w zakresie, w którym elementy są zastępowane iteratora wejściowego.  
  
 `last`  
 Wejściowy iteratora wskazujący pozycji w jednym ostatniego elementu w zakresie, w którym elementy są zastępowane.  
  
 `result`  
 Wskazuje położenie pierwszego elementu w zakresie docelowego, do której są kopiowane elementy iteratora danych wyjściowych.  
  
 `_Pred`  
 Predykat jednoargumentowe, które muszą być spełnione jest wartość elementu ma zostać zastąpiony.  
  
 `val`  
 Nowa wartość jest przypisywany do elementów, których stara wartość spełnia predykatu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskazuje pozycji w jednym ostatniego elementu w zakresie docelowego, do którego skopiowane zmieniony sekwencję elementów iteratora danych wyjściowych.  
  
### <a name="remarks"></a>Uwagi  
 Odwołuje się do zakresów źródłowych i docelowych musi nakłada się na i muszą być prawidłowe: wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Kolejność elementów zastąpione nie jest trwały.  
  
 `operator==` Używany do określenia równości między elementami musi nałożyć równoważność stosunek argumentów.  
  
 Złożoność jest liniowa; Brak ( `last`  -   `first`) porównania równości i Max ( `last`  -   `first`) przypisania nowe wartości.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_replace_copy_if.cpp  
// compile with: /EHsc  
#include <vector>  
#include <list>  
#include <algorithm>  
#include <iostream>  
  
bool greater6 ( int value ) {  
   return value >6;  
}  
  
int main( ) {  
   using namespace std;  
   vector <int> v1;  
   list <int> L1 (13);  
   vector <int>::iterator Iter1;  
   list <int>::iterator L_Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 3 ; ii++ )  
      v1.push_back( 7 );  
  
   random_shuffle ( v1.begin( ), v1.end( ) );  
  
   int iii;  
   for ( iii = 0 ; iii <= 13 ; iii++ )  
      v1.push_back( 1 );  
  
   cout << "The original vector v1 is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Replace elements with a value of 7 in the 1st half of a vector  
   // with a value of 70 and copy it into the 2nd half of the vector  
   replace_copy_if ( v1.begin( ), v1.begin( ) + 14,v1.end( ) -14,  
      greater6 , 70);  
  
   cout << "The vector v1 with values of 70 replacing those greater"  
        << "\n than 6 in the 1st half & copied into the 2nd half is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Replace elements in a vector with a value of 70  
   // with a value of 1 and copy into a list  
   replace_copy_if ( v1.begin( ), v1.begin( ) + 13,L1.begin( ),  
      greater6 , -1 );  
  
   cout << "A list copy of vector v1 with the value -1\n replacing "  
        << "those greater than 6 is:\n ( " ;  
   for ( L_Iter1 = L1.begin( ) ; L_Iter1 != L1.end( ) ; L_Iter1++ )  
      cout << *L_Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="replace_if"></a>  replace_if  
 Sprawdza każdy element w zakresie i zastępuje go, jeśli spełnia określony predykat.  
  
```  
template<class ForwardIterator, class Predicate, class Type>  
void replace_if(ForwardIterator first, ForwardIterator last, Predicate pred, const Type& val);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Wskazuje położenie pierwszego elementu w zakresie, z którego są zastępowane elementy do przodu iteratora.  
  
 `last`  
 Wskazuje położenie jedną poza ostatniego elementu w zakresie, w którym elementy są zastępowane iteratora.  
  
 `_Pred`  
 Predykat jednoargumentowe, które muszą być spełnione jest wartość elementu ma zostać zastąpiony.  
  
 `val`  
 Nowa wartość jest przypisywany do elementów, których stara wartość spełnia predykatu.  
  
### <a name="remarks"></a>Uwagi  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Kolejność elementów zastąpione nie jest trwały.  
  
 Algorytm `replace_if` jest generalizacji algorytmu **Zastąp**, umożliwiając żadnych predykatu należy określić zamiast równości określonej stałej wartości.  
  
 `operator==` Używany do określenia równości między elementami musi nałożyć równoważność stosunek argumentów.  
  
 Złożoność jest liniowa: Brak ( `last`  -   `first`) porównania równości i co najwyżej ( `last`  -   `first`) przypisania nowe wartości.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_replace_if.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
bool greater6 ( int value ) {  
   return value >6;  
}  
  
int main( ) {  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
      v1.push_back( i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 3 ; ii++ )  
      v1.push_back( 7 );  
  
   random_shuffle ( v1.begin( ), v1.end( ) );  
   cout << "The original vector v1 is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Replace elements satisfying the predicate greater6  
   // with a value of 70  
   replace_if ( v1.begin( ), v1.end( ), greater6 , 70);  
  
   cout << "The vector v1 with a value 70 replacing those\n "  
        << "elements satisfying the greater6 predicate is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="reverse"></a>  Reverse  
 Odwraca kolejność elementów w obrębie zakresu.  
  
```  
template<class BidirectionalIterator>  
 void reverse(BidirectionalIterator first, BidirectionalIterator last);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Wskazuje położenie pierwszego elementu w ramach którego elementy są trwa cieniowania zakresu iteratora dwukierunkowego.  
  
 `last`  
 Iterator dwukierunkowego, wskazujący pozycji w jednym ostatniego elementu w ramach którego elementy są trwa cieniowania zakresu.  
  
### <a name="remarks"></a>Uwagi  
 Zakres źródłowy odwołania musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_reverse.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( ) {  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   cout << "The original vector v1 is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Reverse the elements in the vector   
   reverse (v1.begin( ), v1.end( ) );  
  
   cout << "The modified vector v1 with values reversed is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The original vector v1 is:  
 ( 0 1 2 3 4 5 6 7 8 9 ).  
The modified vector v1 with values reversed is:  
 ( 9 8 7 6 5 4 3 2 1 0 ).  
```  
  
##  <a name="reverse_copy"></a>  reverse_copy  
 Odwraca kolejność elementów w obrębie zakresu źródłowego, jednocześnie kopiując je do zakresu docelowego  
  
```  
template<class BidirectionalIterator, class OutputIterator>  
OutputIterator reverse_copy(   
    BidirectionalIterator  first,  
    BidirectionalIterator Last,  
    OutputIterator  result);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Wskazuje położenie pierwszego elementu w zakresie źródła w ramach którego elementy są trwa cieniowania iteratora dwukierunkowego.  
  
 `last`  
 Iterator dwukierunkowego, wskazujący pozycji w jednym ostatniego elementu w zakresie źródła w ramach którego elementy są trwa cieniowania.  
  
 `result`  
 Wskazuje położenie pierwszego elementu w zakresie docelowego, do której są kopiowane elementy iteratora danych wyjściowych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskazuje pozycji w jednym ostatniego elementu w zakresie docelowego, do którego skopiowane zmieniony sekwencję elementów iteratora danych wyjściowych.  
  
### <a name="remarks"></a>Uwagi  
 Odwołuje się do zakresów źródłowych i docelowych musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_reverse_copy.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( ) {  
   using namespace std;  
   vector <int> v1, v2( 10 );  
   vector <int>::iterator Iter1, Iter2;  
  
   int i;  
   for ( i = 0 ; i <= 9 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   cout << "The original vector v1 is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Reverse the elements in the vector   
   reverse_copy (v1.begin( ), v1.end( ), v2.begin( ) );  
  
   cout << "The copy v2 of the reversed vector v1 is:\n ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   cout << "The original vector v1 remains unmodified as:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="rotate"></a>  Obróć  
 Wymienia elementy znajdujące się w dwóch sąsiednich zakresach.  
  
```  
template<class ForwardIterator>  
 void rotate(ForwardIterator first, ForwardIterator middle, ForwardIterator last);  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterator do przodu adresowania położenie pierwszego elementu w zakresie jest.  
  
 `middle`  
 Definiowanie granic zakres adresów położenie pierwszego elementu w drugiej części zakresu, w której elementy są wymienianych z aliasami w pierwszej części zakresu do przodu iteratora.  
  
`Last`  
 Iterator do przodu adresowania pozycji w jednym ostatniego elementu w zakresie jest.  
  
### <a name="remarks"></a>Uwagi  
 Zakresy odwołania musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Złożoność jest liniowa z co najwyżej ( `last`  -   `first`) zamienia.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_rotate.cpp  
// compile with: /EHsc  
#include <vector>  
#include <deque>  
#include <algorithm>  
#include <iostream>  
  
int main( ) {  
   using namespace std;  
   vector <int> v1;  
   deque <int> d1;  
   vector <int>::iterator v1Iter1;  
   deque<int>::iterator d1Iter1;  
  
   int i;  
   for ( i = -3 ; i <= 5 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   int ii;  
   for ( ii =0 ; ii <= 5 ; ii++ )  
   {  
      d1.push_back( ii );  
   }  
  
   cout << "Vector v1 is ( " ;  
   for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )  
      cout << *v1Iter1  << " ";  
   cout << ")." << endl;  
  
   rotate ( v1.begin ( ) , v1.begin ( ) + 3 , v1.end ( ) );  
   cout << "After rotating, vector v1 is ( " ;  
   for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )  
      cout << *v1Iter1  << " ";  
   cout << ")." << endl;  
  
   cout << "The original deque d1 is ( " ;  
   for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )  
      cout << *d1Iter1  << " ";  
   cout << ")." << endl;  
  
   int iii = 1;  
   while ( iii <= d1.end ( ) - d1.begin ( ) ) {  
      rotate ( d1.begin ( ) , d1.begin ( ) + 1 , d1.end ( ) );  
      cout << "After the rotation of a single deque element to the back,\n d1 is   ( " ;  
      for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )  
         cout << *d1Iter1  << " ";  
      cout << ")." << endl;  
      iii++;  
   }  
}  
```  
  
```Output  
Vector v1 is ( -3 -2 -1 0 1 2 3 4 5 ).  
After rotating, vector v1 is ( 0 1 2 3 4 5 -3 -2 -1 ).  
The original deque d1 is ( 0 1 2 3 4 5 ).  
After the rotation of a single deque element to the back,  
 d1 is   ( 1 2 3 4 5 0 ).  
After the rotation of a single deque element to the back,  
 d1 is   ( 2 3 4 5 0 1 ).  
After the rotation of a single deque element to the back,  
 d1 is   ( 3 4 5 0 1 2 ).  
After the rotation of a single deque element to the back,  
 d1 is   ( 4 5 0 1 2 3 ).  
After the rotation of a single deque element to the back,  
 d1 is   ( 5 0 1 2 3 4 ).  
After the rotation of a single deque element to the back,  
 d1 is   ( 0 1 2 3 4 5 ).  
```  
  
##  <a name="rotate_copy"></a>  rotate_copy  
 Wymienia elementy w dwóch sąsiednich zakresach w ramach zakresu źródłowego i kopiuje wynik do zakresu docelowego.  
  
```  
template<class ForwardIterator, class OutputIterator>  
OutputIterator rotate_copy(  
    ForwardIterator first,  
    ForwardIterator middle,  
    ForwardIterator last,  
    OutputIterator result );  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterator do przodu adresowania położenie pierwszego elementu w zakresie jest.  
  
 `middle`  
 Definiowanie granic zakres adresów położenie pierwszego elementu w drugiej części zakresu, w której elementy są wymienianych z aliasami w pierwszej części zakresu do przodu iteratora.  
  
 _ `Last`  
 Iterator do przodu adresowania pozycji w jednym ostatniego elementu w zakresie jest.  
  
 `result`  
 Dane wyjściowe iteratora adresowania położenie pierwszego elementu w zakresie docelowym.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dane wyjściowe iteratora adresowania jedną pozycję poza ostatniego elementu w zakresie docelowym.  
  
### <a name="remarks"></a>Uwagi  
 Zakresy odwołania musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Złożoność jest liniowa z co najwyżej ( `last`  -   `first`) zamienia.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_rotate_copy.cpp  
// compile with: /EHsc  
#include <vector>  
#include <deque>  
#include <algorithm>  
#include <iostream>  
  
int main() {  
   using namespace std;  
   vector <int> v1 , v2 ( 9 );  
   deque <int> d1 , d2 ( 6 );  
   vector <int>::iterator v1Iter , v2Iter;  
   deque<int>::iterator d1Iter , d2Iter;  
  
   int i;  
   for ( i = -3 ; i <= 5 ; i++ )  
      v1.push_back( i );  
  
   int ii;  
   for ( ii =0 ; ii <= 5 ; ii++ )  
      d1.push_back( ii );  
  
   cout << "Vector v1 is ( " ;  
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )  
      cout << *v1Iter  << " ";  
   cout << ")." << endl;  
  
   rotate_copy ( v1.begin ( ) , v1.begin ( ) + 3 , v1.end ( ) , v2.begin ( ) );  
   cout << "After rotating, the vector v1 remains unchanged as:\n v1 = ( " ;  
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )  
      cout << *v1Iter  << " ";  
   cout << ")." << endl;  
  
   cout << "After rotating, the copy of vector v1 in v2 is:\n v2 = ( " ;  
   for ( v2Iter = v2.begin( ) ; v2Iter != v2.end( ) ;v2Iter ++ )  
      cout << *v2Iter  << " ";  
   cout << ")." << endl;  
  
   cout << "The original deque d1 is ( " ;  
   for ( d1Iter = d1.begin( ) ; d1Iter != d1.end( ) ;d1Iter ++ )  
      cout << *d1Iter  << " ";  
   cout << ")." << endl;  
  
   int iii = 1;  
   while ( iii <= d1.end ( ) - d1.begin ( ) )  
   {  
      rotate_copy ( d1.begin ( ) , d1.begin ( ) + iii , d1.end ( ) , d2.begin ( ) );  
      cout << "After the rotation of a single deque element to the back,\n d2 is   ( " ;  
      for ( d2Iter = d2.begin( ) ; d2Iter != d2.end( ) ;d2Iter ++ )  
         cout << *d2Iter  << " ";  
      cout << ")." << endl;  
      iii++;  
   }  
}  
```  
  
##  <a name="search"></a>  Wyszukiwanie  
 Wyszukuje pierwsze wystąpienie sekwencji w zakresie docelowym, której elementy są równe tym w danej sekwencji elementów lub której elementy są równoważne w sensie określonym przez predykat binarny dla elementów w danej sekwencji.  
  
```  
template<class ForwardIterator1, class ForwardIterator2>  
   ForwardIterator1 search(  
      ForwardIterator1 first1,   
      ForwardIterator1 last1,  
      ForwardIterator2 first2,   
      ForwardIterator2 last2);
  
template<class ForwardIterator1, class ForwardIterator2, class Predicate>  
   ForwardIterator1 search(  
      ForwardIterator1 first1,   
      ForwardIterator1 last1,  
      ForwardIterator2 first2,   
      ForwardIterator2 last2  
      Predicate comp);
  
```  
  
### <a name="parameters"></a>Parametry  
  `first1`  
 Iterator do przodu adresowania położenie pierwszego elementu w zakresie do wyszukania.  
  
 `last1`  
 Iterator do przodu adresowania pozycji w jednym ostatniego elementu w zakresie do wyszukania.  
  
  `first2`  
 Iterator do przodu adresowania położenie pierwszego elementu w zakresie do dopasowania.  
  
 `last2`  
 Iterator do przodu adresowania pozycji w jednym ostatniego elementu w zakresie do dopasowania.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje warunek muszą być spełnione, jeśli dwa elementy mają zostać pobrane jako równoważne. Predykat binarne przyjmuje dwa argumenty i zwraca **true** po spełnieniu i **false** gdy nie są spełnione.  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator do przodu, adresowania położenie pierwszego elementu pierwszy podsekwencji, odpowiadający określonej sekwencji lub jest równoważna w znaczeniu, określony przez predykat binarnego.  
  
### <a name="remarks"></a>Uwagi  
 `operator==` Używany do określenia pasuje do elementu i określona wartość musi nałożyć równoważność stosunek argumentów.  
  
 Zakresy odwołania musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w ramach każdej sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Średni złożoności jest liniowa względem rozmiar przeszukane zakresu, a jest również liniowej względem rozmiaru sekwencji wyszukane w najgorszym przypadku złożoności.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_search.cpp  
// compile with: /EHsc  
#include <vector>  
#include <list>  
#include <algorithm>  
#include <iostream>  
  
// Return whether second element is twice the first  
bool twice (int elem1, int elem2 )  
{  
   return 2 * elem1 == elem2;  
}  
  
int main( ) {  
   using namespace std;  
   vector <int> v1, v2;  
   list <int> L1;  
   vector <int>::iterator Iter1, Iter2;  
   list <int>::iterator L1_Iter, L1_inIter;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
  
   int ii;  
   for ( ii = 4 ; ii <= 5 ; ii++ )  
   {  
      L1.push_back( 5 * ii );  
   }  
  
   int iii;  
   for ( iii = 2 ; iii <= 4 ; iii++ )  
   {  
      v2.push_back( 10 * iii );  
   }  
  
   cout << "Vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "List L1 = ( " ;  
   for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )  
      cout << *L1_Iter << " ";  
   cout << ")" << endl;  
  
   cout << "Vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
      cout << ")" << endl;  
  
   // Searching v1 for first match to L1 under identity  
   vector <int>::iterator result1;  
   result1 = search (v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );  
  
   if ( result1 == v1.end( ) )  
      cout << "There is no match of L1 in v1."  
           << endl;  
   else  
      cout << "There is at least one match of L1 in v1"  
           << "\n and the first one begins at "  
           << "position "<< result1 - v1.begin( ) << "." << endl;  
  
   // Searching v1 for a match to L1 under the binary predicate twice  
   vector <int>::iterator result2;  
   result2 = search  (v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );  
  
   if ( result2 == v1.end( ) )  
      cout << "There is no match of L1 in v1."  
           << endl;  
   else  
      cout << "There is a sequence of elements in v1 that "  
           << "are equivalent\n to those in v2 under the binary "  
           << "predicate twice\n and the first one begins at position "  
           << result2 - v1.begin( ) << "." << endl;  
}  
```  
  
```Output  
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )  
List L1 = ( 20 25 )  
Vector v2 = ( 20 30 40 )  
There is at least one match of L1 in v1  
 and the first one begins at position 4.  
There is a sequence of elements in v1 that are equivalent  
 to those in v2 under the binary predicate twice  
 and the first one begins at position 2.  
```  
  
##  <a name="search_n"></a>  search_n —  
 Wyszukuje pierwszą podsekwencję w zakresie, w której określona liczba elementów ma określoną wartość lub relację do tej wartości określoną przez predykat binarny.  
  
```  
template<class ForwardIterator1, class Diff2, class Type>  
   ForwardIterator1 search_n(  
      ForwardIterator1 first1,   
      ForwardIterator1 last1,  
      Diff2 count,   
      const Type& val);
  
template<class ForwardIterator1, class Diff2, class Type, class BinaryPredicate>  
   ForwardIterator1 search_n(  
      ForwardIterator1 first1,   
      ForwardIterator1 last1,  
      Diff2 count,   
      const Type& val,  
      BinaryPredicate comp);
  
```  
  
### <a name="parameters"></a>Parametry  
  `first1`  
 Iterator do przodu adresowania położenie pierwszego elementu w zakresie do wyszukania.  
  
 `last1`  
 Iterator do przodu adresowania pozycji w jednym ostatniego elementu w zakresie do wyszukania.  
  
 `count`  
 Rozmiar podsekwencji wyszukane.  
  
 `val`  
 Wartość elementów w sekwencji wyszukane.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje warunek muszą być spełnione, jeśli dwa elementy mają zostać pobrane jako równoważne. Predykat binarne przyjmuje dwa argumenty i zwraca **true** po spełnieniu i **false** gdy nie są spełnione.  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator do przodu, adresowania położenie pierwszego elementu pierwszy podsekwencji, odpowiadający określonej sekwencji lub jest równoważna w znaczeniu, określony przez predykat binarnego.  
  
### <a name="remarks"></a>Uwagi  
 `operator==` Używany do określenia pasuje do elementu i określona wartość musi nałożyć równoważność stosunek argumentów.  
  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Złożoność jest liniowa względem rozmiaru przeszukiwane.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_search_n.cpp  
// compile with: /EHsc  
#include <vector>  
#include <list>  
#include <algorithm>  
#include <iostream>  
  
// Return whether second element is 1/2 of the first  
bool one_half ( int elem1, int elem2 )  
{  
   return elem1 == 2 * elem2;  
}  
  
int main( )   
{  
   using namespace std;  
   vector <int> v1, v2;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
  
   for ( i = 0 ; i <= 2 ; i++ )  
   {  
      v1.push_back( 5  );  
   }  
  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
  
   for ( i = 0 ; i <= 2 ; i++ )  
   {  
      v1.push_back( 10  );  
   }  
  
   cout << "Vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // Searching v1 for first match to (5 5 5) under identity  
   vector <int>::iterator result1;  
   result1 = search_n ( v1.begin( ), v1.end( ), 3, 5 );  
  
   if ( result1 == v1.end( ) )  
      cout << "There is no match for a sequence ( 5 5 5 ) in v1."  
           << endl;  
   else  
      cout << "There is at least one match of a sequence ( 5 5 5 )"  
           << "\n in v1 and the first one begins at "  
           << "position "<< result1 - v1.begin( ) << "." << endl;  
  
   // Searching v1 for first match to (5 5 5) under one_half  
   vector <int>::iterator result2;  
   result2 = search_n (v1.begin( ), v1.end( ), 3, 5, one_half );  
  
   if ( result2 == v1.end( ) )  
      cout << "There is no match for a sequence ( 5 5 5 ) in v1"  
           << " under the equivalence predicate one_half." << endl;  
   else  
      cout << "There is a match of a sequence ( 5 5 5 ) "  
           << "under the equivalence\n predicate one_half "  
           << "in v1 and the first one begins at "  
           << "position "<< result2 - v1.begin( ) << "." << endl;  
}  
```  
  
```Output  
Vector v1 = ( 0 5 10 15 20 25 5 5 5 0 5 10 15 20 25 10 10 10 )  
There is at least one match of a sequence ( 5 5 5 )  
 in v1 and the first one begins at position 6.  
There is a match of a sequence ( 5 5 5 ) under the equivalence  
 predicate one_half in v1 and the first one begins at position 15.  
```  
  
##  <a name="set_difference"></a>  set_difference —  
 Łączy w sobie wszystkie elementy, które należą do jednego posortowanego zakresu źródłowego, ale nie do drugiego posortowanego zakresu źródłowego, w pojedynczy, posortowany zakres docelowy, gdzie kryterium sortowania może być określone przez predykat binarny.  
  
```  
 template<class InputIterator1, class InputIterator2, class OutputIterator>  
 OutputIterator set_difference(  
     InputIterator1  first1,  
     InputIterator1  last1,  
     InputIterator2  first2,  
     InputIterator2  last2,  
     OutputIterator  result  );  
  
template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>  
OutputIterator set_difference(  
    InputIterator1  first1,  
    InputIterator1  last1,  
    InputIterator2  first2,  
    InputIterator2  last2,  
    OutputIterator  result,  
    BinaryPredicate  comp  );  
  
```  
  
### <a name="parameters"></a>Parametry  
 `first1`  
 Wejściowy iteratora adresowania położenie pierwszego elementu w pierwszym dwa zakresy posortowane źródła Zjednoczone i posortowane w jednym zakresem reprezentujący różnica dwóch zakresów.  
  
 `last1`  
 Iteratora wejściowych adresowania pozycja jeden po ostatnim elementem w pierwszym dwa zakresy posortowane źródła Zjednoczone i posortowane w jednym zakresem reprezentujący różnica dwóch zakresów.  
  
 `first2`  
 Wejściowy iteratora adresowania położenie pierwszego elementu w drugim dwóch kolejnych sortowane zakresów Zjednoczone i posortowane w jednym zakresem reprezentujący różnica dwóch zakresów.  
  
 `last2`  
 Wejściowy iteratora adresowania ostatnich pozycji, co ostatnim elementem w drugim dwóch kolejnych sortowane zakresów Zjednoczone i posortowane w jednym zakresem reprezentujący różnica dwóch zakresów.  
  
 `result`  
 Pozycja pierwszego elementu w zakres docelowy, w którym mają być scalone w jednym zakresem posortowane reprezentujący różnica dwóch zakresów dwóch zakresów adresów iteratora danych wyjściowych.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje znaczeniu, w której jeden element jest większa niż innym. Predykat binarne przyjmuje dwa argumenty i powinna zostać zwrócona **true** po pierwszym elementem jest mniejszy od drugiego elementu i **false** inaczej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dane wyjściowe iteratora adresowania jedną pozycję po ostatnim elementem w zakres docelowy posortowane reprezentujący różnica dwóch zakresów.  
  
### <a name="remarks"></a>Uwagi  
 Posortowane zakresów odwołania musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w ramach każdej sekwencji ostatniej pozycji musi być dostępny z pierwszego przez przyrostowo zmieniać.  
  
 Zakres docelowy nie powinien zachodzić albo zakresów i powinien być wystarczająco duży, aby zawierać pierwszego zakresu źródła.  
  
 Posortowane zakresów muszą być ustawione jako warunek wstępny stosowania `set_difference` algorytm zgodnie z tej samej kolejności jak ma być używany przez algorytm sortowania połączonych zakresów.  
  
 Operacja jest stabilna jako względną kolejność elementów w obrębie każdego zakresu jest zachowywana w zakresie docelowym. Zakresów nie są modyfikowane przez scalenie algorytmu.  
  
 Typy wartości wejściowych Iteratory musi być mniejszy niż porównywanie może zostać określona, tak, aby dane dwa elementy mogą ustalić, czy są równoważne (w tym sensie, że nie jest mniejsza niż drugi) albo że jeden jest mniejsza niż innych. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Gdy w obu zakresów źródła równoważny elementów, elementy w zakresie pierwszy poprzedzać elementy z drugiego zakresu źródła w zakresie docelowym. Jeśli zakresów zawierają duplikaty elementu w taki sposób, że istnieją bardziej pierwszego zakresu źródła niż w ciągu sekundy, następnie zakres docelowy będzie zawierać liczbę za pomocą którego wystąpień tych elementów w zakresie pierwszego źródła przekracza wystąpień te elementy w zakresie drugiego źródła.  
  
 Złożoność algorytm jest liniowa z maksymalnie 2 \* (( *Nazwisko1 - first1*)-( *Nazwisko2 - first2*)) - 1 porównań niepustym zakresów.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_set_diff.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // For greater<int>( )  
#include <iostream>  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser (int elem1, int elem2 )  
{  
   if (elem1 < 0)   
      elem1 = - elem1;  
   if (elem2 < 0)   
      elem2 = - elem2;  
   return elem1 < elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1a, v1b, v1 ( 12 );  
   vector <int>::iterator Iter1a,  Iter1b, Iter1, Result1;  
  
   // Constructing vectors v1a & v1b with default less-than ordering  
   int i;  
   for ( i = -1 ; i <= 4 ; i++ )  
   {  
      v1a.push_back(  i );  
   }  
  
   int ii;  
   for ( ii =-3 ; ii <= 0 ; ii++ )  
   {  
      v1b.push_back(  ii  );  
   }  
  
   cout << "Original vector v1a with range sorted by the\n "  
        <<  "binary predicate less than is  v1a = ( " ;  
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )  
      cout << *Iter1a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v1b with range sorted by the\n "  
        <<  "binary predicate less than is  v1b = ( " ;  
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )  
      cout << *Iter1b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v2a & v2b with ranges sorted by greater  
   vector <int> v2a ( v1a ) , v2b ( v1b ) ,  v2 ( v1 );  
   vector <int>::iterator Iter2a, Iter2b, Iter2, Result2;  
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );  
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );  
  
   cout << "Original vector v2a with range sorted by the\n "  
        <<  "binary predicate greater is   v2a =  ( " ;  
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )  
      cout << *Iter2a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v2b with range sorted by the\n "  
        <<  "binary predicate greater is   v2b =  ( " ;  
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )  
      cout << *Iter2b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser  
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );  
   vector <int>::iterator Iter3a,  Iter3b, Iter3, Result3;  
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );  
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser  );  
  
   cout << "Original vector v3a with range sorted by the\n "  
        <<  "binary predicate mod_lesser is   v3a =  ( " ;  
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )  
      cout << *Iter3a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v3b with range sorted by the\n "  
        <<  "binary predicate mod_lesser is   v3b =  ( " ;  
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )  
      cout << *Iter3b << " ";  
   cout << ")." << endl;  
  
   // To combine into a difference in asscending  
   // order with the default binary predicate less <int> ( )  
   Result1 = set_difference ( v1a.begin ( ) , v1a.end ( ) ,  
      v1b.begin ( ) , v1b.end ( ) , v1.begin ( ) );  
   cout << "Set_difference of source ranges with default order,"  
        << "\n vector v1mod =  ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // To combine into a difference in descending  
   // order specify binary predicate greater<int>( )  
   Result2 = set_difference ( v2a.begin ( ) , v2a.end ( ) ,  
      v2b.begin ( ) , v2b.end ( ) ,v2.begin ( ) , greater <int> ( ) );  
   cout << "Set_difference of source ranges with binary"  
        << "predicate greater specified,\n vector v2mod  = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   // To combine into a difference applying a user  
   // defined binary predicate mod_lesser  
   Result3 = set_difference (  v3a.begin ( ) , v3a.end ( ) ,  
      v3b.begin ( ) , v3b.end ( ) , v3.begin ( ) , mod_lesser );  
   cout << "Set_difference of source ranges with binary "  
        << "predicate mod_lesser specified,\n vector v3mod  = ( " ; ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="set_intersection"></a>  set_intersection —  
 Łączy w sobie wszystkie elementy, które należą do obu posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.  
  
```  
 template<class InputIterator1, class InputIterator2, class OutputIterator>  
 OutputIterator set_intersection(   
      InputIterator1 first1,  
      InputIterator1 last1,  
      InputIterator2 first2,  
      InputIterator2 last2,  
      OutputIterator result );  
  
template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>  
OutputIterator set_intersection(  
      InputIterator1 first1,  
      InputIterator1 last1,  
      InputIterator2 first2,  
      InputIterator2 last2,  
      OutputIterator result,  
      BinaryPredicate comp );  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first1`  
 Wejściowy iteratora adresowania położenie pierwszego elementu w pierwszym dwa zakresy posortowane źródła Zjednoczone i posortowane w jednym zakresem reprezentujący część wspólną dwóch zakresów.  
  
 `last1`  
 Iteratora wejściowych adresowania pozycja jeden po ostatnim elementem w pierwszym dwa zakresy posortowane źródła Zjednoczone i posortowane w jednym zakresem reprezentujący część wspólną dwóch zakresów.  
  
  `first2`  
 Wejściowy iteratora adresowania położenie pierwszego elementu w drugim dwóch kolejnych sortowane zakresów Zjednoczone i posortowane w jednym zakresem reprezentujący część wspólną dwóch zakresów.  
  
 `last2`  
 Wejściowy iteratora adresowania ostatnich pozycji, co ostatnim elementem w drugim dwóch kolejnych sortowane zakresów Zjednoczone i posortowane w jednym zakresem reprezentujący część wspólną dwóch zakresów.  
  
 **_** *Wynik*  
 Pozycja pierwszego elementu w zakres docelowy, w którym mają być scalone w jednym zakresem posortowane reprezentujący część wspólną dwóch zakresów dwóch zakresów adresów iteratora danych wyjściowych.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje znaczeniu, w której jeden element jest większa niż innym. Predykat binarne przyjmuje dwa argumenty i powinna zostać zwrócona **true** po pierwszym elementem jest mniejszy od drugiego elementu i **false** inaczej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dane wyjściowe iteratora adresowania jedną pozycję po ostatnim elementem w zakres docelowy posortowane reprezentujący część wspólną dwóch zakresów.  
  
### <a name="remarks"></a>Uwagi  
 Posortowane zakresów odwołania musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w ramach każdej sekwencji ostatniej pozycji musi być dostępny z pierwszego przez przyrostowo zmieniać.  
  
 Zakres docelowy nie powinien zachodzić albo zakresów i powinien być wystarczająco duży, ma zakres docelowy.  
  
 Jest posortowane zakresy muszą być ustawione jako warunek wstępny stosowanie algorytmu scalania zgodnie z tej samej porządkowanie jako źródła do użycia przez algorytm sortowania połączonych zakresów.  
  
 Operacja jest stabilna jako względną kolejność elementów w obrębie każdego zakresu jest zachowywana w zakresie docelowym. Zakresów nie są modyfikowane przez algorytm.  
  
 Typy wartości wejściowych Iteratory musi być mniejsza-niż porównywalne może zostać określona, tak, aby dane dwa elementy, można ustalić czy są równoważne (w tym sensie, że nie jest mniejsza niż drugi) albo że jeden jest mniejsza niż innych. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Gdy w obu zakresów źródła równoważny elementów, elementy w zakresie pierwszy poprzedzać elementy z drugiego zakresu źródła w zakresie docelowym. Jeśli zakresów zawierać duplikatów elementu, zakres docelowy będzie zawierał maksymalną liczbę tych elementów, które występują w obu zakresów źródła.  
  
 Złożoność algorytm jest liniowa z maksymalnie 2 \* (( *Nazwisko1 - first1*) + ( *Nazwisko2 - first2*)) - 1 porównań niepustym zakresów.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_set_intersection.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>   // For greater<int>( )  
#include <iostream>  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser (int elem1, int elem2 ) {  
   if ( elem1 < 0 )   
      elem1 = - elem1;  
   if ( elem2 < 0 )   
      elem2 = - elem2;  
   return elem1 < elem2;  
}  
  
int main() {  
   using namespace std;  
   vector <int> v1a, v1b, v1 ( 12 );  
   vector <int>::iterator Iter1a,  Iter1b, Iter1, Result1;  
  
   // Constructing vectors v1a & v1b with default less than ordering  
   int i;  
   for ( i = -1 ; i <= 3 ; i++ )  
      v1a.push_back( i );  
  
   int ii;  
   for ( ii =-3 ; ii <= 1 ; ii++ )  
      v1b.push_back( ii );  
  
   cout << "Original vector v1a with range sorted by the\n "  
        <<  "binary predicate less than is  v1a = ( " ;  
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )  
      cout << *Iter1a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v1b with range sorted by the\n "  
        <<  "binary predicate less than is  v1b = ( " ;  
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )  
      cout << *Iter1b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v2a & v2b with ranges sorted by greater  
   vector <int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );  
   vector <int>::iterator Iter2a, Iter2b, Iter2, Result2;  
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );  
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );  
  
   cout << "Original vector v2a with range sorted by the\n "  
        << "binary predicate greater is   v2a =  ( " ;  
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )  
      cout << *Iter2a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v2b with range sorted by the\n "  
        << "binary predicate greater is   v2b =  ( " ;  
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )  
      cout << *Iter2b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser  
   vector <int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );  
   vector <int>::iterator Iter3a,  Iter3b, Iter3, Result3;  
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );  
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser );  
  
   cout << "Original vector v3a with range sorted by the\n "  
        <<  "binary predicate mod_lesser is   v3a =  ( " ;  
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )  
      cout << *Iter3a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v3b with range sorted by the\n "  
           <<  "binary predicate mod_lesser is   v3b =  ( " ;  
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )  
      cout << *Iter3b << " ";  
   cout << ")." << endl;  
  
   // To combine into an intersection in asscending order with the  
   // default binary predicate less <int> ( )  
   Result1 = set_intersection ( v1a.begin ( ) , v1a.end ( ) ,  
      v1b.begin ( ) , v1b.end ( ) , v1.begin ( ) );  
   cout << "Intersection of source ranges with default order,"  
        << "\n vector v1mod =  ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; ++Iter1 )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // To combine into an intersection in descending order, specify  
   // binary predicate greater<int>( )  
   Result2 = set_intersection ( v2a.begin ( ) , v2a.end ( ) ,  
      v2b.begin ( ) , v2b.end ( ) ,v2.begin ( ) , greater <int> ( ) );  
   cout << "Intersection of source ranges with binary predicate"  
        << " greater specified,\n vector v2mod  = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; ++Iter2 )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   // To combine into an intersection applying a user-defined  
   // binary predicate mod_lesser  
   Result3 = set_intersection ( v3a.begin ( ) , v3a.end ( ) ,  
      v3b.begin ( ) , v3b.end ( ) , v3.begin ( ) , mod_lesser );  
   cout << "Intersection of source ranges with binary predicate "  
        << "mod_lesser specified,\n vector v3mod  = ( " ; ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; ++Iter3 )  
      cout << *Iter3 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="set_symmetric_difference"></a>  set_symmetric_difference —  
 Łączy w sobie wszystkie elementy, które należą do jednego z, ale nie obu posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.  
  
```  
template<class InputIterator1, class InputIterator2, class OutputIterator>  
 OutputIterator set_symmetric_difference(  
    InputIterator1 first1,  
    InputIterator1 last1,  
    InputIterator2 first2,  
    InputIterator2 last2,  
    OutputIterator result );  
  
template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>  
OutputIterator set_symmetric_difference(  
    InputIterator1 first1,  
    InputIterator1 last1,  
    InputIterator2 first2,  
    InputIterator2 last2,  
    OutputIterator result,  
    BinaryPredicate comp );  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first1`  
 Wejściowy iteratora adresowania położenie pierwszego elementu w pierwszym dwa zakresy posortowane źródła Zjednoczone i posortowane w jednym zakresem reprezentujący symetrycznego różnica dwóch zakresów.  
  
 `last1`  
 Iteratora wejściowych adresowania pozycja jeden po ostatnim elementem w pierwszym dwa zakresy posortowane źródła Zjednoczone i posortowane w jednym zakresem reprezentujący symetrycznego różnica dwóch zakresów.  
  
  `first2`  
 Wejściowy iteratora adresowania położenie pierwszego elementu w drugim dwóch kolejnych sortowane zakresów Zjednoczone i posortowane w jednym zakresem reprezentujący symetrycznego różnica dwóch zakresów.  
  
 `last2`  
 Wejściowy iteratora adresowania ostatnich pozycji, co ostatnim elementem w drugim dwóch kolejnych sortowane zakresów Zjednoczone i posortowane w jednym zakresem reprezentujący symetrycznego różnica dwóch zakresów.  
  
 **_** *Wynik*  
 Pozycja pierwszego elementu w zakres docelowy, w którym mają być scalone w jednym zakresem posortowane reprezentujący symetrycznego różnica dwóch zakresów dwóch zakresów adresów iteratora danych wyjściowych.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje znaczeniu, w której jeden element jest większa niż innym. Predykat binarne przyjmuje dwa argumenty i powinna zostać zwrócona **true** po pierwszym elementem jest mniejszy od drugiego elementu i **false** inaczej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dane wyjściowe iteratora adresowania pozycji w jedną ostatniego elementu w zakresie posortowane docelowym reprezentujący symetrycznego różnica dwóch zakresów.  
  
### <a name="remarks"></a>Uwagi  
 Posortowane zakresów odwołania musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w ramach każdej sekwencji ostatniej pozycji musi być dostępny z pierwszego przez przyrostowo zmieniać.  
  
 Zakres docelowy nie powinien zachodzić albo zakresów i powinien być wystarczająco duży, ma zakres docelowy.  
  
 Posortowane zakresów muszą być ustawione jako warunek wstępny stosowania **scalania** algorytm zgodnie z tej samej kolejności jak ma być używany przez algorytm sortowania połączonych zakresów.  
  
 Operacja jest stabilna jako względną kolejność elementów w obrębie każdego zakresu jest zachowywana w zakresie docelowym. Zakresów nie są modyfikowane przez scalenie algorytmu.  
  
 Typy wartości wejściowych Iteratory musi być mniejsza-niż porównywalne może zostać określona, tak, aby dane dwa elementy, można ustalić czy są równoważne (w tym sensie, że nie jest mniejsza niż drugi) albo że jeden jest mniejsza niż innych. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Gdy w obu zakresów źródła równoważny elementów, elementy w zakresie pierwszy poprzedzać elementy z drugiego zakresu źródła w zakresie docelowym. Jeśli zakresów zawierać duplikatów elementu, następnie zakres docelowy będzie zawierał wartość bezwzględna liczby wystąpień tych elementów w jednym z zakresów przekracza wystąpień tych elementów w źródle drugi zakres.  
  
 Złożoność algorytm jest liniowa z maksymalnie 2 \* ((*Nazwisko1 - first1*)-(*Nazwisko2 - first2*)) - 1 porównań niepustym zakresów.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_set_sym_diff.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // For greater<int>( )  
#include <iostream>  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser (int elem1, int elem2 )  
{  
   if ( elem1 < 0 )   
      elem1 = - elem1;  
   if ( elem2 < 0 )   
      elem2 = - elem2;  
   return elem1 < elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1a, v1b, v1 ( 12 );  
   vector <int>::iterator Iter1a,  Iter1b, Iter1, Result1;  
  
   // Constructing vectors v1a & v1b with default less-than ordering  
   int i;  
   for ( i = -1 ; i <= 4 ; i++ )  
   {  
      v1a.push_back(  i );  
   }  
  
   int ii;  
   for ( ii =-3 ; ii <= 0 ; ii++ )  
   {  
      v1b.push_back(  ii  );  
   }  
  
   cout << "Original vector v1a with range sorted by the\n "  
        <<  "binary predicate less than is  v1a = ( " ;  
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )  
      cout << *Iter1a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v1b with range sorted by the\n "  
        <<  "binary predicate less than is  v1b = ( " ;  
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )  
      cout << *Iter1b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v2a & v2b with ranges sorted by greater  
   vector <int> v2a ( v1a ) , v2b ( v1b ) ,  v2 ( v1 );  
   vector <int>::iterator Iter2a, Iter2b, Iter2, Result2;  
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );  
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );  
  
   cout << "Original vector v2a with range sorted by the\n "  
        <<  "binary predicate greater is   v2a =  ( " ;  
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )  
      cout << *Iter2a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v2b with range sorted by the\n "  
        <<  "binary predicate greater is   v2b =  ( " ;  
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )  
      cout << *Iter2b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser  
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );  
   vector <int>::iterator Iter3a, Iter3b, Iter3, Result3;  
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );  
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser  );  
  
   cout << "Original vector v3a with range sorted by the\n "  
        <<  "binary predicate mod_lesser is   v3a =  ( " ;  
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )  
      cout << *Iter3a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v3b with range sorted by the\n "  
        <<  "binary predicate mod_lesser is   v3b =  ( " ;  
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )  
      cout << *Iter3b << " ";  
   cout << ")." << endl;  
  
   // To combine into a symmetric difference in ascending  
   // order with the default binary predicate less <int> ( )  
   Result1 = set_symmetric_difference ( v1a.begin ( ) , v1a.end ( ) ,  
      v1b.begin ( ) , v1b.end ( ) , v1.begin ( ) );  
   cout << "Set_symmetric_difference of source ranges with default order,"  
        << "\n vector v1mod =  ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // To combine into a symmetric difference in descending  
   // order, specify binary predicate greater<int>( )  
   Result2 = set_symmetric_difference ( v2a.begin ( ) , v2a.end ( ) ,  
      v2b.begin ( ) , v2b.end ( ) ,v2.begin ( ) , greater <int> ( ) );  
   cout << "Set_symmetric_difference of source ranges with binary"  
        << "predicate greater specified,\n vector v2mod  = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   // To combine into a symmetric difference applying a user  
   // defined binary predicate mod_lesser  
   Result3 = set_symmetric_difference ( v3a.begin ( ) , v3a.end ( ) ,  
      v3b.begin ( ) , v3b.end ( ) , v3.begin ( ) , mod_lesser );  
   cout << "Set_symmetric_difference of source ranges with binary "  
        << "predicate mod_lesser specified,\n vector v3mod  = ( " ; ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="set_union"></a>  set_union —  
 Łączy w sobie wszystkie elementy, które należą do przynajmniej jednego z dwóch posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.  
  
```  
 template<class InputIterator1, class InputIterator2, class OutputIterator>  
 OutputIterator set_union(  
    InputIterator1 first1,  
    InputIterator1 last1,  
    InputIterator2 first2,  
    InputIterator2 last2,  
    OutputIterator result );   
  
template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryPredicate>  
OutputIterator set_union(  
    InputIterator1 first1,  
    InputIterator1 last1,  
    InputIterator2 first2,  
    InputIterator2 last2,  
    OutputIterator result,  
    BinaryPredicate comp );  
```  
  
### <a name="parameters"></a>Parametry  
  `first1`  
 Wejściowy iteratora adresowania położenie pierwszego elementu w pierwszym dwa zakresy posortowane źródła Zjednoczone i posortowane w jednym zakresem reprezentujący złożenie dwóch zakresów.  
  
 `last1`  
 Iteratora wejściowych adresowania pozycja jeden po ostatnim elementem w pierwszym dwa zakresy posortowane źródła Zjednoczone i posortowane w jednym zakresem reprezentujący złożenie dwóch zakresów.  
  
  `first2`  
 Wejściowy iteratora adresowania położenie pierwszego elementu w drugim dwóch kolejnych sortowane zakresów Zjednoczone i posortowane w jednym zakresem reprezentujący złożenie dwóch zakresów.  
  
 `last2`  
 Wejściowy iteratora adresowania ostatnich pozycji, co ostatnim elementem w drugim dwóch kolejnych sortowane zakresów Zjednoczone i posortowane w jednym zakresem reprezentujący złożenie dwóch zakresów.  
  
 **_** *Wynik*  
 Pozycja pierwszego elementu w zakres docelowy, w którym mają być scalone w jednym zakresem posortowane reprezentujący złożenie dwóch zakresów dwóch zakresów adresów iteratora danych wyjściowych.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje znaczeniu, w której jeden element jest większa niż innym. Predykat binarne przyjmuje dwa argumenty i powinna zostać zwrócona **true** po pierwszym elementem jest mniejszy od drugiego elementu i **false** inaczej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dane wyjściowe iteratora adresowania jedną pozycję po ostatnim elementem w zakres docelowy posortowane reprezentujący złożenie dwóch zakresów.  
  
### <a name="remarks"></a>Uwagi  
 Posortowane zakresów odwołania musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w ramach każdej sekwencji ostatniej pozycji musi być dostępny z pierwszego przez przyrostowo zmieniać.  
  
 Zakres docelowy nie powinien zachodzić albo zakresów i powinien być wystarczająco duży, ma zakres docelowy.  
  
 Posortowane zakresów muszą być ustawione jako warunek wstępny stosowania **scalania** algorytm zgodnie z tej samej kolejności jak ma być używany przez algorytm sortowania połączonych zakresów.  
  
 Operacja jest stabilna jako względną kolejność elementów w obrębie każdego zakresu jest zachowywana w zakresie docelowym. Zakresów nie są modyfikowane przez algorytm **scalania**.  
  
 Typy wartości wejściowych Iteratory musi być mniejsza-niż porównywalne może zostać określona, tak, aby dane dwa elementy, można ustalić czy są równoważne (w tym sensie, że nie jest mniejsza niż drugi) albo że jeden jest mniejsza niż innych. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Gdy w obu zakresów źródła równoważny elementów, elementy w zakresie pierwszy poprzedzać elementy z drugiego zakresu źródła w zakresie docelowym. Jeśli zakresów zawierać duplikatów elementu, zakres docelowy będzie zawierał maksymalną liczbę tych elementów, które występują w obu zakresów źródła.  
  
 Złożoność algorytm jest liniowa z maksymalnie 2 \* (( *Nazwisko1 - first1*)-( *Nazwisko2 - first2*)) - 1 porównania.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_set_union.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // For greater<int>( )  
#include <iostream>  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser ( int elem1, int elem2 )  
{  
   if ( elem1 < 0 )   
      elem1 = - elem1;  
   if ( elem2 < 0 )   
      elem2 = - elem2;  
   return elem1 < elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1a, v1b, v1 ( 12 );  
   vector <int>::iterator Iter1a, Iter1b, Iter1, Result1;  
  
   // Constructing vectors v1a & v1b with default less than ordering  
   int i;  
   for ( i = -1 ; i <= 3 ; i++ )  
   {  
      v1a.push_back(  i );  
   }  
  
   int ii;  
   for ( ii =-3 ; ii <= 1 ; ii++ )  
   {  
      v1b.push_back(  ii  );  
   }  
  
   cout << "Original vector v1a with range sorted by the\n "  
        <<  "binary predicate less than is  v1a = ( " ;  
   for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )  
      cout << *Iter1a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v1b with range sorted by the\n "  
        <<  "binary predicate less than is  v1b = ( " ;  
   for ( Iter1b = v1b.begin ( ) ; Iter1b != v1b.end ( ) ; Iter1b++ )  
      cout << *Iter1b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v2a & v2b with ranges sorted by greater  
   vector <int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );  
   vector <int>::iterator Iter2a,  Iter2b, Iter2, Result2;  
   sort ( v2a.begin ( ) , v2a.end ( ) , greater<int> ( ) );  
   sort ( v2b.begin ( ) , v2b.end ( ) , greater<int> ( ) );  
  
   cout << "Original vector v2a with range sorted by the\n "  
        <<  "binary predicate greater is   v2a =  ( " ;  
   for ( Iter2a = v2a.begin ( ) ; Iter2a != v2a.end ( ) ; Iter2a++ )  
      cout << *Iter2a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v2b with range sorted by the\n "  
        <<  "binary predicate greater is   v2b =  ( " ;  
   for ( Iter2b = v2b.begin ( ) ; Iter2b != v2b.end ( ) ; Iter2b++ )  
      cout << *Iter2b << " ";  
   cout << ")." << endl;  
  
   // Constructing vectors v3a & v3b with ranges sorted by mod_lesser  
   vector <int> v3a ( v1a ), v3b ( v1b ) ,  v3 ( v1 );  
   vector <int>::iterator Iter3a, Iter3b, Iter3, Result3;  
   sort ( v3a.begin ( ) , v3a.end ( ) , mod_lesser );  
   sort ( v3b.begin ( ) , v3b.end ( ) , mod_lesser  );  
  
   cout << "Original vector v3a with range sorted by the\n "  
        <<  "binary predicate mod_lesser is   v3a =  ( " ;  
   for ( Iter3a = v3a.begin ( ) ; Iter3a != v3a.end ( ) ; Iter3a++ )  
      cout << *Iter3a << " ";  
   cout << ")." << endl;  
  
   cout << "Original vector v3b with range sorted by the\n "  
        <<  "binary predicate mod_lesser is   v3b =  ( " ;  
   for ( Iter3b = v3b.begin ( ) ; Iter3b != v3b.end ( ) ; Iter3b++ )  
      cout << *Iter3b << " ";  
   cout << ")." << endl;  
  
   // To combine into a union in ascending order with the default   
    // binary predicate less <int> ( )  
   Result1 = set_union ( v1a.begin ( ) , v1a.end ( ) ,  
      v1b.begin ( ) , v1b.end ( ) , v1.begin ( ) );  
   cout << "Union of source ranges with default order,"  
        << "\n vector v1mod =  ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // To combine into a union in descending order, specify binary   
   // predicate greater<int>( )  
   Result2 = set_union (  v2a.begin ( ) , v2a.end ( ) ,  
      v2b.begin ( ) , v2b.end ( ) ,v2.begin ( ) , greater <int> ( ) );  
   cout << "Union of source ranges with binary predicate greater "  
        << "specified,\n vector v2mod  = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   // To combine into a union applying a user-defined  
   // binary predicate mod_lesser  
   Result3 = set_union ( v3a.begin ( ) , v3a.end ( ) ,  
      v3b.begin ( ) , v3b.end ( ) , v3.begin ( ) , mod_lesser );  
   cout << "Union of source ranges with binary predicate "  
        << "mod_lesser specified,\n vector v3mod  = ( " ; ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="shuffle"></a>  STD::shuffle  
 Elementy przesuwa (Reorganizuje) dla określonego zakresu przy użyciu generator liczb losowych.  
  
```  
template<class RandomAccessIterator, class UniformRandomNumberGenerator>  
void shuffle(RandomAccessIterator first,  
    RandomAccessIterator last,  
    UniformRandomNumberGenerator&& gen);  
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Iteratora do pierwszego elementu w zakresie przesuniętą, włącznie. Musi spełniać wymagania `RandomAccessIterator` i `ValueSwappable`.  
  
 `last`  
 Iterator do ostatniego elementu w zakresie przesuniętą, wyłącznego. Musi spełniać wymagania `RandomAccessIterator` i `ValueSwappable`.  
  
 `gen`  
 Generatora liczb losowych który `shuffle()` użyje funkcji dla tej operacji. Musi spełniać wymagania `UniformRandomNumberGenerator`.  
  
### <a name="remarks"></a>Uwagi  
 Więcej informacji oraz przykładowy kod, który używa `shuffle()`, zobacz [ \<losowe >](../standard-library/random.md).  
  
##  <a name="sort"></a>  Sortowanie  
 Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryteriów sortowania określonych przez binarny predykat.  
  
```  
template<class RandomAccessIterator>  
   void sort(  
      RandomAccessIterator first,   
      RandomAccessIterator last);
  
template<class RandomAccessIterator, class Predicate>  
   void sort(  
      RandomAccessIterator first,   
      RandomAccessIterator last,   
      Predicate comp);
  
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Dostęp losowy iteratora adresowania położenie pierwszego elementu w zakresie ma zostać posortowana.  
  
 `last`  
 Dostęp losowy iteratora adresowania poza ostatniego elementu w zakresie pozycji, co ma zostać posortowana.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje kryterium porównania muszą być spełnione przez kolejnych elementów w kolejności. Przyjmuje dwa argumenty i zwraca ten binarne predykatu `true` przypadku dwa argumenty w kolejności i `false` inaczej. Ta funkcja komparatora musi nakładają strict słabe porządkowanie dla pary elementów z sekwencji. Aby uzyskać więcej informacji, zobacz [algorytmy](../standard-library/algorithms.md).  
  
### <a name="remarks"></a>Uwagi  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Elementy są równoważne, ale niekoniecznie równości, jeśli nie jest mniejsza niż innych. `sort` Algorytmu nie jest trwały i dlatego nie gwarantuje, że zostaną zachowane względne uporządkowanie równoważne elementów. Algorytm `stable_sort` zachować oryginalne porządkowania.  
  
 Średnia złożoności sortowania jest *O*( *N* dziennika *N*), gdzie *N* =  *ostatnich — pierwszy*.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_sort.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // For greater<int>( )  
#include <iostream>  
  
// Return whether first element is greater than the second  
bool UDgreater ( int elem1, int elem2 )  
{  
   return elem1 > elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 2 * i );  
   }  
  
   int ii;  
   for ( ii = 0 ; ii <= 5 ; ii++ )  
   {  
      v1.push_back( 2 * ii + 1 );  
   }  
  
   cout << "Original vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   sort( v1.begin( ), v1.end( ) );  
   cout << "Sorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in descending order. specify binary predicate  
   sort( v1.begin( ), v1.end( ), greater<int>( ) );  
   cout << "Resorted (greater) vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // A user-defined (UD) binary predicate can also be used  
   sort( v1.begin( ), v1.end( ), UDgreater );  
   cout << "Resorted (UDgreater) vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
```Output  
Original vector v1 = ( 0 2 4 6 8 10 1 3 5 7 9 11 )  
Sorted vector v1 = ( 0 1 2 3 4 5 6 7 8 9 10 11 )  
Resorted (greater) vector v1 = ( 11 10 9 8 7 6 5 4 3 2 1 0 )  
Resorted (UDgreater) vector v1 = ( 11 10 9 8 7 6 5 4 3 2 1 0 )  
```  
  
##  <a name="sort_heap"></a>  sort_heap —  
 Konwertuje stertę na sortowany zakres.  
  
```  
template<class RandomAccessIterator>  
   void sort_heap(  
      RandomAccessIterator first,   
      RandomAccessIterator last);
  
template<class RandomAccessIterator, class Predicate>  
   void sort_heap(  
      RandomAccessIterator first,   
      RandomAccessIterator last,  
      Predicate comp);  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterator dostępie swobodnym, adresowania położenie pierwszego elementu w stercie docelowej.  
  
 `last`  
 Iterator dostępie swobodnym, adresowania jedną pozycję poza ostatniego elementu w stosie docelowej.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje znaczeniu, w której jeden element jest mniejsza niż innym. Predykat binarne przyjmuje dwa argumenty i zwraca **true** po spełnieniu i **false** gdy nie są spełnione.  
  
### <a name="remarks"></a>Uwagi  
 Stosów ma dwie właściwości:  
  
-   Pierwszy element zawsze jest największy.  
  
-   Elementy może dodać lub usunąć w czasie logarytmicznych.  
  
 Po zastosowaniu Jeśli ten algorytm, zakres została zastosowana do nie jest już stosu.  
  
 Nie jest stabilna sortowania, ponieważ względną kolejność elementów równoważne niekoniecznie nie są zachowywane.  
  
 Stosów są idealne sposób implementowania priorytet kolejek i ich użycia w implementacji karty kontenera standardowa biblioteka C++ [priority_queue — klasa](../standard-library/priority-queue-class.md).  
  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Złożoność jest najwyżej *N* dziennika *N*, gdzie *N* = ( *ostatni — najpierw*).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_sort_heap.cpp  
// compile with: /EHsc  
#include <algorithm>  
#include <functional>  
#include <iostream>  
#include <ostream>  
#include <string>  
#include <vector>  
using namespace std;  
  
void print(const string& s, const vector<int>& v) {  
    cout << s << ": ( ";  
  
    for (auto i = v.begin(); i != v.end(); ++i) {  
        cout << *i << " ";  
    }  
  
    cout << ")" << endl;  
}  
  
int main() {  
    vector<int> v;  
    for (int i = 1; i <= 9; ++i) {  
        v.push_back(i);  
    }  
    print("Initially", v);  
  
    random_shuffle(v.begin(), v.end());  
    print("After random_shuffle", v);  
  
    make_heap(v.begin(), v.end());  
    print("     After make_heap", v);  
  
    sort_heap(v.begin(), v.end());  
    print("     After sort_heap", v);  
  
    random_shuffle(v.begin(), v.end());  
    print("             After random_shuffle", v);  
  
    make_heap(v.begin(), v.end(), greater<int>());  
    print("After make_heap with greater<int>", v);  
  
    sort_heap(v.begin(), v.end(), greater<int>());  
    print("After sort_heap with greater<int>", v);  
}  
```  
  
##  <a name="stable_partition"></a>  stable_partition —  
 Klasyfikuje elementy w zakresie na dwa rozłączne zestawy, z elementami spełniającymi predykat unarny poprzedzającymi te, które go nie spełniają, zachowując względną kolejność elementów równoważnych.  
  
```  
template<class BidirectionalIterator, class Predicate>  
BidirectionalIterator stable_partition(  
    BidirectionalIterator first,  
    BidirectionalIterator last,  
    Predicate pred );  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Dwukierunkowy iteratora adresowania położenie pierwszego elementu w zakresie do partycjonowania.  
  
 `last`  
 Dwukierunkowy iteratora adresowania jedną pozycję poza ostatniego elementu w zakresie do partycjonowania.  
  
 `_Pred`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje warunek muszą być spełnione, jeśli element ma być klasyfikowane. Predykat przyjmuje jeden argument i zwraca **true** lub **false**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dwukierunkowy iteratora adresowania położenie pierwszego elementu w zakresie do spełnia warunek predykatu.  
  
### <a name="remarks"></a>Uwagi  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Elementy *a* i *b* są równoważne, ale nie musi być równa, jeśli obie *Pr* ( *a*, *b*) ma wartość false i *Pr* ( *b*, *a*) w przypadku wartości FAŁSZ, gdy *Pr* jest określony parametr predykatu. **Partycji stable_** algorytm jest stabilna i gwarantuje, że zostaną zachowane względne uporządkowanie równoważne elementów. Algorytm **partycji** jest niekoniecznie Zachowaj oryginalne porządkowania.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_stable_partition.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
bool greater5 ( int value ) {  
   return value >5;  
}  
  
int main( ) {  
   using namespace std;  
   vector <int> v1, v2;  
   vector <int>::iterator Iter1, Iter2, result;  
  
   int i;  
   for ( i = 0 ; i <= 10 ; i++ )  
      v1.push_back( i );  
  
   int ii;  
   for ( ii = 0 ; ii <= 4 ; ii++ )  
      v1.push_back( 5 );  
  
   random_shuffle(v1.begin( ), v1.end( ) );  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Partition the range with predicate greater10  
   result = stable_partition (v1.begin( ), v1.end( ), greater5 );  
   cout << "The partitioned set of elements in v1 is:\n ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   cout << "The first element in v1 to fail to satisfy the"  
        << "\n predicate greater5 is: " << *result << "." << endl;  
}  
```  
  
##  <a name="stable_sort"></a>  stable_sort —  
 Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryterium sortowania określonego przez binarny predykat i zachowuje względną kolejność elementów równoważnych.  
  
```  
template<class BidirectionalIterator>  
 void stable_sort( BidirectionalIterator first, BidirectionalIterator last );  
  
template<class BidirectionalIterator, class BinaryPredicate>  
void stable_sort(   
    BidirectionalIterator first,  
    BidirectionalIterator last,   
    BinaryPredicate comp );  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Dwukierunkowy iteratora adresowania położenie pierwszego elementu w zakresie ma zostać posortowana.  
  
 `last`  
 Dwukierunkowy iteratora adresowania poza ostatniego elementu w zakresie pozycji, co ma zostać posortowana.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje kryterium porównania muszą być spełnione przez kolejnych elementów w kolejności. Predykat binarne przyjmuje dwa argumenty i zwraca **true** po spełnieniu i **false** gdy nie są spełnione.  
  
### <a name="remarks"></a>Uwagi  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Elementy są równoważne, ale niekoniecznie równości, jeśli nie jest mniejsza niż innych. **Sortowania** algorytm jest stabilna i gwarantuje, że zostaną zachowane względne uporządkowanie równoważne elementów.  
  
 Złożoność środowiska wykonawczego `stable_sort` zależy od ilości dostępnej pamięci, ale jest najlepszym przypadku (podane wystarczającą ilość pamięci) *O*( *N* dziennika *N*) i najgorszego jest *O*( *N* (dziennika *N* ) 2), gdzie *N* =  *ostatni — najpierw.* Zazwyczaj **sortowania** algorytm jest znacznie szybsze niż `stable_sort`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_stable_sort.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // For greater<int>( )  
#include <iostream>  
  
// Return whether first element is greater than the second  
bool UDgreater (int elem1, int elem2 )  
{  
   return elem1 > elem2;  
}  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 2 * i );  
   }  
  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 2 * i  );  
   }  
  
   cout << "Original vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   stable_sort(v1.begin( ), v1.end( ) );  
   cout << "Sorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in descending order, specify binary predicate  
   stable_sort(v1.begin( ), v1.end( ), greater<int>( ) );  
   cout << "Resorted (greater) vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // A user-defined (UD) binary predicate can also be used  
   stable_sort(v1.begin( ), v1.end( ), UDgreater );  
   cout << "Resorted (UDgreater) vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
```Output  
Original vector v1 = ( 0 2 4 6 8 10 0 2 4 6 8 10 )  
Sorted vector v1 = ( 0 0 2 2 4 4 6 6 8 8 10 10 )  
Resorted (greater) vector v1 = ( 10 10 8 8 6 6 4 4 2 2 0 0 )  
Resorted (UDgreater) vector v1 = ( 10 10 8 8 6 6 4 4 2 2 0 0 )  
```  
  
##  <a name="swap"></a>  Swap  
 Pierwszy zastępowanie zamienia wartości dwa obiekty. Drugi zastępowanie zamienia wartości między dwiema tablicami obiektów.  
  
```  
template<class Type>  
   void swap(  
      Type& left,   
      Type& right);  
template<class Type, size_t N>  
   void swap(  
      Type (& left)[N],  
      Type (& right)[N]);\r
  
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Dla pierwszego zastąpienia pierwszy obiekt ma zawartością wymieniane. Dla drugiego zastąpienia pierwszy tablicę obiektów, aby jego zawartość wymieniane.  
  
 `right`  
 Dla pierwszego zastąpienia drugi obiekt, aby jego zawartość wymieniane. Dla drugiego zastąpienia drugi tablicę obiektów, aby jego zawartość wymieniane.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy przeciążenia jest przeznaczony do działania na pojedyncze obiekty. Drugi przeciążenia zamienia zawartość obiektów między dwiema tablicami.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_swap.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   vector <int> v1, v2;  
   vector <int>::iterator Iter1, Iter2, result;  
  
   for ( int i = 0 ; i <= 10 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   for ( int ii = 0 ; ii <= 4 ; ii++ )  
   {  
      v2.push_back( 5 );  
   }  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   cout << "Vector v2 is ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   swap( v1, v2 );  
  
   cout << "Vector v1 is ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   cout << "Vector v2 is ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
Vector v1 is ( 0 1 2 3 4 5 6 7 8 9 10 ).  
Vector v2 is ( 5 5 5 5 5 ).  
Vector v1 is ( 5 5 5 5 5 ).  
Vector v2 is ( 0 1 2 3 4 5 6 7 8 9 10 ).  
```  
  
##  <a name="swap_ranges"></a>  swap_ranges —  
 Zamienia elementy jednego zakresu przez elementy innego zakresu, zakresy mają równe wielkości.  
  
```  
template<class ForwardIterator1, class ForwardIterator2>  
ForwardIterator2 swap_ranges(   
   ForwardIterator1 first1,  
   ForwardIterator1 last1,  
   ForwardIterator2 first2 );  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first1`  
 Wskazuje pierwszą pozycję pierwszego zakresu, w której elementy mają być przekazywane do przodu iteratora.  
  
 `last1`  
 Wskazuje poza końcowego położenie pierwszego zakresu, w której elementy mają być przekazywane do przodu iteratora.  
  
  `first2`  
 Wskazuje pierwszą pozycję drugiego zakresu, w której elementy mają być przekazywane do przodu iteratora.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskazuje poza końcowym pozycję drugiego zakresu, w których elementy mają być wymieniane do przodu iteratora.  
  
### <a name="remarks"></a>Uwagi  
 Zakresy odwołania musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w ramach każdej sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać. Drugi zakres musi być większy niż pierwszy zakres.  
  
 Złożoność jest liniowa z `last1`  -   `first1` zamiany wykonywane. Jeśli elementy z kontenerów tego samego typu są wymieniane, ich `swap` elementu członkowskiego z tego kontenera należy użyć funkcji, ponieważ funkcja członkowska zwykle ma stałą złożoności.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_swap_ranges.cpp  
// compile with: /EHsc  
#include <vector>  
#include <deque>  
#include <algorithm>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   vector <int> v1;  
   deque <int> d1;  
   vector <int>::iterator v1Iter1;  
   deque<int>::iterator d1Iter1;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   int ii;  
   for ( ii =4 ; ii <= 9 ; ii++ )  
   {  
      d1.push_back( 6 );  
   }  
  
   cout << "Vector v1 is ( " ;  
   for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )  
      cout << *v1Iter1  << " ";  
   cout << ")." << endl;  
  
   cout << "Deque d1 is  ( " ;  
   for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )  
      cout << *d1Iter1  << " ";  
   cout << ")." << endl;  
  
   swap_ranges ( v1.begin ( ) , v1.end ( ) , d1.begin ( ) );  
  
   cout << "After the swap_range, vector v1 is ( " ;  
   for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )  
      cout << *v1Iter1 << " ";  
   cout << ")." << endl;  
  
   cout << "After the swap_range deque d1 is   ( " ;  
   for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )  
      cout << *d1Iter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
Vector v1 is ( 0 1 2 3 4 5 ).  
Deque d1 is  ( 6 6 6 6 6 6 ).  
After the swap_range, vector v1 is ( 6 6 6 6 6 6 ).  
After the swap_range deque d1 is   ( 0 1 2 3 4 5 ).  
```  
  
##  <a name="transform"></a>  Przekształcenia  
 Stosuje określony obiekt funkcji dla każdego elementu w zakresie sortowania lub dla pary elementów z dwóch zakresów sortowania i kopiuje zwracane wartości obiektu funkcji do zakresu docelowego.  
  
```  
 template<class InputIterator, class OutputIterator, class UnaryFunction>  
 OutputIterator transform(  
    InputIterator first1,  
    InputIterator last1,  
    OutputIterator result,  
    UnaryFunction _Func );  
  
template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryFunction>  
OutputIterator transform(   
    InputIterator1 first1,  
    InputIterator1 last1,  
    InputIterator2 first2,  
    OutputIterator result,  
    BinaryFunction _Func );  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first1`  
 Adresowanie położenie pierwszego elementu w zakresie pierwszego źródła działały na iteratora wejściowego.  
  
 `last1`  
 Wejściowy iteratora adresowania jedną pozycję poza ostatniego elementu w zakresie pierwszego źródła zasilaniu.  
  
  `first2`  
 Adresowanie położenie pierwszego elementu w zakresie drugiego źródła działały na iteratora wejściowego.  
  
 `result`  
 Dane wyjściowe iteratora adresowania położenie pierwszego elementu w zakresie docelowym.  
  
 `_Func`  
 Jednoargumentowy zdefiniowane przez użytkownika funkcji obiektu używane w pierwszej wersji algorytm jest stosowane do każdego elementu w zakresie pierwszego źródła lub zdefiniowanej przez użytkownika (UD) binarne funkcji używane w drugiej wersji algorytmu parowania, stosowany w kolejności do przodu , aby dwóch zakresów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dane wyjściowe iteratora adresowania jedną pozycję poza ostatniego elementu w zakresie docelowym, który otrzymuje przekształcenia przez obiekt funkcji elementy danych wyjściowych.  
  
### <a name="remarks"></a>Uwagi  
 Zakresy odwołania musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w ramach każdej sekwencji ostatniej pozycji musi być dostępny z pierwszego przez przyrostowo zmieniać. Zakres docelowy musi być wystarczająco duży, aby zawiera zakresu przekształcone źródła.  
  
 Jeśli `result` jest równe `first1` w pierwszej wersji algorytmu, następnie zakresy źródłowego i docelowego będzie taka sama i sekwencja zostaną zmodyfikowane w miejscu. Ale `result` nie może kierować pozycji z zakresu [`first1` + 1, `last1`).  
  
 Złożoność jest liniowa z co najwyżej (`last1` -  `first1`) porównania.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_transform.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
// The function object multiplies an element by a Factor  
template <class Type>  
class MultValue  
{  
   private:  
      Type Factor;   // The value to multiply by  
   public:  
      // Constructor initializes the value to multiply by  
      MultValue ( const Type& val ) : Factor ( val ) {  
      }  
  
      // The function call for the element to be multiplied  
      Type operator ( ) ( Type& elem ) const   
      {  
         return elem * Factor;  
      }  
};  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1, v2 ( 7 ), v3 ( 7 );  
   vector <int>::iterator Iter1, Iter2 , Iter3;  
  
   // Constructing vector v1  
   int i;  
   for ( i = -4 ; i <= 2 ; i++ )  
   {  
      v1.push_back(  i );  
   }  
  
   cout << "Original vector  v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Modifying the vector v1 in place  
   transform (v1.begin ( ) , v1.end ( ) , v1.begin ( ) , MultValue<int> ( 2 ) );  
   cout << "The elements of the vector v1 multiplied by 2 in place gives:"  
        << "\n v1mod = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")." << endl;  
  
   // Using transform to multiply each element by a factor of 5  
   transform ( v1.begin ( ) , v1.end ( ) , v2.begin ( ) , MultValue<int> ( 5 ) );  
  
   cout << "Multiplying the elements of the vector v1mod\n "  
        <<  "by the factor 5 & copying to v2 gives:\n v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")." << endl;  
  
   // The second version of transform used to multiply the   
   // elements of the vectors v1mod & v2 pairwise  
   transform ( v1.begin ( ) , v1.end ( ) ,  v2.begin ( ) , v3.begin ( ) ,   
      multiplies <int> ( ) );  
  
   cout << "Multiplying elements of the vectors v1mod and v2 pairwise "  
        <<  "gives:\n v3 = ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
Original vector  v1 = ( -4 -3 -2 -1 0 1 2 ).  
The elements of the vector v1 multiplied by 2 in place gives:  
 v1mod = ( -8 -6 -4 -2 0 2 4 ).  
Multiplying the elements of the vector v1mod  
 by the factor 5 & copying to v2 gives:  
 v2 = ( -40 -30 -20 -10 0 10 20 ).  
Multiplying elements of the vectors v1mod and v2 pairwise gives:  
 v3 = ( 320 180 80 20 0 20 80 ).  
```  
  
##  <a name="unique"></a>  Unikatowe  
 Usuwa zduplikowane elementy, które sąsiadują ze sobą w określonym zakresie.  
  
```  
template<class ForwardIterator>  
   ForwardIterator unique(  
      ForwardIterator first,   
      ForwardIterator last);
  
template<class ForwardIterator, class Predicate>  
   ForwardIterator unique(  
      ForwardIterator first,   
      ForwardIterator last,  
      Predicate comp);
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Do przodu iteratora adresowania położenie pierwszego elementu w zakresie dla usuwania duplikatów.  
  
 `last`  
 Do przodu iteratora adresowania pozycji w jednym ostatniego elementu w zakresie dla usuwania duplikatów.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje warunek muszą być spełnione, jeśli dwa elementy mają zostać pobrane jako równoważne. Predykat binarne przyjmuje dwa argumenty i zwraca **true** po spełnieniu i **false** gdy nie są spełnione.  
  
### <a name="return-value"></a>Wartość zwracana  
 Do przodu iteratora nowy koniec sekwencji zmodyfikowane, która nie zawiera następujących po sobie duplikatów, adresowania pozycji w jednym ostatni element nie został usunięty.  
  
### <a name="remarks"></a>Uwagi  
 Oba rodzaje algorytm Usuń duplikat drugi pary kolejnych elementów takie same.  
  
 Operacji algorytm jest stabilna, dzięki czemu względną kolejność elementów cofnąć usunięcia nie ulega zmianie.  
  
 Odwołanie do zakresu musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w obrębie sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać. Liczba elementów w sekwencji on nie ulega zmianie przez algorytm **unikatowy** i elementy poza koniec sekwencji zmodyfikowane są dereferenceable, ale nie został określony.  
  
 Złożoność jest liniowa, wymagających ( `last`  -   `first`) - 1 porównania.  
  
 Lista zawiera bardziej wydajne element członkowski funkcji "unique", które mogą działać lepiej.  
  
 Nie można używać tych algorytmów asocjacyjnej kontenera.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_unique.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
#include <ostream>  
  
using namespace std;  
  
// Return whether modulus of elem1 is equal to modulus of elem2  
bool mod_equal ( int elem1, int elem2 )  
{  
   if ( elem1 < 0 )   
      elem1 = - elem1;  
   if ( elem2 < 0 )   
      elem2 = - elem2;  
   return elem1 == elem2;  
};  
  
int main( )  
{  
   vector <int> v1;  
   vector <int>::iterator v1_Iter1, v1_Iter2, v1_Iter3,  
         v1_NewEnd1, v1_NewEnd2, v1_NewEnd3;  
  
   int i;  
   for ( i = 0 ; i <= 3 ; i++ )  
   {  
      v1.push_back( 5 );  
      v1.push_back( -5 );  
   }  
  
   int ii;  
   for ( ii = 0 ; ii <= 3 ; ii++ )  
   {  
      v1.push_back( 4 );  
   }  
   v1.push_back( 7 );  
  
   cout << "Vector v1 is ( " ;  
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1.end( ) ; v1_Iter1++ )  
      cout << *v1_Iter1 << " ";  
   cout << ")." << endl;  
  
   // Remove consecutive duplicates  
   v1_NewEnd1 = unique ( v1.begin ( ) , v1.end ( ) );  
  
   cout << "Removing adjacent duplicates from vector v1 gives\n ( " ;  
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )  
      cout << *v1_Iter1 << " ";  
   cout << ")." << endl;  
  
   // Remove consecutive duplicates under the binary prediate mod_equals  
   v1_NewEnd2 = unique ( v1.begin ( ) , v1_NewEnd1 , mod_equal );  
  
   cout << "Removing adjacent duplicates from vector v1 under the\n "  
        << " binary predicate mod_equal gives\n ( " ;  
   for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )  
      cout << *v1_Iter2 << " ";  
   cout << ")." << endl;  
  
   // Remove elements if preceded by an element that was greater  
   v1_NewEnd3 = unique ( v1.begin ( ) , v1_NewEnd2, greater<int>( ) );  
  
   cout << "Removing adjacent elements satisfying the binary\n "  
        << " predicate mod_equal from vector v1 gives ( " ;  
   for ( v1_Iter3 = v1.begin( ) ; v1_Iter3 != v1_NewEnd3 ; v1_Iter3++ )  
      cout << *v1_Iter3 << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
Vector v1 is ( 5 -5 5 -5 5 -5 5 -5 4 4 4 4 7 ).  
Removing adjacent duplicates from vector v1 gives  
 ( 5 -5 5 -5 5 -5 5 -5 4 7 ).  
Removing adjacent duplicates from vector v1 under the  
  binary predicate mod_equal gives  
 ( 5 4 7 ).  
Removing adjacent elements satisfying the binary  
  predicate mod_equal from vector v1 gives ( 5 7 ).  
```  
  
##  <a name="unique_copy"></a>  unique_copy —  
 Kopiuje elementy z zakresu źródłowego do zakresu docelowego z wyjątkiem zduplikowanych elementów, które ze sobą sąsiadują.  
  
```  
 template<class InputIterator, class OutputIterator>  
 OutputIterator unique_copy( InputIterator first,  
    InputIterator last,  
    OutputIterator result );  
  
template<class InputIterator, class OutputIterator, class BinaryPredicate>  
OutputIterator unique_copy( InputIterator first,  
    InputIterator last,  
    OutputIterator result,  
    BinaryPredicate comp );  
  
```  
  
### <a name="parameters"></a>Parametry  
  `first`  
 Iterator do przodu adresowania położenie pierwszego elementu w zakresie od źródła do skopiowania.  
  
 `last`  
 Iterator do przodu adresowania jedną pozycję poza ostatniego elementu w zakresie od źródła do skopiowania.  
  
 `result`  
 Iteratora dane wyjściowe adresowania położenie pierwszego elementu w zakresie docelowym, który otrzymuje kopiowania z kolejnych duplikaty są usuwane.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje warunek muszą być spełnione, jeśli dwa elementy mają zostać pobrane jako równoważne. Predykat binarne przyjmuje dwa argumenty i zwraca **true** po spełnieniu i **false** gdy nie są spełnione.  
  
### <a name="return-value"></a>Wartość zwracana  
 Usunięte adresowania jedną pozycję poza ostatniego elementu w zakresie docelowym, który otrzymuje kopiowania z kolejnych duplikaty iteratora danych wyjściowych.  
  
### <a name="remarks"></a>Uwagi  
 Oba rodzaje algorytm Usuń duplikat drugi pary kolejnych elementów takie same.  
  
 Operacji algorytm jest stabilna, dzięki czemu względną kolejność elementów cofnąć usunięcia nie ulega zmianie.  
  
 Zakresy odwołania musi być prawidłowym; wszystkie wskaźniki musi być dereferenceable i w sekwencji ostatniej pozycji jest dostępny od pierwszego przez przyrostowo zmieniać.  
  
 Złożoność jest liniowa, wymagających ( `last`  -   `first`) porównania.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_unique_copy.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
#include <ostream>  
  
using namespace std;  
  
// Return whether modulus of elem1 is equal to modulus of elem2  
bool mod_equal ( int elem1, int elem2 ) {  
   if ( elem1 < 0 )   
      elem1 = - elem1;  
   if ( elem2 < 0 )   
      elem2 = - elem2;  
   return elem1 == elem2;  
};  
  
int main() {  
   vector <int> v1;  
   vector <int>::iterator v1_Iter1, v1_Iter2,  
         v1_NewEnd1, v1_NewEnd2;  
  
   int i;  
   for ( i = 0 ; i <= 1 ; i++ ) {  
      v1.push_back( 5 );  
      v1.push_back( -5 );  
   }  
  
   int ii;  
   for ( ii = 0 ; ii <= 2 ; ii++ )  
      v1.push_back( 4 );  
   v1.push_back( 7 );  
  
   int iii;  
   for ( iii = 0 ; iii <= 5 ; iii++ )  
      v1.push_back( 10 );  
  
   cout << "Vector v1 is\n ( " ;  
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1.end( ) ; v1_Iter1++ )  
      cout << *v1_Iter1 << " ";  
   cout << ")." << endl;  
  
   // Copy first half to second, removing consecutive duplicates  
   v1_NewEnd1 = unique_copy ( v1.begin ( ) , v1.begin ( ) + 8, v1.begin ( ) + 8 );  
  
   cout << "Copying the first half of the vector to the second half\n "  
        << "while removing adjacent duplicates gives\n ( " ;  
   for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )  
      cout << *v1_Iter1 << " ";  
   cout << ")." << endl;  
  
   int iv;  
   for ( iv = 0 ; iv <= 7 ; iv++ )  
      v1.push_back( 10 );  
  
   // Remove consecutive duplicates under the binary prediate mod_equals  
   v1_NewEnd2 = unique_copy ( v1.begin ( ) , v1.begin ( ) + 14,   
      v1.begin ( ) + 14 , mod_equal );  
  
   cout << "Copying the first half of the vector to the second half\n "  
        << " removing adjacent duplicates under mod_equals gives\n ( " ;  
   for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )  
      cout << *v1_Iter2 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="upper_bound"></a>  upper_bound  
 Znajduje pozycję pierwszego elementu w uporządkowanym zakresie, który ma wartość większą niż określona wartość, gdzie kryterium sortowania może być określone przez predykat binarny.  
  
```  
template<class ForwardIterator, class Type>  
   ForwardIterator upper_bound(  
      ForwardIterator first,   
      ForwardIterator last,  
      const Type& value);
  
template<class ForwardIterator, class Type, class Predicate>  
   ForwardIterator upper_bound(  
      ForwardIterator first,   
      ForwardIterator last,  
      const Type& value,  
      Predicate comp);
  
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Pozycja pierwszego elementu w zakresie do wyszukania.  
  
 `last`  
 Pozycja jedną poza ostatniego elementu w zakresie do wyszukania.  
  
 `value`  
 Wartość w zakresie uporządkowanej wymagające może przekroczyć wartość elementu dotyczy iteratora zwracane.  
  
 `comp`  
 Zdefiniowane przez użytkownika funkcja predykatu obiektu, który definiuje znaczeniu, w której jeden element jest mniejsza niż innym. Predykat binarne przyjmuje dwa argumenty i zwraca **true** po spełnieniu i **false** gdy nie są spełnione.  
  
### <a name="return-value"></a>Wartość zwracana  
 Do przodu iteratora położenie pierwszego elementu, który ma wartość większą niż określona wartość.  
  
### <a name="remarks"></a>Uwagi  
 Zakres źródła posortowane odwołuje się do musi być prawidłowym; Iteratory wszystkie muszą być dereferenceable i w obrębie sekwencji ostatniej pozycji musi być dostępny z pierwszego przez przyrostowo zmieniać.  
  
 Posortowane zakres jest warunkiem wstępnym stosowania `upper_bound` i gdzie kryterium porządkowania jest taki sam jak określony przez predykat binarnego.  
  
 Zakres nie jest modyfikowany przez `upper_bound`.  
  
 Typy wartości iteratorów do przodu musi być mniejsza-niż porównywalne może zostać określona, tak, aby dane dwa elementy, można ustalić czy są równoważne (w tym sensie, że nie jest mniejsza niż drugi) albo że jeden jest mniejsza niż innych. Powoduje to kolejność między elementami nonequivalent  
  
 Złożoność algorytm jest logarytmiczna dla Iteratory dostęp losowy i liniowej, w przeciwnym razie wartość o liczbie kroków proporcjonalny do ( `last - first`).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// alg_upper_bound.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>      // greater<int>( )  
#include <iostream>  
  
// Return whether modulus of elem1 is less than modulus of elem2  
bool mod_lesser( int elem1, int elem2 )  
{  
    if ( elem1 < 0 )  
        elem1 = - elem1;  
    if ( elem2 < 0 )  
        elem2 = - elem2;  
    return elem1 < elem2;  
}  
  
int main( )  
{  
    using namespace std;  
  
    vector<int> v1;  
    // Constructing vector v1 with default less-than ordering  
    for ( auto i = -1 ; i <= 4 ; ++i )  
    {  
        v1.push_back(  i );  
    }  
  
    for ( auto ii =-3 ; ii <= 0 ; ++ii )  
    {  
        v1.push_back(  ii  );  
    }  
  
    cout << "Starting vector v1 = ( " ;  
    for (const auto &Iter : v1)  
        cout << Iter << " ";  
    cout << ")." << endl;  
  
    sort(v1.begin(), v1.end());  
    cout << "Original vector v1 with range sorted by the\n "  
        << "binary predicate less than is v1 = ( " ;  
    for (const auto &Iter : v1)  
        cout << Iter << " ";  
    cout << ")." << endl;  
  
    // Constructing vector v2 with range sorted by greater  
    vector<int> v2(v1);  
  
    sort(v2.begin(), v2.end(), greater<int>());  
  
    cout << "Original vector v2 with range sorted by the\n "  
        << "binary predicate greater is v2 = ( " ;  
    for (const auto &Iter : v2)  
        cout << Iter << " ";  
    cout << ")." << endl;  
  
    // Constructing vectors v3 with range sorted by mod_lesser  
    vector<int> v3(v1);  
    sort(v3.begin(), v3.end(), mod_lesser);  
  
    cout << "Original vector v3 with range sorted by the\n "  
        <<  "binary predicate mod_lesser is v3 = ( " ;  
    for (const auto &Iter : v3)  
        cout << Iter << " ";  
    cout << ")." << endl;  
  
    // Demonstrate upper_bound  
  
    vector<int>::iterator Result;  
  
    // upper_bound of 3 in v1 with default binary predicate less<int>()  
    Result = upper_bound(v1.begin(), v1.end(), 3);  
    cout << "The upper_bound in v1 for the element with a value of 3 is: "  
        << *Result << "." << endl;  
  
    // upper_bound of 3 in v2 with the binary predicate greater<int>( )  
    Result = upper_bound(v2.begin(), v2.end(), 3, greater<int>());  
    cout << "The upper_bound in v2 for the element with a value of 3 is: "  
        << *Result << "." << endl;  
  
    // upper_bound of 3 in v3 with the binary predicate  mod_lesser  
    Result = upper_bound(v3.begin(), v3.end(), 3,  mod_lesser);  
    cout << "The upper_bound in v3 for the element with a value of 3 is: "  
        << *Result << "." << endl;  
}  
  
```  
## <a name="see-also"></a>Zobacz też   
 [\<algorithm>](../standard-library/algorithm.md)