---
title: Algorytmy równoległe
ms.date: 11/04/2016
helpviewer_keywords:
- parallel algorithms [Concurrency Runtime]
ms.assetid: 045dca7b-4d73-4558-a44c-383b88a28473
ms.openlocfilehash: 0ad7f67016dcb7d4638de0f159feb23cd1282b19
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445594"
---
# <a name="parallel-algorithms"></a>Algorytmy równoległe

Biblioteka równoległych wzorców (PPL) zawiera algorytmy, które jednocześnie wykonują prace na zbiory danych. Te algorytmy przypominają te oferowane przez standardowej biblioteki języka C++.

Algorytmy równoległe składają się z istniejącą funkcje we współbieżnym środowisku wykonawczym. Na przykład [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytm używa [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) obiektu w celu wykonania iteracji pętli równoległej. `parallel_for` Partycje algorytm pracować w optymalny sposób podana liczba dostępnych zasobów obliczeniowych.

##  <a name="top"></a> Sekcje

- [Funkcja parallel_for Algorithm](#parallel_for)

- [Funkcja parallel_for_each Algorithm](#parallel_for_each)

- [Funkcja parallel_invoke Algorithm](#parallel_invoke)

- [Funkcja parallel_transform and parallel_reduce Algorithms](#parallel_transform_reduce)

    - [Funkcja parallel_transform Algorithm](#parallel_transform)

    - [Funkcja parallel_reduce Algorithm](#parallel_reduce)

    - [Przykład: Wykonywanie mapowania i zmniejszenie równoległości](#map_reduce_example)

- [Partycjonowanie pracy](#partitions)

- [Sortowanie równoległe](#parallel_sorting)

    - [Wybieranie algorytmu sortowania](#choose_sort)

##  <a name="parallel_for"></a> Funkcja parallel_for Algorithm

[Concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytm wielokrotnie wykonuje to samo zadanie równocześnie. Każda z tych zadań jest sparametryzowane przez wartość iteracji. Ten algorytm jest przydatne, gdy ciało pętli, która nie współużytkowanie zasobów między iteracjami pętli tego.

`parallel_for` Algorytm partycje zadania w sposób optymalny dla przetwarzania równoległego. Używa algorytmu kradzież pracy się i kradzież równoważyć partycje, w przypadku obciążeń niezrównoważone zakresu. Gdy jednej iteracji pętli blokuje wspólne, środowisko uruchomieniowe dystrybuuje zakres iteracji, który jest przypisany do bieżącego wątku do innych wątków lub procesorów. Podobnie gdy wątek ukończy szeregu iteracji, środowisko uruchomieniowe dystrybuuje pracy z innych wątków do tego wątku. `parallel_for` Obsługuje również algorytm *zagnieżdżone równoległości*. Po jednej pętli równoległej zawiera innej pętli równoległej, środowisko uruchomieniowe koordynuje przetwarzania zasobów między jednostkami pętli w sposób efektywny dla przetwarzania równoległego.

`parallel_for` Algorytm ma kilka przeciążone wersje. Pierwsza wersja przyjmuje wartość początkową, wartość końcową i funkcji pracy (wyrażenia lambda, obiektów funkcyjnych lub wskaźnik funkcji). Druga wersja przyjmuje wartość początkową, wartość końcową, wartości za pomocą którego kroku, a funkcja pracy. Pierwsza wersja tej funkcji używa 1 jako wartość kroku. Pozostałe wersje zająć partycjonera obiektów, które umożliwiają określenie sposobu `parallel_for` powinien partycji zakresów między wątkami. Partycjonery omówiona bardziej szczegółowo w sekcji [partycjonowanie pracy](#partitions) w tym dokumencie.

Można przekonwertować wiele `for` pętli, aby użyć `parallel_for`. Jednak `parallel_for` algorytmu, który różni się od `for` instrukcji w następujący sposób:

- `parallel_for` Algorytm `parallel_for` nie wykonuje zadania w ustalonej kolejności.

- `parallel_for` Algorytm nie obsługuje warunków dowolnego rozwiązania. `parallel_for` Algorytm zatrzymuje, gdy bieżąca wartość zmiennej iteracji jest jeden mniejsza niż `last`.

- `_Index_type` Parametr typu musi być typu całkowitego. Ten typ całkowity może podpisane lub niepodpisane.

- Iteracji pętli musi być do przodu. `parallel_for` Algorytm zgłasza wyjątek typu [std::invalid_argument](../../standard-library/invalid-argument-class.md) Jeśli `_Step` parametru jest mniejszy niż 1.

- Mechanizm obsługi wyjątków `parallel_for` algorytmu, który różni się od `for` pętli. Jeśli wiele wyjątków jednocześnie występować w treści pętli równoległej, środowisko uruchomieniowe propaguje tylko jeden z wyjątków do wątku, który wywołał `parallel_for`. Ponadto po jednej iteracji pętli zgłasza wyjątek, środowisko wykonawcze nie natychmiast zatrzymuje ogólną pętli. Zamiast tego należy pętli znajduje się w stanie anulowania i środowisko uruchomieniowe odrzuca wszelkie zadania, które nie zostały rozpoczęte. Aby uzyskać więcej informacji na temat obsługi wyjątków i równoległych algorytmów, zobacz [wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Mimo że `parallel_for` algorytm nie obsługuje warunków dowolnego rozwiązania, możesz użyć anulowania, aby zatrzymać wszystkie zadania. Aby uzyskać więcej informacji dotyczących anulowania, zobacz [anulowanie w PPL](cancellation-in-the-ppl.md).

> [!NOTE]
>  Planowanie kosztów, czy wyniki z równoważenia obciążenia i pomoc techniczna dla funkcji, takich jak anulowanie nie może być przezwyciężyć zalety wykonywanie równoległe pętli, szczególnie gdy ciało pętli jest stosunkowo mały. Za pomocą partycjonera w swojej pętli równoległej, można zminimalizować to obciążenie. Aby uzyskać więcej informacji, zobacz [partycjonowanie pracy](#partitions) w dalszej części tego dokumentu.

### <a name="example"></a>Przykład

Poniższy kod przedstawia podstawowe struktury `parallel_for` algorytmu. W tym przykładzie drukuje do konsoli każdej wartości z zakresu [1, 5] równolegle.

[!code-cpp[concrt-parallel-for-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_1.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe:

```Output
1 2 4 3 5
```

Ponieważ `parallel_for` algorytm działa dla każdego elementu w sposób równoległy, różnią się w kolejności, w których wartości są drukowane do konsoli.

Aby uzyskać kompletny przykład, który używa `parallel_for` algorytmu, zobacz [instrukcje: pisanie pętli parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md).

[[Górnej](#top)]

##  <a name="parallel_for_each"></a> Funkcja parallel_for_each Algorithm

[Concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytm wykonuje zadania w pojemniku iteracyjne, takich jak te oferowane przez standardowej biblioteki C++, równolegle. Używa ona tę samą logikę partycjonowania, `parallel_for` używa algorytmu.

`parallel_for_each` Algorytm przypomina standardowej biblioteki C++ [std::for_each](../../standard-library/algorithm-functions.md#for_each) algorytmu, chyba że `parallel_for_each` algorytm wykonuje zadania jednocześnie. Inne algorytmy równoległe, takie jak `parallel_for_each` nie wykonuje zadania w określonej kolejności.

Mimo że `parallel_for_each` algorytm działa zarówno na tworzyć Iteratory do przodu i iteratorami dostępu swobodnego, działa lepiej z iteratorami dostępu swobodnego.

### <a name="example"></a>Przykład

Poniższy kod przedstawia podstawowe struktury `parallel_for_each` algorytmu. W tym przykładzie drukuje do konsoli każdej wartości w [std::array](../../standard-library/array-class-stl.md) obiektu równolegle.

[!code-cpp[concrt-parallel-for-each-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_2.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe:

```Output
4 5 1 2 3
```

Ponieważ `parallel_for_each` algorytm działa dla każdego elementu w sposób równoległy, różnią się w kolejności, w których wartości są drukowane do konsoli.

Aby uzyskać kompletny przykład, który używa `parallel_for_each` algorytmu, zobacz [instrukcje: pisanie pętli parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md).

[[Górnej](#top)]

##  <a name="parallel_invoke"></a> Funkcja parallel_invoke Algorithm

[Concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytm zestaw zadań jest wykonywana równolegle. Nie zwraca zakończenie każdego zadania. Ten algorytm jest przydatne, gdy masz kilka niezależnych zadań, które mają zostać zrealizowane w tym samym czasie.

`parallel_invoke` Algorytm przyjmuje jako parametry szereg funkcji pracy (funkcji lambda, obiektów funkcyjnych lub wskaźniki funkcji). `parallel_invoke` Algorytm jest przeciążona, aby zająć od 2 do 10 parametrów. Każdej funkcji, który jest przekazywany do `parallel_invoke` musi podjąć parametrów.

Inne algorytmy równoległe, takie jak `parallel_invoke` nie wykonuje zadania w określonej kolejności. Temat [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md) wyjaśnia sposób, w jaki `parallel_invoke` algorytmu, który odnosi się do grupy zadań i zadania.

### <a name="example"></a>Przykład

Poniższy kod przedstawia podstawowe struktury `parallel_invoke` algorytmu. W tym przykładzie jednocześnie wywołuje `twice` funkcji w trzech zmiennych lokalnych i drukuje wynik do konsoli.

[!code-cpp[concrt-parallel-invoke-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_3.cpp)]

Ten przykład generuje następujące wyniki:

```Output
108 11.2 HelloHello
```

Kompletne przykłady, które używają `parallel_invoke` algorytmu, zobacz [porady: używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) i [porady: używanie parallel_invoke do operacji równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md).

[[Górnej](#top)]

##  <a name="parallel_transform_reduce"></a> Funkcja parallel_transform and parallel_reduce Algorithms

[Concurrency::parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) i [concurrency::parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) algorytmy są wersje równoległych algorytmów standardowej biblioteki języka C++ [std::transform](../../standard-library/algorithm-functions.md#transform)i [std::accumulate](../../standard-library/numeric-functions.md#accumulate), odpowiednio. Wersje środowiska uruchomieniowego współbieżności zachowują się jak w wersjach standardowej biblioteki języka C++, z tą różnicą, że kolejność operacji nie jest określona, ponieważ są wykonywane równolegle. Podczas pracy z zestawem, która jest wystarczająco duża, aby uzyskać korzyści wynikające z wydajności i skalowalności być przetwarzana równolegle, należy użyć tych algorytmów.

> [!IMPORTANT]
>  `parallel_transform` i `parallel_reduce` algorytmów obsługuje tylko dostępu swobodnego dwukierunkowej i do przodu Iteratory, ponieważ te Iteratory wygenerować adresy stabilnej pamięci. Ponadto te Iteratory muszą przedstawić non -`const` l wartościami.

###  <a name="parallel_transform"></a> Funkcja parallel_transform Algorithm

Możesz użyć `parallel transform` algorytmu, aby wykonać wiele operacji przetwarzania równoległego danych. Możesz na przykład:

- Dopasuj jasność obrazu i wykonywać inne operacje przetwarzania obrazów.

- Suma lub ulokowania produktu kropka między dwoma wektorami i wykonywanie innych obliczeń numerycznych na wektorów.

- Wykonaj śledzenie 3-ray, gdzie każda iteracja odnosi się do jednego piksela, który musi być renderowany.

Poniższy kod przedstawia podstawowe strukturę, która jest używana do wywołania `parallel_transform` algorytmu. W tym przykładzie neguje każdy element std::[wektor](../../standard-library/vector-class.md) obiektu na dwa sposoby. Pierwszy sposób używa wyrażenia lambda. W drugim sposobie używana [std::negate](../../standard-library/negate-struct.md), która jest pochodną [std::unary_function](../../standard-library/unary-function-struct.md).

[!code-cpp[concrt-basic-parallel-transform#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_4.cpp)]

> [!WARNING]
>  W tym przykładzie pokazano podstawowe zastosowanie `parallel_transform`. Ponieważ ta funkcja pracy wykonuje znaczną ilość pracy, w tym przykładzie nie przewiduje się znaczne zwiększenie wydajności.

`parallel_transform` Algorytm ma dwa przeciążenia. Pierwsze przeciążenie przyjmuje jeden zakres danych wejściowych i funkcję jednoargumentową. Funkcję jednoargumentową może być wyrażenie lambda, która przyjmuje jeden argument, obiekt funkcji lub typ pochodzący z `unary_function`. Drugie przeciążenie przyjmuje dwa zakresy danych wejściowych i funkcja binarnego. Binarny funkcja może być wyrażenie lambda, która przyjmuje dwa argumenty, obiekt funkcji lub typ pochodzący z [std::binary_function](../../standard-library/binary-function-struct.md). Poniższy przykład ilustruje te różnice.

[!code-cpp[concrt-parallel-transform-vectors#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_5.cpp)]

> [!IMPORTANT]
>  Iterator, który należy podać dane wyjściowe `parallel_transform` należy całkowicie nakładają się iterator danych wejściowych lub nie nakładają się na wszystkich. Zachowanie ten algorytm jest nieokreślony, jeśli częściowo zachodzą na Iteratory wejściowych i wyjściowych.

###  <a name="parallel_reduce"></a> Funkcja parallel_reduce Algorithm

`parallel_reduce` Algorytm jest przydatne w przypadku, gdy sekwencji operacji, które spełniają asocjacyjnych właściwości. (Ten algorytm nie wymagają przemiennego właściwości). Poniżej przedstawiono niektóre operacje, które można wykonywać za pomocą `parallel_reduce`:

- Pomnóż sekwencje macierzy w celu utworzenia macierzy.

- Za pomocą sekwencji macierzy w celu utworzenia wektora, należy pomnożyć wektora.

- Obliczenia długości sekwencji ciągów.

- Lista elementów, takich jak ciągi, należy połączyć w jeden element.

Poniższy przykład podstawowy pokazuje, jak używać `parallel_reduce` algorytm połączyć sekwencją ciągów w jeden ciąg. Podobnie jak w przypadku przykładów dla `parallel_transform`, wzrost wydajności nie oczekuje się w tym podstawowym przykładzie.

[!code-cpp[concrt-basic-parallel-reduce#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_6.cpp)]

W wielu przypadkach można traktować `parallel_reduce` jako skrót do użytku z `parallel_for_each` algorytm wraz z [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) klasy.

###  <a name="map_reduce_example"></a> Przykład: Wykonywanie mapowania i zmniejszenie równoległości

A *mapy* operacja dotyczy funkcji każdej wartości w sekwencji. A *zmniejszyć* operacji łączy elementy sekwencji w jedną wartość. Możesz użyć standardowej biblioteki C++ [std::transform](../../standard-library/algorithm-functions.md#transform) i [std::accumulate](../../standard-library/numeric-functions.md#accumulate) funkcji wykonywanie mapowania i zmniejszanie operacji. Jednak wiele problemów, można użyć `parallel_transform` algorytmu do wykonania tej operacji mapy równolegle i `parallel_reduce` algorytmu do operacji Zmniejsz równolegle.

W poniższym przykładzie porównano czasu potrzebnego do obliczania sumy liczby pierwsze szeregowo i równolegle. Faza mapy przekształca niż iloczyn wartości 0 i Zmniejsz fazy sumy wartości.

[!code-cpp[concrt-parallel-map-reduce-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_7.cpp)]

Inny przykład, która wykonuje mapy i zmniejszyć liczbę operacji równoległych, zobacz [jak: wykonywać mapy i zmniejszyć operacji wykonywane równolegle](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

[[Górnej](#top)]

##  <a name="partitions"></a> Partycjonowanie pracy

Równoległe przetwarzanie operacji na źródle danych, jest bardzo ważnym etapem *partycji* źródło w wiele sekcji, które mogą być udostępniane jednocześnie z wielu wątków. Partycjonera Określa, jak algorytmu równoległego powinien partycji zakresów między wątkami. Jak wyjaśniono wcześniej w tym dokumencie, PPL korzysta z domyślnego partycjonowanie mechanizm, który tworzy początkową obciążenia, a następnie używa algorytmu kradzież pracy się i zakres kradzież równoważyć partycje, w przypadku obciążeń niezrównoważone. Na przykład po jednej iteracji pętli zakończeniu szeregu iteracji, środowisko uruchomieniowe dystrybuuje pracy z innych wątków wątek. Jednak w niektórych scenariuszach możesz chcieć określić inny mechanizm partycjonowania, który działa lepiej dostosowane do danego problemu.

`parallel_for`, `parallel_for_each`, I `parallel_transform` algorytmy podać przeciążone wersje, które przyjmują dodatkowy parametr, `_Partitioner`. Ten parametr określa typ partycjonera, który dzieli pracy. Poniżej przedstawiono rodzaje partycjonery definiujących PPL:

[CONCURRENCY::affinity_partitioner](../../parallel/concrt/reference/affinity-partitioner-class.md)<br/>
Dzieli działają na stałą liczbę zakresów (zwykle liczba wątków roboczych, które są dostępne do pracy w pętli). Ten typ partycjonera przypomina `static_partitioner`, ale zwiększa koligacji pamięci podręcznej, sposób mapowania zakresów wątków roboczych. Ten typ partycjonera może poprawić wydajność, jeśli pętla jest wykonywana za pośrednictwem tego samego zestawu danych, wiele razy (na przykład pętli w pętli) i danych mieści się w pamięci podręcznej. Ta partycjonera nie pełni uczestniczy w anulowania. On również nie używa semantyki blokowanie współpracy i dlatego nie można używać z pętli równoległych, które mają zależności do przodu.

[CONCURRENCY::auto_partitioner](../../parallel/concrt/reference/auto-partitioner-class.md)<br/>
Dzieli działają na początkową liczbę zakresów (zwykle liczba wątków roboczych, które są dostępne do pracy w pętli). Środowisko wykonawcze używa tego typu domyślnie podczas nie należy wywoływać metody przeciążone algorytmu równoległego, która przyjmuje `_Partitioner` parametru. Każdy z zakresów, mogą zostać podzielone na zakresy podrzędne, a tym samym umożliwia równoważenie obciążenia nastąpi. Po zakończeniu zakresu pracy, środowisko uruchomieniowe dystrybuuje zakresy podrzędne pracy od innych wątków do tego wątku. Użyj tego partycjonera, jeśli obciążenie nie znajduje się w jednej z innych kategorii, lub wymagasz pełnej obsługi anulowania lub blokowanie współpracy.

[CONCURRENCY::simple_partitioner](../../parallel/concrt/reference/simple-partitioner-class.md)<br/>
Dzieli działać do zakresów w taki sposób, że każdy z zakresów, ma co najmniej liczba iteracji, które są określone przez rozmiar danego fragmentu. Ten typ partycjonera uczestniczy w równoważeniu obciążenia; Jednakże środowisko wykonawcze nie podzielić zakresów zakresy podrzędne. Dla każdego pracownika, środowisko uruchomieniowe sprawdza, czy anulowania i przeprowadza równoważenia obciążenia po `_Chunk_size` ukończenia iteracji.

[CONCURRENCY::static_partitioner](../../parallel/concrt/reference/static-partitioner-class.md)<br/>
Dzieli działają na stałą liczbę zakresów (zwykle liczba wątków roboczych, które są dostępne do pracy w pętli). Ten typ partycjonera może poprawić wydajność, ponieważ nie korzysta z kradzież pracy i dlatego ma mniejszy narzut. Użyj tego typu partycjonera każdej iteracji pętli równoległej wykonuje stałych i jednolitego ilość pracy, i nie wymaga obsługi anulowania lub przekazywać blokowanie współpracy.

> [!WARNING]
>  `parallel_for_each` i `parallel_transform` algorytmy obsługi kontenerów, korzystających z iteratorami dostępu swobodnego (takich jak standardowe::[wektor](../../standard-library/vector-class.md)) dla partycjonery statyczne, prosty i koligacji. Korzystanie z kontenerów, które można dwukierunkową i tworzyć Iteratory do przodu generuje błąd w czasie kompilacji. Partycjonera domyślne, `auto_partitioner`, obsługuje wszystkie trzy typy iteratora.

Partycjonery te są zazwyczaj używane w taki sam sposób, z wyjątkiem `affinity_partitioner`. Większość typów partycjonera nie zarządzania stanem i nie są modyfikowane w czasie wykonywania. W związku z tym można utworzyć te obiekty partycjonera w witrynie wywołania, jak pokazano w poniższym przykładzie.

[!code-cpp[concrt-static-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_8.cpp)]

Jednakże, należy przekazać `affinity_partitioner` obiektu jako innej niż`const`, l wartości odwołują się tak, że algorytm może przechowywać stan dla przyszłych pętli, aby ponownie użyć. Poniższy przykład pokazuje Podstawowa aplikacja, która wykonuje tę samą operację na zestawie danych równolegle wiele razy. Korzystanie z `affinity_partitioner` może poprawić wydajność, ponieważ tablica jest prawdopodobne zmieścić ją w pamięci podręcznej.

[!code-cpp[concrt-affinity-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_9.cpp)]

> [!CAUTION]
>  Należy zachować ostrożność podczas modyfikowania istniejącego kodu, która zależy od współpracy blokowania semantyki do użycia `static_partitioner` lub `affinity_partitioner`. Te typy partycjonera nie używaj równoważenia obciążenia lub kradzież zakresu, a w związku z tym można zmieniać działanie aplikacji.

Najlepszym sposobem ustalenia, czy należy użyć partycjonera w dowolnym danym scenariuszu jest eksperymentowanie i zmierzyć czas potrzebny na zakończenie reprezentatywny obciążeń i konfiguracji komputerów operacji. Na przykład partycjonowania statycznego może zapewnić znaczne przyspieszenie na komputerze z wieloma procesorami ma tylko kilka rdzeni, ale może spowodować spowolnienie na komputerach, które mają względnie wiele rdzeni.

[[Górnej](#top)]

##  <a name="parallel_sorting"></a> Sortowanie równoległe

PPL zawiera trzy algorytmów sortowania: [concurrency::parallel_sort](reference/concurrency-namespace-functions.md#parallel_sort), [concurrency::parallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort), i [concurrency::parallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort). Algorytmy sortujące są przydatne w przypadku zestawu danych, który może być korzystne posortowana równolegle. W szczególności sortowanie równolegle jest przydatna, jeśli masz duży zestaw danych lub podczas używania operacji porównywania obliczeniowo kosztowne do sortowania danych. Każda z tych algorytmów sortowania elementów w miejscu.

`parallel_sort` i `parallel_buffered_sort` algorytmy są oba algorytmy na podstawie porównania. To znaczy służą do porównywania elementów przez wartość. `parallel_sort` Algorytmu nie ma dodatkowej pamięci wymagań i nadaje się do ogólnego przeznaczenia sortowania. `parallel_buffered_sort` Algorytm można wykonywać lepsze niż `parallel_sort`, ale wymaga O(N) miejsca.

`parallel_radixsort` Algorytm jest bazujących na skrótach. Oznacza to używa kluczy liczby całkowitej, aby posortować elementy. Przy użyciu kluczy, ten algorytm można bezpośrednio obliczeń docelowego elementu zamiast porównania. Podobnie jak `parallel_buffered_sort`, ten algorytm wymaga O(N) miejsca.

W poniższej tabeli podsumowano ważne właściwości trzy równoległych algorytmów sortowania.

|Algorytm|Opis|Mechanizm sortowania|Sortuj stabilności|Wymagania dotyczące pamięci|Złożoność czasu|Iterator dostępu|
|---------------|-----------------|-----------------------|--------------------|-------------------------|---------------------|---------------------|
|`parallel_sort`|Ogólnego przeznaczenia sortowania na podstawie porównania.|Na podstawie porównania (rosnąco)|Niestabilne|Brak|O((N/P)log(N/P) + 2N((P-1)/P))|losowe|
|`parallel_buffered_sort`|Szybsze ogólnego przeznaczenia na podstawie porównania sortowania, które wymaga O(N) miejsca.|Na podstawie porównania (rosnąco)|Niestabilne|Wymaga dodatkowego miejsca O(N)|O((N/P)log(N))|losowe|
|`parallel_radixsort`|Liczba całkowita opartego na kluczach sortowania, które wymaga O(N) miejsca.|Bazujących na skrótach|Wersja stabilna|Wymaga dodatkowego miejsca O(N)|O(N/P)|losowe|

Poniżej przedstawiono ważne właściwości trzy równoległych algorytmów sortowania bardziej graficznie.

![Porównanie algorytmów sortowania](../../parallel/concrt/media/concrt_parallel_sorting.png "concrt_parallel_sorting")

Te algorytmy sortujące równoległe zgodne z regułami anulowania i obsługi wyjątków. Aby uzyskać więcej informacji na temat anulowania i obsługi wyjątków w środowisku uruchomieniowym współbieżności: zobacz [anulowanie algorytmów równoległych](../../parallel/concrt/cancellation-in-the-ppl.md#algorithms) i [wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

> [!TIP]
>  Te algorytmy sortujące równoległe obsługują semantyki przenoszenia. Można zdefiniować operator przypisania przenoszenia, aby włączyć wymiany operacji wydajniej. Aby uzyskać więcej informacji dotyczących semantyki przenoszenia i operator przypisania przenoszenia, zobacz [Rvalue Reference Declarator: & &](../../cpp/rvalue-reference-declarator-amp-amp.md), i [konstruktory przenoszenia i operatory przenoszenia przypisania (C++)](../../cpp/move-constructors-and-move-assignment-operators-cpp.md). Jeśli nie podasz, operator przypisania przenoszenia lub funkcja zamiany, algorytmów sortowania użyć konstruktora kopiującego.

Poniższy przykład podstawowy pokazuje, jak używać `parallel_sort` sortowania `vector` z `int` wartości. Domyślnie `parallel_sort` używa [std::less](../../standard-library/less-struct.md) do porównywania wartości.

[!code-cpp[concrt-basic-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_10.cpp)]

Ten przykład przedstawia sposób udostępniania funkcji niestandardowych porównania. Używa ona [std::complex::real](../../standard-library/complex-class.md#real) metodę, aby posortować [wartość std::complex\<double >](../../standard-library/complex-double.md) wartości w kolejności rosnącej.

[!code-cpp[concrt-basic-parallel-sort#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_11.cpp)]

W tym przykładzie pokazano, jak zapewnić funkcji skrótu do `parallel_radixsort` algorytmu. W tym przykładzie sortuje 3-w punktach. Punkty są sortowane w oparciu o ich odległości od punktu odniesienia.

[!code-cpp[concrt-parallel-sort-points#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_12.cpp)]

Do celów informacyjnych w tym przykładzie użyto stosunkowo małego zestawu danych. Możesz zwiększyć rozmiar początkowy wektora eksperymentować ulepszenia wydajności za pośrednictwem większych zestawów danych.

W tym przykładzie używa wyrażenia lambda jako funkcji wyznaczania wartości skrótu. Można także użyć jednego z wbudowanych implementacji std::[hash, klasa](../../standard-library/hash-class.md) lub definiować własne specjalizacji. Umożliwia także niestandardowy obiekt funkcji mieszania, jak pokazano w poniższym przykładzie:

[!code-cpp[concrt-parallel-sort-points#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_13.cpp)]

[!code-cpp[concrt-parallel-sort-points#3](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_14.cpp)]

Funkcja wyznaczania wartości skrótu musi zwracać typ całkowity ([std::is_integral::value](../../standard-library/is-integral-class.md) musi być **true**). Ten typ całkowity musi być konwertowany na typ `size_t`.

###  <a name="choose_sort"></a> Wybieranie algorytmu sortowania

W wielu przypadkach `parallel_sort` zapewnia najlepszą równowagę pamięci i szybkości. Jednak, jak zwiększyć rozmiaru zestawu danych, liczba dostępnych procesorów lub złożoność funkcji porównywania, `parallel_buffered_sort` lub `parallel_radixsort` może działać lepiej. Najlepszym sposobem ustalenia, który algorytm sortowania do użycia w dowolnym danym scenariuszu jest eksperymentowanie i zmierzyć, jak długo trwa sortowanie typowych danych w ramach konfiguracji reprezentatywny komputerów. W przypadku wybrania strategii sortowania, należy pamiętać o następujących wytycznych.

- Rozmiar zestawu danych. W tym dokumencie *małych* zestaw danych zawiera mniej niż 1000 elementów *średni* zestaw danych zawiera 10 000 do 100 000 elementów, a *dużych* zestaw danych zawiera ponad 100 000 elementów.

- Ilość pracy, która wykonuje swoje porównania funkcji lub funkcji skrótu.

- Ilość dostępnych zasobów obliczeniowych.

- Właściwości zestawu danych. Na przykład jeden algorytm może działać dobrze w przypadku danych, które jest już prawie sortowana, ale także nie dla danych, które są całkowicie nieposortowana.

- Rozmiar fragmentu. Opcjonalny `_Chunk_size` argument określa, kiedy algorytm zmienia się z równoległego do implementacji serial sortowania zgodnie z jego dzieli ogólną sortowania na mniejsze jednostki pracy. Na przykład jeśli podasz 512, algorytm przełącza się na implementacji serial gdy jednostka pracy zawiera 512 lub mniejszej liczby elementów. Implementacja serial może zwiększyć ogólną wydajność, ponieważ eliminuje narzut, który jest wymagany do przetwarzania danych w sposób równoległy.

Może nie być zwiększonej sortowania małego zestawu danych w sposób równoległy, nawet wtedy, gdy masz dużą liczbę dostępnych zasobach komputerowych lub z porównania funkcji lub funkcji skrótu wykonuje stosunkowo dużej ilości pracy. Możesz użyć [std::sort](../../standard-library/algorithm-functions.md#sort) funkcję, aby posortować małych zestawów danych. (`parallel_sort` i `parallel_buffered_sort` wywołania `sort` podczas określania rozmiaru fragmentu, który jest większy od zestawu danych; jednak `parallel_buffered_sort` musiałaby przydzielanie O(N) miejsca, co może zająć więcej czasu z powodu blokady alokacji pamięci lub rywalizacji o zasoby.)

Jeśli musisz zachowywania pamięci lub usługi alokatora pamięci podlega Rywalizacja o blokady, użyj `parallel_sort` sortowanie zestawu danych średniej wielkości. `parallel_sort` wymaga nie dodatkowego miejsca; inne algorytmy wymagają O(N) miejsca.

Użyj `parallel_buffered_sort` sortowania średnie zestawów danych, a kiedy Twoja aplikacja spełnia dodatkowych wymagań dotyczących miejsca O(N). `parallel_buffered_sort` może być szczególnie przydatne, jeśli masz dużą liczbę zasobów obliczeniowych lub funkcja porównania kosztowne lub funkcji skrótu.

Użyj `parallel_radixsort` sortowania dużych zestawów danych, a kiedy Twoja aplikacja spełnia dodatkowych wymagań dotyczących miejsca O(N). `parallel_radixsort` może być szczególnie przydatne podczas operacji porównywania równoważne jest droższe, lub gdy obie operacje są kosztowne.

> [!CAUTION]
>  Implementacja funkcji skrótu dobrej wymaga, że znasz zakres zestawu danych i jak każdy element w zestawie danych jest przekształcana w odpowiedniej wartości bez znaku. Ponieważ operacja wyznaczania wartości skrótu działa z wartościami typu unsigned, należy wziąć pod uwagę innych strategii sortowania wartości bez znaku skrótu nie może zostać utworzony.

W poniższym przykładzie porównano wydajność `sort`, `parallel_sort`, `parallel_buffered_sort`, i `parallel_radixsort` względem tego samego zestawu dużych z losowymi danymi.

[!code-cpp[concrt-choosing-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_15.cpp)]

W tym przykładzie przyjęto założenie, że jest dopuszczalne przydzielanie O(N) miejsca podczas sortowania, `parallel_radixsort` działa najlepiej na ten zestaw danych w tej konfiguracji komputera.

[[Górnej](#top)]

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Instrukcje: pisanie pętli parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)|Ilustruje sposób używania `parallel_for` algorytm mnożenie macierzy.|
|[Instrukcje: pisanie pętli parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)|Ilustruje sposób używania `parallel_for_each` algorytm obliczania liczby liczb pierwszych w [std::array](../../standard-library/array-class-stl.md) obiektu równolegle.|
|[Instrukcje: używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Ilustruje sposób używania `parallel_invoke` algorytmu, aby zwiększyć wydajność algorytmu sortowania bitonicznego.|
|[Instrukcje: korzystanie z parallel_invoke podczas przeprowadzania operacji równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Ilustruje sposób używania `parallel_invoke` algorytmu, aby zwiększyć wydajność programu, który wykonuje wiele operacji na udostępnione źródło danych.|
|[Instrukcje: równoległe wykonywanie operacji mapowania i zmniejszania](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Ilustruje sposób używania `parallel_transform` i `parallel_reduce` algorytmy umożliwiające wykonywanie mapowania i zmniejszanie operacji, który zlicza wystąpienia słów w plikach.|
|[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|W tym artykule opisano PPL, która zapewnia model programowania na najwyższym skalowalność i łatwość użytkowania umożliwiający projektowanie aplikacji współbieżnych.|
|[Anulowanie w PPL](cancellation-in-the-ppl.md)|W tym artykule wyjaśniono roli anulowanie w PPL, jak anulować czynność równoległą i jak określić, kiedy grupy zadań zostanie anulowane.|
|[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|W tym artykule wyjaśniono roli Obsługa wyjątków w środowisku uruchomieniowym współbieżności.|

## <a name="reference"></a>Tematy pomocy

[parallel_for — funkcja](reference/concurrency-namespace-functions.md#parallel_for)

[parallel_for_each — funkcja](reference/concurrency-namespace-functions.md#parallel_for_each)

[parallel_invoke — funkcja](reference/concurrency-namespace-functions.md#parallel_invoke)

[affinity_partitioner, klasa](../../parallel/concrt/reference/affinity-partitioner-class.md)

[auto_partitioner, klasa](../../parallel/concrt/reference/auto-partitioner-class.md)

[simple_partitioner, klasa](../../parallel/concrt/reference/simple-partitioner-class.md)

[static_partitioner, klasa](../../parallel/concrt/reference/static-partitioner-class.md)

[parallel_sort — funkcja](reference/concurrency-namespace-functions.md#parallel_sort)

[parallel_buffered_sort — funkcja](reference/concurrency-namespace-functions.md#parallel_buffered_sort)

[parallel_radixsort Function](reference/concurrency-namespace-functions.md#parallel_radixsort)

