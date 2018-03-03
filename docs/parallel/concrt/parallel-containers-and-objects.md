---
title: "Równoległe kontenery i obiekty | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9159b9c8170ee73afd8bee5305506a842368a231
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="parallel-containers-and-objects"></a>Równoległe kontenery oraz obiekty
Biblioteka równoległych wzorców (PLL) obejmuje kilka kontenerów i obiektów, które dostarczają wątkowo dostęp do swoich elementów.  
  
 A *równoczesnych kontenera* zapewnia współbieżność bezpieczny dostęp do najważniejszych operacji. Funkcje te kontenery podobny do tych, które są udostępniane przez standardowa biblioteka C++. Na przykład [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) podobny klasy [std::vector](../../standard-library/vector-class.md) klasy, z wyjątkiem `concurrent_vector` klasa umożliwia dołączanie elementów jednocześnie. Kontenery współbieżne należy użyć w przypadku równoległego kodu, który uprawnienia zarówno do odczytu i zapisu do tego samego kontenera.  
  
 A *równoczesnych obiektu* współużytkowany jednocześnie składników. Proces, który oblicza stan równoczesnych obiektu równolegle tworzy takiego samego wyniku jako innego procesu, który oblicza takim samym stanie pojedynczo. [Concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) klasy jest przykładem typu obiektu współbieżnych. `combinable` Klasa umożliwia wykonać obliczenia równolegle, a następnie połączenie tych obliczeń do końcowego wyniku. Użycie równoczesnych obiektów, gdy mechanizm synchronizacji, na przykład obiektu mutex, w przeciwnym razie użyje synchronizujący dostęp do współdzielonej zmiennej lub zasobu.  
  
##  <a name="top"></a>Sekcje  
 W tym temacie opisano następujące równoległe kontenery oraz obiekty szczegółowo.  
  
 Kontenery współbieżne:  
  
-   [concurrent_vector, klasa](#ctor)  
  
    -   [Różnice między concurrent_vector — i wektora](#ctor)  
  
    -   [Operacje bezpieczne współbieżności](#ctor)  
  
    -   [Wyjątek bezpieczeństwa](#ctor)  
  
-   [concurrent_queue, klasa](#queue)  
  
    -   [Różnice między concurrent_queue — i kolejki](#queue-differences)  
  
    -   [Operacje bezpieczne współbieżności](#queue-safety)  
  
    -   [Obsługa iteratora](#queue-iterators)  
  
-   [concurrent_unordered_map, klasa](#unordered_map)  
  
    -   [Różnice między concurrent_unordered_map — i unordered_map](#map-differences)  
  
    -   [Operacje bezpieczne współbieżności](#map-safety)  
  
-   [concurrent_unordered_multimap, klasa](#unordered_multimap)  
  
-   [concurrent_unordered_set, klasa](#unordered_set)  
  
-   [concurrent_unordered_multiset, klasa](#unordered_multiset)  
  
 Obiekty współbieżnych:  
  
-   [combinable, klasa](#combinable)  
  
    -   [Metody i funkcje](#combinable-features)  
  
    -   [Przykłady](#combinable-examples)  
  
##  <a name="vector"></a>concurrent_vector — klasa  
 [Concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) klasa jest klasą kontenerem sekwencji, że, podobnie jak [std::vector](../../standard-library/vector-class.md) klasy, umożliwia losowo dostęp do jego elementów. `concurrent_vector` Klasa umożliwia bezpieczne współbieżności Dołącz i elementu dostęp. Dołącz operacje nie unieważniają istniejące wskaźniki lub Iteratory. Operacje dostępu i przechodzenie iteratora są również bezpieczne współbieżności.  
  
###  <a name="vector-differences"></a>Różnice między concurrent_vector — i wektora  
 `concurrent_vector` Klasy przypomina `vector` klasy. Złożoność append, dostępu do elementu i operacje związane z dostępem iteratora na `concurrent_vector` obiektu są takie same, jak w przypadku `vector` obiektu. Następujące punkty ilustrują where `concurrent_vector` różni się od `vector`:  
  
-   Dołącz dostępu elementu iteratora dostępu, operacje i iteratora przechodzenie na `concurrent_vector` obiektu są bezpieczne współbieżności.  
  
-   Elementy można dodać tylko do końca `concurrent_vector` obiektu. `concurrent_vector` Klasa nie zapewnia `insert` metody.  
  
-   A `concurrent_vector` obiektu nie używa [Przenieś semantyki](../../cpp/rvalue-reference-declarator-amp-amp.md) po dołączeniu do niego.  
  

-   `concurrent_vector` Klasa nie zapewnia `erase` lub `pop_back` metody. Jak `vector`, użyj [wyczyść](reference/concurrent-vector-class.md#clear) metodę, aby usunąć wszystkie elementy z `concurrent_vector` obiektu.  
  
-   `concurrent_vector` Klasa nie przechowuje jej elementy połączone ze sobą w pamięci. W związku z tym nie można użyć `concurrent_vector` klasy z metod, których można używać tablicy. Na przykład dla zmiennej o nazwie `v` typu `concurrent_vector`, wyrażenie `&v[0]+2` tworzy niezdefiniowane zachowanie.  
  
-   `concurrent_vector` Klasa definiuje [grow_by](reference/concurrent-vector-class.md#grow_by) i [grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least) metody. Te metody przypominać [zmiany rozmiaru](reference/concurrent-vector-class.md#resize) metody, z tą różnicą, że są one bezpieczne współbieżności.  
  
-   A `concurrent_vector` obiektu nie przemieszczenie jej elementy podczas dołączania do niego lub jej rozmiar. Dzięki temu istniejących wskaźników i Iteratory pozostaje ważne podczas operacji współbieżnych.  
  
-   Środowisko uruchomieniowe nie definiuje specjalna wersja `concurrent_vector` dla typu `bool`.  
  
###  <a name="vector-safety"></a>Operacje bezpieczne współbieżności  
 Wszystkie metody, które dołącza do lub zwiększyć rozmiar `concurrent_vector` obiektu lub uzyskiwanie dostępu do elementu w `concurrent_vector` obiektów, są bezpieczne współbieżności. Wyjątkiem od tej reguły jest `resize` metody.  
  
 W poniższej tabeli przedstawiono typowe `concurrent_vector` metody i operatory, które są bezpieczne współbieżności.  
  
||||  
|-|-|-|  

|[w](reference/concurrent-vector-class.md#at)|[zakończenia](reference/concurrent-vector-class.md#end)|[operatora &#91; &#93;](reference/concurrent-vector-class.md#operator_at)|  
|[Rozpocznij](reference/concurrent-vector-class.md#begin)|[przodu](reference/concurrent-vector-class.md#front)|[push_back](reference/concurrent-vector-class.md#push_back)|  
|[ponownie](reference/concurrent-vector-class.md#back)|[grow_by](reference/concurrent-vector-class.md#grow_by)|[rbegin](reference/concurrent-vector-class.md#rbegin)|  
|[pojemność](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)|[rend](reference/concurrent-vector-class.md#rend)|  
|[pusty](reference/concurrent-vector-class.md#empty)|[max_size](reference/concurrent-vector-class.md#max_size)|[rozmiaru](reference/concurrent-vector-class.md#size)|  

  
 Operacje, które środowiska uruchomieniowego zapewnia zgodność z standardowa biblioteka C++, na przykład `reserve`, nie są bezpieczne współbieżności. W poniższej tabeli przedstawiono typowe metody i operatory, które nie są bezpieczne współbieżności.  
  
|||  
|-|-|  

|[Przypisz](reference/concurrent-vector-class.md#assign)|[rezerwowa](reference/concurrent-vector-class.md#reserve)|  
|[Wyczyść](reference/concurrent-vector-class.md#clear)|[zmiana rozmiaru](reference/concurrent-vector-class.md#resize)|  
|[operator =](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit](reference/concurrent-vector-class.md#shrink_to_fit)|  
  
 Operacje, które modyfikują wartość istniejące elementy nie są bezpieczne współbieżności. Użyj obiektu synchronizacji, takie jak [reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) obiekt, aby zsynchronizować równoczesnych odczytu i zapisu do tego samego elementu danych. Aby uzyskać więcej informacji o obiektach synchronizacji, zobacz [struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md).  
  
 Podczas konwertowania istniejący kod, który używa `vector` do używania `concurrent_vector`, jednoczesnych operacji może spowodować, że działanie aplikacji w taki sposób, aby zmienić. Rozważmy na przykład następujący program jednocześnie wykonujące dwa zadania na `concurrent_vector` obiektu. Pierwszym zadaniem dołącza dodatkowe elementy do `concurrent_vector` obiektu. Drugie zadanie oblicza sumę wszystkich elementów w tym samym obiekcie.  
  
 [!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]  
  

 Mimo że `end` metoda jest współbieżności palety współbieżnych wywołań do [push_back](reference/concurrent-vector-class.md#push_back) metoda powoduje, że wartość, która jest zwracana w wyniku `end` można zmienić. Liczba elementów, które przechodzi przez iterator jest nieokreślony. W związku z tym ten program można utworzyć różne wyniki za każdym razem, uruchom go.  
  
###  <a name="vector-exceptions"></a>Wyjątek bezpieczeństwa  
 Jeśli operacja wzrostu lub przypisania zgłasza wyjątek, stan `concurrent_vector` obiekt staje się nieprawidłowy. Zachowanie `concurrent_vector` obiekt, który jest w nieprawidłowym stanie jest niezdefiniowany, chyba że określono inaczej. Jednak destruktor zawsze powoduje zwolnienie pamięci przydzielanej obiektu, nawet jeśli obiekt jest w nieprawidłowym stanie.  
  
 Typ danych elementów wektora `T`, musi spełniać następujące wymagania. W przeciwnym razie zachowanie `concurrent_vector` klasy jest niezdefiniowana.  
  
-   Destruktor nie może zostać zwrócone.  
  
-   Jeśli Konstruktor domyślny lub kopiowania zgłasza wyjątek, destruktor nie może być deklarowana przy użyciu `virtual` — słowo kluczowe i musi działać poprawnie przy pamięci zainicjowane przez zero.  
  
 [[Górnej](#top)]  
  
##  <a name="queue"></a>concurrent_queue — klasa  
 [Concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) klasy, tak jak [std::queue](../../standard-library/queue-class.md) klasy, umożliwia dostęp do przodu jego i kopii elementów. `concurrent_queue` Klasa umożliwia bezpieczne współbieżności umieścić w kolejce i usuwania z kolejki operacji. `concurrent_queue` Klasa udostępnia także obsługa iteratora, który nie jest bezpieczne współbieżności.  
  
###  <a name="queue-differences"></a>Różnice między concurrent_queue — i kolejki  
 `concurrent_queue` Klasy przypomina `queue` klasy. Następujące punkty ilustrują where `concurrent_queue` różni się od `queue`:  
  
-   Umieścić w kolejce i usuwania z kolejki operacji na `concurrent_queue` obiektu są bezpieczne współbieżności.  
  
-   `concurrent_queue` Klasy zapewnia obsługę iteratora, który nie jest bezpieczne współbieżności.  
  

-   `concurrent_queue` Klasa nie zapewnia `front` lub `pop` metody. `concurrent_queue` Klasy zastępuje tych metod, definiując [try_pop](reference/concurrent-queue-class.md#try_pop) metody.  
  
-   `concurrent_queue` Klasa nie zapewnia `back` metody. W związku z tym nie może przywoływać koniec kolejki.  
  
-   `concurrent_queue` Klasa udostępnia [unsafe_size](reference/concurrent-queue-class.md#unsafe_size) zamiast metody `size` metody. `unsafe_size` Metoda nie jest bezpieczne współbieżności.  

  
###  <a name="queue-safety"></a>Operacje bezpieczne współbieżności  
 Wszystkie metody tego umieścić w kolejce do lub usuwania z kolejki z `concurrent_queue` obiektu są bezpieczne współbieżności.  
  
 W poniższej tabeli przedstawiono typowe `concurrent_queue` metody i operatory, które są bezpieczne współbieżności.  
  
|||  
|-|-|  
|[pusty](reference/concurrent-queue-class.md#empty)|[push](reference/concurrent-queue-class.md#push)|  
|[get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|  


  
 Mimo że `empty` metoda jest bezpieczne współbieżności, równoczesnych operacji może spowodować w kolejce zwiększać i zmniejszać przed `empty` zwraca metody.  
  
 W poniższej tabeli przedstawiono typowe metody i operatory, które nie są bezpieczne współbieżności.  
  
|||  
|-|-|  
|[Wyczyść](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|  
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|  


  
###  <a name="queue-iterators"></a>Obsługa iteratora  
 `concurrent_queue` Zapewnia Iteratory, które nie są bezpieczne współbieżności. Zalecane jest użycie tych Iteratory tylko do debugowania.  
  
 A `concurrent_queue` elementy do przodu tylko przechodzi przez iterator. W poniższej tabeli przedstawiono operatorów, że obsługuje każdego iteratora.  
  
|Operator|Opis|  
|--------------|-----------------|  
|[operator ++](http://msdn.microsoft.com/en-us/4cfdd07e-927a-42f8-aaa0-d6881687f413)|Przechodzi do następnego elementu w kolejce. Ten operator jest przeciążony zapewnienie semantyki zarówno przyrostu przed i po przyrostu.|  
|[operator *](http://msdn.microsoft.com/en-us/a0e671fc-76e6-4fb4-b95c-ced4dd2b2017)|Pobiera odwołanie do bieżącego elementu.|  
|[operator ->](http://msdn.microsoft.com/en-us/41fa393d-ae1e-4a38-bb4b-19e8df709ca9)|Pobiera wskaźnik do bieżącego elementu.|  
  
 [[Górnej](#top)]  
  
##  <a name="unordered_map"></a>concurrent_unordered_map — klasa  
 [HYPERLINK "file:///C:\\\Users\\\thompet\\\AppData\\\Local\\\Temp\\\DxEditor\\\DduePreview\\\Default \\\798d7037-df37-4310-858b-6f590bbf6ebf\\\HTM\\\html\\\a217b4ac-af2b-4d41-94eb-09a75ee28622 "concurrency::concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) jest — klasa Klasa asocjacyjnej kontenera, który, podobnie jak [std::unordered_map](../../standard-library/unordered-map-class.md) klasy, określa długość zróżnicowanie sekwencję elementów typu [std::pair\<const klucza, Ty >](../../standard-library/pair-structure.md). Mapa nieuporządkowaną można traktować jako słownik, który można dodać parę kluczy i wartości do lub wyszukiwanie wartości według klucza. Ta klasa jest przydatne, jeśli masz wiele wątków lub zadania, które mają jednocześnie dostęp do udostępnionego kontenera, Wstaw do niego lub zaktualizować go.  
  
 W poniższym przykładzie przedstawiono podstawową strukturę przy użyciu `concurrent_unordered_map`. W tym przykładzie wstawia klucze znak z zakresu ["", "i"]. Ponieważ kolejność operacji jest nieokreślony, również jest nieokreślona końcowej dla każdego klucza. Jednak jest bezpieczne do wykonywania operacji wstawienia równolegle.  
  
 [!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]  
  
 Na przykład, który używa `concurrent_unordered_map` do wykonywanie mapowania i zmniejszanie operacji równolegle, zobacz [porady: wykonaj mapy i zmniejszyć operacji wykonywane równolegle](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).  
  
###  <a name="map-differences"></a>Różnice między concurrent_unordered_map — i unordered_map  
 `concurrent_unordered_map` Klasy przypomina `unordered_map` klasy. Następujące punkty ilustrują where `concurrent_unordered_map` różni się od `unordered_map`:  
  
-   `erase`, `bucket`, `bucket_count`, I `bucket_size` metody są nazywane `unsafe_erase`, `unsafe_bucket`, `unsafe_bucket_count`, i `unsafe_bucket_size`odpowiednio. `unsafe_` Konwencji nazewnictwa wskazuje, że te metody nie są bezpieczne współbieżności. Aby uzyskać więcej informacji na temat bezpieczeństwa współbieżności, zobacz [Safe współbieżności operacji](#map-safety).  
  
-   Operacje wstawiania nie unieważniają istniejące wskaźniki lub Iteratory nie należy zmieniać kolejność elementów, które już istnieją na mapie. Wstaw i przechodzić między nimi operacje mogą być wykonywane równocześnie.  
  
-   `concurrent_unordered_map`obsługuje przekazywać tylko iteracji.  
  
-   Wstawianie nie unieważnienie lub zaktualizuj Iteratory, które są zwracane przez `equal_range`. Wstawiania można dołączyć nierówne elementy do końca zakresu. Iterator punkty początkowe elementu takie same.  
  
 Aby uniknąć zakleszczenia, Metoda `concurrent_unordered_map` utrzymuje blokadę, gdy wywołuje alokatora, funkcje skrótu lub inny kod użytkownika. Należy Ponadto upewnij się, że funkcji skrótu ocenia zawsze równa kluczy na tę samą wartość. Najważniejsze funkcje skrótu dystrybucję kluczy jednolicie przestrzeni kod skrótu.  
  
###  <a name="map-safety"></a>Operacje bezpieczne współbieżności  
 `concurrent_unordered_map` Klasa umożliwia bezpieczne współbieżności operacji insert i dostęp do elementu. Operacje wstawiania nie unieważniają istniejące wskaźniki lub Iteratory. Operacje dostępu i przechodzenie iteratora są również bezpieczne współbieżności. W poniższej tabeli przedstawiono często używane `concurrent_unordered_map` metody i operatory, które są bezpieczne współbieżności.  
  
|||||  
|-|-|-|-|  
|[w](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|  
|`begin`|`empty`|`get_allocator`|`max_size`|  
|`cbegin`|`end`|`hash_function`|[Operator &#91; &#93;](reference/concurrent-unordered-map-class.md#operator_at)|  
|`cend`|`equal_range`|[Wstaw](reference/concurrent-unordered-map-class.md#insert)|`size`|  
  
 Mimo że `count` można wywołać metody bezpiecznie z jednocześnie uruchomionych wątków, inne wątki może odbierać różne wyniki, jeśli nowa wartość jednocześnie zostaną wstawione do kontenera.  
  
 W poniższej tabeli przedstawiono najczęściej używanych metod i operatory, które nie są bezpieczne współbieżności.  
  
||||  
|-|-|-|  
|`clear`|`max_load_factor`|`rehash`|  
|`load_factor`|[operator =](reference/concurrent-unordered-map-class.md#operator_eq) 


  
 Oprócz tych metod dowolnej metody, która rozpoczyna się z `unsafe_` również nie jest bezpieczne współbieżności.  
  
 [[Górnej](#top)]  
  
##  <a name="unordered_multimap"></a>concurrent_unordered_multimap — klasa  
 [Concurrency::concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) klasy przypomina `concurrent_unordered_map` klasy z tą różnicą, że umożliwia wiele wartości do mapowania na tym samym kluczem. Również różni się od `concurrent_unordered_map` w następujący sposób:  
  
-   [Concurrent_unordered_multimap::insert](reference/concurrent-unordered-multimap-class.md#insert) metodę zwracającą iterator zamiast `std::pair<iterator, bool>`.  

  
-   `concurrent_unordered_multimap` Klasa nie zapewnia `operator[]` ani `at` metody.  
  
 W poniższym przykładzie przedstawiono podstawową strukturę przy użyciu `concurrent_unordered_multimap`. W tym przykładzie wstawia klucze znak z zakresu ["", "i"]. `concurrent_unordered_multimap`Włącza klucz ma wiele wartości.  
  
 [!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]  
  
 [[Górnej](#top)]  
  
##  <a name="unordered_set"></a>concurrent_unordered_set — klasa  
 [Concurrency::concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md) klasy przypomina `concurrent_unordered_map` klasy z tą różnicą, że zarządza wartości zamiast pary kluczy i wartości. `concurrent_unordered_set` Klasa nie zapewnia `operator[]` ani `at` metody.  
  
 W poniższym przykładzie przedstawiono podstawową strukturę przy użyciu `concurrent_unordered_set`. W tym przykładzie wstawia wartości znakowych z zakresu ["", "i"]. Jest bezpieczne do wykonywania operacji wstawienia równolegle.  
  
 [!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]  
  
 [[Górnej](#top)]  
  
##  <a name="unordered_multiset"></a>concurrent_unordered_multiset — klasa  
 [Concurrency::concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) klasy przypomina `concurrent_unordered_set` klasy z tą różnicą, że umożliwia zduplikowane wartości. Również różni się od `concurrent_unordered_set` w następujący sposób:  
  

-   [Concurrent_unordered_multiset::insert](reference/concurrent-unordered-multiset-class.md#insert) metodę zwracającą iterator zamiast `std::pair<iterator, bool>`.  

  
-   `concurrent_unordered_multiset` Klasa nie zapewnia `operator[]` ani `at` metody.  
  
 W poniższym przykładzie przedstawiono podstawową strukturę przy użyciu `concurrent_unordered_multiset`. W tym przykładzie wstawia wartości znakowych z zakresu ["", "i"]. `concurrent_unordered_multiset`Umożliwia wartość występuje wiele razy.  
  
 [!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]  
  
 [[Górnej](#top)]  
  
##  <a name="combinable"></a>combinable — klasa  
 [Concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) klasa udostępnia magazynu wielokrotnego użytku, lokalnej wątku, który pozwala przeprowadzić obliczenia szczegółowych, a następnie scalić tych obliczeń do końcowego wyniku. Można potraktować `combinable` obiektu jako zmienną redukcyjną.  
  
 `combinable` Klasy jest przydatne, gdy zasób współużytkowany kilka wątków lub zadania. `combinable` Klasy pomaga wyeliminować stanu udostępnionego, zapewniając dostęp do zasobów udostępnionych w sposób wolny blokady. W związku z tym ta klasa stanowi alternatywę dla przy użyciu mechanizmu synchronizacji, na przykład elementu mutex synchronizujący dostęp do danych udostępnionych przez wiele wątków.  
  
###  <a name="combinable-features"></a>Metody i funkcje  
 W poniższej tabeli przedstawiono niektóre ważne metody `combinable` klasy. Aby uzyskać więcej informacji o wszystkich `combinable` metody klasy, zobacz [combinable — klasa](../../parallel/concrt/reference/combinable-class.md).  
  
|Metoda|Opis|  
|------------|-----------------|  
|[lokalne](reference/combinable-class.md#local)|Pobiera odwołanie do zmiennej lokalnej, która jest skojarzona z bieżącym kontekście wątku.|  
|[Wyczyść](reference/combinable-class.md#clear)|Usuwa wszystkie zmienne lokalne wątków z `combinable` obiektu.|  
|[Łączenie](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|Funkcja podana łączenie wygenerować końcowa wartość z zestawu wszystkie obliczenia lokalnej wątku.|  
  
 `combinable` Klasy to klasa szablonu, która jest sparametryzowana końcowego wyniku scalone. Wywołanie konstruktora domyślnego `T` typ parametru szablonu musi mieć konstruktora domyślnego i Konstruktor kopiujący. Jeśli `T` typ parametru szablonu nie ma domyślnego konstruktora, wywołanie przeciążonej wersja konstruktora, który przyjmuje jako jego parametr funkcji inicjowania.  
  
 Można przechowywać w dodatkowe dane `combinable` obiektu po wywołaniu metody [połączyć](reference/combinable-class.md#combine) lub [combine_each](reference/combinable-class.md#combine_each) metody. Możesz także wywołać `combine` i `combine_each` metody wiele razy. Jeśli żadna wartość lokalnego `combinable` obiekt zmian, `combine` i `combine_each` metody uzyskania tego samego wyniku zawsze, gdy są wywoływane.  
  
###  <a name="combinable-examples"></a>Przykłady  
 Przykłady dotyczące korzystania `combinable` , zobacz następujące tematy:  
  
-   [Instrukcje: korzystanie z wyników połączonych do poprawiania wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)  
  
-   [Instrukcje: korzystanie z wyników połączonych w celu łączenia zestawów](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)  
  
 [[Górnej](#top)]  
  
## <a name="related-topics"></a>Tematy pokrewne  
 [Instrukcje: korzystanie z kontenerów równoległych do zwiększania wydajności](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)  
 Pokazuje, jak przy użyciu kontenerów równoległych wydajne przechowywanie i uzyskać dostęp do danych równolegle.  
  
 [Instrukcje: korzystanie z wyników połączonych do poprawiania wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)  
 Przedstawia sposób użycia `combinable` klasy w celu usunięcia udostępniony stan, a tym samym poprawić wydajność.  
  
 [Instrukcje: korzystanie z wyników połączonych w celu łączenia zestawów](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)  
 Przedstawia sposób użycia `combine` funkcji do scalenia wątków lokalnych zestawów danych.  
  
 [Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)  
 W tym artykule opisano PPL, oferujący imperatywnych model programowania wspiera skalowalność i łatwość użycia dla tworzenie współbieżnych aplikacji.  
  
## <a name="reference"></a>Tematy pomocy  
 [concurrent_vector, klasa](../../parallel/concrt/reference/concurrent-vector-class.md)  
  
 [concurrent_queue, klasa](../../parallel/concrt/reference/concurrent-queue-class.md)  
  
 [concurrent_unordered_map, klasa](../../parallel/concrt/reference/concurrent-unordered-map-class.md)  
  
 [concurrent_unordered_multimap, klasa](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)  
  
 [concurrent_unordered_set, klasa](../../parallel/concrt/reference/concurrent-unordered-set-class.md)  
  
 [concurrent_unordered_multiset, klasa](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)  
  
 [combinable, klasa](../../parallel/concrt/reference/combinable-class.md)
