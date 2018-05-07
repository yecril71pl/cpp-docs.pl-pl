---
title: Algorytm (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/algorithm>
dev_langs:
- C++
helpviewer_keywords:
- algorithm functions [STL/CLR]
- <algorithm> header [STL/CLR]
- <cliext/algorithm> header [STL/CLR]
ms.assetid: ee2718dc-a98d-40b8-8341-593fe7d2ac15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 30e347905c6802e544cb9f81c045f9cc881f29fb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="algorithm-stlclr"></a>algorithm (STL/CLR)
Definiuje funkcje szablonu kontenera STL/CLR, wykonujących algorytmów.  
  
## <a name="syntax"></a>Składnia  
  
```  
#include <cliext/algorithm>  
```  
  
## <a name="functions"></a>Funkcje  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[adjacent_find (STL/CLR)](../dotnet/adjacent-find-stl-clr.md)|Wyszukuje dwóch sąsiadujących ze sobą elementów, które są takie same.|  
|[binary_search (STL/CLR)](../dotnet/binary-search-stl-clr.md)|Sprawdza, czy sortowane sekwencja zawiera podanej wartości.|  
|[copy (STL/CLR)](../dotnet/copy-stl-clr.md)|Kopiuje wartości z zakresu źródła docelowy zakres iteracja w kierunku do przodu.|  
|[copy_backward (STL/CLR)](../dotnet/copy-backward-stl-clr.md)|Kopiuje wartości z zakresu źródła docelowy zakres iteracja w kierunku do tyłu.|  
|[count (STL/CLR)](../dotnet/count-stl-clr.md)|Zwraca liczbę elementów w zakresie, których wartości pasują do określonej wartości.|  
|[count_if (STL/CLR)](../dotnet/count-if-stl-clr.md)|Zwraca liczbę elementów w zakresie, których wartości pasują do określonego warunku.|  
|[equal (STL/CLR)](../dotnet/equal-stl-clr.md)|Porównuje dwa zakresy, elementów.|  
|[equal_range (STL/CLR)](../dotnet/equal-range-stl-clr.md)|Wyszukuje uporządkowana sekwencja wartości i zwraca dwie pozycje ograniczających podsekwencji wartości, które są równe do danego elementu.|  
|[fill (STL/CLR)](../dotnet/fill-stl-clr.md)|Przypisuje tę samą nową wartość każdemu elementowi w określonym zakresie.|  
|[fill_n (STL/CLR)](../dotnet/fill-n-stl-clr.md)|Przypisuje nową wartość do określonej liczby elementów na początku zakresu z określonym elementem.|  
|[find (STL/CLR)](../dotnet/find-stl-clr.md)|Zwraca pozycję pierwszego wystąpienia określonej wartości.|  
|[find_end (STL/CLR)](../dotnet/find-end-stl-clr.md)|Zwraca ostatni podsekwencji zakresu, który jest taka sama jak określona sekwencja.|  
|[find_first_of (STL/CLR)](../dotnet/find-first-of-stl-clr.md)|Wyszukuje zakresu dla pierwszego wystąpienia jednego z danego zakresu elementów.|  
|[find_if (STL/CLR)](../dotnet/find-if-stl-clr.md)|Zwraca pozycję pierwszego elementu w sekwencji wartości, jeśli element spełnia określony warunek.|  
|[for_each (STL/CLR)](../dotnet/for-each-stl-clr.md)|Stosuje obiektu o określonej funkcji do każdego elementu w sekwencji wartości i zwraca obiekt funkcji.|  
|[generate (STL/CLR)](../dotnet/generate-stl-clr.md)|Przypisuje wartości generowanych przez obiekt funkcji do każdego elementu w sekwencji wartości.|  
|[generate_n (STL/CLR)](../dotnet/generate-n-stl-clr.md)|Przypisuje wartości generowanych przez obiekt funkcji do określonej liczby elementów.|  
|[includes (STL/CLR)](../dotnet/includes-stl-clr.md)|Sprawdza, czy jeden zakres posortowane zawiera wszystkie elementy w drugiego zakresu posortowane.|  
|[inplace_merge (STL/CLR)](../dotnet/inplace-merge-stl-clr.md)|Łączy elementy z dwóch kolejnych zakresów posortowane w jednym zakresem posortowane.|  
|[iter_swap (STL/CLR)](../dotnet/iter-swap-stl-clr.md)|Wymienia dwie wartości, do których odnosi się para określonych iteratorów.|  
|[lexicographical_compare (STL/CLR)](../dotnet/lexicographical-compare-stl-clr.md)|Porównuje dwie sekwencje, elementów, identyfikowanie, które sekwencja jest mniejszy z dwóch.|  
|[lower_bound (STL/CLR)](../dotnet/lower-bound-stl-clr.md)|Odnajduje położenie pierwszego elementu w uporządkowanej kolejności wartości ma wartość większa niż lub równa określonej wartości.|  
|[make_heap (STL/CLR)](../dotnet/make-heap-stl-clr.md)|Konwertuje sterty, gdzie pierwszy element na stosie jest największy elementy z określonego zakresu.|  
|[max (STL/CLR)](../dotnet/max-stl-clr.md)|Porównuje dwa obiekty i zwraca większa niż dwa.|  
|[max_element (STL/CLR)](../dotnet/max-element-stl-clr.md)|Wyszukuje największy element w kolejności określonej wartości.|  
|[merge (STL/CLR)](../dotnet/merge-stl-clr.md)|Łączy wszystkie elementy z dwóch posortowane zakresów w zasięgu pojedynczego, posortowane docelowym.|  
|[min (STL/CLR)](../dotnet/min-stl-clr.md)|Porównuje dwa obiekty i zwraca mniejszy z dwóch.|  
|[min_element (STL/CLR)](../dotnet/min-element-stl-clr.md)|Wyszukuje najmniejszy element w kolejności określonej wartości.|  
|[mismatch (STL/CLR)](../dotnet/mismatch-stl-clr.md)|Porównuje dwa zakresy elementów i zwraca pierwszą pozycję, gdzie występuje różnica.|  
|[next_permutation (STL/CLR)](../dotnet/next-permutation-stl-clr.md)|Zmienia kolejność elementów w zakresie, dzięki czemu oryginalnego kolejność zostało zastąpione przez lexicographically dalej permutacji większa, jeśli istnieje.|  
|[nth_element (STL/CLR)](../dotnet/nth-element-stl-clr.md)|Partycje sekwencję elementów poprawnie lokalizowanie `n`element th sekwencji, aby wszystkie elementy przed nim mniejsza lub równa i wszystkie elementy, których przestrzeganie są większe niż lub równą jej.|  
|[partial_sort (STL/CLR)](../dotnet/partial-sort-stl-clr.md)|Rozmieszcza określoną liczbę mniejsze elementy w zakresie nondescending kolejności.|  
|[partial_sort_copy (STL/CLR)](../dotnet/partial-sort-copy-stl-clr.md)|Kopiuje elementy z zakresu źródła do zakresu docelowego taki sposób, że elementy z zakresu źródła są uporządkowane.|  
|[partition (STL/CLR)](../dotnet/partition-stl-clr.md)|Rozmieszcza elementy w zakresie w taki sposób, że te elementy, które spełniają predykat jednoargumentowy poprzedzać te, które nie spełniają jej.|  
|[pop_heap (STL/CLR)](../dotnet/pop-heap-stl-clr.md)|Przenosi największy element z przodu sterty na końcu i następnie tworzy nowy sterty od pozostałych elementów.|  
|[prev_permutation (STL/CLR)](../dotnet/prev-permutation-stl-clr.md)|Zmienia kolejność sekwencję elementów, dzięki czemu oryginalnego kolejność zostało zastąpione przez lexicographically poprzedniego permutacji większa, jeśli istnieje.|  
|[push_heap (STL/CLR)](../dotnet/push-heap-stl-clr.md)|Dodaje element znajdujący się na końcu zakresu do istniejącej sterty, która składa się z poprzednich elementów w zakresie.|  
|[random_shuffle (STL/CLR)](../dotnet/random-shuffle-stl-clr.md)|Rozmieszcza sekwencji `N` elementy w zakresie do jednego z `N`! możliwości ustalenia losowo wybrany.|  
|[remove (STL/CLR)](../dotnet/remove-stl-clr.md)|Usuwa określoną wartość z danego zakresu bez zakłócania kolejność pozostałych elementów i zwraca koniec nowy zakres wolne od określonej wartości.|  
|[remove_copy (STL/CLR)](../dotnet/remove-copy-stl-clr.md)|Kopiuje elementy z zakresu źródła do zakresu docelowego z tą różnicą, że nie są kopiowane elementy określoną wartość, bez zakłócania kolejność pozostałych elementów.|  
|[remove_copy_if (STL/CLR)](../dotnet/remove-copy-if-stl-clr.md)|Kopiuje elementy z zakresu źródła zakres docelowy, z wyjątkiem tych, które spełniają predykatu, bez zakłócania kolejność pozostałych elementów.|  
|[remove_if (STL/CLR)](../dotnet/remove-if-stl-clr.md)|Usuwa elementy, które spełniają predykat z danego zakresu bez zakłócania kolejność pozostałych elementów. .|  
|[replace (STL/CLR)](../dotnet/replace-stl-clr.md)|Zastępuje elementy w zakresie zgodne z określoną wartość z nową wartością.|  
|[replace_copy (STL/CLR)](../dotnet/replace-copy-stl-clr.md)|Kopiuje elementy z zakresu źródła zakresu docelowego, zastępując elementy, które pasują do określonej wartości z nową wartością.|  
|[replace_copy_if (STL/CLR)](../dotnet/replace-copy-if-stl-clr.md)|Sprawdza każdy element w zakresie źródłowym i zastępuje go, jeśli spełnia określony predykat, jednocześnie kopiując wynik do nowego zakresu docelowego.|  
|[replace_if (STL/CLR)](../dotnet/replace-if-stl-clr.md)|Sprawdza każdy element w zakresie i zastępuje go, jeśli spełnia określony predykat.|  
|[reverse (STL/CLR)](../dotnet/reverse-stl-clr.md)|Odwraca kolejność elementów w obrębie zakresu.|  
|[reverse_copy (STL/CLR)](../dotnet/reverse-copy-stl-clr.md)|Odwraca kolejność elementów w zakresie źródła podczas kopiowania ich do zakresu docelowego.|  
|[rotate (STL/CLR)](../dotnet/rotate-stl-clr.md)|Wymienia elementy znajdujące się w dwóch sąsiednich zakresach.|  
|[rotate_copy (STL/CLR)](../dotnet/rotate-copy-stl-clr.md)|Wymienia elementy w dwóch sąsiednich zakresach w ramach zakresu źródłowego i kopiuje wynik do zakresu docelowego.|  
|[search (STL/CLR)](../dotnet/search-stl-clr.md)|Wyszukuje pierwsze wystąpienie sekwencji w zakresie docelowym, której elementy są równe tym w danej sekwencji elementów lub której elementy są równoważne w sensie określonym przez predykat binarny dla elementów w danej sekwencji.|  
|[search_n (STL/CLR)](../dotnet/search-n-stl-clr.md)|Wyszukuje pierwszą podsekwencję w zakresie, w której określona liczba elementów ma określoną wartość lub relację do tej wartości określoną przez predykat binarny.|  
|[set_difference (STL/CLR)](../dotnet/set-difference-stl-clr.md)|Łączy w sobie wszystkie elementy, które należą do jednego posortowanego zakresu źródłowego, ale nie do drugiego posortowanego zakresu źródłowego, w pojedynczy, posortowany zakres docelowy, gdzie kryterium sortowania może być określone przez predykat binarny.|  
|[set_intersection (STL/CLR)](../dotnet/set-intersection-stl-clr.md)|Łączy w sobie wszystkie elementy, które należą do obu posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.|  
|[set_symmetric_difference (STL/CLR)](../dotnet/set-symmetric-difference-stl-clr.md)|Łączy w sobie wszystkie elementy, które należą do jednego z, ale nie obu posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.|  
|[set_union (STL/CLR)](../dotnet/set-union-stl-clr.md)|Łączy w sobie wszystkie elementy, które należą do przynajmniej jednego z dwóch posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.|  
|[sort (STL/CLR)](../dotnet/sort-stl-clr.md)|Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryteriów sortowania określonych przez binarny predykat.|  
|[sort_heap (STL/CLR)](../dotnet/sort-heap-stl-clr.md)|Konwertuje stertę na sortowany zakres.|  
|[stable_partition (STL/CLR)](../dotnet/stable-partition-stl-clr.md)|Klasyfikuje elementy w zakresie na dwa rozłączne zestawy, z elementami spełniającymi predykat unarny poprzedzającymi te, które go nie spełniają, zachowując względną kolejność elementów równoważnych.|  
|[stable_sort (STL/CLR)](../dotnet/stable-sort-stl-clr.md)|Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryterium sortowania określonego przez binarny predykat i zachowuje względną kolejność elementów równoważnych.|  
|[swap (STL/CLR)](../dotnet/swap-stl-clr.md)|Wymienia wartości elementów między dwoma typami obiektów, przypisując zawartość pierwszego obiektu do drugiego obiektu, a zawartość drugiego do pierwszego.|  
|[swap_ranges (STL/CLR)](../dotnet/swap-ranges-stl-clr.md)|Zamienia elementy jednego zakresu przez elementy innego zakresu, zakresy mają równe wielkości.|  
|[transform (STL/CLR)](../dotnet/transform-stl-clr.md)|Stosuje określony obiekt funkcji dla każdego elementu w zakresie sortowania lub dla pary elementów z dwóch zakresów sortowania i kopiuje zwracane wartości obiektu funkcji do zakresu docelowego.|  
|[unique (STL/CLR)](../dotnet/unique-stl-clr.md)|Usuwa zduplikowane elementy, które sąsiadują ze sobą w określonym zakresie.|  
|[unique_copy (STL/CLR)](../dotnet/unique-copy-stl-clr.md)|Kopiuje elementy z zakresu źródłowego do zakresu docelowego z wyjątkiem zduplikowanych elementów, które ze sobą sąsiadują.|  
|[upper_bound (STL/CLR)](../dotnet/upper-bound-stl-clr.md)|Znajduje pozycję pierwszego elementu w uporządkowanym zakresie, który ma wartość większą niż określona wartość, gdzie kryterium sortowania może być określone przez predykat binarny.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/algorytm >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja biblioteki STL/CLR](../dotnet/stl-clr-library-reference.md)