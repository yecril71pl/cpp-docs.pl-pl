---
title: Biblioteka wzorów równoległych — Najlepsze praktyki
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Patterns Library, practices to avoid
- practices to avoid, Parallel Patterns Library
- best practices, Parallel Patterns Library
- Parallel Patterns Library, best practices
ms.assetid: e43e0304-4d54-4bd8-a3b3-b8673559a9d7
ms.openlocfilehash: fc120ecc122678b54c7dd27b95445f523bc114a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394497"
---
# <a name="best-practices-in-the-parallel-patterns-library"></a>Biblioteka wzorów równoległych — Najlepsze praktyki

W tym dokumencie opisano jak najlepiej Aby efektywnie wykorzystać równoległe Biblioteka wzorców (PPL). PPL zapewnia ogólnego przeznaczenia kontenerów, obiektów i algorytmy umożliwiające wykonywanie równoległość drobnoziarnistą.

Aby uzyskać więcej informacji na temat PPL, zobacz [biblioteki wzorców równoległych (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md).

##  <a name="top"></a> Sekcje

Ten dokument zawiera następujące sekcje:

- [Nie Zrównoleglij małych jednostek pętli](#small-loops)

- [Ekspresowa równoległość na najwyższym możliwym poziomie](#highest)

- [Używanie parallel_invoke do rozwiązywania problemów dzielenia i Zwyciężaj](#divide-and-conquer)

- [Użyj anulowania lub obsługi aby przerwać pętlę równoległą wyjątków](#breaking-loops)

- [Zrozumieć sposób unieważnienie i obsługa wyjątków wpływają na zniszczenie obiektu](#object-destruction)

- [Nie powtarzaj blokowania w pętli równoległej](#repeated-blocking)

- [Nie wykonuj operacji blokowania po anulowaniu czynności równoległej](#blocking)

- [Nie wpisuj do współdzielonych danych w pętli równoległej](#shared-writes)

- [Jeśli to możliwe, unikaj niezamierzonego współdzielenia](#false-sharing)

- [Upewnij się, że zmienne są ważne przez cały okres istnienia zadania](#lifetime)

##  <a name="small-loops"></a> Nie Zrównoleglij małych jednostek pętli

Przetwarzanie równoległe stosunkowo małych jednostek pętli może spowodować skojarzone planowanie obciążenie ma przeważyć zalety przetwarzania równoległego. Rozważmy następujący przykład, który dodaje każdej pary elementów w dwóch tablicach.

[!code-cpp[concrt-small-loops#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_1.cpp)]

Obciążenie dla każdej iteracji pętli równoległej jest zbyt mała, aby korzystać z obciążenie do przetwarzania równoległego. Może zwiększyć wydajność tej pętli, wykonując więcej pracy w ciele pętli lub wykonując szeregowo pętli.

[[Górnej](#top)]

##  <a name="highest"></a> Ekspresowa równoległość na najwyższym możliwym poziomie

Gdy można zrównoleglić kod tylko na niskim poziomie, możesz wprowadzić konstrukcji rozwidlenia sprzężenia, która nie działa jako liczba procesorów wzrasta. A *przyłączaniem do rozwidlenia* konstrukcja jest konstrukcją, gdzie jedno zadanie dzieli swoją pracę na mniejsze równoległe podzadań i oczekuje na te podzadania zakończyć. Każdego z nich można rekursywnie dzielenie się na dodatkowe podzadania.

Chociaż model rozwidlenia sprzężenia mogą być przydatne w przypadku rozwiązywania różnych problemów, istnieją sytuacje, w którym obciążenie synchronizacji, można zmniejszyć skalowalność. Na przykład rozważmy następujący kod szeregowe, który przetwarza dane obrazu.

[!code-cpp[concrt-image-processing-filter#20](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_2.cpp)]

Ponieważ każdej iteracji pętli jest niezależny, można zrównoleglić znaczną część pracy, jak pokazano w poniższym przykładzie. W tym przykładzie użyto [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytmów równoległe przetwarzanie zewnętrzna pętla.

[!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_3.cpp)]

W poniższym przykładzie pokazano konstrukcję rozwidlenia sprzężenia, wywołując `ProcessImage` funkcji w pętli. Każde wywołanie `ProcessImage` nie może zwracać zakończenie każdego z nich.

[!code-cpp[concrt-image-processing-filter#21](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_4.cpp)]

W przypadku każdej iteracji pętli równoległej, albo wykonuje prawie nie pracy lub pracy, która jest wykonywana przez pętlę równoległą imbalanced, to znaczy, niektórych iteracji pętli trwać dłużej niż inne, planowanie obciążenie, jest wymagany do rozwidlenia się często i pracy sprzężenia mogą przeważają korzyści dla wykonywania równoległego. Zwiększa to obciążenie w miarę zwiększania procesorów liczby.

Aby zmniejszyć ilość planowania obciążenie w tym przykładzie, można zrównoleglić zewnętrznej pętli przed zrównoleglenia pętli wewnętrzny lub użyć innej konstrukcji równoległe, takie jak przetwarzanie potokowe. Poniższy przykład modyfikuje `ProcessImages` funkcja do użycia [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytmów równoległe przetwarzanie zewnętrzna pętla.

[!code-cpp[concrt-image-processing-filter#22](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_5.cpp)]

Aby uzyskać podobny przykład, który używa potoku do wykonywania przetwarzania obrazów w sposób równoległy, zobacz [instruktażu: Tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

[[Górnej](#top)]

##  <a name="divide-and-conquer"></a> Używanie parallel_invoke do rozwiązywania problemów dzielenia i Zwyciężaj

A *dzielenia i zwyciężaj* problemu jest rodzaj konstrukcji rozwidlenia sprzężenia, która używa rekursji do Podziel zadanie na podzadania. Oprócz [concurrency::task_group](reference/task-group-class.md) i [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) klasy, można również użyć [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytm Rozwiązywanie problemów z dzielenia i zwyciężaj. `parallel_invoke` Algorytm ma bardziej zwięzłą składnię niż obiektów grupy zadań i jest przydatne, gdy ma stałą liczbę równoległych zadań podrzędnych.

Poniższy przykład ilustruje użycie `parallel_invoke` algorytm bitonicznego sortowania algorytm implementacji.

[!code-cpp[concrt-parallel-bitonic-sort#12](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_6.cpp)]

Aby zmniejszyć obciążenie, `parallel_invoke` algorytm wykonuje ostatniego sekwencję zadań na kontekst wywołania.

Aby uzyskać pełną wersję tego przykładu, zobacz [jak: Używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md). Aby uzyskać więcej informacji na temat `parallel_invoke` algorytmu, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

[[Górnej](#top)]

##  <a name="breaking-loops"></a> Użyj anulowania lub obsługi aby przerwać pętlę równoległą wyjątków

PPL udostępnia dwa sposoby, aby anulować czynność równoległą, które jest wykonywane przez grupy zadań lub algorytmu równoległego. Jednym ze sposobów jest używany mechanizm anulowania, który jest dostarczany przez [concurrency::task_group](reference/task-group-class.md) i [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) klasy. Drugi sposób to zgłosić wyjątek w ciele funkcji roboczych zadania. W mechanizmie anulowania jest bardziej wydajne niż Obsługa w drzewie równoległej pracy anulowanie wyjątków. A *drzewa pracy równoległej* jest grupą grup powiązanych zadań, w których niektóre grupy zadań zawierają innych grupach zadań. W mechanizmie anulowania przerywa grupy zadań i jej podrzędne grupy zadań w sposób góra dół. Z drugiej strony Obsługa wyjątków działa w sposób od dołu do góry i musi anulować każda grupa zadań podrzędnych niezależnie jako wyjątek propaguje w górę.

Podczas pracy bezpośrednio z obiektu grupy zadań, użyj [concurrency::task_group::cancel](reference/task-group-class.md#cancel) lub [CONCURRENCY::structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) metod można anulować pracy, który należy do tej grupy zadań . Aby anulować algorytmu równoległego, na przykład `parallel_for`, Utwórz grupę nadrzędną zadań i anulowania tej grupy zadań. Na przykład rozważmy następującą funkcję `parallel_find_any`, która wyszukuje wartość w tablicy równolegle.

[!code-cpp[concrt-parallel-array-search#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_7.cpp)]

Algorytmy równoległe używają grupy zadań, gdy jeden z równoległych iteracji anuluje grupę nadrzędną zadań, całkowitej zadanie zostanie anulowane. Aby uzyskać pełną wersję tego przykładu, zobacz [jak: Użyj anulowania aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md).

Obsługa wyjątków jest mniej skuteczny sposób, aby anulować czynność równoległą niż mechanizmie anulowania, istnieją przypadki, gdy obsługi wyjątków jest odpowiedni. Na przykład następującą metodę `for_all`, rekursywnie wykonuje funkcję pracy w każdym węźle `tree` struktury. W tym przykładzie `_children` element członkowski danych jest [kontener std::list](../../standard-library/list-class.md) zawierający `tree` obiektów.

[!code-cpp[concrt-task-tree-search#6](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_8.cpp)]

Obiekt wywołujący `tree::for_all` metoda może zgłosić wyjątek, jeśli ta funkcja pracy ma być wywoływana dla każdego elementu w drzewie nie jest wymagane. W poniższym przykładzie przedstawiono `search_for_value` funkcji, która wyszukuje wartość w określonych `tree` obiektu. `search_for_value` Funkcja używa funkcja pracy, która zgłosiła wyjątek, gdy podana wartość jest zgodna z bieżącym elementem drzewa. `search_for_value` Używa funkcji `try-catch` bloku, aby przechwycić wyjątek i wydrukować wynik do konsoli.

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_9.cpp)]

Aby uzyskać pełną wersję tego przykładu, zobacz [jak: Użyj wyjątków, obsługa aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

Aby uzyskać więcej ogólnych informacji na temat anulowania i mechanizmy obsługi wyjątków, które są dostarczane przez PPL, zobacz [anulowanie w PPL](cancellation-in-the-ppl.md) i [wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

[[Górnej](#top)]

##  <a name="object-destruction"></a> Zrozumieć sposób unieważnienie i obsługa wyjątków wpływają na zniszczenie obiektu

W drzewie równoległej pracy zadanie, które zostało anulowane zapobiega zadania podrzędne uruchamiania. Może to powodować problemy, jeśli jedno z zadań podrzędnych wykonuje operację, która jest ważna dla aplikacji, taką jak zwalnianie zasobu. Ponadto anulowanie zadania może spowodować wyjątek dotyczący propagować przez destruktora obiektu i spowodować niezdefiniowane zachowanie w aplikacji.

W poniższym przykładzie `Resource` klasa opisuje zasobu i `Container` klasa opisuje kontener, który zawiera zasoby. W destruktorze `Container` klasy wywołania `cleanup` metody na dwie jego `Resource` elementów członkowskich w równoległego, a następnie wywołania `cleanup` metody na jego innych `Resource` elementu członkowskiego.

[!code-cpp[concrt-parallel-resource-destruction#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_10.h)]

Mimo że ten wzorzec nie ma problemów z samodzielnie, należy wziąć pod uwagę następujący kod, który jest wykonywany współbieżnie dwa zadania. Pierwsze zadanie tworzy `Container` obiektu, a drugie zadanie podrzędne anuluje całego zadania. Do celów informacyjnych, w przykładzie użyto dwóch [concurrency::event](../../parallel/concrt/reference/event-class.md) obiektów, aby upewnić się, że anulowanie występuje po `Container` obiekt zostanie utworzony i czy `Container` obiekt jest niszczony, po anulowaniu Operacja jest wykonywana.

[!code-cpp[concrt-parallel-resource-destruction#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_11.cpp)]

Ten przykład generuje następujące wyniki:

```Output
Container 1: Freeing resources...Exiting program...
```

Ten przykładowy kod zawiera następujące problemy, które mogą spowodować, że zachowywać się inaczej, niż można by oczekiwać:

- Anulowanie zadania nadrzędnego powoduje, że zadanie podrzędne, wywołanie [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke), również zostaną anulowane. W związku z tym tych zasobów nie są zwalniane.

- Anulowanie zadania nadrzędnego powoduje, że zadanie podrzędne zgłosić wyjątek wewnętrzny. Ponieważ `Container` destruktor nie zapewnia obsługi tego wyjątku, wyjątek jest propagowany w górę i trzeci zasób nie zostanie zwolniony.

- Propaguje wyjątek, który jest generowany przez zadanie podrzędne, za pośrednictwem `Container` destruktora. Zostanie zgłoszony został pominięty przez destruktora umieszcza ją w stanie niezdefiniowane.

Firma Microsoft zaleca, nie wykonuj krytyczne operacje, takie jak zwalnianie zasobów w zadaniach, o ile nie może zagwarantować, że te zadania nie zostaną anulowane. Zalecamy również, że nie używasz funkcji środowiska uruchomieniowego, który może zgłosić w destruktorze typów.

[[Górnej](#top)]

##  <a name="repeated-blocking"></a> Nie powtarzaj blokowania w pętli równoległej

Pętli równoległej, takie jak [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) lub [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) , jest zdominowany przez blokowanie operacji może spowodować, że środowisko uruchomieniowe utworzyć wiele wątków przez krótki czas.

Środowisko uruchomieniowe współbieżności wykonuje dodatkowej pracy, jeśli zadanie zakończy się lub blokuje wspólne lub daje. Gdy jeden równoległego pętli bloki iteracji, środowisko uruchomieniowe może zacząć innej iteracji. Gdy nie ma żadnych dostępnych bezczynne wątki, środowisko uruchomieniowe tworzy nowy wątek.

Gdy treść równoległego pętli od czasu do czasu bloków, ten mechanizm pomaga zmaksymalizować ogólną przepływność zadania. Jednak gdy zablokować liczby iteracji, środowisko uruchomieniowe może tworzyć wiele wątków, aby uruchomić dodatkowej pracy. Może to prowadzić do warunków małej ilości pamięci lub niską wykorzystania zasobów sprzętowych.

Rozważmy następujący przykład, który wywołuje [concurrency::send](reference/concurrency-namespace-functions.md#send) funkcji w każdej iteracji `parallel_for` pętli. Ponieważ `send` blokuje wspólne, środowisko uruchomieniowe tworzy nowy wątek, aby uruchomić dodatkowej pracy w każdym `send` jest wywoływana.

[!code-cpp[concrt-repeated-blocking#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_12.cpp)]

Zaleca się, że Refaktoryzuj swój kod, aby uniknąć tego wzorca. W tym przykładzie można uniknąć tworzenia dodatkowych wątków przez wywołanie metody `send` w szeregowego `for` pętli.

[[Górnej](#top)]

##  <a name="blocking"></a> Nie wykonuj operacji blokowania po anulowaniu czynności równoległej

Jeśli to możliwe, nie wykonuj operacji blokowania przed wywołaniem [concurrency::task_group::cancel](reference/task-group-class.md#cancel) lub [CONCURRENCY::structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) metodę, aby anulować czynność równoległą.

Gdy zadanie wykonuje cooperative, blokowanie operacji, środowisko uruchomieniowe może wykonywać inne zadania, gdy pierwsze zadanie czeka na dane. Środowisko uruchomieniowe zmieni ustalony zadanie oczekujące, gdy jej odblokowuje. Środowisko uruchomieniowe zwykle zmienia harmonogram zadań, które były bardziej ostatnio odblokowany przed jej zmienia harmonogram zadań, które były mniejsza, ostatnio odblokowane. W związku z tym środowisko uruchomieniowe można zaplanować niepotrzebne pracy podczas operacji blokowania, co prowadzi do obniżenie wydajności. W związku z tym podczas wykonywania operacji blokowania przed anulowaniu czynności równoległej, blokowanie operacji można opóźnić wywołanie `cancel`. To powoduje, że inne zadania do wykonania pracy niepotrzebne.

Rozważmy następujący przykład, który definiuje `parallel_find_answer` funkcji, która wyszukuje element podana tablica, która spełnia podane funkcji predykatu. Gdy funkcja predykatu zwraca **true**, tworzy równoległy funkcja pracy `Answer` obiektu i anuluje całego zadania.

[!code-cpp[concrt-blocking-cancel#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_13.cpp)]

`new` Operator wykonuje alokacji stosu, która może spowodować zablokowanie. Środowisko uruchomieniowe wykonuje inne prace, tylko wtedy, gdy zadanie wykonuje cooperative, blokuje wywołania, takie jak wywołanie [concurrency::critical_section::lock](reference/critical-section-class.md#lock).

Poniższy przykład pokazuje, jak można uniknąć niepotrzebnych, a przez to zwiększyć wydajność. W tym przykładzie anuluje grupy zadań, zanim przydziela magazyn dla `Answer` obiektu.

[!code-cpp[concrt-blocking-cancel#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_14.cpp)]

[[Górnej](#top)]

##  <a name="shared-writes"></a> Nie wpisuj do współdzielonych danych w pętli równoległej

Środowisko uruchomieniowe współbieżności udostępnia kilka struktur danych, na przykład [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md), synchronizowanych równoczesny dostęp do udostępnionych danych. Te struktury danych są przydatne w wielu przypadkach, na przykład wiele zadań rzadko wymagają dostępu do zasobu.

Rozważmy następujący przykład, który używa [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytmu i `critical_section` obiektu do obliczenia liczby liczb pierwszych w [std::array](../../standard-library/array-class-stl.md) obiektu. W tym przykładzie nie skaluje się, ponieważ każdy wątek musi czekać na dostęp do współdzielonej zmiennej `prime_sum`.

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_15.cpp)]

W tym przykładzie również może prowadzić do pogorszenia wydajności, ponieważ często operacji blokowania skutecznie serializuje pętli. Ponadto kiedy obiekt środowiska uruchomieniowego współbieżności wykonuje operację blokowania, harmonogram może utworzyć dodatkowy wątek może wykonywać inne zadania, gdy pierwszy wątek oczekuje na dane. Jeśli środowisko uruchomieniowe tworzy wiele wątków, ponieważ wiele zadań oczekują na udostępnionych danych, aplikacja może działać nieprawidłowo lub przejść w stan zasobów.

PPL definiuje [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) klasy, która pomaga wyeliminować udostępnionego stanu, zapewniając dostęp do zasobów udostępnionych w sposób, wolne od blokady. `combinable` Klasa udostępnia magazynu wątków lokalnych, który pozwala wykonywać precyzyjną obliczeń, a następnie scalić te obliczenia na wynik końcowy. Można potraktować `combinable` obiektu jako zmienną redukcyjną.

Poniższy przykład modyfikuje poprzedni, za pomocą `combinable` zamiast obiektu `critical_section` obiektu do obliczania sumy. W tym przykładzie jest skalowana, ponieważ każdy wątek nałoży własnej kopii lokalnej sumy. W tym przykładzie użyto [concurrency::combinable::combine](reference/combinable-class.md#combine) metodę, aby scalić lokalnego obliczeń na wynik końcowy.

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_16.cpp)]

Aby uzyskać pełną wersję tego przykładu, zobacz [jak: Korzystanie z wyników połączonych do poprawiania wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md). Aby uzyskać więcej informacji na temat `combinable` klasy, zobacz [równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md).

[[Górnej](#top)]

##  <a name="false-sharing"></a> Jeśli to możliwe, unikaj niezamierzonego współdzielenia

*Niezamierzonego współdzielenia* występuje, gdy wiele współbieżnych zadań, które są uruchomione na oddzielnych procesorów zapisu zmiennych, które znajdują się na tym samym wierszu pamięci podręcznej. Gdy jedno zadanie zapisuje dane w jednym zmiennych, zostaje unieważniony wiersza pamięci podręcznej dla obu zmiennych. Każdy procesor trzeba ponownie załadować wiersza pamięci podręcznej ilekroć dany zostaje unieważniony wiersza pamięci podręcznej. W związku z tym niezamierzonego współdzielenia może spowodować obniżenie wydajności w aplikacji.

Następujący przykład podstawowy pokazuje dwóch zadań jednoczesnych każdego zwiększyć wartości zmiennej licznika udostępnionych.

[!code-cpp[concrt-false-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_17.cpp)]

Aby wyeliminować, udostępnianie danych między dwa zadania, można zmodyfikować przykład, aby używał dwie zmienne liczników. W tym przykładzie oblicza wartość licznika końcowe po zakończeniu zadania. Jednak ten przykład ilustruje niezamierzonego współdzielenia, ponieważ zmienne `count1` i `count2` mogą znajdować się na tym samym wierszu pamięci podręcznej.

[!code-cpp[concrt-false-sharing#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_18.cpp)]

Jednym ze sposobów, aby wyeliminować niezamierzonego współdzielenia jest upewnij się, że zmienne liczników w pamięci podręcznej w osobnych wierszach. Poniższy przykład wyrównuje zmienne `count1` i `count2` na 64-bajtowych granicach.

[!code-cpp[concrt-false-sharing#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_19.cpp)]

W tym przykładzie przyjęto założenie, że rozmiar pamięci podręcznej wynosi 64 lub mniej bajtów.

Firma Microsoft zaleca użycie [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) klasy podczas musi udostępniać dane między zadaniami. `combinable` Klasy tworzy zmiennymi lokalnymi wątku w taki sposób, że jest mniej prawdopodobne niezamierzonego współdzielenia. Aby uzyskać więcej informacji na temat `combinable` klasy, zobacz [równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md).

[[Górnej](#top)]

##  <a name="lifetime"></a> Upewnij się, że zmienne są ważne przez cały okres istnienia zadania

Jeśli podasz wyrażenia lambda do grupy zadań lub algorytmu równoległego, klauzula przechwytywania określa, czy treść wyrażenia lambda uzyskuje dostęp do zmiennych w zasięgu, przez wartość lub przez odwołanie. Podczas przekazywania zmiennych do wyrażenia lambda przez odniesienie, musisz gwarantować, że okres istnienia tej zmiennej będzie się powtarzał, zakończenie zadania.

Rozważmy następujący przykład, który definiuje `object` klasy i `perform_action` funkcji. `perform_action` Funkcja tworzy `object` zmiennej i asynchronicznie wykonuje jakąś akcję na tej zmiennej. Ponieważ zadanie nie jest gwarantowana dopiero po zakończeniu `perform_action` funkcja zwraca będzie awarii lub wykazują nieokreślone zachowanie, jeśli `object` zmienna jest niszczony, kiedy zadanie jest uruchomione.

[!code-cpp[concrt-lambda-lifetime#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_20.cpp)]

W zależności od wymagań aplikacji można użyć jednej z następujących technik do zagwarantowania, że zmienne zachować ważność przez cały okres istnienia każdego zadania.

Poniższy przykład przekazuje `object` zmiennej przez wartość do zadania. W związku z tym zadanie działa na własną kopię zmiennej.

[!code-cpp[concrt-lambda-lifetime#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_21.cpp)]

Ponieważ `object` zmienna jest przekazywany przez wartość, zmiany stanu występujących w tej zmiennej nie są wyświetlane w oryginalnej kopii.

W poniższym przykładzie użyto [CONCURRENCY::task_group:: wait](reference/task-group-class.md#wait) metody, aby upewnić się, że zadanie kończy się przed `perform_action` funkcja zwraca.

[!code-cpp[concrt-lambda-lifetime#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_22.cpp)]

Ponieważ zadanie zakończy teraz zanim funkcja zwróci, `perform_action` funkcja nie jest już działa asynchronicznie.

Poniższy przykład modyfikuje `perform_action` funkcję, aby wykonać odwołanie do `object` zmiennej. Obiekt wywołujący musi zagwarantować, że okres istnienia `object` zmienna jest prawidłowy, przed zakończeniem zadania.

[!code-cpp[concrt-lambda-lifetime#4](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_23.cpp)]

Wskaźnik umożliwia również kontrolować okres istnienia obiektu, który jest przekazywany do grupy zadań lub algorytmu równoległego.

Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażeń Lambda](../../cpp/lambda-expressions-in-cpp.md).

[[Górnej](#top)]

## <a name="see-also"></a>Zobacz także

[Środowisko uruchomieniowe współbieżności — najlepsze praktyki](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[Anulowanie w PPL](cancellation-in-the-ppl.md)<br/>
[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Przewodnik: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[Instrukcje: używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br/>
[Instrukcje: używanie anulowania, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br/>
[Instrukcje: korzystanie z wyników połączonych do poprawiania wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
[Biblioteka agentów asynchronicznych — najlepsze praktyki](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br/>
[Środowisko uruchomieniowe współbieżności — najlepsze praktyki ogólne](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)
