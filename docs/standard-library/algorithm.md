---
title: '&lt;algorytm&gt;'
ms.date: 11/04/2016
f1_keywords:
- <algorithm>
helpviewer_keywords:
- algorithm header [C++]
- C++ Standard Library, algorithms
- <algorithm> header
ms.assetid: 19f97711-7a67-4a65-8fd1-9a2bd3ca327d
ms.openlocfilehash: d36ee5ea0d38455b52cb988dc30b13d47be16e53
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623844"
---
# <a name="ltalgorithmgt"></a>&lt;algorytm&gt;

Definiuje funkcje szablonu kontenera standardowej biblioteki języka C++, które wykonują algorytmy.

## <a name="syntax"></a>Składnia

```cpp
(see relevant links below for specific algorithm syntax)
```

> [!NOTE]
> \<algorithm>Biblioteka używa również `#include <initializer_list>` instrukcji.

## <a name="remarks"></a>Uwagi

Algorytmy standardowej biblioteki języka C++ są ogólne, ponieważ mogą działać na różnych strukturach danych. Struktury danych, na których mogą pracować, obejmują nie tylko klasy kontenerów standardowej biblioteki języka C++, takie jak `vector` i `list` , ale również struktury danych zdefiniowane przez program i tablice elementów, które spełniają wymagania określonego algorytmu. Algorytmy standardowej biblioteki języka C++ osiągają ten poziom ogólny poprzez dostęp do elementów kontenera pośrednio i przechodzenie przez nie przez Iteratory.

Algorytmy standardowej biblioteki języka C++ przetwarzają zakresy iteratorów, które zazwyczaj są określane przez ich początkową lub końcową pozycję. Odnośne zakresy muszą być prawidłowe w tym sensie, że wszystkie wskaźniki w zakresach muszą być wyłuskiwalne, a w ramach sekwencji każdego zakresu, ostatnia pozycja musi być osiągalna od pierwszej przez inkrementację.

Algorytmy standardowej biblioteki języka C++ zwiększają działania obsługiwane przez operacje i funkcje elementów członkowskich każdego kontenera standardowej biblioteki C++ i umożliwiają pracę, na przykład z różnymi typami obiektów kontenera w tym samym czasie. Do przekazywania informacji o przeznaczeniu algorytmów były używane dwa przyrostki.

- `_if`Sufiks wskazuje, że algorytm jest używany z obiektami funkcji, które działają na wartościach elementów, a nie samych elementów. `find_if`Algorytm szuka elementów, których wartości spełniają kryterium określone przez obiekt funkcji, a `find` algorytm wyszukuje określoną wartość.

- Przyrostek _copy oznacza, że algorytm nie tylko manipuluje wartościami elementów, ale również kopiuje zmodyfikowane wartości do zakresu docelowego. `reverse`Algorytm odwraca kolejność elementów w zakresie, a `reverse_copy` algorytm kopiuje także wynik do zakresu docelowego.

Algorytmy standardowej biblioteki języka C++ często są klasyfikowane do grup, które wskazują na ich przeznaczenie lub wymagania. Obejmują one modyfikowanie algorytmów, które zmieniają wartość elementów w porównaniu z niemodyfikującymi algorytmami, które nie są modyfikowane. Algorytmy mutujące zmieniają kolejność elementów, ale nie ich wartości. Algorytmy usuwające mogą wyeliminować elementy z zakresu lub kopii zakresu. Algorytmy sortowania umożliwiają zmianę kolejności elementów w zakresie na różne sposoby i posortowane algorytmy zakresów działają tylko na zakresach, których elementy zostały posortowane w określony sposób.

Algorytmy liczbowe standardowej biblioteki języka C++, które są udostępniane do przetwarzania liczbowego, mają własny plik nagłówkowy [\<numeric>](numeric.md) , a obiekty funkcji i adaptery są zdefiniowane w [\<functional>](functional.md) obiektach funkcji nagłówka, które zwracają wartości logiczne, są znane jako predykaty. Domyślnym predykatem binarnym jest porównanie `operator<` . Ogólnie rzecz biorąc, szeregowane elementy muszą być mniej niż porównywalne, tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi), czy że jeden jest mniejszy od drugiego. Skutkuje to ustaleniem kolejności elementów nierównoważnych.

### <a name="function-templates"></a>Szablony funkcji

|||
|-|-|
|[adjacent_find](algorithm-functions.md#adjacent_find)|Wyszukuje dwa sąsiadujące elementy, które są równe lub spełniają określony warunek.|
|[all_of](algorithm-functions.md#all_of)|Zwraca **wartość PRAWDA** , jeśli warunek jest obecny dla każdego elementu w danym zakresie.|
|[any_of](algorithm-functions.md#any_of)|Zwraca **wartość PRAWDA** , jeśli warunek występuje co najmniej raz w określonym zakresie elementów.|
|[binary_search](algorithm-functions.md#binary_search)|Testuje, czy w sortowanym zakresie istnieje element, który jest równy określonej wartości lub który jest odpowiednikiem w sensie określonym przez predykat binarny.|
|[opraw](algorithm-functions.md#clamp)||
|[kopiowane](algorithm-functions.md#copy)|Przypisuje wartości elementów z zakresu źródłowego do zakresu docelowego, iterując przez sekwencję źródłową elementów oraz przypisując im nowe pozycje w kierunku do przodu.|
|[copy_backward](algorithm-functions.md#copy_backward)|Przypisuje wartości elementów z zakresu źródłowego do zakresu docelowego, iterując przez sekwencję źródłową elementów oraz przypisując im nowe pozycje w kierunku do tyłu.|
|[copy_if](algorithm-functions.md#copy_if)|Kopiuj wszystkie elementy w danym zakresie, które testują **true** dla określonego warunku|
|[copy_n](algorithm-functions.md#copy_n)|Kopiuje określoną liczbę elementów.|
|[count](algorithm-functions.md#count)|Zwraca liczbę elementów w zakresie, których wartości pasują do określonej wartości.|
|[count_if](algorithm-functions.md#count_if)|Zwraca liczbę elementów w zakresie, których wartości pasują do określonego warunku.|
|[większy](algorithm-functions.md#equal)|Porównuje dwa zakresy element po elemencie, pod względem równości lub równoważności w sensie określonym przez predykat binarny.|
|[equal_range](algorithm-functions.md#equal_range)|Wyszukuje parę pozycji w uporządkowanym zakresie, pierwszą mniejszą lub równoważną położeniu określonego elementu, a drugą większą niż pozycja elementu, gdzie sens równoważności lub szeregowania używany do ustanawiania pozycji w sekwencji może zostać określony przez predykat binarny.|
|[pełni](algorithm-functions.md#fill)|Przypisuje tę samą nową wartość każdemu elementowi w określonym zakresie.|
|[fill_n](algorithm-functions.md#fill_n)|Przypisuje nową wartość określonej liczbie elementów z zakresu, począwszy od konkretnego elementu.|
|[find](algorithm-functions.md#find)|Lokalizuje pozycję pierwszego wystąpienia elementu w zakresie, który ma określoną wartość.|
|[find_end](algorithm-functions.md#find_end)|Wyszukuje w zakresie ostatnią podsekwencję, która jest identyczna z określoną sekwencją lub jest równoważna w sensie określonym przez predykat binarny.|
|[find_first_of](algorithm-functions.md#find_first_of)|Wyszukuje pierwsze wystąpienie którejś z kilku wartości w zakresie docelowym lub pierwsze wystąpienie któregoś z kilku elementów, które są równoważne w sensie określonym przez predykat binarny dla określonego zestawu elementów.|
|[find_if](algorithm-functions.md#find_if)|Lokalizuje pozycję pierwszego wystąpienia elementu w zakresie, który spełnia określony warunek.|
|[find_if_not](algorithm-functions.md#find_if_not)|Zwraca pierwszy element we wskazanym zakresie, który nie spełnia warunku.|
|[for_each](algorithm-functions.md#for_each)|Stosuje określony obiekt funkcji do każdego elementu w kolejności do przodu w zakresie i zwraca obiekt funkcji.|
|[for_each_n](algorithm-functions.md#for_each_n)||
|[utworzenie](algorithm-functions.md#generate)|Przypisuje wartości generowane przez obiekt funkcji do każdego elementu w zakresie.|
|[generate_n](algorithm-functions.md#generate_n)|Przypisuje wartości generowane przez obiekt funkcji określonej liczbie elementów w zakresie i wraca do jednej pozycji poza ostatnią przypisaną wartością.|
|[łącznie](algorithm-functions.md#includes)|Sprawdza, czy jeden posortowany zakres zawiera wszystkie elementy zawarte w drugim posortowanym zakresie, gdzie kryterium szeregowania lub równoważności między elementami może zostać określone przez predykat binarny.|
|[inplace_merge](algorithm-functions.md#inplace_merge)|Łączy elementy z dwóch następujących po sobie posortowanych zakresów w pojedynczy posortowany zakres, gdzie kryterium szeregowania może być określone przez predykat binarny.|
|[is_heap](algorithm-functions.md#is_heap)|Zwraca **wartość true** , jeśli elementy w określonym zakresie tworzą stertę.|
|[is_heap_until](algorithm-functions.md#is_heap_until)|Zwraca **wartość true** , jeśli określony zakres tworzy stertę do momentu ostatniego elementu.|
|[is_partitioned](algorithm-functions.md#is_partitioned)|Zwraca **wartość true** , jeśli wszystkie elementy w danym zakresie, które testują **wartość true** dla warunku, są przed wszystkimi elementami, które testują **wartość false**.|
|[is_permutation](algorithm-functions.md#is_permutation)|Określa, czy elementy w danym zakresie tworzą prawidłową permutację.|
|[is_sorted](algorithm-functions.md#is_sorted)|Zwraca **wartość true** , jeśli elementy w określonym zakresie są sortowane według kolejności.|
|[is_sorted_until](algorithm-functions.md#is_sorted_until)|Zwraca **wartość true** , jeśli elementy w określonym zakresie są sortowane według kolejności.|
|[iter_swap](algorithm-functions.md#iter_swap)|Wymienia dwie wartości, do których odnosi się para określonych iteratorów.|
|[lexicographical_compare](algorithm-functions.md#lexicographical_compare)|Porównuje dwie sekwencje element po elemencie, aby określić, która z nich jest mniejsza.|
|[lower_bound](algorithm-functions.md#lower_bound)|Znajduje pozycję pierwszego elementu w uporządkowanym zakresie, który ma wartość większą niż lub równoważną określonej wartości, gdzie kryterium szeregowania może być określone przez predykat binarny.|
|[make_heap](algorithm-functions.md#make_heap)|Konwertuje elementy z określonego zakresu na stertę, w której pierwszy element jest największy i dla której kryterium sortowania może być określone przez predykat binarny.|
|[Maksymalny](algorithm-functions.md#max)|Porównuje dwa obiekty i zwraca większy z nich, gdzie kryterium sortowania może być określone przez predykat binarny.|
|[max_element](algorithm-functions.md#max_element)|Znajduje pierwsze wystąpienie największego elementu w określonym zakresie, gdzie kryterium sortowania może być określone przez predykat binarny.|
|[połączenie](algorithm-functions.md#merge)|Łączy wszystkie elementy z dwóch następujących po sobie posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.|
|[długości](algorithm-functions.md#min)|Porównuje dwa obiekty i zwraca mniejszy z nich, gdzie kryterium sortowania może być określone przez predykat binarny.|
|[min_element](algorithm-functions.md#min_element)|Znajduje pierwsze wystąpienie najmniejszego elementu w określonym zakresie, gdzie kryterium sortowania może być określone przez predykat binarny.|
|[MinMax](algorithm-functions.md#minmax)|Porównuje dwa parametry wejściowe i zwraca je jako parę w kolejności od najmniejszego do największego.|
|[minmax_element](algorithm-functions.md#minmax_element)|Wykonuje działania wykonywane przez [min_element](algorithm-functions.md#min_element) i [max_element](algorithm-functions.md#max_element) w jednym wywołaniu.|
|[nieodpowiedni](algorithm-functions.md#mismatch)|Porównuje dwa zakresy element po elemencie pod względem równości lub odpowiedniości w sensie określonym przez predykat binarny i lokalizuje pierwsze miejsce, w którym występuje różnica.|
|[&lt;alg &gt; Przenieś](algorithm-functions.md#alg_move)|Przenieś elementy związane z określonym zakresem.|
|[move_backward](algorithm-functions.md#move_backward)|Przenosi elementy jednego iteratora do drugiego. Przeniesienie rozpoczyna się od ostatniego elementu w określonym zakresie, a kończy się na pierwszym elemencie w tym zakresie.|
|[next_permutation](algorithm-functions.md#next_permutation)|Zmienia kolejność elementów w zakresie, tak że oryginalna kolejność jest zastąpiona przez leksykograficznie kolejną większą permutację, o ile takowa istnieje, gdzie sens „kolejna” może być określony przez predykat binarny.|
|[none_of](algorithm-functions.md#none_of)|Zwraca **wartość PRAWDA** , jeśli warunek nigdy nie występuje między elementami w danym zakresie.|
|[nth_element](algorithm-functions.md#nth_element)|Dzieli zakres elementów, poprawnie lokalizując *n*-ty element sekwencji w zakresie, tak aby wszystkie elementy przed nim były mniejsze lub równe, a wszystkie elementy, które podążają w sekwencji, są większe lub równe.|
|[partial_sort](algorithm-functions.md#partial_sort)|Rozmieszcza określoną liczbę mniejszych elementów w zakresie w niemalejącej kolejności, lub według kryteriów sortowania określonych przez binarny predykat.|
|[partial_sort_copy](algorithm-functions.md#partial_sort_copy)|Kopiuje elementy z zakresu źródłowego do zakresu docelowego, gdzie elementy źródłowe są uporządkowane według albo zasady mniejszy niż, albo innego określonego predykatu binarnego.|
|[podzielić](algorithm-functions.md#partition)|Klasyfikuje elementy w zakresie na dwa rozłączne zestawy, z elementami spełniającymi predykat unarny poprzedzającymi te, które go nie spełniają.|
|[partition_copy](algorithm-functions.md#partition_copy)|Kopiuje elementy, dla których warunek ma **wartość true** do jednego miejsca docelowego i dla którego warunek ma **wartość false** . Elementy muszą pochodzić z określonego zakresu.|
|[partition_point](algorithm-functions.md#partition_point)|Zwraca pierwszy element w danym zakresie, który nie spełnia warunku. Elementy są sortowane, aby te, które spełniają warunek, występowały przed tymi, które go nie spełniają.|
|[pop_heap](algorithm-functions.md#pop_heap)|Usuwa największy element z przodu sterty do przedostatniej pozycji w zakresie, a następnie tworzy nową stertę z pozostałych elementów.|
|[prev_permutation](algorithm-functions.md#prev_permutation)|Zmienia kolejność elementów w zakresie, tak że oryginalna kolejność jest zastąpiona przez leksykograficznie kolejną większą permutację, o ile takowa istnieje, gdzie sens „kolejna” może być określony przez predykat binarny.|
|[push_heap](algorithm-functions.md#push_heap)|Dodaje element znajdujący się na końcu zakresu do istniejącej sterty, która składa się z poprzednich elementów w zakresie.|
|[random_shuffle](algorithm-functions.md#random_shuffle)|Ponownie rozmieszcza sekwencję *N* elementów w zakresie w jeden z *n*! możliwe rozwiązania wybrane losowo.|
|[usuwa](algorithm-functions.md#remove)|Eliminuje określoną wartość z danego zakresu bez zakłócania kolejności pozostałych elementów i zwracania końca nowego zakresu wolnego od określonej wartości.|
|[remove_copy](algorithm-functions.md#remove_copy)|Kopiuje elementy z zakresu źródłowego do zakresu docelowego, z tym wyjątkiem, że elementy o określonej wartości nie są kopiowane, bez naruszania kolejności pozostałych elementów i zwracania końca nowego zakresu docelowego.|
|[remove_copy_if](algorithm-functions.md#remove_copy_if)|Kopiuje elementy z zakresu źródłowego do zakresu docelowego, z tym wyjątkiem, że elementy spełniające predykat nie są kopiowane, bez naruszania kolejności pozostałych elementów i zwracania końca nowego zakresu docelowego.|
|[remove_if](algorithm-functions.md#remove_if)|Eliminuje elementy, które spełniają predykat, z danego zakresu bez zakłócania kolejności pozostałych elementów i zwracania końca nowego zakresu wolnego od określonej wartości.|
|[stępować](algorithm-functions.md#replace)|Sprawdza każdy element w zakresie i zastępuje go, jeśli odpowiada określonej wartości.|
|[replace_copy](algorithm-functions.md#replace_copy)|Sprawdza każdy element w zakresie źródłowym i zastępuje go, jeśli odpowiada określonej wartości, jednocześnie kopiując wynik do nowego zakresu docelowego.|
|[replace_copy_if](algorithm-functions.md#replace_copy_if)|Sprawdza każdy element w zakresie źródłowym i zastępuje go, jeśli spełnia określony predykat, jednocześnie kopiując wynik do nowego zakresu docelowego.|
|[replace_if](algorithm-functions.md#replace_if)|Sprawdza każdy element w zakresie i zastępuje go, jeśli spełnia określony predykat.|
|[cofnięci](algorithm-functions.md#reverse)|Odwraca kolejność elementów w obrębie zakresu.|
|[reverse_copy](algorithm-functions.md#reverse_copy)|Odwraca kolejność elementów w obrębie zakresu źródłowego, jednocześnie kopiując je do zakresu docelowego|
|[obróceni](algorithm-functions.md#rotate)|Wymienia elementy znajdujące się w dwóch sąsiednich zakresach.|
|[rotate_copy](algorithm-functions.md#rotate_copy)|Wymienia elementy w dwóch sąsiednich zakresach w ramach zakresu źródłowego i kopiuje wynik do zakresu docelowego.|
|[Northwind](algorithm-functions.md#sample)||
|[wyszukiwania](algorithm-functions.md#search)|Wyszukuje pierwsze wystąpienie sekwencji w zakresie docelowym, której elementy są równe tym w danej sekwencji elementów lub której elementy są równoważne w sensie określonym przez predykat binarny dla elementów w danej sekwencji.|
|[search_n](algorithm-functions.md#search_n)|Wyszukuje pierwszą podsekwencję w zakresie, w której określona liczba elementów ma określoną wartość lub relację do tej wartości określoną przez predykat binarny.|
|[set_difference](algorithm-functions.md#set_difference)|Łączy w sobie wszystkie elementy, które należą do jednego posortowanego zakresu źródłowego, ale nie do drugiego posortowanego zakresu źródłowego, w pojedynczy, posortowany zakres docelowy, gdzie kryterium sortowania może być określone przez predykat binarny.|
|[set_intersection](algorithm-functions.md#set_intersection)|Łączy w sobie wszystkie elementy, które należą do obu posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.|
|[set_symmetric_difference](algorithm-functions.md#set_symmetric_difference)|Łączy w sobie wszystkie elementy, które należą do jednego z, ale nie obu posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.|
|[set_union](algorithm-functions.md#set_union)|Łączy w sobie wszystkie elementy, które należą do przynajmniej jednego z dwóch posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.|
|[porządku](algorithm-functions.md#sort)|Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryteriów sortowania określonych przez binarny predykat.|
|[losowo](algorithm-functions.md#shuffle)|Powoduje losowe (rozmieszczanie) elementów dla danego zakresu przy użyciu generatora liczb losowych.|
|[sort_heap](algorithm-functions.md#sort_heap)|Konwertuje stertę na sortowany zakres.|
|[stable_partition](algorithm-functions.md#stable_partition)|Klasyfikuje elementy w zakresie na dwa rozłączne zestawy, z elementami spełniającymi predykat unarny poprzedzającymi te, które go nie spełniają, zachowując względną kolejność elementów równoważnych.|
|[stable_sort](algorithm-functions.md#stable_sort)|Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryterium sortowania określonego przez binarny predykat i zachowuje względną kolejność elementów równoważnych.|
|[wymiany](algorithm-functions.md#swap)|Wymienia wartości elementów między dwoma typami obiektów, przypisując zawartość pierwszego obiektu do drugiego obiektu, a zawartość drugiego do pierwszego.|
|[swap_ranges](algorithm-functions.md#swap_ranges)|Zamienia elementy jednego zakresu przez elementy innego zakresu, zakresy mają równe wielkości.|
|[przekształcania](algorithm-functions.md#transform)|Stosuje określony obiekt funkcji dla każdego elementu w zakresie sortowania lub dla pary elementów z dwóch zakresów sortowania i kopiuje zwracane wartości obiektu funkcji do zakresu docelowego.|
|[unique](algorithm-functions.md#unique)|Usuwa zduplikowane elementy, które sąsiadują ze sobą w określonym zakresie.|
|[unique_copy](algorithm-functions.md#unique_copy)|Kopiuje elementy z zakresu źródłowego do zakresu docelowego z wyjątkiem zduplikowanych elementów, które ze sobą sąsiadują.|
|[upper_bound](algorithm-functions.md#upper_bound)|Znajduje pozycję pierwszego elementu w uporządkowanym zakresie, który ma wartość większą niż określona wartość, gdzie kryterium sortowania może być określone przez predykat binarny.|

## <a name="see-also"></a>Zobacz też

[Dokumentacja plików nagłówkowych](cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki języka C++](cpp-standard-library-reference.md)
