---
title: Współbieżność środowiska wykonawczego — Najlepsze praktyki ogólne
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, general best practices
ms.assetid: ce5c784c-051e-44a6-be84-8b3e1139c18b
ms.openlocfilehash: e25011e2466d76c946cc55421ed228c8ea174161
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413921"
---
# <a name="general-best-practices-in-the-concurrency-runtime"></a>Współbieżność środowiska wykonawczego — Najlepsze praktyki ogólne

W tym dokumencie opisano najlepsze rozwiązania, które mają zastosowanie do wielu obszarów w czasie wykonywania współbieżności.

##  <a name="top"></a> Sekcje

Ten dokument zawiera następujące sekcje:

- [Użyj Konstruktów Kooperatywnej synchronizacji, gdy jest to możliwe](#synchronization)

- [Unikaj długich zadań, które nie dają wyniku](#yield)

- [Używanie Nadsubskrypcji operacji przesunięcia, która blokuje lub odznacza duże opóźnienie](#oversubscription)

- [Użyj funkcji zarządzania pamięcią Współbieżną, jeśli jest to możliwe](#memory)

- [Użyj RAII, aby zarządzać okresem istnienia obiektów współbieżnych](#raii)

- [Nie twórz obiektów współbieżności w zakresie globalnym](#global-scope)

- [Nie używaj obiektów współbieżności w segmentach współdzielonych danych](#shared-data)

##  <a name="synchronization"></a> Użyj Konstruktów Kooperatywnej synchronizacji, gdy jest to możliwe

Środowisko uruchomieniowe współbieżności udostępnia wiele konstrukcji bezpieczne pod względem współbieżności, które nie wymagają obiektu zewnętrznego synchronizacji. Na przykład [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) klasa udostępnia bezpieczne pod względem współbieżności dołączania i element dostęp do operacji. W przypadkach, gdy wymagają wyłącznego dostępu do zasobu, środowisko wykonawcze zapewnia jednak [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md), [concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md), i [współbieżności :: zdarzeń](../../parallel/concrt/reference/event-class.md) klasy. Te typy zachowują się wspólne; Harmonogram zadań może alokację zasoby przetwarzania do innego kontekstu, ponieważ pierwsze zadanie czeka na dane. Jeśli to możliwe, należy użyć tych typów synchronizacji, zamiast innych mechanizmów synchronizacji, np. udostępnianych przez interfejs API Windows, które nie działają wspólnie. Aby uzyskać więcej informacji na temat tych typów synchronizacji i przykładowy kod, zobacz [struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md) i [porównywanie struktur danych synchronizacji z interfejsu API Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).

[[Górnej](#top)]

##  <a name="yield"></a> Unikaj długich zadań, które nie dają wyniku

Ponieważ wspólne działa w harmonogramie zadań, nie zapewnia sprawiedliwe spośród zadań. W związku z tym zadanie może uniemożliwić innym zadaniom uruchamiania. Mimo że jest to dopuszczalne w niektórych przypadkach, w innych przypadkach może to spowodować zakleszczenia lub zablokowania.

Poniższy przykład wykonuje więcej niż liczba przydzielonych przetwarzania zasobów. Pierwsze zadanie przekazuje do harmonogramu zadań i w związku z tym drugie zadanie podrzędne uruchamia, dopóki zakończeniu pierwszego zadania.

[!code-cpp[concrt-cooperative-tasks#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_1.cpp)]

Ten przykład generuje następujące wyniki:

1: 250000000 1: 500000000 1: 750000000 1: 1000000000 2: 250000000 2: 500000000 2: 750000000 2: 1000000000

Istnieje kilka sposobów, aby umożliwić współpracę między dwa zadania. Jednym ze sposobów jest od czasu do czasu podania harmonogramu zadań w zadaniu długoterminowych. Poniższy przykład modyfikuje `task` funkcji do wywołania [concurrency::Context::Yield](reference/context-class.md#yield) metody umożliwiające uzyskanie wykonywania do harmonogramu zadań, aby uruchomić inne zadanie.

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

`Context::Yield` Metoda daje tylko inny wątek aktywny w harmonogramie, do której należy dany bieżącego wątku, lekkie zadanie lub inny wątek systemu operacyjnego. Ta metoda nie przekazuje do pracy, które jest zaplanowane do uruchomienia [concurrency::task_group](reference/task-group-class.md) lub [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) obiektu, ale nie została jeszcze uruchomiona.

Istnieją inne sposoby umożliwiające współpracę między długotrwałych zadań. Dużych zadań można podzielić mniejszych podzadania. Można również włączyć nadsubskrypcję podczas długich zadań. Nadsubskrypcja umożliwia utworzenie większej liczby wątków niż liczba dostępnych wątków sprzętu. Nadsubskrypcja jest szczególnie przydatne, gdy długie zadanie zawiera dużej ilości opóźnienia, na przykład odczytywania danych z dysku lub połączenia sieciowego. Aby uzyskać więcej informacji na temat lekkie zadanie i nadsubskrypcji zobacz [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[[Górnej](#top)]

##  <a name="oversubscription"></a> Używanie Nadsubskrypcji operacji przesunięcia, która blokuje lub odznacza duże opóźnienie

Środowisko uruchomieniowe współbieżności zawiera podstawowych synchronizacji, takich jak [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md), umożliwiające zadania wspólne zablokować, a uzyskanie do siebie nawzajem. Gdy jedno zadanie wspólne blokuje lub daje, harmonogram zadań można ponownie przydzielić zasoby przetwarzania kontekst jako pierwsze zadanie czeka na dane.

Istnieją przypadki, w których nie można używać wspólnych mechanizm blokowania, który znajduje się w czasie wykonywania współbieżności. Na przykład zewnętrznej biblioteki, którego używasz może być używany był mechanizm różnych synchronizacji. Innym przykładem jest podczas wykonywania operacji, która może mieć dużej ilości opóźnienia, na przykład, korzystając z interfejsu API Windows `ReadFile` funkcji w celu odczytania danych z połączeniem sieciowym. W takich przypadkach nadsubskrypcji można włączyć inne zadania do uruchamiania, gdy inne zadanie jest w stanie bezczynności. Nadsubskrypcja umożliwia utworzenie większej liczby wątków niż liczba dostępnych wątków sprzętu.

Należy wziąć pod uwagę następującą funkcję `download`, co spowoduje pobranie pliku na podany adres URL. W tym przykładzie użyto [concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe) metodę, aby tymczasowo zwiększyć liczbę aktywnych wątków.

[!code-cpp[concrt-download-oversubscription#4](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_3.cpp)]

Ponieważ `GetHttpFile` funkcja wykonuje operację potencjalnie ukryte, nadsubskrypcji włączyć inne zadania do uruchomienia, ponieważ bieżące zadanie czeka na dane. Aby uzyskać pełną wersję tego przykładu, zobacz [jak: Używanie Nadsubskrypcji do opóźnienia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).

[[Górnej](#top)]

##  <a name="memory"></a> Użyj funkcji zarządzania pamięcią Współbieżną, jeśli jest to możliwe

Funkcje zarządzania pamięcią, użyj [concurrency::Alloc](reference/concurrency-namespace-functions.md#alloc) i [concurrency::Free](reference/concurrency-namespace-functions.md#free), gdy masz szczegółowe zadania, które często przydzielania małych obiektów, które mają relatywnie krótkiego okresu istnienia. Środowisko uruchomieniowe współbieżności przechowuje w oddzielnych pamięci podręcznej dla każdego uruchomionego wątku. `Alloc` i `Free` funkcje alokują i zwalniają pamięć z tych pamięci podręcznych bez użycia blokad lub barier pamięci.

Aby uzyskać więcej informacji o tych funkcje zarządzania pamięcią, zobacz [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Na przykład, który używa tych funkcji, zobacz [jak: Używanie z funkcji Alloc i Free do poprawiania wydajności pamięci](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).

[[Górnej](#top)]

##  <a name="raii"></a> Użyj RAII, aby zarządzać okresem istnienia obiektów współbieżnych

Środowisko uruchomieniowe współbieżności używa obsługi wyjątków, aby zaimplementować funkcje, takie jak anulowania. W związku z tym należy napisać kod, bezpieczne pod względem wyjątków, gdy wywołanie środowiska uruchomieniowego lub wywołania innej biblioteki, która wywołuje w czasie wykonywania.

*Inicjowania jest pozyskiwanie zasobów* wzorca (RAII) jest jednym ze sposobów bezpiecznego zarządzania okresem istnienia obiektów współbieżności w danym zakresie. W obszarze wzór RAII to struktura danych jest przydzielany na stosie. Tej struktury danych inicjuje lub uzyskuje zasobu, gdy jest tworzony i niszczy lub zwalnia tego zasobu, kiedy niszczony jest struktury danych. Wzór RAII gwarantuje, że destruktor jest wywoływany przed zasięgu kończy działanie. Ten wzorzec jest przydatny, gdy funkcja zawiera wiele `return` instrukcji. Ten wzorzec pomaga także napisać kod bezpieczne pod względem wyjątków. Gdy `throw` instrukcja powoduje stosu na odpoczynek, destruktor obiektu RAII jest nazywana; w związku z tym, zasób jest zawsze poprawnie usunięty lub wydania.

Środowisko uruchomieniowe definiuje kilka klas, które na przykład użyć wzór RAII [concurrency::critical_section::scoped_lock](../../parallel/concrt/reference/critical-section-class.md#critical_section__scoped_lock_class) i [concurrency::reader_writer_lock::scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class). Te klasy pomocy są znane jako *zakres blokady*. Te klasy oferują wiele zalet, podczas pracy z [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) lub [concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) obiektów. Konstruktor klasy te uzyskuje dostęp do udostępnionych `critical_section` lub `reader_writer_lock` obiekt; dostęp do wersji destruktora do tego obiektu. Ponieważ blokady o określonym zakresie wydaje dostęp do jego obiektu wzajemne wykluczenie automatycznie, kiedy niszczony jest, możesz nie ręcznie odblokować obiektu źródłowego.

Należy wziąć pod uwagę następujące klasy `account`, który jest definiowany przez zewnętrznej biblioteki i nie może być modyfikowany.

[!code-cpp[concrt-account-transactions#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_4.h)]

Poniższy przykład wykonuje wiele transakcji na `account` obiektu równolegle. W przykładzie użyto `critical_section` obiektu do synchronizowania dostępu do `account` obiektu, ponieważ `account` klasa nie jest bezpieczna pod kątem współbieżności. Używa każdej operacji równoległej `critical_section::scoped_lock` obiekt, aby zagwarantować, że `critical_section` obiektu jest odblokowany, gdy operacja powiedzie się lub kończy się niepowodzeniem. Kiedy saldo konta jest ujemna, `withdraw` operacja zakończy się niepowodzeniem, zostanie zgłoszony wyjątek.

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

Aby uzyskać więcej przykładów, które umożliwiają zarządzanie okresem istnienia obiektów współbieżnych wzór RAII, zobacz [instruktażu: Usuwanie pracy z wątku interfejsu użytkownika](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md), [jak: Korzystanie z klasy kontekstu do wdrażania Kooperatywnego semafora](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md), i [jak: Używanie Nadsubskrypcji do opóźnienia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).

[[Górnej](#top)]

##  <a name="global-scope"></a> Nie twórz obiektów współbieżności w zakresie globalnym

Podczas tworzenia obiektów współbieżności w zakresie globalnym może spowodować problemy, takie jak zakleszczenia lub pamięci naruszenia zasad dostępu w aplikacji.

Na przykład podczas tworzenia obiektu środowisko uruchomieniowe współbieżności środowiska wykonawczego tworzy domyślnego harmonogramu dla Ciebie, jeśli nie została jeszcze utworzona. Obiekt środowiska uruchomieniowego, który jest tworzony podczas tworzenia obiektów globalnych odpowiednio spowoduje, że środowisko uruchomieniowe do utworzenia tego domyślnego harmonogramu. Jednak ten proces trwa blokady wewnętrznych, które mogą zakłócać inicjowania inne obiekty, które obsługują infrastrukturę współbieżność środowiska wykonawczego. Ta blokada wewnętrznego, mogą być wymagane przez inny obiekt infrastruktury, która nie została jeszcze zainicjowana i dlatego może spowodować zakleszczenia występuje w aplikacji.

W poniższym przykładzie pokazano tworzenie globalnych [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) obiektu. Ten wzorzec dotyczy nie tylko `Scheduler` klasy, ale wszystkie inne typy, które są dostarczane przez środowisko uruchomieniowe współbieżności. Zaleca się, że nie podlegają tego wzorca, ponieważ może to spowodować nieoczekiwane zachowanie w aplikacji.

[!code-cpp[concrt-global-scheduler#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_6.cpp)]

Przykłady prawidłowy sposób do utworzenia `Scheduler` obiekty, zobacz [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[[Górnej](#top)]

##  <a name="shared-data"></a> Nie używaj obiektów współbieżności w segmentach współdzielonych danych

Środowisko uruchomieniowe współbieżności nie obsługuje obiektów współbieżności w sekcji danych udostępnionych, na przykład sekcji danych, który jest tworzony przez [data_seg](../../preprocessor/data-seg.md) `#pragma` dyrektywy. Obiekt współbieżności, który jest współużytkowany przez granice procesu umieścić środowiska uruchomieniowego w niespójny lub ma nieprawidłowy stan.

[[Górnej](#top)]

## <a name="see-also"></a>Zobacz także

[Środowisko uruchomieniowe współbieżności — najlepsze praktyki](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Task Scheduler](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Porównywanie struktur danych synchronizacji z Windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
[Instrukcje: używanie z funkcji Alloc i Free do poprawiania wydajności pamięci](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)<br/>
[Instrukcje: używanie nadsubskrypcji do przesuwania opóźnienia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)<br/>
[Instrukcje: korzystanie z klasy kontekstu do wdrażania a kooperatywnego semafora](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[Przewodnik: usuwanie pracy z wątku interfejs użytkownika](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)<br/>
[Biblioteka wzorów równoległych — najlepsze praktyki](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[Biblioteka agentów asynchronicznych — najlepsze praktyki](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)
