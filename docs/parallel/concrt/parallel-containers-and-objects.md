---
title: Równoległe kontenery oraz obiekty
ms.date: 03/27/2019
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
ms.openlocfilehash: 7387173378e79a4707008a11846eab19d7ae4341
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831791"
---
# <a name="parallel-containers-and-objects"></a>Równoległe kontenery oraz obiekty

Biblioteka równoległych wzorców (PPL) zawiera kilka kontenerów i obiektów, które zapewniają bezpieczny wątkowy dostęp do ich elementów.

*Współbieżny kontener* zapewnia bezpieczny dostęp współbieżności do najważniejszych operacji. W tym miejscu są zawsze ważne wskaźniki lub Iteratory, które są bezpieczne. Nie jest to gwarancja inicjalizacji elementu lub konkretnej kolejności przechodzenia. Funkcje tych kontenerów są podobne do tych, które są dostarczane przez standardową bibliotekę języka C++. Na przykład Klasa [concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) jest podobna do klasy [std:: Vector](../../standard-library/vector-class.md) , z tą różnicą, że `concurrent_vector` Klasa umożliwia równoczesne Dołączanie elementów. Używaj współbieżnych kontenerów w przypadku równoległego kodu, który wymaga dostępu do odczytu i zapisu do tego samego kontenera.

*Obiekt współbieżny* jest udostępniany jednocześnie między składnikami. Proces, który oblicza stan współbieżnego obiektu równolegle, daje ten sam wynik, co inny proces, który obliczy ten sam stan szeregowo. Klasa [concurrency:: kombinowane](../../parallel/concrt/reference/combinable-class.md) jest jednym z przykładowych typów obiektów współbieżnych. `combinable`Klasa umożliwia wykonywanie obliczeń równolegle, a następnie łączenie tych obliczeń w końcowy wynik. Używaj współbieżnych obiektów, gdy w inny sposób użyjesz mechanizmu synchronizacji, na przykład, elementu mutex, aby synchronizować dostęp do udostępnionej zmiennej lub zasobu.

## <a name="sections"></a><a name="top"></a> Poszczególne

W tym temacie opisano szczegóły następujących kontenerów równoległych i obiektów.

Kontenery współbieżne:

- [Klasa concurrent_vector](#vector)

  - [Różnice między concurrent_vector i wektorem](#vector-differences)

  - [Operacje dotyczące współbieżności](#vector-safety)

  - [Bezpieczeństwo wyjątków](#vector-exceptions)

- [Klasa concurrent_queue](#queue)

  - [Różnice między concurrent_queue i kolejką](#queue-differences)

  - [Operacje dotyczące współbieżności](#queue-safety)

  - [Obsługa iteratora](#queue-iterators)

- [Klasa concurrent_unordered_map](#unordered_map)

  - [Różnice między concurrent_unordered_map i unordered_map](#map-differences)

  - [Operacje dotyczące współbieżności](#map-safety)

- [Klasa concurrent_unordered_multimap](#unordered_multimap)

- [Klasa concurrent_unordered_set](#unordered_set)

- [Klasa concurrent_unordered_multiset](#unordered_multiset)

Obiekty współbieżne:

- [Klasa z kombinacją](#combinable)

  - [Metody i funkcje](#combinable-features)

  - [Przykłady](#combinable-examples)

## <a name="concurrent_vector-class"></a><a name="vector"></a> Klasa concurrent_vector

[Concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) Klasa jest klasą kontenera sekwencji, która podobnie jak Klasa [Vector:: wektor](../../standard-library/vector-class.md) , umożliwia losowo dostęp do jej elementów. `concurrent_vector`Klasa umożliwia bezpieczne wykonywanie operacji dołączania i dostępu do elementów. Operacje dołączania nie weryfikują istniejących wskaźników lub iteratorów. Operacje dostępu i przechodzenia iteratora są również bezpieczne dla współbieżności. W tym miejscu są zawsze ważne wskaźniki lub Iteratory, które są bezpieczne. Nie jest to gwarancja inicjalizacji elementu lub konkretnej kolejności przechodzenia.

### <a name="differences-between-concurrent_vector-and-vector"></a><a name="vector-differences"></a> Różnice między concurrent_vector i wektorem

`concurrent_vector`Klasa jest ściśle podobna do `vector` klasy. Złożoność operacji dołączania, dostępu do elementów i dostępu iteratora na `concurrent_vector` obiekcie jest taka sama jak w przypadku `vector` obiektu. Poniższe punkty ilustrują, gdzie `concurrent_vector` różnią się od `vector` :

- Operacje dołączania, dostępu do elementów, dostępu iteratora i przechodzenia iteratora do `concurrent_vector` obiektu są bezpieczne dla współbieżności.

- Elementy można dodawać tylko do końca `concurrent_vector` obiektu. `concurrent_vector`Klasa nie dostarcza `insert` metody.

- `concurrent_vector`Obiekt nie używa [semantyki przenoszenia](../../cpp/rvalue-reference-declarator-amp-amp.md) podczas dołączania do niego.

- `concurrent_vector`Klasa nie udostępnia `erase` `pop_back` metod lub. Podobnie jak w przypadku programu `vector` , należy użyć metody [Clear](reference/concurrent-vector-class.md#clear) , aby usunąć wszystkie elementy z `concurrent_vector` obiektu.

- `concurrent_vector`Klasa nie przechowuje swoich elementów w sposób ciągły w pamięci. W związku z tym nie można użyć `concurrent_vector` klasy we wszystkich sposobach, w których można użyć tablicy. Na przykład dla zmiennej o nazwie `v` typu `concurrent_vector` wyrażenie `&v[0]+2` generuje niezdefiniowane zachowanie.

- `concurrent_vector`Klasa definiuje metody [grow_by](reference/concurrent-vector-class.md#grow_by) i [grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least) . Metody te są podobne do metody [zmiany rozmiaru](reference/concurrent-vector-class.md#resize) , z tą różnicą, że są bezpieczne pod względem współbieżności.

- `concurrent_vector`Obiekt nie zmienia położenia jego elementów po dołączeniu do niego lub zmiany jego rozmiaru. Dzięki temu istniejące wskaźniki i Iteratory pozostają ważne podczas współbieżnych operacji.

- Środowisko uruchomieniowe nie definiuje wyspecjalizowanej wersji programu `concurrent_vector` dla typu **`bool`** .

### <a name="concurrency-safe-operations"></a><a name="vector-safety"></a> Operacje dotyczące współbieżności

Wszystkie metody, które dołączają lub zwiększają rozmiar `concurrent_vector` obiektu lub uzyskują dostęp do elementu w `concurrent_vector` obiekcie, są bezpieczne dla współbieżności. W tym miejscu są zawsze ważne wskaźniki lub Iteratory, które są bezpieczne. Nie jest to gwarancja inicjalizacji elementu lub konkretnej kolejności przechodzenia. Wyjątkiem od tej reguły jest `resize` Metoda.

W poniższej tabeli przedstawiono typowe `concurrent_vector` metody i operatory, które są bezpieczne pod względem współbieżności.

:::row:::
   :::column span="":::
      [`at`](reference/concurrent-vector-class.md#at)\
      [`back`](reference/concurrent-vector-class.md#back)\
      [`begin`](reference/concurrent-vector-class.md#begin)\
      [`capacity`](reference/concurrent-vector-class.md#capacity)
   :::column-end:::
   :::column span="":::
      [`empty`](reference/concurrent-vector-class.md#empty)\
      [`end`](reference/concurrent-vector-class.md#end)\
      [`front`](reference/concurrent-vector-class.md#front)\
      [`grow_by`](reference/concurrent-vector-class.md#grow_by)
   :::column-end:::
   :::column span="":::
      [`grow_to_at_least`](reference/concurrent-vector-class.md#grow_to_at_least)\
      [`max_size`](reference/concurrent-vector-class.md#max_size)\
      [`operator[]`](reference/concurrent-vector-class.md#operator_at)\
      [`push_back`](reference/concurrent-vector-class.md#push_back)
   :::column-end:::
   :::column span="":::
      [`rbegin`](reference/concurrent-vector-class.md#rbegin)\
      [`rend`](reference/concurrent-vector-class.md#rend)\
      [`size`](reference/concurrent-vector-class.md#size)
   :::column-end:::
:::row-end:::

Operacje wykonywane przez środowisko uruchomieniowe zapewniające zgodność z biblioteką standardową języka C++, na przykład, `reserve` nie są bezpieczne pod względem współbieżności. W poniższej tabeli przedstawiono typowe metody i operatory, które nie są bezpieczne pod względem współbieżności.

:::row:::
   :::column span="":::
      [`assign`](reference/concurrent-vector-class.md#assign)\
      [`clear`](reference/concurrent-vector-class.md#clear)
   :::column-end:::
   :::column span="":::
      [`operator=`](reference/concurrent-vector-class.md#operator_eq)\
      [`reserve`](reference/concurrent-vector-class.md#reserve)
   :::column-end:::
   :::column span="":::
      [`resize`](reference/concurrent-vector-class.md#resize)
   :::column-end:::
   :::column span="":::
      [`shrink_to_fit`](reference/concurrent-vector-class.md#shrink_to_fit)
   :::column-end:::
:::row-end:::

Operacje modyfikujące wartość istniejących elementów nie są bezpieczne pod względem współbieżności. Użyj obiektu synchronizacji, takiego jak obiekt [reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) , aby synchronizować współbieżne operacje odczytu i zapisu do tego samego elementu danych. Aby uzyskać więcej informacji na temat obiektów synchronizacji, zobacz [struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md).

Podczas konwersji istniejącego kodu, który używa `vector` do użycia `concurrent_vector` , współbieżne operacje mogą spowodować zmianę działania aplikacji. Rozważmy na przykład następujący program, który jednocześnie wykonuje dwa zadania na `concurrent_vector` obiekcie. Pierwsze zadanie dołącza dodatkowe elementy do `concurrent_vector` obiektu. Drugie zadanie oblicza sumę wszystkich elementów w tym samym obiekcie.

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

Chociaż `end` Metoda jest bezpieczna współbieżność, współbieżne wywołanie metody [push_back](reference/concurrent-vector-class.md#push_back) powoduje zmianę wartości zwracanej przez `end` . Liczba elementów, których przechodzenie iteratora jest nieokreślony. W związku z tym program ten może generować różne wyniki przy każdym uruchomieniu. Gdy typ elementu jest nieuproszczony, możliwe jest istnienie warunku wyścigu między `push_back` i `end` . `end`Metoda może zwrócić element, który został przydzielony, ale nie został w pełni zainicjowany.

### <a name="exception-safety"></a><a name="vector-exceptions"></a> Bezpieczeństwo wyjątków

Jeśli operacja wzrostu lub przypisywania zgłasza wyjątek, stan `concurrent_vector` obiektu stanie się nieprawidłowy. Zachowanie `concurrent_vector` obiektu znajdującego się w nieprawidłowym stanie jest niezdefiniowane, chyba że określono inaczej. Jednakże destruktor zawsze zwalnia pamięć przydzielaną przez obiekt, nawet jeśli obiekt jest w nieprawidłowym stanie.

Typ danych elementów wektora, `T` musi spełniać poniższe wymagania. W przeciwnym razie zachowanie `concurrent_vector` klasy jest niezdefiniowane.

- Destruktor nie może zgłosić.

- Jeśli Konstruktor Default lub Copy zgłasza, destruktor nie może być zadeklarowany za pomocą **`virtual`** słowa kluczowego i musi działać poprawnie z pamięcią zainicjowaną przez zero.

[[Top](#top)]

## <a name="concurrent_queue-class"></a><a name="queue"></a> Klasa concurrent_queue

Klasa [concurrency:: concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) , podobnie jak Klasa [std:: Queue](../../standard-library/queue-class.md) , umożliwia dostęp do jej elementów przednich i back. `concurrent_queue`Klasa umożliwia wykonywanie operacji w kolejce i dekolejkach bezpiecznych dla współbieżności. W tym miejscu są zawsze ważne wskaźniki lub Iteratory, które są bezpieczne. Nie jest to gwarancja inicjalizacji elementu lub konkretnej kolejności przechodzenia. `concurrent_queue`Klasa zapewnia również obsługę iteratora, która nie jest bezpieczna pod kątem współbieżności.

### <a name="differences-between-concurrent_queue-and-queue"></a><a name="queue-differences"></a> Różnice między concurrent_queue i kolejką

`concurrent_queue`Klasa jest ściśle podobna do `queue` klasy. Poniższe punkty ilustrują, gdzie `concurrent_queue` różnią się od `queue` :

- Operacje na kolejce i dequeuee na `concurrent_queue` obiekcie są bezpieczne dla współbieżności.

- `concurrent_queue`Klasa zapewnia obsługę iteratora, która nie jest bezpieczna pod kątem współbieżności.

- `concurrent_queue`Klasa nie udostępnia `front` `pop` metod lub. `concurrent_queue`Klasa zastępuje te metody, definiując metodę [try_pop](reference/concurrent-queue-class.md#try_pop) .

- `concurrent_queue`Klasa nie dostarcza `back` metody. W związku z tym nie można odwołać się do końca kolejki.

- `concurrent_queue`Klasa udostępnia metodę [unsafe_size](reference/concurrent-queue-class.md#unsafe_size) zamiast `size` metody. `unsafe_size`Metoda nie jest bezpieczna pod kątem współbieżności.

### <a name="concurrency-safe-operations"></a><a name="queue-safety"></a> Operacje dotyczące współbieżności

Wszystkie metody, które znajdują się w kolejce lub Dequeue z `concurrent_queue` obiektu, są bezpieczne dla współbieżności. W tym miejscu są zawsze ważne wskaźniki lub Iteratory, które są bezpieczne. Nie jest to gwarancja inicjalizacji elementu lub konkretnej kolejności przechodzenia.

W poniższej tabeli przedstawiono typowe `concurrent_queue` metody i operatory, które są bezpieczne pod względem współbieżności.

:::row:::
   :::column span="":::
      [`empty`](reference/concurrent-queue-class.md#empty)
   :::column-end:::
   :::column span="":::
      [`get_allocator`](reference/concurrent-queue-class.md#get_allocator)
   :::column-end:::
   :::column span="":::
      [`push`](reference/concurrent-queue-class.md#push)
   :::column-end:::
   :::column span="":::
      [`try_pop`](reference/concurrent-queue-class.md#try_pop)
   :::column-end:::
:::row-end:::

Chociaż `empty` Metoda jest bezpieczna współbieżność, współbieżna operacja może spowodować powiększenie lub zmniejszenie kolejki przed `empty` zwróceniem metody.

W poniższej tabeli przedstawiono typowe metody i operatory, które nie są bezpieczne pod względem współbieżności.

:::row:::
   :::column span="":::
      [`clear`](reference/concurrent-queue-class.md#clear)
   :::column-end:::
   :::column span="":::
      [`unsafe_begin`](reference/concurrent-queue-class.md#unsafe_begin)
   :::column-end:::
   :::column span="":::
      [`unsafe_end`](reference/concurrent-queue-class.md#unsafe_end)
   :::column-end:::
   :::column span="":::
      [`unsafe_size`](reference/concurrent-queue-class.md#unsafe_size)
   :::column-end:::
:::row-end:::

### <a name="iterator-support"></a><a name="queue-iterators"></a> Obsługa iteratora

`concurrent_queue`Zawiera Iteratory, które nie są bezpieczne pod kątem współbieżności. Zalecamy używanie tych iteratorów tylko do debugowania.

`concurrent_queue`Iterator przechodzą elementy tylko w kierunku do przodu. W poniższej tabeli przedstawiono operatory, które są obsługiwane przez każdy iterator.

|Operator|Opis|
|--------------|-----------------|
|`operator++`|Przechodzi do następnego elementu w kolejce. Ten operator jest przeciążony w celu zapewnienia semantyki wstępnej i przyrostowej.|
|`operator*`|Pobiera odwołanie do bieżącego elementu.|
|`operator->`|Pobiera wskaźnik do bieżącego elementu.|

\[[Góra](#top)]

## <a name="concurrent_unordered_map-class"></a><a name="unordered_map"></a> Klasa concurrent_unordered_map

[Concurrency:: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) Klasa jest klasą kontenera asocjacyjnego, która podobnie jak Klasa [std:: unordered_map](../../standard-library/unordered-map-class.md) , kontroluje różnej długości sekwencje elementów typu [std::p powietrze \<const Key, Ty> ](../../standard-library/pair-structure.md). Zanotuj nieuporządkowaną mapę jako słownik, w którym można dodać parę klucz-wartość lub wyszukać wartość według klucza. Ta klasa jest przydatna w przypadku wielu wątków lub zadań, które muszą jednocześnie uzyskiwać dostęp do udostępnionego kontenera, wstawiać do niego lub aktualizować.

Poniższy przykład pokazuje podstawową strukturę przy użyciu `concurrent_unordered_map` . Ten przykład wstawia klucze znaków z zakresu ["a", "i"]. Ze względu na to, że kolejność operacji jest nieustalona, końcowa wartość dla każdego klucza również jest nieustalona. Można jednak bezpiecznie wykonać wstawienia równolegle.

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

Przykład, który używa `concurrent_unordered_map` do wykonywania mapy i zmniejszania operacji równolegle, można znaleźć [w temacie How to: wykonywanie map i zmniejszanie operacji równolegle](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

### <a name="differences-between-concurrent_unordered_map-and-unordered_map"></a><a name="map-differences"></a> Różnice między concurrent_unordered_map i unordered_map

`concurrent_unordered_map`Klasa jest ściśle podobna do `unordered_map` klasy. Poniższe punkty ilustrują, gdzie `concurrent_unordered_map` różnią się od `unordered_map` :

- `erase`Metody, `bucket` , `bucket_count` i `bucket_size` są `unsafe_erase` odpowiednio nazwane,,, `unsafe_bucket` `unsafe_bucket_count` i `unsafe_bucket_size` . `unsafe_`Konwencja nazewnictwa wskazuje, że te metody nie są bezpieczne pod względem współbieżności. Aby uzyskać więcej informacji na temat bezpieczeństwa współbieżności, zobacz [współbieżność wykonywania operacji](#map-safety).

- Operacje INSERT nie weryfikują istniejących wskaźników lub iteratorów ani nie zmieniają kolejności elementów, które już istnieją na mapie. Operacje INSERT i przechodzenie mogą odbywać się współbieżnie.

- `concurrent_unordered_map` obsługuje tylko iterację do przodu.

- Wstawienie nie unieważnia ani nie aktualizuje iteratorów, które są zwracane przez `equal_range` . Wstawianie może dołączyć nierówne elementy do końca zakresu. Iterator początkowy wskazuje równą pozycję.

Aby uniknąć zakleszczenia, żadna metoda nie `concurrent_unordered_map` jest blokowana w przypadku wywołania programu przydzielania pamięci, funkcji mieszania lub innego kodu zdefiniowanego przez użytkownika. Ponadto należy upewnić się, że funkcja skrótu zawsze oblicza równe klucze do tej samej wartości. Funkcja Najlepsza wartość skrótu dystrybuuje klucze jednolicie w przestrzeni kodu skrótu.

### <a name="concurrency-safe-operations"></a><a name="map-safety"></a> Operacje dotyczące współbieżności

`concurrent_unordered_map`Klasa umożliwia bezpieczne wykonywanie operacji wstawiania i dostępu do elementów. Operacje INSERT nie weryfikują istniejących wskaźników lub iteratorów. Operacje dostępu i przechodzenia iteratora są również bezpieczne dla współbieżności. W tym miejscu są zawsze ważne wskaźniki lub Iteratory, które są bezpieczne. Nie jest to gwarancja inicjalizacji elementu lub konkretnej kolejności przechodzenia. W poniższej tabeli przedstawiono najczęściej używane `concurrent_unordered_map` metody i operatory, które są bezpieczne pod względem współbieżności.

:::row:::
   :::column span="":::
      [`at`](reference/concurrent-unordered-map-class.md#at)\
      [`begin`](reference/concurrent-unordered-map-class.md#begin)\
      [`cbegin`](reference/concurrent-unordered-map-class.md#cbegin)\
      [`cend`](reference/concurrent-unordered-map-class.md#cend)
   :::column-end:::
   :::column span="":::
      [`count`](reference/concurrent-unordered-map-class.md#count)\
      [`empty`](reference/concurrent-unordered-map-class.md#empty)\
      [`end`](reference/concurrent-unordered-map-class.md#cend)\
      [`equal_range`](reference/concurrent-unordered-map-class.md#equal_range)
   :::column-end:::
   :::column span="":::
      [`find`](reference/concurrent-unordered-map-class.md#find)\
      [`get_allocator`](reference/concurrent-unordered-map-class.md#get_allocator)\
      [`hash_function`](reference/concurrent-unordered-map-class.md#hash_function)\
      [`insert`](reference/concurrent-unordered-map-class.md#insert)
   :::column-end:::
   :::column span="":::
      [`key_eq`](reference/concurrent-unordered-map-class.md#key_eq)\
      [`max_size`](reference/concurrent-unordered-map-class.md#max_size)\
      [`operator[]`](./reference/concurrent-unordered-map-class.md#operator_at)\
      [`size`](reference/concurrent-unordered-map-class.md#size)
   :::column-end:::
:::row-end:::

Chociaż `count` Metoda może być wywoływana bezpiecznie z współbieżnie uruchomionych wątków, różne wątki mogą odbierać różne wyniki, jeśli nowa wartość jest jednocześnie wstawiana do kontenera.

W poniższej tabeli przedstawiono najczęściej używane metody i operatory, które nie są bezpieczne dla współbieżności.

:::row:::
   :::column span="":::
      [`clear`](reference/concurrent-unordered-map-class.md#clear)\
      [`load_factor`](reference/concurrent-unordered-map-class.md#load_factor)
   :::column-end:::
   :::column span="":::
      [`max_load_factor`](reference/concurrent-unordered-map-class.md#max_load_factor)
   :::column-end:::
   :::column span="":::
      [`operator=`](reference/concurrent-unordered-map-class.md#operator_eq)
   :::column-end:::
   :::column span="":::
      [`rehash`](reference/concurrent-unordered-map-class.md#rehash)
   :::column-end:::
:::row-end:::

Oprócz tych metod jakakolwiek metoda, która zaczyna się od, `unsafe_` również nie jest bezpieczna pod kątem współbieżności.

[[Top](#top)]

## <a name="concurrent_unordered_multimap-class"></a><a name="unordered_multimap"></a> Klasa concurrent_unordered_multimap

Klasa [concurrency:: concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) ściśle przypomina `concurrent_unordered_map` klasę, z tą różnicą, że umożliwia mapowanie wielu wartości na ten sam klucz. Różni się to również od `concurrent_unordered_map` następujących sposobów:

- Metoda [concurrent_unordered_multimap:: INSERT](reference/concurrent-unordered-multimap-class.md#insert) zwraca iterator zamiast `std::pair<iterator, bool>` .

- `concurrent_unordered_multimap`Klasa nie oferuje ani nie `operator[]` ma `at` metody.

Poniższy przykład pokazuje podstawową strukturę przy użyciu `concurrent_unordered_multimap` . Ten przykład wstawia klucze znaków z zakresu ["a", "i"]. `concurrent_unordered_multimap` Włącza klucz, aby miał wiele wartości.

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

[[Top](#top)]

## <a name="concurrent_unordered_set-class"></a><a name="unordered_set"></a> Klasa concurrent_unordered_set

Klasa [concurrency:: concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md) ściśle przypomina `concurrent_unordered_map` klasę, z tą różnicą, że zarządza wartościami zamiast par klucz-wartość. `concurrent_unordered_set`Klasa nie oferuje ani nie `operator[]` ma `at` metody.

Poniższy przykład pokazuje podstawową strukturę przy użyciu `concurrent_unordered_set` . Ten przykład wstawia wartości znakowe z zakresu ["a", "i"]. Wykonywanie operacji wstawiania równolegle jest bezpieczne.

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

[[Top](#top)]

## <a name="concurrent_unordered_multiset-class"></a><a name="unordered_multiset"></a> Klasa concurrent_unordered_multiset

Klasa [concurrency:: concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) ściśle przypomina `concurrent_unordered_set` klasę, z tą różnicą, że umożliwia duplikowanie wartości. Różni się to również od `concurrent_unordered_set` następujących sposobów:

- Metoda [concurrent_unordered_multiset:: INSERT](reference/concurrent-unordered-multiset-class.md#insert) zwraca iterator zamiast `std::pair<iterator, bool>` .

- `concurrent_unordered_multiset`Klasa nie oferuje ani nie `operator[]` ma `at` metody.

Poniższy przykład pokazuje podstawową strukturę przy użyciu `concurrent_unordered_multiset` . Ten przykład wstawia wartości znakowe z zakresu ["a", "i"]. `concurrent_unordered_multiset` Włącza wartość wiele razy.

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

[[Top](#top)]

## <a name="combinable-class"></a><a name="combinable"></a> Klasa z kombinacją

Klasa [concurrency::](../../parallel/concrt/reference/combinable-class.md) Scaled umożliwia wielokrotne użycie magazynu wątków lokalnych, który umożliwia wykonywanie szczegółowych obliczeń, a następnie scalanie tych obliczeń w końcowym wyniku. Obiekt można traktować `combinable` jako zmienną redukcji.

`combinable`Klasa jest przydatna w przypadku zasobu, który jest współużytkowany przez kilka wątków lub zadań. `combinable`Klasa pomaga wyeliminować współużytkowany stan, zapewniając dostęp do udostępnionych zasobów w sposób niezależny od blokady. W związku z tym Klasa ta zapewnia alternatywę dla korzystania z mechanizmu synchronizacji, na przykład obiektu mutex, do synchronizowania dostępu do udostępnionych danych z wielu wątków.

### <a name="methods-and-features"></a><a name="combinable-features"></a> Metody i funkcje

W poniższej tabeli przedstawiono niektóre ważne metody `combinable` klasy. Aby uzyskać więcej informacji na temat wszystkich `combinable` metod klasy, zobacz [Klasa z kombinacją](../../parallel/concrt/reference/combinable-class.md).

|Metoda|Opis|
|------------|-----------------|
|[LAN](reference/combinable-class.md#local)|Pobiera odwołanie do zmiennej lokalnej, która jest skojarzona z bieżącym kontekstem wątku.|
|[Wyczyść](reference/combinable-class.md#clear)|Usuwa wszystkie zmienne lokalne wątku z `combinable` obiektu.|
|[combine](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|Używa podanej funkcji Połącz w celu wygenerowania końcowej wartości z zestawu wszystkich obliczeń lokalnych wątków.|

`combinable`Klasa jest klasą szablonu, która jest sparametryzowane na końcowym scalonym wyniku. Jeśli wywołasz konstruktora domyślnego, `T` Typ parametru szablonu musi mieć konstruktora domyślnego i konstruktora kopiującego. Jeśli `T` Typ parametru szablonu nie ma domyślnego konstruktora, wywołaj przeciążoną wersję konstruktora, który przyjmuje funkcję inicjującą jako parametr.

`combinable`Po wywołaniu metody [łączenia](reference/combinable-class.md#combine) lub [combine_each](reference/combinable-class.md#combine_each) można przechowywać dodatkowe dane w obiekcie. Można również wielokrotnie wywołać `combine` metody i `combine_each` . Jeśli żadna wartość lokalna w `combinable` obiekcie nie ulegnie zmianie, `combine` `combine_each` metody i dają ten sam wynik przy każdym wywołaniu.

### <a name="examples"></a><a name="combinable-examples"></a> Pokazują

Aby zapoznać się z przykładami dotyczącymi używania `combinable` klasy, zobacz następujące tematy:

- [Instrukcje: używanie kombinacji w celu poprawy wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [Instrukcje: używanie kombinacji do łączenia zestawów](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

[[Top](#top)]

## <a name="related-topics"></a>Tematy pokrewne

[Instrukcje: korzystanie z kontenerów równoległych w celu zwiększenia wydajności](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
Pokazuje, jak używać kontenerów równoległych do wydajnego przechowywania i uzyskiwania dostępu do danych.

[Instrukcje: używanie kombinacji w celu poprawy wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
Pokazuje, w jaki sposób używać `combinable` klasy w celu wyeliminowania stanu udostępnionego, a tym samym zwiększenia wydajności.

[Instrukcje: używanie kombinacji do łączenia zestawów](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
Pokazuje, jak używać `combine` funkcji do scalania lokalnych zestawów danych wątku.

[Biblioteka równoległych wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
Opisuje PPL, który zapewnia bezwzględny model programistyczny, który promuje skalowalność i łatwość używania do tworzenia współbieżnych aplikacji.

## <a name="reference"></a>Dokumentacja

[Klasa concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)

[Klasa concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)

[Klasa concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[Klasa concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[Klasa concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[Klasa concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[Klasa z kombinacją](../../parallel/concrt/reference/combinable-class.md)
