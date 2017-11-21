---
title: '&lt;Algorytm&gt; | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <algorithm>
dev_langs: C++
helpviewer_keywords:
- algorithm header [C++]
- C++ Standard Library, algorithms
- <algorithm> header
ms.assetid: 19f97711-7a67-4a65-8fd1-9a2bd3ca327d
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 65cb348e19031965d70175d73ed8df94692f9db6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltalgorithmgt"></a>&lt;Algorytm&gt;
Definiuje standardowa biblioteka C++ kontenera szablonu funkcji, wykonujących algorytmów.  
  
## <a name="syntax"></a>Składnia  
  
```
(see relevant links below for specific algorithm syntax)
```  
  
## <a name="remarks"></a>Uwagi  
 Algorytmy standardowa biblioteka C++ są ogólne, ponieważ mogą one działać na różnych struktury danych. Struktury danych, które działają na obejmują nie tylko klasy kontenerów standardowa biblioteka języka C++, takie jak `vector` i `list`, ale również struktur danych programu i tablice elementów, które spełniają wymagania danego algorytm. Algorytmy standardowa biblioteka C++ osiągnąć ten poziom odpisy za dostęp i przechodzących przez elementy kontenera pośrednio za pośrednictwem Iteratory.  
  
 Algorytmy standardowa biblioteka C++ przetworzyć iteratora zakresy, które zwykle są określane przez ich początkowego lub końcowego pozycji. Odnośne zakresy muszą być prawidłowe w tym sensie, że wszystkie wskaźniki w zakresach muszą być wyłuskiwalne, a w ramach sekwencji każdego zakresu, ostatnia pozycja musi być osiągalna od pierwszej przez inkrementację.  
  
 Algorytmy standardowa biblioteka C++ rozszerzyć akcji obsługiwanych przez operacje i funkcje Członkowskie każdego kontenera standardowa biblioteka C++ i umożliwić pracy, na przykład różne typy obiektów kontenera, w tym samym czasie. Do przekazywania informacji o przeznaczeniu algorytmów były używane dwa przyrostki.  
  
-   `_if` Sufiks wskazuje, że algorytm jest używane z obiektami funkcja operacyjnego wartości elementów, a nie wartości ze sobą elementy. `find_if` Algorytm wyszukuje elementy, których wartości spełniają kryteria określone przez obiekt funkcji i `find` algorytmu wyszukiwania dla określonej wartości.  
  
-   Przyrostek _copy oznacza, że algorytm nie tylko manipuluje wartościami elementów, ale również kopiuje zmodyfikowane wartości do zakresu docelowego. `reverse` Algorytm Odwraca kolejność elementów w zakresie, a `reverse_copy` algorytm kopiuje wynik do zakresu docelowego.  
  
 Algorytmy standardowa biblioteka C++ często są klasyfikowane w grupach, które wskazują coś o ich przeznaczenia lub wymagań. Obejmują one modyfikowanie algorytmów zmienić wartości elementów w porównaniu z systemem innym niż modyfikowanie algorytmy, które nie. Algorytmy mutujące zmieniają kolejność elementów, ale nie ich wartości. Algorytmy usuwające mogą wyeliminować elementy z zakresu lub kopii zakresu. Algorytmy sortujące zmieniają kolejność elementów w zakresie na różne sposoby, a algorytmy sortowanego zakresu działają jedynie na algorytmach, których elementy zostały posortowane w określony sposób.  
  
 Standardowa biblioteka C++ algorytmy liczbowych, używane do przetwarzania numeryczny mają własne pliku nagłówka [ \<liczbowych >](../standard-library/numeric.md), a obiekty funkcji i adapterów są definiowane w nagłówku [ \<funkcjonalności >](../standard-library/functional.md) obiekty funkcji, które zwracają wartości logiczne są określane jako predykatów. Predykat binarne domyślny jest porównanie `operator<`. Ogólnie rzecz biorąc, szeregowane elementy muszą być mniej niż porównywalne, tak aby, mając dowolne dwa elementy, można było określić, czy są one równoważne (w sensie, żaden nie jest mniejszy niż ten drugi), czy że jeden jest mniejszy od drugiego. Skutkuje to ustaleniem kolejności elementów nierównoważnych.  
  
### <a name="functions"></a>Funkcje  
  
|||  
|-|-|  
|[adjacent_find —](../standard-library/algorithm-functions.md#adjacent_find)|Wyszukuje dwa sąsiadujące elementy, które są równe lub spełniają określony warunek.|  
|[all_of](../standard-library/algorithm-functions.md#all_of)|Zwraca `true` po warunek musi być obecny przy każdym elemencie podanego zakresu.|  
|[any_of](../standard-library/algorithm-functions.md#any_of)|Zwraca `true` gdy warunek ma co najmniej raz w określonym zakresie elementów.|  
|[binary_search —](../standard-library/algorithm-functions.md#binary_search)|Testuje, czy w sortowanym zakresie istnieje element, który jest równy określonej wartości lub który jest odpowiednikiem w sensie określonym przez predykat binarny.|  
|[Kopiuj](../standard-library/algorithm-functions.md#copy)|Przypisuje wartości elementów z zakresu źródłowego do zakresu docelowego, iterując przez sekwencję źródłową elementów oraz przypisując im nowe pozycje w kierunku do przodu.|  
|[copy_backward —](../standard-library/algorithm-functions.md#copy_backward)|Przypisuje wartości elementów z zakresu źródłowego do zakresu docelowego, iterując przez sekwencję źródłową elementów oraz przypisując im nowe pozycje w kierunku do tyłu.|  
|[copy_if](../standard-library/algorithm-functions.md#copy_if)|Skopiuj wszystkie elementy w danym zakresie, że testowy `true` dla określonego warunku|  
|[copy_n](../standard-library/algorithm-functions.md#copy_n)|Kopiuje określoną liczbę elementów.|  
|[Liczba](../standard-library/algorithm-functions.md#count)|Zwraca liczbę elementów w zakresie, których wartości pasują do określonej wartości.|  
|[count_if](../standard-library/algorithm-functions.md#count_if)|Zwraca liczbę elementów w zakresie, których wartości pasują do określonego warunku.|  
|[takie same](../standard-library/algorithm-functions.md#equal)|Porównuje dwa zakresy element po elemencie, pod względem równości lub równoważności w sensie określonym przez predykat binarny.|  
|[equal_range](../standard-library/algorithm-functions.md#equal_range)|Wyszukuje parę pozycji w uporządkowanym zakresie, pierwszą mniejszą lub równoważną położeniu określonego elementu, a drugą większą niż pozycja elementu, gdzie sens równoważności lub szeregowania używany do ustanawiania pozycji w sekwencji może zostać określony przez predykat binarny.|  
|[wypełnienia](../standard-library/algorithm-functions.md#fill)|Przypisuje tę samą nową wartość każdemu elementowi w określonym zakresie.|  
|[fill_n](../standard-library/algorithm-functions.md#fill_n)|Przypisuje nową wartość określonej liczbie elementów z zakresu, począwszy od konkretnego elementu.|  
|[Znajdź](../standard-library/algorithm-functions.md#find)|Lokalizuje pozycję pierwszego wystąpienia elementu w zakresie, który ma określoną wartość.|  
|[find_end —](../standard-library/algorithm-functions.md#find_end)|Wyszukuje w zakresie ostatnią podsekwencję, która jest identyczna z określoną sekwencją lub jest równoważna w sensie określonym przez predykat binarny.|  
|[find_first_of —](../standard-library/algorithm-functions.md#find_first_of)|Wyszukuje pierwsze wystąpienie którejś z kilku wartości w zakresie docelowym lub pierwsze wystąpienie któregoś z kilku elementów, które są równoważne w sensie określonym przez predykat binarny dla określonego zestawu elementów.|  
|[find_if](../standard-library/algorithm-functions.md#find_if)|Lokalizuje pozycję pierwszego wystąpienia elementu w zakresie, który spełnia określony warunek.|  
|[find_if_not —](../standard-library/algorithm-functions.md#find_if_not)|Zwraca pierwszy element we wskazanym zakresie, który nie spełnia warunku.|  
|[for_each](../standard-library/algorithm-functions.md#for_each)|Stosuje określony obiekt funkcji do każdego elementu w kolejności do przodu w zakresie i zwraca obiekt funkcji.|  
|[Generowanie](../standard-library/algorithm-functions.md#generate)|Przypisuje wartości generowane przez obiekt funkcji do każdego elementu w zakresie.|  
|[generate_n](../standard-library/algorithm-functions.md#generate_n)|Przypisuje wartości generowane przez obiekt funkcji określonej liczbie elementów w zakresie i wraca do jednej pozycji poza ostatnią przypisaną wartością.|  
|[zawiera](../standard-library/algorithm-functions.md#includes)|Sprawdza, czy jeden posortowany zakres zawiera wszystkie elementy zawarte w drugim posortowanym zakresie, gdzie kryterium szeregowania lub równoważności między elementami może zostać określone przez predykat binarny.|  
|[inplace_merge —](../standard-library/algorithm-functions.md#inplace_merge)|Łączy elementy z dwóch następujących po sobie posortowanych zakresów w pojedynczy posortowany zakres, gdzie kryterium szeregowania może być określone przez predykat binarny.|  
|[is_heap](../standard-library/algorithm-functions.md#is_heap)|Zwraca `true` Jeśli sterty tworzą elementów w określonym zakresie.|  
|[is_heap_until —](../standard-library/algorithm-functions.md#is_heap_until)|Zwraca `true` , jeśli określony zakres formularzy sterty do ostatniego elementu.|  
|[is_partitioned](../standard-library/algorithm-functions.md#is_partitioned)|Zwraca `true` wszystkie elementy w danym zakresie który należy przetestować `true` dla warunku występować przed elementów, które test `false`.|  
|[is_permutation](../standard-library/algorithm-functions.md#is_permutation)|Określa, czy elementy w danym zakresie tworzą prawidłowy permutacji.|  
|[is_sorted](../standard-library/algorithm-functions.md#is_sorted)|Zwraca `true` Jeśli elementów w określonym zakresie są posortowane.|  
|[is_sorted_until —](../standard-library/algorithm-functions.md#is_sorted_until)|Zwraca `true` Jeśli elementów w określonym zakresie są posortowane.|  
|[iter_swap —](../standard-library/algorithm-functions.md#iter_swap)|Wymienia dwie wartości, do których odnosi się para określonych iteratorów.|  
|[lexicographical_compare —](../standard-library/algorithm-functions.md#lexicographical_compare)|Porównuje dwie sekwencje element po elemencie, aby określić, która z nich jest mniejsza.|  
|[lower_bound —](../standard-library/algorithm-functions.md#lower_bound)|Znajduje pozycję pierwszego elementu w uporządkowanym zakresie, który ma wartość większą niż lub równoważną określonej wartości, gdzie kryterium szeregowania może być określone przez predykat binarny.|  
|[make_heap —](../standard-library/algorithm-functions.md#make_heap)|Konwertuje elementy z określonego zakresu na stertę, w której pierwszy element jest największy i dla której kryterium sortowania może być określone przez predykat binarny.|  
|[Maksymalna](../standard-library/algorithm-functions.md#max)|Porównuje dwa obiekty i zwraca większy z nich, gdzie kryterium sortowania może być określone przez predykat binarny.|  
|[max_element —](../standard-library/algorithm-functions.md#max_element)|Znajduje pierwsze wystąpienie największego elementu w określonym zakresie, gdzie kryterium sortowania może być określone przez predykat binarny.|  
|[scalania](../standard-library/algorithm-functions.md#merge)|Łączy wszystkie elementy z dwóch następujących po sobie posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.|  
|[min](../standard-library/algorithm-functions.md#min)|Porównuje dwa obiekty i zwraca mniejszy z nich, gdzie kryterium sortowania może być określone przez predykat binarny.|  
|[min_element —](../standard-library/algorithm-functions.md#min_element)|Znajduje pierwsze wystąpienie najmniejszego elementu w określonym zakresie, gdzie kryterium sortowania może być określone przez predykat binarny.|  
|[minmax](../standard-library/algorithm-functions.md#minmax)|Porównuje dwa parametry wejściowe i zwraca je jako parę w kolejności od najmniejszego do największego.|  
|[minmax_element](../standard-library/algorithm-functions.md#minmax_element)|Wykonuje pracę z zastosowaniem [min_element](../standard-library/algorithm-functions.md#min_element) i [max_element](../standard-library/algorithm-functions.md#max_element) w jednym wywołaniu.|  
|[Niezgodność](../standard-library/algorithm-functions.md#mismatch)|Porównuje dwa zakresy element po elemencie pod względem równości lub odpowiedniości w sensie określonym przez predykat binarny i lokalizuje pierwsze miejsce, w którym występuje różnica.|  
|[&lt;alg&gt; Przenieś](../standard-library/algorithm-functions.md#alg_move)|Przenieś elementy związane z określonym zakresem.|  
|[move_backward](../standard-library/algorithm-functions.md#move_backward)|Przenosi elementy jednego iteratora do drugiego. Przeniesienie rozpoczyna się od ostatniego elementu w określonym zakresie, a kończy się na pierwszym elemencie w tym zakresie.|  
|[next_permutation —](../standard-library/algorithm-functions.md#next_permutation)|Zmienia kolejność elementów w zakresie, tak że oryginalna kolejność jest zastąpiona przez leksykograficznie kolejną większą permutację, o ile takowa istnieje, gdzie sens „kolejna” może być określony przez predykat binarny.|  
|[none_of](../standard-library/algorithm-functions.md#none_of)|Zwraca `true` po warunek nigdy nie znajduje się między elementami w danym zakresie.|  
|[nth_element —](../standard-library/algorithm-functions.md#nth_element)|Partycje zakresu elementów poprawnie lokalizowanie  *n* są tak, aby wszystkie elementy przed nim są mniejsze niż lub równe go i wszystkie elementy, które po nim w sekwencji, element th sekwencji w zakresie większa niż lub równą jej.|  
|[partial_sort —](../standard-library/algorithm-functions.md#partial_sort)|Rozmieszcza określoną liczbę mniejszych elementów w zakresie w niemalejącej kolejności, lub według kryteriów sortowania określonych przez binarny predykat.|  
|[partial_sort_copy —](../standard-library/algorithm-functions.md#partial_sort_copy)|Kopiuje elementy z zakresu źródłowego do zakresu docelowego, gdzie elementy źródłowe są uporządkowane według albo zasady mniejszy niż, albo innego określonego predykatu binarnego.|  
|[partycji](../standard-library/algorithm-functions.md#partition)|Klasyfikuje elementy w zakresie na dwa rozłączne zestawy, z elementami spełniającymi predykat unarny poprzedzającymi te, które go nie spełniają.|  
|[partition_copy —](../standard-library/algorithm-functions.md#partition_copy)|Kopiuje elementy, dla których jest warunek `true` do jednego miejsca docelowego i dla których jest warunek `false` na inny. Elementy muszą pochodzić z określonego zakresu.|  
|[partition_point](../standard-library/algorithm-functions.md#partition_point)|Zwraca pierwszy element w danym zakresie, który nie spełnia warunku. Elementy są sortowane, aby te, które spełniają warunek, występowały przed tymi, które go nie spełniają.|  
|[pop_heap —](../standard-library/algorithm-functions.md#pop_heap)|Usuwa największy element z przodu sterty do przedostatniej pozycji w zakresie, a następnie tworzy nową stertę z pozostałych elementów.|  
|[prev_permutation](../standard-library/algorithm-functions.md#prev_permutation)|Zmienia kolejność elementów w zakresie, tak że oryginalna kolejność jest zastąpiona przez leksykograficznie kolejną większą permutację, o ile takowa istnieje, gdzie sens „kolejna” może być określony przez predykat binarny.|  
|[push_heap —](../standard-library/algorithm-functions.md#push_heap)|Dodaje element znajdujący się na końcu zakresu do istniejącej sterty, która składa się z poprzednich elementów w zakresie.|  
|[random_shuffle —](../standard-library/algorithm-functions.md#random_shuffle)|Rozmieszcza sekwencji *N* elementy w zakresie do jednego z *N*! możliwości ustalenia losowo wybrany.|  
|[Usuń](../standard-library/algorithm-functions.md#remove)|Eliminuje określoną wartość z danego zakresu bez zakłócania kolejności pozostałych elementów i zwracania końca nowego zakresu wolnego od określonej wartości.|  
|[remove_copy](../standard-library/algorithm-functions.md#remove_copy)|Kopiuje elementy z zakresu źródłowego do zakresu docelowego, z tym wyjątkiem, że elementy o określonej wartości nie są kopiowane, bez naruszania kolejności pozostałych elementów i zwracania końca nowego zakresu docelowego.|  
|[remove_copy_if](../standard-library/algorithm-functions.md#remove_copy_if)|Kopiuje elementy z zakresu źródłowego do zakresu docelowego, z tym wyjątkiem, że elementy spełniające predykat nie są kopiowane, bez naruszania kolejności pozostałych elementów i zwracania końca nowego zakresu docelowego.|  
|[remove_if](../standard-library/algorithm-functions.md#remove_if)|Eliminuje elementy, które spełniają predykat, z danego zakresu bez zakłócania kolejności pozostałych elementów i zwracania końca nowego zakresu wolnego od określonej wartości.|  
|[Zamień](../standard-library/algorithm-functions.md#replace)|Sprawdza każdy element w zakresie i zastępuje go, jeśli odpowiada określonej wartości.|  
|[replace_copy](../standard-library/algorithm-functions.md#replace_copy)|Sprawdza każdy element w zakresie źródłowym i zastępuje go, jeśli odpowiada określonej wartości, jednocześnie kopiując wynik do nowego zakresu docelowego.|  
|[replace_copy_if](../standard-library/algorithm-functions.md#replace_copy_if)|Sprawdza każdy element w zakresie źródłowym i zastępuje go, jeśli spełnia określony predykat, jednocześnie kopiując wynik do nowego zakresu docelowego.|  
|[replace_if](../standard-library/algorithm-functions.md#replace_if)|Sprawdza każdy element w zakresie i zastępuje go, jeśli spełnia określony predykat.|  
|[wstecznego](../standard-library/algorithm-functions.md#reverse)|Odwraca kolejność elementów w obrębie zakresu.|  
|[reverse_copy](../standard-library/algorithm-functions.md#reverse_copy)|Odwraca kolejność elementów w obrębie zakresu źródłowego, jednocześnie kopiując je do zakresu docelowego|  
|[Obróć](../standard-library/algorithm-functions.md#rotate)|Wymienia elementy znajdujące się w dwóch sąsiednich zakresach.|  
|[rotate_copy](../standard-library/algorithm-functions.md#rotate_copy)|Wymienia elementy w dwóch sąsiednich zakresach w ramach zakresu źródłowego i kopiuje wynik do zakresu docelowego.|  
|[Wyszukiwanie](../standard-library/algorithm-functions.md#search)|Wyszukuje pierwsze wystąpienie sekwencji w zakresie docelowym, której elementy są równe tym w danej sekwencji elementów lub której elementy są równoważne w sensie określonym przez predykat binarny dla elementów w danej sekwencji.|  
|[search_n —](../standard-library/algorithm-functions.md#search_n)|Wyszukuje pierwszą podsekwencję w zakresie, w której określona liczba elementów ma określoną wartość lub relację do tej wartości określoną przez predykat binarny.|  
|[set_difference —](../standard-library/algorithm-functions.md#set_difference)|Łączy w sobie wszystkie elementy, które należą do jednego posortowanego zakresu źródłowego, ale nie do drugiego posortowanego zakresu źródłowego, w pojedynczy, posortowany zakres docelowy, gdzie kryterium sortowania może być określone przez predykat binarny.|  
|[set_intersection —](../standard-library/algorithm-functions.md#set_intersection)|Łączy w sobie wszystkie elementy, które należą do obu posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.|  
|[set_symmetric_difference —](../standard-library/algorithm-functions.md#set_symmetric_difference)|Łączy w sobie wszystkie elementy, które należą do jednego z, ale nie obu posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.|  
|[set_union —](../standard-library/algorithm-functions.md#set_union)|Łączy w sobie wszystkie elementy, które należą do przynajmniej jednego z dwóch posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.|  
|[Sortowanie](../standard-library/algorithm-functions.md#sort)|Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryteriów sortowania określonych przez binarny predykat.|  
|[losowo](../standard-library/algorithm-functions.md#shuffle)|Elementy przesuwa (Reorganizuje) dla określonego zakresu przy użyciu generator liczb losowych.|  
|[sort_heap —](../standard-library/algorithm-functions.md#sort_heap)|Konwertuje stertę na sortowany zakres.|  
|[stable_partition —](../standard-library/algorithm-functions.md#stable_partition)|Klasyfikuje elementy w zakresie na dwa rozłączne zestawy, z elementami spełniającymi predykat unarny poprzedzającymi te, które go nie spełniają, zachowując względną kolejność elementów równoważnych.|  
|[stable_sort —](../standard-library/algorithm-functions.md#stable_sort)|Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryterium sortowania określonego przez binarny predykat i zachowuje względną kolejność elementów równoważnych.|  
|[swap](../standard-library/algorithm-functions.md#swap)|Wymienia wartości elementów między dwoma typami obiektów, przypisując zawartość pierwszego obiektu do drugiego obiektu, a zawartość drugiego do pierwszego.|  
|[swap_ranges —](../standard-library/algorithm-functions.md#swap_ranges)|Zamienia elementy jednego zakresu przez elementy innego zakresu, zakresy mają równe wielkości.|  
|[przekształcenia](../standard-library/algorithm-functions.md#transform)|Stosuje określony obiekt funkcji dla każdego elementu w zakresie sortowania lub dla pary elementów z dwóch zakresów sortowania i kopiuje zwracane wartości obiektu funkcji do zakresu docelowego.|  
|[unikatowe](../standard-library/algorithm-functions.md#unique)|Usuwa zduplikowane elementy, które sąsiadują ze sobą w określonym zakresie.|  
|[unique_copy —](../standard-library/algorithm-functions.md#unique_copy)|Kopiuje elementy z zakresu źródłowego do zakresu docelowego z wyjątkiem zduplikowanych elementów, które ze sobą sąsiadują.|  
|[upper_bound](../standard-library/algorithm-functions.md#upper_bound)|Znajduje pozycję pierwszego elementu w uporządkowanym zakresie, który ma wartość większą niż określona wartość, gdzie kryterium sortowania może być określone przez predykat binarny.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Odwołanie do biblioteki C++ Standard](../standard-library/cpp-standard-library-reference.md)



