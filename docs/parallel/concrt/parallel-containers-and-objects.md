---
title: Równoległe kontenery oraz obiekty
ms.date: 03/27/2019
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
ms.openlocfilehash: f3fb2bb57c8bcf65de0a7f74f2992050d8257429
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363044"
---
# <a name="parallel-containers-and-objects"></a>Równoległe kontenery oraz obiekty

Biblioteka wzorców równoległych (PPL) zawiera kilka kontenerów i obiektów, które zapewniają bezpieczny dostęp do ich elementów.

Kontener *równoczesnych* zapewnia bezpieczny dostęp do najważniejszych operacji. W tym miejscu, współbieżność oznacza, że wskaźniki lub iteratory są zawsze prawidłowe. Nie jest to gwarancja inicjowania elementu lub określonej kolejności przechodzenia. Funkcjonalność tych kontenerów przypomina te, które są dostarczane przez bibliotekę standardową języka C++. Na przykład [współbieżność::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) klasa przypomina [klasę std::vector,](../../standard-library/vector-class.md) z tą `concurrent_vector` różnicą, że klasa umożliwia dołączanie elementów równolegle. Użyj równoczesnych kontenerów, gdy masz równoległy kod, który wymaga zarówno odczytu i zapisu dostępu do tego samego kontenera.

*Równoczesnych obiektu* jest współużytkowana jednocześnie między składnikami. Proces, który oblicza stan równoczesnych obiektów równolegle daje taki sam wynik jak inny proces, który oblicza ten sam stan szeregowo. [Współbieżność::combinable](../../parallel/concrt/reference/combinable-class.md) klasa jest jednym z przykładów równoczesnych typów obiektów. Klasa `combinable` umożliwia równoległe wykonywanie obliczeń, a następnie łączenie tych obliczeń w wynik końcowy. Współbieżne obiekty można użyć mechanizmu synchronizacji, na przykład obiektu mutex, aby zsynchronizować dostęp do udostępnionej zmiennej lub zasobu.

## <a name="sections"></a><a name="top"></a>Sekcje

W tym temacie opisano szczegółowo następujące równoległe kontenery i obiekty.

Kontenery równoczesnych:

- [Klasa concurrent_vector](#vector)

  - [Różnice między concurrent_vector a wektorem](#vector-differences)

  - [Operacje bezpieczne dla współbieżności](#vector-safety)

  - [Bezpieczeństwo wyjątków](#vector-exceptions)

- [Klasa concurrent_queue](#queue)

  - [Różnice między concurrent_queue a kolejką](#queue-differences)

  - [Operacje bezpieczne dla współbieżności](#queue-safety)

  - [Obsługa iteratora](#queue-iterators)

- [Klasa concurrent_unordered_map](#unordered_map)

  - [Różnice między concurrent_unordered_map a unordered_map](#map-differences)

  - [Operacje bezpieczne dla współbieżności](#map-safety)

- [Klasa concurrent_unordered_multimap](#unordered_multimap)

- [Klasa concurrent_unordered_set](#unordered_set)

- [Klasa concurrent_unordered_multiset](#unordered_multiset)

Obiekty współbieżne:

- [combinable — Klasa](#combinable)

  - [Metody i funkcje](#combinable-features)

  - [Przykłady](#combinable-examples)

## <a name="concurrent_vector-class"></a><a name="vector"></a>Klasa concurrent_vector

[Współbieżność::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) klasa jest klasą kontenera sekwencji, która, podobnie jak [klasa std::vector,](../../standard-library/vector-class.md) umożliwia losowy dostęp do jego elementów. Klasa `concurrent_vector` umożliwia współbieżności bezpieczne dołączanie i operacje dostępu do elementów. Operacje dołączania nie unieważniają istniejących wskaźników ani iteratorów. Dostęp do iteratora i operacje przechodzenia są również bezpieczne współbieżności. W tym miejscu, współbieżność oznacza, że wskaźniki lub iteratory są zawsze prawidłowe. Nie jest to gwarancja inicjowania elementu lub określonej kolejności przechodzenia.

### <a name="differences-between-concurrent_vector-and-vector"></a><a name="vector-differences"></a>Różnice między concurrent_vector a wektorem

Klasa `concurrent_vector` bardzo przypomina `vector` klasę. Złożoność dołączania, dostępu do elementu i operacji dostępu `concurrent_vector` iteratora na `vector` obiekcie są takie same jak dla obiektu. Poniższe punkty ilustrują, gdzie `concurrent_vector` różni się od: `vector`

- Dołącz, dostęp do elementu, dostęp do iteratora i `concurrent_vector` operacje przechodzenia iteratora na obiekcie są bezpieczne współbieżności.

- Elementy można dodawać tylko na `concurrent_vector` końcu obiektu. Klasa `concurrent_vector` nie zapewnia `insert` metody.

- Obiekt `concurrent_vector` nie używa [semantyki przenoszenia](../../cpp/rvalue-reference-declarator-amp-amp.md) podczas dołączania do niego.

- Klasa `concurrent_vector` nie zawiera `erase` lub `pop_back` metody. Podobnie `vector`jak w przypadku , użyj [clear](reference/concurrent-vector-class.md#clear) metody, aby usunąć wszystkie elementy z `concurrent_vector` obiektu.

- Klasa `concurrent_vector` nie przechowuje jego elementy ciągłe w pamięci. W związku z tym `concurrent_vector` nie można używać klasy na wszystkie sposoby, które można użyć tablicy. Na przykład dla zmiennej `concurrent_vector`o nazwie `&v[0]+2` `v` typu wyrażenie tworzy niezdefiniowane zachowanie.

- Klasa `concurrent_vector` definiuje [metody grow_by](reference/concurrent-vector-class.md#grow_by) i [grow_to_at_least.](reference/concurrent-vector-class.md#grow_to_at_least) Metody te przypominają metodę [zmiany rozmiaru,](reference/concurrent-vector-class.md#resize) z tą różnicą, że są one bezpieczne współbieżności.

- Obiekt `concurrent_vector` nie przenosi swoich elementów podczas dołączania do niego ani zmieniania jego rozmiaru. Dzięki temu istniejące wskaźniki i iteratory pozostają prawidłowe podczas równoczesnych operacji.

- Środowisko wykonawcze nie definiuje wyspecjalizowanej `concurrent_vector` `bool`wersji dla typu .

### <a name="concurrency-safe-operations"></a><a name="vector-safety"></a>Operacje bezpieczne dla współbieżności

Wszystkie metody, które dołączyć lub zwiększyć `concurrent_vector` rozmiar obiektu lub uzyskać `concurrent_vector` dostęp do elementu w obiekcie, są współbieżności bezpieczne. W tym miejscu, współbieżność oznacza, że wskaźniki lub iteratory są zawsze prawidłowe. Nie jest to gwarancja inicjowania elementu lub określonej kolejności przechodzenia. Wyjątkiem od tej reguły `resize` jest metoda.

W poniższej tabeli przedstawiono typowe `concurrent_vector` metody i operatory, które są bezpieczne współbieżności.

||||
|-|-|-|
|[O](reference/concurrent-vector-class.md#at)|[Końcu](reference/concurrent-vector-class.md#end)|[&#91;&#93;operatora](reference/concurrent-vector-class.md#operator_at)|
|[Rozpocząć](reference/concurrent-vector-class.md#begin)|[Przednie](reference/concurrent-vector-class.md#front)|[push_back](reference/concurrent-vector-class.md#push_back)|
|[Wstecz](reference/concurrent-vector-class.md#back)|[grow_by](reference/concurrent-vector-class.md#grow_by)|[rbegin (rbegin)](reference/concurrent-vector-class.md#rbegin)|
|[capacity](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)|[Rend](reference/concurrent-vector-class.md#rend)|
|[Pusty](reference/concurrent-vector-class.md#empty)|[Max_size](reference/concurrent-vector-class.md#max_size)|[Rozmiar](reference/concurrent-vector-class.md#size)|

Operacje, które środowisko wykonawcze zapewnia zgodność z biblioteką standardową `reserve`języka C++, na przykład, nie są bezpieczne współbieżności. W poniższej tabeli przedstawiono typowe metody i operatory, które nie są bezpieczne współbieżności.

|||
|-|-|
|[Przypisać](reference/concurrent-vector-class.md#assign)|[Rezerwy](reference/concurrent-vector-class.md#reserve)|
|[Wyczyść](reference/concurrent-vector-class.md#clear)|[Zmienić rozmiar](reference/concurrent-vector-class.md#resize)|
|[operator=](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit](reference/concurrent-vector-class.md#shrink_to_fit)|

Operacje modyfikując wartość istniejących elementów nie są bezpieczne współbieżności. Użyj obiektu synchronizacji, takiego jak [obiekt reader_writer_lock,](../../parallel/concrt/reference/reader-writer-lock-class.md) aby zsynchronizować równoczesne operacje odczytu i zapisu z tym samym elementem danych. Aby uzyskać więcej informacji o obiektach synchronizacji, zobacz [Synchronizacja struktur danych](../../parallel/concrt/synchronization-data-structures.md).

Podczas konwertowania istniejącego kodu, który używa `vector` do użycia, `concurrent_vector`równoczesnych operacji może spowodować zachowanie aplikacji, aby zmienić. Rozważmy na przykład następujący program, który jednocześnie wykonuje `concurrent_vector` dwa zadania na obiekcie. Pierwsze zadanie dołącza dodatkowe elementy `concurrent_vector` do obiektu. Drugie zadanie oblicza sumę wszystkich elementów w tym samym obiekcie.

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

Mimo `end` że metoda jest współbieżność bezpieczne, równoczesnych wywołania [push_back](reference/concurrent-vector-class.md#push_back) metoda powoduje, `end` że wartość, która jest zwracana przez do zmiany. Liczba elementów, które przechodzi iteratora jest nieokreślony. W związku z tym ten program może produkować inny wynik za każdym razem, gdy go uruchomić. Gdy typ elementu nie jest trywialne, jest możliwe dla `push_back` `end` sytuacji wyścigu istnieje między i wywołania. Metoda `end` może zwrócić element, który jest przydzielony, ale nie w pełni zainicjowane.

### <a name="exception-safety"></a><a name="vector-exceptions"></a>Bezpieczeństwo wyjątków

Jeśli operacja wzrostu lub przypisania zgłasza wyjątek, stan `concurrent_vector` obiektu staje się nieprawidłowy. Zachowanie `concurrent_vector` obiektu, który jest w nieprawidłowym stanie jest niezdefiniowana, chyba że określono inaczej. Jednak destruktor zawsze zwalnia pamięć, która przydziela obiekt, nawet jeśli obiekt jest w nieprawidłowym stanie.

Typ danych elementów wektorowych `T`musi spełniać następujące wymagania. W przeciwnym razie `concurrent_vector` zachowanie klasy jest niezdefiniowane.

- Destruktor nie może rzucać.

- Jeśli domyślny lub kopiuj konstruktora zgłasza, destruktor nie może być zadeklarowany przy użyciu `virtual` słowa kluczowego i musi działać poprawnie z pamięcią zainicjowaną zeru.

[[Góra](#top)]

## <a name="concurrent_queue-class"></a><a name="queue"></a>Klasa concurrent_queue

[Współbieżność::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) klasa, podobnie jak [std::queue](../../standard-library/queue-class.md) klasy, umożliwia dostęp do jego elementów z przodu i z tyłu. Klasa `concurrent_queue` umożliwia współtworza bezpieczne enqueue i dequeue operacji. W tym miejscu, współbieżność oznacza, że wskaźniki lub iteratory są zawsze prawidłowe. Nie jest to gwarancja inicjowania elementu lub określonej kolejności przechodzenia. Klasa `concurrent_queue` zapewnia również obsługę iteratora, który nie jest bezpieczny dla współbieżności.

### <a name="differences-between-concurrent_queue-and-queue"></a><a name="queue-differences"></a>Różnice między concurrent_queue a kolejką

Klasa `concurrent_queue` bardzo przypomina `queue` klasę. Poniższe punkty ilustrują, gdzie `concurrent_queue` różni się od: `queue`

- Operacje enqueue i dequeue na `concurrent_queue` obiekcie są bezpieczne współbieżności.

- Klasa `concurrent_queue` zapewnia obsługę iteratora, który nie jest bezpieczny dla współbieżności.

- Klasa `concurrent_queue` nie zawiera `front` lub `pop` metody. Klasa `concurrent_queue` zastępuje te metody, definiując [metodę try_pop.](reference/concurrent-queue-class.md#try_pop)

- Klasa `concurrent_queue` nie zapewnia `back` metody. W związku z tym nie można odwołać się do końca kolejki.

- Klasa `concurrent_queue` zawiera [unsafe_size](reference/concurrent-queue-class.md#unsafe_size) metodę zamiast `size` metody. Metoda `unsafe_size` nie jest bezpieczna współbieżności.

### <a name="concurrency-safe-operations"></a><a name="queue-safety"></a>Operacje bezpieczne dla współbieżności

Wszystkie metody, które są w kolejce do `concurrent_queue` lub dequeue z obiektu są współbieżności bezpieczne. W tym miejscu, współbieżność oznacza, że wskaźniki lub iteratory są zawsze prawidłowe. Nie jest to gwarancja inicjowania elementu lub określonej kolejności przechodzenia.

W poniższej tabeli przedstawiono typowe `concurrent_queue` metody i operatory, które są bezpieczne współbieżności.

|||
|-|-|
|[Pusty](reference/concurrent-queue-class.md#empty)|[Push](reference/concurrent-queue-class.md#push)|
|[Get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|

Mimo `empty` że metoda jest bezpieczna współbieżności, jednoczesna operacja może spowodować kolejki `empty` rosnąć lub zmniejszać przed zwraca metodę.

W poniższej tabeli przedstawiono typowe metody i operatory, które nie są bezpieczne współbieżności.

|||
|-|-|
|[Wyczyść](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|

### <a name="iterator-support"></a><a name="queue-iterators"></a>Obsługa iteratora

Zapewnia `concurrent_queue` iteratory, które nie są bezpieczne współbieżności. Zaleca się użycie tych iteratorów tylko do debugowania.

Iterator `concurrent_queue` przechodzi przez elementy tylko w kierunku do przodu. W poniższej tabeli przedstawiono operatory, które obsługuje każdy iterator.

|Operator|Opis|
|--------------|-----------------|
|`operator++`|Przejście do następnego elementu w kolejce. Ten operator jest przeciążony, aby zapewnić zarówno semantyki przyrostu wstępnego, jak i przyrostowego.|
|`operator*`|Pobiera odwołanie do bieżącego elementu.|
|`operator->`|Pobiera wskaźnik do bieżącego elementu.|

[[Góra](#top)]

## <a name="concurrent_unordered_map-class"></a><a name="unordered_map"></a>Klasa concurrent_unordered_map

[Współbieżność::concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) klasa jest klasą kontenera zespolonego, która podobnie jak klasa [std::unordered_map](../../standard-library/unordered-map-class.md) kontroluje sekwencję różnych długości elementów typu [std::pair\<const Key, Ty>](../../standard-library/pair-structure.md). Nieurządzonych map należy potraktować jako słownik, do którego można dodać parę kluczy i wartości lub wyszukać wartość według klucza. Ta klasa jest przydatna, gdy masz wiele wątków lub zadań, które muszą jednocześnie uzyskiwać dostęp do udostępnionego kontenera, wstawić do niego lub zaktualizować go.

W poniższym przykładzie przedstawiono podstawową strukturę użycia `concurrent_unordered_map`. W tym przykładzie wstawia klawisze znaków w zakresie ['a', 'i']. Ponieważ kolejność operacji jest nieokreślony, ostateczna wartość dla każdego klucza jest również nieokreślony. Jednak jest to bezpieczne, aby wykonać wstawienia równolegle.

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

Na przykład, który `concurrent_unordered_map` używa do wykonywania mapy i zmniejszyć działanie równolegle, zobacz [Jak: Wykonywanie map i zmniejszanie operacji równolegle](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

### <a name="differences-between-concurrent_unordered_map-and-unordered_map"></a><a name="map-differences"></a>Różnice między concurrent_unordered_map a unordered_map

Klasa `concurrent_unordered_map` bardzo przypomina `unordered_map` klasę. Poniższe punkty ilustrują, gdzie `concurrent_unordered_map` różni się od: `unordered_map`

- , `erase` `bucket`, `bucket_count`i `bucket_size` metody `unsafe_erase`są `unsafe_bucket` `unsafe_bucket_count`nazwane `unsafe_bucket_size`, , i , odpowiednio. Konwencja `unsafe_` nazewnictwa wskazuje, że te metody nie są bezpieczne współbieżności. Aby uzyskać więcej informacji na temat bezpieczeństwa współbieżności, zobacz [Operacje bezpieczne współbieżności](#map-safety).

- Operacje wstawiania nie unieważniają istniejących wskaźników ani iteratorów ani nie zmieniają kolejności elementów, które już istnieją na mapie. Operacje wstawiania i przechodzenia mogą występować jednocześnie.

- `concurrent_unordered_map`obsługuje tylko iterację do przodu.

- Wstawianie nie unieważnia ani nie aktualizuje `equal_range`iteratorów, które są zwracane przez program . Wstawianie może dołączać nierówne elementy na końcu zakresu. Iterator begin wskazuje na równy element.

Aby uniknąć zakleszczenia, `concurrent_unordered_map` żadna metoda zawiera blokadę, gdy wywołuje alokator pamięci, funkcje mieszania lub inny kod zdefiniowany przez użytkownika. Ponadto należy upewnić się, że funkcja mieszania zawsze ocenia równe klucze do tej samej wartości. Najlepsze funkcje mieszania równomiernie rozdzielają klucze w przestrzeni kodu skrótu.

### <a name="concurrency-safe-operations"></a><a name="map-safety"></a>Operacje bezpieczne dla współbieżności

Klasa `concurrent_unordered_map` umożliwia operacje wstawiania i dostępu do elementu bezpieczne współbieżności. Operacje wstawiania nie unieważniają istniejących wskaźników ani iteratorów. Dostęp do iteratora i operacje przechodzenia są również bezpieczne współbieżności. W tym miejscu, współbieżność oznacza, że wskaźniki lub iteratory są zawsze prawidłowe. Nie jest to gwarancja inicjowania elementu lub określonej kolejności przechodzenia. W poniższej tabeli `concurrent_unordered_map` przedstawiono powszechnie używane metody i operatory, które są bezpieczne współbieżności.

|||||
|-|-|-|-|
|[O](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|
|`begin`|`empty`|`get_allocator`|`max_size`|
|`cbegin`|`end`|`hash_function`|[&#91;&#93;operatora](reference/concurrent-unordered-map-class.md#operator_at)|
|`cend`|`equal_range`|[Wstawić](reference/concurrent-unordered-map-class.md#insert)|`size`|

Chociaż `count` metoda może być wywoływana bezpiecznie z jednocześnie uruchomionych wątków, różne wątki mogą odbierać różne wyniki, jeśli nowa wartość jest jednocześnie wstawiana do kontenera.

W poniższej tabeli przedstawiono powszechnie używane metody i operatory, które nie są bezpieczne dla współbieżności.

||||
|-|-|-|
|`clear`|`max_load_factor`|`rehash`|
|`load_factor`|[operator=](reference/concurrent-unordered-map-class.md#operator_eq)

Oprócz tych metod, każda metoda, `unsafe_` która zaczyna się od również nie współbieżności bezpieczne.

[[Góra](#top)]

## <a name="concurrent_unordered_multimap-class"></a><a name="unordered_multimap"></a>Klasa concurrent_unordered_multimap

[Współbieżność::concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) klasa bardzo przypomina klasę, `concurrent_unordered_map` z tą różnicą, że umożliwia wiele wartości do mapowania do tego samego klucza. Różni się również `concurrent_unordered_map` od następujących sposobów:

- Metoda [concurrent_unordered_multimap::insert](reference/concurrent-unordered-multimap-class.md#insert) zwraca iterator zamiast `std::pair<iterator, bool>`.

- Klasa `concurrent_unordered_multimap` nie zawiera `operator[]` ani `at` metody.

W poniższym przykładzie przedstawiono podstawową strukturę użycia `concurrent_unordered_multimap`. W tym przykładzie wstawia klawisze znaków w zakresie ['a', 'i']. `concurrent_unordered_multimap`umożliwia klucz ma wiele wartości.

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

[[Góra](#top)]

## <a name="concurrent_unordered_set-class"></a><a name="unordered_set"></a>Klasa concurrent_unordered_set

[Współbieżność::concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md) klasa bardzo przypomina klasę, `concurrent_unordered_map` z tą różnicą, że zarządza wartościami zamiast par kluczy i wartości. Klasa `concurrent_unordered_set` nie zawiera `operator[]` ani `at` metody.

W poniższym przykładzie przedstawiono podstawową strukturę użycia `concurrent_unordered_set`. W tym przykładzie wstawia wartości znaków w zakresie ['a', 'i']. Można bezpiecznie wykonywać wstawienia równolegle.

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

[[Góra](#top)]

## <a name="concurrent_unordered_multiset-class"></a><a name="unordered_multiset"></a>Klasa concurrent_unordered_multiset

[Współbieżność::concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) klasa bardzo przypomina klasę, z `concurrent_unordered_set` tą różnicą, że pozwala na zduplikowane wartości. Różni się również `concurrent_unordered_set` od następujących sposobów:

- Metoda [concurrent_unordered_multiset::insert](reference/concurrent-unordered-multiset-class.md#insert) zwraca iterator zamiast `std::pair<iterator, bool>`.

- Klasa `concurrent_unordered_multiset` nie zawiera `operator[]` ani `at` metody.

W poniższym przykładzie przedstawiono podstawową strukturę użycia `concurrent_unordered_multiset`. W tym przykładzie wstawia wartości znaków w zakresie ['a', 'i']. `concurrent_unordered_multiset`umożliwia wiele razy występować wartości.

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

[[Góra](#top)]

## <a name="combinable-class"></a><a name="combinable"></a>kombinowalna klasa

[Współbieżność::combinable](../../parallel/concrt/reference/combinable-class.md) klasa zapewnia wielokrotnego korzystania z magazynu lokalnego wątku, który umożliwia wykonywanie obliczeń szczegółowe, a następnie scalanie tych obliczeń w wynik końcowy. Obiekt można potraktować `combinable` jako zmienną redukcjów.

Klasa `combinable` jest przydatna, gdy masz zasób, który jest współużytkowane przez kilka wątków lub zadań. Klasa `combinable` pomaga wyeliminować stan udostępniony, zapewniając dostęp do zasobów udostępnionych w sposób bez blokady. W związku z tym ta klasa stanowi alternatywę dla przy użyciu mechanizmu synchronizacji, na przykład obiektu mutex, do synchronizacji dostępu do udostępnionych danych z wielu wątków.

### <a name="methods-and-features"></a><a name="combinable-features"></a>Metody i funkcje

W poniższej tabeli przedstawiono `combinable` niektóre z ważnych metod klasy. Aby uzyskać więcej `combinable` informacji na temat wszystkich metod klasy, zobacz [kombinowalną klasę](../../parallel/concrt/reference/combinable-class.md).

|Metoda|Opis|
|------------|-----------------|
|[Lokalnych](reference/combinable-class.md#local)|Pobiera odwołanie do zmiennej lokalnej, która jest skojarzona z bieżącym kontekstem wątku.|
|[Wyczyść](reference/combinable-class.md#clear)|Usuwa wszystkie zmienne lokalne wątku `combinable` z obiektu.|
|[combine](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|Używa dostarczonej funkcji kombajnu do generowania wartości końcowej z zestawu wszystkich obliczeń lokalnych wątków.|

Klasa `combinable` jest klasą szablonu, która jest sparametryzowana na końcowy wynik scalony. Jeśli wywołasz konstruktora `T` domyślnego, typ parametru szablonu musi mieć domyślny konstruktor i konstruktor kopii. Jeśli `T` typ parametru szablonu nie ma domyślnego konstruktora, wywołaj przeciążoną wersję konstruktora, która przyjmuje funkcję inicjowania jako parametr.

Dodatkowe dane w `combinable` obiekcie można przechowywać po wywołaniu metody [kombajnu](reference/combinable-class.md#combine) lub [combine_each.](reference/combinable-class.md#combine_each) Można również `combine` wywołać `combine_each` i metody wiele razy. Jeśli nie zmieni `combinable` się wartość `combine` lokalna w obiekcie, i `combine_each` metody dają taki sam wynik za każdym razem, gdy są wywoływane.

### <a name="examples"></a><a name="combinable-examples"></a>Przykłady

Aby uzyskać przykłady dotyczące `combinable` używania klasy, zobacz następujące tematy:

- [Instrukcje: korzystanie z wyników połączonych do poprawiania wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [Instrukcje: korzystanie z wyników połączonych w celu łączenia zestawów](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

[[Góra](#top)]

## <a name="related-topics"></a>Tematy pokrewne

[Instrukcje: korzystanie z kontenerów równoległych do zwiększania wydajności](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
Pokazuje, jak używać kontenerów równoległych do efektywnego przechowywania i uzyskiwania dostępu do danych równolegle.

[Instrukcje: korzystanie z wyników połączonych do poprawiania wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
Pokazuje, jak `combinable` używać klasy, aby wyeliminować stan udostępniony, a tym samym zwiększyć wydajność.

[Instrukcje: korzystanie z wyników połączonych w celu łączenia zestawów](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
Pokazuje, jak `combine` używać funkcji do scalania lokalnych zestawów danych wątku.

[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
W tym artykule opisano PPL, który zapewnia imperatywne model programowania, który promuje skalowalność i łatwość użycia do tworzenia równoczesnych aplikacji.

## <a name="reference"></a>Dokumentacja

[Klasa concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)

[Klasa concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)

[Klasa concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[Klasa concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[Klasa concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[Klasa concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[combinable — Klasa](../../parallel/concrt/reference/combinable-class.md)
