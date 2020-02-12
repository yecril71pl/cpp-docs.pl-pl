---
title: Równoległe kontenery oraz obiekty
ms.date: 03/27/2019
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
ms.openlocfilehash: 04b38fdc66a5c37a1780deaae4ae165f63238d93
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142904"
---
# <a name="parallel-containers-and-objects"></a>Równoległe kontenery oraz obiekty

Biblioteka równoległych wzorców (PPL) zawiera kilka kontenerów i obiektów, które zapewniają bezpieczny wątkowy dostęp do ich elementów.

*Współbieżny kontener* zapewnia bezpieczny dostęp współbieżności do najważniejszych operacji. W tym miejscu są zawsze ważne wskaźniki lub Iteratory, które są bezpieczne. Nie jest to gwarancja inicjalizacji elementu lub konkretnej kolejności przechodzenia. Funkcje tych kontenerów są podobne do tych, które są udostępniane przez C++ bibliotekę standardową. Na przykład Klasa [concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) jest podobna do klasy [std:: Vector](../../standard-library/vector-class.md) , z tą różnicą, że Klasa `concurrent_vector` umożliwia równoczesne Dodawanie elementów. Używaj współbieżnych kontenerów w przypadku równoległego kodu, który wymaga dostępu do odczytu i zapisu do tego samego kontenera.

*Obiekt współbieżny* jest udostępniany jednocześnie między składnikami. Proces, który oblicza stan współbieżnego obiektu równolegle, daje ten sam wynik, co inny proces, który obliczy ten sam stan szeregowo. Klasa [concurrency:: kombinowane](../../parallel/concrt/reference/combinable-class.md) jest jednym z przykładowych typów obiektów współbieżnych. Klasa `combinable` umożliwia równoległe wykonywanie obliczeń, a następnie łączenie tych obliczeń w końcowy wynik. Używaj współbieżnych obiektów, gdy w inny sposób użyjesz mechanizmu synchronizacji, na przykład, elementu mutex, aby synchronizować dostęp do udostępnionej zmiennej lub zasobu.

## <a name="top"></a>Poszczególne

W tym temacie opisano szczegóły następujących kontenerów równoległych i obiektów.

Kontenery współbieżne:

- [concurrent_vector, klasa](#vector)

   - [Różnice między concurrent_vector i wektorem](#vector-differences)

   - [Operacje dotyczące współbieżności](#vector-safety)

   - [Bezpieczeństwo wyjątków](#vector-exceptions)

- [concurrent_queue, klasa](#queue)

   - [Różnice między concurrent_queue i kolejką](#queue-differences)

   - [Operacje dotyczące współbieżności](#queue-safety)

   - [Obsługa iteratora](#queue-iterators)

- [concurrent_unordered_map, klasa](#unordered_map)

   - [Różnice między concurrent_unordered_map i unordered_map](#map-differences)

   - [Operacje dotyczące współbieżności](#map-safety)

- [concurrent_unordered_multimap, klasa](#unordered_multimap)

- [concurrent_unordered_set, klasa](#unordered_set)

- [concurrent_unordered_multiset, klasa](#unordered_multiset)

Obiekty współbieżne:

- [combinable, klasa](#combinable)

   - [Metody i funkcje](#combinable-features)

   - [Przykłady](#combinable-examples)

## <a name="vector"></a>Klasa concurrent_vector

[Concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) Klasa jest klasą kontenera sekwencji, która podobnie jak Klasa [Vector:: wektor](../../standard-library/vector-class.md) , umożliwia losowo dostęp do jej elementów. Klasa `concurrent_vector` umożliwia bezpieczne wykonywanie operacji dołączania i dostępu do elementów. Operacje dołączania nie weryfikują istniejących wskaźników lub iteratorów. Operacje dostępu i przechodzenia iteratora są również bezpieczne dla współbieżności. W tym miejscu są zawsze ważne wskaźniki lub Iteratory, które są bezpieczne. Nie jest to gwarancja inicjalizacji elementu lub konkretnej kolejności przechodzenia.

### <a name="vector-differences"></a>Różnice między concurrent_vector i wektorem

Klasa `concurrent_vector` jest ściśle podobna do klasy `vector`. Złożoność operacji dołączania, dostępu do elementów i dostępu iteratora na obiekcie `concurrent_vector` jest taka sama jak dla obiektu `vector`. Poniższe punkty ilustrują, gdzie `concurrent_vector` różnić się od `vector`:

- Operacje dołączania, dostępu do elementów, dostępu iteratora i przechodzenia iteratora na obiekcie `concurrent_vector` są bezpieczne dla współbieżności.

- Elementy można dodawać tylko do końca obiektu `concurrent_vector`. Klasa `concurrent_vector` nie udostępnia metody `insert`.

- Obiekt `concurrent_vector` nie używa [semantyki przenoszenia](../../cpp/rvalue-reference-declarator-amp-amp.md) podczas dołączania do niego.

- Klasa `concurrent_vector` nie udostępnia metod `erase` lub `pop_back`. Podobnie jak w przypadku `vector`, użyj metody [Clear](reference/concurrent-vector-class.md#clear) , aby usunąć wszystkie elementy z obiektu `concurrent_vector`.

- Klasa `concurrent_vector` nie przechowuje swoich elementów w sposób ciągły w pamięci. W związku z tym nie można użyć klasy `concurrent_vector` we wszystkich sposobach użycia tablicy. Na przykład dla zmiennej o nazwie `v` typu `concurrent_vector`wyrażenie `&v[0]+2` generuje niezdefiniowane zachowanie.

- Klasa `concurrent_vector` definiuje metody [grow_by](reference/concurrent-vector-class.md#grow_by) i [grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least) . Metody te są podobne do metody [zmiany rozmiaru](reference/concurrent-vector-class.md#resize) , z tą różnicą, że są bezpieczne pod względem współbieżności.

- Obiekt `concurrent_vector` nie zmienia położenia jego elementów po dołączeniu do niego lub zmiany rozmiaru. Dzięki temu istniejące wskaźniki i Iteratory pozostają ważne podczas współbieżnych operacji.

- Środowisko uruchomieniowe nie definiuje wyspecjalizowanej wersji `concurrent_vector` dla typu `bool`.

### <a name="vector-safety"></a>Operacje dotyczące współbieżności

Wszystkie metody, które dołączają lub zwiększają rozmiar obiektu `concurrent_vector` lub uzyskują dostęp do elementu w obiekcie `concurrent_vector`, są bezpieczne dla współbieżności. W tym miejscu są zawsze ważne wskaźniki lub Iteratory, które są bezpieczne. Nie jest to gwarancja inicjalizacji elementu lub konkretnej kolejności przechodzenia. Wyjątkiem od tej reguły jest metoda `resize`.

W poniższej tabeli przedstawiono typowe metody `concurrent_vector` i operatory, które są bezpieczne pod kątem współbieżności.

||||
|-|-|-|
|[w](reference/concurrent-vector-class.md#at)|[punktów](reference/concurrent-vector-class.md#end)|[zakład&#91;&#93;](reference/concurrent-vector-class.md#operator_at)|
|[zaczną](reference/concurrent-vector-class.md#begin)|[FSB](reference/concurrent-vector-class.md#front)|[push_back](reference/concurrent-vector-class.md#push_back)|
|[Wstecz](reference/concurrent-vector-class.md#back)|[grow_by](reference/concurrent-vector-class.md#grow_by)|[rbegin](reference/concurrent-vector-class.md#rbegin)|
|[pojemności](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)|[rend](reference/concurrent-vector-class.md#rend)|
|[ciągiem](reference/concurrent-vector-class.md#empty)|[max_size](reference/concurrent-vector-class.md#max_size)|[zmienia](reference/concurrent-vector-class.md#size)|

Operacje wykonywane przez środowisko uruchomieniowe zapewniające zgodność C++ z biblioteką Standard, na przykład `reserve`, nie są bezpieczne pod względem współbieżności. W poniższej tabeli przedstawiono typowe metody i operatory, które nie są bezpieczne pod względem współbieżności.

|||
|-|-|
|[ponownie](reference/concurrent-vector-class.md#assign)|[zarezerwować](reference/concurrent-vector-class.md#reserve)|
|[Wyczyść](reference/concurrent-vector-class.md#clear)|[Zmień rozmiar](reference/concurrent-vector-class.md#resize)|
|[operator =](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit](reference/concurrent-vector-class.md#shrink_to_fit)|

Operacje modyfikujące wartość istniejących elementów nie są bezpieczne pod względem współbieżności. Użyj obiektu synchronizacji, takiego jak obiekt [reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) , aby synchronizować współbieżne operacje odczytu i zapisu do tego samego elementu danych. Aby uzyskać więcej informacji na temat obiektów synchronizacji, zobacz [struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md).

Podczas konwertowania istniejącego kodu, który używa `vector` do użycia `concurrent_vector`, współbieżne operacje mogą spowodować zmianę zachowania aplikacji. Rozważmy na przykład następujący program, który jednocześnie wykonuje dwa zadania na obiekcie `concurrent_vector`. Pierwsze zadanie dołącza dodatkowe elementy do `concurrent_vector` obiektu. Drugie zadanie oblicza sumę wszystkich elementów w tym samym obiekcie.

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

Chociaż metoda `end` jest bezpieczna współbieżność, współbieżne wywołanie metody [push_back](reference/concurrent-vector-class.md#push_back) powoduje zmianę wartości zwracanej przez `end`. Liczba elementów, których przechodzenie iteratora jest nieokreślony. W związku z tym program ten może generować różne wyniki przy każdym uruchomieniu. Gdy typ elementu jest nieuproszczony, możliwe jest istnienie warunku wyścigu między `push_back` i `end` wywołania. Metoda `end` może zwrócić element, który został przydzielony, ale nie został w pełni zainicjowany.

### <a name="vector-exceptions"></a>Bezpieczeństwo wyjątków

Jeśli operacja wzrostu lub przypisywania zgłosi wyjątek, stan obiektu `concurrent_vector` stanie się nieprawidłowy. Zachowanie obiektu `concurrent_vector`, który znajduje się w nieprawidłowym stanie, nie jest zdefiniowane, chyba że określono inaczej. Jednakże destruktor zawsze zwalnia pamięć przydzielaną przez obiekt, nawet jeśli obiekt jest w nieprawidłowym stanie.

Typ danych elementów wektora, `T`, musi spełniać poniższe wymagania. W przeciwnym razie zachowanie klasy `concurrent_vector` jest niezdefiniowane.

- Destruktor nie może zgłosić.

- Jeśli Konstruktor Default lub Copy zgłasza, destruktor nie może być zadeklarowany za pomocą słowa kluczowego `virtual` i musi działać poprawnie z pamięcią zainicjowaną przez zero.

[[Top](#top)]

## <a name="queue"></a>Klasa concurrent_queue

Klasa [concurrency:: concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) , podobnie jak Klasa [std:: Queue](../../standard-library/queue-class.md) , umożliwia dostęp do jej elementów przednich i back. Klasa `concurrent_queue` umożliwia wykonywanie operacji w kolejce i dekolejkowanie bezpiecznych współbieżności. W tym miejscu są zawsze ważne wskaźniki lub Iteratory, które są bezpieczne. Nie jest to gwarancja inicjalizacji elementu lub konkretnej kolejności przechodzenia. Klasa `concurrent_queue` zapewnia również obsługę iteratora, która nie jest bezpieczna pod kątem współbieżności.

### <a name="queue-differences"></a>Różnice między concurrent_queue i kolejką

Klasa `concurrent_queue` jest ściśle podobna do klasy `queue`. Poniższe punkty ilustrują, gdzie `concurrent_queue` różnić się od `queue`:

- Operacje na kolejce i Dequeue w obiekcie `concurrent_queue` są bezpieczne dla współbieżności.

- Klasa `concurrent_queue` zapewnia obsługę iteratora, która nie jest bezpieczna pod kątem współbieżności.

- Klasa `concurrent_queue` nie udostępnia metod `front` lub `pop`. Klasa `concurrent_queue` zastępuje te metody przez zdefiniowanie metody [try_pop](reference/concurrent-queue-class.md#try_pop) .

- Klasa `concurrent_queue` nie udostępnia metody `back`. W związku z tym nie można odwołać się do końca kolejki.

- Klasa `concurrent_queue` udostępnia metodę [unsafe_size](reference/concurrent-queue-class.md#unsafe_size) zamiast metody `size`. Metoda `unsafe_size` nie jest bezpieczna pod kątem współbieżności.

### <a name="queue-safety"></a>Operacje dotyczące współbieżności

Wszystkie metody, które znajdują się w kolejce lub Dequeue z obiektu `concurrent_queue` są bezpieczne dla współbieżności. W tym miejscu są zawsze ważne wskaźniki lub Iteratory, które są bezpieczne. Nie jest to gwarancja inicjalizacji elementu lub konkretnej kolejności przechodzenia.

W poniższej tabeli przedstawiono typowe metody `concurrent_queue` i operatory, które są bezpieczne pod kątem współbieżności.

|||
|-|-|
|[ciągiem](reference/concurrent-queue-class.md#empty)|[push](reference/concurrent-queue-class.md#push)|
|[get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|

Chociaż metoda `empty` jest bezpieczna pod kątem współbieżności, współbieżna operacja może spowodować powiększenie lub zmniejszenie kolejki przed zwróceniem metody `empty`.

W poniższej tabeli przedstawiono typowe metody i operatory, które nie są bezpieczne pod względem współbieżności.

|||
|-|-|
|[Wyczyść](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|

### <a name="queue-iterators"></a>Obsługa iteratora

`concurrent_queue` zawiera Iteratory, które nie są bezpieczne pod względem współbieżności. Zalecamy używanie tych iteratorów tylko do debugowania.

Iterator `concurrent_queue` przechodzą elementy tylko w kierunku do przodu. W poniższej tabeli przedstawiono operatory, które są obsługiwane przez każdy iterator.

|Operator|Opis|
|--------------|-----------------|
|`operator++`|Przechodzi do następnego elementu w kolejce. Ten operator jest przeciążony w celu zapewnienia semantyki wstępnej i przyrostowej.|
|`operator*`|Pobiera odwołanie do bieżącego elementu.|
|`operator->`|Pobiera wskaźnik do bieżącego elementu.|

[[Top](#top)]

## <a name="unordered_map"></a>Klasa concurrent_unordered_map

[Concurrency:: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) Klasa jest klasą kontenera asocjacyjnego, która podobnie jak Klasa [std:: unordered_map](../../standard-library/unordered-map-class.md) , kontroluje różnej długości sekwencje elementów typu [std::p Air\<klucz const, br >](../../standard-library/pair-structure.md). Zanotuj nieuporządkowaną mapę jako słownik, w którym można dodać parę klucz-wartość lub wyszukać wartość według klucza. Ta klasa jest przydatna w przypadku wielu wątków lub zadań, które muszą jednocześnie uzyskiwać dostęp do udostępnionego kontenera, wstawiać do niego lub aktualizować.

Poniższy przykład pokazuje podstawową strukturę przy użyciu `concurrent_unordered_map`. Ten przykład wstawia klucze znaków z zakresu ["a", "i"]. Ze względu na to, że kolejność operacji jest nieustalona, końcowa wartość dla każdego klucza również jest nieustalona. Można jednak bezpiecznie wykonać wstawienia równolegle.

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

Przykład, który używa `concurrent_unordered_map` do wykonywania mapy i zmniejszania operacji równolegle, można znaleźć [w temacie How to: wykonywanie map i zmniejszanie operacji równolegle](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

### <a name="map-differences"></a>Różnice między concurrent_unordered_map i unordered_map

Klasa `concurrent_unordered_map` jest ściśle podobna do klasy `unordered_map`. Poniższe punkty ilustrują, gdzie `concurrent_unordered_map` różnić się od `unordered_map`:

- Metody `erase`, `bucket`, `bucket_count`i `bucket_size` mają odpowiednio nazwę `unsafe_erase`, `unsafe_bucket`, `unsafe_bucket_count`i `unsafe_bucket_size`. Konwencja nazewnictwa `unsafe_` wskazuje, że te metody nie są bezpieczne pod względem współbieżności. Aby uzyskać więcej informacji na temat bezpieczeństwa współbieżności, zobacz [współbieżność wykonywania operacji](#map-safety).

- Operacje INSERT nie weryfikują istniejących wskaźników lub iteratorów ani nie zmieniają kolejności elementów, które już istnieją na mapie. Operacje INSERT i przechodzenie mogą odbywać się współbieżnie.

- `concurrent_unordered_map` obsługuje tylko iterację do przodu.

- Wstawienie nie unieważnia ani nie aktualizuje iteratorów zwracanych przez `equal_range`. Wstawianie może dołączyć nierówne elementy do końca zakresu. Iterator początkowy wskazuje równą pozycję.

Aby uniknąć zakleszczenia, żadna metoda `concurrent_unordered_map` nie utrzymuje blokady, gdy wywołuje program przydzielania pamięci, funkcję mieszania lub inny kod zdefiniowany przez użytkownika. Ponadto należy upewnić się, że funkcja skrótu zawsze oblicza równe klucze do tej samej wartości. Funkcja Najlepsza wartość skrótu dystrybuuje klucze jednolicie w przestrzeni kodu skrótu.

### <a name="map-safety"></a>Operacje dotyczące współbieżności

Klasa `concurrent_unordered_map` umożliwia bezpieczne współbieżność operacji wstawiania i dostępu do elementów. Operacje INSERT nie weryfikują istniejących wskaźników lub iteratorów. Operacje dostępu i przechodzenia iteratora są również bezpieczne dla współbieżności. W tym miejscu są zawsze ważne wskaźniki lub Iteratory, które są bezpieczne. Nie jest to gwarancja inicjalizacji elementu lub konkretnej kolejności przechodzenia. W poniższej tabeli przedstawiono najczęściej używane metody `concurrent_unordered_map` i operatory, które są bezpieczne pod kątem współbieżności.

|||||
|-|-|-|-|
|[w](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|
|`begin`|`empty`|`get_allocator`|`max_size`|
|`cbegin`|`end`|`hash_function`|[zakład&#91;&#93;](reference/concurrent-unordered-map-class.md#operator_at)|
|`cend`|`equal_range`|[wstawienia](reference/concurrent-unordered-map-class.md#insert)|`size`|

Mimo że metoda `count` może być wywoływana bezpiecznie z współbieżnie uruchomionych wątków, różne wątki mogą odbierać różne wyniki, jeśli nowa wartość jest jednocześnie wstawiana do kontenera.

W poniższej tabeli przedstawiono najczęściej używane metody i operatory, które nie są bezpieczne dla współbieżności.

||||
|-|-|-|
|`clear`|`max_load_factor`|`rehash`|
|`load_factor`|[operator =](reference/concurrent-unordered-map-class.md#operator_eq)

Oprócz tych metod jakakolwiek metoda, która rozpoczyna się od `unsafe_`, również nie jest bezpieczna pod kątem współbieżności.

[[Top](#top)]

## <a name="unordered_multimap"></a>Klasa concurrent_unordered_multimap

Klasa [concurrency:: concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) ściśle przypomina klasę `concurrent_unordered_map`, z tą różnicą, że umożliwia mapowanie wielu wartości na ten sam klucz. Różni się to również od `concurrent_unordered_map` w następujący sposób:

- Metoda [concurrent_unordered_multimap:: INSERT](reference/concurrent-unordered-multimap-class.md#insert) zwraca iterator, a nie `std::pair<iterator, bool>`.

- Klasa `concurrent_unordered_multimap` nie zapewnia `operator[]` ani metody `at`.

Poniższy przykład pokazuje podstawową strukturę przy użyciu `concurrent_unordered_multimap`. Ten przykład wstawia klucze znaków z zakresu ["a", "i"]. `concurrent_unordered_multimap` umożliwia kluczowi posiadanie wielu wartości.

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

[[Top](#top)]

## <a name="unordered_set"></a>Klasa concurrent_unordered_set

Klasa [concurrency:: concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md) ściśle przypomina klasę `concurrent_unordered_map`, z tą różnicą, że zarządza wartościami zamiast par klucz-wartość. Klasa `concurrent_unordered_set` nie zapewnia `operator[]` ani metody `at`.

Poniższy przykład pokazuje podstawową strukturę przy użyciu `concurrent_unordered_set`. Ten przykład wstawia wartości znakowe z zakresu ["a", "i"]. Wykonywanie operacji wstawiania równolegle jest bezpieczne.

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

[[Top](#top)]

## <a name="unordered_multiset"></a>Klasa concurrent_unordered_multiset

Klasa [concurrency:: concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) ściśle przypomina klasę `concurrent_unordered_set`, z tą różnicą, że umożliwia duplikowanie wartości. Różni się to również od `concurrent_unordered_set` w następujący sposób:

- Metoda [concurrent_unordered_multiset:: INSERT](reference/concurrent-unordered-multiset-class.md#insert) zwraca iterator, a nie `std::pair<iterator, bool>`.

- Klasa `concurrent_unordered_multiset` nie zapewnia `operator[]` ani metody `at`.

Poniższy przykład pokazuje podstawową strukturę przy użyciu `concurrent_unordered_multiset`. Ten przykład wstawia wartości znakowe z zakresu ["a", "i"]. `concurrent_unordered_multiset` włącza wartość wiele razy.

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

[[Top](#top)]

## <a name="combinable"></a>Klasa z kombinacją

Klasa [concurrency::](../../parallel/concrt/reference/combinable-class.md) Scaled umożliwia wielokrotne użycie magazynu wątków lokalnych, który umożliwia wykonywanie szczegółowych obliczeń, a następnie scalanie tych obliczeń w końcowym wyniku. Obiekt `combinable` można traktować jako zmienną redukcji.

Klasa `combinable` jest przydatna w przypadku zasobu, który jest współużytkowany przez kilka wątków lub zadań. Klasa `combinable` pomaga wyeliminować współużytkowany stan, zapewniając dostęp do udostępnionych zasobów w sposób niezależny od blokady. W związku z tym Klasa ta zapewnia alternatywę dla korzystania z mechanizmu synchronizacji, na przykład obiektu mutex, do synchronizowania dostępu do udostępnionych danych z wielu wątków.

### <a name="combinable-features"></a>Metody i funkcje

W poniższej tabeli przedstawiono niektóre ważne metody klasy `combinable`. Aby uzyskać więcej informacji na temat wszystkich metod klasy `combinable`, zobacz [Klasa z kombinacją](../../parallel/concrt/reference/combinable-class.md).

|Metoda|Opis|
|------------|-----------------|
|[local](reference/combinable-class.md#local)|Pobiera odwołanie do zmiennej lokalnej, która jest skojarzona z bieżącym kontekstem wątku.|
|[Wyczyść](reference/combinable-class.md#clear)|Usuwa wszystkie zmienne lokalne wątku z obiektu `combinable`.|
|[żądany](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|Używa podanej funkcji Połącz w celu wygenerowania końcowej wartości z zestawu wszystkich obliczeń lokalnych wątków.|

Klasa `combinable` jest klasą szablonu, która jest sparametryzowane na końcowym scalonym wyniku. Jeśli wywołasz konstruktora domyślnego, typ parametru szablonu `T` musi mieć konstruktora domyślnego i konstruktora kopiującego. Jeśli typ parametru szablonu `T` nie ma domyślnego konstruktora, wywołaj przeciążoną wersję konstruktora, która przyjmuje funkcję inicjującą jako parametr.

Po wywołaniu metody [łączenia](reference/combinable-class.md#combine) lub [combine_each](reference/combinable-class.md#combine_each) można przechowywać dodatkowe dane w obiekcie `combinable`. Można również wielokrotnie wywołać `combine` i `combine_each` metod. Jeśli żadna wartość lokalna w obiekcie `combinable` nie ulegnie zmianie, metody `combine` i `combine_each` dają ten sam wynik przy każdym wywołaniu.

### <a name="combinable-examples"></a>Pokazują

Aby zapoznać się z przykładami dotyczącymi używania klasy `combinable`, zobacz następujące tematy:

- [Instrukcje: korzystanie z wyników połączonych do poprawiania wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [Instrukcje: korzystanie z wyników połączonych w celu łączenia zestawów](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

[[Top](#top)]

## <a name="related-topics"></a>Tematy pokrewne

[Instrukcje: korzystanie z kontenerów równoległych do zwiększania wydajności](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
Pokazuje, jak używać kontenerów równoległych do wydajnego przechowywania i uzyskiwania dostępu do danych.

[Instrukcje: korzystanie z wyników połączonych do poprawiania wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
Pokazuje, w jaki sposób używać klasy `combinable`, aby wyeliminować współużytkowany stan, a tym samym zwiększyć wydajność.

[Instrukcje: korzystanie z wyników połączonych w celu łączenia zestawów](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
Pokazuje, jak używać funkcji `combine` do scalania lokalnych zestawów danych wątku.

[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
Opisuje PPL, który zapewnia bezwzględny model programistyczny, który promuje skalowalność i łatwość używania do tworzenia współbieżnych aplikacji.

## <a name="reference"></a>Dokumentacja

[concurrent_vector, klasa](../../parallel/concrt/reference/concurrent-vector-class.md)

[concurrent_queue, klasa](../../parallel/concrt/reference/concurrent-queue-class.md)

[concurrent_unordered_map, klasa](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[concurrent_unordered_multimap, klasa](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[concurrent_unordered_set, klasa](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[concurrent_unordered_multiset, klasa](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[combinable, klasa](../../parallel/concrt/reference/combinable-class.md)
