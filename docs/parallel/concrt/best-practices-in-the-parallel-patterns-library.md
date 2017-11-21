---
title: "Najlepsze rozwiązania w bibliotece równoległych wzorców | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Parallel Patterns Library, practices to avoid
- practices to avoid, Parallel Patterns Library
- best practices, Parallel Patterns Library
- Parallel Patterns Library, best practices
ms.assetid: e43e0304-4d54-4bd8-a3b3-b8673559a9d7
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ea611f555abe21a6ad3196bca287a7bd4ff00aa4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="best-practices-in-the-parallel-patterns-library"></a>Biblioteka wzorów równoległych — Najlepsze praktyki
W tym dokumencie opisano jak najbardziej efektywne wykorzystanie równoległych biblioteki wzorców (PLL). PPL udostępnia ogólnego przeznaczenia kontenerów, obiektów i algorytmy do wykonywania równoległości szczegółowych.  
  
 Aby uzyskać więcej informacji o PPL, zobacz [równoległych biblioteki wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md).  
  
##  <a name="top"></a>Sekcje  
 Ten dokument zawiera następujące sekcje:  
  
- [Nie Parallelize małych jednostek pętli](#small-loops)  
  
- [Równoległość najwyższym możliwym poziomie Express](#highest)  
  
- [Korzystanie z parallel_invoke do rozwiązywania problemów dzielenia oraz o](#divide-and-conquer)  
  
- [Użyj anulowania lub obsługa aby przerwać pętlę równoległą wyjątków](#breaking-loops)  
  
- [Zrozumienie wpływu zniszczeniem obiektu anulowania i obsługa wyjątków](#object-destruction)  
  
- [Nie należy blokować wielokrotnie w równoległej pętli](#repeated-blocking)  
  
- [Nie wykonuj blokowanie operacji anulowania pracy równoległych](#blocking)  
  
- [Nie zapisuj udostępnionych danych w równoległej pętli](#shared-writes)  
  
- [Jeśli to możliwe, należy unikać udostępnianie False](#false-sharing)  
  
- [Upewnij się, że zmienne są prawidłowe w okresie istnienia zadania](#lifetime)  
  
##  <a name="small-loops"></a>Nie Parallelize małych jednostek pętli  
 Paralelizacja jednostek pętli stosunkowo mały może spowodować skojarzone planowanie obciążenie ma przeważają korzyści przetwarzania równoległego. Rozważmy poniższy przykład, który dodaje każda para elementów w dwóch tablic.  
  
 [!code-cpp[concrt-small-loops#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_1.cpp)]  
  
 Obciążenie pracą dla każdej iteracji pętli równoległej jest za mały, aby korzystać z obciążenie przetwarzania równoległego. Można zwiększyć wydajność pętlę, wykonując więcej pracy w pętli lub pętli pojedynczo.  
  
 [[Górnej](#top)]  
  
##  <a name="highest"></a>Równoległość najwyższym możliwym poziomie Express  
 Gdy parallelize kodu tylko na niskim poziomie, mogą stać się konstrukcja rozwidlenia sprzężenia, która nie obsługuje jako liczba wzrasta procesorów. A *rozwidlenia sprzężenia* konstrukcja jest konstrukcji, na którym jedno zadanie dzieli pracę na mniejsze równoległych zadań podrzędnych i czeka na tych zadań podrzędnych zakończyć. Każdy podzadanie można rekursywnie dzielenie się w dodatkowych podzadań.  
  
 Chociaż modelu rozwidlenia sprzężenia mogą być przydatne podczas rozwiązywania szerokiej gamy problemów, istnieją sytuacje, w którym zmniejszyć koszty synchronizacji skalowalności. Rozważmy na przykład następujący kod szeregowych, który przetwarza dane obrazu.  
  
 [!code-cpp[concrt-image-processing-filter#20](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_2.cpp)]  
  
 Każdej iteracji pętli są niezależne, można większość zadań, parallelize, jak pokazano w poniższym przykładzie. W tym przykładzie użyto [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytm parallelize zewnętrzne pętli.  

  
 [!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_3.cpp)]  
  
 Poniższy przykład przedstawia konstrukcję sprzężenia rozwidlenia wywołując `ProcessImage` funkcję w pętli. Każde wywołanie `ProcessImage` nie może zwracać zakończenie każdego podzadania.  
  
 [!code-cpp[concrt-image-processing-filter#21](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_4.cpp)]  
  
 W przypadku każdej iteracji pętli równoległej albo wykonuje prawie nie pracy lub pracy, które jest przeprowadzane przez równoległej pętli imbalanced, oznacza to, niektóre iteracji pętli trwać dłużej niż inne, planowanie nakładów pracy jest wymagana do często rozwidlania i Dołącz do pracy można przeważają korzyści przetwarzania równoległego. Ten narzut zwiększa jako liczba wzrasta procesorów.  
  
 Aby zmniejszyć ilość planowania obciążenie w tym przykładzie, można parallelize zewnętrzne pętle przed parallelize wewnętrzny pętli lub użyj innego konstrukcja równoległe, takich jak przetwarzanie potokowe. Poniższy przykład modyfikuje `ProcessImages` funkcji należy użyć [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytm parallelize zewnętrzne pętli.  

  
 [!code-cpp[concrt-image-processing-filter#22](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_5.cpp)]  
  
 Podobny przykład używa potoku do wykonywania równoległego przetwarzania obrazu, zobacz [wskazówki: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).  
  
 [[Górnej](#top)]  
  
##  <a name="divide-and-conquer"></a>Korzystanie z parallel_invoke do rozwiązywania problemów dzielenia oraz o  

 A *dzielenia oraz o* problem jest formą konstrukcji rozwidlenia sprzężenia używa rekursji można przerwać zadania w podzadania. Oprócz [concurrency::task_group](reference/task-group-class.md) i [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) klas, można również użyć [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytm Rozwiązywanie problemów z dzielenia oraz o. `parallel_invoke` Algorytm ma składnię zwięzły więcej niż obiekty grupy zadań i jest przydatne w przypadku stała liczba równoległych zadań.  
  
 Poniższy przykład przedstawia użycie `parallel_invoke` algorytmu do zaimplementowania bitonic algorytm sortowania.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#12](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_6.cpp)]  
  
 Aby zmniejszyć nakład pracy `parallel_invoke` algorytm wykonuje ostatniego sekwencję zadań na kontekst wywołania.  
  
 Aby uzyskać pełną wersję tego przykładu, zobacz [porady: używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md). Aby uzyskać więcej informacji na temat `parallel_invoke` algorytmu, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).  
  
 [[Górnej](#top)]  
  
##  <a name="breaking-loops"></a>Użyj anulowania lub obsługa aby przerwać pętlę równoległą wyjątków  
 PPL udostępnia dwa sposoby, aby anulować równoległych pracy wykonywanego przez grupy zadań lub równoległych algorytmu. Jednym ze sposobów jest użycie mechanizmu anulowania, które są udostępniane przez [concurrency::task_group](reference/task-group-class.md) i [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) klasy. Inny sposób jest Zgłoś wyjątek w treści funkcji pracy zadania. Mechanizm anulowania jest bardziej efektywne niż obsługi na anulowanie drzewa pracy równoległej wyjątków. A *drzewa pracy równoległej* jest grupą grup powiązane zadanie, w których niektóre grupy zadań zawierają inne grupy zadań. Mechanizm anulowania anuluje grupy zadań i jej grup podrzędnych zadania w sposób góra dół. Z drugiej strony Obsługa wyjątków w sposób dołu do góry i musiał zrezygnować z każdej grupy zadań podrzędnych niezależnie jako wyjątek w górę propaguje.  
  

 Podczas pracy bezpośrednio z obiektu grupy zadań, użyj [concurrency::task_group::cancel](reference/task-group-class.md#cancel) lub [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) metod można anulować pracy, który należy do tej grupy zadań . Aby anulować równoległych algorytmu, na przykład `parallel_for`, Utwórz grupę nadrzędną zadań i anulować tej grupy zadań. Rozważmy na przykład następująca funkcja `parallel_find_any`, która wyszukuje wartości w tablicy równolegle.  


  
 [!code-cpp[concrt-parallel-array-search#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_7.cpp)]  
  
 Algorytmy równoległe używają grupy zadań, gdy jeden z równoległych iteracji anuluje nadrzędnej grupy zadań, ogólne zadanie zostało anulowane. Aby uzyskać pełną wersję tego przykładu, zobacz [porady: Użyj anulowania, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md).  
  
 Chociaż obsługi wyjątków jest mniej wydajne sposób anulowania pracy równoległej niż mechanizmu anulowania, mogą występować przypadkach, gdy obsługa wyjątków jest odpowiedni. Na przykład następujące metody `for_all`, rekursywnie pełni funkcję pracy na każdym węźle `tree` struktury. W tym przykładzie `_children` elementu członkowskiego danych jest [kontener std::list](../../standard-library/list-class.md) zawierający `tree` obiektów.  
  
 [!code-cpp[concrt-task-tree-search#6](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_8.cpp)]  
  
 Element wywołujący `tree::for_all` — metoda może zgłosić wyjątek, jeśli nie wymaga funkcji pracy ma być wywoływana na każdym elemencie drzewa. W poniższym przykładzie przedstawiono `search_for_value` funkcji, która wyszukuje wartość w określonych `tree` obiektu. `search_for_value` Funkcja korzysta z funkcji pracy, który zgłasza wyjątek, gdy bieżący element drzewa jest zgodna z podanej wartości. `search_for_value` Używa `try-catch` blok do przechwycenia wyjątek i wydrukować wynik do konsoli.  
  
 [!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_9.cpp)]  
  
 Aby uzyskać pełną wersję tego przykładu, zobacz [porady: Użyj obsługi wyjątków aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).  
  
 Aby uzyskać więcej ogólnych informacji na temat anulowania i mechanizmy obsługi wyjątków, które są udostępniane przez PPL, zobacz [anulowanie w PPL](cancellation-in-the-ppl.md) i [obsługi wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
 [[Górnej](#top)]  
  
##  <a name="object-destruction"></a>Zrozumienie wpływu zniszczeniem obiektu anulowania i obsługa wyjątków  
 Drzewa pracy równoległej zadania, które zostało anulowane zapobiega zadania podrzędne uruchamianie. Może to powodować problemy, jeśli jedno z zadań podrzędnych wykonuje operację, która jest istotne dla aplikacji, takich jak zwalnianie zasobu. Ponadto anulowanie zadania może spowodować wyjątek propagację za pośrednictwem destruktor obiektu i spowodować niezdefiniowane zachowanie aplikacji.  
  
 W poniższym przykładzie `Resource` klasa opisuje zasobu i `Container` klasa opisuje kontener, który zawiera zasoby. W jego destruktora `Container` klasy wywołania `cleanup` metody w dwóch jego `Resource` elementów członkowskich w równolegle, a następnie wywołania `cleanup` metody na jego trzeciej `Resource` elementu członkowskiego.  
  
 [!code-cpp[concrt-parallel-resource-destruction#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_10.h)]  
  
 Chociaż ten wzorzec nie ma problemów samodzielnie, należy rozważyć następujący kod, który uruchamia się równolegle dwa zadania. Pierwszym zadaniem tworzy `Container` obiekt i drugie zadanie anuluje zadanie ogólnej. Na ilustracji, w przykładzie użyto dwóch [concurrency::event](../../parallel/concrt/reference/event-class.md) obiektów, aby upewnić się, że anulowania występuje po `Container` obiekt jest tworzony i że `Container` obiekt zostanie zniszczony po anulowaniu Operacja jest wykonywana.  
  
 [!code-cpp[concrt-parallel-resource-destruction#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_11.cpp)]  
  
 Ten przykład generuje następujące wyniki:  
  
```Output  
Container 1: Freeing resources...Exiting program...  
```  
  
 W tym przykładzie kodu zawiera następujące problemy, które mogą spowodować, że plik zachowywać się inaczej niż oczekiwana:  
  
-   Anulowanie zadania nadrzędnego powoduje, że zadanie podrzędne, wywołanie [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke), również zostać anulowane. W związku z tym nie są zwalniane tych zasobów.  

  
-   Anulowanie zadania nadrzędnego powoduje, że zadania podrzędnego zostać zgłoszony wyjątek wewnętrzny. Ponieważ `Container` destruktor nie obsługuje tego wyjątku, wyjątek są propagowane w górę i trzeci zasobów nie zostanie zwolniona.  
  
-   Wyjątek zgłaszany przez zadanie podrzędne propaguje za pośrednictwem `Container` destruktora. Zgłaszanie z destruktora umieszcza aplikacji w stanie niezdefiniowany.  
  
 Zaleca się, że nie wykonuj krytycznej operacji, takich jak zwalnianie zasobów, zadań, o ile nie może zagwarantować, że te zadania nie można anulować. Firma Microsoft zaleca, nie używaj funkcji środowiska uruchomieniowego, które może zgłosić w destruktorze typów.  
  
 [[Górnej](#top)]  
  
##  <a name="repeated-blocking"></a>Nie należy blokować wielokrotnie w równoległej pętli  

 Równoległe pętli, takie jak [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) lub [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) który jest zdominowany przez blokowanie operacji może spowodować środowisko uruchomieniowe umożliwia tworzenie wielu wątków w krótkim czasie.  

  
 Współbieżność środowiska wykonawczego wykonuje dodatkowej pracy, gdy zakończenie zadania lub wspólnie blokuje lub daje. Równoległe jeden pętli bloki iteracji, środowisko uruchomieniowe może rozpocząć innego iteracji. Jeśli nie ma żadnych dostępnych wątków bezczynności, środowisko uruchomieniowe tworzy nowego wątku.  
  
 Gdy treść równoległego czasami pętli bloków, ten mechanizm pomaga zmaksymalizować ogólną przepustowość zadań. Jednak gdy zablokować dużo iteracji, środowisko uruchomieniowe może tworzyć wiele wątków, aby uruchomić dodatkowe czynności. Może to prowadzić do warunków ilości pamięci lub niska wykorzystania zasobów sprzętowych.  
  
 Rozważmy następujący przykład, który wywołuje [concurrency::send](reference/concurrency-namespace-functions.md#send) funkcji w każdej iteracji `parallel_for` pętli. Ponieważ `send` wspólnie, blokuje środowiska uruchomieniowego tworzy nowego wątku do uruchomienia dodatkowych działań zawsze `send` jest wywoływana.  
  
 [!code-cpp[concrt-repeated-blocking#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_12.cpp)]  
  
 Zaleca się, że Refaktoryzuj swój kod, aby uniknąć tego wzorca. W tym przykładzie można uniknąć tworzenia dodatkowe wątki wywołując `send` w szeregowego `for` pętli.  
  
 [[Górnej](#top)]  
  
##  <a name="blocking"></a>Nie wykonuj blokowanie operacji anulowania pracy równoległych  

 Jeśli to możliwe, nie należy wykonywać operacji blokowania przed wywołaniem [concurrency::task_group::cancel](reference/task-group-class.md#cancel) lub [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) metodę, aby anulować pracy równoległych.  


  
 Gdy zadanie wykonuje wspólnego, blokowanie operacji, środowisko uruchomieniowe można wykonywać inne zadania podczas pierwszego zadania oczekuje na dane. Środowisko uruchomieniowe zmienia harmonogram zadań oczekiwania, po jego odblokowuje. Środowisko uruchomieniowe zwykle zmienia harmonogram zadań, które były bardziej ostatnio odblokowany, przed jego zmienia harmonogram zadań, które były mniej ostatnio odblokowany. W związku z tym środowiska uruchomieniowego można zaplanować niepotrzebnej pracy podczas operacji blokowania, co prowadzi do zmniejszenia wydajności. W związku z tym podczas wykonywania operacji blokowania przed anulowaniem pracy równoległej, operacji blokowania można opóźnić wywołanie `cancel`. Powoduje to, że inne zadania do wykonania pracy niepotrzebne.  
  
 Rozważmy następujący przykład, który definiuje `parallel_find_answer` funkcji, która wyszukuje element podana tablica, która spełnia podane funkcja predykatu. Gdy predykatu funkcja zwraca `true`, tworzy równoległych funkcja pracy `Answer` obiektu i anuluje zadania ogólnej.  
  
 [!code-cpp[concrt-blocking-cancel#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_13.cpp)]  
  


 `new` Operator wykonuje alokacji sterty, które mogłyby zablokować. Środowisko uruchomieniowe wykonuje inne zadania tylko wtedy, gdy zadanie wykonuje wspólnego, blokuje połączenia, takie jak wywołanie [concurrency::critical_section::lock](reference/critical-section-class.md#lock).  


  
 Poniższy przykład pokazuje, jak można uniknąć niepotrzebnych pracy, a tym samym poprawić wydajność. W tym przykładzie anuluje grupy zadań przed przydzielania magazynu dla `Answer` obiektu.  
  
 [!code-cpp[concrt-blocking-cancel#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_14.cpp)]  
  
 [[Górnej](#top)]  
  
##  <a name="shared-writes"></a>Nie zapisuj udostępnionych danych w równoległej pętli  
 Współbieżność środowiska wykonawczego zapewnia kilka struktury danych, na przykład [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md), synchronizowanych równoczesny dostęp do współużytkowanych danych. Te struktury danych są przydatne w wielu przypadkach, na przykład wielu zadań rzadko potrzebują dostępu współdzielonego do zasobu.  
  
 Rozważmy następujący przykład, który używa [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytmu i `critical_section` obiekt do obliczenia liczba liczb pierwszych w [std::array](../../standard-library/array-class-stl.md) obiektu. W tym przykładzie nie działa, ponieważ każdy wątek należy poczekać na dostęp do współdzielonej zmiennej `prime_sum`.  

  
 [!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_15.cpp)]  
  
 W tym przykładzie może również spowodować słabą wydajność, ponieważ częste operacji blokowania skutecznie serializuje pętli. Ponadto kiedy obiekt współbieżność środowiska wykonawczego wykonuje operację blokowania, planista może utworzyć dodatkowe wątku może wykonywać inne zadania podczas pierwszego wątek oczekuje na dane. Jeśli środowisko uruchomieniowe tworzy wiele wątków, ponieważ wielu zadań, które oczekują na udostępnionych danych, aplikacji może niska wydajność lub przejść w stan zasobów.  
  
 Definiuje PPL [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) klasy, która pomaga wyeliminować stanu udostępnionego, zapewniając dostęp do zasobów udostępnionych w sposób wolny blokady. `combinable` Klasa udostępnia magazynu lokalnego wątku, który pozwala przeprowadzić obliczenia szczegółowych, a następnie scalić tych obliczeń do końcowego wyniku. Można potraktować `combinable` obiektu jako zmienną redukcyjną.  
  
 Poniższy przykład modyfikuje poprzedniego przy użyciu `combinable` obiekt zamiast `critical_section` obiekt do obliczenia sumy. W tym przykładzie skaluje, ponieważ każdy wątek utrzymuje własną kopię lokalną suma. W tym przykładzie użyto [concurrency::combinable::combine](reference/combinable-class.md#combine) metody do scalenia lokalnego obliczenia wynik końcowy.  

  
 [!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_16.cpp)]  
  
 Aby uzyskać pełną wersję tego przykładu, zobacz [porady: Korzystanie z wyników połączonych do poprawiania wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md). Aby uzyskać więcej informacji na temat `combinable` , zobacz [równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md).  
  
 [[Górnej](#top)]  
  
##  <a name="false-sharing"></a>Jeśli to możliwe, należy unikać udostępnianie False  
 *Udostępnianie false* występuje, gdy wiele równoczesnych zadań, które są uruchomione na oddzielnych procesorów zapisu zmienne, które znajdują się na tym samym wierszu pamięci podręcznej. Jedno zadanie zapisuje dane w jednym zmiennych, unieważnienia wiersza pamięci podręcznej dla obu zmiennych. Każdemu procesorowi musi ponownie załadować wiersza pamięci podręcznej zawsze unieważnienia wiersza pamięci podręcznej. W związku z tym udostępnianie false może spowodować zmniejszenie wydajności w aplikacji.  
  
 Podstawowy przykład pokazuje dwóch poniższych równoczesnych zadań każdego zwiększyć wartości zmiennej licznika udostępnionego.  
  
 [!code-cpp[concrt-false-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_17.cpp)]  
  
 Aby wyeliminować udostępniania danych między dwa zadania, można zmodyfikować przykładu do używania dwóch zmiennych licznika. W tym przykładzie oblicza wartość licznika końcowe po zakończeniu zadania. Jednak w tym przykładzie przedstawiono udostępnianie false, ponieważ zmienne `count1` i `count2` mogą znajdować się w tym samym wierszu pamięci podręcznej.  
  
 [!code-cpp[concrt-false-sharing#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_18.cpp)]  
  
 Jednym ze sposobów wyeliminować fałszywe udostępniania jest upewnij się, że zmienne licznika są w pamięci podręcznej w oddzielnych wierszach. Poniższy przykład wyrównuje zmienne `count1` i `count2` na 64-bajtowych granicach.  
  
 [!code-cpp[concrt-false-sharing#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_19.cpp)]  
  
 W tym przykładzie zakłada, że rozmiar pamięci podręcznej 64 lub mniejszą liczbę bajtów.  
  
 Firma Microsoft zaleca użycie [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) klasy podczas musi udostępniać dane między zadania. `combinable` Klasy tworzy zmiennymi lokalnymi wątku w taki sposób, że udostępnianie false jest mniej prawdopodobne. Aby uzyskać więcej informacji na temat `combinable` , zobacz [równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md).  
  
 [[Górnej](#top)]  
  
##  <a name="lifetime"></a>Upewnij się, że zmienne są prawidłowe w okresie istnienia zadania  
 Podając wyrażenia lambda do grupy zadań lub równoległych algorytmu klauzuli przechwytywania określa, czy treść wyrażenia lambda uzyskuje dostęp do zmiennych w otaczającym zakresie, według wartości lub według odwołania. Jeśli zmienne do wyrażenia lambda przez odwołanie, musi zapewniać, że okres istnienia tej zmiennej będzie się powtarzać, zakończenie zadania.  
  
 Rozważmy następujący przykład, który definiuje `object` klasy i `perform_action` funkcji. `perform_action` Funkcja tworzy `object` zmiennej i asynchronicznie wykonuje akcję na tej zmiennej. Ponieważ zadanie nie jest gwarantowana, aby zakończyć działanie przed `perform_action` funkcja zwraca będzie awarii lub zachowują nieokreślony Jeśli `object` zmienna zostanie zniszczony, gdy zadanie jest uruchomione.  
  
 [!code-cpp[concrt-lambda-lifetime#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_20.cpp)]  
  
 W zależności od wymagań aplikacji można użyć jednej z następujących metod aby zagwarantować, że zmienne ważność w okresie istnienia każdego zadania.  
  
 W poniższym przykładzie `object` zmiennej przez wartość do zadania. W związku z tym zadanie działa na własną kopię zmiennej.  
  
 [!code-cpp[concrt-lambda-lifetime#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_21.cpp)]  
  
 Ponieważ `object` zmienna jest przekazywana przez wartość, wszelkie zmiany stanu w tej zmiennej pojawią się w oryginalnej kopii.  
  
 W poniższym przykładzie użyto [concurrency::task_group::wait](reference/task-group-class.md#wait) metody, aby upewnić się, że zadanie kończy się przed `perform_action` funkcja zwraca.  


  
 [!code-cpp[concrt-lambda-lifetime#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_22.cpp)]  
  
 Ponieważ zadanie zakończy teraz przed funkcja zwraca, `perform_action` funkcja nie jest już działa asynchronicznie.  
  
 Poniższy przykład modyfikuje `perform_action` przez funkcję odwołanie do `object` zmiennej. Obiekt wywołujący musi zagwarantować, że okres istnienia `object` zmiennej jest prawidłowy, zakończenie zadania.  
  
 [!code-cpp[concrt-lambda-lifetime#4](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_23.cpp)]  
  
 Umożliwia także wskaźnik do kontrolowania okres istnienia obiektu do grupy zadań lub równoległych algorytmu.  
  
 Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażenia Lambda](../../cpp/lambda-expressions-in-cpp.md).  
  
 [[Górnej](#top)]  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność środowiska wykonawczego — najlepsze praktyki](../../parallel/concrt/concurrency-runtime-best-practices.md)   
 [Biblioteka równoległych wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [Równoległe kontenery i obiekty](../../parallel/concrt/parallel-containers-and-objects.md)   
 [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)   
 [Anulowanie w PPL](cancellation-in-the-ppl.md)   
 [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [Wskazówki: Tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)   
 [Porady: używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)   
 [Porady: Użyj anulowania, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)   
 [Porady: Korzystanie z wyników połączonych do poprawiania wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)   
 [Biblioteki agentów asynchronicznych — najlepsze praktyki](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)   
 [Najlepsze praktyki ogólne współbieżności środowiska wykonawczego](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)

