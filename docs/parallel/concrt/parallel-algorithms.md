---
title: Algorytmy równoległe
ms.date: 11/19/2018
helpviewer_keywords:
- parallel algorithms [Concurrency Runtime]
ms.assetid: 045dca7b-4d73-4558-a44c-383b88a28473
ms.openlocfilehash: a31787172c89e23e5eb32aa203b9f541584c0f68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363207"
---
# <a name="parallel-algorithms"></a>Algorytmy równoległe

Biblioteka wzorców równoległych (PPL) udostępnia algorytmy, które jednocześnie wykonują pracę nad kolekcjami danych. Algorytmy te przypominają algorytmy dostarczane przez standardową bibliotekę języka C++.

Algorytmy równoległe składają się z istniejących funkcji w współbieżności środowiska wykonawczego. Na przykład [współbieżność::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytm używa [współbieżności::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) obiektu do wykonywania iteracji pętli równoległej. Partycje `parallel_for` algorytmu działają w optymalny sposób, biorąc pod uwagę dostępną liczbę zasobów obliczeniowych.

## <a name="sections"></a><a name="top"></a>Sekcje

- [Algorytm parallel_for](#parallel_for)

- [Algorytm parallel_for_each](#parallel_for_each)

- [Algorytm parallel_invoke](#parallel_invoke)

- [Algorytmy parallel_transform i parallel_reduce](#parallel_transform_reduce)

  - [Algorytm parallel_transform](#parallel_transform)

  - [Algorytm parallel_reduce](#parallel_reduce)

  - [Przykład: Wykonywanie mapy i zmniejszanie równolegle](#map_reduce_example)

- [Praca partycjonowania](#partitions)

- [Sortowanie równoległe](#parallel_sorting)

  - [Wybieranie algorytmu sortowania](#choose_sort)

## <a name="the-parallel_for-algorithm"></a><a name="parallel_for"></a>Algorytm parallel_for

[Współbieżność::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytm wielokrotnie wykonuje to samo zadanie równolegle. Każde z tych zadań jest sparametryzowane przez wartość iteracji. Ten algorytm jest przydatny, gdy masz treść pętli, która nie udostępnia zasobów między iteracjami tej pętli.

Algorytm `parallel_for` dzieli zadania w optymalny sposób do wykonywania równoległego. Używa algorytmu kradzieży pracy i kradzieży zakresu, aby zrównoważyć te partycje, gdy obciążenia są niezrównoważone. Gdy jedna iteracja pętli blokuje się wspólnie, środowisko wykonawcze rozdziela zakres iteracji, który jest przypisany do bieżącego wątku do innych wątków lub procesorów. Podobnie, gdy wątek kończy zakres iteracji, środowisko wykonawcze rozdziela pracę z innych wątków do tego wątku. Algorytm `parallel_for` obsługuje również *zagnieżdżony równoległość*. Gdy jedna pętla równoległa zawiera inną pętlę równoległą, środowisko uruchomieniowe współrzędnych przetwarzania zasobów między treściami pętli w skuteczny sposób do wykonywania równoległego.

Algorytm `parallel_for` ma kilka przeciążonych wersji. Pierwsza wersja przyjmuje wartość początkową, wartość końcową i funkcję pracy (wyrażenie lambda, obiekt funkcyjny lub wskaźnik funkcji). Druga wersja przyjmuje wartość początkową, wartość końcową, wartość, o którą krok i funkcję pracy. Pierwsza wersja tej funkcji używa 1 jako wartości kroku. Pozostałe wersje wziąć partitioner obiektów, które `parallel_for` umożliwiają określenie, jak należy zakresy partycji między wątkami. Partitioners są wyjaśnione bardziej szczegółowo w sekcji [Partycjonowanie pracy](#partitions) w tym dokumencie.

Można przekonwertować `for` wiele `parallel_for`pętli do użycia . Jednak `parallel_for` algorytm różni się `for` od instrukcji w następujący sposób:

- Algorytm `parallel_for` `parallel_for` nie wykonuje zadań w wstępnie określonej kolejności.

- Algorytm `parallel_for` nie obsługuje dowolnych warunków zakończenia. Algorytm `parallel_for` zatrzymuje się, gdy bieżąca wartość zmiennej `last`iteracji jest o jeden mniejszy niż .

- Parametr `_Index_type` type musi być typem integralnym. Ten typ całka może być podpisany lub niepodpisany.

- Iteracja pętli musi być do przodu. Algorytm `parallel_for` zgłasza wyjątek typu [std::invalid_argument,](../../standard-library/invalid-argument-class.md) jeśli `_Step` parametr jest mniejszy niż 1.

- Mechanizm obsługi wyjątków `parallel_for` dla algorytmu różni `for` się od mechanizmu pętli. Jeśli wiele wyjątków występuje jednocześnie w treści pętli równoległej, środowisko wykonawcze propaguje `parallel_for`tylko jeden z wyjątków od wątku, który o nazwie . Ponadto gdy jedna iteracja pętli zgłasza wyjątek, środowisko wykonawcze nie natychmiast zatrzymuje ogólną pętlę. Zamiast tego pętla jest umieszczana w stanie anulowane i środowisko wykonawcze odrzuca wszystkie zadania, które nie zostały jeszcze uruchomione. Aby uzyskać więcej informacji na temat obsługi wyjątków i algorytmów równoległych, zobacz [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Mimo `parallel_for` że algorytm nie obsługuje dowolne warunki zakończenia, można użyć anulowania, aby zatrzymać wszystkie zadania. Aby uzyskać więcej informacji na temat anulowania, zobacz [Anulowanie w PPL](cancellation-in-the-ppl.md).

> [!NOTE]
> Koszt planowania, który wynika z równoważenia obciążenia i obsługi funkcji, takich jak anulowanie nie może przezwyciężyć korzyści z wykonywania treści pętli równolegle, zwłaszcza gdy treść pętli jest stosunkowo mała. Można zminimalizować to obciążenie przy użyciu partycjonowania w pętli równoległej. Aby uzyskać więcej informacji, zobacz [Partycjonowanie pracy](#partitions) w dalszej części tego dokumentu.

### <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono podstawową strukturę algorytmu. `parallel_for` W tym przykładzie drukuje do konsoli każdą wartość w zakresie [1, 5] równolegle.

[!code-cpp[concrt-parallel-for-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_1.cpp)]

W tym przykładzie przedstawiono następujące dane wyjściowe:

```Output
1 2 4 3 5
```

Ponieważ `parallel_for` algorytm działa na każdy element równolegle, kolejność, w której wartości są drukowane do konsoli będzie się różnić.

Aby uzyskać pełny przykład, `parallel_for` który używa algorytmu, zobacz [Jak: Napisz pętlę parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md).

[[Góra](#top)]

## <a name="the-parallel_for_each-algorithm"></a><a name="parallel_for_each"></a>Algorytm parallel_for_each

[Współbieżność::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytm wykonuje zadania w kontenerze iteracyjnym, takich jak te dostarczone przez bibliotekę standardową języka C++, równolegle. Używa tej samej logiki `parallel_for` partycjonowania, który używa algorytmu.

Algorytm `parallel_for_each` przypomina algorytm [std:::for_each](../../standard-library/algorithm-functions.md#for_each) biblioteki standardowej języka C++, z tą różnicą, `parallel_for_each` że algorytm wykonuje zadania jednocześnie. Podobnie jak inne `parallel_for_each` algorytmy równoległe, nie wykonuje zadań w określonej kolejności.

Mimo `parallel_for_each` że algorytm działa zarówno na iteratory przekazywania i iteratory dostępu losowego, działa lepiej z iteratorów dostępu losowego.

### <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono podstawową strukturę algorytmu. `parallel_for_each` W tym przykładzie można wydrukować do konsoli każdą wartość w [obiekcie std::array](../../standard-library/array-class-stl.md) równolegle.

[!code-cpp[concrt-parallel-for-each-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_2.cpp)]

W tym przykładzie przedstawiono następujące dane wyjściowe:

```Output
4 5 1 2 3
```

Ponieważ `parallel_for_each` algorytm działa na każdy element równolegle, kolejność, w której wartości są drukowane do konsoli będzie się różnić.

Aby uzyskać pełny przykład, `parallel_for_each` który używa algorytmu, zobacz [Jak: Napisz pętlę parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md).

[[Góra](#top)]

## <a name="the-parallel_invoke-algorithm"></a><a name="parallel_invoke"></a>Algorytm parallel_invoke

Algorytm [współbieżności::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) wykonuje zestaw zadań równolegle. Nie zwraca, dopóki każde zadanie zakończy. Ten algorytm jest przydatny, gdy masz kilka niezależnych zadań, które chcesz wykonać w tym samym czasie.

Algorytm `parallel_invoke` przyjmuje za swoje parametry serię funkcji roboczych (funkcje lambda, obiekty funkcyjne lub wskaźniki funkcji). Algorytm `parallel_invoke` jest przeciążony, aby wziąć od dwóch do dziesięciu parametrów. Każda funkcja, do `parallel_invoke` której przechodzisz, musi mieć parametry zerowe.

Podobnie jak inne `parallel_invoke` algorytmy równoległe, nie wykonuje zadań w określonej kolejności. W temacie [Równoległość](../../parallel/concrt/task-parallelism-concurrency-runtime.md) zadania `parallel_invoke` wyjaśnia, jak algorytm odnosi się do zadań i grup zadań.

### <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono podstawową strukturę algorytmu. `parallel_invoke` W tym przykładzie jednocześnie wywołuje `twice` funkcję na trzech zmiennych lokalnych i drukuje wynik do konsoli.

[!code-cpp[concrt-parallel-invoke-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_3.cpp)]

Ten przykład generuje następujące wyniki:

```Output
108 11.2 HelloHello
```

Aby uzyskać pełne przykłady, które używają algorytmu, `parallel_invoke` zobacz [Jak: Użyj parallel_invoke do zapisu procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) i [jak: Użyj parallel_invoke do wykonywania operacji równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md).

[[Góra](#top)]

## <a name="the-parallel_transform-and-parallel_reduce-algorithms"></a><a name="parallel_transform_reduce"></a>Algorytmy parallel_transform i parallel_reduce

[Współbieżność::parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) i [współbieżność::parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) algorytmy są równoległe wersje algorytmów biblioteki standardowej języka C++: [transform](../../standard-library/algorithm-functions.md#transform) i [std::accumulate](../../standard-library/numeric-functions.md#accumulate), odpowiednio. Wersje środowiska uruchomieniowego współbieżności zachowują się jak wersje biblioteki standardowej języka C++, z tą różnicą, że kolejność operacji nie jest określana, ponieważ są wykonywane równolegle. Użyj tych algorytmów podczas pracy z zestawem, który jest wystarczająco duży, aby uzyskać korzyści wydajności i skalowalności z przetwarzania równolegle.

> [!IMPORTANT]
> `parallel_transform` Algorytmy `parallel_reduce` i obsługuje tylko losowy dostęp, dwukierunkowe i dalej iteratory, ponieważ te iteratory produkcji stabilne adresy pamięci. Ponadto te iteratory muszą produkować wartości inne niż`const` l.

### <a name="the-parallel_transform-algorithm"></a><a name="parallel_transform"></a>Algorytm parallel_transform

Algorytmu można `parallel transform` użyć do wykonywania wielu operacji równoległości danych. Można na przykład:

- Dostosuj jasność obrazu i wykonaj inne operacje przetwarzania obrazu.

- Zsumuj lub weź produkt kropki między dwoma wektorami i wykonaj inne obliczenia liczbowe na wektorach.

- Wykonaj śledzenie promieni 3-W, gdzie każda iteracja odwołuje się do jednego piksela, który musi być renderowany.

Poniższy przykład przedstawia podstawową strukturę, `parallel_transform` która jest używana do wywoływania algorytmu. W tym przykładzie neguje każdy element obiektu std::[wektor na](../../standard-library/vector-class.md) dwa sposoby. Pierwszy sposób używa wyrażenia lambda. Drugi sposób używa [std::neggate](../../standard-library/negate-struct.md), który pochodzi z [std::unary_function](../../standard-library/unary-function-struct.md).

[!code-cpp[concrt-basic-parallel-transform#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_4.cpp)]

> [!WARNING]
> W tym przykładzie pokazano `parallel_transform`podstawowe zastosowanie programu . Ponieważ funkcja pracy nie wykonuje znaczną ilość pracy, znaczny wzrost wydajności nie jest oczekiwany w tym przykładzie.

Algorytm `parallel_transform` ma dwa przeciążenia. Pierwsze przeciążenie zajmuje jeden zakres wejściowy i funkcję jednozakresową. Funkcja jednoarysyjna może być wyrażeniem lambda, które przyjmuje jeden argument, `unary_function`obiekt funkcji lub typ, który wywodzi się od . Drugie przeciążenie zajmuje dwa zakresy wejściowe i funkcję binarną. Funkcja binarna może być wyrażeniem lambda, które przyjmuje dwa argumenty, obiekt funkcji lub typ, który wywodzi się z [std::binary_function](../../standard-library/binary-function-struct.md). Poniższy przykład ilustruje te różnice.

[!code-cpp[concrt-parallel-transform-vectors#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_5.cpp)]

> [!IMPORTANT]
> Iterator, który można podać `parallel_transform` dla danych wyjściowych musi całkowicie pokrywać się z iteratora wejściowego lub nie nakładają się w ogóle. Zachowanie tego algorytmu jest nieokreślony, jeśli iteratory danych wejściowych i wyjściowych częściowo nakładają się na siebie.

### <a name="the-parallel_reduce-algorithm"></a><a name="parallel_reduce"></a>Algorytm parallel_reduce

Algorytm `parallel_reduce` jest przydatny, gdy masz sekwencję operacji, które spełniają właściwości asowiązkowej. (Ten algorytm nie wymaga właściwości przemienny.) Oto niektóre z operacji, które `parallel_reduce`można wykonać za pomocą:

- Pomnóż sekwencje macierzy, aby utworzyć macierz.

- Mnożyć wektor przez sekwencję macierzy do produkcji wektora.

- Oblicz długość sekwencji ciągów.

- Połącz listę elementów, takich jak ciągi, w jeden element.

W poniższym przykładzie podstawowym `parallel_reduce` pokazano, jak użyć algorytmu, aby połączyć sekwencję ciągów w jeden ciąg. Podobnie jak w `parallel_transform`przypadku przykładów , wzrost wydajności nie są oczekiwane w tym podstawowym przykładzie.

[!code-cpp[concrt-basic-parallel-reduce#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_6.cpp)]

W wielu przypadkach można `parallel_reduce` myśleć jako skrót do `parallel_for_each` korzystania z algorytmu wraz z [współbieżności::combinable](../../parallel/concrt/reference/combinable-class.md) klasy.

### <a name="example-performing-map-and-reduce-in-parallel"></a><a name="map_reduce_example"></a>Przykład: Wykonywanie mapy i zmniejszanie równolegle

Operacja *mapy* stosuje funkcję do każdej wartości w sekwencji. Operacja *reduce* łączy elementy sekwencji w jedną wartość. Za pomocą biblioteki standardowej języka C++ [std::transform](../../standard-library/algorithm-functions.md#transform) i [std::accumulate](../../standard-library/numeric-functions.md#accumulate) można wykonywać operacje mapowania i redukować. Jednak w przypadku wielu problemów `parallel_transform` można użyć algorytmu do wykonywania `parallel_reduce` operacji mapy równolegle i algorytm wykonać operację reduce równolegle.

W poniższym przykładzie porównano czas potrzebny do obliczenia sumy liczb pierwszych szeregowo i równolegle. Faza mapy przekształca wartości nie prime na 0, a faza redukcji sumuje wartości.

[!code-cpp[concrt-parallel-map-reduce-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_7.cpp)]

Inny przykład, który wykonuje mapę i zmniejsza działanie równolegle, zobacz [Jak: Wykonywanie map i zmniejszanie operacji równolegle](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

[[Góra](#top)]

## <a name="partitioning-work"></a><a name="partitions"></a>Praca partycjonowania

Aby zrównać operację ze źródłem danych, istotnym krokiem jest *partycjonowanie* źródła na wiele sekcji, do których można uzyskać dostęp jednocześnie przez wiele wątków. Partycjoner określa, jak algorytm równoległy powinien podzielić zakresy między wątkami. Jak wyjaśniono wcześniej w tym dokumencie, PPL używa domyślnego mechanizmu partycjonowania, który tworzy początkowe obciążenie, a następnie używa algorytmu kradzieży pracy i kradzieży zakresu, aby zrównoważyć te partycje, gdy obciążenia są niezrównoważone. Na przykład gdy jedna iteracja pętli kończy zakres iteracji, środowisko wykonawcze rozdziela pracę z innych wątków do tego wątku. Jednak w niektórych scenariuszach można określić inny mechanizm partycjonowania, który jest lepiej dostosowany do problemu.

`parallel_for`Algorytmy `parallel_for_each`i `parallel_transform` algorytmy zapewniają przeciążone wersje, `_Partitioner`które przyjmują dodatkowy parametr. Ten parametr definiuje typ partycjonowania, który dzieli pracę. Oto rodzaje partycjonowania, które definiuje PPL:

[współbieżność::affinity_partitioner](../../parallel/concrt/reference/affinity-partitioner-class.md)<br/>
Dzieli pracę na stałą liczbę zakresów (zazwyczaj liczbę wątków roboczych, które są dostępne do pracy w pętli). Ten typ partycjonowania przypomina `static_partitioner`, ale poprawia koligacji pamięci podręcznej przez sposób mapuje zakresy do wątków roboczych. Ten typ partycjonowania może zwiększyć wydajność, gdy pętla jest wykonywana za pośrednictwem tego samego zestawu danych wiele razy (na przykład pętli w pętli) i dane mieści się w pamięci podręcznej. Ten partycjoner nie w pełni uczestniczyć w anulowaniu. Nie używa również semantyki blokowania współpracy i dlatego nie można używać z równoległymi pętlami, które mają zależność do przodu.

[współbieżność::auto_partitioner](../../parallel/concrt/reference/auto-partitioner-class.md)<br/>
Dzieli pracę na początkową liczbę zakresów (zazwyczaj liczbę wątków roboczych, które są dostępne do pracy w pętli). Środowisko wykonawcze używa tego typu domyślnie, gdy nie wywołasz przeciążony algorytm równoległy, który przyjmuje `_Partitioner` parametr. Każdy zakres można podzielić na podzakresy, a tym samym umożliwia równoważenie obciążenia. Po zakończeniu zakresu pracy środowisko wykonawcze rozdziela podzakresy pracy z innych wątków do tego wątku. Użyj tego partycjonowania, jeśli obciążenie nie należy do jednej z innych kategorii lub wymagana jest pełna obsługa anulowania lub blokowania współpracy.

[współbieżność::simple_partitioner](../../parallel/concrt/reference/simple-partitioner-class.md)<br/>
Dzieli pracy na zakresy takie, że każdy zakres ma co najmniej liczbę iteracji, które są określone przez danego rozmiaru fragmentu. Ten typ partycjonowania uczestniczy w równoważeniu obciążenia; jednak środowisko wykonawcze nie dzieli zakresów na podzakresy. Dla każdego procesu roboczego środowisko wykonawcze sprawdza anulowanie `_Chunk_size` i wykonuje równoważenie obciążenia po zakończeniu iteracji.

[współbieżność::static_partitioner](../../parallel/concrt/reference/static-partitioner-class.md)<br/>
Dzieli pracę na stałą liczbę zakresów (zazwyczaj liczbę wątków roboczych, które są dostępne do pracy w pętli). Ten typ partycjonowania może zwiększyć wydajność, ponieważ nie używa kradzieży pracy i dlatego ma mniej narzutów. Użyj tego typu partycjonowania, gdy każda iteracja pętli równoległej wykonuje stałą i jednolitą ilość pracy i nie wymaga wsparcia dla anulowania lub przekazywania blokowania współpracy.

> [!WARNING]
> `parallel_for_each` Algorytmy `parallel_transform` i obsługują tylko kontenery, które używają iteratorów dostępu losowego (takich jak std::[vector)](../../standard-library/vector-class.md)dla partycjonowania statycznego, prostego i koligacji. Użycie kontenerów, które używają dwukierunkowych i do przodu iteratorów powoduje błąd w czasie kompilacji. Domyślny partycjoner, `auto_partitioner`obsługuje wszystkie trzy z tych typów iteratora.

Zazwyczaj te partycjonowania są używane w ten `affinity_partitioner`sam sposób, z wyjątkiem . Większość typów partycjonowania nie zachowują stanu i nie są modyfikowane przez środowisko wykonawcze. W związku z tym można utworzyć te obiekty partycjonowania w witrynie wywołania, jak pokazano w poniższym przykładzie.

[!code-cpp[concrt-static-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_8.cpp)]

Jednak należy przekazać `affinity_partitioner` obiekt jako odwołanie`const`non- , l-value, tak aby algorytm może przechowywać stan dla przyszłych pętli do ponownego użycia. W poniższym przykładzie przedstawiono podstawową aplikację, która wykonuje tę samą operację na zestawie danych równolegle wiele razy. Użycie `affinity_partitioner` może zwiększyć wydajność, ponieważ tablica może zmieścić się w pamięci podręcznej.

[!code-cpp[concrt-affinity-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_9.cpp)]

> [!CAUTION]
> Należy zachować ostrożność podczas modyfikowania istniejącego kodu, który `static_partitioner` `affinity_partitioner`opiera się na współpracy blokowania semantyki do użycia lub . Te typy partycjonowania nie używają równoważenia obciążenia lub kradzieży zakresu i dlatego można zmienić zachowanie aplikacji.

Najlepszym sposobem, aby ustalić, czy używać partycjonowania w danym scenariuszu jest do eksperymentowania i pomiaru, jak długo trwa operacje, aby zakończyć w ramach reprezentatywnych obciążeń i konfiguracji komputera. Na przykład partycjonowanie statyczne może zapewnić znaczne przyspieszenie na komputerze wielordzeniowym, który ma tylko kilka rdzeni, ale może spowodować spowolnienie na komputerach, które mają stosunkowo wiele rdzeni.

[[Góra](#top)]

## <a name="parallel-sorting"></a><a name="parallel_sorting"></a>Sortowanie równoległe

PPL zawiera trzy algorytmy sortowania: [współbieżność::parallel_sort](reference/concurrency-namespace-functions.md#parallel_sort), [współbieżność::parallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort)i [współbieżność::parallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort). Te algorytmy sortowania są przydatne, gdy masz zestaw danych, które mogą korzystać z sortowania równolegle. W szczególności sortowanie równolegle jest przydatne, gdy masz duży zestaw danych lub gdy używasz operacji porównywania kosztownej obliczeniowo do sortowania danych. Każdy z tych algorytmów sortuje elementy w miejscu.

`parallel_sort` Algorytmy `parallel_buffered_sort` i są zarówno algorytmy oparte na porównaniu. Oznacza to, że porównują elementy według wartości. Algorytm `parallel_sort` nie ma dodatkowych wymagań dotyczących pamięci i nadaje się do sortowania ogólnego przeznaczenia. Algorytm `parallel_buffered_sort` może działać `parallel_sort`lepiej niż , ale wymaga miejsca O(N).

Algorytm `parallel_radixsort` jest oparty na skrótach. Oznacza to, że używa kluczy całkowitych do sortowania elementów. Za pomocą kluczy, ten algorytm można bezpośrednio obliczyć miejsce docelowe elementu zamiast przy użyciu porównań. Podobnie `parallel_buffered_sort`jak , ten algorytm wymaga miejsca O(N).

W poniższej tabeli podsumowano ważne właściwości trzech algorytmów sortowania równoległego.

|Algorytm|Opis|Mechanizm sortowania|Stabilność sortowania|Wymagania dotyczące pamięci|Złożoność czasu|Dostęp do iteratora|
|---------------|-----------------|-----------------------|--------------------|-------------------------|---------------------|---------------------|
|`parallel_sort`|Sortowanie oparte na porównaniu ogólnego przeznaczenia.|Oparte na porównaniu (rosnąco)|Niestabilny|Brak|O((N/P)log(N/P) + 2N((P-1)/P))|Losowe|
|`parallel_buffered_sort`|Szybsze sortowanie oparte na porównaniu ogólnego przeznaczenia, które wymaga miejsca O(N).|Oparte na porównaniu (rosnąco)|Niestabilny|Wymaga dodatkowego miejsca O(N)|O((N/P)log(N))|Losowe|
|`parallel_radixsort`|Sortowanie oparte na kluczu całkowitym, które wymaga miejsca O(N).|Oparte na skrótach|Stable|Wymaga dodatkowego miejsca O(N)|O(N/P)|Losowe|

Na poniższej ilustracji przedstawiono ważne właściwości trzech algorytmów sortowania równoległego bardziej graficznie.

![Porównanie algorytmów sortowania](../../parallel/concrt/media/concrt_parallel_sorting.png "Porównanie algorytmów sortowania")

Te algorytmy sortowania równoległego są zgodne z regułami anulowania i obsługi wyjątków. Aby uzyskać więcej informacji na temat anulowania i obsługi wyjątków w czasie wykonywania współbieżności, zobacz [Anulowanie algorytmów równoległych](../../parallel/concrt/cancellation-in-the-ppl.md#algorithms) i [obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

> [!TIP]
> Te algorytmy sortowania równoległego obsługują semantyki przenoszenia. Można zdefiniować operator przypisania przenoszenia, aby umożliwić bardziej efektywne działanie operacji wymiany. Aby uzyskać więcej informacji na temat semantyki przenoszenia i operatora przypisania [przenoszenia, zobacz Deklarator odwołania Rvalue: &&](../../cpp/rvalue-reference-declarator-amp-amp.md), i [Przenieś konstruktory i operatory przenoszenia przydziałów (C++)](../../cpp/move-constructors-and-move-assignment-operators-cpp.md). Jeśli nie podasz operatora przypisania przenoszenia lub funkcji wymiany, algorytmy sortowania używają konstruktora kopiowania.

W poniższym przykładzie `parallel_sort` podstawowym pokazano, jak używać do sortowania `vector` `int` wartości. Domyślnie `parallel_sort` do porównywania wartości używa [std::less.](../../standard-library/less-struct.md)

[!code-cpp[concrt-basic-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_10.cpp)]

W tym przykładzie pokazano, jak podać funkcję porównania niestandardowego. Używa [std::complex::real](../../standard-library/complex-class.md#real) metoda sortowania [std::complex\<double>](../../standard-library/complex-double.md) wartości w porządku rosnącym.

[!code-cpp[concrt-basic-parallel-sort#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_11.cpp)]

W tym przykładzie pokazano, jak `parallel_radixsort` podać funkcję mieszania do algorytmu. W tym przykładzie sortuje punkty 3-W. Punkty są sortowane na podstawie ich odległości od punktu odniesienia.

[!code-cpp[concrt-parallel-sort-points#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_12.cpp)]

Na ilustracji w tym przykładzie użyto stosunkowo mały zestaw danych. Można zwiększyć początkowy rozmiar wektora, aby eksperymentować z poprawą wydajności w większych zestawach danych.

W tym przykładzie użyto wyrażenia lambda jako funkcji mieszania. Można również użyć jednej z wbudowanych implementacji klasy[skrótu](../../standard-library/hash-class.md) std:: lub zdefiniować własną specjalizację. Można również użyć niestandardowego obiektu funkcji mieszania, jak pokazano w tym przykładzie:

[!code-cpp[concrt-parallel-sort-points#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_13.cpp)]

[!code-cpp[concrt-parallel-sort-points#3](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_14.cpp)]

Funkcja mieszania musi zwracać typ integralny ([std::is_integral::value](../../standard-library/is-integral-class.md) must be **true**). Ten typ integralny musi `size_t`być konwertowany na typ .

### <a name="choosing-a-sorting-algorithm"></a><a name="choose_sort"></a>Wybieranie algorytmu sortowania

W wielu `parallel_sort` przypadkach zapewnia najlepszą równowagę między szybkością i wydajnością pamięci. Jednak w miarę zwiększania rozmiaru zestawu danych, liczby dostępnych procesorów lub złożoności `parallel_buffered_sort` `parallel_radixsort` funkcji porównywania lub może działać lepiej. Najlepszym sposobem określenia, który algorytm sortowania ma być używany w danym scenariuszu, jest eksperymentowanie i mierzenie czasu sortowania typowych danych w reprezentatywnych konfiguracjach komputerów. Podczas wybierania strategii sortowania należy pamiętać o poniższych wskazówkach.

- Rozmiar zestawu danych. W tym dokumencie *mały* zestaw danych zawiera mniej niż 1000 elementów, *średni* zestaw danych zawiera między 10 000 a 100 000 elementów, a *duży* zestaw danych zawiera ponad 100 000 elementów.

- Ilość pracy wykonywanej przez funkcję porównywania lub funkcję mieszania.

- Ilość dostępnych zasobów obliczeniowych.

- Charakterystyka zestawu danych. Na przykład jeden algorytm może działać dobrze dla danych, które są już prawie posortowane, ale nie tak dobrze dla danych, które są całkowicie niesegregowane.

- Rozmiar fragmentu. Opcjonalny `_Chunk_size` argument określa, kiedy algorytm przełącza się z implementacji sortowania równoległego do szeregowego, ponieważ dzieli ogólny sortowanie na mniejsze jednostki pracy. Na przykład jeśli podasz 512, algorytm przełącza się do implementacji szeregowej, gdy jednostka pracy zawiera 512 lub mniej elementów. Implementacja szeregowa może poprawić ogólną wydajność, ponieważ eliminuje obciążenie, które jest wymagane do przetwarzania danych równolegle.

Sortowanie małego zestawu danych równolegle może nie być konieczne, nawet jeśli masz dużą liczbę dostępnych zasobów obliczeniowych lub funkcja porównywania lub funkcja mieszania wykonuje stosunkowo dużą ilość pracy. Do sortowania małych zestawów danych można użyć funkcji [std::sort.](../../standard-library/algorithm-functions.md#sort) (`parallel_sort` `parallel_buffered_sort` i `sort` wywołać po określeniu rozmiaru fragmentu, `parallel_buffered_sort` który jest większy niż zestaw danych; jednak musiałby przydzielić miejsce O(N), co może zająć dodatkowy czas ze względu na rywalizację blokady lub alokacji pamięci.)

Jeśli należy oszczędzać pamięć lub alokator pamięci podlega rywalizacji blokady, użyj `parallel_sort` do sortowania średniej wielkości zestawu danych. `parallel_sort`nie wymaga dodatkowej przestrzeni; inne algorytmy wymagają miejsca O(N).

Służy `parallel_buffered_sort` do sortowania średnich zestawów danych i gdy aplikacja spełnia dodatkowe wymagania dotyczące miejsca O(N). `parallel_buffered_sort`może być szczególnie przydatne, gdy masz dużą liczbę zasobów obliczeniowych lub kosztowne funkcji porównania lub funkcji mieszania.

Służy `parallel_radixsort` do sortowania dużych zestawów danych i gdy aplikacja spełnia dodatkowe wymagania dotyczące miejsca O(N). `parallel_radixsort`może być szczególnie przydatne, gdy równoważne porównanie operacji jest droższe lub gdy obie operacje są drogie.

> [!CAUTION]
> Implementowanie dobrej funkcji mieszania wymaga znać zakres zestawu danych i jak każdy element w zestawie danych jest przekształcany do odpowiedniej wartości niepodpisanej. Ponieważ operacja mieszania działa na niepodpisanych wartości, należy wziąć pod uwagę inną strategię sortowania, jeśli niepodpisane wartości skrótu nie mogą być produkowane.

W poniższym przykładzie `sort`porównano `parallel_buffered_sort`wydajność `parallel_radixsort` , `parallel_sort`, i z tym samym dużym zestawem danych losowych.

[!code-cpp[concrt-choosing-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_15.cpp)]

W tym przykładzie, który zakłada, że jest dopuszczalne przydzielić `parallel_radixsort` miejsce O(N) podczas sortowania, wykonuje najlepsze w tym zestawie danych w tej konfiguracji komputera.

[[Góra](#top)]

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Porady: pisanie pętli parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)|Pokazuje, jak `parallel_for` używać algorytmu do wykonywania mnożenia macierzy.|
|[Instrukcje: pisanie pętli parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)|Pokazuje, jak `parallel_for_each` używać algorytmu do obliczania liczby liczb pierwszych w [obiekcie std::array](../../standard-library/array-class-stl.md) równolegle.|
|[Porady: używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Pokazuje, jak `parallel_invoke` używać algorytmu, aby poprawić wydajność algorytmu sortowania bitonic.|
|[Jak: Użyj parallel_invoke do wykonywania operacji równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Pokazuje, jak `parallel_invoke` użyć algorytmu, aby zwiększyć wydajność programu, który wykonuje wiele operacji na udostępnionym źródle danych.|
|[Instrukcje: równoległe wykonywanie operacji mapowania i zmniejszania](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Pokazuje, jak `parallel_transform` używać `parallel_reduce` algorytmów i do wykonywania mapy i zmniejszyć operację, która zlicza wystąpienia słów w plikach.|
|[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|W tym artykule opisano PPL, który zapewnia imperatywne model programowania, który promuje skalowalność i łatwość użycia do tworzenia równoczesnych aplikacji.|
|[Anulowanie w PPL](cancellation-in-the-ppl.md)|W tym artykule wyjaśniono rolę anulowania w PPL, jak anulować pracę równoległą i jak określić, kiedy grupa zadań zostanie anulowana.|
|[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Wyjaśniono rolę obsługi wyjątków w czasie wykonywania współbieżności.|

## <a name="reference"></a>Dokumentacja

[Funkcja parallel_for](reference/concurrency-namespace-functions.md#parallel_for)

[Funkcja parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)

[Funkcja parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)

[affinity_partitioner, klasa](../../parallel/concrt/reference/affinity-partitioner-class.md)

[auto_partitioner, klasa](../../parallel/concrt/reference/auto-partitioner-class.md)

[simple_partitioner, klasa](../../parallel/concrt/reference/simple-partitioner-class.md)

[static_partitioner, klasa](../../parallel/concrt/reference/static-partitioner-class.md)

[Funkcja parallel_sort](reference/concurrency-namespace-functions.md#parallel_sort)

[Funkcja parallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort)

[Funkcja parallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort)
