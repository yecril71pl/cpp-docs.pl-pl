---
title: Algorytmy równoległe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parallel algorithms [Concurrency Runtime]
ms.assetid: 045dca7b-4d73-4558-a44c-383b88a28473
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 365acd15c61b52631fc75018ab4c3a017d3eed8f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="parallel-algorithms"></a>Algorytmy równoległe
Biblioteka równoległych wzorców (PLL) zapewnia algorytmów jednocześnie wykonywania pracy na kolekcji danych. Algorytmy te przypominają te udostępniane przez standardowa biblioteka C++.  
  

 Algorytmy równoległe składają się z istniejące funkcje współbieżność środowiska wykonawczego. Na przykład [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytm używa [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) obiektu w celu wykonania iteracji pętli równoległej. `parallel_for` Partycje algorytm pracy w optymalny sposób podana liczba dostępnych zasobów obliczeniowych.  

  
##  <a name="top"></a> Sekcje  
  
- [Parallel_for algorytmu](#parallel_for)  
  
- [Parallel_for_each — algorytm](#parallel_for_each)  
  
- [Parallel_invoke — algorytm](#parallel_invoke)  
  
- [Parallel_transform — i parallel_reduce — algorytmów](#parallel_transform_reduce)  
  
    - [Parallel_transform — algorytm](#parallel_transform)  
  
    - [Parallel_reduce — algorytm](#parallel_reduce)  
  
    - [Przykład: Wykonywanie mapowania i zmniejszyć równolegle](#map_reduce_example)  
  
- [Podziału pracy](#partitions)  
  
- [Sortowania równoległego](#parallel_sorting)  
  
    - [Wybieranie algorytmu sortowania](#choose_sort)  
  
##  <a name="parallel_for"></a> Parallel_for algorytmu  

 [Concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytm wielokrotnie wykonuje to samo zadanie równocześnie. Każdy z tych zadań jest sparametryzowanych przez wartość iteracji. Ten algorytm jest przydatne w przypadku treści pętli, która nie współużytkowanie zasobów między iteracji pętli tego.  
  
 `parallel_for` Algorytmu partycje zadania w sposób optymalny do wykonywania równoległego. Używa algorytmu kradzież pracy się i zakres kradzież w celu zrównoważenia tych partycji w przypadku obciążeń równowagi. Po jednym iteracji pętli blokuje wspólnie, środowisko uruchomieniowe ponownie dystrybuuje zakres iteracji, który jest przypisany do bieżącego wątku do innych wątków lub procesorów. Podobnie po ukończeniu zakres iteracji wątku środowiska uruchomieniowego ponownie dystrybuuje pracy z innych wątków tego wątku. `parallel_for` Obsługuje również algorytmu *zagnieżdżone równoległości*. Gdy równoległej pętli zawiera inny równoległej pętli, środowisko uruchomieniowe koordynuje przetwarzania zasobów między treści pętli w wydajny sposób do wykonywania równoległego.  
  
 `parallel_for` Algorytm ma kilka wersji przeciążona. Pierwszą wersję przyjmuje wartość początkową, wartość końcowa i funkcję pracy (wyrażenia lambda, funkcja obiekt lub wskaźnik funkcji). Druga wersja przyjmuje wartość początkową, wartość końcowa wartość za pomocą którego kroku, a funkcja pracy. Pierwszą wersję tej funkcji używa 1 jako wartość kroku. Pozostałych wersji zająć partycjonera obiektów, które można określić sposób `parallel_for` powinien partycji zakresów między wątkami. Partycjonery omówiono bardziej szczegółowo w sekcji [pracy partycjonowania](#partitions) w tym dokumencie.  
  
 Można przekonwertować wiele `for` pętli do użycia `parallel_for`. Jednak `parallel_for` algorytm różni się od `for` instrukcji w następujący sposób:  
  
-   `parallel_for` Algorytm `parallel_for` nie wykonuj zadania w ustalonej kolejności.  
  
-   `parallel_for` Algorytm nie obsługuje warunków zakończenia dowolnego. `parallel_for` Zatrzymuje algorytmu, gdy bieżąca wartość zmiennej iteracyjnej jest jeden mniej niż `last`.  
  
-   `_Index_type` Parametr typu musi być typem całkowitym. Ten typ całkowity może podpisane lub bez znaku.  
  
-   Iteracji pętli musi być do przodu. `parallel_for` Algorytm zgłasza wyjątek typu [std::invalid_argument](../../standard-library/invalid-argument-class.md) Jeśli `_Step` parametru jest mniejszy niż 1.  
  
-   Mechanizm obsługi wyjątków `parallel_for` algorytm różni się od `for` pętli. Jeśli wiele wyjątków jednocześnie występować w treści pętli równoległej, środowisko uruchomieniowe propaguje tylko jeden z wyjątków wątku, który wywołuje `parallel_for`. Ponadto po jednym iteracji pętli zgłasza wyjątek, środowisko uruchomieniowe nie natychmiast zatrzymać ogólną pętli. Zamiast tego pętli znajduje się w stanie anulowania i środowiska uruchomieniowego odrzuca wszystkie zadania, które nie zostały jeszcze uruchomione. Aby uzyskać więcej informacji na temat algorytmy Obsługa wyjątków i równoległych zobacz [obsługi wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
 Mimo że `parallel_for` algorytm nie obsługuje warunków zakończenia dowolnego, użyj anulowania, aby zatrzymać wszystkie zadania. Aby uzyskać więcej informacji na temat anulowania, zobacz [anulowanie w PPL](cancellation-in-the-ppl.md).  
  
> [!NOTE]
>  Koszt planowania, że wyniki z równoważenia obciążenia i obsługę funkcji, takich jak anulowania nie może rozwiązać zalet wykonywania pętli równolegle, szczególnie gdy pętli jest stosunkowo mały. Ten narzut można zminimalizować przy użyciu partycjonera w Twojej równoległej pętli. Aby uzyskać więcej informacji, zobacz [pracy partycjonowania](#partitions) dalszej części tego dokumentu.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono podstawowej struktury `parallel_for` algorytmu. W tym przykładzie drukowane konsoli każdej wartości z zakresu [1, 5] równolegle.  
  
 [!code-cpp[concrt-parallel-for-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_1.cpp)]  
  
 W tym przykładzie tworzy następujące przykładowe dane wyjściowe:  
  
```Output  
1 2 4 3 5  
```  
  
 Ponieważ `parallel_for` algorytm działania w przypadku każdego elementu równolegle, różnią się w kolejności, w której wartości są podane w konsoli.  
  
 Pełny przykład, który używa `parallel_for` algorytmu, zobacz [porady: pisanie pętli parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md).  
  
 [[Górnej](#top)]  
  
##  <a name="parallel_for_each"></a> Parallel_for_each — algorytm  

 [Concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytm wykonuje zadania w kontenerze iteracyjną, np. udostępnianych przez bibliotekę Standard C++ równolegle. Używa tej samej logiki partycjonowania który `parallel_for` algorytm.  
  
 `parallel_for_each` Algorytm podobny standardowa biblioteka C++ [std::for_each](../../standard-library/algorithm-functions.md#for_each) algorytmu, z wyjątkiem `parallel_for_each` algorytm wykonuje zadań jednocześnie. Inne algorytmy równoległe, takich jak `parallel_for_each` nie wykonuj zadania w określonej kolejności.  
  
 Mimo że `parallel_for_each` algorytm działa zarówno do przodu Iteratory i dostępie swobodnym Iteratory, lepiej wykonuje się o dostępie swobodnym Iteratory.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono podstawowej struktury `parallel_for_each` algorytmu. W tym przykładzie drukowane konsoli każdej wartości w [std::array](../../standard-library/array-class-stl.md) obiektu równolegle.  
  
 [!code-cpp[concrt-parallel-for-each-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_2.cpp)]  
  
 W tym przykładzie tworzy następujące przykładowe dane wyjściowe:  
  
```Output  
4 5 1 2 3  
```  
  
 Ponieważ `parallel_for_each` algorytm działania w przypadku każdego elementu równolegle, różnią się w kolejności, w której wartości są podane w konsoli.  
  
 Pełny przykład, który używa `parallel_for_each` algorytmu, zobacz [porady: pisanie pętli parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md).  
  
 [[Górnej](#top)]  
  
##  <a name="parallel_invoke"></a> Parallel_invoke — algorytm  

 [Concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytm wykonuje zestaw zadań równolegle. Zwraca przed zakończeniem każdego zadania. Ten algorytm jest przydatne w przypadku kilku niezależnych zadania, które ma być wykonane w tym samym czasie.  
  
 `parallel_invoke` Algorytmu przyjmuje jako parametry szereg funkcji pracy (funkcje lambda, obiektów funkcji lub wskaźników funkcji). `parallel_invoke` Algorytm jest przeciążony podjęcie między dwoma i dziesięć parametrami. Każda funkcja, który jest przekazywany do `parallel_invoke` musi mieć parametrów.  
  
 Inne algorytmy równoległe, takich jak `parallel_invoke` nie wykonuj zadania w określonej kolejności. Temat [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md) wyjaśniono sposób `parallel_invoke` algorytm odnosi się do zadań i grupy zadań.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono podstawowej struktury `parallel_invoke` algorytmu. W tym przykładzie jednocześnie wywołuje `twice` funkcja na trzech zmiennych lokalnych i wynik do konsoli.  
  
 [!code-cpp[concrt-parallel-invoke-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_3.cpp)]  
  
 Ten przykład generuje następujące wyniki:  
  
```Output  
108 11.2 HelloHello  
```  
  
 Pełne przykłady, które używają `parallel_invoke` algorytmu, zobacz [porady: używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) i [porady: Korzystanie z parallel_invoke do przeprowadzania operacji równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md).  
  
 [[Górnej](#top)]  
  
##  <a name="parallel_transform_reduce"></a> Parallel_transform — i parallel_reduce — algorytmów  

 [Concurrency::parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) i [concurrency::parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) algorytmy są wersje równoległych algorytmów standardowa biblioteka C++ [std::transform](../../standard-library/algorithm-functions.md#transform)i [std::accumulate](../../standard-library/numeric-functions.md#accumulate)odpowiednio. Współbieżność środowiska wykonawczego wersji przypominają wersji standardowa biblioteka C++ z tą różnicą, że kolejność operacji nie jest określona, ponieważ są one wykonywane równolegle. Użyj tych algorytmów podczas pracy z zestawem jest wystarczająco duży, aby uzyskać korzyści w zakresie wydajności i skalowalności z przetwarzane równolegle.  
  
> [!IMPORTANT]
>  `parallel_transform` i `parallel_reduce` algorytmów obsługuje tylko dostęp losowy dwukierunkowe i do przodu Iteratory, ponieważ te Iteratory tworzy adresów pamięci stabilna. Ponadto te Iteratory musi mieć inną niż`const` l wartości.  
  
###  <a name="parallel_transform"></a> Parallel_transform — algorytm  
 Można użyć `parallel transform` algorytmu w celu wykonania wielu operacji paralelizacja danych. Możesz na przykład:  
  
-   Dopasuj jasność obrazu i wykonywać innych operacji przetwarzania obrazów.  
  
-   Suma lub podjąć skalarnego między dwoma wektorami oraz wykonywać inne obliczenia liczbowych na wektory.  
  
-   Wykonywanie śledzenia 3-ray, gdzie każdej iteracji odnosi się do jednego pikseli, który musi być renderowany.  
  
 W poniższym przykładzie przedstawiono podstawową strukturę, które są używane do wywoływania `parallel_transform` algorytmu. W tym przykładzie Negacja każdy element std::[wektor](../../standard-library/vector-class.md) obiektu na dwa sposoby. W pierwszym sposobie używana wyrażenia lambda. W drugim sposobie używana [std::negate](../../standard-library/negate-struct.md), która jest pochodną [std::unary_function](../../standard-library/unary-function-struct.md).  
  
 [!code-cpp[concrt-basic-parallel-transform#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_4.cpp)]  
  
> [!WARNING]
>  W tym przykładzie przedstawiono podstawowe wykorzystanie `parallel_transform`. Ponieważ funkcja pracy wykonuje znaczną część pracy, znaczny wzrost wydajności nie jest oczekiwany w tym przykładzie.  
  
 `parallel_transform` Algorytm ma dwa przeciążenia. Pierwszy przeciążenia przyjmuje jeden zakres wejściowy i funkcja jednoargumentowy. Funkcja jednoargumentowy może być wyrażenie lambda, który pobiera jeden argument, obiekt funkcji lub typu pochodzącego od `unary_function`. Drugi przeciążenia przyjmuje dwa zakresy wejściowy i funkcja binarnej. Funkcja binarny może być wyrażenie lambda, która przyjmuje dwa argumenty, obiekt funkcji lub typu pochodzącego od [std::binary_function](../../standard-library/binary-function-struct.md). Poniższy przykład przedstawia tych różnic.  
  
 [!code-cpp[concrt-parallel-transform-vectors#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_5.cpp)]  
  
> [!IMPORTANT]
>  Iterator, wprowadzona w danych wyjściowych `parallel_transform` należy całkowicie nakładają się iteratora wejściowy lub nie nakładają się na wszystkich. Zachowanie tego algorytmu jest nieokreślony, jeżeli Iteratory wejściowymi i wyjściowymi częściowo pokrywają się.  
  
###  <a name="parallel_reduce"></a> Parallel_reduce — algorytm  
 `parallel_reduce` Algorytm jest przydatne w przypadku sekwencję operacji, które spełniają asocjacyjnej właściwości. (Ten algorytm nie wymagają przemienne właściwości). Poniżej podano niektóre czynności, które można wykonywać za pomocą `parallel_reduce`:  
  
-   Należy pomnożyć sekwencji macierzy w celu utworzenia macierzy.  
  
-   Należy pomnożyć wektora przez sekwencję macierzy do utworzenia wektora.  
  
-   Oblicza długość sekwencję ciągów.  
  
-   Łączenie listę elementów, takich jak ciągi, w jeden element.  
  
 Podstawowe poniższy przykład przedstawia użycie `parallel_reduce` algorytm połączyć sekwencji ciągi w jeden ciąg. Jak wraz z przykładami dla `parallel_transform`, w tym przykładzie podstawowe nie powinny wzrost wydajności.  
  
 [!code-cpp[concrt-basic-parallel-reduce#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_6.cpp)]  
  
 W wielu przypadkach można traktować `parallel_reduce` jako skrót do użytku `parallel_for_each` algorytm razem z [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) klasy.  
  
###  <a name="map_reduce_example"></a> Przykład: Wykonywanie mapowania i zmniejszyć równolegle  

 A *mapy* operacja dotyczy funkcji każdej wartości w sekwencji. A *zmniejszyć* operacji łączy elementy sekwencji w jedną wartość. Standardowa biblioteka C++ można użyć [std::transform](../../standard-library/algorithm-functions.md#transform) i [std::accumulate](../../standard-library/numeric-functions.md#accumulate) funkcji wykonywanie mapowania i zmniejszanie operacji. Jednak wiele problemów, można użyć `parallel_transform` algorytmu do wykonania tej operacji mapy równolegle i `parallel_reduce` algorytm operacji Zmniejsz równolegle.  

  
 Poniższy przykład porównuje czas potrzebny do obliczenia sumę liczb pierwszych szeregowe i równolegle. Faza mapy przekształca wartości prime z systemem innym niż 0 i sumy fazy Zmniejsz wartości.  
  
 [!code-cpp[concrt-parallel-map-reduce-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_7.cpp)]  
  
 Na przykład innego wykonuje mapy i zmniejszyć operacji równolegle, zobacz [porady: wykonaj mapy i zmniejszyć operacji wykonywane równolegle](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).  
  
 [[Górnej](#top)]  
  
##  <a name="partitions"></a> Podziału pracy  
 Aby parallelize operacji na źródle danych, jest kluczowy etap *partycji* źródła do sekcje, które mogą być jednocześnie udostępniane przez wiele wątków. Partycjonera Określa, jak algorytm równoległych powinien partycji zakresów między wątkami. Jak opisano wcześniej w tym dokumencie, PPL korzysta z domyślnego mechanizmu, który tworzy początkowej obciążeń i następnie używa algorytmu i zakres kradzież do równoważenie tych partycji, podczas obciążenia są niezrównoważone kradzież pracy partycjonowania. Na przykład po ukończeniu zakres iteracji jednego iteracji pętli środowiska uruchomieniowego ponownie dystrybuuje pracy z innych wątków tego wątku. Jednak w przypadku niektórych scenariuszy możesz określić inny mechanizm partycjonowania, który lepiej nadaje się do problemu.  
  
 `parallel_for`, `parallel_for_each`, I `parallel_transform` algorytmy zawiera przeciążone wersji, które przyjmują dodatkowy parametr `_Partitioner`. Ten parametr określa typ partycjonera dzielącą pracy. Oto rodzaje partycjonery definiujących PPL:  
  
 [CONCURRENCY::affinity_partitioner](../../parallel/concrt/reference/affinity-partitioner-class.md)  
 Dzieli działają w stałej liczby zakresów (zazwyczaj liczbę wątków roboczych, które są dostępne do pracy w pętli). Ten typ partycjonera podobny `static_partitioner`, ale zwiększa koligacji pamięci podręcznej w sposób mapowania zakresów wątków roboczych. Ten typ partycjonera może poprawić wydajność pętli jest wykonywane przez ten sam zestaw danych wielokrotnie (np. Pętla w pętli) i danych mieści się w pamięci podręcznej. Ten moduł partycjonowania nie pełni uczestniczy w anulowania. On również nie korzysta z semantyki blokowania współpracy i w związku z tym nie można używać z pętle równoległe mających zależności do przodu.  
  
 [CONCURRENCY::auto_partitioner](../../parallel/concrt/reference/auto-partitioner-class.md)  
 Dzieli działają w początkowa liczba zakresów (zazwyczaj liczbę wątków roboczych, które są dostępne do pracy w pętli). Środowisko uruchomieniowe używa tego typu domyślnie podczas Nie wywołuj algorytm równoległych przeciążone przyjmuje `_Partitioner` parametru. Każdego zakresu można podzielić na zakresy podrzędne, a tym samym umożliwia równoważenie obciążenia występuje. Po ukończeniu zakresu pracy środowiska uruchomieniowego ponownie dystrybuuje zakresy podrzędne pracy z innych wątków do tego wątku. Ten moduł partycjonowania należy używać, jeśli obciążenie nie spełnia jednego z innych kategorii lub wymagają Pełna obsługa anulowania lub blokuje współpracy.  
  
 [CONCURRENCY::simple_partitioner](../../parallel/concrt/reference/simple-partitioner-class.md)  
 Bez reszty pracy do zakresów w taki sposób, że każdy zakres ma co najmniej liczba iteracji, które są określone przez rozmiar fragmentu danego. Ten typ partycjonera uczestniczy w programie Równoważenie obciążenia; Jednak środowiska uruchomieniowego nie podział zakresy zakresy podrzędne. Dla każdego pracownika środowiska uruchomieniowego sprawdza anulowania i przeprowadza równoważenia obciążenia po `_Chunk_size` ukończenia iteracji.  
  
 [CONCURRENCY::static_partitioner](../../parallel/concrt/reference/static-partitioner-class.md)  
 Dzieli działają w stałej liczby zakresów (zazwyczaj liczbę wątków roboczych, które są dostępne do pracy w pętli). Ten typ partycjonera może zwiększyć wydajność, ponieważ nie używa kradzież pracy i w związku z tym mają mniejszy narzut. Po każdej iteracji pętli równoległej wykonuje stałych i uniform ilość pracy i nie wymagają obsługi anulowania lub przekazywania blokuje współpracy, należy użyć tego typu partycjonera.  
  
> [!WARNING]
>  `parallel_for_each` i `parallel_transform` algorytmy obsługuje tylko kontenery używających Iteratory dostępie swobodnym (takich jak std::[wektor](../../standard-library/vector-class.md)) dla partycjonery statyczną, prosty i koligacji. Używanie kontenerów używające dwukierunkowy i do przodu Iteratory generuje błąd kompilacji. Partycjoner domyślne `auto_partitioner`, obsługuje wszystkie trzy typy iteratora.  
  
 Te partycjonery są zazwyczaj używane w taki sam sposób, z wyjątkiem `affinity_partitioner`. Większość typów partycjonera nie obsługują stanu i nie są modyfikowane w czasie wykonywania. W związku z tym można utworzyć te obiekty partycjonera w miejsce wywołania, jak pokazano w poniższym przykładzie.  
  
 [!code-cpp[concrt-static-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_8.cpp)]  
  
 Jednak należy przekazać `affinity_partitioner` obiektu jako niż`const`, l wartość odwołania, tak aby algorytm może przechowywać stanu dla przyszłych pętli do ponownego użycia. W poniższym przykładzie przedstawiono podstawowe aplikacji, która wykonuje tę samą operację na zestaw danych równolegle wiele razy. Użycie `affinity_partitioner` może poprawić wydajność, ponieważ tablica jest prawdopodobne zmieścić ją w pamięci podręcznej.  
  
 [!code-cpp[concrt-affinity-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_9.cpp)]  
  
> [!CAUTION]
>  Należy zachować ostrożność podczas modyfikowania istniejącego kodu, który polega na współpracy semantyki blokowania do użycia `static_partitioner` lub `affinity_partitioner`. Te typy partycjonera nie używaj równoważenia obciążenia lub kradzież zakresu, a w związku z tym można zmienić zachowania aplikacji.  
  
 Najlepszy sposób, aby określić, czy ma być używany z partycjonerem w dowolnym danego scenariusza jest eksperymentu i mierzyć czas potrzebny na zakończenie reprezentatywny obciążeń i konfiguracji komputerów operacji. Na przykład partycjonowania statycznego może zawierać znaczące przyspieszenie komputera wielordzeniowych, który ma tylko kilka rdzeni, ale może to spowodować spowolnienie na komputerach, które mają względnie wiele rdzeni.  
  
 [[Górnej](#top)]  
  
##  <a name="parallel_sorting"></a> Sortowania równoległego  

 PPL udostępnia trzy algorytmów sortowania: [concurrency::parallel_sort](reference/concurrency-namespace-functions.md#parallel_sort), [concurrency::parallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort), i [concurrency::parallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort). Sortowanie algorytmy są przydatne w przypadku zestaw danych, które mogą korzystać z sortowane równolegle. W szczególności sortowanie równolegle jest przydatna, jeśli masz dużego zestawu danych lub gdy sortowanie danych za pomocą operacji porównywania w praktyce kosztowne. Każdy z tych algorytmów sortuje elementów w miejscu.  

  
 `parallel_sort` i `parallel_buffered_sort` algorytmy są oba algorytmy na podstawie porównania. Oznacza to, że ich porównanie elementów według wartości. `parallel_sort` Algorytmu nie ma więcej pamięci wymagań i nadaje się do ogólnego przeznaczenia sortowania. `parallel_buffered_sort` Algorytm można wykonywać lepszym rozwiązaniem niż `parallel_sort`, ale wymaga to O(N) miejsca.  
  
 `parallel_radixsort` Jest algorytm wyznaczania wartości skrótu na podstawie. Oznacza to używa kluczy liczba całkowita, aby posortować elementy. Przy użyciu kluczy, ten algorytm można obliczyć bezpośrednio docelowego elementu zamiast porównania. Podobnie jak `parallel_buffered_sort`, miejsca O(N) wymaga tego algorytmu.  
  
 W poniższej tabeli przedstawiono ważne właściwości trzy algorytmy równoległe sortowania.  
  
|Algorytm|Opis|Mechanizm sortowania|Stabilność sortowania|Wymagania dotyczące pamięci|Złożoność czasu|Dostęp do iteratora|  
|---------------|-----------------|-----------------------|--------------------|-------------------------|---------------------|---------------------|  
|`parallel_sort`|Ogólnego przeznaczenia sortowania na podstawie porównania.|Na podstawie porównania (rosnąco)|Niestabilny|Brak|O((N/P)log(N/P) + 2N((P-1)/P))|Losowe|  
|`parallel_buffered_sort`|Szybsze ogólnego przeznaczenia na podstawie porównania sortowania, które wymaga O(N) miejsca na dysku.|Na podstawie porównania (rosnąco)|Niestabilny|Wymaga dodatkowego miejsca O(N)|O((N/P)log(N))|Losowe|  
|`parallel_radixsort`|Liczba całkowita opartego na kluczach sortowania, które wymaga O(N) miejsca na dysku.|Na podstawie wyznaczania wartości skrótu|Stały|Wymaga dodatkowego miejsca O(N)|O(N/P)|Losowe|  
  
 Na poniższej ilustracji przedstawiono bardziej graficznie ważne właściwości trzy algorytmy równoległe sortowania.  
  
 ![Porównanie sortowania algorytmów](../../parallel/concrt/media/concrt_parallel_sorting.png "concrt_parallel_sorting")  
  
 Te równoległe sortowanie algorytmów zgodne z regułami anulowania i obsługa wyjątków. Aby uzyskać więcej informacji na temat anulowania i obsługa wyjątków w współbieżności środowiska wykonawczego, zobacz [anulowanie algorytmów równoległych](../../parallel/concrt/cancellation-in-the-ppl.md#algorithms) i [obsługi wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
> [!TIP]
>  Obsługują one równoległe sortowanie algorytmów przenoszenia semantyki. Można zdefiniować operator przypisania przenoszenia w celu umożliwienia operacji wymiany wydajniej występuje. Aby uzyskać więcej informacji dotyczących przenoszenia semantykę i operator przypisania przenoszenia, zobacz [deklarator odwołania do r-wartości: & &](../../cpp/rvalue-reference-declarator-amp-amp.md), i [konstruktory przenoszenia i operatory przypisania przenoszenia (C++)](../../cpp/move-constructors-and-move-assignment-operators-cpp.md). Jeśli operator przypisania przenoszenia lub swap — funkcja nie zostanie określona, sortowania algorytmów Użyj konstruktora kopiowania.  
  
 Podstawowe poniższy przykład przedstawia użycie `parallel_sort` sortowania `vector` z `int` wartości. Domyślnie `parallel_sort` używa [std::less](../../standard-library/less-struct.md) porównuje wartości.  
  
 [!code-cpp[concrt-basic-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_10.cpp)]  
  
 Ten przykład przedstawia, jak zapewnić Funkcja porównywania niestandardowych. Używa [std::complex::real](../../standard-library/complex-class.md#real) metody, aby posortować [std::complex\<podwójne >](../../standard-library/complex-double.md) wartości w kolejności rosnącej.  
  
 [!code-cpp[concrt-basic-parallel-sort#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_11.cpp)]  
  
 W tym przykładzie pokazano, jak zapewnić funkcji skrótu do `parallel_radixsort` algorytmu. W tym przykładzie sortuje 3-punktów. Punkty są sortowane według ich odległość od punktu odniesienia.  
  
 [!code-cpp[concrt-parallel-sort-points#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_12.cpp)]  
  
 Na ilustracji w tym przykładzie użyto stosunkowo mały zestaw danych. Można zwiększyć rozmiar początkowy wektora eksperymentować ulepszenia wydajności za pośrednictwem większych zestawów danych.  
  
 W tym przykładzie korzysta z wyrażenia lambda jako funkcji wyznaczania wartości skrótu. Można także użyć jednego z wbudowanych implementacje std::[hash — klasa](../../standard-library/hash-class.md) lub definiować własne specjalizacji. Można także użyć obiektu funkcji skrótu niestandardowych, jak pokazano w poniższym przykładzie:  
  
 [!code-cpp[concrt-parallel-sort-points#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_13.cpp)]  
  
 [!code-cpp[concrt-parallel-sort-points#3](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_14.cpp)]  
  
 Funkcja wyznaczania wartości skrótu musi zwracać typ całkowity ([std::is_integral::value](../../standard-library/is-integral-class.md) musi być `true`). Ten typ całkowity musi być do przekonwertowania na typ `size_t`.  
  
###  <a name="choose_sort"></a> Wybieranie algorytmu sortowania  
 W wielu przypadkach `parallel_sort` zapewnia równowagę pamięci i szybkości. Jednak jako możesz zwiększyć rozmiar zestawu danych, liczba dostępnych procesorów lub złożoność funkcji porównania, `parallel_buffered_sort` lub `parallel_radixsort` mogą działać lepiej. Najlepszy sposób, aby ustalić, który algorytm sortowania do użycia w dowolnym danego scenariusza jest eksperymentu i miary, jak długo trwa sortowanie typowych danych w ramach konfiguracji reprezentatywny komputerów. W przypadku strategii dotyczącej sortowania, należy pamiętać o następujących wytycznych.  
  
-   Rozmiar zestawu danych. W tym dokumencie *małych* zestaw danych zawiera mniej niż 1000 elementów *średni* zestaw danych zawiera między elementami 10 000 do 100 000, a *dużych* zestaw danych zawiera więcej niż 100 000 elementów.  
  
-   Ilość pracy wykonuje z Funkcja porównywania lub funkcji skrótu.  
  
-   Wielkość dostępnych zasobów obliczeniowych.  
  
-   Właściwości zestawu danych. Na przykład jeden algorytm może wykonywać również dane, które jest już prawie sortowane, ale nie również dane, które są całkowicie nieposortowana.  
  
-   Rozmiar fragmentu. Opcjonalny `_Chunk_size` argument określa, kiedy algorytm zmienia się z równoległe implementacji serial sortowania zgodnie z jego dzieli ogólną sortowania na mniejsze jednostki pracy. Na przykład jeśli podasz 512 algorytm przełącza się na implementacji serial gdy jednostka pracy zawiera 512 lub mniej elementów. Implementacja serial może zwiększyć ogólną wydajność, ponieważ eliminuje obciążenie, który jest wymagany do przetwarzania danych równolegle.  
  
 Nie może być wyodrębnienie sortowania w małym zestawie danych równolegle, nawet jeśli masz dużą liczbę dostępnych zasobów obliczeniowych lub z funkcji Porównaj lub funkcji skrótu wykonuje stosunkowo dużą ilość pracy. Można użyć [std::sort](../../standard-library/algorithm-functions.md#sort) funkcji, aby posortować małych zestawów danych. (`parallel_sort` i `parallel_buffered_sort` wywołać `sort` podczas określania rozmiaru fragmentu, który jest większy niż zestaw danych; jednak `parallel_buffered_sort` musi przydzielić miejsca O(N), co może zająć więcej czasu z powodu przydziału pamięci lub rywalizacji blokad.)  
  
 Jeśli musisz zachowywania pamięci lub Twoje alokatora podlega rywalizacji blokad, użyj `parallel_sort` do sortowania zestawu danych średniej wielkości. `parallel_sort` wymaga nie dodatkowe miejsce; inne algorytmy wymagają O(N) miejsca.  
  
 Użyj `parallel_buffered_sort` sortowania średnich zestawów danych i gdy aplikacja spełnia dodatkowe wymagania dotyczące wolnego miejsca O(N). `parallel_buffered_sort` może być szczególnie przydatne, jeśli masz dużą liczbę zasobów obliczeniowych lub funkcja porównywania kosztowna lub funkcji skrótu.  
  
 Użyj `parallel_radixsort` sortowania dużych zestawów danych, a także jeśli aplikacja spełnia dodatkowe wymagania dotyczące wolnego miejsca O(N). `parallel_radixsort` może być przydatny podczas operacji porównywania równoważne jest droższe lub gdy obie operacje jest dość kosztowna.  
  
> [!CAUTION]
>  Implementowanie funkcji skrótu dobrej wymaga znasz zakres zestawu danych i jak każdy element w zestawie danych jest przekształcana do odpowiedniej wartości bez znaku. Ponieważ operacja wyznaczania wartości skrótu działa na wartości bez znaku, należy rozważyć innych strategii sortowania, jeśli nie można przedstawić wartości skrótu bez znaku.  
  
 Poniższy przykład porównuje wydajność `sort`, `parallel_sort`, `parallel_buffered_sort`, i `parallel_radixsort` przed ten sam zestaw dużych losowe dane.  
  
 [!code-cpp[concrt-choosing-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_15.cpp)]  
  
 W tym przykładzie przyjęto założenie, że jest dopuszczalne do przydzielenia miejsca O(N) podczas sortowania, `parallel_radixsort` działa najlepiej na ten zestaw danych w tej konfiguracji komputera.  
  
 [[Górnej](#top)]  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: pisanie pętli parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)|Przedstawia sposób użycia `parallel_for` algorytm mnożenie macierzy.|  
|[Instrukcje: pisanie pętli parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)|Przedstawia sposób użycia `parallel_for_each` algorytm obliczania liczby liczb pierwszych w [std::array](../../standard-library/array-class-stl.md) obiektu równolegle.|  
|[Instrukcje: używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Przedstawia sposób użycia `parallel_invoke` algorytmu, aby poprawić wydajność bitonic algorytm sortowania.|  
|[Instrukcje: korzystanie z parallel_invoke podczas przeprowadzania operacji równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Przedstawia sposób użycia `parallel_invoke` algorytmu, aby poprawić wydajność program, który wykonuje wiele operacji na udostępnione źródło danych.|  
|[Instrukcje: równoległe wykonywanie operacji mapowania i zmniejszania](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Przedstawia sposób użycia `parallel_transform` i `parallel_reduce` algorytmy do wykonywanie mapowania i zmniejszanie operacji liczby wystąpień słowa w plikach.|  
|[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|W tym artykule opisano PPL, oferujący imperatywnych model programowania wspiera skalowalność i łatwość użycia dla tworzenie współbieżnych aplikacji.|  
|[Anulowanie w PPL](cancellation-in-the-ppl.md)|Opisano rolę anulowanie w PPL, jak anulować równoległych pracy i sposób określania, kiedy grupy zadań została anulowana.|  
|[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Opisano rolę obsługi wyjątków w współbieżności środowiska wykonawczego.|  
  
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


