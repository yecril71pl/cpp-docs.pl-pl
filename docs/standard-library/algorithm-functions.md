---
title: funkcje&gt; algorytm &lt;
ms.date: 11/04/2016
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
ms.assetid: c10b0c65-410c-4c83-abf8-8b7f61bba8d0
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
ms.openlocfilehash: 199634997397cca0008c60843b5d977633277331
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821886"
---
# <a name="ltalgorithmgt-functions"></a>funkcje&gt; algorytm &lt;

## <a name="adjacent_find"></a>adjacent_find

Wyszukuje dwa sąsiadujące elementy, które są równe lub spełniają określony warunek.

```cpp
template<class ForwardIterator>
ForwardIterator adjacent_find(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator , class BinaryPredicate>
ForwardIterator adjacent_find(
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator adjacent_find(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class BinaryPredicate>
ForwardIterator adjacent_find(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator do przodu, odnoszący się do pozycji pierwszego elementu w zakresie, który ma być przeszukiwany.

*ostatni*\
Iterator do przodu, odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma być przeszukiwany.

*pred*\
Predykat binarny dający warunek do spełnienia przez wartości sąsiadujących elementów w przeszukiwanym zakresie.

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu do pierwszego z sąsiadujących elementów, które są równe siebie (w pierwszej wersji) lub który spełnia warunek określony przez Predykat binarny (w drugiej wersji), pod warunkiem, że taka para elementów zostanie znaleziona. W przeciwnym razie zwracany jest iterator wskazujący *ostatni* .

### <a name="remarks"></a>Uwagi

Algorytm `adjacent_find` jest niemutacją algorytmem sekwencji. Zakres, który ma być przeszukiwany, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a ostatnia pozycja jest dostępna od pierwszej do przyrostu. Stopień złożoności algorytmu jest liniowy w liczbie elementów zawartych w zakresie.

`operator==` używany do określenia dopasowania między elementami musi nałożyć relację równoważności między operandami.

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
    list<int> L;
    list<int>::iterator Iter;
    list<int>::iterator result1, result2;

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
        cout << "There are two adjacent elements that are equal.\n"
            << "They have a value of "
            << *( result1 ) << "." << endl;

    result2 = adjacent_find( L.begin( ), L.end( ), twice );
    if ( result2 == L.end( ) )
        cout << "There are not two adjacent elements where the "
            << "second is twice the first." << endl;
    else
    {
        cout << "There are two adjacent elements where "
            << "the second is twice the first.\n"
            << "They have values of " << *(result2++)
            << " & " << *result2 << "." << endl;
    }
}
```

```Output
L = ( 50 40 10 20 20 )
There are two adjacent elements that are equal.
They have a value of 20.
There are two adjacent elements where the second is twice the first.
They have values of 10 & 20.
```

## <a name="all_of"></a>all_of

Zwraca **wartość PRAWDA** , jeśli warunek jest obecny dla każdego elementu w danym zakresie.

```cpp
template<class InputIterator, class UnaryPredicate>
bool all_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool all_of(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator danych wejściowych, który wskazuje, gdzie rozpocząć sprawdzanie warunku. Znaczniki iteratora, w których jest uruchamiany zakres elementów.

*ostatni*\
Iterator danych wejściowych, który wskazuje koniec zakresu elementów do sprawdzenia dla warunku.

*pred*\
Warunek do przetestowania. Jest to zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje warunek, który ma być spełniony przez sprawdzany element. Predykat jednoargumentowy przyjmuje jeden argument i zwraca **wartość PRAWDA** lub **Fałsz**.

### <a name="return-value"></a>Wartość zwracana

Zwraca **wartość true** , jeśli warunek jest wykrywany dla każdego elementu w wskazanym zakresie lub jeśli zakres jest pusty, a w przeciwnym razie ma **wartość false** .

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca **wartość true** tylko wtedy, gdy dla każdego `N` w zakresie `[0, last - first)`, predykat `pred(*(first + N))` ma **wartość true**.

### <a name="example"></a>Przykład

```cpp
// alg_all_of.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;

    list<int> li { 50, 40, 10, 20, 20 };
    list<int>::iterator iter;

    cout << "li = ( ";
    for (iter = li.begin(); iter != li.end(); iter++)
        cout << *iter << " ";
    cout << ")" << endl;

    // Check if all elements in li are even.
    auto is_even = [](int elem){ return !(elem % 2); };
    if (all_of(li.begin(), li.end(), is_even))
        cout << "All the elements are even numbers.\n";
    else
        cout << "Not all the elements are even numbers.\n";
}
```

```Output
li = ( 50 40 10 20 20 )
All the elements are even numbers.
```

## <a name="any_of"></a>any_of

Zwraca **wartość PRAWDA** , jeśli warunek występuje co najmniej raz w określonym zakresie elementów.

```cpp
template<class InputIterator, class UnaryPredicate>
bool any_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool any_of(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator danych wejściowych, który wskazuje, gdzie rozpocząć sprawdzanie zakresu elementów dla warunku.

*ostatni*\
Iterator danych wejściowych, który wskazuje koniec zakresu elementów do sprawdzenia dla warunku.

*pred*\
Warunek do przetestowania. Jest to zapewniane przez zdefiniowany przez użytkownika obiekt funkcji predykatu. Predykat definiuje warunek, który ma być spełniony przez testowany element. Predykat jednoargumentowy przyjmuje jeden argument i zwraca **wartość PRAWDA** lub **Fałsz**.

### <a name="return-value"></a>Wartość zwracana

Zwraca **wartość true** , jeśli warunek jest wykrywany co najmniej raz we wskazanym zakresie, **Fałsz** , jeśli warunek nie jest nigdy wykryty.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca **wartość true** tylko wtedy, gdy dla niektórych `N` w zakresie

`[0, last - first)`predykat `pred(*(first + N))` ma wartość true.

### <a name="example"></a>Przykład

```cpp
// alg_any_of.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;

    list<int> li { 51, 41, 11, 21, 20 };

    cout << "li = ( ";
    for (auto const& el : li)
        cout << el << " ";
    cout << ")" << endl;

    // Check if there is an even elememt in li.
    auto is_even = [](int const elem){ return !(elem % 2); };
    if (any_of(li.begin(), li.end(), is_even))
        cout << "There's an even element in li.\n";
    else
        cout << "There are no even elements in li.\n";
}
```

```Output
li = ( 51 41 11 21 20 )
There's an even element in li.
```

## <a name="binary_search"></a>binary_search

Testuje, czy w sortowanym zakresie istnieje element, który jest równy określonej wartości lub który jest odpowiednikiem w sensie określonym przez predykat binarny.

```cpp
template<class ForwardIterator, class Type>
bool binary_search(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator, class Type, class BinaryPredicate>
bool binary_search(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*pierwszy*\
Iterator do przodu, odnoszący się do pozycji pierwszego elementu w zakresie, który ma być przeszukiwany.

*ostatni*\
Iterator do przodu, odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma być przeszukiwany.

\ *wartości*
Wartość wymagana do dopasowania przez wartość elementu lub, która musi spełniać warunek z wartością elementu określoną przez Predykat binarny.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje sens, w którym jeden element jest mniejszy niż inny. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli element znajduje się w zakresie równym lub równoważnym z określoną wartością; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Posortowany zakres źródłowy musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w ramach sekwencji Ostatnia pozycja musi być osiągalna od pierwszej przez przyrost.

Posortowany zakres musi być uporządkowany jako warunek wstępny do zastosowania algorytmu `binary_search`, zgodnie z tą samą kolejnością, w jakiej ma być używany przez algorytm w celu sortowania połączonych zakresów.

Zakresy źródłowe nie są modyfikowane przez `binary_search`.

Typy wartości iteratorów do przodu muszą być mniej-niż porównywalne do uporządkowania, tak że, w przypadku dwóch elementów, można określić, że są one równoważne (w sensie, że żaden z nich nie jest mniejszy niż drugi) lub że jeden z nich jest mniejszy od drugiego. Powoduje to porządkowanie między nierównoważnymi elementami

Złożoność algorytmu jest logarytmiczna dla iteratorów dostępu losowego i liniowego w przeciwnym razie z liczbą kroków proporcjonalną do (`last` - `first`).

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

int main()
{
    using namespace std;

    list<int> List1;

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
    if ( binary_search(List1.begin(), List1.end(), 10) )
        cout << "There is an element in list List1 with a value equal to 10."
        << endl;
    else
        cout << "There is no element in list List1 with a value equal to 10."
        << endl;

    // a binary_search under the binary predicate greater
    List1.sort(greater<int>());
    if ( binary_search(List1.begin(), List1.end(), 10, greater<int>()) )
        cout << "There is an element in list List1 with a value greater than 10 "
        << "under greater than." << endl;
    else
        cout << "No element in list List1 with a value greater than 10 "
        << "under greater than." << endl;

    // a binary_search under the user-defined binary predicate mod_lesser
    vector<int> v1;

    for ( auto i = -2; i <= 4; ++i )
    {
        v1.push_back(i);
    }

    sort(v1.begin(), v1.end(), mod_lesser);

    cout << "Ordered using mod_lesser, vector v1 = ( " ;
    for ( auto Iter : v1 )
        cout << Iter << " ";
    cout << ")" << endl;

    if ( binary_search(v1.begin(), v1.end(), -3, mod_lesser) )
        cout << "There is an element with a value equivalent to -3 "
        << "under mod_lesser." << endl;
    else
        cout << "There is not an element with a value equivalent to -3 "
        << "under mod_lesser." << endl;
}
```

```Output
List1 = ( 5 10 20 25 30 50 )
There is an element in list List1 with a value equal to 10.
There is an element in list List1 with a value greater than 10 under greater than.
Ordered using mod_lesser, vector v1 = ( 0 -1 1 -2 2 3 4 )
There is an element with a value equivalent to -3 under mod_lesser.
```

## <a name="clamp"></a>opraw

Porównuje wartość z górną i dolną granicą i zwraca odwołanie do wartości, jeśli jest między granicami lub odwołaniem do górnej lub dolnej granicy, jeśli wartość jest odpowiednio powyżej lub poniżej.

```cpp
template<class Type>
constexpr const Type& clamp(
    const Type& value,
    const Type& lower,
    const Type& upper);

template<class Type, class Compare>
constexpr const Type& clamp(
    const Type& value,
    const Type& lower,
    const Type& upper,
    Compare pred);
```

### <a name="parameters"></a>Parametry

\ *wartości*
Wartość do porównania z *górną* i *niższą*.

*dolna*\
Dolna granica wartości, do której ma zostać zamocowana *wartość* .

*górny*\
Górna granica wartości, do której należy *wartość* .

*pred*\
Predykat używany do porównywania *wartości* z *dolną* lub *górną*. Predykat porównania przyjmuje dwa argumenty i zwraca **wartość true** , jeśli pierwszy jest w pewnym sensie mniejszy niż drugi i w przeciwnym razie **false**.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do *mniejszej* , jeśli `value < lower`lub odwołanie do *górnego* , jeśli `upper < value`. W przeciwnym razie zwraca odwołanie do *wartości*.

### <a name="remarks"></a>Uwagi

Zachowanie jest niezdefiniowane, jeśli *Górna* wartość jest mniejsza niż *Dolna*.

## <a name="copy"></a>kopiowane

Przypisuje wartości elementów z zakresu źródłowego do zakresu docelowego, iterując przez sekwencję źródłową elementów oraz przypisując im nowe pozycje w kierunku do przodu.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator copy(
    InputIterator first,
    InputIterator last,
    OutputIterator destBeg);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w zakresie źródłowym.

*ostatni*\
Iterator danych wejściowych odnoszący się do pozycji, która jest jedną poza ostatnim elementem w zakresie źródłowym.

*destBeg*\
Iterator danych wyjściowych odnoszący się do pozycji pierwszego elementu w zakresie docelowym.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych odnoszący się do pozycji, która jest jedną poza ostatnim elementem w zakresie docelowym, czyli adresów iteratorów `result` + (*ostatni* - *pierwszy*).

### <a name="remarks"></a>Uwagi

Zakres źródłowy musi być prawidłowy i musi być wystarczająco dużo miejsca w miejscu przeznaczenia, aby pomieścić wszystkie elementy kopiowane.

Ponieważ algorytm Kopiuje elementy źródłowe w kolejności rozpoczynającej się od pierwszego elementu, zakres docelowy może pokrywać się z zakresem źródłowym, pod warunkiem, że *Ostatnia* pozycja zakresu źródłowego nie jest zawarta w zakresie docelowym. `copy` może służyć do przesuwania elementów z lewej strony, ale nie do prawej, chyba że między zakres źródłowy i docelowy. Aby przesunąć do prawej dowolnej liczby pozycji, użyj algorytmu [copy_backward](../standard-library/algorithm-functions.md#copy_backward) .

Algorytm `copy` modyfikuje tylko wartości wskazywane przez Iteratory, przypisując nowe wartości do elementów w zakresie docelowym. Nie może służyć do tworzenia nowych elementów i nie może bezpośrednio wstawiać elementów do pustego kontenera.

### <a name="example"></a>Przykład

```cpp
// alg_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

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

## <a name="copy_backward"></a>copy_backward

Przypisuje wartości elementów z zakresu źródłowego do zakresu docelowego, iterując przez sekwencję źródłową elementów oraz przypisując im nowe pozycje w kierunku do tyłu.

```cpp
template<class BidirectionalIterator1, class BidirectionalIterator2>
BidirectionalIterator2 copy_backward(
    BidirectionalIterator1 first,
    BidirectionalIterator1 last,
    BidirectionalIterator2 destEnd);
```

### <a name="parameters"></a>Parametry

*pierwszy*\
Iterator dwukierunkowy odnoszący się do pozycji pierwszego elementu w zakresie źródłowym.

*ostatni*\
Iterator dwukierunkowy odnoszący się do pierwszej pozycji po elemencie końcowym w zakresie źródłowym.

*destEnd*\
Iterator dwukierunkowy odnoszący się do pierwszej pozycji po elemencie końcowym w zakresie docelowym.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych odnoszący się do pozycji, która jest jedną poza elementem końcowym*w - zakresie* docelowym

### <a name="remarks"></a>Uwagi

Zakres źródłowy musi być prawidłowy i musi być wystarczająco dużo miejsca w miejscu przeznaczenia, aby pomieścić wszystkie elementy kopiowane.

Algorytm `copy_backward` nakłada bardziej rygorystyczne wymagania niż algorytm `copy`. Oba iteratory, wejściowy i wyjściowy muszą być dwukierunkowe.

Algorytmy `copy_backward` i [move_backward](../standard-library/algorithm-functions.md#move_backward) są jedynymi C++ algorytmami biblioteki standardowej, które wyznaczają zakres wyjściowy z iteratorem wskazującym na koniec zakresu docelowego.

Ponieważ algorytm Kopiuje elementy źródłowe w kolejności rozpoczynającej się od ostatniego elementu, zakres docelowy może pokrywać się z zakresem źródłowym, pod warunkiem, że *Pierwsza* pozycja zakresu źródłowego nie jest zawarta w zakresie docelowym. `copy_backward` może służyć do przesuwania elementów w prawo, ale nie do lewej, chyba że między zakres źródłowy i docelowy. Aby przesunąć w lewo dowolną liczbę pozycji, użyj algorytmu [kopiowania](../standard-library/algorithm-functions.md#copy) .

Algorytm `copy_backward` modyfikuje tylko wartości wskazywane przez Iteratory, przypisując nowe wartości do elementów w zakresie docelowym. Nie może służyć do tworzenia nowych elementów i nie może bezpośrednio wstawiać elementów do pustego kontenera.

### <a name="example"></a>Przykład

```cpp
// alg_copy_bkwd.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

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

```Output
v1 = ( 0 10 20 30 40 50 )
v2 = ( 0 3 6 9 12 15 18 21 24 27 30 )
v2 with v1 insert = ( 0 3 6 9 0 10 20 21 24 27 30 )
v2 with shifted insert = ( 0 3 6 9 0 10 0 10 20 27 30 )
```

## <a name="copy_if"></a>copy_if

W zakresie elementów Kopiuje elementy, które są **spełnione** dla określonego warunku.

```cpp
template<class InputIterator, class OutputIterator, class UnaryPredicate>
OutputIterator copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator dest,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate>
ForwardIterator2 copy_if(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator danych wejściowych, który wskazuje początek zakresu do sprawdzenia warunku.

*ostatni*\
Iterator danych wejściowych, który wskazuje koniec zakresu.

\ miejsca *docelowego*
Iterator danych wyjściowych, który wskazuje miejsce docelowe dla skopiowanych elementów.

*pred*\
Warunek, względem którego jest testowany każdy element w zakresie. Ten warunek jest dostarczany przez zdefiniowany przez użytkownika obiekt funkcji predykatu. Predykat jednoargumentowy przyjmuje jeden argument i zwraca **wartość PRAWDA** lub **Fałsz**.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych, który jest równy elementowi *docelowy* przyrostowo dla każdego elementu, który spełnia warunek. Innymi słowy wartość zwracana minus *docelowy* jest równa liczbie skopiowanych elementów.

### <a name="remarks"></a>Uwagi

Funkcja szablonu oblicza

`if (pred(*first + N)) * dest++ = *(first + N))`

jeden raz dla każdego `N` w zakresie `[0, last - first)`, dla ściśle rosnących wartości `N` zaczynających się od najniższej wartości. Jeśli *docelowy* i *pierwszy* wyznaczysz regiony magazynu, element *docelowy* nie może znajdować się w zakresie `[ first, last )`.

### <a name="example"></a>Przykład

```cpp
// alg_copy_if.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

void listlist(std::list<int> l)
{
    std::cout << "( ";
    for (auto const& el : l)
        std::cout << el << " ";
    std::cout << ")" << std::endl;
}

int main()
{
    using namespace std;
    list<int> li{ 46, 59, 88, 72, 79, 71, 60, 5, 40, 84 };
    list<int> le(li.size()); // le = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
    list<int> lo(li.size()); // lo = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };

    cout << "li = ";
    listlist(li);

    // is_even checks if the element is even.
    auto is_even = [](int const elem) { return !(elem % 2); };
    // use copy_if to select only even elements from li 
    // and copy them to le, starting from le's begin position
    auto ec = copy_if(li.begin(),li.end(), le.begin(), is_even);
    le.resize(std::distance(le.begin(), ec));  // shrink le to new size

    cout << "Even numbers are le = ";
    listlist(le);

    // is_odd checks if the element is odd.
    auto is_odd = [](int const elem) { return (elem % 2); };
    // use copy_if to select only odd elements from li
    // and copy them to lo, starting from lo's begin position
    auto oc = copy_if(li.begin(), li.end(), lo.begin(), is_odd);
    lo.resize(std::distance(lo.begin(), oc));  // shrink lo to new size

    cout << "Odd numbers are lo = ";
    listlist(lo);
}
```

```Output
li = ( 46 59 88 72 79 71 60 5 40 84 )
Even numbers are le = ( 46 88 72 60 40 84 )
Odd numbers are lo = ( 59 79 71 5 )
```

## <a name="copy_n"></a>copy_n

Kopiuje określoną liczbę elementów.

```cpp
template<class InputIterator, class Size, class OutputIterator>
OutputIterator copy_n(
    InputIterator first,
    Size count,
    OutputIterator dest);

template<class ExecutionPolicy, class ForwardIterator1, class Size, class ForwardIterator2>
ForwardIterator2 copy_n(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    Size count,
    ForwardIterator2 dest);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator danych wejściowych wskazujący miejsce, z którego mają zostać skopiowane elementy.

*liczba*\
Typ liczby całkowitej ze znakiem lub bez znaku określający liczbę elementów do skopiowania.

\ miejsca *docelowego*
Iterator danych wyjściowych wskazujący miejsce, do którego należy skopiować elementy.

### <a name="return-value"></a>Wartość zwracana

Zwraca iterator danych wyjściowych, w przypadku których elementy zostały skopiowane do. Jest taka sama jak wartość zwrócona przez parametr *docelowy* .

### <a name="remarks"></a>Uwagi

Funkcja szablonu oblicza `*(dest + N) = *(first + N))` raz dla każdego `N` w zakresie `[0, count)`, dla ściśle rosnących wartości `N`, zaczynając od najniższej wartości. Następnie zwraca `dest + N`. Jeśli *docelowy* i *pierwszy* wyznaczysz regiony magazynu, element *docelowy* nie może znajdować się w zakresie `[first, last)`.

### <a name="example"></a>Przykład

```cpp
// alg_copy_n.cpp
// compile with: cl /EHsc /W4 alg_copy_n.cpp
#include <algorithm>
#include <iostream>
#include <string>

int main()
{
    using namespace std;
    string s1{"dandelion"};
    string s2{"badger"};

    cout << s1 << " + " << s2 << " = ";

    // Copy the first 3 letters from s1
    // to the first 3 positions in s2
    copy_n(s1.begin(), 3, s2.begin());

    cout << s2 << endl;
}
```

```Output
dandelion + badger = danger
```

## <a name="count"></a>liczbą

Zwraca liczbę elementów w zakresie, których wartości pasują do określonej wartości.

```cpp
template<class InputIterator, class Type>
typename iterator_traits<InputIterator>::difference_type count(
    InputIterator first,
    InputIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
typename iterator_traits<ForwardIterator>::difference_type
count(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w zakresie, który ma zostać przesunięty.

*ostatni*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma zostać przesunięty.

\ *wartości*
Wartość elementów do zliczenia.

### <a name="return-value"></a>Wartość zwracana

Typ różnicy `InputIterator`, który zlicza liczbę elementów w zakresie [*First*, *Last*), które mają *wartość*Value.

### <a name="remarks"></a>Uwagi

`operator==` używany do określenia dopasowania między elementem a określoną wartością musi nałożyć relację równoważności między operandami.

Ten algorytm jest uogólniony do zliczania elementów, które spełniają dowolny predykat za pomocą funkcji szablonu [count_if](../standard-library/algorithm-functions.md#count_if).

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

## <a name="count_if"></a>count_if

Zwraca liczbę elementów w zakresie, których wartości spełniają określony warunek.

```cpp
template<class InputIterator, class UnaryPredicate>
typename iterator_traits<InputIterator>::difference_type count_if(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
typename iterator_traits<ForwardIterator>::difference_type
count_if(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w zakresie, który ma być przeszukiwany.

*ostatni*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma być przeszukiwany.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje warunek do spełnienia w przypadku zliczenia elementu. Predykat jednoargumentowy przyjmuje jeden argument i zwraca **wartość PRAWDA** lub **Fałsz**.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów, które spełniają warunek określony przez predykat.

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu jest generalizacją [liczby](../standard-library/algorithm-functions.md#count)algorytmów, zastępując predykat "równa określonej wartości" z dowolnym predykatem.

### <a name="example"></a>Przykład

```cpp
// alg_count_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater10(int value)
{
    return value > 10;
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

## <a name="equal"></a>większy

Porównuje dwa zakresy elementów przez element pod kątem równości lub równoważności w sensie określonym przez Predykat binarny.

Użyj `std::equal` podczas porównywania elementów w różnych typach kontenerów (na przykład `vector` i `list`) lub podczas porównywania różnych typów elementów lub gdy zachodzi potrzeba porównania podzakresów kontenerów. W przeciwnym razie, podczas porównywania elementów tego samego typu w tym samym typie kontenera, użyj `operator==` nienależących do elementu członkowskiego, który jest udostępniany dla każdego kontenera.

Używaj przeciążeń podwójnego zakresu w kodzie języka C++ 14, ponieważ przeciążenia, które pobierają tylko jeden iterator dla drugiego zakresu, nie wykryją różnic, jeśli drugi zakres jest dłuższy niż pierwszy zakres i spowoduje niezdefiniowane zachowanie, jeśli drugi zakres jest krótszy niż pierwszy zakres.

```cpp
template<class InputIterator1, class InputIterator2>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    BinaryPredicate pred); // C++14

template<class InputIterator1, class InputIterator2>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*first1*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w pierwszym zakresie do przetestowania.

*last1*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem z pierwszego zakresu do przetestowania.

*first2*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w drugim zakresie, który ma zostać przetestowany.

*last2*\
Iterator danych wejściowych odnoszący się do pozycji jednego ostatniego elementu z drugiego zakresu, który ma zostać przetestowany.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje warunek do spełnienia, jeśli dwa elementy mają być wykonane jako równoważne. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli i tylko wtedy, gdy zakresy są identyczne lub równoważne pod predykatem binarnym, gdy porównane elementy przez element; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Zakres, który ma być przeszukiwany, musi być prawidłowy; wszystkie Iteratory muszą być odwołujące się, a ostatnia pozycja jest dostępna od pierwszego do przyrostu.

Jeśli dwa zakresy są równej długości, to stopień złożoności algorytmu jest liniowy w liczbie elementów zawartych w zakresie. W przeciwnym razie funkcja natychmiast zwraca **wartość false**.

Ani `operator==` ani predykatu zdefiniowanego przez użytkownika nie jest wymagana, aby nałożyć relację równoważności, która jest symetryczna, zwrotna i przechodnia między operandami.

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

## <a name="equal_range"></a>equal_range

Mając uporządkowany zakres, znajduje Podzakres, w którym wszystkie elementy są równoważne danej wartości.

```cpp
template<class ForwardIterator, class Type>
pair<ForwardIterator, ForwardIterator> equal_range(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator, class Type, class Compare>
pair<ForwardIterator, ForwardIterator> equal_range(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*pierwszy*\
Iterator do przodu, odnoszący się do pozycji pierwszego elementu w zakresie, który ma być przeszukiwany.

*ostatni*\
Iterator do przodu, odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma być przeszukiwany.

\ *wartości*
Wartość wyszukiwana w zakresie uporządkowanym.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje sens, w którym jeden element jest mniejszy niż inny. Predykat porównania przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="return-value"></a>Wartość zwracana

Para iteratorów do przodu, która określa Podzakres, zawarty w przeszukiwanym zakresie, w którym wszystkie elementy są równoważne *wartości* w sensie zdefiniowanym przez używany Predykat binarny ( *pred* lub domyślny, mniejszy niż).

Jeśli żadne elementy z zakresu nie są równoważne *wartości*, Iteratory do przodu w zwróconej parze są równe i określają punkt, w którym *wartość* może zostać wstawiona bez zakłócania kolejności zakresu.

### <a name="remarks"></a>Uwagi

Pierwszy iterator pary zwracanej przez algorytm jest [lower_bound](../standard-library/algorithm-functions.md#lower_bound), a drugi iterator jest [upper_bound](../standard-library/algorithm-functions.md#upper_bound).

Zakres musi być sortowany zgodnie z predykatem dostarczonym do `equal_range`. Na przykład, jeśli zamierzasz użyć predykatu większości, zakres musi być sortowany w kolejności malejącej.

Elementy w prawdopodobnie pustym podzakresie zdefiniowanym przez parę iteratorów zwracanych przez `equal_range` będą równoważne *wartości* w sensie zdefiniowanym przez użyty predykat.

Złożoność algorytmu jest logarytmiczna dla iteratorów dostępu losowego i liniowego w przeciwnym razie z liczbą kroków proporcjonalnie*do (* *najpierw - pierwszej*).

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

template<class T> void dump_vector( const vector<T>& v, pair<typename vector<T>::iterator, typename vector<T>::iterator> range )
{
    // prints vector v with range delimited by [ and ]

    for ( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        if ( i == range.first )
        {
            cout << "[ ";
        }
        if ( i == range.second )
        {
            cout << "] ";
        }

        cout << *i << " ";
    }
    cout << endl;
}

template<class T> void equal_range_demo( const vector<T>& original_vector, T value )
{
    vector<T> v(original_vector);

    sort( v.begin(), v.end() );
    cout << "Vector sorted by the default binary predicate <:" << endl << '\t';
    for ( vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        cout << *i << " ";
    }
    cout << endl << endl;

    pair<vector<T>::iterator, vector<T>::iterator> result
        = equal_range( v.begin(), v.end(), value );

    cout << "Result of equal_range with value = " << value << ":" << endl << '\t';
    dump_vector( v, result );
    cout << endl;
}

template<class T, class F> void equal_range_demo( const vector<T>& original_vector, T value, F pred, string predname )
{
    vector<T> v(original_vector);

    sort( v.begin(), v.end(), pred );
    cout << "Vector sorted by the binary predicate " << predname << ":" << endl << '\t';
    for ( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        cout << *i << " ";
    }
    cout << endl << endl;

    pair<typename vector<T>::iterator, typename vector<T>::iterator> result
        = equal_range( v.begin(), v.end(), value, pred );

    cout << "Result of equal_range with value = " << value << ":" << endl << '\t';
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
    for ( int i = -1; i <= 4; ++i )
    {
        v1.push_back(i);
    }

    for ( int i =-3; i <= 0; ++i )
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

## <a name="fill"></a>pełni

Przypisuje tę samą nową wartość każdemu elementowi w określonym zakresie.

```cpp
template<class ForwardIterator, class Type>
void fill(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
void fill(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator do przodu, odnoszący się do pozycji pierwszego elementu w zakresie, który ma zostać przesunięty.

*ostatni*\
Iterator do przodu, odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma zostać przesunięty.

\ *wartości*
Wartość, która ma zostać przypisana do elementów w zakresie [*First*, *Last*).

### <a name="remarks"></a>Uwagi

Zakres docelowy musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a ostatnia pozycja jest dostępna od pierwszej do przyrostu. Złożoność jest liniowa z rozmiarem zakresu.

### <a name="example"></a>Przykład

```cpp
// alg_fill.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

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

## <a name="fill_n"></a>fill_n

Przypisuje nową wartość do określonej liczby elementów w zakresie rozpoczynającym się od określonego elementu.

```cpp
template<class OutputIterator, class Size, class Type>
OutputIterator fill_n(
    OutputIterator first,
    Size count,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Type>
ForwardIterator fill_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    Size count,
    const Type& value);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator danych wyjściowych odnoszący się do pozycji pierwszego elementu w zakresie, w którym ma zostać przypisana *wartość*wartości.

*liczba*\
Typ liczby całkowitej ze znakiem lub bez znaku określający liczbę elementów do przypisania do wartości.

\ *wartości*
Wartość, która ma zostać przypisana do elementów w zakresie [*First*, *First + Count*).

### <a name="return-value"></a>Wartość zwracana

Iterator do elementu, który następuje po ostatnim elemencie wypełnionym, jeśli *licznik* > zero, w przeciwnym razie pierwszy element.

### <a name="remarks"></a>Uwagi

Zakres docelowy musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a ostatnia pozycja jest dostępna od pierwszej do przyrostu. Złożoność jest liniowa z rozmiarem zakresu.

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
    vector<int> v;

    for ( auto i = 0 ; i < 9 ; ++i )
        v.push_back( 0 );

    cout << " vector v = ( " ;
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

## <a name="find"></a>wyświetlić

Lokalizuje pozycję pierwszego wystąpienia elementu w zakresie, który ma określoną wartość.

```cpp
template<class InputIterator, class Type>
InputIterator find(
    InputIterator first,
    InputIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
ForwardIterator find(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w zakresie, który ma być wyszukiwany dla określonej wartości.

*ostatni*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma być wyszukiwany dla określonej wartości.

\ *wartości*
Wartość do wyszukania.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych odnoszący się do pierwszego wystąpienia określonej wartości w przeszukiwanym przedziale. Jeśli nie zostanie znaleziony żaden element o równoważnej wartości, zwraca *Last*.

### <a name="remarks"></a>Uwagi

`operator==` używany do określenia dopasowania między elementem a określoną wartością musi nałożyć relację równoważności między operandami.

Aby zapoznać się z przykładem kodu przy użyciu `find()`, zobacz [find_if](../standard-library/algorithm-functions.md#find_if).

## <a name="find_end"></a>find_end

Wyszukuje w zakresie ostatnią podsekwencję, która jest identyczna z określoną sekwencją lub jest równoważna w sensie określonym przez predykat binarny.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 find_end(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class Pred>
ForwardIterator1 find_end(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    Pred pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator1
find_end(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1,
class ForwardIterator2, class BinaryPredicate>
ForwardIterator1
find_end(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*first1*\
Iterator do przodu, odnoszący się do pozycji pierwszego elementu w zakresie, który ma być przeszukiwany.

*last1*\
Iterator do przodu, odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma być przeszukiwany.

*first2*\
Iterator do przodu, odnoszący się do pozycji pierwszego elementu w zakresie, który ma zostać wyszukany.

*last2*\
Iterator do przodu, odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma zostać wyszukany.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje warunek do spełnienia, jeśli dwa elementy mają być wykonane jako równoważne. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, odnoszący się do pozycji pierwszego elementu ostatniej podsekwencji w obrębie [FIRST1, last1), który jest zgodny z określoną sekwencją [First2, last2).

### <a name="remarks"></a>Uwagi

`operator==` używany do określenia dopasowania między elementem a określoną wartością musi nałożyć relację równoważności między operandami.

Zakresy, do których istnieją odwołania, muszą być prawidłowe; wszystkie wskaźniki muszą być odwołujące się, a w każdej sekwencji Ostatnia pozycja jest dostępna od pierwszej do przyrostu.

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

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

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
    vector<int>::iterator result1;
    result1 = find_end ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

    if ( result1 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is a match of L1 in v1 that begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for a match to L1 under the binary predicate twice
    vector<int>::iterator result2;
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

## <a name="find_first_of"></a>find_first_of

Wyszukuje pierwsze wystąpienie którejś z kilku wartości w zakresie docelowym lub pierwsze wystąpienie któregoś z kilku elementów, które są równoważne w sensie określonym przez predykat binarny dla określonego zestawu elementów.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 find_first_of(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 find_first_of(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator1
find_first_of(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1,
class ForwardIterator2, class BinaryPredicate>
ForwardIterator1
find_first_of(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*first1*\
Iterator do przodu, odnoszący się do pozycji pierwszego elementu w zakresie, który ma być przeszukiwany.

*last1*\
Iterator do przodu, odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma być przeszukiwany.

*first2*\
Iterator do przodu, odnoszący się do pozycji pierwszego elementu w zakresie, który ma zostać dopasowany.

*last2*\
Iterator do przodu, odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma zostać dopasowany.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje warunek do spełnienia, jeśli dwa elementy mają być wykonane jako równoważne. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, odnoszący się do pozycji pierwszego elementu pierwszej podsekwencji, która pasuje do określonej sekwencji lub jest równoważne w sensie określonym przez Predykat binarny.

### <a name="remarks"></a>Uwagi

`operator==` używany do określenia dopasowania między elementem a określoną wartością musi nałożyć relację równoważności między operandami.

Zakresy, do których istnieją odwołania, muszą być prawidłowe; wszystkie wskaźniki muszą być odwołujące się, a w każdej sekwencji Ostatnia pozycja jest dostępna od pierwszej do przyrostu.

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

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

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
    vector<int>::iterator result1;
    result1 = find_first_of ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

    if ( result1 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is at least one match of L1 in v1"
            << "\n and the first one begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for a match to L1 under the binary predicate twice
    vector<int>::iterator result2;
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

## <a name="find_if"></a>find_if

Lokalizuje pozycję pierwszego wystąpienia elementu w zakresie, który spełnia określony warunek.

```cpp
template<class InputIterator, class UnaryPredicate>
InputIterator find_if(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator find_if(
    ExecutionPolicy&& exec,
    ForwardIterator first, ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*pierwszy*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w zakresie, który ma być przeszukiwany.

*ostatni*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma być przeszukiwany.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu lub [wyrażenie lambda](../cpp/lambda-expressions-in-cpp.md) , które definiuje warunek, który ma być spełniony przez wyszukiwany element. Predykat jednoargumentowy przyjmuje jeden argument i zwraca **wartość true** , jeśli jest spełniony, lub **false** , jeśli nie jest spełniony. Sygnatura *pred* musi być efektywnie `bool pred(const T& arg);`, gdzie `T` jest typem, do którego `InputIterator` można niejawnie skonwertować podczas wyłączania. Słowo kluczowe **const** jest wyświetlane tylko w celu zilustrowania, że obiekt Function lub lambda nie powinien modyfikować argumentu.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych odnoszący się do pierwszego elementu w zakresie, który spełnia warunek określony przez predykat (predykat daje w wyniku **wartość true**). Jeśli żaden element nie zostanie znaleziony do spełnienia predykatu, zwraca wartość *Last*.

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu jest generalizacją w celu [znalezienia](../standard-library/algorithm-functions.md#find)algorytmu, zastępując predykat "równa się określonej wartości" z dowolnym predykatem. Dla logicznego przeciwieństwa (Znajdź pierwszy element, który nie spełnia predykatu), zobacz [find_if_not](../standard-library/algorithm-functions.md#find_if_not).

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

## <a name="find_if_not"></a>find_if_not

Zwraca pierwszy element we wskazanym zakresie, który nie spełnia warunku.

```cpp
template<class InputIterator, class UnaryPredicate>
InputIterator find_if_not(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator find_if_not(
    ExecutionPolicy&& exec,
    ForwardIterator first, ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*pierwszy*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w zakresie, który ma być przeszukiwany.

*ostatni*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma być przeszukiwany.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu lub [wyrażenie lambda](../cpp/lambda-expressions-in-cpp.md) , które definiuje warunek, który nie jest spełniony przez wyszukiwany element. Predykat jednoargumentowy przyjmuje jeden argument i zwraca **wartość true** , jeśli jest spełniony, lub **false** , jeśli nie jest spełniony. Sygnatura *pred* musi być efektywnie `bool pred(const T& arg);`, gdzie `T` jest typem, do którego `InputIterator` można niejawnie skonwertować podczas wyłączania. Słowo kluczowe **const** jest wyświetlane tylko w celu zilustrowania, że obiekt Function lub lambda nie powinien modyfikować argumentu.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wejściowych odnoszący się do pierwszego elementu w zakresie, który nie spełnia warunku określonego przez predykat (predykat wynikiem jest **false**). Jeśli wszystkie elementy spełniają predykat (predykat jest **wartością true** dla każdego elementu), zwraca *Last*.

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu jest generalizacją w celu [znalezienia](../standard-library/algorithm-functions.md#find)algorytmu, zastępując predykat "równa się określonej wartości" z dowolnym predykatem. Dla logicznego przeciwieństwa (Znajdź pierwszy element, który spełnia predykat), zobacz [find_if](../standard-library/algorithm-functions.md#find_if).

Aby zapoznać się z przykładem kodu, który można łatwo dostosować do `find_if_not()`, zobacz [find_if](../standard-library/algorithm-functions.md#find_if).

## <a name="for_each"></a>for_each

Stosuje określony obiekt funkcji do każdego elementu w kolejności do przodu w zakresie i zwraca obiekt funkcji.

```cpp
template<class InputIterator, class Function>
Function for_each(
    InputIterator first,
    InputIterator last,
    Function func);

template<class ExecutionPolicy, class ForwardIterator, class Function>
void for_each(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Function func);
```

### <a name="parameters"></a>Parametry

*pierwszy*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w zakresie, w którym mają być obsługiwane.

*ostatni*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w zakresie obsługiwanym przez.

\ *Func*
Obiekt funkcji zdefiniowanej przez użytkownika, który jest stosowany do każdego elementu w zakresie.

### <a name="return-value"></a>Wartość zwracana

Kopia obiektu funkcji po zastosowaniu do wszystkich elementów w zakresie.

### <a name="remarks"></a>Uwagi

Algorytm `for_each` jest bardzo elastyczny, co pozwala na modyfikację każdego elementu w zakresie w różnych sposób określony przez użytkownika. Funkcje szablonowana mogą być ponownie używane w zmodyfikowanym formularzu przez przekazanie innych parametrów. Funkcje zdefiniowane przez użytkownika mogą zbierać informacje w ramach wewnętrznego stanu, które algorytm może zwrócić po przetworzeniu wszystkich elementów w zakresie.

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w ramach sekwencji Ostatnia pozycja musi być osiągalna od pierwszej przez przyrost.

Złożoność jest liniowa z najwyżej (*ostatni* - *pierwsze*) porównania.

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
    MultValue ( const Type& value ) : Factor ( value ) {
    }

    // The function call for the element to be multiplied
    void operator( ) ( Type& elem ) const
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
    Average( ) : num ( 0 ) , sum ( 0 )
    {
    }

    // The function call to process the next elment
    void operator( ) ( int elem )
    {
        num++;      // Increment the element count
        sum += elem;   // Add the value to the partial sum
    }

    // return Average
    operator double( )
    {
        return static_cast<double> (sum) /
            static_cast<double> (num);
    }
};

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    // Constructing vector v1
    int i;
    for ( i = -4 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "Original vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Using for_each to multiply each element by a Factor
    for_each ( v1.begin( ), v1.end( ), MultValue<int> ( -2 ) );

    cout << "Multiplying the elements of the vector v1\n "
            << "by the factor -2 gives:\n v1mod1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // The function object is templatized and so can be
    // used again on the elements with a different Factor
    for_each (v1.begin( ), v1.end( ), MultValue<int> (5 ) );

    cout << "Multiplying the elements of the vector v1mod\n "
            << "by the factor 5 gives:\n v1mod2 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // The local state of a function object can accumulate
    // information about a sequence of actions that the
    // return value can make available, here the Average
    double avemod2 = for_each ( v1.begin( ), v1.end( ),
        Average( ) );
    cout << "The average of the elements of v1 is:\n Average ( v1mod2 ) = "
            << avemod2 << "." << endl;
}
```

```Output
Original vector v1 = ( -4 -3 -2 -1 0 1 2 ).
Multiplying the elements of the vector v1
by the factor -2 gives:
v1mod1 = ( 8 6 4 2 0 -2 -4 ).
Multiplying the elements of the vector v1mod
by the factor 5 gives:
v1mod2 = ( 40 30 20 10 0 -10 -20 ).
The average of the elements of v1 is:
Average ( v1mod2 ) = 10.
```

## <a name="for_each_n"></a>for_each_n

```cpp
template<class InputIterator, class Size, class Function>
InputIterator for_each_n(
    InputIterator first,
    Size n,
    Function f);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Function>
ForwardIterator for_each_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    Size n,
    Function f);
```

## <a name="generate"></a>utworzenie

Przypisuje wartości generowane przez obiekt funkcji do każdego elementu w zakresie.

```cpp
template<class ForwardIterator, class Generator>
void generate(
    ForwardIterator first,
    ForwardIterator last,
    Generator gen);

template<class ExecutionPolicy, class ForwardIterator, class Generator>
void generate(
    ExecutionPolicy&& exec,
    ForwardIterator first, ForwardIterator last,
    Generator gen);
```

### <a name="parameters"></a>Parametry

*pierwszy*\
Iterator do przodu, odnoszący się do pozycji pierwszego elementu w zakresie, do którego mają być przypisane wartości.

*ostatni*\
Iterator do przodu, odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, do którego mają być przypisane wartości.

\ *Gen*
Obiekt funkcji, który jest wywoływany bez argumentów, które są używane do generowania wartości, które mają być przypisane do każdego z elementów w zakresie.

### <a name="remarks"></a>Uwagi

Obiekt Function jest wywoływany dla każdego elementu w zakresie i nie musi zwracać tej samej wartości przy każdym wywołaniu. Może to być na przykład odczytany z pliku lub zajrzeć do i zmodyfikowanie stanu lokalnego. Typ wyniku generatora musi być konwertowany na typ wartości iteratorów do przodu dla zakresu.

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w ramach sekwencji Ostatnia pozycja musi być osiągalna od pierwszej przez przyrost.

Złożoność jest liniowa, przy czym dokładnie (`last` - `first`) wywołania generatora są wymagane.

### <a name="example"></a>Przykład

```cpp
// alg_generate.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

int main()
{
    using namespace std;

    // Assigning random values to vector integer elements
    vector<int> v1 ( 5 );
    vector<int>::iterator Iter1;
    deque<int> deq1 ( 5 );
    deque<int>::iterator d1_Iter;

    generate ( v1.begin( ), v1.end( ), rand );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Assigning random values to deque integer elements
    generate ( deq1.begin( ), deq1.end( ), rand );

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

## <a name="generate_n"></a>generate_n

Przypisuje wartości generowane przez obiekt funkcji do określonej liczby elementów w zakresie i powraca do położenia jednego z ostatniej przypisanej wartości.

```cpp
template<class OutputIterator, class Diff, class Generator>
void generate_n(
    OutputIterator first,
    Diff count,
    Generator gen);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Generator>
ForwardIterator generate_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    Size count,
    Generator gen);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator danych wyjściowych odnoszący się do pozycji pierwszego elementu w zakresie, do którego mają być przypisane wartości.

*liczba*\
Typ liczby całkowitej ze znakiem lub bez znaku określający liczbę elementów, do których ma zostać przypisana wartość przez funkcję generatora.

\ *Gen*
Obiekt funkcji, który jest wywoływany bez argumentów, które są używane do generowania wartości, które mają być przypisane do każdego z elementów w zakresie.

### <a name="remarks"></a>Uwagi

Obiekt Function jest wywoływany dla każdego elementu w zakresie i nie musi zwracać tej samej wartości przy każdym wywołaniu. Może to być na przykład odczytany z pliku lub zajrzeć do i zmodyfikowanie stanu lokalnego. Typ wyniku generatora musi być konwertowany na typ wartości iteratorów do przodu dla zakresu.

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w ramach sekwencji Ostatnia pozycja musi być osiągalna od pierwszej przez przyrost.

Złożoność jest liniowa i dokładnie `count` są wymagane wywołania generatora.

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

template <typename C>
void print(const string& s, const C& c)
{
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

## <a name="includes"></a>łącznie

Sprawdza, czy jeden posortowany zakres zawiera wszystkie elementy zawarte w drugim posortowanym zakresie, gdzie kryterium szeregowania lub równoważności między elementami może zostać określone przez predykat binarny.

```cpp
template<class InputIterator1, class InputIterator2>
bool includes(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2);

template<class InputIterator1, class InputIterator2, class Compare>
bool includes(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool includes(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Compare>
bool includes(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    Compare pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*first1*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w pierwszym z dwóch posortowanych zakresów źródłowych do sprawdzenia, czy wszystkie elementy drugiego są zawarte w pierwszym elemencie.

*last1*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w pierwszym z dwóch posortowanych zakresów źródłowych do sprawdzenia, czy wszystkie elementy drugiego są zawarte w pierwszym elemencie.

*first2*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w drugim z dwóch kolejnych posortowanych zakresów źródłowych do sprawdzenia, czy wszystkie elementy drugiego są zawarte w pierwszym elemencie.

*last2*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w drugim z dwóch kolejnych posortowanych zakresów źródłowych do sprawdzenia, czy wszystkie elementy drugiego są zawarte w pierwszym elemencie.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje sens, w którym jeden element jest mniejszy niż inny. Predykat porównania przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="return-value"></a>Wartość zwracana

**wartość true** , jeśli pierwszy posortowany zakres zawiera wszystkie elementy w drugim posortowanym zakresie; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Innym sposobem na ustalenie tego testu jest określenie, czy drugi zakres źródłowy jest podzbiorem pierwszego zakresu źródłowego.

Posortowane zakresy źródłowe, do których istnieją odwołania, muszą być prawidłowe; wszystkie wskaźniki muszą być odwołujące się, a w każdej sekwencji Ostatnia pozycja musi być osiągalna od pierwszego przez przyrost.

Posortowane zakresy źródłowe muszą być uporządkowane jako warunek wstępny do zastosowania algorytmu, w tym takie samo porządkowanie, jak ma być używane przez algorytm do sortowania połączonych zakresów.

Zakresy źródłowe nie są modyfikowane przez algorytm `merge`.

Typy wartości iteratorów danych wejściowych muszą być mniejsze niż porównywalne do uporządkowania, tak aby w przypadku dwóch elementów można było określić, że są one równoważne (w sensie, że żaden z nich nie jest mniejszy niż drugi) lub że jeden z nich jest mniejszy od drugiego. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Dokładniej, algorytm sprawdza, czy wszystkie elementy w pierwszym posortowanym zakresie w ramach określonego predykatu binarnego mają równoważne porządkowanie do tych w drugim posortowanym zakresie.

Złożoność algorytmu jest liniowa z co najwyżej `2 * ((last1 - first1) - (last2 - first2)) - 1` porównania dla niepustych zakresów źródłowych.

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

int main()
{
    using namespace std;
    vector<int> v1a, v1b;
    vector<int>::iterator Iter1a, Iter1b;

    // Constructing vectors v1a & v1b with default less-than ordering
    int i;
    for ( i = -2 ; i <= 4 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-2 ; ii <= 3 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
            << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
            << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b );
    vector<int>::iterator Iter2a, Iter2b;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );
    v2a.pop_back( );

    cout << "Original vector v2a with range sorted by the\n "
            << "binary predicate greater is v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
            << "binary predicate greater is v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) ;
    vector<int>::iterator Iter3a, Iter3b;
    reverse (v3a.begin( ), v3a.end( ) );
    v3a.pop_back( );
    v3a.pop_back( );
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
            << "binary predicate mod_lesser is v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
            << "binary predicate mod_lesser is v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To test for inclusion under an asscending order
    // with the default binary predicate less<int>( )
    bool Result1;
    Result1 = includes ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ) );
    if ( Result1 )
        cout << "All the elements in vector v1b are "
            << "contained in vector v1a." << endl;
    else
        cout << "At least one of the elements in vector v1b "
            << "is not contained in vector v1a." << endl;

    // To test for inclusion under descending
    // order specify binary predicate greater<int>( )
    bool Result2;
    Result2 = includes ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ), greater<int>( ) );
    if ( Result2 )
        cout << "All the elements in vector v2b are "
            << "contained in vector v2a." << endl;
    else
        cout << "At least one of the elements in vector v2b "
            << "is not contained in vector v2a." << endl;

    // To test for inclusion under a user
    // defined binary predicate mod_lesser
    bool Result3;
    Result3 = includes ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), mod_lesser );
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
At least one of the elements in vector v3b is not contained under mod_lesser in vector v3a.
```

## <a name="inplace_merge"></a>inplace_merge

Łączy elementy z dwóch następujących po sobie posortowanych zakresów w pojedynczy posortowany zakres, gdzie kryterium szeregowania może być określone przez predykat binarny.

```cpp
template<class BidirectionalIterator>
void inplace_merge(
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last);

template<class BidirectionalIterator, class Compare>
void inplace_merge(
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last,
    Compare pred);

template<class ExecutionPolicy, class BidirectionalIterator>
void inplace_merge(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last);

template<class ExecutionPolicy, class BidirectionalIterator, class Compare>
void inplace_merge(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator dwukierunkowy odnoszący się do pozycji pierwszego elementu w pierwszym z dwóch kolejnych posortowanych zakresów, które mają być połączone i posortowane w pojedynczym zakresie.

\ *środkowy*
Iterator dwukierunkowy odnoszący się do pozycji pierwszego elementu w drugim z dwóch kolejnych posortowanych zakresów, które mają być połączone i posortowane w pojedynczym zakresie.

*ostatni*\
Iterator dwukierunkowy odnoszący się do pozycji jednej poza ostatnim elementem w drugim z dwóch kolejnych posortowanych zakresów, który ma zostać połączony i posortowany w pojedynczym zakresie.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje sens, w którym jeden element jest mniejszy niż inny. Predykat porównania przyjmuje dwa argumenty i zwraca **wartość true** , gdy pierwszy element jest mniejszy od drugiego elementu i w przeciwnym razie zwraca **wartość false** .

### <a name="remarks"></a>Uwagi

Sortowane kolejne zakresy, do których istnieją odwołania, muszą być prawidłowe; wszystkie wskaźniki muszą być odwołujące się, a w każdej sekwencji Ostatnia pozycja musi być osiągalna od pierwszego przez przyrost.

Posortowane kolejne zakresy muszą być ułożone jako warunek wstępny do zastosowania algorytmu `inplace_merge`, zgodnie z tą samą kolejnością, w jakiej ma być używany przez algorytm w celu sortowania połączonych zakresów. Operacja jest stabilna, ponieważ jest zachowywana względna kolejność elementów w ramach każdego zakresu. Gdy w obu zakresach źródłowych znajdują się równoważne elementy, element to pierwszy zakres poprzedza element od drugiego w połączonym zakresie.

Złożoność zależy od dostępnej pamięci, ponieważ algorytm przydziela pamięć do tymczasowego buforu. Jeśli dostępna jest wystarczająca ilość pamięci, najlepszym przypadkiem jest liniowy z `(last - first) - 1` porównaniami; Jeśli pamięć pomocnicza nie jest dostępna, najgorszy przypadek jest `N log(N)`, gdzie *N* = *ostatnią* -  *.*

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

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1, Iter2, Iter3;

    // Constructing vector v1 with default less-than ordering
    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii =-5 ; ii <= 0 ; ii++ )
    {
        v1.push_back( ii );
    }

    cout << "Original vector v1 with subranges sorted by the\n "
            << "binary predicate less than is v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // Constructing vector v2 with ranges sorted by greater
    vector<int> v2 ( v1 );
    vector<int>::iterator break2;
    break2 = find ( v2.begin( ), v2.end( ), -5 );
    sort ( v2.begin( ), break2 , greater<int>( ) );
    sort ( break2 , v2.end( ), greater<int>( ) );
    cout << "Original vector v2 with subranges sorted by the\n "
            << "binary predicate greater is v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // Constructing vector v3 with ranges sorted by mod_lesser
    vector<int> v3 ( v1 );
    vector<int>::iterator break3;
    break3 = find ( v3.begin( ), v3.end( ), -5 );
    sort ( v3.begin( ), break3 , mod_lesser );
    sort ( break3 , v3.end( ), mod_lesser );
    cout << "Original vector v3 with subranges sorted by the\n "
            << "binary predicate mod_lesser is v3 = ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")" << endl;

    vector<int>::iterator break1;
    break1 = find (v1.begin( ), v1.end( ), -5 );
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
binary predicate less than is v1 = ( 0 1 2 3 4 5 -5 -4 -3 -2 -1 0 )
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

## <a name="is_heap"></a>is_heap

Zwraca **wartość true** , jeśli elementy w określonym zakresie tworzą stertę.

```cpp
template<class RandomAccessIterator>
bool is_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
bool is_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
bool is_heap(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
bool is_heap(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator dostępu losowego, który wskazuje początek zakresu do sprawdzenia sterty.

*ostatni*\
Iterator dostępu losowego, który wskazuje koniec zakresu.

*pred*\
Warunek, który ma zostać przetestowany w celu przetestowania elementów. Predykat porównania przyjmuje dwa argumenty i zwraca **wartość true** lub **false**.

### <a name="return-value"></a>Wartość zwracana

Zwraca **wartość true** , jeśli elementy w określonym zakresie tworzą stertę, **Fałsz** , jeśli nie.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja szablonu zwraca [is_heap_until](../standard-library/algorithm-functions.md#is_heap_until)`(first , last) == last`.

Druga funkcja szablonu zwraca

`is_heap_until(first, last, pred) == last`.

## <a name="is_heap_until"></a>is_heap_until

Zwraca iterator umieszczony na pierwszym elemencie w zakresie [`first`, `last`), który nie spełnia warunku porządkowania sterty lub *kończy* , jeśli zakres tworzy stertę.

```cpp
template<class RandomAccessIterator>
RandomAccessIterator is_heap_until(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
RandomAccessIterator is_heap_until(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
RandomAccessIterator is_heap_until(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
RandomAccessIterator is_heap_until(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator dostępu losowego, który określa pierwszy element zakresu do sprawdzenia sterty.

*ostatni*\
Iterator dostępu losowego, który określa koniec zakresu do sprawdzenia sterty.

*pred*\
Predykat binarny określający ścisły, słaby warunek porządkowania, który definiuje stertę. Predykat domyślny jest `std::less<>`, gdy nie określono *pred* .

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość *Last* , jeśli określony zakres tworzy stertę lub zawiera co najmniej jeden element. W przeciwnym razie zwraca iterator dla pierwszego znalezionego elementu, który nie spełnia warunku sterty.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja szablonu zwraca ostatni `next` iteratora w `[first, last)` gdzie `[first, next)` jest stertą uporządkowaną według `std::less<>`obiektu funkcji. Jeśli odległość `last - first` jest mniejsza niż 2, funkcja zwraca wartość *Last*.

Druga funkcja szablonu zachowuje się tak samo jak pierwszy, z tą różnicą, że używa predykatu *pred* zamiast `std::less<>` jako warunek porządkowania sterty.

## <a name="is_partitioned"></a>is_partitioned

Zwraca **wartość true** , jeśli wszystkie elementy w danym zakresie, które testują **wartość true** dla warunku, są przed wszystkimi elementami, które testują **wartość false**.

```cpp
template<class InputIterator, class UnaryPredicate>
bool is_partitioned(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool is_partitioned(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator danych wejściowych, który wskazuje, gdzie rozpocznie się sprawdzanie warunku przez zakres.

*ostatni*\
Iterator danych wejściowych, który wskazuje koniec zakresu.

*pred*\
Warunek do przetestowania. Jest to zapewniane przez zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje warunek, który ma być spełniony przez wyszukiwany element. Predykat jednoargumentowy przyjmuje jeden argument i zwraca **wartość PRAWDA** lub **Fałsz**.

### <a name="return-value"></a>Wartość zwracana

Zwraca **wartość PRAWDA** , jeśli wszystkie elementy w danym zakresie, które testują **wartość true** dla warunku, są przed wszystkimi elementami, które testują **wartość false**, i w przeciwnym razie zwraca **wartość false**.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca **wartość true** tylko wtedy, gdy wszystkie elementy w `[first, last)` są podzielone na partycje przez *pred*; oznacza to, że wszystkie elementy `X` w `[first, last)`, dla których `pred (X)` jest spełniony, zanim wszystkie elementy `Y`, dla których `pred (Y)` ma **wartość false**.

## <a name="is_permutation"></a>is_permutation

Zwraca wartość true, jeśli oba zakresy zawierają te same elementy, niezależnie od tego, czy elementy znajdują się w tej samej kolejności. Używaj przeciążeń podwójnego zakresu w kodzie języka C++ 14, ponieważ przeciążenia, które pobierają tylko jeden iterator dla drugiego zakresu, nie wykryją różnic, jeśli drugi zakres jest dłuższy niż pierwszy zakres i spowoduje niezdefiniowane zachowanie, jeśli drugi zakres jest krótszy niż pierwszy zakres.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    BinaryPredicate Pred);

// C++14
template<class ForwardIterator1, class ForwardIterator2>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*first1*\
Iterator do przodu, który odwołuje się do pierwszego elementu zakresu.

*last1*\
Iterator do przodu, który odwołuje się do jednej poza ostatnim elementem zakresu.

*first2*\
Iterator do przodu, który odwołuje się do pierwszego elementu drugiego zakresu, używany do porównania.

*last2*\
Iterator do przodu, który odwołuje się do jednego z nich poza ostatnim elementem drugiego zakresu, używany do porównania.

*pred*\
Predykat, który testuje dla równoważności i zwraca wartość **logiczną**.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli zakresy można zmienić tak, aby były takie same, jak w przypadku predykatu komparator; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

w najgorszym przypadku `is_permutation` ma złożoność kwadratową.

W pierwszej funkcji szablonu założono, że istnieje wiele elementów w zakresie zaczynającym się od *First2* , tak jak w zakresie wydzielonym przez `[first1, last1)`. Jeśli w drugim zakresie znajduje się więcej elementów, są one ignorowane; w przypadku mniej, niezdefiniowane zachowanie zostanie wykonane. Trzecia funkcja szablonu (C++ 14 i nowsze) nie przyjmuje tego założeń. Oba zwracają **wartość true** tylko wtedy, gdy dla każdego elementu X w zakresie wyznaczono przez `[first1, last1)` istnieje tyle elementów Y w tym samym zakresie, dla których x = = Y, tak jak w zakresie rozpoczynającym się o *First2* lub `[first2, last2)`. W tym miejscu `operator==` musi wykonać porównanie parowania między operandami.

Drugie i czwarte funkcje szablonu zachowują się tak samo, z tą różnicą, że zastępują `operator==(X, Y)` z `Pred(X, Y)`. Aby zachować prawidłowe działanie, predykat musi być symetryczny, zwrotny i przechodni.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać `is_permutation`:

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

## <a name="is_sorted"></a>is_sorted

Zwraca **wartość true** , jeśli elementy w określonym zakresie są sortowane według kolejności.

```cpp
template<class ForwardIterator>
bool is_sorted(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class Compare>
bool is_sorted(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
bool is_sorted(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
bool is_sorted(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator do przodu, który wskazuje, gdzie rozpoczyna się zakres do sprawdzenia.

*ostatni*\
Iterator do przodu, który wskazuje koniec zakresu.

*pred*\
Warunek do przetestowania w celu określenia kolejności między dwoma elementami. Predykat porównania przyjmuje dwa argumenty i zwraca **wartość true** lub **false**. Wykonuje to to samo zadanie co `operator<`.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja szablonu zwraca [is_sorted_until](#is_sorted_until)`( first, last ) == last`. Funkcja `operator<` wykonuje porównanie kolejności.

Druga funkcja szablonu zwraca `is_sorted_until( first, last , pred ) == last`. Funkcja predykatu *pred* wykonuje porównanie kolejności.

## <a name="is_sorted_until"></a>is_sorted_until

Zwraca `ForwardIterator`, który jest ustawiony do ostatniego elementu, który jest sortowany w kolejności od określonego zakresu.

Druga wersja pozwala dostarczyć obiekt funkcji porównywania zwraca **wartość PRAWDA** , jeśli dwa podano elementy w kolejności sortowania, a w przeciwnym razie **wartość false** .

```cpp
template<class ForwardIterator>
ForwardIterator is_sorted_until(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class Compare>
ForwardIterator is_sorted_until(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator is_sorted_until(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
ForwardIterator is_sorted_until(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator do przodu, który wskazuje, gdzie zaczyna się zakres do sprawdzenia.

*ostatni*\
Iterator do przodu, który wskazuje koniec zakresu.

*pred*\
Warunek do przetestowania w celu określenia kolejności między dwoma elementami. Predykat porównania przyjmuje dwa argumenty i zwraca **wartość true** lub **false**.

### <a name="return-value"></a>Wartość zwracana

Zwraca `ForwardIterator` ustawiany jako ostatni element w sortowanej kolejności. Posortowana Sekwencja zaczyna się od *pierwszego*.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja szablonu zwraca ostatni `next` iteratora w `[first, last]`, tak że `[first, next)` jest sortowaną sekwencją uporządkowaną według `operator<`. Jeśli `distance()` jest mniejsza niż 2, funkcja zwraca wartość *Last*.

Druga funkcja szablonu zachowuje się tak samo, z tą różnicą, że zastępuje `operator<(X, Y)` z `pred(X, Y)`.

## <a name="iter_swap"></a>iter_swap

Wymienia dwie wartości, do których odnosi się para określonych iteratorów.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
void iter_swap( ForwardIterator1 left, ForwardIterator2 right );
```

### <a name="parameters"></a>Parametry

\ *lewo*
Jeden z iteratorów do przodu, którego wartość ma być wymieniana.

*prawa*\
Drugi iterator do przodu, którego wartość ma być wymieniana.

### <a name="remarks"></a>Uwagi

`swap` powinna być używana w preferencjach do **iter_swap**, która została uwzględniona C++ w standardzie w celu zapewnienia zgodności z poprzednimi wersjami. Jeśli `Fit1` i `Fit2` są iteratorami progresywnymi, `iter_swap( Fit1, Fit2 )`, jest równoznaczne z `swap( *Fit1, *Fit2 )`.

Typy wartości iteratorów przekazujących dane wejściowe muszą mieć tę samą wartość.

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

int main()
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
    iter_swap ( deq1.begin( ), --deq1.end( ) );

    cout << "The deque of CInts with first & last elements swapped is:\n deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    // Swapping back first and last elements with swap
    swap ( *deq1.begin( ), *(deq1.end( ) -1 ) );

    cout << "The deque of CInts with first & last elements swapped back is:\n deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    // Swapping a vector element with a deque element
    vector<int> v1;
    vector<int>::iterator Iter1;
    deque<int> deq2;
    deque<int>::iterator d2_Iter;

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

    iter_swap ( v1.begin( ), deq2.begin( ) );

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

## <a name="lexicographical_compare"></a>lexicographical_compare

Porównuje dwie sekwencje element po elemencie, aby określić, która z nich jest mniejsza.

```cpp
template<class InputIterator1, class InputIterator2>
bool lexicographical_compare(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2 );

template<class InputIterator1, class InputIterator2, class Compare>
bool lexicographical_compare(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool lexicographical_compare(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Compare>
bool lexicographical_compare(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    Compare pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*first1*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w pierwszym zakresie, który ma zostać porównany.

*last1*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w pierwszym zakresie, który ma zostać porównany.

*first2*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w drugim zakresie, który ma zostać porównany.

*last2*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w drugim zakresie, który ma zostać porównany.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje sens, w którym jeden element jest mniejszy niż inny. Predykat porównania przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli pierwszy zakres jest lexicographically mniejszy niż drugi zakres; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Porównanie lexicographical między sekwencjami porównuje je z elementem do momentu:

- Znajduje dwa odpowiadające im elementy, a wynik porównania jest traktowany jako wynik porównania między sekwencjami.

- Nie znaleziono żadnych nierówności, ale jedna sekwencja ma więcej elementów niż pozostałe, a krótsza sekwencja jest uznawana za mniejszą niż dłuższa.

- Nie znaleziono żadnych nierówności i sekwencje mają taką samą liczbę elementów, dlatego sekwencje są równe, a wynik porównania ma **wartość false**.

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

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

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

## <a name="lower_bound"></a>lower_bound

Znajduje pozycję pierwszego elementu w uporządkowanym zakresie, który ma wartość większą niż lub równoważną określonej wartości, gdzie kryterium szeregowania może być określone przez predykat binarny.

```cpp
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
    BinaryPredicate pred );
```

### <a name="parameters"></a>Parametry

*pierwszy*\
Iterator do przodu, odnoszący się do pozycji pierwszego elementu w zakresie, który ma być przeszukiwany.

*ostatni*\
Iterator do przodu, odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma być przeszukiwany.

\ *wartości*
Wartość, której Pierwsza pozycja lub możliwe pierwsze miejsce są wyszukiwane w zakresie uporządkowanym.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje sens, w którym jeden element jest mniejszy niż inny. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu na pozycji pierwszego elementu w uporządkowanym zakresie o wartości, która jest większa lub równa określonej wartości, gdzie równoważność jest określona przy użyciu predykatu binarnego.

### <a name="remarks"></a>Uwagi

Posortowany zakres źródłowy musi być prawidłowy; wszystkie Iteratory muszą być odwołujące się, a w sekwencji Ostatnia pozycja musi być osiągalna od pierwszej przez przyrost.

Sortowany zakres jest warunkiem wstępnym używania `lower_bound` i gdzie kolejność jest taka sama jak określona przez Predykat binarny.

Zakres nie jest modyfikowany przez algorytm `lower_bound`.

Typy wartości iteratorów do przodu muszą być mniejsze niż porównywalne do uporządkowania, tak że, w przypadku dwóch elementów, można określić, że są one równoważne (w sensie, że żaden z nich nie jest mniejszy od drugiego) lub że jeden z nich jest mniejszy od drugiego. Powoduje to porządkowanie między nierównoważnymi elementami

Złożoność algorytmu jest logarytmiczna dla iteratorów dostępu losowego i liniowego w przeciwnym razie z liczbą kroków proporcjonalną do (`last - first`).

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

int main()
{
    using namespace std;

    vector<int> v1;
    // Constructing vector v1 with default less-than ordering
    for ( auto i = -1 ; i <= 4 ; ++i )
    {
        v1.push_back( i );
    }

    for ( auto ii =-3 ; ii <= 0 ; ++ii )
    {
        v1.push_back( ii );
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
        << "binary predicate mod_lesser is v3 = ( " ;
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

    // lower_bound of 3 in v3 with the binary predicate mod_lesser
    Result = lower_bound(v3.begin(), v3.end(), 3, mod_lesser);
    cout << "The lower_bound in v3 for the element with a value of 3 is: "
        << *Result << "." << endl;
}
```

## <a name="make_heap"></a>make_heap

Konwertuje elementy z określonego zakresu na stertę, w której pierwszy element jest największy i dla której kryterium sortowania może być określone przez predykat binarny.

```cpp
template<class RandomAccessIterator>
void make_heap(
    RandomAccessIterator first,
    RandomAccessIterator last );

template<class RandomAccessIterator, class BinaryPredicate>
void make_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate pred );
```

### <a name="parameters"></a>Parametry

*pierwszy*\
Iterator dostępu swobodnego odnoszący się do pozycji pierwszego elementu w zakresie, który ma zostać przekonwertowany na stos.

*ostatni*\
Iterator dostępu swobodnego odnoszący się do jednej z elementów znajdujących się poza ostatnim elementem w zakresie, który ma zostać przekonwertowany na stos.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje sens, w którym jeden element jest mniejszy niż inny. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="remarks"></a>Uwagi

Sterty mają dwie właściwości:

- Pierwszy element jest zawsze największy.

- Elementy mogą być dodawane lub usuwane w czasie logarytmu.

Sterty są idealnym sposobem implementacji kolejek priorytetów i są używane w implementacji adaptera [priority_queue](../standard-library/priority-queue-class.md)biblioteki C++ standardowej.

Złożoność jest liniowa, wymagając `3 * (last - first)` porównania.

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
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

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

## <a name="max"></a>Maksymalny

Porównuje dwa obiekty i zwraca większy z nich, gdzie kryterium sortowania może być określone przez predykat binarny.

```cpp
template<class Type>
constexpr Type& max(
    const Type& left,
    const Type& right);
template<class Type, class Pr>
constexpr Type& max(
    const Type& left,
    const Type& right,
    BinaryPredicate pred);
template<class Type>
constexpr Type& max (
    initializer_list<Type> ilist);
template<class Type, class Pr>
constexpr Type& max(
    initializer_list<Type> ilist,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Pierwszy z dwóch obiektów, które są porównywane.

*prawa*\
Drugi z dwóch obiektów, które są porównywane.

*pred*\
Predykat binarny służący do porównywania dwóch obiektów.

\ *listy*
Lista inicjatorów zawierająca obiekty, które mają być porównane.

### <a name="return-value"></a>Wartość zwracana

Większy z dwóch obiektów, chyba że ani nie jest większy; w takim przypadku zwraca pierwsze z dwóch obiektów. W przypadku initializer_list zwraca największy z obiektów na liście.

### <a name="remarks"></a>Uwagi

Algorytm `max` jest nietypowy w przypadku, gdy obiekty są przenoszone jako parametry. Większość C++ algorytmów biblioteki standardowej operuje na zakresie elementów, których pozycja jest określona przez Iteratory przekazaną jako parametry. Jeśli potrzebujesz funkcji, która działa w zakresie elementów, użyj [max_element](../standard-library/algorithm-functions.md#max_element) zamiast tego. Program Visual Studio 2017 włącza wartość **constexpr** dla przeciążenia, które pobierają initializer_list.

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

int main()
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
    vector<int> v1, v2, v3, v4, v5;
    vector<int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;

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
Comparing the members of an initializer_list...The member with the greater value is: 6The integer with the greater absolute value is: -7
s1 = ( CInt( 1 ), CInt( 2 ) ).
s2 = ( CInt( 2 ), CInt( 3 ) ).
s3 = max ( s1, s2 ) = ( CInt( 2 ), CInt( 3 ) ).

Vector v1 is ( 0 1 2 ).
Vector v2 is ( 0 1 2 ).
Vector v3 is ( 0 2 4 ).
Vector v4 = max (v1,v2) is ( 0 1 2 ).
Vector v5 = max (v1,v3) is ( 0 2 4 ).
```

## <a name="max_element"></a>max_element

Znajduje pierwsze wystąpienie największego elementu w określonym zakresie, gdzie kryterium sortowania może być określone przez predykat binarny.

```cpp
template<class ForwardIterator>
constexpr ForwardIterator max_element(
    ForwardIterator first,
    ForwardIterator last );

template<class ForwardIterator, class Compare>
constexpr ForwardIterator max_element(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator max_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
ForwardIterator max_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator do przodu, odnoszący się do pozycji pierwszego elementu w zakresie, który ma być przeszukiwany dla największego elementu.

*ostatni*\
Iterator do przodu, odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma być przeszukiwany dla największego elementu.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje sens, w którym jeden element jest mniejszy niż inny. Predykat porównania przyjmuje dwa argumenty i zwraca **wartość true** , gdy pierwszy element jest mniejszy od drugiego elementu i w przeciwnym razie zwraca **wartość false** .

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, odnoszący się do pozycji pierwszego wystąpienia największego elementu w przeszukiwanym zakresie.

### <a name="remarks"></a>Uwagi

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się i w każdej sekwencji, która jest dostępna od pierwszej do przyrostu.

Złożoność jest liniowa: porównania `(last - first) - 1` są wymagane dla niepustego zakresu.

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

int main()
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

    s1_R1_Iter = max_element ( s1.begin( ), s1.end( ) );

    cout << "The largest element in s1 is: " << *s1_R1_Iter << endl;
    cout << endl;

    // Searching a vector with elements of type int for the maximum
    // element under default less than & mod_lesser binary predicates
    vector<int> v1;
    vector<int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;

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

    v1_R1_Iter = max_element ( v1.begin( ), v1.end( ) );
    v1_R2_Iter = max_element ( v1.begin( ), v1.end( ), mod_lesser);

    cout << "The largest element in v1 is: " << *v1_R1_Iter << endl;
    cout << "The largest element in v1 under the mod_lesser"
            << "\n binary predicate is: " << *v1_R2_Iter << endl;
}
```

## <a name="merge"></a>połączenie

Łączy wszystkie elementy z dwóch posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium sortowania może być określone przez Predykat binarny.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator merge(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator merge(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator merge(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator merge(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*first1*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w pierwszym z dwóch posortowanych zakresów źródłowych do połączenia i sortowania w pojedynczym zakresie.

*last1*\
Iterator danych wejściowych odnoszący się do pozycji jednego z ostatniego elementu w pierwszym z dwóch posortowanych zakresów źródłowych do połączenia i posortowania w pojedynczym zakresie.

*first2*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w drugim z dwóch kolejnych posortowanych zakresów źródłowych do połączenia i sortowania w pojedynczym zakresie.

*last2*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w drugim z dwóch kolejnych posortowanych zakresów źródłowych do łączenia i sortowania w pojedynczym zakresie.

\ *wyniku*
Iterator danych wyjściowych odnoszący się do pozycji pierwszego elementu w zakresie docelowym, w którym dwa zakresy źródłowe mają być połączone w pojedynczy posortowany zakres.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje sens, w którym jeden element jest mniejszy niż inny. Predykat porównania przyjmuje dwa argumenty i zwraca **wartość true** , gdy pierwszy element jest mniejszy od drugiego elementu i w przeciwnym razie zwraca **wartość false** .

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych odnoszący się do położenia jednej poza ostatnim elementem w sortowanym zakresie docelowym.

### <a name="remarks"></a>Uwagi

Posortowane zakresy źródłowe, do których istnieją odwołania, muszą być prawidłowe; wszystkie wskaźniki muszą być odwołujące się, a w każdej sekwencji Ostatnia pozycja musi być osiągalna od pierwszej przez przyrost.

Zakres docelowy nie powinien nakładać się na żaden z zakresów źródłowych i powinien być wystarczająco duży, aby zawierał zakres docelowy.

Posortowane zakresy źródłowe muszą być uporządkowane jako warunek wstępny do zastosowania algorytmu `merge`, zgodnie z tą samą kolejnością, w jakiej ma być używana przez algorytm w celu sortowania połączonych zakresów.

Operacja jest stabilna, ponieważ względna kolejność elementów w każdym zakresie jest zachowywana w zakresie docelowym. Zakresy źródłowe nie są modyfikowane przez algorytm `merge`.

Typy wartości iteratorów danych wejściowych muszą być mniejsze niż porównywalne do uporządkowania, tak aby w przypadku dwóch elementów można było określić, że są one równoważne (w sensie, że żaden z nich nie jest mniejszy niż drugi) lub że jeden z nich jest mniejszy od drugiego. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Gdy w obu zakresach źródłowych znajdują się równoważne elementy, elementy z pierwszego zakresu poprzedzają elementy z drugiego zakresu źródłowego w zakresie docelowym.

Złożoność algorytmu jest liniowa z co najwyżej `(last1 - first1) - (last2 - first2) - 1` porównaniami.

[Klasa list](../standard-library/list-class.md) udostępnia funkcję członkowską "merge" do scalania elementów dwóch list.

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
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1;

    // Constructing vector v1a and v1b with default less than ordering
    int i;
    for ( i = 0 ; i <= 5 ; i++ )
        v1a.push_back( i );

    int ii;
    for ( ii =-5 ; ii <= 0 ; ii++ )
        v1b.push_back( ii );

    cout << "Original vector v1a with range sorted by the\n "
            << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
            << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vector v2 with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
            << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
            << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vector v3 with ranges sorted by mod_lesser
    vector<int> v3a( v1a ), v3b( v1b ) , v3( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
            << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
            << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To merge inplace in ascending order with default binary
    // predicate less<int>( )
    merge ( v1a.begin( ), v1a.end( ), v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Merged inplace with default order,\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To merge inplace in descending order, specify binary
    // predicate greater<int>( )
    merge ( v2a.begin( ), v2a.end( ), v2b.begin( ), v2b.end( ),
        v2.begin( ), greater<int>( ) );
    cout << "Merged inplace with binary predicate greater specified,\n "
            << "vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // Applying A user-defined (UD) binary predicate mod_lesser
    merge ( v3a.begin( ), v3a.end( ), v3b.begin( ), v3b.end( ),
        v3.begin( ), mod_lesser );
    cout << "Merged inplace with binary predicate mod_lesser specified,\n "
            << "vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="min"></a>długości

Porównuje dwa obiekty i zwraca mniejszy z nich, gdzie kryterium sortowania może być określone przez predykat binarny.

```cpp
template<class Type>
constexpr const Type& min(
    const Type& left,
    const Type& right);

template<class Type, class Pr>
constexpr const Type& min(
    const Type& left,
    const Type& right,
    BinaryPredicate pred);

template<class Type>
constexpr Type min(
    initializer_list<Type> ilist);

template<class Type, class Pr>
constexpr Type min(
    initializer_list<Type> ilist,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Pierwszy z dwóch obiektów, które są porównywane.

*prawa*\
Drugi z dwóch obiektów, które są porównywane.

*pred*\
Predykat binarny służący do porównywania dwóch obiektów.

\ *listy*
`initializer_list`, który zawiera elementy członkowskie, które mają być porównane.

### <a name="return-value"></a>Wartość zwracana

Dwa obiekty, chyba że ani nie są mniejsze; w takim przypadku zwraca pierwsze z dwóch obiektów. W przypadku `initializer_list`zwraca najmniejszą liczbę obiektów na liście.

### <a name="remarks"></a>Uwagi

Algorytm `min` jest nietypowy w przypadku, gdy obiekty są przenoszone jako parametry. Większość C++ algorytmów biblioteki standardowej operuje na zakresie elementów, których pozycja jest określona przez Iteratory przekazaną jako parametry. Jeśli potrzebujesz funkcji korzystającej z zakresu elementów, użyj [min_element](../standard-library/algorithm-functions.md#min_element). Funkcja [constexpr](../cpp/constexpr-cpp.md) została włączona dla przeciążeń `initializer_list` w programie Visual Studio 2017.

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

int main()
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
    vector<int> v1, v2, v3, v4, v5;
    vector<int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;

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

## <a name="min_element"></a>min_element

Znajduje pierwsze wystąpienie najmniejszego elementu w określonym zakresie, gdzie kryterium sortowania może być określone przez predykat binarny.

```cpp
template<class ForwardIterator>
constexpr ForwardIterator min_element(
    ForwardIterator first,
    ForwardIterator last );

template<class ForwardIterator, class Compare>
constexpr ForwardIterator min_element(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator min_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
ForwardIterator min_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator do przodu, odnoszący się do pozycji pierwszego elementu w zakresie, który ma być przeszukiwany dla najmniejszego elementu.

*ostatni*\
Iterator do przodu, odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma być przeszukiwany dla najmniejszego elementu.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje sens, w którym jeden element jest mniejszy niż inny. Predykat porównania przyjmuje dwa argumenty i zwraca **wartość true** , gdy pierwszy element jest mniejszy od drugiego elementu i w przeciwnym razie zwraca **wartość false** .

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, odnoszący się do pozycji pierwszego wystąpienia najmniejszego elementu w przeszukiwanym zakresie.

### <a name="remarks"></a>Uwagi

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się i w każdej sekwencji, która jest dostępna od pierwszej do przyrostu.

Złożoność jest liniowa: porównania `(last - first) - 1` są wymagane dla niepustego zakresu.

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

    s1_R1_Iter = min_element ( s1.begin( ), s1.end( ) );

    cout << "The smallest element in s1 is: " << *s1_R1_Iter << endl;
    cout << endl;

    // Searching a vector with elements of type int for the maximum
    // element under default less than & mod_lesser binary predicates
    vector<int> v1;
    vector<int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;

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

    v1_R1_Iter = min_element ( v1.begin( ), v1.end( ) );
    v1_R2_Iter = min_element ( v1.begin( ), v1.end( ), mod_lesser);

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

## <a name="minmax_element"></a>minmax_element

Wykonuje działania wykonywane przez `min_element` i `max_element` w jednym wywołaniu.

```cpp
template<class ForwardIterator>
constexpr pair<ForwardIterator, ForwardIterator> minmax_element(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class Compare>
constexpr pair<ForwardIterator, ForwardIterator> minmax_element(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
pair<ForwardIterator, ForwardIterator> minmax_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
pair<ForwardIterator, ForwardIterator> minmax_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator do przodu, który wskazuje początek zakresu.

*ostatni*\
Iterator do przodu, który wskazuje koniec zakresu.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje sens, w którym jeden element jest mniejszy niż inny. Predykat porównania przyjmuje dwa argumenty i zwraca **wartość true** , jeśli pierwszy jest mniejszy niż drugi i w przeciwnym razie zwraca **wartość false** .

### <a name="return-value"></a>Wartość zwracana

Zwraca

`pair<ForwardIterator, ForwardIterator>( min_element(first, last), max_element(first, last))`.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja szablonu zwraca

`pair<ForwardIterator,ForwardIterator>(min_element(first,last), max_element(first,last))`.

Druga funkcja szablonu zachowuje się tak samo, z tą różnicą, że zastępuje `operator<(X, Y)` z `pred(X, Y)`.

Jeśli sekwencja nie jest pusta, funkcja wykonuje co najwyżej `3 * (last - first - 1) / 2` porównania.

## <a name="minmax"></a>MinMax

Porównuje dwa parametry wejściowe i zwraca je jako parę, w kolejności od najmniejszej do wyższej.

```cpp
template<class Type>
constexpr pair<const Type&, const Type&> minmax(
    const Type& left,
    const Type& right);

template<class Type, class BinaryPredicate>
constexpr pair<const Type&, const Type&> minmax(
    const Type& left,
    const Type& right,
    BinaryPredicate pred);

template<class Type>
constexpr pair<Type&, Type&> minmax(
    initializer_list<Type> ilist);

template<class Type, class BinaryPredicate>
constexpr pair<Type&, Type&> minmax(
    initializer_list<Type> ilist,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Pierwszy z dwóch obiektów, które są porównywane.

*prawa*\
Drugi z dwóch obiektów, które są porównywane.

*pred*\
Predykat binarny służący do porównywania dwóch obiektów.

\ *listy*
`initializer_list`, który zawiera elementy członkowskie, które mają być porównane.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja szablonu zwraca `pair<const Type&, const Type&>( right, left )`, jeśli wartość *Right* jest mniejsza od *lewej*. W przeciwnym razie zwraca `pair<const Type&, const Type&>( left, right )`.

Druga funkcja członkowska zwraca parę, w której pierwszy element jest mniejszy, a drugi jest większy w porównaniu z *pred*predykatu.

Pozostałe funkcje szablonu zachowują się tak samo, z tą różnicą, że zastępują *lewe* i *prawe* parametry z *listą*.

Funkcja wykonuje dokładnie jedno porównanie.

## <a name="mismatch"></a>nieodpowiedni

Porównuje dwa zakresy elementów według elementu i lokalizuje pierwsze miejsce, w którym występuje różnica.

Używaj przeciążeń podwójnego zakresu w kodzie języka C++ 14, ponieważ przeciążenia, które pobierają tylko jeden iterator dla drugiego zakresu, nie wykryją różnic, jeśli drugi zakres jest dłuższy niż pierwszy zakres i spowoduje niezdefiniowane zachowanie, jeśli drugi zakres jest krótszy niż pierwszy zakres.

```cpp
template<class InputIterator1, class InputIterator2>
pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2 );

template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    BinaryPredicate pred );

//C++14
template<class InputIterator1, class InputIterator2>
pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2 );

template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    BinaryPredicate pred);

//C++17
template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*first1*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w pierwszym zakresie do przetestowania.

*last1*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem z pierwszego zakresu do przetestowania.

*first2*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w drugim zakresie, który ma zostać przetestowany.

*last2*\
Iterator danych wejściowych odnoszący się do pozycji jednego ostatniego elementu z drugiego zakresu, który ma zostać przetestowany.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który porównuje bieżące elementy w każdym zakresie i określa, czy są one równoważne. Zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="return-value"></a>Wartość zwracana

Para iteratorów odwołująca się do pozycji niezgodności w dwóch zakresach, pierwszy składnik iterator do pozycji w pierwszym zakresie i drugi iterator składnika do pozycji w drugim zakresie. Jeśli nie ma różnicy między elementami w porównywanych zakresach lub jeśli Predykat binarny w drugiej wersji jest spełniony przez wszystkie pary elementów z dwóch zakresów, a następnie pierwszy punkt końcowy wskazuje na pozycję, która znajduje się po ostatnim elemencie w pierwszym zakres i drugi iterator składnika, aby pomieścić jeden poza ostatnim elementem przetestowanym w drugim zakresie.

### <a name="remarks"></a>Uwagi

W pierwszej funkcji szablonu założono, że istnieje wiele elementów w zakresie zaczynającym się od First2, tak jak w zakresie wydzielonym przez [FIRST1, last1). Jeśli w drugim zakresie występuje więcej, są one ignorowane; Jeśli jest mniej, to zachowanie zostanie niezdefiniowane.

Zakres, który ma być przeszukiwany, musi być prawidłowy; wszystkie Iteratory muszą być odwołujące się, a ostatnia pozycja jest dostępna od pierwszego do przyrostu.

Stopień złożoności algorytmu jest liniowy w liczbie elementów zawartych w krótszym zakresie.

Predykat zdefiniowany przez użytkownika nie jest wymagany do nakładania relacji równoważności, która jest symetryczna, zwrotna i przechodnia między operandami.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia niezgodności. Przeciążenie C++ 03 jest wyświetlane tylko w celu zademonstrowania, w jaki sposób może wygenerować nieoczekiwany wynik.

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
```

```Output
C++03: vec_1 and vec_2 are a mismatch: false
C++14: vec_1 and vec_2: mismatch. Left iterator at end right iterator at 30
C++14 vec_1 v. vec_2 modified: mismatch. Left iterator at 15 right iterator at 42
C++14 vec_3 v. vec_4 with pred: match.
C++14 vec_3 v. modified vec_4 with pred: mismatch. Left iterator at 60 right iterator at 31
C++14: vec_1 and list_1 are a mismatch: false
Press a key
```

## <a name="alg_move"></a>&lt;alg&gt; przenoszenia

Przenieś elementy związane z określonym zakresem.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator move(
    InputIterator first,
    InputIterator last,
    OutputIterator dest);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 move(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator danych wejściowych wskazujący, gdzie ma być uruchamiany zakres elementów do przeniesienia.

*ostatni*\
Iterator danych wejściowych, który wskazuje koniec zakresu elementów do przeniesienia.

\ miejsca *docelowego*
Iterator danych wyjściowych, który ma zawierać przeniesione elementy.

### <a name="remarks"></a>Uwagi

Funkcja szablonu oblicza `*(dest + N) = move(*(first + N))` raz dla każdego `N` w zakresie `[0, last - first)`, dla ściśle rosnących wartości `N`, zaczynając od najniższej wartości. Następnie zwraca `dest + N`. Jeśli `dest` i *najpierw* wyznaczać regiony magazynu, miejscem *docelowy* nie może być w zakresie `[first, last)`.

## <a name="move_backward"></a>move_backward

Przenosi elementy jednego iteratora do drugiego. Przeniesienie rozpoczyna się od ostatniego elementu w określonym zakresie, a kończy się na pierwszym elemencie w tym zakresie.

```cpp
template<class BidirectionalIterator1, class BidirectionalIterator2>
BidirectionalIterator2 move_backward(
    BidirectionalIterator1 first,
    BidirectionalIterator1 last,
    BidirectionalIterator2 destEnd);
```

### <a name="parameters"></a>Parametry

*pierwszy*\
Iterator, który wskazuje początek zakresu, z którego można przenieść elementy.

*ostatni*\
Iterator, który wskazuje koniec zakresu, z którego można przenieść elementy. Ten element nie jest przenoszony.

*destEnd*\
Iterator dwukierunkowy odnoszący się do pierwszej pozycji po elemencie końcowym w zakresie docelowym.

### <a name="remarks"></a>Uwagi

Funkcja szablonu oblicza `*(destEnd - N - 1) = move(*(last - N - 1))` raz dla każdego `N` w zakresie `[0, last - first)`, dla ściśle rosnących wartości `N`, zaczynając od najniższej wartości. Następnie zwraca `destEnd - (last - first)`. Jeśli *destEnd* i *pierwszy* wyznaczysz regiony magazynu, *destEnd* nie może znajdować się w zakresie `[first, last)`.

`move` i `move_backward` są funkcjonalnie równoważne z użyciem `copy` i `copy_backward` z iteratorem przenoszenia.

## <a name="next_permutation"></a>next_permutation

Zmienia kolejność elementów w zakresie, tak że oryginalna kolejność jest zastąpiona przez leksykograficznie kolejną większą permutację, o ile takowa istnieje, gdzie sens „kolejna” może być określony przez predykat binarny.

```cpp
template<class BidirectionalIterator>
bool next_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class BidirectionalIterator, class BinaryPredicate>
bool next_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*pierwszy*\
Iterator dwukierunkowy wskazujący na pozycję pierwszego elementu w zakresie, który ma być permuted.

*ostatni*\
Iterator dwukierunkowy wskazujący na pozycję jeden poza ostatnim elementem w zakresie, który ma być permuted.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje kryterium porównania do spełnienia przez kolejne elementy w kolejności. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli istnieje lexicographically Następna Permutacja i zastąpiła pierwotna kolejność zakresu; w przeciwnym razie **wartość false**, w takim przypadku kolejność jest przekształcana do lexicographically najmniejszej permutacji.

### <a name="remarks"></a>Uwagi

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Domyślny Predykat binarny jest mniejszy niż, a elementy w zakresie muszą być mniejsze niż porównywalne, aby upewnić się, że następna Permutacja jest dobrze zdefiniowana.

Złożoność jest liniowa z maksymalnie `(last - first) / 2` wymian.

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
    CInt( int n = 0 ) : m_nVal( n ) {}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ) {}
    CInt& operator=( const CInt& rhs ) {m_nVal =
        rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        { return ( m_nVal < rhs.m_nVal ); }
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

    deq1Result = next_permutation ( deq1.begin( ), deq1.end( ) );

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
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = -3 ; i <= 3 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    next_permutation ( v1.begin( ), v1.end( ), mod_lesser );

    cout << "After the first next_permutation, vector v1 is:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= 5 ) {
        next_permutation ( v1.begin( ), v1.end( ), mod_lesser );
        cout << "After another next_permutation of vector v1,\n v1 =   ( " ;
        for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ;Iter1 ++ )
            cout << *Iter1 << " ";
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

## <a name="nth_element"></a>nth_element

Dzieli zakres elementów, poprawnie lokalizując *n*-ty element sekwencji w zakresie, tak aby wszystkie elementy przed nim były mniejsze lub równe, a wszystkie elementy, które podążają w sekwencji, są większe lub równe.

```cpp
template<class RandomAccessIterator>
void nth_element(
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void nth_element(
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
void nth_element(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void nth_element(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator dostępu swobodnego odnoszący się do pozycji pierwszego elementu w zakresie, który ma zostać podzielony na partycje.

*n*\
Iterator dostępu swobodnego odnoszący się do pozycji elementu, który ma być prawidłowo uporządkowany na granicy partycji.

*ostatni*\
Iterator dostępu swobodnego odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma zostać podzielony na partycje.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje kryterium porównania do spełnienia przez kolejne elementy w kolejności. Predykat porównania przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="remarks"></a>Uwagi

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Algorytm `nth_element` nie gwarantuje, że elementy w podzakresach są sortowane po obu stronach *tego elementu*. Powoduje to mniejsze gwarancje niż `partial_sort`, które porządkują elementy w zakresie poniżej wybranego elementu i mogą być używane jako szybsza alternatywa dla `partial_sort`, gdy kolejność dolnego zakresu nie jest wymagana.

Elementy są równoważne, ale niekoniecznie równe, jeśli nie są mniejsze od siebie.

Średnia złożoności sortowania jest liniowa w odniesieniu do *ostatniej pierwszej*.

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
    vector<int> v1;
    vector<int>::iterator Iter1;

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

## <a name="none_of"></a>none_of

Zwraca **wartość PRAWDA** , jeśli warunek nigdy nie występuje między elementami w danym zakresie.

```cpp
template<class InputIterator, class UnaryPredicate>
bool none_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool none_of(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator danych wejściowych, który wskazuje, gdzie rozpocząć sprawdzanie zakresu elementów dla warunku.

*ostatni*\
Iterator danych wejściowych, który wskazuje koniec zakresu elementów.

*pred*\
Warunek do przetestowania. Jest to zapewniane przez zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje warunek. Predykat jednoargumentowy przyjmuje jeden argument i zwraca **wartość PRAWDA** lub **Fałsz**.

### <a name="return-value"></a>Wartość zwracana

Zwraca **wartość true** , jeśli warunek nie jest wykrywany co najmniej raz we wskazanym zakresie, i **wartość false** , jeśli warunek zostanie wykryty.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca **wartość true** tylko wtedy, gdy dla niektórych `N` w zakresie `[0, last - first)`, predykat `pred(*(first + N))` ma zawsze **wartość false**.

## <a name="partial_sort"></a>partial_sort

Rozmieszcza określoną liczbę mniejszych elementów w zakresie w niemalejącej kolejności, lub według kryteriów sortowania określonych przez binarny predykat.

```cpp
template<class RandomAccessIterator>
void partial_sort(
    RandomAccessIterator first,
    RandomAccessIterator sortEnd,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void partial_sort(
    RandomAccessIterator first,
    RandomAccessIterator sortEnd,
    RandomAccessIterator last
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
void partial_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator middle,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void partial_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator middle,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator dostępu swobodnego odnoszący się do pozycji pierwszego elementu w zakresie, który ma zostać posortowany.

*sortEnd*\
Iterator dostępu swobodnego, odnoszący się do pozycji jednej poza ostatnim elementem w podzakresie, który ma zostać posortowany.

*ostatni*\
Iterator dostępu swobodnego, odnoszący się do jednej z elementów znajdujących się poza ostatnim elementem w zakresie, który ma zostać częściowo posortowany.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje kryterium porównania do spełnienia przez kolejne elementy w kolejności. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="remarks"></a>Uwagi

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Elementy są równoważne, ale niekoniecznie równe, jeśli nie są mniejsze od siebie. Algorytm `sort` nie jest stabilny i nie gwarantuje, że względne porządkowanie elementów równoważnych zostanie zachowane. Algorytm `stable_sort` zachowuje to oryginalne porządkowanie.

Średnia częściowa złożoność sortowania to *O*((`last`- `first`) log (`sortEnd`- `first`)).

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

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

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
    partial_sort(v1.begin( ), v1.begin( ) + 8, v1.end( ), UDgreater );
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

## <a name="partial_sort_copy"></a>partial_sort_copy

Kopiuje elementy z zakresu źródłowego do zakresu docelowego, gdzie elementy źródłowe są uporządkowane według albo zasady mniejszy niż, albo innego określonego predykatu binarnego.

```cpp
template<class InputIterator, class RandomAccessIterator>
RandomAccessIterator partial_sort_copy(
    InputIterator first1,
    InputIterator last1,
    RandomAccessIterator first2,
    RandomAccessIterator last2 );

template<class InputIterator, class RandomAccessIterator, class Compare>
RandomAccessIterator partial_sort_copy(
    InputIterator first1,
    InputIterator last1,
    RandomAccessIterator first2,
    RandomAccessIterator last2,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator, class RandomAccessIterator>
RandomAccessIterator partial_sort_copy(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    RandomAccessIterator result_first,
    RandomAccessIterator result_last);

template<class ExecutionPolicy, class ForwardIterator, class RandomAccessIterator, class Compare>
RandomAccessIterator partial_sort_copy(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    RandomAccessIterator result_first,
    RandomAccessIterator result_last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*first1*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w zakresie źródłowym.

*last1*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w zakresie źródłowym.

*first2*\
Iterator dostępu swobodnego, odnoszący się do pozycji pierwszego elementu w sortowanym zakresie docelowym.

*last2*\
Iterator dostępu swobodnego odnoszący się do pozycji jednej poza ostatnim elementem w sortowanym zakresie docelowym.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje kryterium porównania do spełnienia przez kolejne elementy w kolejności. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="return-value"></a>Wartość zwracana

Iterator dostępu swobodnego, odnoszący się do elementu w zakresie docelowym jedną pozycję poza ostatnim elementem wstawionym z zakresu źródłowego.

### <a name="remarks"></a>Uwagi

Zakresy źródłowe i docelowe nie mogą nakładać się na siebie i muszą być prawidłowe; wszystkie wskaźniki muszą być odwołujące się, a w każdej sekwencji Ostatnia pozycja musi być osiągalna od pierwszej przez przyrost.

Predykat binarny musi zapewniać ścisłą słabą kolejność, tak aby elementy, które nie są równoważne, były uporządkowane, ale elementy, które są równoważne, nie są. Dwa elementy są równoważne poniżej wartości mniejszej niż, ale niekoniecznie, jeśli nie są mniejsze od siebie.

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

## <a name="partition"></a>podzielić

Klasyfikuje elementy w zakresie na dwa rozłączne zestawy, z elementami spełniającymi predykat unarny poprzedzającymi te, które go nie spełniają.

```cpp
template<class BidirectionalIterator, class UnaryPredicate>
BidirectionalIterator partition(
    BidirectionalIterator first,
    BidirectionalIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator partition(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator dwukierunkowy odnoszący się do pozycji pierwszego elementu w zakresie, który ma zostać podzielony na partycje.

*ostatni*\
Iterator dwukierunkowy odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma zostać podzielony na partycje.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje warunek, który ma zostać spełniony, jeśli element ma zostać sklasyfikowany. Predykat jednoargumentowy przyjmuje jeden argument i zwraca **wartość PRAWDA** lub **Fałsz**.

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy odnoszący się do pozycji pierwszego elementu w zakresie, który nie spełnia warunku predykatu.

### <a name="remarks"></a>Uwagi

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Elementy *a* i *b* są równoważne, ale niekoniecznie równe, jeśli oba `pred( a, b )` ma wartość false i `pred( b, a )` ma wartość false, gdzie *pred* jest predykatem określonym parametrem. Algorytm `partition` nie jest stabilny i nie gwarantuje, że względne porządkowanie elementów równoważnych zostanie zachowane. Algorytm `stable_partition` zachowuje to oryginalne porządkowanie.

Złożoność jest liniowa: istnieją `(last - first)` aplikacje *pred* i `(last - first)/2` zamian.

### <a name="example"></a>Przykład

```cpp
// alg_partition.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater5 ( int value )
{
    return value > 5;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

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

## <a name="partition_copy"></a>partition_copy

Kopiuje elementy, dla których warunek ma **wartość true** do jednego miejsca docelowego i dla którego warunek ma **wartość false** . Elementy muszą pochodzić z określonego zakresu.

```cpp
template<class InputIterator, class OutputIterator1, class OutputIterator2, class UnaryPredicate>
pair<OutputIterator1, OutputIterator2> partition_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator1 dest1,
    OutputIterator2 dest2,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate>
pair<ForwardIterator1, ForwardIterator2> partition_copy(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    ForwardIterator1 out_true,
    ForwardIterator2 out_false,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator danych wejściowych, który wskazuje początek zakresu do sprawdzenia warunku.

*ostatni*\
Iterator danych wejściowych, który wskazuje koniec zakresu.

*dest1*\
Iterator wyjściowy używany do kopiowania elementów zwracających wartość true dla warunku testowanego przy użyciu *pred*.

*dest2*\
Iterator wyjściowy używany do kopiowania elementów zwracających wartość false dla warunku testowanego przy użyciu *pred*.

*pred*\
Warunek do przetestowania. Jest to zapewniane przez zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje warunek do przetestowania. Predykat jednoargumentowy przyjmuje jeden argument i zwraca **wartość PRAWDA** lub **Fałsz**.

### <a name="remarks"></a>Uwagi

Funkcja Template kopiuje każdy element `X` w `[first,last)` do `*dest1++` Jeśli `pred(X)` ma wartość true lub `*dest2++`, jeśli nie. Zwraca `pair<OutputIterator1, OutputIterator2>(dest1, dest2)`.

## <a name="partition_point"></a>partition_point

Zwraca pierwszy element w danym zakresie, który nie spełnia warunku. Elementy są sortowane, aby te, które spełniają warunek, występowały przed tymi, które go nie spełniają.

```cpp
template<class ForwardIterator, class UnaryPredicate>
ForwardIterator partition_point(
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*pierwszy*\
`ForwardIterator` wskazujący początek zakresu do sprawdzenia warunku.

*ostatni*\
`ForwardIterator` wskazujący koniec zakresu.

*pred*\
Warunek do przetestowania. Jest to zapewniane przez zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje warunek, który ma być spełniony przez wyszukiwany element. Predykat jednoargumentowy przyjmuje jeden argument i zwraca **wartość PRAWDA** lub **Fałsz**.

### <a name="return-value"></a>Wartość zwracana

Zwraca `ForwardIterator`, która odwołuje się do pierwszego elementu, który nie spełnia warunku przetestowanego przez *pred*, lub zwraca wartość *Last* , jeśli nie zostanie znaleziona.

### <a name="remarks"></a>Uwagi

Funkcja Template znajduje pierwszy iterator `it` w `[first, last)`, dla którego `pred(*it)` ma **wartość false**. Sekwencja musi być uporządkowana według *pred*.

## <a name="pop_heap"></a>pop_heap

Usuwa największy element z przodu sterty do przedostatniej pozycji w zakresie, a następnie tworzy nową stertę z pozostałych elementów.

```cpp
template<class RandomAccessIterator>
void pop_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class BinaryPredicate>
void pop_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*pierwszy*\
Iterator dostępu swobodnego, odnoszący się do pozycji pierwszego elementu sterty.

*ostatni*\
Iterator dostępu swobodnego, odnoszący się do jednej z elementów znajdujących się poza ostatnim elementem w stercie.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje sens, w którym jeden element jest mniejszy niż inny. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="remarks"></a>Uwagi

Algorytm `pop_heap` jest odwrotnością operacji wykonywanej przez algorytm push_heap, w którym element w następnej pozycji zakresu jest dodawany do sterty składającej się z wcześniejszych elementów w zakresie, w przypadku gdy element dodawany do sterty jest większy niż którykolwiek z elementów znajdujących się już na stercie.

Sterty mają dwie właściwości:

- Pierwszy element jest zawsze największy.

- Elementy mogą być dodawane lub usuwane w czasie logarytmu.

Sterty są idealnym sposobem implementacji kolejek priorytetów i są używane w implementacji adaptera [priority_queue](../standard-library/priority-queue-class.md)biblioteki C++ standardowej.

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Zakres wykluczający nowo dodany element na końcu musi być stertą.

Złożoność jest logarytmu, wymagającą co najwyżej `log (last - first)` porównania.

### <a name="example"></a>Przykład

```cpp
// alg_pop_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1, Iter2;

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

## <a name="prev_permutation"></a>prev_permutation

Zmienia kolejność elementów w zakresie, aby oryginalne porządkowanie zostało zastąpione przez lexicographically poprzednią permutację (jeśli istnieje), gdzie Sense Previous można określić za pomocą predykatu binarnego.

```cpp
template<class BidirectionalIterator>
bool prev_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class BidirectionalIterator, class BinaryPredicate>
bool prev_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*pierwszy*\
Iterator dwukierunkowy wskazujący na pozycję pierwszego elementu w zakresie, który ma być permuted.

*ostatni*\
Iterator dwukierunkowy wskazujący na pozycję jeden poza ostatnim elementem w zakresie, który ma być permuted.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje kryterium porównania do spełnienia przez kolejne elementy w kolejności. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli istnieje lexicographically Poprzednia Permutacja i zastąpiła pierwotna kolejność zakresu; w przeciwnym razie **wartość false**, w takim przypadku kolejność jest przekształcana do lexicographically największej permutacji.

### <a name="remarks"></a>Uwagi

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Domyślny Predykat binarny jest mniejszy niż i elementy w zakresie muszą być mniejsze niż porównywalne, aby upewnić się, że poprzednia Permutacja jest dobrze zdefiniowana.

Złożoność jest liniowa, z maksymalnie (`last` - `first`)/2.

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

int main()
{
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

    deq1Result = prev_permutation ( deq1.begin( ), deq1.end( ) );

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
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = -3 ; i <= 3 ; i++ )
        v1.push_back( i );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    prev_permutation ( v1.begin( ), v1.end( ), mod_lesser );

    cout << "After the first prev_permutation, vector v1 is:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= 5 ) {
        prev_permutation ( v1.begin( ), v1.end( ), mod_lesser );
        cout << "After another prev_permutation of vector v1,\n v1 =   ( " ;
        for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ;Iter1 ++ )
            cout << *Iter1 << " ";
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

## <a name="push_heap"></a>push_heap

Dodaje element znajdujący się na końcu zakresu do istniejącej sterty, która składa się z poprzednich elementów w zakresie.

```cpp
template<class RandomAccessIterator>
void push_heap(
    RandomAccessIterator first,
    RandomAccessIterator last );

template<class RandomAccessIterator, class BinaryPredicate>
void push_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*pierwszy*\
Iterator dostępu swobodnego, odnoszący się do pozycji pierwszego elementu sterty.

*ostatni*\
Iterator dostępu swobodnego odnoszący się do jednej z elementów znajdujących się poza ostatnim elementem w zakresie, który ma zostać przekonwertowany na stos.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje sens, w którym jeden element jest mniejszy niż inny. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="remarks"></a>Uwagi

Element musi zostać najpierw wypchnięci z powrotem do końca istniejącej sterty, a następnie algorytm służy do dodawania tego elementu do istniejącej sterty.

Sterty mają dwie właściwości:

- Pierwszy element jest zawsze największy.

- Elementy mogą być dodawane lub usuwane w czasie logarytmu.

Sterty są idealnym sposobem implementacji kolejek priorytetów i są używane w implementacji adaptera [priority_queue](../standard-library/priority-queue-class.md)biblioteki C++ standardowej.

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Zakres wykluczający nowo dodany element na końcu musi być stertą.

Złożoność jest logarytmu, wymagającą co najwyżej `log(last - first)` porównania.

### <a name="example"></a>Przykład

```cpp
// alg_push_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

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

## <a name="random_shuffle"></a>random_shuffle

Funkcja std:: random_shuffle () jest przestarzała, zastąpiona przez [std:: losowo](../standard-library/algorithm-functions.md#shuffle). Aby uzyskać przykład kodu i więcej informacji, zobacz [\<losowo >](../standard-library/random.md) i Stack Overflow post [dlaczego są std:: random_shuffle metody przestarzałe w języku c++ 14?](https://go.microsoft.com/fwlink/p/?linkid=397954).

## <a name="remove"></a>usuwa

Eliminuje określoną wartość z danego zakresu bez zakłócania kolejności pozostałych elementów i zwracania końca nowego zakresu wolnego od określonej wartości.

```cpp
template<class ForwardIterator, class Type>
ForwardIterator remove(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
ForwardIterator remove(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator do przodu, odnoszący się do pozycji pierwszego elementu w zakresie, z którego elementy są usuwane.

*ostatni*\
Iterator do przodu, odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, z którego elementy są usuwane.

\ *wartości*
Wartość, która ma zostać usunięta z zakresu.

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, odnoszący się do nowej pozycji końcowej zmodyfikowanego zakresu, jeden poza ostatnim elementem sekwencji pozostałej z określoną wartością.

### <a name="remarks"></a>Uwagi

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Kolejność elementów, które nie zostały usunięte, pozostaje stabilna.

`operator==` używany do określania równości między elementami musi nałożyć relację równoważności między operandami.

Złożoność jest liniowa; Istnieją porównania (`last` - `first`) dla równości.

[Klasa list](../standard-library/list-class.md) ma wydajniejszą wersję funkcji składowej `remove`, która również łączy wskaźniki.

### <a name="example"></a>Przykład

```cpp
// alg_remove.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1, Iter2, new_end;

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

## <a name="remove_copy"></a>remove_copy

Kopiuje elementy z zakresu źródłowego do zakresu docelowego, z tym wyjątkiem, że elementy o określonej wartości nie są kopiowane, bez naruszania kolejności pozostałych elementów i zwracania końca nowego zakresu docelowego.

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator remove_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
ForwardIterator2 remove_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    const Type& value);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w zakresie, z którego elementy są usuwane.

*ostatni*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, z którego elementy są usuwane.

\ *wyniku*
Iterator danych wyjściowych odnoszący się do pozycji pierwszego elementu w zakresie docelowym, do którego elementy są usuwane.

\ *wartości*
Wartość, która ma zostać usunięta z zakresu.

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, odnoszący się do nowej pozycji końcowej zakresu docelowego, jeden poza ostatnim elementem kopii sekwencji pozostałej o określonej wartości.

### <a name="remarks"></a>Uwagi

Przywoływany zakres źródłowy i docelowy muszą być prawidłowe; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Musi być wystarczająco dużo miejsca w zakresie docelowym, aby można było zawierać pozostałe elementy, które zostaną skopiowane po usunięciu elementów z określonej wartości.

Kolejność elementów, które nie zostały usunięte, pozostaje stabilna.

`operator==` używany do określania równości między elementami musi nałożyć relację równoważności między operandami.

Złożoność jest liniowa; Istnieje (`last` - `first`) porównania dla równości i maksymalnie (`last` - `first`).

### <a name="example"></a>Przykład

```cpp
// alg_remove_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2(10);
    vector<int>::iterator Iter1, Iter2, new_end;

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

## <a name="remove_copy_if"></a>remove_copy_if

Kopiuje elementy z zakresu źródłowego do zakresu docelowego, z wyjątkiem elementów, które spełniają predykat. Elementy są kopiowane bez zakłócania kolejności pozostałych elementów. Zwraca koniec nowego zakresu docelowego.

```cpp
template<class InputIterator, class OutputIterator, class UnaryPredicate>
OutputIterator remove_copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate>
ForwardIterator2 remove_copy_if(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w zakresie, z którego elementy są usuwane.

*ostatni*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, z którego elementy są usuwane.

\ *wyniku*
Iterator danych wyjściowych odnoszący się do pozycji pierwszego elementu w zakresie docelowym, do którego elementy są usuwane.

*pred*\
Predykat jednoargumentowy, który musi być spełniony, jest wartością elementu, który ma zostać zastąpiony.

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, odnoszący się do nowej pozycji końcowej zakresu docelowego, jeden poza ostatnim elementem sekwencji pozostałej, wolnych od elementów spełniających predykat.

### <a name="remarks"></a>Uwagi

Przywoływany zakres źródłowy musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Musi być wystarczająco dużo miejsca w zakresie docelowym, aby można było zawierać pozostałe elementy, które zostaną skopiowane po usunięciu elementów z określonej wartości.

Kolejność elementów, które nie zostały usunięte, pozostaje stabilna.

`operator==` używany do określania równości między elementami musi nałożyć relację równoważności między operandami.

Złożoność jest liniowa: istnieje (`last` - `first`) porównania dla równości i maksymalnie (`last` - `first`).

Aby uzyskać informacje na temat zachowania tych funkcji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

```cpp
// alg_remove_copy_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value ) {
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1, v2(10);
    vector<int>::iterator Iter1, Iter2, new_end;

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

## <a name="remove_if"></a>remove_if

Eliminuje elementy, które spełniają predykat, z danego zakresu bez zakłócania kolejności pozostałych elementów i zwracania końca nowego zakresu wolnego od określonej wartości.

```cpp
template<class ForwardIterator, class UnaryPredicate>
ForwardIterator remove_if(
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator remove_if(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator do przodu wskazujący na pozycję pierwszego elementu w zakresie, z którego elementy są usuwane.

*ostatni*\
Iterator do przodu, wskazujący na pozycję jeden poza ostatnim elementem w zakresie, z którego elementy są usuwane.

*pred*\
Predykat jednoargumentowy, który musi być spełniony, jest wartością elementu, który ma zostać zastąpiony.

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, odnoszący się do nowej pozycji końcowej zmodyfikowanego zakresu, jeden poza ostatnim elementem sekwencji pozostałej z określoną wartością.

### <a name="remarks"></a>Uwagi

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Kolejność elementów, które nie zostały usunięte, pozostaje stabilna.

`operator==` używany do określania równości między elementami musi nałożyć relację równoważności między operandami.

Złożoność jest liniowa: istnieje (`last` - `first`) porównania dla równości.

Lista ma wydajniejszą wersję funkcji składowej, która umożliwia usunięcie wskaźników, które łączą się.

### <a name="example"></a>Przykład

```cpp
// alg_remove_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value )
{
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2, new_end;

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

## <a name="replace"></a>stępować

Sprawdza każdy element w zakresie i zastępuje go, jeśli odpowiada określonej wartości.

```cpp
template<class ForwardIterator, class Type>
void replace(
    ForwardIterator first,
    ForwardIterator last,
    const Type& oldVal,
    const Type& newVal);

template<class ExecutionPolicy, class ForwardIterator, class Type>
void replace(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& oldVal,
    const Type& newVal);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator do przodu wskazujący na pozycję pierwszego elementu w zakresie, z którego są zamieniane elementy.

*ostatni*\
Iterator do przodu, wskazujący na pozycję jedną poza ostatnim elementem w zakresie, z którego są zamieniane elementy.

*oldVal*\
Stara wartość zastępowanych elementów.

*newVal*\
Nowa wartość przypisana do elementów ze starą wartością.

### <a name="remarks"></a>Uwagi

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Kolejność elementów, które nie zostały zastąpione, pozostaje stabilna.

`operator==` używany do określania równości między elementami musi nałożyć relację równoważności między operandami.

Złożoność jest liniowa; Istnieją (`last` - `first`) porównania dla równości i maksymalnie (`last` - `first`) przypisań nowych wartości.

### <a name="example"></a>Przykład

```cpp
// alg_replace.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

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

## <a name="replace_copy"></a>replace_copy

Sprawdza każdy element w zakresie źródłowym i zastępuje go, jeśli odpowiada określonej wartości, jednocześnie kopiując wynik do nowego zakresu docelowego.

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator replace_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    const Type& oldVal,
    const Type& newVal);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
ForwardIterator2 replace_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    const Type& oldVal,
    const Type& newVal);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator wejściowy wskazujący pozycję pierwszego elementu w zakresie, z którego są zamieniane elementy.

*ostatni*\
Iterator wejściowy wskazujący na pozycję jedną poza ostatnim elementem w zakresie, z którego są zamieniane elementy.

\ *wyniku*
Iterator danych wyjściowych wskazujący na pierwszy element w zakresie docelowym, do miejsca, w którym jest kopiowana zmieniona sekwencja elementów.

*oldVal*\
Stara wartość zastępowanych elementów.

*newVal*\
Nowa wartość przypisana do elementów ze starą wartością.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych wskazujący na pozycję jeden obok elementu końcowego w zakresie docelowym, do którego jest kopiowana zmieniona sekwencja elementów.

### <a name="remarks"></a>Uwagi

Zakresy źródłowe i docelowe, do których istnieją odwołania, nie mogą się nakładać i muszą być prawidłowe: wszystkie wskaźniki muszą mieć możliwość odwołującego się do siebie i w sekwencjach, w których ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Kolejność elementów, które nie zostały zastąpione, pozostaje stabilna.

`operator==` używany do określania równości między elementami musi nałożyć relację równoważności między operandami.

Złożoność jest liniowa: istnieje (`last` - `first`) porównania dla równości i maksymalnie (`last` - `first`) przypisań nowych wartości.

### <a name="example"></a>Przykład

```cpp
// alg_replace_copy.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    list<int> L1 (15);
    vector<int>::iterator Iter1;
    list<int>::iterator L_Iter1;

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

## <a name="replace_copy_if"></a>replace_copy_if

Sprawdza każdy element w zakresie źródłowym i zastępuje go, jeśli spełnia określony predykat, jednocześnie kopiując wynik do nowego zakresu docelowego.

```cpp
template<class InputIterator, class OutputIterator, class UnaryPredicate, class Type>
OutputIterator replace_copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    UnaryPredicate pred,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate, class Type>
ForwardIterator2 replace_copy_if(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryPredicate pred,
    const Type& value);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator wejściowy wskazujący pozycję pierwszego elementu w zakresie, z którego są zamieniane elementy.

*ostatni*\
Iterator wejściowy wskazujący na pozycję jedną poza ostatnim elementem w zakresie, z którego są zamieniane elementy.

\ *wyniku*
Iterator danych wyjściowych wskazujący na pozycję pierwszego elementu w zakresie docelowym, do którego kopiowane są elementy.

*pred*\
Predykat jednoargumentowy, który musi być spełniony, jest wartością elementu, który ma zostać zastąpiony.

\ *wartości*
Nowa wartość jest przypisywana do elementów, których stara wartość spełnia predykat.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych wskazujący na pozycję jeden obok elementu końcowego w zakresie docelowym, do którego jest kopiowana zmieniona sekwencja elementów.

### <a name="remarks"></a>Uwagi

Zakresy źródłowe i docelowe, do których istnieją odwołania, nie mogą się nakładać i muszą być prawidłowe: wszystkie wskaźniki muszą mieć możliwość odwołującego się do siebie i w sekwencjach, w których ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Kolejność elementów, które nie zostały zastąpione, pozostaje stabilna.

`operator==` używany do określania równości między elementami musi nałożyć relację równoważności między operandami.

Złożoność jest liniowa; Istnieją (`last` - `first`) porównania dla równości i maksymalnie (`last` - `first`) przypisań nowych wartości.

### <a name="example"></a>Przykład

```cpp
// alg_replace_copy_if.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

bool greater6 ( int value )
{
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1;
    list<int> L1 (13);
    vector<int>::iterator Iter1;
    list<int>::iterator L_Iter1;

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

## <a name="replace_if"></a>replace_if

Sprawdza każdy element w zakresie i zastępuje go, jeśli spełnia określony predykat.

```cpp
template<class ForwardIterator, class UnaryPredicate, class Type>
void replace_if(
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate, class Type>
void replace_if(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred,
    const Type& value);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator do przodu wskazujący na pozycję pierwszego elementu w zakresie, z którego są zamieniane elementy.

*ostatni*\
Iterator wskazujący na pozycję jedną poza ostatnim elementem w zakresie, z którego są zamieniane elementy.

*pred*\
Predykat jednoargumentowy, który musi być spełniony, jest wartością elementu, który ma zostać zastąpiony.

\ *wartości*
Nowa wartość jest przypisywana do elementów, których stara wartość spełnia predykat.

### <a name="remarks"></a>Uwagi

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Kolejność elementów, które nie zostały zastąpione, pozostaje stabilna.

Algorytm `replace_if` jest generalizacją algorytmu `replace`, co pozwala określić dowolny predykat, a nie równość do określonej wartości stałej.

`operator==` używany do określania równości między elementami musi nałożyć relację równoważności między operandami.

Złożoność jest liniowa: istnieje (`last` - `first`) porównania dla równości i maksymalnie (`last` - `first`) przypisań nowych wartości.

### <a name="example"></a>Przykład

```cpp
// alg_replace_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value )
{
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

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

## <a name="reverse"></a>cofnięci

Odwraca kolejność elementów w obrębie zakresu.

```cpp
template<class BidirectionalIterator>
void reverse(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class ExecutionPolicy, class BidirectionalIterator>
void reverse(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator last);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator dwukierunkowy wskazujący na pozycję pierwszego elementu w zakresie, w którym są permuted elementy.

*ostatni*\
Iterator dwukierunkowy wskazujący na pozycję jeden poza ostatnim elementem w zakresie, w którym są permuted elementy.

### <a name="remarks"></a>Uwagi

Przywoływany zakres źródłowy musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

### <a name="example"></a>Przykład

```cpp
// alg_reverse.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

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

## <a name="reverse_copy"></a>reverse_copy

Odwraca kolejność elementów w obrębie zakresu źródłowego, jednocześnie kopiując je do zakresu docelowego

```cpp
template<class BidirectionalIterator, class OutputIterator>
OutputIterator reverse_copy(
    BidirectionalIterator first,
    BidirectionalIterator last,
    OutputIterator result);

template<class ExecutionPolicy, class BidirectionalIterator, class ForwardIterator>
ForwardIterator reverse_copy(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator last,
    ForwardIterator result);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator dwukierunkowy wskazujący na pozycję pierwszego elementu w zakresie źródłowym, w którym są permuted elementy.

*ostatni*\
Iterator dwukierunkowy wskazujący na pozycję jeden poza ostatnim elementem w zakresie źródłowym, w którym są permuted elementy.

\ *wyniku*
Iterator danych wyjściowych wskazujący na pozycję pierwszego elementu w zakresie docelowym, do którego kopiowane są elementy.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych wskazujący na pozycję jeden obok elementu końcowego w zakresie docelowym, do którego jest kopiowana zmieniona sekwencja elementów.

### <a name="remarks"></a>Uwagi

Przywoływany zakres źródłowy i docelowy muszą być prawidłowe; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

### <a name="example"></a>Przykład

```cpp
// alg_reverse_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2( 10 );
    vector<int>::iterator Iter1, Iter2;

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

## <a name="rotate"></a>obróceni

Wymienia elementy znajdujące się w dwóch sąsiednich zakresach.

```cpp
template<class ForwardIterator>
void rotate(
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator rotate(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator do przodu, odnoszący się do pozycji pierwszego elementu w zakresie, który ma zostać obrócony.

\ *środkowy*
Iterator do przodu definiujący granicę w zakresie, który odnosi się do pozycji pierwszego elementu w drugiej części zakresu, którego elementy mają być wymieniane z tymi w pierwszej części zakresu.

*ostatni*\
Iterator do przodu, odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma zostać obrócony.

### <a name="remarks"></a>Uwagi

Zakresy, do których istnieją odwołania, muszą być prawidłowe; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Złożoność jest liniowa z maksymalnie (`last` - `first`) wymian.

### <a name="example"></a>Przykład

```cpp
// alg_rotate.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1;
    deque<int> d1;
    vector<int>::iterator v1Iter1;
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
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    rotate ( v1.begin( ), v1.begin( ) + 3 , v1.end( ) );
    cout << "After rotating, vector v1 is ( " ;
    for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    cout << "The original deque d1 is ( " ;
    for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
        cout << *d1Iter1 << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= d1.end( ) - d1.begin( ) ) {
        rotate ( d1.begin( ), d1.begin( ) + 1 , d1.end( ) );
        cout << "After the rotation of a single deque element to the back,\n d1 is   ( " ;
        for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
            cout << *d1Iter1 << " ";
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

## <a name="rotate_copy"></a>rotate_copy

Wymienia elementy w dwóch sąsiednich zakresach w ramach zakresu źródłowego i kopiuje wynik do zakresu docelowego.

```cpp
template<class ForwardIterator, class OutputIterator>
OutputIterator rotate_copy(
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last,
    OutputIterator result );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 rotate_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 middle,
    ForwardIterator1 last,
    ForwardIterator2 result);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator do przodu, odnoszący się do pozycji pierwszego elementu w zakresie, który ma zostać obrócony.

\ *środkowy*
Iterator do przodu definiujący granicę w zakresie, który odnosi się do pozycji pierwszego elementu w drugiej części zakresu, którego elementy mają być wymieniane z tymi w pierwszej części zakresu.

*ostatni*\
Iterator do przodu, odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma zostać obrócony.

\ *wyniku*
Iterator danych wyjściowych odnoszący się do pozycji pierwszego elementu w zakresie docelowym.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych odnoszący się do pozycji jednej poza ostatnim elementem w zakresie docelowym.

### <a name="remarks"></a>Uwagi

Zakresy, do których istnieją odwołania, muszą być prawidłowe; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Złożoność jest liniowa z maksymalnie (`last` - `first`) wymian.

### <a name="example"></a>Przykład

```cpp
// alg_rotate_copy.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1 , v2 ( 9 );
    deque<int> d1 , d2 ( 6 );
    vector<int>::iterator v1Iter , v2Iter;
    deque<int>::iterator d1Iter , d2Iter;

    int i;
    for ( i = -3 ; i <= 5 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii =0 ; ii <= 5 ; ii++ )
        d1.push_back( ii );

    cout << "Vector v1 is ( " ;
    for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )
        cout << *v1Iter << " ";
    cout << ")." << endl;

    rotate_copy ( v1.begin( ), v1.begin( ) + 3 , v1.end( ), v2.begin( ) );
    cout << "After rotating, the vector v1 remains unchanged as:\n v1 = ( " ;
    for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )
        cout << *v1Iter << " ";
    cout << ")." << endl;

    cout << "After rotating, the copy of vector v1 in v2 is:\n v2 = ( " ;
    for ( v2Iter = v2.begin( ) ; v2Iter != v2.end( ) ;v2Iter ++ )
        cout << *v2Iter << " ";
    cout << ")." << endl;

    cout << "The original deque d1 is ( " ;
    for ( d1Iter = d1.begin( ) ; d1Iter != d1.end( ) ;d1Iter ++ )
        cout << *d1Iter << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= d1.end( ) - d1.begin( ) )
    {
        rotate_copy ( d1.begin( ), d1.begin( ) + iii , d1.end( ), d2.begin( ) );
        cout << "After the rotation of a single deque element to the back,\n d2 is   ( " ;
        for ( d2Iter = d2.begin( ) ; d2Iter != d2.end( ) ;d2Iter ++ )
            cout << *d2Iter << " ";
        cout << ")." << endl;
        iii++;
    }
}
```

## <a name="sample"></a>Northwind

```cpp
template<class PopulationIterator, class SampleIterator, class Distance, class UniformRandomBitGenerator>
SampleIterator sample(
    PopulationIterator first,
    PopulationIterator last,
    SampleIterator out,
    Distance n,
    UniformRandomBitGenerator&& g);
```

## <a name="search"></a>wyszukiwania

Wyszukuje pierwsze wystąpienie sekwencji w zakresie docelowym, której elementy są równe tym w danej sekwencji elementów lub której elementy są równoważne w sensie określonym przez predykat binarny dla elementów w danej sekwencji.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 search(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 search(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 search(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 search(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);

template <class ForwardIterator, class Searcher>
ForwardIterator search(
    ForwardIterator first,
    ForwardIterator last,
    const Searcher& searcher);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*first1*\
Iterator do przodu, odnoszący się do pozycji pierwszego elementu w zakresie, który ma być przeszukiwany.

*last1*\
Iterator do przodu, odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma być przeszukiwany.

*first2*\
Iterator do przodu, odnoszący się do pozycji pierwszego elementu w zakresie, który ma zostać dopasowany.

*last2*\
Iterator do przodu, odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma zostać dopasowany.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje warunek do spełnienia, jeśli dwa elementy mają być wykonane jako równoważne. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

\ *wyszukiwania*
Program do wyszukiwania, który hermetyzuje wzorzec do wyszukania i algorytm wyszukiwania do użycia. Aby uzyskać więcej informacji o wyszukiwarkach, zobacz Klasa [default_searcher](default-searcher-class.md), [Klasa boyer_moore_horspool_searcher](boyer-moore-horspool-searcher-class.md)i [Klasa boyer_moore_searcher](boyer-moore-searcher-class.md).

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, odnoszący się do pozycji pierwszego elementu pierwszej podsekwencji, która pasuje do określonej sekwencji lub jest równoważne w sensie określonym przez Predykat binarny.

### <a name="remarks"></a>Uwagi

`operator==` używany do określenia dopasowania między elementem a określoną wartością musi nałożyć relację równoważności między operandami.

Zakresy, do których istnieją odwołania, muszą być prawidłowe; wszystkie wskaźniki muszą być odwołujące się i w każdej sekwencji, która jest dostępna od pierwszej do przyrostu.

Średnia złożoność jest liniowa w odniesieniu do rozmiaru przeszukanego zakresu, a najgorszy stopień złożoności jest również liniowy w odniesieniu do rozmiaru przeszukiwanej sekwencji.

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

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

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
    vector<int>::iterator result1;
    result1 = search (v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

    if ( result1 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is at least one match of L1 in v1"
            << "\n and the first one begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for a match to L1 under the binary predicate twice
    vector<int>::iterator result2;
    result2 = search (v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

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

## <a name="search_n"></a>search_n

Wyszukuje pierwszą podsekwencję w zakresie, w której określona liczba elementów ma określoną wartość lub relację do tej wartości określoną przez predykat binarny.

```cpp
template<class ForwardIterator1, class Diff2, class Type>
ForwardIterator1 search_n(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    Diff2 count,
    const Type& value);

template<class ForwardIterator1, class Diff2, class Type, class BinaryPredicate>
ForwardIterator1 search_n(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    Diff2 count,
    const Type& value,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Type>
ForwardIterator search_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Size count,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Type, class BinaryPredicate>
ForwardIterator search_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Size count,
    const Type& value,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*first1*\
Iterator do przodu, odnoszący się do pozycji pierwszego elementu w zakresie, który ma być przeszukiwany.

*last1*\
Iterator do przodu, odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma być przeszukiwany.

*liczba*\
Rozmiar podsekwencji podszukiwanej.

\ *wartości*
Wartość elementów w przeszukiwanej sekwencji.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje warunek do spełnienia, jeśli dwa elementy mają być wykonane jako równoważne. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, odnoszący się do pozycji pierwszego elementu pierwszej podsekwencji, która pasuje do określonej sekwencji lub jest równoważne w sensie określonym przez Predykat binarny.

### <a name="remarks"></a>Uwagi

`operator==` używany do określenia dopasowania między elementem a określoną wartością musi nałożyć relację równoważności między operandami.

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Złożoność jest liniowa w odniesieniu do wielkości przeszukiwanych.

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

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( 5 );
    }

    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( 10 );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // Searching v1 for first match to (5 5 5) under identity
    vector<int>::iterator result1;
    result1 = search_n ( v1.begin( ), v1.end( ), 3, 5 );

    if ( result1 == v1.end( ) )
        cout << "There is no match for a sequence ( 5 5 5 ) in v1."
            << endl;
    else
        cout << "There is at least one match of a sequence ( 5 5 5 )"
            << "\n in v1 and the first one begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for first match to (5 5 5) under one_half
    vector<int>::iterator result2;
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

## <a name="set_difference"></a>set_difference

Łączy w sobie wszystkie elementy, które należą do jednego posortowanego zakresu źródłowego, ale nie do drugiego posortowanego zakresu źródłowego, w pojedynczy, posortowany zakres docelowy, gdzie kryterium sortowania może być określone przez predykat binarny.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*first1*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w pierwszym z dwóch posortowanych zakresów źródłowych w celu posortowania w jeden zakres reprezentujący różnicę dwóch zakresów źródłowych.

*last1*\
Iterator danych wejściowych odnoszący się do pozycji jeden poza ostatnim elementem w pierwszym z dwóch posortowanych zakresów źródłowych do zapełnienia i posortowany w pojedynczy zakres reprezentujący różnicę dwóch zakresów źródłowych.

*first2*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w drugim z dwóch kolejnych posortowanych zakresów źródłowych w celu posortowania w jeden zakres reprezentujący różnicę dwóch zakresów źródłowych.

*last2*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w drugim z dwóch kolejnych posortowanych zakresów źródłowych do zapełnienia i posortowania w jeden zakres reprezentujący różnicę dwóch zakresów źródłowych.

\ *wyniku*
Iterator danych wyjściowych odnoszący się do pozycji pierwszego elementu w zakresie docelowym, w którym dwa zakresy źródłowe mają być umieszczone w jednym posortowanym zakresie, reprezentującym różnicę dwóch zakresów źródłowych.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje sens, w którym jeden element jest mniejszy niż inny. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , gdy pierwszy element jest mniejszy od drugiego elementu i w przeciwnym razie zwraca **wartość false** .

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych odnoszący się do pozycji jednej poza ostatnim elementem w sortowanym zakresie docelowym reprezentującą różnicę dwóch zakresów źródłowych.

### <a name="remarks"></a>Uwagi

Posortowane zakresy źródłowe, do których istnieją odwołania, muszą być prawidłowe; wszystkie wskaźniki muszą być odwołujące się, a w każdej sekwencji Ostatnia pozycja musi być osiągalna od pierwszej przez przyrost.

Zakres docelowy nie powinien nakładać się na żaden z zakresów źródłowych i powinien być wystarczająco duży, aby zawierał pierwszy zakres źródłowy.

Posortowane zakresy źródłowe muszą być uporządkowane jako warunek wstępny do zastosowania algorytmu `set_difference`, zgodnie z tą samą kolejnością, w jakiej ma być używana przez algorytm w celu sortowania połączonych zakresów.

Operacja jest stabilna, ponieważ względna kolejność elementów w każdym zakresie jest zachowywana w zakresie docelowym. Zakresy źródłowe nie są modyfikowane przez scalanie algorytmów.

Typy wartości iteratorów wejściowych muszą być mniejsze niż-porównywalne, aby można je było uporządkować, tak że, w przypadku dwóch elementów, można określić, że są one równoważne (w sensie, że żaden z nich nie jest mniejszy od drugiego) lub jeden z nich jest mniejszy od drugiego. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Gdy w obu zakresach źródłowych znajdują się równoważne elementy, elementy z pierwszego zakresu poprzedzają elementy z drugiego zakresu źródłowego w zakresie docelowym. Jeśli zakresy źródłowe zawierają duplikaty elementu, takie jak w pierwszym zakresie źródłowym niż w drugim, zakres docelowy będzie zawierać liczbę, za pomocą której wystąpienia tych elementów w pierwszym zakresie źródłowym przekraczają wystąpienia elementu te elementy w drugim zakresie źródłowym.

Złożoność algorytmu jest liniowa z co najwyżej `2 * ((last1 - first1) - (last2 - first2)) - 1` porównania dla niepustych zakresów źródłowych.

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

int main()
{
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less-than ordering
    int i;
    for ( i = -1 ; i <= 4 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-3 ; ii <= 0 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into a difference in asscending
    // order with the default binary predicate less<int>( )
    Result1 = set_difference ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Set_difference of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into a difference in descending
    // order specify binary predicate greater<int>( )
    Result2 = set_difference ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Set_difference of source ranges with binary"
         << "predicate greater specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into a difference applying a user
    // defined binary predicate mod_lesser
    Result3 = set_difference ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Set_difference of source ranges with binary "
         << "predicate mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="set_intersection"></a>set_intersection

Łączy w sobie wszystkie elementy, które należą do obu posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_intersection(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result);

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_intersection(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_intersection(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_intersection(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*first1*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w pierwszym z dwóch posortowanych zakresów źródłowych w celu posortowania w jeden zakres reprezentujący przecięcie dwóch zakresów źródłowych.

*last1*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w pierwszym z dwóch posortowanych zakresów źródłowych do zapełnienia i posortowany w pojedynczy zakres reprezentujący przecięcie dwóch zakresów źródłowych.

*first2*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w drugim z dwóch kolejnych posortowanych zakresów źródłowych w celu posortowania w jeden zakres reprezentujący przecięcie dwóch zakresów źródłowych.

*last2*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w drugim z dwóch kolejnych posortowanych zakresów źródłowych w celu posortowania w jeden zakres reprezentujący przecięcie dwóch zakresów źródłowych.

\ *wyniku*
Iterator danych wyjściowych odnoszący się do pozycji pierwszego elementu w zakresie docelowym, w którym dwa zakresy źródłowe mają być załączone do pojedynczego posortowanego zakresu reprezentującego część wspólną dwóch zakresów źródłowych.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje sens, w którym jeden element jest mniejszy niż inny. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , gdy pierwszy element jest mniejszy od drugiego elementu i w przeciwnym razie zwraca **wartość false** .

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych odnoszący się do pozycji jednej poza ostatnim elementem w sortowanym zakresie docelowym reprezentującej część wspólną dwóch zakresów źródłowych.

### <a name="remarks"></a>Uwagi

Posortowane zakresy źródłowe, do których istnieją odwołania, muszą być prawidłowe; wszystkie wskaźniki muszą być odwołujące się, a w każdej sekwencji Ostatnia pozycja musi być osiągalna od pierwszej przez przyrost.

Zakres docelowy nie powinien nakładać się na żaden z zakresów źródłowych i powinien być wystarczająco duży, aby zawierał zakres docelowy.

Posortowane zakresy źródłowe muszą być uporządkowane jako warunek wstępny do zastosowania algorytmu scalania zgodnie z tą samą kolejnością, w jakiej ma być używana przez algorytm w celu sortowania połączonych zakresów.

Operacja jest stabilna, ponieważ względna kolejność elementów w każdym zakresie jest zachowywana w zakresie docelowym. Zakresy źródłowe nie są modyfikowane przez algorytm.

Typy wartości iteratorów danych wejściowych muszą być mniejsze niż porównywalne do uporządkowania, tak aby w przypadku dwóch elementów można było określić, że są one równoważne (w sensie, że żaden z nich nie jest mniejszy niż drugi) lub że jeden z nich jest mniejszy od drugiego. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Gdy w obu zakresach źródłowych znajdują się równoważne elementy, elementy z pierwszego zakresu poprzedzają elementy z drugiego zakresu źródłowego w zakresie docelowym. Jeśli zakresy źródłowe zawierają duplikaty elementu, zakres docelowy będzie zawierać maksymalną liczbę elementów występujących w obu zakresach źródłowych.

Złożoność algorytmu jest liniowa z co najwyżej `2 * ((last1 - first1) + (last2 - first2)) - 1` porównania dla niepustych zakresów źródłowych.

### <a name="example"></a>Przykład

```cpp
// alg_set_intersection.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>   // For greater<int>( )
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

int main()
{
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less than ordering
    int i;
    for ( i = -1 ; i <= 3 ; i++ )
        v1a.push_back( i );

    int ii;
    for ( ii =-3 ; ii <= 1 ; ii++ )
        v1b.push_back( ii );

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into an intersection in asscending order with the
    // default binary predicate less<int>( )
    Result1 = set_intersection ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Intersection of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; ++Iter1 )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into an intersection in descending order, specify
    // binary predicate greater<int>( )
    Result2 = set_intersection ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Intersection of source ranges with binary predicate"
            << " greater specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; ++Iter2 )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into an intersection applying a user-defined
    // binary predicate mod_lesser
    Result3 = set_intersection ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Intersection of source ranges with binary predicate "
            << "mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; ++Iter3 )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="set_symmetric_difference"></a>set_symmetric_difference

Łączy w sobie wszystkie elementy, które należą do jednego z, ale nie obu posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_symmetric_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_symmetric_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_symmetric_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_symmetric_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*first1*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w pierwszym z dwóch posortowanych zakresów źródłowych w celu posortowania w jeden zakres reprezentujący różnicę symetryczne dwóch zakresów źródłowych.

*last1*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w pierwszym z dwóch posortowanych zakresów źródłowych do zapełnienia i posortowany w jeden zakres reprezentujący różnicę symetryczne dwóch zakresów źródłowych.

*first2*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w drugim z dwóch kolejnych posortowanych zakresów źródłowych w celu posortowania w jeden zakres reprezentujący różnicę symetryczne dwóch zakresów źródłowych.

*last2*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w drugim z dwóch kolejnych posortowanych zakresów źródłowych w celu posortowania w jeden zakres reprezentujący różnicę symetryczne dwóch zakresów źródłowych.

\ *wyniku*
Iterator danych wyjściowych odnoszący się do pozycji pierwszego elementu w zakresie docelowym, w którym dwa zakresy źródłowe mają być załączone do pojedynczego posortowanego zakresu reprezentującego różnicę symetryczne dwóch zakresów źródłowych.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje sens, w którym jeden element jest mniejszy niż inny. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , gdy pierwszy element jest mniejszy od drugiego elementu i w przeciwnym razie zwraca **wartość false** .

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych odnoszący się do pozycji jednej poza ostatnim elementem w sortowanym zakresie docelowym reprezentującym różnicę symetryczne dwóch zakresów źródłowych.

### <a name="remarks"></a>Uwagi

Posortowane zakresy źródłowe, do których istnieją odwołania, muszą być prawidłowe; wszystkie wskaźniki muszą być odwołujące się, a w każdej sekwencji Ostatnia pozycja musi być osiągalna od pierwszej przez przyrost.

Zakres docelowy nie powinien nakładać się na żaden z zakresów źródłowych i powinien być wystarczająco duży, aby zawierał zakres docelowy.

Posortowane zakresy źródłowe muszą być uporządkowane jako warunek wstępny do zastosowania algorytmu `merge*`, zgodnie z tą samą kolejnością, w jakiej ma być używana przez algorytm w celu sortowania połączonych zakresów.

Operacja jest stabilna, ponieważ względna kolejność elementów w każdym zakresie jest zachowywana w zakresie docelowym. Zakresy źródłowe nie są modyfikowane przez scalanie algorytmów.

Typy wartości iteratorów danych wejściowych muszą być mniejsze niż porównywalne do uporządkowania, tak aby w przypadku dwóch elementów można było określić, że są one równoważne (w sensie, że żaden z nich nie jest mniejszy niż drugi) lub że jeden z nich jest mniejszy od drugiego. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Gdy w obu zakresach źródłowych znajdują się równoważne elementy, elementy z pierwszego zakresu poprzedzają elementy z drugiego zakresu źródłowego w zakresie docelowym. Jeśli zakresy źródłowe zawierają duplikaty elementu, zakres docelowy będzie zawierać wartość bezwzględną liczby, za pomocą której wystąpienia tych elementów w jednym z zakresów źródłowych przekraczają wystąpienia tych elementów w drugim źródle. zakresu.

Złożoność algorytmu jest liniowa z co najwyżej `2 * ((last1 - first1) - (last2 - first2)) - 1` porównania dla niepustych zakresów źródłowych.

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

int main()
{
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less-than ordering
    int i;
    for ( i = -1 ; i <= 4 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-3 ; ii <= 0 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into a symmetric difference in ascending
    // order with the default binary predicate less<int>( )
    Result1 = set_symmetric_difference ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Set_symmetric_difference of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into a symmetric difference in descending
    // order, specify binary predicate greater<int>( )
    Result2 = set_symmetric_difference ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Set_symmetric_difference of source ranges with binary"
         << "predicate greater specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into a symmetric difference applying a user
    // defined binary predicate mod_lesser
    Result3 = set_symmetric_difference ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Set_symmetric_difference of source ranges with binary "
         << "predicate mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="set_union"></a>set_union

Łączy w sobie wszystkie elementy, które należą do przynajmniej jednego z dwóch posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_union(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_union(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_union(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_union(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*first1*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w pierwszym z dwóch posortowanych zakresów źródłowych w celu posortowania w jeden zakres reprezentujący Unię dwóch zakresów źródłowych.

*last1*\
Iterator danych wejściowych odnoszący się do pozycji jeden poza ostatnim elementem w pierwszym z dwóch posortowanych zakresów źródłowych do zapełnienia i posortowany w jeden zakres reprezentujący Unię dwóch zakresów źródłowych.

*first2*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w drugim z dwóch kolejnych posortowanych zakresów źródłowych w celu posortowania w jeden zakres reprezentujący Unię dwóch zakresów źródłowych.

*last2*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w drugim z dwóch kolejnych posortowanych zakresów źródłowych do zapełnienia i posortowania w jeden zakres reprezentujący Unię dwóch zakresów źródłowych.

\ *wyniku*
Iterator danych wyjściowych odnoszący się do pozycji pierwszego elementu w zakresie docelowym, w którym dwa zakresy źródłowe mają być załączone do pojedynczego posortowanego zakresu reprezentującego Unię dwóch zakresów źródłowych.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje sens, w którym jeden element jest mniejszy niż inny. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , gdy pierwszy element jest mniejszy od drugiego elementu i w przeciwnym razie zwraca **wartość false** .

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych odnoszący się do położenia jednej poza ostatnim elementem w sortowanym zakresie docelowym reprezentującym Unię dwóch zakresów źródłowych.

### <a name="remarks"></a>Uwagi

Posortowane zakresy źródłowe, do których istnieją odwołania, muszą być prawidłowe; wszystkie wskaźniki muszą być odwołujące się, a w każdej sekwencji Ostatnia pozycja musi być osiągalna od pierwszej przez przyrost.

Zakres docelowy nie powinien nakładać się na żaden z zakresów źródłowych i powinien być wystarczająco duży, aby zawierał zakres docelowy.

Posortowane zakresy źródłowe muszą być uporządkowane jako warunek wstępny do zastosowania algorytmu `merge`, zgodnie z tą samą kolejnością, w jakiej ma być używana przez algorytm w celu sortowania połączonych zakresów.

Operacja jest stabilna, ponieważ względna kolejność elementów w każdym zakresie jest zachowywana w zakresie docelowym. Zakresy źródłowe nie są modyfikowane przez algorytm `merge`.

Typy wartości iteratorów danych wejściowych muszą być mniejsze niż porównywalne do uporządkowania, tak aby w przypadku dwóch elementów można było określić, że są one równoważne (w sensie, że żaden z nich nie jest mniejszy niż drugi) lub że jeden z nich jest mniejszy od drugiego. Skutkuje to ustaleniem kolejności dla elementów nierównoważnych. Gdy w obu zakresach źródłowych znajdują się równoważne elementy, elementy z pierwszego zakresu poprzedzają elementy z drugiego zakresu źródłowego w zakresie docelowym. Jeśli zakresy źródłowe zawierają duplikaty elementu, zakres docelowy będzie zawierać maksymalną liczbę elementów występujących w obu zakresach źródłowych.

Złożoność algorytmu jest liniowa z co najwyżej `2 * ((last1 - first1) - (last2 - first2)) - 1` porównaniami.

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

int main()
{
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less than ordering
    int i;
    for ( i = -1 ; i <= 3 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-3 ; ii <= 1 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into a union in ascending order with the default
        // binary predicate less<int>( )
    Result1 = set_union ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Union of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into a union in descending order, specify binary
    // predicate greater<int>( )
    Result2 = set_union ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Union of source ranges with binary predicate greater "
         << "specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into a union applying a user-defined
    // binary predicate mod_lesser
    Result3 = set_union ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Union of source ranges with binary predicate "
         << "mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="shuffle"></a>konfigurację

Powoduje losowe (rozmieszczanie) elementów dla danego zakresu przy użyciu generatora liczb losowych.

```cpp
template<class RandomAccessIterator, class UniformRandomNumberGenerator>
void shuffle(
    RandomAccessIterator first,
    RandomAccessIterator last,
    UniformRandomNumberGenerator&& gen);
```

### <a name="parameters"></a>Parametry

*pierwszy*\
Iterator do pierwszego elementu w zakresie, który ma być przestawiony, włącznie. Muszą spełniać wymagania `RandomAccessIterator` i `ValueSwappable`.

*ostatni*\
Iterator do ostatniego elementu w zakresie, który ma zostać przelosowy, na wyłączność. Muszą spełniać wymagania `RandomAccessIterator` i `ValueSwappable`.

\ *Gen*
Generator liczb losowych, który będzie używany przez funkcję `shuffle()` dla operacji. Musi spełniać wymagania `UniformRandomNumberGenerator`.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji i przykład kodu, który używa `shuffle()`, zobacz [\<losowo >](../standard-library/random.md).

## <a name="sort"></a>porządku

Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryteriów sortowania określonych przez binarny predykat.

```cpp
template<class RandomAccessIterator>
void sort(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void sort(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
void sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator dostępu swobodnego odnoszący się do pozycji pierwszego elementu w zakresie, który ma zostać posortowany.

*ostatni*\
Iterator dostępu swobodnego, odnoszący się do jednej z elementów znajdujących się poza ostatnim elementem w zakresie, który ma zostać posortowany.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje kryterium porównania do spełnienia przez kolejne elementy w kolejności. Ten Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , jeśli dwa argumenty są w porządku i w przeciwnym razie ma **wartość false** . Ta funkcja komparator musi nałożyć ścisłe słabe porządkowanie dla par elementów z sekwencji. Aby uzyskać więcej informacji, zobacz [algorytmy](../standard-library/algorithms.md).

### <a name="remarks"></a>Uwagi

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Elementy są równoważne, ale niekoniecznie równe, jeśli nie są mniejsze od siebie. Algorytm `sort` nie jest stabilny i dlatego nie gwarantuje, że względne porządkowanie elementów równoważnych zostanie zachowane. Algorytm `stable_sort` zachowuje to oryginalne porządkowanie.

Średnia złożoności sortowania jest `O( N log N )`, gdzie *N* = *ostatnią* * - .*

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

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

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

## <a name="sort_heap"></a>sort_heap

Konwertuje stertę na sortowany zakres.

```cpp
template<class RandomAccessIterator>
void sort_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void sort_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*pierwszy*\
Iterator dostępu swobodnego odnoszący się do pozycji pierwszego elementu w stercie docelowej.

*ostatni*\
Iterator dostępu swobodnego, odnoszący się do pozycji jednej poza ostatnim elementem w stercie docelowej.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje sens, w którym jeden element jest mniejszy niż inny. Predykat porównania przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="remarks"></a>Uwagi

Sterty mają dwie właściwości:

- Pierwszy element jest zawsze największy.

- Elementy mogą być dodawane lub usuwane w czasie logarytmu.

Gdy aplikacja, jeśli ten algorytm, zakres, do którego został zastosowany, nie jest już stertą.

Jest to niestabilne sortowanie, ponieważ względna kolejność elementów równorzędnych nie jest konieczna.

Sterty są idealnym sposobem implementacji kolejek priorytetów i są używane w implementacji adaptera [priority_queue](../standard-library/priority-queue-class.md)biblioteki C++ standardowej.

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Złożoność jest najwyżej `N log N`, gdzie *N* = *ostatnią* -  *.*

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

void print(const string& s, const vector<int>& v)
{
    cout << s << ": ( ";

    for (auto i = v.begin(); i != v.end(); ++i)
    {
        cout << *i << " ";
    }

    cout << ")" << endl;
}

int main()
{
    vector<int> v;
    for (int i = 1; i <= 9; ++i)
    {
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

## <a name="stable_partition"></a>stable_partition

Klasyfikuje elementy w zakresie na dwa rozłączne zestawy, z elementami spełniającymi predykat unarny poprzedzającymi te, które go nie spełniają, zachowując względną kolejność elementów równoważnych.

```cpp
template<class BidirectionalIterator, class UnaryPredicate>
BidirectionalIterator stable_partition(
    BidirectionalIterator first,
    BidirectionalIterator last,
    UnaryPredicate pred );

template<class ExecutionPolicy, class BidirectionalIterator, class UnaryPredicate>
BidirectionalIterator stable_partition(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator dwukierunkowy odnoszący się do pozycji pierwszego elementu w zakresie, który ma zostać podzielony na partycje.

*ostatni*\
Iterator dwukierunkowy odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma zostać podzielony na partycje.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje warunek, który ma zostać spełniony, jeśli element ma zostać sklasyfikowany. Predykat jednoargumentowy przyjmuje jeden argument i zwraca **wartość true** , jeśli jest spełniony, lub **false** , jeśli nie jest spełniony.

### <a name="return-value"></a>Wartość zwracana

Iterator dwukierunkowy odnoszący się do pozycji pierwszego elementu w zakresie, który nie spełnia warunku predykatu.

### <a name="remarks"></a>Uwagi

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Elementy *a* i *b* są równoważne, ale niekoniecznie równe, jeśli oba `pred( a, b )` ma wartość false i `pred( b, a )` ma wartość false, gdzie *pred* jest predykatem określonym parametrem. Algorytm `stable_partition` jest stabilny i gwarantuje, że względne kolejność elementów równoważnych zostanie zachowana. Algorytm `partition` nie musi zachować oryginalnego uporządkowania.

### <a name="example"></a>Przykład

```cpp
// alg_stable_partition.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater5 ( int value )
{
    return value > 5;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2, result;

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

## <a name="stable_sort"></a>stable_sort

Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryterium sortowania określonego przez binarny predykat i zachowuje względną kolejność elementów równoważnych.

```cpp
template<class BidirectionalIterator>
void stable_sort(
    BidirectionalIterator first,
    BidirectionalIterator last );

template<class BidirectionalIterator, class Compare>
void stable_sort(
    BidirectionalIterator first,
    BidirectionalIterator last,
    Compare pred );

template<class ExecutionPolicy, class RandomAccessIterator>
void stable_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void stable_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator dwukierunkowy odnoszący się do pozycji pierwszego elementu w zakresie, który ma zostać posortowany.

*ostatni*\
Iterator dwukierunkowy odnoszący się do pozycji jednej poza ostatnim elementem w zakresie, który ma zostać posortowany.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje kryterium porównania do spełnienia przez kolejne elementy w kolejności. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="remarks"></a>Uwagi

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Elementy są równoważne, ale niekoniecznie równe, jeśli nie są mniejsze od siebie. Algorytm `sort` jest stabilny i gwarantuje, że względne kolejność elementów równoważnych zostanie zachowana.

Złożoność w czasie wykonywania `stable_sort` zależy od ilości dostępnej pamięci, ale najlepszym przypadkiem (w przypadku wystarczającej ilości pamięci) jest `O(N log N)` i najgorszy przypadek jest `O(N (log N)^2)`, gdzie *N* = *najpierw* *ostatni* - . Zazwyczaj algorytm `sort` jest znacznie szybszy niż `stable_sort`.

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

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
    }

    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
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

## <a name="swap"></a>wymiany

Pierwsze zastąpienie wymienia wartości dwóch obiektów. Drugie zastąpienie wymienia wartości między dwiema tablicami obiektów.

```cpp
template<class Type>
void swap(
    Type& left,
    Type& right);
template<class Type, size_t N>
void swap(
    Type (& left)[N],
    Type (& right)[N]);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Dla pierwszego przesłonięcia pierwszy obiekt, dla którego zamieni się jego zawartość. W przypadku drugiego przesłonięcia pierwsza tablica obiektów ma zawartooć wymiany.

*prawa*\
Dla pierwszego przesłonięcia, drugi obiekt do wymiany jego zawartości. W przypadku drugiego przesłonięcia druga tablica obiektów ma wymieniać jej zawartość.

### <a name="remarks"></a>Uwagi

Pierwsze Przeciążenie zostało zaprojektowane do działania na poszczególnych obiektach. Drugie Przeciążenie zamienia zawartość obiektów między dwiema tablicami.

### <a name="example"></a>Przykład

```cpp
// alg_swap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2, result;

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

## <a name="swap_ranges"></a>swap_ranges

Zamienia elementy jednego zakresu przez elementy innego zakresu, zakresy mają równe wielkości.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 swap_ranges(
   ForwardIterator1 first1,
   ForwardIterator1 last1,
   ForwardIterator2 first2 );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 swap_ranges(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*first1*\
Iterator do przodu wskazujący na pierwszą pozycję pierwszego zakresu, którego elementy mają być wymieniane.

*last1*\
Iterator do przodu wskazujący na poprzednią pozycję pierwszego zakresu, którego elementy mają być wymieniane.

*first2*\
Iterator do przodu wskazujący na pierwszą pozycję drugiego zakresu, którego elementy mają być wymieniane.

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu wskazujący na poprzednią pozycję drugiego zakresu, którego elementy mają być wymieniane.

### <a name="remarks"></a>Uwagi

Zakresy, do których istnieją odwołania, muszą być prawidłowe; wszystkie wskaźniki muszą być odwołujące się i w każdej sekwencji, która jest dostępna od pierwszej do przyrostu. Drugi zakres musi być tak duży, jak pierwszy zakres.

Złożoność jest liniowa z *last1* - *FIRST1* . Jeśli są wymieniane elementy z kontenerów tego samego typu, należy używać ich funkcji składowej `swap` z tego kontenera, ponieważ funkcja członkowska zazwyczaj ma stałą złożoność.

### <a name="example"></a>Przykład

```cpp
// alg_swap_ranges.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    deque<int> d1;
    vector<int>::iterator v1Iter1;
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
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    cout << "Deque d1 is  ( " ;
    for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
        cout << *d1Iter1 << " ";
    cout << ")." << endl;

    swap_ranges ( v1.begin( ), v1.end( ), d1.begin( ) );

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

## <a name="transform"></a>przekształcania

Stosuje określony obiekt funkcji dla każdego elementu w zakresie sortowania lub dla pary elementów z dwóch zakresów sortowania i kopiuje zwracane wartości obiektu funkcji do zakresu docelowego.

```cpp
template<class InputIterator, class OutputIterator, class UnaryFunction>
OutputIterator transform(
    InputIterator first1,
    InputIterator last1,
    OutputIterator result,
    UnaryFunction func );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryFunction>
OutputIterator transform(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    OutputIterator result,
    BinaryFunction func );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryOperation>
ForwardIterator2 transform(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryOperation op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class BinaryOperation>
ForwardIterator transform(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*first1*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w pierwszym zakresie źródłowym, w którym mają być obsługiwane.

*last1*\
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w pierwszym zakresie źródłowym.

*first2*\
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w drugim zakresie źródłowym, w którym mają być obsługiwane.

\ *wyniku*
Iterator danych wyjściowych odnoszący się do pozycji pierwszego elementu w zakresie docelowym.

\ *Func*
Zdefiniowany przez użytkownika obiekt funkcji jednoargumentowej używany w pierwszej wersji algorytmu, który jest stosowany do każdego elementu w pierwszym zakresie źródłowym lub obiekt funkcji binarnej zdefiniowany przez użytkownika (UD) używany w drugiej wersji algorytmu, który jest stosowany do parowania w kolejności przesyłania dalej , do dwóch zakresów źródłowych.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych odnoszący się do pozycji jednej poza ostatnim elementem w zakresie docelowym, który otrzymuje elementy wyjściowe przekształcone przez obiekt Function.

### <a name="remarks"></a>Uwagi

Zakresy, do których istnieją odwołania, muszą być prawidłowe; wszystkie wskaźniki muszą być odwołujące się, a w każdej sekwencji Ostatnia pozycja musi być osiągalna od pierwszej przez przyrost. Zakres docelowy musi być wystarczająco duży, aby można było zawierać przekształcony zakres źródłowy.

Jeśli *wynik* jest ustawiony na *FIRST1* w pierwszej wersji algorytmu, zakres źródłowy i docelowy będą takie same, a sekwencja zostanie zmodyfikowana. Jednak *wynik* nie może dotyczyć pozycji z zakresu [`first1` + 1, `last1`).

Złożoność jest liniowa z maksymalnie (`last1` - `first1`) porównania.

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
    MultValue ( const Type& value ) : Factor ( value ) { }

    // The function call for the element to be multiplied
    Type operator( ) ( Type& elem ) const
    {
        return elem * Factor;
    }
};

int main()
{
    using namespace std;
    vector<int> v1, v2 ( 7 ), v3 ( 7 );
    vector<int>::iterator Iter1, Iter2 , Iter3;

    // Constructing vector v1
    int i;
    for ( i = -4 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "Original vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Modifying the vector v1 in place
    transform (v1.begin( ), v1.end( ), v1.begin( ), MultValue<int> ( 2 ) );
    cout << "The elements of the vector v1 multiplied by 2 in place gives:"
            << "\n v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Using transform to multiply each element by a factor of 5
    transform ( v1.begin( ), v1.end( ), v2.begin( ), MultValue<int> ( 5 ) );

    cout << "Multiplying the elements of the vector v1mod\n "
            << "by the factor 5 & copying to v2 gives:\n v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // The second version of transform used to multiply the
    // elements of the vectors v1mod & v2 pairwise
    transform ( v1.begin( ), v1.end( ), v2.begin( ), v3.begin( ),
        multiplies<int>( ) );

    cout << "Multiplying elements of the vectors v1mod and v2 pairwise "
            << "gives:\n v3 = ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

```Output
Original vector v1 = ( -4 -3 -2 -1 0 1 2 ).
The elements of the vector v1 multiplied by 2 in place gives:
v1mod = ( -8 -6 -4 -2 0 2 4 ).
Multiplying the elements of the vector v1mod
by the factor 5 & copying to v2 gives:
v2 = ( -40 -30 -20 -10 0 10 20 ).
Multiplying elements of the vectors v1mod and v2 pairwise gives:
v3 = ( 320 180 80 20 0 20 80 ).
```

## <a name="unique"></a>unikatowy

Usuwa zduplikowane elementy, które sąsiadują ze sobą w określonym zakresie.

```cpp
template<class ForwardIterator>
ForwardIterator unique(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class BinaryPredicate>
ForwardIterator unique(
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator unique(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class BinaryPredicate>
ForwardIterator unique(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator do przodu, odnoszący się do pozycji pierwszego elementu w zakresie, który ma być skanowany w celu usunięcia duplikatu.

*ostatni*\
Iterator do przodu, odnoszący się do pozycji jednej poza ostatnim elementem w zakresie do skanowania w celu usunięcia duplikatów.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje warunek do spełnienia, jeśli dwa elementy mają być wykonane jako równoważne. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu z nowym końcem zmodyfikowanej sekwencji, który nie zawiera kolejnych duplikatów, odnoszący się do położenia jednego ostatniego elementu, który nie został usunięty.

### <a name="remarks"></a>Uwagi

Obie formy algorytmu usuwają drugi duplikat kolejnej pary równych elementów.

Operacja algorytmu jest stabilna, tak aby względna kolejność nieusuniętych elementów nie została zmieniona.

Zakres, do którego istnieje odwołanie, musi być prawidłowy; wszystkie wskaźniki muszą być odwołujące się, a w kolejności, w której ostatnia pozycja jest dostępna od pierwszej do przyrostu. Liczba elementów w sekwencji nie jest zmieniana przez algorytm `unique` i elementy poza końcem zmodyfikowanej sekwencji są odwołujące się, ale nie są określone.

Złożoność jest liniowa, wymagając `(last - first) - 1` porównania.

Lista zawiera bardziej wydajną funkcję członkowską "Unique", która może działać lepiej.

Tych algorytmów nie można używać w kontenerach asocjacyjnych.

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

int main()
{
    vector<int> v1;
    vector<int>::iterator v1_Iter1, v1_Iter2, v1_Iter3,
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
    v1_NewEnd1 = unique ( v1.begin( ), v1.end( ) );

    cout << "Removing adjacent duplicates from vector v1 gives\n ( " ;
    for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )
        cout << *v1_Iter1 << " ";
    cout << ")." << endl;

    // Remove consecutive duplicates under the binary prediate mod_equals
    v1_NewEnd2 = unique ( v1.begin( ), v1_NewEnd1 , mod_equal );

    cout << "Removing adjacent duplicates from vector v1 under the\n "
            << " binary predicate mod_equal gives\n ( " ;
    for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )
        cout << *v1_Iter2 << " ";
    cout << ")." << endl;

    // Remove elements if preceded by an element that was greater
    v1_NewEnd3 = unique ( v1.begin( ), v1_NewEnd2, greater<int>( ) );

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

## <a name="unique_copy"></a>unique_copy

Kopiuje elementy z zakresu źródłowego do zakresu docelowego z wyjątkiem zduplikowanych elementów, które ze sobą sąsiadują.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator unique_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result );

template<class InputIterator, class OutputIterator, class BinaryPredicate>
OutputIterator unique_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryPredicate pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 unique_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryPredicate>
ForwardIterator2 unique_copy(ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

\ *exec*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator do przodu, odnoszący się do pozycji pierwszego elementu w zakresie źródłowym, który ma zostać skopiowany.

*ostatni*\
Iterator do przodu, odnoszący się do pozycji jednej poza ostatnim elementem w zakresie źródłowym, który ma zostać skopiowany.

\ *wyniku*
Iterator danych wyjściowych odnoszący się do pozycji pierwszego elementu w zakresie docelowym, który otrzymuje kopię z usuniętymi kolejnymi duplikatami.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje warunek do spełnienia, jeśli dwa elementy mają być wykonane jako równoważne. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych odnoszący się do pozycji jednej poza ostatnim elementem w zakresie docelowym, który otrzymuje kopię z usuniętymi kolejnymi duplikatami.

### <a name="remarks"></a>Uwagi

Obie formy algorytmu usuwają drugi duplikat kolejnej pary równych elementów.

Operacja algorytmu jest stabilna, tak aby względna kolejność nieusuniętych elementów nie została zmieniona.

Zakresy, do których istnieją odwołania, muszą być prawidłowe; wszystkie wskaźniki muszą być odwołujące się, a w ramach sekwencji Ostatnia pozycja jest dostępna od pierwszej do przyrostu.

Złożoność jest liniowa i wymaga porównania (`last` - `first`).

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
    vector<int> v1;
    vector<int>::iterator v1_Iter1, v1_Iter2,
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
    v1_NewEnd1 = unique_copy ( v1.begin( ), v1.begin( ) + 8, v1.begin( ) + 8 );

    cout << "Copying the first half of the vector to the second half\n "
            << "while removing adjacent duplicates gives\n ( " ;
    for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )
        cout << *v1_Iter1 << " ";
    cout << ")." << endl;

    int iv;
    for ( iv = 0 ; iv <= 7 ; iv++ )
        v1.push_back( 10 );

    // Remove consecutive duplicates under the binary prediate mod_equals
    v1_NewEnd2 = unique_copy ( v1.begin( ), v1.begin( ) + 14,
        v1.begin( ) + 14 , mod_equal );

    cout << "Copying the first half of the vector to the second half\n "
            << " removing adjacent duplicates under mod_equals gives\n ( " ;
    for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )
        cout << *v1_Iter2 << " ";
    cout << ")." << endl;
}
```

## <a name="upper_bound"></a>upper_bound

Znajduje pozycję pierwszego elementu w uporządkowanym zakresie, który ma wartość większą niż określona wartość, gdzie kryterium sortowania może być określone przez predykat binarny.

```cpp
template<class ForwardIterator, class Type>
ForwardIterator upper_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator, class Type, class Compare>
ForwardIterator upper_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    Compare pred);
```

### <a name="parameters"></a>Parametry

*pierwszy*\
Pozycja pierwszego elementu w zakresie, który ma być przeszukiwany.

*ostatni*\
Pozycja jednej poza ostatnim elementem w zakresie, który ma być przeszukiwany.

\ *wartości*
Wartość w uporządkowanym zakresie, która musi zostać przekroczona przez wartość elementu, do którego odnosił się iterator.

*pred*\
Zdefiniowany przez użytkownika obiekt funkcji predykatu porównującego, który definiuje sens, w którym jeden element jest mniejszy niż inny. Predykat porównania przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony.

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu do pozycji pierwszego elementu, który ma wartość większą niż określona wartość.

### <a name="remarks"></a>Uwagi

Posortowany zakres źródłowy musi być prawidłowy; wszystkie Iteratory muszą być odwołujące się, a w sekwencji Ostatnia pozycja musi być osiągalna od pierwszej przez przyrost.

Sortowany zakres jest warunkiem wstępnym użycia `upper_bound` i gdzie kryterium sortowania jest takie samo, jak określone przez predykat porównania.

Zakres nie jest modyfikowany przez `upper_bound`.

Typy wartości iteratorów do przodu muszą być mniejsze niż porównywalne do uporządkowania, tak że, w przypadku dwóch elementów, można określić, że są one równoważne (w sensie, że żaden z nich nie jest mniejszy od drugiego) lub że jeden z nich jest mniejszy od drugiego. Powoduje to porządkowanie między nierównoważnymi elementami

Złożoność algorytmu jest logarytmiczna dla iteratorów dostępu losowego i liniowego w przeciwnym razie z liczbą kroków proporcjonalną do (`last - first`).

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

int main()
{
    using namespace std;

    vector<int> v1;
    // Constructing vector v1 with default less-than ordering
    for ( auto i = -1 ; i <= 4 ; ++i )
    {
        v1.push_back( i );
    }

    for ( auto ii =-3 ; ii <= 0 ; ++ii )
    {
        v1.push_back( ii );
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
        << "binary predicate mod_lesser is v3 = ( " ;
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

    // upper_bound of 3 in v3 with the binary predicate mod_lesser
    Result = upper_bound(v3.begin(), v3.end(), 3, mod_lesser);
    cout << "The upper_bound in v3 for the element with a value of 3 is: "
        << *Result << "." << endl;
}
```
