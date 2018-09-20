---
title: Równoległe kontenery oraz obiekty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb06cf0c4e3e5868a0dadeefb30c2e75158d4e32
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433390"
---
# <a name="parallel-containers-and-objects"></a>Równoległe kontenery oraz obiekty

Biblioteka równoległych wzorców (PPL) obejmuje kilka kontenerów i obiektów, które dostarczają wątkowo dostęp do swoich elementów.

A *współbieżnych kontenera* zapewnia bezpieczne pod względem współbieżności dostęp do najbardziej ważnych operacji. Funkcje te kontenery podobny do tych, które są dostarczane przez standardowej biblioteki języka C++. Na przykład [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) klasa przypomina [std::vector](../../standard-library/vector-class.md) klasy, chyba że `concurrent_vector` klasa umożliwia dołączanie elementów równolegle. Kontenery współbieżne należy użyć, gdy masz kod przetwarzania równoległego, która wymaga odczytu i zapisu do tego samego kontenera.

A *obiektów współbieżnych* współużytkowany jednocześnie składników. Proces, który oblicza stan obiektu współbieżnych równolegle daje ten sam wynik, jako innego procesu, który oblicza takiego samego stanu szeregowo. [Concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) klasa jest przykładem typu obiektu współbieżnych. `combinable` Klasa pozwala wykonywać obliczenia równoległe, a następnie połączyć te obliczenia na wynik końcowy. Użyj obiektów współbieżnych, gdy mechanizm synchronizacji, na przykład mutex, w przeciwnym razie użyje do synchronizowania dostępu do współdzielonej zmiennej lub zasobu.

##  <a name="top"></a> Sekcje

W tym temacie opisano następujące równoległe kontenery oraz obiekty, które szczegółowo.

Kontenery współbieżne:

- [concurrent_vector, klasa](#ctor)

   - [Różnice między concurrent_vector i wektorów](#ctor)

   - [Operacje bezpieczne pod względem współbieżności](#ctor)

   - [Wyjątek bezpieczeństwa](#ctor)

- [concurrent_queue, klasa](#queue)

   - [Różnice między concurrent_queue i kolejki](#queue-differences)

   - [Operacje bezpieczne pod względem współbieżności](#queue-safety)

   - [Obsługa iteratora](#queue-iterators)

- [concurrent_unordered_map, klasa](#unordered_map)

   - [Różnice między concurrent_unordered_map — i unordered_map](#map-differences)

   - [Operacje bezpieczne pod względem współbieżności](#map-safety)

- [concurrent_unordered_multimap, klasa](#unordered_multimap)

- [concurrent_unordered_set, klasa](#unordered_set)

- [concurrent_unordered_multiset, klasa](#unordered_multiset)

Współbieżne obiekty:

- [combinable, klasa](#combinable)

   - [Metody i funkcje](#combinable-features)

   - [Przykłady](#combinable-examples)

##  <a name="vector"></a> concurrent_vector — klasa

[Concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) klasy jest klasą kontenera sekwencji, która, podobnie jak w przypadku [std::vector](../../standard-library/vector-class.md) klasy, można losowo uzyskać dostęp do jego elementów. `concurrent_vector` Umożliwia klasy bezpieczne pod względem współbieżności dołączania i elementu dostęp do operacji. Dołącz operacje nie unieważniają istniejące wskaźniki i Iteratory. Operacje dostęp i przechodzenie iteratora również są bezpieczne pod względem współbieżności.

###  <a name="vector-differences"></a> Różnice między concurrent_vector i wektorów

`concurrent_vector` Klasa przypomina `vector` klasy. Złożoność append, dostęp do elementu i operacje dostępu do iteratora na `concurrent_vector` obiektu są takie same jak w przypadku `vector` obiektu. Następujące punkty ilustrują, gdzie `concurrent_vector` różni się od `vector`:

- Dołącz element dostępu, dostępu do iteratora i operacji przechodzenia iteratora na `concurrent_vector` obiektu są bezpieczne pod względem współbieżności.

- Elementy można dodać tylko do końca `concurrent_vector` obiektu. `concurrent_vector` Klasa nie zapewnia `insert` metody.

- A `concurrent_vector` obiekt nie korzystał [semantyki przenoszenia](../../cpp/rvalue-reference-declarator-amp-amp.md) podczas dołączania do niego.

- `concurrent_vector` Klasa nie zapewnia `erase` lub `pop_back` metody. Podobnie jak w przypadku `vector`, użyj [wyczyść](reference/concurrent-vector-class.md#clear) metodę, aby usunąć wszystkie elementy z `concurrent_vector` obiektu.

- `concurrent_vector` Klasy nie przechowuje jego elementy sposób ciągły w pamięci. W związku z tym, nie można użyć `concurrent_vector` klasy w taki sposób, skorzystaj z tablicy. Na przykład dla zmiennej o nazwie `v` typu `concurrent_vector`, wyrażenie `&v[0]+2` powoduje zachowanie niezdefiniowane.

- `concurrent_vector` Klasa definiuje [grow_by —](reference/concurrent-vector-class.md#grow_by) i [grow_to_at_least —](reference/concurrent-vector-class.md#grow_to_at_least) metody. Metody te przypominają [rozmiar](reference/concurrent-vector-class.md#resize) metody, z tą różnicą, że są one bezpieczne pod względem współbieżności.

- Element `concurrent_vector` obiektu nie przemieszczenie jej elementy, Dołącz do niej lub zmienić jego rozmiar. Dzięki temu istniejące wskaźniki i Iteratory, które były ważne podczas operacji jednoczesnych.

- Środowisko wykonawcze nie zawiera definicji wersji specjalistycznej metody `concurrent_vector` dla typu `bool`.

###  <a name="vector-safety"></a> Operacje bezpieczne pod względem współbieżności

Wszystkie metody, które dołącza do lub zwiększyć rozmiar `concurrent_vector` obiektu lub uzyskiwanie dostępu do elementu w `concurrent_vector` obiektu, są bezpieczne pod względem współbieżności. Wyjątkiem od tej reguły jest `resize` metody.

W poniższej tabeli przedstawiono typowe `concurrent_vector` metody i operatory, które są bezpieczne pod względem współbieżności.

||||
|-|-|-|

|[w](reference/concurrent-vector-class.md#at)|[zakończenia](reference/concurrent-vector-class.md#end)|[operator&#91;&#93;](reference/concurrent-vector-class.md#operator_at)||[ Rozpocznij](reference/concurrent-vector-class.md#begin)|[front](reference/concurrent-vector-class.md#front)|[push_back —](reference/concurrent-vector-class.md#push_back)||[ ponownie](reference/concurrent-vector-class.md#back)|[grow_by —](reference/concurrent-vector-class.md#grow_by)|[rbegin —](reference/concurrent-vector-class.md#rbegin)||[ pojemność](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least —](reference/concurrent-vector-class.md#grow_to_at_least)|[rend —](reference/concurrent-vector-class.md#rend)||[ pusty](reference/concurrent-vector-class.md#empty)|[max_size —](reference/concurrent-vector-class.md#max_size)|[rozmiar](reference/concurrent-vector-class.md#size)|

Operacje, które środowisko wykonawcze zapewnia zgodność ze standardowej biblioteki C++, na przykład `reserve`, nie są bezpieczne pod względem współbieżności. W poniższej tabeli przedstawiono typowe metody i operatory, które nie są bezpieczne pod względem współbieżności.

|||
|-|-|

|[Przypisz](reference/concurrent-vector-class.md#assign)|[zarezerwować](reference/concurrent-vector-class.md#reserve)||[ Wyczyść](reference/concurrent-vector-class.md#clear)|[rozmiar](reference/concurrent-vector-class.md#resize)||[ operator =](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit —](reference/concurrent-vector-class.md#shrink_to_fit)|

Operacje, zmodyfikuj wartość istniejące elementy, które nie są bezpieczne pod względem współbieżności. Użyj obiektu synchronizacji, takie jak [reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) obiekt, aby zsynchronizować współbieżne odczytu i zapisu do tego samego elementu danych. Aby uzyskać więcej informacji na temat obiektów synchronizacji zobacz [struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md).

Podczas konwertowania istniejący kod, który używa `vector` używać `concurrent_vector`, jednoczesnych operacji może spowodować, że działanie aplikacji można zmienić. Na przykład rozważmy następujący program, który wykonuje dwa zadania jednocześnie na `concurrent_vector` obiektu. Pierwsze zadanie dołącza dodatkowe elementy do `concurrent_vector` obiektu. Drugie zadanie oblicza sumę wszystkich elementów w tym samym obiekcie.

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

Mimo że `end` metoda jest bezpieczna pod kątem współbieżności, równoczesne wywołanie do [push_back —](reference/concurrent-vector-class.md#push_back) metoda powoduje, że wartość, która jest zwracana przez `end` można zmienić. Liczba elementów, które są przesyłane za pośrednictwem iteratora jest nieokreślony. W związku z tym ten program może tworzyć różne wyniki za każdym razem, uruchom go.

###  <a name="vector-exceptions"></a> Wyjątek bezpieczeństwa

Jeśli operacja wzrost lub przypisania zgłasza wyjątek, stan `concurrent_vector` obiekt staje się nieprawidłowy. Zachowanie `concurrent_vector` obiekt, który jest w nieprawidłowym stanie jest niezdefiniowana, chyba że określono inaczej. Jednak destruktor zawsze powoduje zwolnienie pamięci przydzielanej przez obiekt, nawet jeśli obiekt jest w nieprawidłowym stanie.

Typ danych elementów wektora `T`, musi spełniać następujące wymagania. W przeciwnym razie zachowanie `concurrent_vector` klasy jest niezdefiniowana.

- Destruktor nie może zgłaszać.

- Jeśli Konstruktor domyślny lub kopiowania zgłasza wyjątek, destruktor nie musi być zadeklarowany za pomocą `virtual` słowa kluczowego i jego musi działać poprawnie z pamięci inicjowany z wartością zerową.

[[Górnej](#top)]

##  <a name="queue"></a> concurrent_queue — klasa

[Concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) klasy, podobnie jak [std::queue](../../standard-library/queue-class.md) klasy, umożliwia dostęp do jego frontonu i wykonać ich kopię elementów. `concurrent_queue` Klasy umożliwia bezpieczne pod względem współbieżności umieścić w kolejce i pobierać operacji. `concurrent_queue` Klasa udostępnia także obsługa iteratora, który nie jest bezpieczna pod kątem współbieżności.

###  <a name="queue-differences"></a> Różnice między concurrent_queue i kolejki

`concurrent_queue` Klasa przypomina `queue` klasy. Następujące punkty ilustrują, gdzie `concurrent_queue` różni się od `queue`:

- Umieścić w kolejce i pobierać operacje na `concurrent_queue` obiektu są bezpieczne pod względem współbieżności.

- `concurrent_queue` Klasy zapewnia obsługę iteratora, który nie jest bezpieczna pod kątem współbieżności.

- `concurrent_queue` Klasa nie zapewnia `front` lub `pop` metody. `concurrent_queue` Klasy zastępuje te metody, definiując [try_pop —](reference/concurrent-queue-class.md#try_pop) metody.

- `concurrent_queue` Klasa nie zapewnia `back` metody. W związku z tym nie może przywoływać koniec kolejki.

- `concurrent_queue` Klasa udostępnia [unsafe_size —](reference/concurrent-queue-class.md#unsafe_size) zamiast metody `size` metody. `unsafe_size` Metoda nie jest bezpieczna pod kątem współbieżności.

###  <a name="queue-safety"></a> Operacje bezpieczne pod względem współbieżności

Wszystkie metody tego umieścić w kolejce do lub usuwania z kolejki z `concurrent_queue` obiektu są bezpieczne pod względem współbieżności.

W poniższej tabeli przedstawiono typowe `concurrent_queue` metody i operatory, które są bezpieczne pod względem współbieżności.

|||
|-|-|
|[pusty](reference/concurrent-queue-class.md#empty)|[push](reference/concurrent-queue-class.md#push)|
|[get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|

Mimo że `empty` metoda jest bezpieczna pod kątem współbieżności, operacja współbieżna może spowodować, że kolejka możliwość zwiększania i zmniejszania przed `empty` metoda zwraca.

W poniższej tabeli przedstawiono typowe metody i operatory, które nie są bezpieczne pod względem współbieżności.

|||
|-|-|
|[Usuń zaznaczenie](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|

###  <a name="queue-iterators"></a> Obsługa iteratora

`concurrent_queue` Zapewnia Iteratory, które nie są bezpieczne pod względem współbieżności. Zalecamy użycie te Iteratory tylko do debugowania.

A `concurrent_queue` iteratora przechodzi przez elementy w kierunku do przodu tylko. W poniższej tabeli przedstawiono operatorów, że obsługuje każdego iteratora.

|Operator|Opis|
|--------------|-----------------|
|`operator++`|Przechodzi do następnego elementu w kolejce. Ten operator jest przeciążony zapewnienie semantyki przyrostu przed i po przyrostu.|
|`operator*`|Pobiera odwołanie do bieżącego elementu.|
|`operator->`|Pobiera wskaźnik do bieżącego elementu.|

[[Górnej](#top)]

##  <a name="unordered_map"></a> concurrent_unordered_map — klasa

[Concurrency::concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) klasy jest klasą kontenerem asocjacyjnym, która, podobnie jak w przypadku [std::unordered_map](../../standard-library/unordered-map-class.md) klasy, kontroluje różnej długości sekwencje elementów typu [std::pair\<const Key, Ty >](../../standard-library/pair-structure.md). Mapy nieuporządkowanej można traktować jako słownik, który można dodać parę klucza i wartości do lub wyszukać wartość według klucza. Ta klasa jest przydatna, jeśli masz wiele wątków lub zadania, które mają jednocześnie dostęp do udostępnionych kontenerów, Wstaw do niej lub go zaktualizować.

Poniższy przykład pokazuje podstawową strukturę przy użyciu `concurrent_unordered_map`. W tym przykładzie Wstawia znak kluczy z zakresu ["" "i"]. Ponieważ kolejność operacji jest nieokreślony, również jest nieokreślony końcowa wartość dla każdego klucza. Jednak jest bezpieczne do wykonywania wstawienia równolegle.

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

Aby uzyskać przykład, który używa `concurrent_unordered_map` na wykonywanie mapowania i zmniejszanie operacji w sposób równoległy, zobacz [jak: wykonywać mapy i zmniejszyć operacji wykonywane równolegle](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

###  <a name="map-differences"></a> Różnice między concurrent_unordered_map — i unordered_map

`concurrent_unordered_map` Klasa przypomina `unordered_map` klasy. Następujące punkty ilustrują, gdzie `concurrent_unordered_map` różni się od `unordered_map`:

- `erase`, `bucket`, `bucket_count`, I `bucket_size` metody są nazywane `unsafe_erase`, `unsafe_bucket`, `unsafe_bucket_count`, i `unsafe_bucket_size`, odpowiednio. `unsafe_` Konwencji nazewnictwa wskazuje, że te metody nie są bezpieczne pod względem współbieżności. Aby uzyskać więcej informacji na temat bezpieczeństwa współbieżności, zobacz [operacje bezpieczne pod względem współbieżności](#map-safety).

- Operacje wstawiania nie unieważniają istniejące wskaźniki i Iteratory, nie należy zmieniać kolejność elementów, które już istnieją w mapie. Wstaw i przechodzić między nimi operacje mogą być wykonywane równocześnie.

- `concurrent_unordered_map` obsługuje przekazywać tylko iteracji.

- Wstawiania nie unieważnia ani zaktualizować Iteratory, które są zwracane przez `equal_range`. Wstawianie można dodać różne elementy do końca zakresu. Iterator wskazuje początek elementu równe.

W celu uniknięcia zakleszczenia, Metoda `concurrent_unordered_map` posiada blokadę, kiedy wywołuje alokatora pamięci, funkcje wyznaczania wartości skrótu lub inny kod użytkownika. Ponadto upewnij się, czy funkcji skrótu ocenia zawsze równa kluczy na tę samą wartość. Najważniejsze funkcje skrótu rozdystrybuować klucze równomiernie miejsce na kod skrótu.

###  <a name="map-safety"></a> Operacje bezpieczne pod względem współbieżności

`concurrent_unordered_map` Klasa umożliwia bezpieczne pod względem współbieżności operacje wstawiania i dostęp do elementu. Operacje wstawiania nie unieważniają istniejące wskaźniki i Iteratory. Operacje dostęp i przechodzenie iteratora również są bezpieczne pod względem współbieżności. W poniższej tabeli przedstawiono powszechnie używane `concurrent_unordered_map` metody i operatory, które są bezpieczne pod względem współbieżności.

|||||
|-|-|-|-|
|[at](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|
|`begin`|`empty`|`get_allocator`|`max_size`|
|`cbegin`|`end`|`hash_function`|[operator&#91;&#93;](reference/concurrent-unordered-map-class.md#operator_at)|
|`cend`|`equal_range`|[Wstaw](reference/concurrent-unordered-map-class.md#insert)|`size`|

Mimo że `count` metoda można bezpiecznie wywołać z jednocześnie uruchomionych wątków, różnych wątków może odbierać różne wyniki, jeśli jednocześnie dodaje się nową wartość do kontenera.

W poniższej tabeli przedstawiono najczęściej używanych metod i operatory, które nie są bezpieczne pod względem współbieżności.

||||
|-|-|-|
|`clear`|`max_load_factor`|`rehash`|
|`load_factor`|[operator=](reference/concurrent-unordered-map-class.md#operator_eq)

Oprócz tych metod dowolnej metody, rozpoczyna się od `unsafe_` również nie jest bezpieczna pod kątem współbieżności.

[[Górnej](#top)]

##  <a name="unordered_multimap"></a> concurrent_unordered_multimap — klasa

[Concurrency::concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) klasa przypomina `concurrent_unordered_map` klasy, z tą różnicą, że umożliwia ona wiele wartości mapować do tego samego klucza. Również różni się od `concurrent_unordered_map` w następujący sposób:

- [Concurrent_unordered_multimap::INSERT —](reference/concurrent-unordered-multimap-class.md#insert) metoda zwraca iterator, zamiast `std::pair<iterator, bool>`.

- `concurrent_unordered_multimap` Klasa nie zapewnia `operator[]` ani `at` metody.

Poniższy przykład pokazuje podstawową strukturę przy użyciu `concurrent_unordered_multimap`. W tym przykładzie Wstawia znak kluczy z zakresu ["" "i"]. `concurrent_unordered_multimap` Włącza klawisz aby mieć wiele wartości.

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

[[Górnej](#top)]

##  <a name="unordered_set"></a> concurrent_unordered_set — klasa

[Concurrency::concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md) klasa przypomina `concurrent_unordered_map` klasy, z tą różnicą, że zarządza wartości zamiast par kluczy i wartości. `concurrent_unordered_set` Klasa nie zapewnia `operator[]` ani `at` metody.

Poniższy przykład pokazuje podstawową strukturę przy użyciu `concurrent_unordered_set`. W tym przykładzie Wstawia znak wartości z zakresu ["" "i"]. Jest to bezpieczne do wykonywania wstawienia równolegle.

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

[[Górnej](#top)]

##  <a name="unordered_multiset"></a> concurrent_unordered_multiset — klasa

[Concurrency::concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) klasa przypomina `concurrent_unordered_set` klasy, z tą różnicą, że umożliwia ona zduplikowanych wartości. Również różni się od `concurrent_unordered_set` w następujący sposób:

- [Concurrent_unordered_multiset::INSERT —](reference/concurrent-unordered-multiset-class.md#insert) metoda zwraca iterator, zamiast `std::pair<iterator, bool>`.

- `concurrent_unordered_multiset` Klasa nie zapewnia `operator[]` ani `at` metody.

Poniższy przykład pokazuje podstawową strukturę przy użyciu `concurrent_unordered_multiset`. W tym przykładzie Wstawia znak wartości z zakresu ["" "i"]. `concurrent_unordered_multiset` Umożliwia wartość występuje wiele razy.

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

[[Górnej](#top)]

##  <a name="combinable"></a> combinable — klasa

[Concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) klasa udostępnia magazynu wielokrotnego użytku, lokalnej wątku, który pozwala wykonywać precyzyjną obliczeń, a następnie scalić te obliczenia na wynik końcowy. Można potraktować `combinable` obiektu jako zmienną redukcyjną.

`combinable` Klasy jest przydatne w przypadku, gdy zasób jest współużytkowana przez wiele wątków lub zadania. `combinable` Klasy pomaga wyeliminować udostępnionego stanu, zapewniając dostęp do zasobów udostępnionych w sposób, wolne od blokady. W związku z tym ta klasa stanowi alternatywę dla przy użyciu mechanizmu synchronizacji, na przykład mutex do synchronizowania dostępu do udostępnionych danych z wielu wątków.

###  <a name="combinable-features"></a> Metody i funkcje

W poniższej tabeli przedstawiono niektóre ważne metody `combinable` klasy. Aby uzyskać więcej informacji na temat wszystkich `combinable` metody klasy, zobacz [combinable — klasa](../../parallel/concrt/reference/combinable-class.md).

|Metoda|Opis|
|------------|-----------------|
|[lokalne](reference/combinable-class.md#local)|Pobiera odwołanie do zmiennej lokalnej, która jest skojarzona z bieżącym kontekstem wątku.|
|[Usuń zaznaczenie](reference/combinable-class.md#clear)|Usuwa wszystkie zmiennymi lokalnymi wątku z `combinable` obiektu.|
|[Łączenie](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|Funkcja łączenia podana wygenerować wartość końcową na podstawie zbiór wszystkich obliczeń lokalnej wątku.|

`combinable` Klasa jest klasą szablonu, które są parametryzowane na wynik końcowy scalone. Jeśli wywołanie konstruktora domyślnego `T` typu parametru szablonu muszą mieć domyślny konstruktor i Konstruktor kopiujący. Jeśli `T` typu parametru szablonu, nie ma domyślnego konstruktora, wywołaj przeciążona wersja konstruktora, który przyjmuje funkcję inicjowania jako parametr.

Można przechowywać w dodatkowe dane `combinable` obiektu po wywołaniu metody [połączyć](reference/combinable-class.md#combine) lub [combine_each —](reference/combinable-class.md#combine_each) metody. Można również wywołać `combine` i `combine_each` metody wiele razy. Jeśli żadna wartość lokalnego `combinable` obiektu zmian `combine` i `combine_each` metody uzyskania tego samego wyniku każdym razem, gdy są wywoływane.

###  <a name="combinable-examples"></a> Przykłady

Przykłady dotyczące korzystania `combinable` klasy, zobacz następujące tematy:

- [Instrukcje: korzystanie z wyników połączonych do poprawiania wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [Instrukcje: korzystanie z wyników połączonych w celu łączenia zestawów](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

[[Górnej](#top)]

## <a name="related-topics"></a>Tematy pokrewne

[Instrukcje: korzystanie z kontenerów równoległych do zwiększania wydajności](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
Pokazuje, jak za pomocą kontenerów równoległych wydajne magazynowanie i uzyskać dostęp do danych w sposób równoległy.

[Instrukcje: korzystanie z wyników połączonych do poprawiania wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
Ilustruje sposób używania `combinable` klasy, aby wyeliminować udostępnionego stanu, a przez to zwiększyć wydajność.

[Instrukcje: korzystanie z wyników połączonych w celu łączenia zestawów](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
Ilustruje sposób używania `combine` funkcję, aby scalić wątków lokalnych zestawów danych.

[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
W tym artykule opisano PPL, która zapewnia model programowania na najwyższym skalowalność i łatwość użytkowania umożliwiający projektowanie aplikacji współbieżnych.

## <a name="reference"></a>Tematy pomocy

[concurrent_vector, klasa](../../parallel/concrt/reference/concurrent-vector-class.md)

[concurrent_queue, klasa](../../parallel/concrt/reference/concurrent-queue-class.md)

[concurrent_unordered_map, klasa](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[concurrent_unordered_multimap, klasa](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[concurrent_unordered_set, klasa](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[concurrent_unordered_multiset, klasa](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[combinable, klasa](../../parallel/concrt/reference/combinable-class.md)
