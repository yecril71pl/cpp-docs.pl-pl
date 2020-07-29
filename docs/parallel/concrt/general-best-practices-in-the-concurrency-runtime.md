---
title: Współbieżność środowiska wykonawczego — Najlepsze praktyki ogólne
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, general best practices
ms.assetid: ce5c784c-051e-44a6-be84-8b3e1139c18b
ms.openlocfilehash: 77ca8acbd3dedc28aaa6c330c3e91ed09046d162
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228456"
---
# <a name="general-best-practices-in-the-concurrency-runtime"></a>Współbieżność środowiska wykonawczego — Najlepsze praktyki ogólne

W tym dokumencie opisano najlepsze rozwiązania dotyczące wielu obszarów środowisko uruchomieniowe współbieżności.

## <a name="sections"></a><a name="top"></a>Poszczególne

Ten dokument zawiera następujące sekcje:

- [Jeśli jest to możliwe, używaj konstrukcji synchronizacji z spółdzielni](#synchronization)

- [Unikaj długotrwałych zadań, które nie są wynikiem](#yield)

- [Używanie nadsubskrypcji do operacji przesunięcia, które blokują lub mają duże opóźnienia](#oversubscription)

- [Używanie współbieżnych funkcji zarządzania pamięcią, gdy jest to możliwe](#memory)

- [Zarządzanie okresem istnienia obiektów współbieżności za pomocą RAII](#raii)

- [Nie twórz obiektów współbieżności w zakresie globalnym](#global-scope)

- [Nie używaj obiektów współbieżności w wspólnych segmentach danych](#shared-data)

## <a name="use-cooperative-synchronization-constructs-when-possible"></a><a name="synchronization"></a>Jeśli jest to możliwe, używaj konstrukcji synchronizacji z spółdzielni

Środowisko uruchomieniowe współbieżności udostępnia wiele konstrukcji bezpiecznych z współbieżnością, które nie wymagają zewnętrznego obiektu synchronizacji. Na przykład Klasa [concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) zapewnia bezpieczne współbieżność operacji dołączania i dostępu do elementów. W tym miejscu są zawsze ważne wskaźniki lub Iteratory, które są bezpieczne. Nie jest to gwarancja inicjalizacji elementu lub konkretnej kolejności przechodzenia. Jednakże w przypadku, gdy wymagany jest wyłączny dostęp do zasobu, środowisko uruchomieniowe udostępnia klasy [concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md), [concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)i [concurrency:: Event](../../parallel/concrt/reference/event-class.md) Classes. Te typy działają wspólnie; w związku z tym harmonogram zadań może ponownie przydzielić zasoby przetwarzania do innego kontekstu, gdy pierwsze zadanie czeka na dane. Jeśli jest to możliwe, należy używać tych typów synchronizacji zamiast innych mechanizmów synchronizacji, takich jak te udostępniane przez interfejs API systemu Windows, które nie są współdziałać ze sobą. Aby uzyskać więcej informacji na temat tych typów synchronizacji i przykładu kodu, zobacz [struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md) i [Porównywanie struktur danych synchronizacji z interfejsem API systemu Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).

[[Top](#top)]

## <a name="avoid-lengthy-tasks-that-do-not-yield"></a><a name="yield"></a>Unikaj długotrwałych zadań, które nie są wynikiem

Ze względu na to, że harmonogram zadań działa wspólnie, nie zapewnia godziwych zadań. W związku z tym zadanie może uniemożliwić uruchomienie innych zadań. Chociaż jest to dopuszczalne w niektórych przypadkach, może to spowodować zakleszczenie lub przetrzymanie.

Poniższy przykład wykonuje więcej zadań niż liczba przydzieloną zasobów przetwarzania. Pierwsze zadanie nie zwraca harmonogramu zadań, a w związku z tym drugie zadanie nie zostanie uruchomione do momentu zakończenia pierwszego zadania.

[!code-cpp[concrt-cooperative-tasks#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_1.cpp)]

Ten przykład generuje następujące wyniki:

1: 250000000 1: 500000000 1: 750000000 1: 1000000000 2: 250000000 2: 500000000 2: 750000000 2: 1000000000

Istnieje kilka sposobów na włączenie współpracy między tymi dwoma zadaniami. Jednym ze sposobów jest sporadyczne przekazanie harmonogramu zadań w długotrwałym zadaniu. Poniższy przykład modyfikuje `task` funkcję w celu wywołania metody [concurrency:: Context:: Yield](reference/context-class.md#yield) w celu uzyskania wykonania do harmonogramu zadań, aby można było uruchomić inne zadanie.

[!code-cpp[concrt-cooperative-tasks#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_2.cpp)]

Ten przykład generuje następujące wyniki:

```Output
1: 250000000
2: 250000000
1: 500000000
2: 500000000
1: 750000000
2: 750000000
1: 1000000000
2: 1000000000
```

`Context::Yield`Metoda daje tylko inny aktywny wątek w harmonogramie, do którego należy bieżący wątek, zadanie lekkie lub inny wątek systemu operacyjnego. Ta metoda nie jest obsługiwana w przypadku pracy zaplanowanej do uruchomienia w obiekcie [concurrency:: task_group](reference/task-group-class.md) lub [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) , ale jeszcze nie została uruchomiona.

Istnieją inne sposoby włączania współpracy między długotrwałymi zadaniami. Duże zadanie można podzielić na mniejsze podzadania. Można również włączyć nadsubskrypcję podczas długotrwałego zadania. Nadsubskrypcja umożliwia tworzenie większej liczby wątków niż dostępna liczba wątków sprzętowych. Nadpłata jest szczególnie przydatna, gdy długotrwałe zadanie zawiera duże opóźnienie, na przykład odczytanie danych z dysku lub z połączenia sieciowego. Aby uzyskać więcej informacji na temat uproszczonych zadań i nadmiarowych, zobacz [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[[Top](#top)]

## <a name="use-oversubscription-to-offset-operations-that-block-or-have-high-latency"></a><a name="oversubscription"></a>Używanie nadsubskrypcji do operacji przesunięcia, które blokują lub mają duże opóźnienia

Środowisko uruchomieniowe współbieżności zawiera elementy pierwotne synchronizacji, takie jak [concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md), które umożliwiają wykonywanie zadań wspólnie ze sobą. Po przeniesieniu lub przeniesieniu jednego zadania w górę, harmonogram zadań może ponownie przydzielić zasoby przetwarzania do innego kontekstu, gdy pierwsze zadanie czeka na dane.

Istnieją przypadki, w których nie można używać wspólnego mechanizmu blokowania, który jest dostarczany przez środowisko uruchomieniowe współbieżności. Na przykład biblioteka zewnętrzna, z której korzystasz, może korzystać z innego mechanizmu synchronizacji. Innym przykładem jest wykonanie operacji, która może mieć wysokie opóźnienie, na przykład w przypadku używania funkcji Windows API `ReadFile` do odczytywania danych z połączenia sieciowego. W takich przypadkach nadsubskrybowanie może umożliwić uruchomienie innych zadań, gdy inne zadanie jest w stanie bezczynności. Nadsubskrypcja umożliwia tworzenie większej liczby wątków niż dostępna liczba wątków sprzętowych.

Weź pod uwagę następującą funkcję, `download` która pobiera plik pod podanym adresem URL. W tym przykładzie zastosowano metodę [concurrency:: Context:: subsubskrybuj](reference/context-class.md#oversubscribe) , aby tymczasowo zwiększyć liczbę aktywnych wątków.

[!code-cpp[concrt-download-oversubscription#4](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_3.cpp)]

Ponieważ `GetHttpFile` Funkcja wykonuje potencjalnie operację ukrytego, nadsubskrypcja może umożliwić uruchamianie innych zadań, ponieważ bieżące zadanie czeka na dane. Aby zapoznać się z pełną wersją tego przykładu, zobacz [How to: use resubscription to offset](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).

[[Top](#top)]

## <a name="use-concurrent-memory-management-functions-when-possible"></a><a name="memory"></a>Używanie współbieżnych funkcji zarządzania pamięcią, gdy jest to możliwe

Użyj funkcji zarządzania pamięcią [concurrency:: Alloc](reference/concurrency-namespace-functions.md#alloc) i [concurrency:: Free](reference/concurrency-namespace-functions.md#free), gdy masz szczegółowe zadania, które często przydzielają małe obiekty, które mają stosunkowo krótki okres istnienia. Środowisko uruchomieniowe współbieżności przechowuje osobną pamięć podręczną pamięci dla każdego działającego wątku. `Alloc`Funkcje i `Free` przydzielają i zwalniają pamięć z tych pamięci podręcznych bez użycia blokad lub barier pamięci.

Aby uzyskać więcej informacji na temat tych funkcji zarządzania pamięcią, zobacz [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Aby zapoznać się z przykładem korzystającym z tych funkcji, zobacz [How to: use a free by zwiększyć wydajność pamięci](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).

[[Top](#top)]

## <a name="use-raii-to-manage-the-lifetime-of-concurrency-objects"></a><a name="raii"></a>Zarządzanie okresem istnienia obiektów współbieżności za pomocą RAII

Środowisko uruchomieniowe współbieżności używa obsługi wyjątków do implementowania funkcji, takich jak anulowanie. W związku z tym napisz kod bezpieczny przed wyjątkami podczas wywoływania do środowiska uruchomieniowego lub wywołać inną bibliotekę, która wywołuje środowisko uruchomieniowe.

Wzorzec *pozyskiwania zasobów jest inicjalizacją* (RAII) jest jednym ze sposobów na bezpieczne zarządzanie okresem istnienia obiektu współbieżności w danym zakresie. Pod wzorcem RAII, struktura danych jest przypisana na stosie. Ta struktura danych inicjuje lub uzyskuje zasób podczas jego tworzenia i niszczy lub zwalnia ten zasób, gdy struktura danych zostanie zniszczona. Wzorzec RAII gwarantuje, że destruktor jest wywoływany przed wyjściem z otaczającego zakresu. Ten wzorzec jest przydatny, gdy funkcja zawiera wiele **`return`** instrukcji. Ten wzorzec pomaga również napisać kod zabezpieczony przed wyjątkami. Gdy **`throw`** instrukcja powoduje odwinięcie stosu, destruktor dla obiektu RAII jest wywoływany; w związku z tym zasób jest zawsze poprawnie usunięty lub wydano.

Środowisko uruchomieniowe definiuje kilka klas, które używają wzorca RAII, na przykład [concurrency:: critical_section:: scoped_lock](../../parallel/concrt/reference/critical-section-class.md#critical_section__scoped_lock_class) i [concurrency:: reader_writer_lock:: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class). Te klasy pomocnika są nazywane *blokadami objętymi zakresem*. Klasy te oferują kilka korzyści podczas pracy z obiektami [concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) lub [concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) . Konstruktor tych klas uzyskuje dostęp do podanego `critical_section` lub `reader_writer_lock` obiektu; destruktor zwalnia dostęp do tego obiektu. Ponieważ blokada zakresu zwalnia dostęp do jego wzajemnego wykluczenia, gdy zostanie zniszczony, nie należy ręcznie odblokować bazowego obiektu.

Rozważmy następujące klasy, `account` zdefiniowane przez bibliotekę zewnętrzną, dlatego nie można ich modyfikować.

[!code-cpp[concrt-account-transactions#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_4.h)]

Poniższy przykład wykonuje równolegle wiele transakcji względem `account` obiektu. W przykładzie używany jest `critical_section` obiekt do synchronizowania dostępu do `account` obiektu, ponieważ `account` Klasa nie jest bezpieczna pod kątem współbieżności. Każda operacja równoległa używa `critical_section::scoped_lock` obiektu w celu zagwarantowania, że `critical_section` obiekt jest odblokowany, gdy operacja zakończy się powodzeniem lub niepowodzeniem. Gdy saldo konta jest ujemne, `withdraw` operacja kończy się niepowodzeniem, zwracając wyjątek.

[!code-cpp[concrt-account-transactions#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_5.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe:

```Output
Balance before deposit: 1924
Balance after deposit: 2924
Balance before withdrawal: 2924
Balance after withdrawal: -76
Balance before withdrawal: -76
Error details:
    negative balance: -76
```

Aby uzyskać dodatkowe przykłady, które wykorzystują wzorzec RAII do zarządzania okresem istnienia obiektów współbieżności, zobacz [Przewodnik: usuwanie pracy z wątku interfejsu użytkownika](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md), [instrukcje: użycie klasy kontekstu w celu zaimplementowania semafora](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)i [instrukcje: Użyj nadsubskrypcji, aby przesunięty czas oczekiwania](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).

[[Top](#top)]

## <a name="do-not-create-concurrency-objects-at-global-scope"></a><a name="global-scope"></a>Nie twórz obiektów współbieżności w zakresie globalnym

Podczas tworzenia obiektu współbieżności w zakresie globalnym można spowodować problemy, takie jak zakleszczenie lub naruszenie dostępu do pamięci w aplikacji.

Na przykład podczas tworzenia obiektu środowisko uruchomieniowe współbieżności środowisko uruchomieniowe tworzy domyślny harmonogram, jeśli nie został jeszcze utworzony. Obiekt środowiska uruchomieniowego tworzony podczas konstruowania obiektu globalnego będzie odpowiednio powodował, że środowisko uruchomieniowe utworzy ten domyślny harmonogram. Jednak ten proces korzysta z blokady wewnętrznej, co może zakłócać inicjalizację innych obiektów, które obsługują infrastrukturę środowisko uruchomieniowe współbieżności. Ta wewnętrzna blokada może być wymagana przez inny obiekt infrastruktury, który nie został jeszcze zainicjowany i w rezultacie może spowodować zakleszczenie w aplikacji.

Poniższy przykład ilustruje tworzenie globalnego obiektu [concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) . Ten wzorzec dotyczy nie tylko klasy, `Scheduler` ale wszystkie inne typy, które są dostarczane przez środowisko uruchomieniowe współbieżności. Zalecamy, aby nie przestrzegać tego wzorca, ponieważ może to spowodować nieoczekiwane zachowanie aplikacji.

[!code-cpp[concrt-global-scheduler#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_6.cpp)]

Przykłady poprawnego sposobu tworzenia obiektów można `Scheduler` znaleźć w temacie [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[[Top](#top)]

## <a name="do-not-use-concurrency-objects-in-shared-data-segments"></a><a name="shared-data"></a>Nie używaj obiektów współbieżności w wspólnych segmentach danych

Środowisko uruchomieniowe współbieżności nie obsługuje używania obiektów współbieżności w sekcji danych udostępnionych, na przykład sekcji danych utworzonej przez dyrektywę [data_seg](../../preprocessor/data-seg.md) `#pragma` . Obiekt współbieżności współużytkowany przez granice procesu może spowodować, że środowisko uruchomieniowe jest w niespójnym lub nieprawidłowym stanie.

[[Top](#top)]

## <a name="see-also"></a>Zobacz także

[środowisko uruchomieniowe współbieżności najlepszych praktyk](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[Biblioteka równoległych wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Porównywanie struktur danych synchronizacji z interfejsem API systemu Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
[Instrukcje: korzystanie z Alloc i Free w celu zwiększenia wydajności pamięci](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)<br/>
[Instrukcje: używanie nadsubskrypcji do opóźnienia przesunięcia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)<br/>
[Instrukcje: korzystanie z klasy kontekstu w celu zaimplementowania współdziałania ze wspólnym semaforem](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[Przewodnik: usuwanie pracy z wątku interfejsu użytkownika](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)<br/>
[Najlepsze rozwiązania w bibliotece równoległych wzorców](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[Najlepsze rozwiązania w bibliotece agentów asynchronicznych](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)
