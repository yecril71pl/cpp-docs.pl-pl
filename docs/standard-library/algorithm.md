---
title: '&lt;algorithm&gt;'
ms.date: 11/04/2016
f1_keywords:
- <algorithm>
helpviewer_keywords:
- algorithm header [C++]
- C++ Standard Library, algorithms
- <algorithm> header
ms.assetid: 19f97711-7a67-4a65-8fd1-9a2bd3ca327d
ms.openlocfilehash: 042523cddf640e7cf6fd7f9a1dac9f3adbc360b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411152"
---
# <a name="ltalgorithmgt"></a>&lt;algorithm&gt;

Definiuje funkcje szablonu kontenera standardowej biblioteki języka C++, które wykonują algorytmy.

## <a name="syntax"></a>Składnia

```cpp
(see relevant links below for specific algorithm syntax)
```

## <a name="remarks"></a>Uwagi

Algorytmy standardowej biblioteki języka C++ są ogólne, ponieważ mogą działać na różnych strukturach danych. Struktury danych, które mogą działać na obejmują nie tylko klasy kontenera standardowej biblioteki języka C++, takie jak `vector` i `list`, ale również struktury danych zdefiniowane przez program i tablice elementów, które spełniają wymogi określonego algorytm. Standardowa biblioteka C++ algorytmy osiągają ten poziom ogólności przez dostęp i przechodzenie przez elementy kontenera pośrednio poprzez Iteratory.

Standardowa biblioteka C++ algorytmy przetwarzają zakresy iteratorów, które zazwyczaj są określane przez ich początkową lub końcową pozycję. Odnośne zakresy muszą być prawidłowe w tym sensie, że wszystkie wskaźniki w zakresach muszą być wyłuskiwalne, a w ramach sekwencji każdego zakresu, ostatnia pozycja musi być osiągalna od pierwszej przez inkrementację.

Algorytmy standardowej biblioteki języka C++ rozszerzają działania wspierane przez operacje i funkcji elementów członkowskich każdego kontenera standardowej biblioteki języka C++ i umożliwiają pracę, na przykład z różnymi typami obiektów kontenera, w tym samym czasie. Do przekazywania informacji o przeznaczeniu algorytmów były używane dwa przyrostki.

- `_if` Sufiks wskazuje, że algorytm jest używany z obiektami funkcji działającymi na wartościach elementów, a nie na wartościach samych elementów. `find_if` Algorytm szuka elementów, których wartości spełniają kryterium określone przez obiekt funkcji, a `find` algorytm wyszukuje określoną wartość.

- Przyrostek _copy oznacza, że algorytm nie tylko manipuluje wartościami elementów, ale również kopiuje zmodyfikowane wartości do zakresu docelowego. `reverse` Algorytm Odwraca kolejność elementów w zakresie, a `reverse_copy` algorytm kopiuje również wynik do zakresu docelowego.

Algorytmami standardowej biblioteki C++ często klasyfikuje się według grup, które w jakiś sposób wskazują ich cel lub wymagania. Należą do nich algorytmy modyfikujące, które zmienić wartości elementów w porównaniu nie modyfikowanie algorytmy, które nie obsługują. Algorytmy mutujące zmieniają kolejność elementów, ale nie ich wartości. Algorytmy usuwające mogą wyeliminować elementy z zakresu lub kopii zakresu. Algorytmy sortujące zmieniają kolejność elementów w zakresie na różne sposoby, a algorytmy sortowanego zakresu działają jedynie na zakresy, których elementy zostały posortowane w określony sposób.

Algorytmy numeryczne standardowej biblioteki języka C++, które są dostępne dla numerycznego przetwarzania, mają własny plik nagłówkowy [ \<liczbowych >](../standard-library/numeric.md), a obiekty i adaptery funkcji są definiowane w nagłówku [ \<funkcjonalności >](../standard-library/functional.md) obiektów funkcyjnych, które zwracają wartości logiczne są znane jako predykaty. Domyślny predykat binarny jest porównanie `operator<`. Ogólnie rzecz biorąc, szeregowane elementy muszą być mniej niż porównywalne, tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi), czy że jeden jest mniejszy od drugiego. Skutkuje to ustaleniem kolejności elementów nierównoważnych.

### <a name="function-templates"></a>Szablony funkcji

|Szablon funkcji|Opis|
|-|-|
|[adjacent_find](../standard-library/algorithm-functions.md#adjacent_find)|Wyszukuje dwa sąsiadujące elementy, które są równe lub spełniają określony warunek.|
|[all_of](../standard-library/algorithm-functions.md#all_of)|Zwraca **true** kiedy warunek jest obecny dla każdego elementu z podanego zakresu.|
|[any_of](../standard-library/algorithm-functions.md#any_of)|Zwraca **true** kiedy warunek występuje co najmniej raz w określonym zakresie elementów.|
|[binary_search](../standard-library/algorithm-functions.md#binary_search)|Testuje, czy w sortowanym zakresie istnieje element, który jest równy określonej wartości lub który jest odpowiednikiem w sensie określonym przez predykat binarny.|
|[Kopiuj](../standard-library/algorithm-functions.md#copy)|Przypisuje wartości elementów z zakresu źródłowego do zakresu docelowego, iterując przez sekwencję źródłową elementów oraz przypisując im nowe pozycje w kierunku do przodu.|
|[copy_backward](../standard-library/algorithm-functions.md#copy_backward)|Przypisuje wartości elementów z zakresu źródłowego do zakresu docelowego, iterując przez sekwencję źródłową elementów oraz przypisując im nowe pozycje w kierunku do tyłu.|
|[copy_if](../standard-library/algorithm-functions.md#copy_if)|Kopiuj wszystkie elementy w danym zakresie, które testują **true** dla określonego warunku|
|[copy_n](../standard-library/algorithm-functions.md#copy_n)|Kopiuje określoną liczbę elementów.|
|[Liczba](../standard-library/algorithm-functions.md#count)|Zwraca liczbę elementów w zakresie, których wartości pasują do określonej wartości.|
|[count_if](../standard-library/algorithm-functions.md#count_if)|Zwraca liczbę elementów w zakresie, których wartości pasują do określonego warunku.|
|[equal](../standard-library/algorithm-functions.md#equal)|Porównuje dwa zakresy element po elemencie, pod względem równości lub równoważności w sensie określonym przez predykat binarny.|
|[equal_range](../standard-library/algorithm-functions.md#equal_range)|Wyszukuje parę pozycji w uporządkowanym zakresie, pierwszą mniejszą lub równoważną położeniu określonego elementu, a drugą większą niż pozycja elementu, gdzie sens równoważności lub szeregowania używany do ustanawiania pozycji w sekwencji może zostać określony przez predykat binarny.|
|[Wypełnienie](../standard-library/algorithm-functions.md#fill)|Przypisuje tę samą nową wartość każdemu elementowi w określonym zakresie.|
|[fill_n](../standard-library/algorithm-functions.md#fill_n)|Przypisuje nową wartość określonej liczbie elementów z zakresu, począwszy od konkretnego elementu.|
|[Znajdź](../standard-library/algorithm-functions.md#find)|Lokalizuje pozycję pierwszego wystąpienia elementu w zakresie, który ma określoną wartość.|
|[find_end —](../standard-library/algorithm-functions.md#find_end)|Wyszukuje w zakresie ostatnią podsekwencję, która jest identyczna z określoną sekwencją lub jest równoważna w sensie określonym przez predykat binarny.|
|[find_first_of](../standard-library/algorithm-functions.md#find_first_of)|Wyszukuje pierwsze wystąpienie którejś z kilku wartości w zakresie docelowym lub pierwsze wystąpienie któregoś z kilku elementów, które są równoważne w sensie określonym przez predykat binarny dla określonego zestawu elementów.|
|[find_if](../standard-library/algorithm-functions.md#find_if)|Lokalizuje pozycję pierwszego wystąpienia elementu w zakresie, który spełnia określony warunek.|
|[find_if_not](../standard-library/algorithm-functions.md#find_if_not)|Zwraca pierwszy element we wskazanym zakresie, który nie spełnia warunku.|
|[for_each](../standard-library/algorithm-functions.md#for_each)|Stosuje określony obiekt funkcji do każdego elementu w kolejności do przodu w zakresie i zwraca obiekt funkcji.|
|[Generowanie](../standard-library/algorithm-functions.md#generate)|Przypisuje wartości generowane przez obiekt funkcji do każdego elementu w zakresie.|
|[generate_n](../standard-library/algorithm-functions.md#generate_n)|Przypisuje wartości generowane przez obiekt funkcji określonej liczbie elementów w zakresie i wraca do jednej pozycji poza ostatnią przypisaną wartością.|
|[zawiera](../standard-library/algorithm-functions.md#includes)|Sprawdza, czy jeden posortowany zakres zawiera wszystkie elementy zawarte w drugim posortowanym zakresie, gdzie kryterium szeregowania lub równoważności między elementami może zostać określone przez predykat binarny.|
|[inplace_merge](../standard-library/algorithm-functions.md#inplace_merge)|Łączy elementy z dwóch następujących po sobie posortowanych zakresów w pojedynczy posortowany zakres, gdzie kryterium szeregowania może być określone przez predykat binarny.|
|[is_heap](../standard-library/algorithm-functions.md#is_heap)|Zwraca **true** Jeśli elementy w określonym zakresie tworzą stertę.|
|[is_heap_until](../standard-library/algorithm-functions.md#is_heap_until)|Zwraca **true** Jeśli określony zakres tworzy stertę do ostatniego elementu.|
|[is_partitioned](../standard-library/algorithm-functions.md#is_partitioned)|Zwraca **true** Jeśli wszystkie elementy w danym zakresie, który należy przetestować **true** dla warunku występować przed żadnych elementów, które testują **false**.|
|[is_permutation](../standard-library/algorithm-functions.md#is_permutation)|Określa, czy elementy w określonym zakresie tworzą prawidłowy permutacji.|
|[is_sorted](../standard-library/algorithm-functions.md#is_sorted)|Zwraca **true** Jeśli elementy w określonym zakresie są w kolejności posortowanej.|
|[is_sorted_until](../standard-library/algorithm-functions.md#is_sorted_until)|Zwraca **true** Jeśli elementy w określonym zakresie są w kolejności posortowanej.|
|[iter_swap](../standard-library/algorithm-functions.md#iter_swap)|Wymienia dwie wartości, do których odnosi się para określonych iteratorów.|
|[lexicographical_compare —](../standard-library/algorithm-functions.md#lexicographical_compare)|Porównuje dwie sekwencje element po elemencie, aby określić, która z nich jest mniejsza.|
|[lower_bound](../standard-library/algorithm-functions.md#lower_bound)|Znajduje pozycję pierwszego elementu w uporządkowanym zakresie, który ma wartość większą niż lub równoważną określonej wartości, gdzie kryterium szeregowania może być określone przez predykat binarny.|
|[make_heap](../standard-library/algorithm-functions.md#make_heap)|Konwertuje elementy z określonego zakresu na stertę, w której pierwszy element jest największy i dla której kryterium sortowania może być określone przez predykat binarny.|
|[max](../standard-library/algorithm-functions.md#max)|Porównuje dwa obiekty i zwraca większy z nich, gdzie kryterium sortowania może być określone przez predykat binarny.|
|[max_element](../standard-library/algorithm-functions.md#max_element)|Znajduje pierwsze wystąpienie największego elementu w określonym zakresie, gdzie kryterium sortowania może być określone przez predykat binarny.|
|[merge](../standard-library/algorithm-functions.md#merge)|Łączy wszystkie elementy z dwóch następujących po sobie posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.|
|[min](../standard-library/algorithm-functions.md#min)|Porównuje dwa obiekty i zwraca mniejszy z nich, gdzie kryterium sortowania może być określone przez predykat binarny.|
|[min_element](../standard-library/algorithm-functions.md#min_element)|Znajduje pierwsze wystąpienie najmniejszego elementu w określonym zakresie, gdzie kryterium sortowania może być określone przez predykat binarny.|
|[minmax](../standard-library/algorithm-functions.md#minmax)|Porównuje dwa parametry wejściowe i zwraca je jako parę w kolejności od najmniejszego do największego.|
|[minmax_element](../standard-library/algorithm-functions.md#minmax_element)|Wykonuje pracę wykonaną przez [min_element](../standard-library/algorithm-functions.md#min_element) i [max_element](../standard-library/algorithm-functions.md#max_element) w jednym wywołaniu.|
|[mismatch](../standard-library/algorithm-functions.md#mismatch)|Porównuje dwa zakresy element po elemencie pod względem równości lub odpowiedniości w sensie określonym przez predykat binarny i lokalizuje pierwsze miejsce, w którym występuje różnica.|
|[&lt;algorytmu podpisu&gt; Przenieś](../standard-library/algorithm-functions.md#alg_move)|Przenieś elementy związane z określonym zakresem.|
|[move_backward](../standard-library/algorithm-functions.md#move_backward)|Przenosi elementy jednego iteratora do drugiego. Przeniesienie rozpoczyna się od ostatniego elementu w określonym zakresie, a kończy się na pierwszym elemencie w tym zakresie.|
|[next_permutation](../standard-library/algorithm-functions.md#next_permutation)|Zmienia kolejność elementów w zakresie, tak że oryginalna kolejność jest zastąpiona przez leksykograficznie kolejną większą permutację, o ile takowa istnieje, gdzie sens „kolejna” może być określony przez predykat binarny.|
|[none_of](../standard-library/algorithm-functions.md#none_of)|Zwraca **true** kiedy warunek nigdy nie jest obecny wśród elementów z podanego zakresu.|
|[nth_element](../standard-library/algorithm-functions.md#nth_element)|Dzieli zakres elementów, poprawnie lokalizując *n*Ty element sekwencji w zakresie tak, aby wszystkie elementy przed nim są mniejsze niż lub równe go oraz wszystkie elementy, które następują w sekwencji jest większa niż lub równe do niego.|
|[partial_sort](../standard-library/algorithm-functions.md#partial_sort)|Rozmieszcza określoną liczbę mniejszych elementów w zakresie w niemalejącej kolejności, lub według kryteriów sortowania określonych przez binarny predykat.|
|[partial_sort_copy](../standard-library/algorithm-functions.md#partial_sort_copy)|Kopiuje elementy z zakresu źródłowego do zakresu docelowego, gdzie elementy źródłowe są uporządkowane według albo zasady mniejszy niż, albo innego określonego predykatu binarnego.|
|[partition](../standard-library/algorithm-functions.md#partition)|Klasyfikuje elementy w zakresie na dwa rozłączne zestawy, z elementami spełniającymi predykat unarny poprzedzającymi te, które go nie spełniają.|
|[partition_copy](../standard-library/algorithm-functions.md#partition_copy)|Kopiuje elementy, dla których warunek jest **true** do jednego miejsca docelowego i dla których warunek jest **false** do innego. Elementy muszą pochodzić z określonego zakresu.|
|[partition_point](../standard-library/algorithm-functions.md#partition_point)|Zwraca pierwszy element w danym zakresie, który nie spełnia warunku. Elementy są sortowane, aby te, które spełniają warunek, występowały przed tymi, które go nie spełniają.|
|[pop_heap](../standard-library/algorithm-functions.md#pop_heap)|Usuwa największy element z przodu sterty do przedostatniej pozycji w zakresie, a następnie tworzy nową stertę z pozostałych elementów.|
|[prev_permutation](../standard-library/algorithm-functions.md#prev_permutation)|Zmienia kolejność elementów w zakresie, tak że oryginalna kolejność jest zastąpiona przez leksykograficznie kolejną większą permutację, o ile takowa istnieje, gdzie sens „kolejna” może być określony przez predykat binarny.|
|[push_heap](../standard-library/algorithm-functions.md#push_heap)|Dodaje element znajdujący się na końcu zakresu do istniejącej sterty, która składa się z poprzednich elementów w zakresie.|
|[random_shuffle](../standard-library/algorithm-functions.md#random_shuffle)|Ponownie rozmieszcza sekwencję *N* elementów w zakresie do jednego z *N*! możliwych rozmieszczeń wybranych losowo.|
|[remove](../standard-library/algorithm-functions.md#remove)|Eliminuje określoną wartość z danego zakresu bez zakłócania kolejności pozostałych elementów i zwracania końca nowego zakresu wolnego od określonej wartości.|
|[remove_copy](../standard-library/algorithm-functions.md#remove_copy)|Kopiuje elementy z zakresu źródłowego do zakresu docelowego, z tym wyjątkiem, że elementy o określonej wartości nie są kopiowane, bez naruszania kolejności pozostałych elementów i zwracania końca nowego zakresu docelowego.|
|[remove_copy_if](../standard-library/algorithm-functions.md#remove_copy_if)|Kopiuje elementy z zakresu źródłowego do zakresu docelowego, z tym wyjątkiem, że elementy spełniające predykat nie są kopiowane, bez naruszania kolejności pozostałych elementów i zwracania końca nowego zakresu docelowego.|
|[remove_if](../standard-library/algorithm-functions.md#remove_if)|Eliminuje elementy, które spełniają predykat, z danego zakresu bez zakłócania kolejności pozostałych elementów i zwracania końca nowego zakresu wolnego od określonej wartości.|
|[Zastąp](../standard-library/algorithm-functions.md#replace)|Sprawdza każdy element w zakresie i zastępuje go, jeśli odpowiada określonej wartości.|
|[replace_copy](../standard-library/algorithm-functions.md#replace_copy)|Sprawdza każdy element w zakresie źródłowym i zastępuje go, jeśli odpowiada określonej wartości, jednocześnie kopiując wynik do nowego zakresu docelowego.|
|[replace_copy_if](../standard-library/algorithm-functions.md#replace_copy_if)|Sprawdza każdy element w zakresie źródłowym i zastępuje go, jeśli spełnia określony predykat, jednocześnie kopiując wynik do nowego zakresu docelowego.|
|[replace_if](../standard-library/algorithm-functions.md#replace_if)|Sprawdza każdy element w zakresie i zastępuje go, jeśli spełnia określony predykat.|
|[reverse](../standard-library/algorithm-functions.md#reverse)|Odwraca kolejność elementów w obrębie zakresu.|
|[reverse_copy](../standard-library/algorithm-functions.md#reverse_copy)|Odwraca kolejność elementów w obrębie zakresu źródłowego, jednocześnie kopiując je do zakresu docelowego|
|[Obróć](../standard-library/algorithm-functions.md#rotate)|Wymienia elementy znajdujące się w dwóch sąsiednich zakresach.|
|[rotate_copy](../standard-library/algorithm-functions.md#rotate_copy)|Wymienia elementy w dwóch sąsiednich zakresach w ramach zakresu źródłowego i kopiuje wynik do zakresu docelowego.|
|[Wyszukiwanie](../standard-library/algorithm-functions.md#search)|Wyszukuje pierwsze wystąpienie sekwencji w zakresie docelowym, której elementy są równe tym w danej sekwencji elementów lub której elementy są równoważne w sensie określonym przez predykat binarny dla elementów w danej sekwencji.|
|[search_n](../standard-library/algorithm-functions.md#search_n)|Wyszukuje pierwszą podsekwencję w zakresie, w której określona liczba elementów ma określoną wartość lub relację do tej wartości określoną przez predykat binarny.|
|[set_difference](../standard-library/algorithm-functions.md#set_difference)|Łączy w sobie wszystkie elementy, które należą do jednego posortowanego zakresu źródłowego, ale nie do drugiego posortowanego zakresu źródłowego, w pojedynczy, posortowany zakres docelowy, gdzie kryterium sortowania może być określone przez predykat binarny.|
|[set_intersection](../standard-library/algorithm-functions.md#set_intersection)|Łączy w sobie wszystkie elementy, które należą do obu posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.|
|[set_symmetric_difference](../standard-library/algorithm-functions.md#set_symmetric_difference)|Łączy w sobie wszystkie elementy, które należą do jednego z, ale nie obu posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.|
|[set_union](../standard-library/algorithm-functions.md#set_union)|Łączy w sobie wszystkie elementy, które należą do przynajmniej jednego z dwóch posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.|
|[sort](../standard-library/algorithm-functions.md#sort)|Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryteriów sortowania określonych przez binarny predykat.|
|[shuffle](../standard-library/algorithm-functions.md#shuffle)|Elementy przesuwa (Reorganizuje) dla określonego zakresu przy użyciu generator liczb losowych.|
|[sort_heap](../standard-library/algorithm-functions.md#sort_heap)|Konwertuje stertę na sortowany zakres.|
|[stable_partition](../standard-library/algorithm-functions.md#stable_partition)|Klasyfikuje elementy w zakresie na dwa rozłączne zestawy, z elementami spełniającymi predykat unarny poprzedzającymi te, które go nie spełniają, zachowując względną kolejność elementów równoważnych.|
|[stable_sort](../standard-library/algorithm-functions.md#stable_sort)|Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryterium sortowania określonego przez binarny predykat i zachowuje względną kolejność elementów równoważnych.|
|[swap](../standard-library/algorithm-functions.md#swap)|Wymienia wartości elementów między dwoma typami obiektów, przypisując zawartość pierwszego obiektu do drugiego obiektu, a zawartość drugiego do pierwszego.|
|[swap_ranges](../standard-library/algorithm-functions.md#swap_ranges)|Zamienia elementy jednego zakresu przez elementy innego zakresu, zakresy mają równe wielkości.|
|[transform](../standard-library/algorithm-functions.md#transform)|Stosuje określony obiekt funkcji dla każdego elementu w zakresie sortowania lub dla pary elementów z dwóch zakresów sortowania i kopiuje zwracane wartości obiektu funkcji do zakresu docelowego.|
|[unique](../standard-library/algorithm-functions.md#unique)|Usuwa zduplikowane elementy, które sąsiadują ze sobą w określonym zakresie.|
|[unique_copy](../standard-library/algorithm-functions.md#unique_copy)|Kopiuje elementy z zakresu źródłowego do zakresu docelowego z wyjątkiem zduplikowanych elementów, które ze sobą sąsiadują.|
|[upper_bound —](../standard-library/algorithm-functions.md#upper_bound)|Znajduje pozycję pierwszego elementu w uporządkowanym zakresie, który ma wartość większą niż określona wartość, gdzie kryterium sortowania może być określone przez predykat binarny.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
