---
title: Algorytmy równoległe
ms.date: 11/19/2018
helpviewer_keywords:
- parallel algorithms [Concurrency Runtime]
ms.assetid: 045dca7b-4d73-4558-a44c-383b88a28473
ms.openlocfilehash: c2d41ccdb8d70095f00cd18508fdff2b78392696
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631548"
---
# <a name="parallel-algorithms"></a>Algorytmy równoległe

Biblioteka wzorców równoległych (PPL) zapewnia algorytmy, które współbieżnie wykonują prace nad kolekcjami danych. Algorytmy te przypominają te udostępniane przez C++ bibliotekę Standard.

Algorytmy równoległe składają się z istniejących funkcji w środowisko uruchomieniowe współbieżności. Na przykład algorytm [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) używa obiektu [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) do wykonywania iteracji pętli równoległej. `parallel_for` Algorytmy partycji działają w optymalny sposób z uwzględnieniem dostępnej liczby zasobów obliczeniowych.

##  <a name="top"></a>Poszczególne

- [Algorytm parallel_for](#parallel_for)

- [Algorytm parallel_for_each](#parallel_for_each)

- [Algorytm parallel_invoke](#parallel_invoke)

- [Algorytmy parallel_transform i parallel_reduce](#parallel_transform_reduce)

    - [Algorytm parallel_transform](#parallel_transform)

    - [Algorytm parallel_reduce](#parallel_reduce)

    - [Przykład: Wykonywanie map i zmniejszanie ich równolegle](#map_reduce_example)

- [Partycjonowanie pracy](#partitions)

- [Sortowanie równoległe](#parallel_sorting)

    - [Wybieranie algorytmu sortowania](#choose_sort)

##  <a name="parallel_for"></a>Algorytm parallel_for

Algorytm [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) wielokrotnie wykonuje to samo zadanie równolegle. Każde z tych zadań jest sparametryzowane przez wartość iteracji. Ten algorytm jest przydatny, gdy istnieje treść pętli, która nie udostępnia zasobów między iteracjami tej pętli.

`parallel_for` Algorytm dzieli zadania w optymalny sposób na potrzeby wykonywania równoległego. Używa algorytmu kradzieży i zakresu kradzieży w celu zrównoważenia tych partycji, gdy obciążenia są niezrównoważone. Gdy pętla iteracji jednej pętli jest wspólna, środowisko uruchomieniowe ponownie dystrybuuje zakres iteracji przypisanych do bieżącego wątku do innych wątków lub procesorów. Podobnie, gdy wątek kończy zakres iteracji, środowisko uruchomieniowe dystrybuuje pracę z innych wątków do tego wątku. Algorytm obsługuje również *zagnieżdżone równoległości.* `parallel_for` Gdy jedna pętla równoległa zawiera inną pętlę równoległą, środowisko uruchomieniowe koordynuje zasoby przetwarzania między ciałami pętli w skuteczny sposób na potrzeby wykonywania równoległego.

`parallel_for` Algorytm ma kilka przeciążonych wersji. Pierwsza wersja przyjmuje wartość początkową, wartość końcową i funkcję służbową (wyrażenie lambda, obiekt funkcji lub wskaźnik funkcji). Druga wersja przyjmuje wartość początkową, wartość końcową, wartość, przez którą można wykonać krok, i funkcję służbową. Pierwsza wersja tej funkcji używa jako wartości kroku 1. Pozostałe wersje pobierają obiekty programu Partitioner, które umożliwiają określenie, jak `parallel_for` należy podzielić na siebie zakresy między wątkami. Partycje zostały omówione bardziej szczegółowo w sekcji partycjonowanie [pracy](#partitions) w tym dokumencie.

Można skonwertować wiele `for` pętli do użycia `parallel_for`. Jednak algorytm różni się od instrukcji w następujący sposób: `for` `parallel_for`

- `parallel_for` Algorytm`parallel_for` nie wykonuje zadań w wstępnie ustalonej kolejności.

- `parallel_for` Algorytm nie obsługuje arbitralnych warunków zakończenia. Algorytm zostaje zatrzymany, gdy bieżąca wartość zmiennej iteracji jest mniejsza niż `last`. `parallel_for`

- Parametr `_Index_type` typu musi być typem całkowitym. Ten typ całkowity może być podpisany lub niepodpisany.

- Iteracja pętli musi być przesunięta. Algorytm zgłasza wyjątek typu [std:: invalid_argument](../../standard-library/invalid-argument-class.md) , `_Step` Jeśli parametr jest mniejszy niż 1. `parallel_for`

- Mechanizm obsługi wyjątków dla `parallel_for` algorytmu różni się od `for` pętli. Jeśli wiele wyjątków występuje jednocześnie w treści pętli równoległej, środowisko uruchomieniowe propaguje tylko jeden z wyjątków do wątku, który został `parallel_for`wywołany. Ponadto, gdy jedna iteracja pętli zgłasza wyjątek, środowisko uruchomieniowe nie zatrzymuje natychmiast pętli ogólnej. Zamiast tego pętla jest umieszczana w stanie anulowanym, a środowisko uruchomieniowe odrzuca wszystkie zadania, które nie zostały jeszcze uruchomione. Aby uzyskać więcej informacji na temat obsługi wyjątków i algorytmów równoległych, zobacz [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

`parallel_for` Chociaż algorytm nie obsługuje arbitralnych warunków zakończenia, można użyć anulowania, aby zatrzymać wszystkie zadania. Aby uzyskać więcej informacji na temat anulowania, zobacz [anulowania w PPL](cancellation-in-the-ppl.md).

> [!NOTE]
>  Koszt planowania, który wynika z równoważenia obciążenia i pomocy technicznej dla funkcji, takich jak anulowanie, może nie przezwyciężyć korzyści płynących z równoległej pętli, szczególnie gdy treść pętli jest stosunkowo mała. Możesz zminimalizować ten koszt przy użyciu partycji w pętli równoległej. Aby uzyskać więcej informacji, zobacz [partycjonowanie pracy](#partitions) w dalszej części tego dokumentu.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje podstawową strukturę `parallel_for` algorytmu. Ten przykład drukuje do konsoli każdej wartości z zakresu [1, 5] równolegle.

[!code-cpp[concrt-parallel-for-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_1.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe:

```Output
1 2 4 3 5
```

`parallel_for` Ponieważ algorytm działa równolegle do każdego elementu, kolejność, w jakiej wartości są drukowane w konsoli, będzie różna.

Pełny przykład wykorzystujący `parallel_for` algorytm można znaleźć w temacie [How to: Napisz pętlę](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)parallel_for.

[[Top](#top)]

##  <a name="parallel_for_each"></a>Algorytm parallel_for_each

Algorytm [concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) wykonuje zadania w kontenerze iteracyjnym, takim jak te dostarczone przez C++ standardową bibliotekę, równolegle. Używa tej samej logiki partycjonowania, której `parallel_for` używa algorytm.

Algorytm `parallel_for_each` jest podobny C++ do algorytmu standardowa biblioteka [std:: for_each](../../standard-library/algorithm-functions.md#for_each) , z tą różnicą `parallel_for_each` , że algorytm wykonuje zadania współbieżnie. Podobnie jak w przypadku innych `parallel_for_each` algorytmów równoległych, program nie wykonuje zadań w określonej kolejności.

Mimo że `parallel_for_each` algorytm działa zarówno Iteratory do przodu, jak i Iteratory dostępu losowego, sprawdza się lepiej przy użyciu iteratorów dostępu losowego.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje podstawową strukturę `parallel_for_each` algorytmu. Ten przykład drukuje do konsoli każdą wartość w obiekcie [std:: Array](../../standard-library/array-class-stl.md) równolegle.

[!code-cpp[concrt-parallel-for-each-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_2.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe:

```Output
4 5 1 2 3
```

`parallel_for_each` Ponieważ algorytm działa równolegle do każdego elementu, kolejność, w jakiej wartości są drukowane w konsoli, będzie różna.

Pełny przykład wykorzystujący `parallel_for_each` algorytm można znaleźć w temacie [How to: Napisz pętlę](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)parallel_for_each.

[[Top](#top)]

##  <a name="parallel_invoke"></a>Algorytm parallel_invoke

Algorytm [concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) wykonuje zestaw zadań równolegle. Nie zwraca do momentu zakończenia każdego zadania. Ten algorytm jest przydatny, gdy masz kilka niezależnych zadań, które mają być wykonywane w tym samym czasie.

`parallel_invoke` Algorytm przyjmuje jako parametry serię funkcji roboczych (funkcji lambda, obiektów funkcyjnych lub wskaźników funkcji). `parallel_invoke` Algorytm jest przeciążony do dwóch i dziesięciu parametrów. Każda funkcja, którą przekazujesz `parallel_invoke` , musi przyjmować zero parametrów.

Podobnie jak w przypadku innych `parallel_invoke` algorytmów równoległych, program nie wykonuje zadań w określonej kolejności. Równoległość [zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md) tematu wyjaśnia, `parallel_invoke` jak algorytm wiąże się z zadaniami i grupami zadań.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje podstawową strukturę `parallel_invoke` algorytmu. Ten przykład współbieżnie wywołuje `twice` funkcję na trzech zmiennych lokalnych i drukuje wynik do konsoli.

[!code-cpp[concrt-parallel-invoke-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_3.cpp)]

Ten przykład generuje następujące wyniki:

```Output
108 11.2 HelloHello
```

Aby zapoznać się z kompletnymi `parallel_invoke` przykładami korzystającymi z algorytmu, zobacz [How to: Użyj parallel_invoke, aby napisać równoległą procedurę](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) sortowania [i instrukcje: Użyj parallel_invoke do wykonywania operacji](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)równoległych.

[[Top](#top)]

##  <a name="parallel_transform_reduce"></a>Algorytmy parallel_transform i parallel_reduce

Algorytmy [concurrency::p arallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) i [concurrency::p arallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) są równoległymi wersjami C++ algorytmów biblioteki standardowej [std:: Transform](../../standard-library/algorithm-functions.md#transform) i [std:: kumulują](../../standard-library/numeric-functions.md#accumulate)się odpowiednio. Wersje środowisko uruchomieniowe współbieżności zachowują się C++ jak standardowe wersje biblioteki, z tą różnicą, że kolejność operacji nie jest określana, ponieważ są wykonywane równolegle. Te algorytmy są używane podczas pracy z zestawem, który jest wystarczająco duży, aby uzyskać korzyści z wydajności i skalowalności przetwarzane równolegle.

> [!IMPORTANT]
>  Algorytmy `parallel_reduce` i obsługują tylko dostęp losowy, dwukierunkowe i Iteratory do przodu, ponieważ te Iteratory generują stabilne adresy pamięci. `parallel_transform` Ponadto te Iteratory muszą generować wartości inne niż`const` l.

###  <a name="parallel_transform"></a>Algorytm parallel_transform

Można użyć `parallel transform` algorytmu do wykonywania wielu operacji przetwarzanie równoległe danych. Możesz na przykład:

- Dostosuj jasność obrazu i wykonaj inne operacje przetwarzania obrazu.

- Należy obliczyć lub pobrać iloczyn kropki między dwoma wektorami i wykonać inne obliczenia liczbowe na wektorach.

- Wykonaj śledzenie 3-D ray, gdzie każda iteracja odnosi się do jednego piksela, który musi być renderowany.

Poniższy przykład pokazuje podstawową strukturę, która jest używana do wywołania `parallel_transform` algorytmu. Ten przykład wyklucza każdy element obiektu std::[Vector](../../standard-library/vector-class.md) na dwa sposoby. Pierwszy sposób używa wyrażenia lambda. Drugi sposób używa [std:: Negate](../../standard-library/negate-struct.md), który pochodzi od [std:: unary_function](../../standard-library/unary-function-struct.md).

[!code-cpp[concrt-basic-parallel-transform#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_4.cpp)]

> [!WARNING]
>  W tym przykładzie przedstawiono podstawowe użycie `parallel_transform`. Ponieważ funkcja robocza nie wykonuje znacznej nakładu pracy, w tym przykładzie nie jest oczekiwany znaczący wzrost wydajności.

`parallel_transform` Algorytm ma dwa przeciążenia. Pierwsze Przeciążenie pobiera jeden zakres wejściowy i funkcję jednoargumentową. Funkcja Jednoargumentowa może być wyrażeniem lambda, które przyjmuje jeden argument, obiekt funkcji lub typ, który pochodzi od `unary_function`. Drugie Przeciążenie pobiera dwa zakresy wejściowe i funkcję binarną. Funkcja Binary może być wyrażeniem lambda, które przyjmuje dwa argumenty, obiekt funkcji lub typ, który pochodzi od [std:: binary_function](../../standard-library/binary-function-struct.md). Poniższy przykład ilustruje te różnice.

[!code-cpp[concrt-parallel-transform-vectors#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_5.cpp)]

> [!IMPORTANT]
>  Iterator, który dostarczasz dla danych wyjściowych `parallel_transform` musi całkowicie nakładać się na iterator danych wejściowych lub nie nakładać się na siebie. Zachowanie tego algorytmu nie jest określone, jeśli Iteratory wejściowe i wyjściowe częściowo nakładają się na siebie.

###  <a name="parallel_reduce"></a>Algorytm parallel_reduce

`parallel_reduce` Algorytm jest przydatny w przypadku sekwencji operacji, które spełniają Właściwość asocjacyjną. (Ten algorytm nie wymaga właściwości komutatywna). Poniżej przedstawiono niektóre operacje, które można wykonywać w programie `parallel_reduce`:

- Pomnóż sekwencje macierzy, aby utworzyć macierz.

- Pomnóż wektor przez sekwencję macierzy, aby utworzyć wektor.

- Oblicza długość sekwencji ciągów.

- Połącz listę elementów, takich jak ciągi, w jeden element.

Poniższy przykład podstawowy pokazuje, `parallel_reduce` jak używać algorytmu do łączenia sekwencji ciągów w jeden ciąg. Podobnie jak w przypadku przykładów `parallel_transform`, wzrost wydajności nie jest oczekiwany w tym podstawowym przykładzie.

[!code-cpp[concrt-basic-parallel-reduce#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_6.cpp)]

W wielu przypadkach można traktować `parallel_reduce` jako skrót do użycia `parallel_for_each` algorytmu wraz z klasą [concurrency::Binding](../../parallel/concrt/reference/combinable-class.md) .

###  <a name="map_reduce_example"></a>Przyklad Wykonywanie map i zmniejszanie ich równolegle

Operacja *mapy* stosuje funkcję do każdej wartości w sekwencji. Operacja *redukcji* łączy elementy sekwencji w jedną wartość. Można użyć C++ standardowych bibliotek [std:: Transform](../../standard-library/algorithm-functions.md#transform) i [std:: akumulacji](../../standard-library/numeric-functions.md#accumulate) do wykonywania map i zmniejszania operacji. Jednak w przypadku wielu problemów można użyć `parallel_transform` algorytmu, aby wykonać operację mapowania równolegle, `parallel_reduce` a algorytm wykonywał równolegle operację zmniejszania.

Poniższy przykład porównuje czas potrzebny do obliczenia sumy wartości i liczby pierwszych. Faza mapy przekształca wartości niepodstawowe na 0, a faza zmniejszania sumuje wartości.

[!code-cpp[concrt-parallel-map-reduce-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_7.cpp)]

Aby uzyskać inny przykład, który wykonuje mapę i zmniejsza operację równolegle, zobacz [How to: Wykonaj mapowanie i zmniejsz liczbę operacji równolegle](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

[[Top](#top)]

##  <a name="partitions"></a>Partycjonowanie pracy

Aby zrównoleglanie operację na źródle danych, istotnym krokiem jest partycjonowanie źródła w wielu sekcjach, do których można uzyskać dostęp jednocześnie przez wiele wątków. Partycja określa, w jaki sposób algorytm równoległy ma podzielić zakresy między wątki. Jak wyjaśniono wcześniej w tym dokumencie, PPL używa domyślnego mechanizmu partycjonowania, który tworzy początkowe obciążenie, a następnie korzysta z algorytmu kradzieży i zakresu kradzieży, aby zrównoważyć te partycje, gdy obciążenia są niezrównoważone. Na przykład gdy jedna pętla iteracji kończy zakres iteracji, środowisko uruchomieniowe dystrybuuje pracę z innych wątków do tego wątku. Jednak w przypadku niektórych scenariuszy warto określić inny mechanizm partycjonowania, który jest lepiej dostosowany do Twojego problemu.

Algorytmy `parallel_for_each` ,i`parallel_transform` zapewniają przeciążone wersje, które pobierają dodatkowy parametr. `_Partitioner` `parallel_for` Ten parametr definiuje typ partycji, który dzieli działanie. Oto typy partycji, które definiuje PPL:

[concurrency:: affinity_partitioner](../../parallel/concrt/reference/affinity-partitioner-class.md)<br/>
Dzieli pracy na stałą liczbę zakresów (zazwyczaj liczbę wątków roboczych, które są dostępne do pracy w pętli). Ten typ partycji jest podobny `static_partitioner`, ale usprawnia koligację pamięci podręcznej w sposób, w jaki mapuje zakresy na wątki robocze. Ten typ partycji może zwiększyć wydajność, gdy pętla jest wykonywana nad tym samym zestawem danych wielokrotnie (np. pętla w pętli), a dane mieszczą się w pamięci podręcznej. Ta partycja nie jest w pełni uczestniczyć w anulowaniu. Nie jest również używana wspólna semantyka blokująca i dlatego nie można jej używać z pętlami równoległymi, które mają zależność dalej.

[concurrency:: auto_partitioner](../../parallel/concrt/reference/auto-partitioner-class.md)<br/>
Dzieli pracy na początkową liczbę zakresów (zazwyczaj liczbę wątków roboczych, które są dostępne do pracy w pętli). Środowisko uruchomieniowe domyślnie używa tego typu, jeśli nie wywoła przeciążonego algorytmu równoległego, który przyjmuje `_Partitioner` parametr. Każdy zakres może być podzielony na podzakresy, a tym samym włączenie równoważenia obciążenia. Po zakończeniu zakresu pracy środowisko uruchomieniowe ponownie dystrybuuje podrzędne zakresy pracy z innych wątków do tego wątku. Użyj tego programu Partitioner, jeśli obciążenie nie jest objęte jedną z innych kategorii lub potrzebujesz pełnej obsługi anulowania lub blokowania w ramach współpracy.

[concurrency:: simple_partitioner](../../parallel/concrt/reference/simple-partitioner-class.md)<br/>
Dzieli pracy na zakresy, aby każdy zakres miał co najmniej liczbę iteracji, które są określone przez dany rozmiar fragmentu. Ten typ partycji wchodzi w skład równoważenia obciążenia; jednak środowisko uruchomieniowe nie dzieli zakresów na zakresy podrzędne. Dla każdego procesu roboczego środowisko uruchomieniowe sprawdza obecność anulowania i wykonuje Równoważenie obciążenia po `_Chunk_size` zakończeniu iteracji.

[concurrency:: static_partitioner](../../parallel/concrt/reference/static-partitioner-class.md)<br/>
Dzieli pracy na stałą liczbę zakresów (zazwyczaj liczbę wątków roboczych, które są dostępne do pracy w pętli). Ten typ partycji może zwiększyć wydajność, ponieważ nie korzysta z kradzieży i dlatego ma mniej nakładu pracy. Użyj tego typu partycji, gdy każda iteracja pętli równoległej wykonuje ustaloną i jednolite ilość pracy, i nie jest wymagana obsługa anulowania ani przekazywania dalej.

> [!WARNING]
>  Algorytmy `parallel_transform`iobsługują tylko kontenery, w których są używane Iteratory dostępu losowego (takie jak std:: Vector) dla partycji statycznych, prostych i koligacji.[](../../standard-library/vector-class.md) `parallel_for_each` Użycie kontenerów korzystających z dwukierunkowych i progresywnych iteratorów powoduje błąd w czasie kompilacji. Domyślny program Partitioner `auto_partitioner`obsługuje wszystkie trzy typy iteratorów.

Zazwyczaj te partycje są używane w taki sam sposób, z wyjątkiem `affinity_partitioner`. Większość typów partycji nie utrzymuje stanu i nie są modyfikowane przez środowisko uruchomieniowe. W związku z tym można utworzyć te obiekty partycji w miejscu wywołania, jak pokazano w poniższym przykładzie.

[!code-cpp[concrt-static-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_8.cpp)]

Jednak należy przekazać `affinity_partitioner` obiekt jako odwołanie`const`niebędące wartością l, aby algorytm mógł przechowywać stan dla przyszłych pętli do ponownego użycia. W poniższym przykładzie pokazano podstawową aplikację, która wykonuje tę samą operację na zestawie danych równolegle wiele razy. Korzystanie z programu `affinity_partitioner` może poprawić wydajność, ponieważ tablica może zmieścić się w pamięci podręcznej.

[!code-cpp[concrt-affinity-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_9.cpp)]

> [!CAUTION]
>  Należy zachować ostrożność, gdy modyfikujesz istniejący kod, który opiera się na wspólnej semantyki `affinity_partitioner`blokującej, aby użyć `static_partitioner` lub. Te typy partycji nie używają funkcji równoważenia obciążenia ani kradzieży zakresu, dlatego mogą zmieniać zachowanie aplikacji.

Najlepszym sposobem, aby określić, czy używać partycji w danym scenariuszu, jest eksperymentowanie i pomiar, jak długo trwa wykonywanie operacji w ramach reprezentatywnych obciążeń i konfiguracji komputerów. Na przykład partycjonowanie statyczne może zapewnić znaczący przyspieszenie na komputerze z wieloma rdzeniami, który ma tylko kilka rdzeni, ale może to spowodować spowolnienie na komputerach mających stosunkowo wiele rdzeni.

[[Top](#top)]

##  <a name="parallel_sorting"></a>Sortowanie równoległe

PPL udostępnia trzy algorytmy sortowania: [concurrency::p arallel_sort](reference/concurrency-namespace-functions.md#parallel_sort), [concurrency::p arallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort)i [concurrency::p arallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort). Te algorytmy sortowania są przydatne, gdy istnieje zestaw danych, który może korzystać z równoczesnego sortowania. W szczególności sortowanie równoległe jest przydatne w przypadku dużego zestawu danych lub korzystania z obliczeniowej operacji porównywania w celu sortowania danych. Każdy z tych algorytmów sortuje elementy na miejscu.

Algorytmy `parallel_buffered_sort` i są zarówno algorytmami opartymi na porównaniu. `parallel_sort` Oznacza to, że porównują elementy według wartości. `parallel_sort` Algorytm nie ma dodatkowych wymagań dotyczących pamięci i jest odpowiedni do sortowania ogólnego przeznaczenia. Algorytm może działać lepiej niż `parallel_sort`, ale wymaga miejsca O (N). `parallel_buffered_sort`

`parallel_radixsort` Algorytm jest oparty na skrótach. Oznacza to, że używa kluczy liczb całkowitych do sortowania elementów. Przy użyciu kluczy, ten algorytm może bezpośrednio obliczyć miejsce docelowe elementu zamiast używać porównań. Podobnie `parallel_buffered_sort`jak, ten algorytm wymaga miejsca O (N).

Poniższa tabela zawiera podsumowanie ważnych właściwości trzech równoległych algorytmów sortowania.

|Algorytm|Opis|Mechanizm sortowania|Zasortuj stabilność|Wymagania dotyczące pamięci|Złożoność czasu|Dostęp iteratora|
|---------------|-----------------|-----------------------|--------------------|-------------------------|---------------------|---------------------|
|`parallel_sort`|Sortowanie w oparciu o porównanie ogólnego przeznaczenia.|Porównanie (rosnąco)|Stanie|Brak|O ((N/P) log (N/P) + 2N ((P-1)/P))|Wybranych|
|`parallel_buffered_sort`|Szybsze sortowanie oparte na porównaniu ogólnego przeznaczenia, które wymaga miejsca O (N).|Porównanie (rosnąco)|Stanie|Wymaga dodatkowego miejsca O (N)|O ((N/P) log (N))|Wybranych|
|`parallel_radixsort`|Sortowanie na podstawie klucza liczb całkowitych, które wymaga miejsca O (N).|Oparte na skrótach|Stable|Wymaga dodatkowego miejsca O (N)|O (N/P)|Wybranych|

Na poniższej ilustracji przedstawiono ważne właściwości trzech równoległych algorytmów sortowania bardziej graficznie.

![Porównanie algorytmów sortowania](../../parallel/concrt/media/concrt_parallel_sorting.png "Porównanie algorytmów sortowania")

Te algorytmy sortowania równoległego są zgodne z regułami anulowania i obsługi wyjątków. Aby uzyskać więcej informacji o anulowaniu i obsłudze wyjątków w środowisko uruchomieniowe współbieżności, zobacz [anulowania równoległych algorytmów](../../parallel/concrt/cancellation-in-the-ppl.md#algorithms) i [obsługi wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

> [!TIP]
>  Te algorytmy sortowania równoległego obsługują semantykę przenoszenia. Można zdefiniować operator przypisania przenoszenia, aby umożliwić wykonywanie operacji zamiany bardziej wydajnie. Aby uzyskać więcej informacji na temat semantyki przenoszenia i operatora przypisania przenoszenia, zobacz [rvalue Reference deklarator: & &](../../cpp/rvalue-reference-declarator-amp-amp.md)i [Przenieś konstruktory i operatory przypisania przenoszeniaC++()](../../cpp/move-constructors-and-move-assignment-operators-cpp.md). Jeśli nie podasz operatora przypisania przenoszenia lub funkcji zamiany, algorytmy sortowania używają konstruktora kopiującego.

Poniższy przykład podstawowy pokazuje `parallel_sort` `vector` , jak używać do sortowania wartości.`int` Domyślnie program `parallel_sort` używa [std:: less](../../standard-library/less-struct.md) do porównywania wartości.

[!code-cpp[concrt-basic-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_10.cpp)]

Ten przykład pokazuje, jak zapewnić niestandardową funkcję porównania. Używa metody [std:: Complex:: Real](../../standard-library/complex-class.md#real) do sortowania wartości [std:: Complex\<o podwójnej precyzji >](../../standard-library/complex-double.md) w kolejności rosnącej.

[!code-cpp[concrt-basic-parallel-sort#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_11.cpp)]

Ten przykład pokazuje, `parallel_radixsort` jak zapewnić funkcję skrótu do algorytmu. Ten przykład sortuje punkty 3-D. Punkty są sortowane na podstawie odległości od punktu odniesienia.

[!code-cpp[concrt-parallel-sort-points#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_12.cpp)]

Na ilustracji w tym przykładzie jest stosowany stosunkowo mały zestaw danych. Możesz zwiększyć początkowy rozmiar wektora, aby eksperymentować z ulepszeniami wydajności nad większymi zestawami danych.

W tym przykładzie używa wyrażenia lambda jako funkcji skrótu. Można również użyć jednego z wbudowanych implementacji klasy std::[hash](../../standard-library/hash-class.md) lub zdefiniować własną specjalizację. Można również użyć niestandardowego obiektu funkcji skrótu, jak pokazano w tym przykładzie:

[!code-cpp[concrt-parallel-sort-points#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_13.cpp)]

[!code-cpp[concrt-parallel-sort-points#3](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_14.cpp)]

Funkcja skrótu musi zwracać typ całkowity ([std:: is_integral:: value](../../standard-library/is-integral-class.md) musi mieć wartość **true**). Ten typ całkowity musi być konwertowany na typ `size_t`.

###  <a name="choose_sort"></a>Wybieranie algorytmu sortowania

W wielu przypadkach `parallel_sort` zapewnia najlepszą równowagę w zakresie szybkości i wydajności pamięci. Jednak w miarę zwiększania rozmiaru zestawu danych, liczby dostępnych procesorów lub złożoności funkcji `parallel_buffered_sort` porównywania lub `parallel_radixsort` można wykonać lepsze. Najlepszym sposobem na określenie, który algorytm sortowania ma być używany w danym scenariuszu, jest eksperymentowanie i pomiar czasu, jaki jest potrzebny do sortowania typowych danych w ramach konfiguracji reprezentatywnych komputerów. Po wybraniu strategii sortowania należy pamiętać o następujących kwestiach.

- Rozmiar Twojego zestawu danych. W tym dokumencie *mały* zestaw danych zawiera mniej niż 1 000 elementów. *Średni* zestaw danych zawiera od 10 000 do 100 000 elementów, a *duży* zestaw danych zawiera więcej niż 100 000 elementów.

- Ilość pracy wykonywanej przez funkcję Compare lub funkcję skrótu.

- Ilość dostępnych zasobów obliczeniowych.

- Charakterystyki zestawu danych. Na przykład jeden algorytm może działać poprawnie dla danych, które są już niemal posortowane, ale nie tylko dla danych, które są całkowicie niesortowane.

- Rozmiar fragmentu. Opcjonalny `_Chunk_size` argument określa, kiedy algorytm przełącza się z równoległej do implementacji sortowania szeregowego, ponieważ dzieli ogólne sortowanie na mniejsze jednostki pracy. Na przykład jeśli podano 512, algorytm przełączy się na implementację seryjną, gdy jednostka pracy zawiera 512 lub mniej elementów. Implementacja szeregowa może poprawić ogólną wydajność, ponieważ eliminuje obciążenie wymagane do równoległego przetwarzania danych.

Nie można wartościowa jednocześnie sortować niewielkiego zestawu danych, nawet jeśli masz dużą liczbę dostępnych zasobów obliczeniowych lub funkcja Compare lub funkcja skrótu wykonuje stosunkowo dużą ilość pracy. Można użyć funkcji [std:: sort](../../standard-library/algorithm-functions.md#sort) do sortowania małych zestawów danych. (`parallel_sort` i `parallel_buffered_sort` wywołuje `parallel_buffered_sort` się, gdy określisz rozmiar fragmentu, który jest większy niż zestaw danych, ale będzie trzeba przydzielić O (N) miejsce, co może zająć dodatkowy czas z powodu zablokowania rywalizacji lub alokacji pamięci). `sort`

W przypadku konieczności zablokowania pamięci lub przydzielenia pamięci należy użyć `parallel_sort` do sortowania zestawu danych o średnim rozmiarze. `parallel_sort`nie wymaga dodatkowego miejsca; inne algorytmy wymagają miejsca O (N).

Użyj `parallel_buffered_sort` , aby posortować zestawy danych o rozmiarze średnim i kiedy aplikacja spełnia dodatkowe wymagania dotyczące miejsca na (N). `parallel_buffered_sort`może być szczególnie przydatne w przypadku dużej liczby zasobów obliczeniowych lub kosztownej funkcji porównywania lub funkcji skrótu.

Użyj `parallel_radixsort` , aby sortować duże zestawy danych, gdy aplikacja spełnia wymagania dodatkowe O (N) przestrzeni. `parallel_radixsort`może być szczególnie przydatne, gdy równoważna operacja porównania jest droższa lub gdy obie operacje są kosztowne.

> [!CAUTION]
>  Zaimplementowanie dobrej funkcji mieszania wymaga, aby znać zakres zestawu danych i jak każdy element w zestawie danych został przekształcony na odpowiadającą mu wartość unsigned. Ponieważ operacja skrótu działa na wartościach bez znaku, należy rozważyć inną strategię sortowania, jeśli nie można wytworzyć niepodpisanych wartości skrótu.

Poniższy przykład porównuje `sort`wydajność `parallel_buffered_sort`, `parallel_sort`, i `parallel_radixsort` z tym samym dużym zestawem danych losowych.

[!code-cpp[concrt-choosing-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_15.cpp)]

W tym przykładzie, który zakłada, że można przydzielić o (N) miejsce podczas sortowania, program `parallel_radixsort` wykonuje najlepsze dla tego zestawu danych w konfiguracji tego komputera.

[[Top](#top)]

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Instrukcje: pisanie pętli parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)|Pokazuje, `parallel_for` jak używać algorytmu do wykonywania mnożenia macierzy.|
|[Instrukcje: pisanie pętli parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)|Pokazuje, `parallel_for_each` jak używać algorytmu do obliczania liczby pierwszych numerów w obiekcie [std:: Array](../../standard-library/array-class-stl.md) równolegle.|
|[Instrukcje: używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Pokazuje, `parallel_invoke` jak używać algorytmu w celu zwiększenia wydajności algorytmu sortowania bitonicznego.|
|[Instrukcje: wykonywanie operacji równoległych za pomocą elementu Parallel.Invoke](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Pokazuje, `parallel_invoke` jak używać algorytmu, aby zwiększyć wydajność programu wykonującego wiele operacji w udostępnionym źródle danych.|
|[Instrukcje: równoległe wykonywanie operacji mapowania i zmniejszania](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Pokazuje, jak używać `parallel_transform` algorytmów i `parallel_reduce` do wykonywania map i zmniejszania operacji, która zlicza wystąpienia wyrazów w plikach.|
|[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Opisuje PPL, który zapewnia bezwzględny model programistyczny, który promuje skalowalność i łatwość używania do tworzenia współbieżnych aplikacji.|
|[Anulowanie w PPL](cancellation-in-the-ppl.md)|Wyjaśnia rolę anulowania w PPL, jak anulować pracę równoległą i jak ustalić, kiedy grupa zadań została anulowana.|
|[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Wyjaśnia rolę obsługi wyjątków w środowisko uruchomieniowe współbieżności.|

## <a name="reference"></a>Tematy pomocy

[parallel_for, funkcja](reference/concurrency-namespace-functions.md#parallel_for)

[parallel_for_each — funkcja](reference/concurrency-namespace-functions.md#parallel_for_each)

[parallel_invoke, funkcja](reference/concurrency-namespace-functions.md#parallel_invoke)

[affinity_partitioner, klasa](../../parallel/concrt/reference/affinity-partitioner-class.md)

[auto_partitioner, klasa](../../parallel/concrt/reference/auto-partitioner-class.md)

[simple_partitioner, klasa](../../parallel/concrt/reference/simple-partitioner-class.md)

[static_partitioner, klasa](../../parallel/concrt/reference/static-partitioner-class.md)

[parallel_sort, funkcja](reference/concurrency-namespace-functions.md#parallel_sort)

[parallel_buffered_sort, funkcja](reference/concurrency-namespace-functions.md#parallel_buffered_sort)

[parallel_radixsort Function](reference/concurrency-namespace-functions.md#parallel_radixsort)
