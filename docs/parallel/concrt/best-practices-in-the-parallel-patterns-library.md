---
title: Biblioteka wzorów równoległych — Najlepsze praktyki
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Patterns Library, practices to avoid
- practices to avoid, Parallel Patterns Library
- best practices, Parallel Patterns Library
- Parallel Patterns Library, best practices
ms.assetid: e43e0304-4d54-4bd8-a3b3-b8673559a9d7
ms.openlocfilehash: 641d85b03fca13a6592610d87563e3e701ad3e3e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142088"
---
# <a name="best-practices-in-the-parallel-patterns-library"></a>Biblioteka wzorów równoległych — Najlepsze praktyki

W tym dokumencie opisano, jak najlepiej korzystać z biblioteki równoległych wzorców (PPL). PPL zawiera kontenery ogólnego przeznaczenia, obiekty i algorytmy umożliwiające wykonywanie współbieżności.

Aby uzyskać więcej informacji na temat PPL, zobacz [Biblioteka wzorców równoległych (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md).

## <a name="top"></a>Poszczególne

Ten dokument zawiera następujące sekcje:

- [Nie Zrównoleglaniej małych ciał pętli](#small-loops)

- [Express Parallels na najwyższym możliwym poziomie](#highest)

- [Użyj parallel_invoke, aby rozwiązać problemy z dzieleniem i rządź](#divide-and-conquer)

- [Użyj anulowania lub obsługi wyjątków, aby przerwać pętlę równoległą](#breaking-loops)

- [Zrozumienie, jak anulowanie i obsługa wyjątków wpływają na zniszczenie obiektu](#object-destruction)

- [Nie blokuj wielokrotnie w pętli równoległej](#repeated-blocking)

- [Nie wykonuj operacji blokowania po anulowaniu pracy równoległej](#blocking)

- [Nie zapisuj danych udostępnionych w pętli równoległej](#shared-writes)

- [Jeśli to możliwe, unikaj udostępniania fałszywych](#false-sharing)

- [Upewnij się, że zmienne są prawidłowe przez cały okres istnienia zadania](#lifetime)

## <a name="small-loops"></a>Nie Zrównoleglaniej małych ciał pętli

Przetwarzanie równoległe stosunkowo małych zbiorników może spowodować obciążenie związane z planowaniem, aby przekroczyć zalety przetwarzania równoległego. Rozważmy poniższy przykład, który dodaje każdą parę elementów w dwóch tablicach.

[!code-cpp[concrt-small-loops#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_1.cpp)]

Obciążenie dla każdej iteracji pętli równoległej jest zbyt małe, aby można było skorzystać z obciążania przetwarzania równoległego. Możesz zwiększyć wydajność tej pętli, wykonując więcej pracy w pętli lub wykonując pętlę szeregowo.

[[Top](#top)]

## <a name="highest"></a>Express Parallels na najwyższym możliwym poziomie

W przypadku zrównoleglanie kodu tylko na niskim poziomie można wprowadzić konstrukcję do przyłączania rozwidlenia, która nie jest skalowana w miarę wzrostu liczby procesorów. Konstrukcja *rozwidlenia Join* to konstrukcja, w której jedno zadanie dzieli swoją pracę na mniejsze podzadania równoległe i czeka na zakończenie tych podzadań. Każde podzadanie może rekursywnie podzielić się na dodatkowe podzadania.

Chociaż model łączenia rozwidlenia może być przydatny do rozwiązywania różnych problemów, istnieją sytuacje, w których obciążenie synchronizacji może obniżyć skalowalność. Rozważmy na przykład następujący kod seryjny, który przetwarza dane obrazu.

[!code-cpp[concrt-image-processing-filter#20](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_2.cpp)]

Ponieważ każda iteracja pętli jest niezależna, można zrównoleglanie większość pracy, jak pokazano w poniższym przykładzie. W tym przykładzie zastosowano algorytm [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) , aby zrównoleglanie pętlę zewnętrzną.

[!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_3.cpp)]

Poniższy przykład ilustruje konstrukcję łączenia rozwidlenia, wywołując funkcję `ProcessImage` w pętli. Każde wywołanie `ProcessImage` nie zwraca do momentu zakończenia każdego zadania podrzędnego.

[!code-cpp[concrt-image-processing-filter#21](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_4.cpp)]

Jeśli każda iteracja pętli równoległej wykonuje niemal brak pracy lub pracy wykonywanej przez pętlę równoległą jest niezrównoważona, to oznacza, że niektóre iteracje pętli trwają dłużej niż inne, obciążenie związane z planowaniem, które jest wymagane do częstego rozwidlenia i przyłączania pracy, może Skorzystaj z zalet wykonywania równoległego. Ten koszt zwiększa się wraz ze wzrostem liczby procesorów.

Aby zmniejszyć liczbę obciążeń związanych z planowaniem w tym przykładzie, możesz zrównoleglanie zewnętrzne pętle przed zrównoleglanie pętlami wewnętrznymi lub użyć innej konstrukcji równoległej, takiej jak przetwarzanie potokowe. Poniższy przykład modyfikuje funkcję `ProcessImages`, aby użyć algorytmu [concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) do zrównoleglanie pętli zewnętrznej.

[!code-cpp[concrt-image-processing-filter#22](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_5.cpp)]

W podobnym przykładzie, który używa potoku do równoległego przetwarzania obrazu, zobacz [Przewodnik: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

[[Top](#top)]

## <a name="divide-and-conquer"></a>Użyj parallel_invoke, aby rozwiązać problemy z dzieleniem i rządź

Problem z *dzieleniem i rządź* jest postacią konstrukcji rozwidlenia, która używa rekursji do dzielenia zadania na podzadania. Oprócz klas [concurrency:: task_group](reference/task-group-class.md) i [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) , można również użyć algorytmu [concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) , aby rozwiązać problemy z dzieleniem i rządź. Algorytm `parallel_invoke` ma bardziej zwięzłą składnię niż obiekty grupy zadań i jest przydatny, gdy istnieje stała liczba zadań równoległych.

Poniższy przykład ilustruje użycie algorytmu `parallel_invoke`, aby zaimplementować algorytm sortowania bitonicznego.

[!code-cpp[concrt-parallel-bitonic-sort#12](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_6.cpp)]

Aby zmniejszyć obciążenie, algorytm `parallel_invoke` wykonuje ostatnią serię zadań w kontekście wywołującym.

Aby zapoznać się z pełną wersją tego przykładu, zobacz [How to: Use parallel_invoke by napisać równoległą procedurę sortowania](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md). Aby uzyskać więcej informacji na temat algorytmu `parallel_invoke`, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

[[Top](#top)]

## <a name="breaking-loops"></a>Użyj anulowania lub obsługi wyjątków, aby przerwać pętlę równoległą

PPL zapewnia dwa sposoby anulowania równoległej pracy wykonywanej przez grupę zadań lub algorytm równoległy. Jednym ze sposobów jest użycie mechanizmu anulowania, który jest dostarczany przez klasy [concurrency:: task_group](reference/task-group-class.md) i [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) . Innym sposobem jest zgłoszenie wyjątku w treści funkcji pracy zadania. Mechanizm anulowania jest bardziej wydajny niż obsługa wyjątków podczas anulowania drzewa równoległej pracy. *Równoległe drzewo robocze* jest grupą powiązanych grup zadań, w których niektóre grupy zadań zawierają inne grupy zadań. Mechanizm anulowania anuluje grupę zadań i jej podrzędne grupy zadań w sposób górny. Odwrotnie, obsługa wyjątków działa w sposób dolny i musi anulować każdą podrzędną grupę zadań niezależnie, ponieważ wyjątek jest propagowany w górę.

Podczas pracy bezpośrednio z obiektem grupy zadań Użyj metody [concurrency:: task_group:: Cancel](reference/task-group-class.md#cancel) lub [concurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) , aby anulować pracę, która należy do tej grupy zadań. Aby anulować algorytm równoległy, na przykład `parallel_for`, Utwórz nadrzędną grupę zadań i Anuluj tę grupę zadań. Rozważmy na przykład następującą funkcję, `parallel_find_any`, która wyszukuje wartość w tablicy równolegle.

[!code-cpp[concrt-parallel-array-search#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_7.cpp)]

Ponieważ algorytmy równoległe używają grup zadań, gdy jedna z iteracji równoległych anuluje nadrzędną grupę zadań, zadanie ogólne zostało anulowane. Aby uzyskać pełną wersję tego przykładu, zobacz [How to: use unanulowania, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md).

Chociaż obsługa wyjątków jest mniej wydajnym sposobem anulowania równoległej pracy niż mechanizm anulowania, istnieją przypadki, w których obsługa wyjątków jest odpowiednia. Na przykład następująca metoda `for_all`rekurencyjnie wykonuje funkcję roboczą na każdym węźle struktury `tree`. W tym przykładzie element członkowski danych `_children` jest [listą std::](../../standard-library/list-class.md) , która zawiera `tree` obiektów.

[!code-cpp[concrt-task-tree-search#6](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_8.cpp)]

Obiekt wywołujący metodę `tree::for_all` może zgłosić wyjątek, jeśli nie wymaga wywołania funkcji pracy dla każdego elementu drzewa. W poniższym przykładzie pokazano funkcję `search_for_value`, która wyszukuje wartość z podanego `tree` obiektu. Funkcja `search_for_value` używa funkcji służbowej, która zgłasza wyjątek, gdy bieżący element drzewa jest zgodny z podaną wartością. Funkcja `search_for_value` używa bloku `try-catch`, aby przechwycić wyjątek i wydrukować wynik do konsoli.

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_9.cpp)]

Aby zapoznać się z pełną wersją tego przykładu, zobacz [How to: use Exception obsługi wyjątków, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

Aby uzyskać więcej ogólnych informacji na temat mechanizmów anulowania i obsługi wyjątków, które są dostarczane przez PPL, zobacz [anulowania w PPL](cancellation-in-the-ppl.md) i [obsłudze wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

[[Top](#top)]

## <a name="object-destruction"></a>Zrozumienie, jak anulowanie i obsługa wyjątków wpływają na zniszczenie obiektu

W drzewie równoległych zadań zadanie, które zostało anulowane, uniemożliwia uruchomienie zadań podrzędnych. Może to spowodować problemy, jeśli jedno z zadań podrzędnych wykonuje operację, która jest ważna dla aplikacji, na przykład zwalniając zasób. Ponadto anulowanie zadania może spowodować, że wyjątek jest propagowany przez destruktor obiektu i spowodować niezdefiniowane zachowanie w aplikacji.

W poniższym przykładzie Klasa `Resource` opisuje zasób, a Klasa `Container` opisuje kontener, który zawiera zasoby. W swoim destruktorze Klasa `Container` wywołuje metodę `cleanup` na dwóch `Resource`ych składowych równolegle, a następnie wywołuje metodę `cleanup` z jej trzeciego `Resource`ego elementu członkowskiego.

[!code-cpp[concrt-parallel-resource-destruction#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_10.h)]

Chociaż ten wzorzec nie ma żadnych problemów, należy wziąć pod uwagę Poniższy kod, który uruchamia równolegle dwa zadania. Pierwsze zadanie tworzy obiekt `Container`, a drugie zadanie anuluje ogólne zadanie. Przykładowo używa dwóch obiektów [concurrency:: Event](../../parallel/concrt/reference/event-class.md) , aby upewnić się, że anulowanie następuje po utworzeniu obiektu `Container` i że obiekt `Container` zostanie zniszczony po wystąpieniu operacji anulowania.

[!code-cpp[concrt-parallel-resource-destruction#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_11.cpp)]

Ten przykład generuje następujące wyniki:

```Output
Container 1: Freeing resources...Exiting program...
```

Ten przykład kodu zawiera następujące problemy, które mogą spowodować zachowywać się inaczej niż oczekiwano:

- Anulowanie zadania nadrzędnego powoduje także anulowanie zadania podrzędnego, wywołanie metody [concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke). W związku z tym te dwa zasoby nie są zwalniane.

- Anulowanie zadania nadrzędnego powoduje zgłoszenie wewnętrznego wyjątku przez zadanie podrzędne. Ponieważ destruktor `Container` nie obsługuje tego wyjątku, wyjątek jest propagowany w górę, a trzeci zasób nie jest zwolniony.

- Wyjątek, który jest generowany przez zadanie podrzędne, jest propagowany przez destruktor `Container`. Wyrzucanie z destruktora powoduje umieszczenie aplikacji w niezdefiniowanym stanie.

Firma Microsoft zaleca, aby nie wykonywać operacji krytycznych, takich jak zwalnianie zasobów w zadaniach, chyba że można zagwarantować, że te zadania nie zostaną anulowane. Zalecamy również, aby nie używać funkcji środowiska uruchomieniowego, które mogą zgłaszać w destruktorze typów.

[[Top](#top)]

## <a name="repeated-blocking"></a>Nie blokuj wielokrotnie w pętli równoległej

Pętla równoległa, taka jak [współbieżność::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) lub [concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) , która jest zdominowana przez operacje blokowania może spowodować, że środowisko uruchomieniowe będzie tworzyć wiele wątków w krótkim czasie.

Środowisko uruchomieniowe współbieżności wykonuje dodatkową pracę po zakończeniu zadania lub przeniesieniu lub przeniesieniu ich w spółdzielnie. W przypadku jednego bloku iteracji pętli równoległej środowisko uruchomieniowe może rozpocząć kolejną iterację. Gdy nie ma dostępnych bezczynnych wątków, środowisko uruchomieniowe tworzy nowy wątek.

Gdy treść pętli równoległej jest sporadycznie blokowana, ten mechanizm ułatwia zmaksymalizowanie ogólnej przepływności zadań. Jednak w przypadku, gdy wiele iteracji blokuje, środowisko uruchomieniowe może utworzyć wiele wątków do uruchomienia dodatkowej pracy. Może to prowadzić do niedostatecznej ilości pamięci lub słabego wykorzystania zasobów sprzętowych.

Rozważmy następujący przykład, który wywołuje funkcję [concurrency:: Send](reference/concurrency-namespace-functions.md#send) w każdej iteracji pętli `parallel_for`. Ponieważ `send` blokuje się wspólnie, środowisko uruchomieniowe tworzy nowy wątek do uruchamiania dodatkowej pracy przy każdym wywołaniu `send`.

[!code-cpp[concrt-repeated-blocking#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_12.cpp)]

Zalecamy refaktoryzację kodu, aby uniknąć tego wzorca. W tym przykładzie można uniknąć tworzenia dodatkowych wątków, wywołując `send` w pętli `for` szeregowej.

[[Top](#top)]

## <a name="blocking"></a>Nie wykonuj operacji blokowania po anulowaniu pracy równoległej

Jeśli to możliwe, nie wykonuj operacji blokowania przed wywołaniem metody [concurrency:: task_group:: Cancel](reference/task-group-class.md#cancel) lub [concurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) , aby anulować pracę równoległą.

Gdy zadanie wykonuje operację blokowania, środowisko uruchomieniowe może wykonać inne czynności, gdy pierwsze zadanie czeka na dane. Środowisko uruchomieniowe ponownie planuje zadanie oczekujące po odblokowaniu. Środowisko uruchomieniowe zwykle ponownie planuje zadania, które były ostatnio odblokowane przed ponownym zaplanowaniem zadań, które były mniej ostatnio odblokowane. W związku z tym środowisko uruchomieniowe może zaplanować niepotrzebne działanie podczas operacji blokowania, co prowadzi do zmniejszenia wydajności. W związku z tym podczas wykonywania operacji blokowania przed anulowaniem pracy równoległej operacja blokowania może opóźnić wywołanie `cancel`. Powoduje to, że inne zadania mogą wykonać niepotrzebne działania.

Rozważmy poniższy przykład, który definiuje funkcję `parallel_find_answer`, która wyszukuje element dostarczonej tablicy, który spełnia podaną funkcję predykatu. Gdy funkcja predykatu zwraca **wartość true**, funkcja równoległej pracy tworzy obiekt `Answer` i anuluje ogólne zadanie.

[!code-cpp[concrt-blocking-cancel#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_13.cpp)]

Operator `new` wykonuje alokację sterty, która może być blokowana. Środowisko uruchomieniowe wykonuje inne czynności tylko wtedy, gdy zadanie wykonuje połączenie blokujące, takie jak wywołanie [concurrency:: critical_section:: Lock](reference/critical-section-class.md#lock).

Poniższy przykład pokazuje, jak zapobiec niepotrzebnej pracy, a tym samym zwiększyć wydajność. Ten przykład powoduje anulowanie grupy zadań przed przydzieleniem magazynu dla obiektu `Answer`.

[!code-cpp[concrt-blocking-cancel#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_14.cpp)]

[[Top](#top)]

## <a name="shared-writes"></a>Nie zapisuj danych udostępnionych w pętli równoległej

Środowisko uruchomieniowe współbieżności zawiera kilka struktur danych, na przykład [concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md), które synchronizują współbieżny dostęp do udostępnionych danych. Te struktury danych są przydatne w wielu przypadkach, na przykład wtedy, gdy wiele zadań rzadko wymaga dostępu współdzielonego do zasobu.

Rozważmy poniższy przykład, który używa algorytmu [concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) i obiektu `critical_section` do obliczenia liczby pierwszych numerów w obiekcie [std:: Array](../../standard-library/array-class-stl.md) . Ten przykład nie jest skalowany, ponieważ każdy wątek musi oczekiwać na uzyskanie dostępu do zmiennej udostępnionej `prime_sum`.

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_15.cpp)]

Ten przykład może również prowadzić do słabej wydajności, ponieważ częste operacje blokowania skutecznie serializować pętlę. Ponadto, gdy obiekt środowisko uruchomieniowe współbieżności wykonuje operację blokowania, harmonogram może utworzyć dodatkowy wątek, aby wykonać inną pracę, podczas gdy pierwszy wątek czeka na dane. Jeśli środowisko uruchomieniowe tworzy wiele wątków, ponieważ wiele zadań oczekuje na dane udostępnione, aplikacja może działać źle lub wprowadzić stan niskiego zasobu.

PPL definiuje klasę [concurrency::](../../parallel/concrt/reference/combinable-class.md) Shared, która pomaga wyeliminować współużytkowany stan, zapewniając dostęp do udostępnionych zasobów w sposób niezależny od blokady. Klasa `combinable` zapewnia magazyn lokalnych wątków, który umożliwia wykonywanie szczegółowych obliczeń, a następnie scalanie tych obliczeń w końcowy wynik. Obiekt `combinable` można traktować jako zmienną redukcji.

Poniższy przykład modyfikuje poprzednią wartość przy użyciu obiektu `combinable`, a nie obiektu `critical_section`, aby obliczyć sumę. Ten przykład skaluje się, ponieważ każdy wątek posiada własną lokalną kopię sum. W tym przykładzie zastosowano metodę [concurrency:: kombinowane::](reference/combinable-class.md#combine) Merge w celu scalenia lokalnych obliczeń w wyniku końcowym.

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_16.cpp)]

Aby zapoznać się z pełną wersją tego przykładu, zobacz [jak: używanie kombinacji w celu zwiększenia wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md). Aby uzyskać więcej informacji na temat klasy `combinable`, zobacz [Parallel Containers and Objects](../../parallel/concrt/parallel-containers-and-objects.md).

[[Top](#top)]

## <a name="false-sharing"></a>Jeśli to możliwe, unikaj udostępniania fałszywych

*Wartość FAŁSZ udostępniania* występuje, gdy wiele współbieżnych zadań, które są uruchomione na oddzielnych procesorach zapisu do zmiennych, które znajdują się w tej samej linii pamięci podręcznej. Gdy jedno zadanie zapisuje w jednej ze zmiennych, wiersz pamięci podręcznej dla obu zmiennych jest unieważniony. Każdy procesor musi ponownie załadować wiersz pamięci podręcznej za każdym razem, gdy wiersz pamięci podręcznej jest unieważniony. W związku z tym fałszywe udostępnianie może spowodować spadek wydajności aplikacji.

W poniższym przykładzie podstawowym przedstawiono dwa współbieżne zadania, które zwiększają zmienną licznika udostępnionego.

[!code-cpp[concrt-false-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_17.cpp)]

Aby wyeliminować udostępnianie danych między tymi dwoma zadaniami, można zmodyfikować przykład, aby użyć dwóch zmiennych licznika. Ten przykład oblicza końcową wartość licznika po zakończeniu zadań. Jednak ten przykład ilustruje wartość FAŁSZ udostępniania, ponieważ zmienne `count1` i `count2` mogą znajdować się w tej samej linii pamięci podręcznej.

[!code-cpp[concrt-false-sharing#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_18.cpp)]

Jednym ze sposobów wyeliminowania wartościowego udostępniania jest upewnienie się, że zmienne licznika znajdują się w osobnych wierszach pamięci podręcznej. Poniższy przykład wyrównuje zmienne `count1` i `count2` na 64-bajtowych granicach.

[!code-cpp[concrt-false-sharing#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_19.cpp)]

W tym przykładzie przyjęto założenie, że rozmiar pamięci podręcznej pamięci wynosi 64 lub mniej bajtów.

Zaleca się użycie klasy [concurrency:: prekombinowanej](../../parallel/concrt/reference/combinable-class.md) , gdy konieczne jest udostępnianie danych między zadaniami. Klasa `combinable` tworzy zmienne lokalne wątku w taki sposób, że fałszywe udostępnianie jest mniej podobne. Aby uzyskać więcej informacji na temat klasy `combinable`, zobacz [Parallel Containers and Objects](../../parallel/concrt/parallel-containers-and-objects.md).

[[Top](#top)]

## <a name="lifetime"></a>Upewnij się, że zmienne są prawidłowe przez cały okres istnienia zadania

Gdy podajesz wyrażenie lambda do grupy zadań lub algorytmu równoległego, klauzula przechwytywania określa, czy treść wyrażenia lambda uzyskuje dostęp do zmiennych w otaczającym zakresie przez wartość lub przez odwołanie. Gdy zmienne są przekazywane do wyrażenia lambda przez odwołanie, należy zagwarantować, że okres istnienia tej zmiennej będzie trwały do momentu zakończenia zadania.

Rozważmy następujący przykład, który definiuje klasę `object` i funkcję `perform_action`. Funkcja `perform_action` tworzy zmienną `object` i wykonuje pewne akcje dla tej zmiennej asynchronicznie. Ponieważ zadanie nie zostanie ukończone przed zwróceniem przez funkcję `perform_action`, program ulegnie awarii lub wykryje nieokreślone zachowanie, jeśli zmienna `object` zostanie zniszczona, gdy zadanie jest uruchomione.

[!code-cpp[concrt-lambda-lifetime#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_20.cpp)]

W zależności od wymagań aplikacji można użyć jednej z następujących technik w celu zagwarantowania, że zmienne pozostają ważne przez cały okres istnienia każdego zadania.

Poniższy przykład przekazuje do zadania zmienną `object` według wartości. W związku z tym zadanie działa na własnej kopii zmiennej.

[!code-cpp[concrt-lambda-lifetime#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_21.cpp)]

Ponieważ zmienna `object` jest przenoszona przez wartość, wszelkie zmiany stanu występujące w tej zmiennej nie są wyświetlane w oryginalnej kopii.

W poniższym przykładzie zastosowano metodę [concurrency:: task_group:: wait](reference/task-group-class.md#wait) , aby upewnić się, że zadanie zostało zakończone przed zwróceniem przez funkcję `perform_action`.

[!code-cpp[concrt-lambda-lifetime#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_22.cpp)]

Ponieważ zadanie kończy się teraz przed zwróceniem przez funkcję, funkcja `perform_action` nie zachowuje już asynchronicznie.

Poniższy przykład modyfikuje funkcję `perform_action`, aby pobrać odwołanie do zmiennej `object`. Obiekt wywołujący musi zagwarantować, że okres istnienia zmiennej `object` jest ważny do momentu zakończenia zadania.

[!code-cpp[concrt-lambda-lifetime#4](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_23.cpp)]

Możesz również użyć wskaźnika, aby kontrolować okres istnienia obiektu przekazanego do grupy zadań lub algorytmu równoległego.

Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [lambda Expressions](../../cpp/lambda-expressions-in-cpp.md).

[[Top](#top)]

## <a name="see-also"></a>Zobacz też

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
