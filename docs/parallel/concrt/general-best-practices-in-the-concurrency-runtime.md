---
title: "Najlepsze praktyki ogólne współbieżności środowiska wykonawczego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Concurrency Runtime, general best practices
ms.assetid: ce5c784c-051e-44a6-be84-8b3e1139c18b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d5c2c626ceb0243e91e56d70f0d8ae71208b157f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="general-best-practices-in-the-concurrency-runtime"></a>Współbieżność środowiska wykonawczego — Najlepsze praktyki ogólne
Ten dokument zawiera wskazówki, które są stosowane do wielu obszarów współbieżności środowiska wykonawczego.  
  
##  <a name="top"></a>Sekcje  
 Ten dokument zawiera następujące sekcje:  
  
- [Użyj konstrukcji współpracy synchronizacji, gdy jest to możliwe](#synchronization)  
  
- [Uniknąć długich zadań, które nie zwracają](#yield)  
  
- [Używanie Nadsubskrypcji do blokowania lub ma duże opóźnienie operacji przesunięcia](#oversubscription)  
  
- [Użyj funkcje zarządzania pamięcią jednoczesnych, jeśli to możliwe](#memory)  
  
- [Umożliwia zarządzanie okresem istnienia obiektów współbieżności RAII](#raii)  
  
- [Nie należy tworzyć obiektów współbieżność w zakresie globalnym](#global-scope)  
  
- [Nie używaj obiektów współbieżność w segmentach udostępnionych danych](#shared-data)  
  
##  <a name="synchronization"></a>Użyj konstrukcji współpracy synchronizacji, gdy jest to możliwe  
 Współbieżność środowiska wykonawczego zawiera wiele konstrukcji bezpieczne współbieżności niewymagających obiektu zewnętrznego synchronizacji. Na przykład [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) klasa udostępnia bezpieczny współbieżności dołączania i elementu dostęp. W przypadkach, gdy wymaga wyłącznego dostępu do zasobu, środowisko uruchomieniowe zapewnia jednak [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md), [concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md), i [współbieżności :: zdarzeń](../../parallel/concrt/reference/event-class.md) klasy. Te typy zachowują się wspólnie; Harmonogram zadań można ponownie zasoby przetwarzania kontekst, jak pierwszy zadanie czeka na danych. Jeśli to możliwe, należy używać tych typów synchronizacji zamiast innych mechanizmów synchronizacji, np. udostępnianych przez interfejs API systemu Windows, które nie zachowują się wspólnie. Aby uzyskać więcej informacji o tych typów synchronizacji i przykładowego kodu, zobacz [struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md) i [porównywanie struktur danych synchronizacji interfejsu API systemu Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).  
  
 [[Górnej](#top)]  
  
##  <a name="yield"></a>Uniknąć długich zadań, które nie zwracają  
 Ponieważ Harmonogram zadań zachowuje wspólne, nie zapewnia sprawiedliwe przydzielanie zasobów spośród zadań. W związku z tym zadania może uniemożliwić innych zadań uruchomienie. Chociaż jest to dopuszczalne tylko w niektórych przypadkach, w innych przypadkach może to spowodować zakleszczenie lub zablokowania.  
  
 Poniższy przykład wykonuje zadania więcej niż liczba przetwarzania przydzielone zasoby. Pierwszym zadaniem nie przekazuje do harmonogramu zadań, a w związku z tym drugie zadanie nie uruchamia przed zakończeniem pierwszego zadania.  
  
 [!code-cpp[concrt-cooperative-tasks#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_1.cpp)]  
  
 Ten przykład generuje następujące wyniki:  
  
 1: 250000000 1: 500000000 1: 750000000 1: 1000000000 2: 250000000 2: 500000000 2: 750000000 2: 1000000000  
  

 Istnieje kilka sposobów, aby umożliwić współpracę między dwa zadania. Jednym ze sposobów jest uzyskanie czasami z harmonogramem zadań w długotrwałe zadanie. Poniższy przykład modyfikuje `task` funkcji do wywołania [concurrency::Context::Yield](reference/context-class.md#yield) metody umożliwiające uzyskanie wykonywania harmonogram zadań, dzięki czemu można uruchamiać inne zadanie.  

  
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
  
 `Context::Yield` Metoda daje tylko inny wątek active w harmonogramie, do której należy dany bieżący wątek, lekkie zadań lub inny wątek systemu operacyjnego. Ta metoda nie przekazuje do pracy, który jest zaplanowane do uruchomienia w [concurrency::task_group](reference/task-group-class.md) lub [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) obiekt, ale nie została jeszcze uruchomiona.  
  
 Istnieją inne sposoby umożliwiające współpracę między długotrwałych zadań. Dużych zadań mogą być dzielone na mniejsze podzadania. Można również włączyć nadsubskrypcji podczas długie zadanie. Nadsubskrypcji umożliwia utworzenie większej liczby wątków niż liczba dostępnych wątków sprzętu. Nadsubskrypcji jest szczególnie przydatne, gdy długie zadanie zawiera dużej ilości opóźnienia, na przykład Odczyt danych z dysku lub z połączeniem sieciowym. Aby uzyskać więcej informacji na temat zadań lekkich i nadsubskrypcji, zobacz [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
 [[Górnej](#top)]  
  
##  <a name="oversubscription"></a>Używanie Nadsubskrypcji do blokowania lub ma duże opóźnienie operacji przesunięcia  
 Współbieżność środowiska wykonawczego zawiera elementy podstawowe synchronizacji, takie jak [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md), które umożliwiają zadań w celu blokowania wspólnie i uzyskanie ze sobą. Jedno zadanie wspólnie blokuje lub daje, harmonogram zadań można ponownie przydzielić zasoby przetwarzania kontekst jako pierwsze zadanie oczekuje na dane.  
  
 Istnieją przypadki, w których nie można używać mechanizmu blokowania współpracy są dostarczane przez współbieżności środowiska wykonawczego. Na przykład zewnętrznej biblioteki, którego używasz, może korzysta z mechanizmu różnych synchronizacji. Innym przykładem jest podczas wykonywania operacji, która może mieć dużej ilości opóźnienia, na przykład, korzystając z interfejsu API systemu Windows `ReadFile` funkcji można odczytać danych z połączeniem sieciowym. W takich przypadkach nadsubskrypcji można włączyć innych zadań do uruchomienia, gdy inne zadanie jest w stanie bezczynności. Nadsubskrypcji umożliwia utworzenie większej liczby wątków niż liczba dostępnych wątków sprzętu.  
  
 Należy wziąć pod uwagę następujące funkcji `download`, co spowoduje pobranie plików pod danym adresem URL. W tym przykładzie użyto [concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe) metodę tymczasowo zwiększania liczba aktywnych wątków.  

 [!code-cpp[concrt-download-oversubscription#4](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_3.cpp)]  
  
 Ponieważ `GetHttpFile` funkcja wykonuje operację potencjalnie ukryty, nadsubskrypcji można włączyć innych zadań do wykonania jako bieżące zadanie czeka na danych. Aby uzyskać pełną wersję tego przykładu, zobacz [jak: Użyj Nadsubskrypcji do przesunięcia opóźnienia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).  
  
 [[Górnej](#top)]  
  
##  <a name="memory"></a>Użyj funkcje zarządzania pamięcią jednoczesnych, jeśli to możliwe  

 Funkcje zarządzania pamięcią, użyj [concurrency::Alloc](reference/concurrency-namespace-functions.md#alloc) i [concurrency::Free](reference/concurrency-namespace-functions.md#free), jeśli masz szczegółowych zadań, które często przydzielić małych obiektów, które mają względnie krótkim okresie istnienia. Współbieżność środowiska wykonawczego zawiera osobne pamięci podręcznej dla każdego uruchomionego wątku. `Alloc` i `Free` funkcji alokacji i zwolnić pamięć z tych pamięci podręcznych bez użycia blokady lub bariery pamięci.  
  
 Aby uzyskać więcej informacji o tych funkcje zarządzania pamięcią, zobacz [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Na przykład, który używa tych funkcji, zobacz [porady: użycie alokacji i wolne do poprawiania wydajności pamięci](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).  
  
 [[Górnej](#top)]  
  
##  <a name="raii"></a>Umożliwia zarządzanie okresem istnienia obiektów współbieżności RAII  
 Współbieżność środowiska wykonawczego używa obsługi wyjątków do implementowania funkcji, takich jak anulowania. W związku z tym zapisu wyjątek bezpieczny kod, gdy wywołanie w czasie wykonywania, lub zadzwoń innej biblioteki, który wywołuje w czasie wykonywania.  
  
 *Inicjowania jest nabywania zasobów* wzorca (RAII) jest jednym ze sposobów bezpiecznego zarządzania istnienia obiektu współbieżność w danym zakresie. W obszarze wzorzec RAII to struktura danych został przydzielony na stosie. Tej struktury danych inicjuje lub uzyskuje zasobu, gdy jest tworzony i niszczy lub zwalnia tego zasobu, gdy zostanie zniszczony struktury danych. Wzorzec RAII gwarantuje, że destruktor jest wywoływana przed opuszcza otaczającego zakresu. Ten wzorzec jest przydatne, gdy funkcja zawiera wiele `return` instrukcje. Ten wzorzec pomaga również napisać kod wyjątku palety. Gdy `throw` instrukcja powoduje stosu cofnąć destruktor dla obiekt RAII jest nazywany; w związku z tym zasobu jest zawsze poprawnie usunięty lub zwolnione.  
  
 Środowisko uruchomieniowe definiuje kilka klas korzystających ze wzorca RAII, na przykład [concurrency::critical_section::scoped_lock](../../parallel/concrt/reference/critical-section-class.md#critical_section__scoped_lock_class) i [concurrency::reader_writer_lock::scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class). Te klasy pomocy są określane jako *zakres blokady*. Te klasy zapewnia kilka korzyści, podczas pracy z [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) lub [concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) obiektów. Konstruktor tych klas uzyskuje dostęp do udostępnionych `critical_section` lub `reader_writer_lock` obiekt; destruktora wersjach dostęp do tego obiektu. Ponieważ zakresami blokady zwalnia dostęp do jego obiektu wzajemne wykluczenie automatycznie, gdy został zniszczony, możesz nie ręcznie odblokowane obiektu źródłowego.  
  
 Należy wziąć pod uwagę następujące klasy `account`, która jest definiowana za pomocą zewnętrznej biblioteki i nie może być modyfikowany.  
  
 [!code-cpp[concrt-account-transactions#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_4.h)]  
  
 Poniższy przykład wykonuje wiele transakcji na `account` obiektu równolegle. W przykładzie użyto `critical_section` obiektu synchronizujący dostęp do `account` obiektu, ponieważ `account` klasa nie jest bezpieczne współbieżności. Używa każdej operacji równoległych `critical_section::scoped_lock` obiekt, aby zagwarantować, że `critical_section` obiektu jest odblokowany, gdy operacja zakończy się powodzeniem lub nie powiedzie się. Gdy stan konta jest ujemna, `withdraw` operacja zakończy się niepowodzeniem przez Zgłaszanie wyjątku.  
  
 [!code-cpp[concrt-account-transactions#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_5.cpp)]  
  
 W tym przykładzie tworzy następujące przykładowe dane wyjściowe:  
  
```Output  
Balance before deposit: 1924  
Balance after deposit: 2924  
Balance before withdrawal: 2924  
Balance after withdrawal: -76  
Balance before withdrawal: -76  
Error details:  
    negative balance: -76  
```  
  
 Dodatkowe przykłady korzystających ze wzorca RAII Zarządzanie okresem istnienia obiektów współbieżności, zobacz [wskazówki: usuwanie pracy z wątku interfejsu użytkownika](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md), [porady: Korzystanie z klasy kontekstu do zaimplementowania wspólnego Semafor](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md), i [porady: używanie Nadsubskrypcji do przesuwania opóźnienia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).  
  
 [[Górnej](#top)]  
  
##  <a name="global-scope"></a>Nie należy tworzyć obiektów współbieżność w zakresie globalnym  
 Podczas tworzenia obiektu współbieżność w zakresie globalnym może spowodować problemy, takie jak zakleszczenia lub pamięci naruszenia zasad dostępu w aplikacji.  
  
 Na przykład podczas tworzenia obiektu współbieżność środowiska wykonawczego środowiska uruchomieniowego tworzy domyślnego harmonogramu dla Ciebie, jeśli nie została jeszcze utworzona. Obiektu środowiska wykonawczego, który jest tworzony podczas konstruowania obiektu globalnego odpowiednio spowoduje środowiska uruchomieniowego utworzyć ten harmonogram domyślny. Jednak ten proces trwa blokadę wewnętrzny może zakłócać proces inicjowania inne obiekty, które obsługują infrastrukturę współbieżność środowiska wykonawczego. Ta blokada wewnętrzny może być wymagany przez inny obiekt infrastruktury, która nie została jeszcze zainicjowana, a w związku z tym mogą powodować zakleszczenie występuje w aplikacji.  
  
 W poniższym przykładzie pokazano utworzenia globalną [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) obiektu. Ten wzorzec dotyczą nie tylko `Scheduler` klasy, ale wszystkie inne typy, które są udostępniane przez współbieżności środowiska wykonawczego. Zaleca się, że nie wykonuj tego wzorca ponieważ może spowodować nieoczekiwane zachowanie aplikacji.  
  
 [!code-cpp[concrt-global-scheduler#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_6.cpp)]  
  
 Przykłady w prawidłowy sposób, aby utworzyć `Scheduler` obiekty, zobacz [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
 [[Górnej](#top)]  
  
##  <a name="shared-data"></a>Nie używaj obiektów współbieżność w segmentach udostępnionych danych  
 Współbieżność środowiska wykonawczego nie obsługuje obiektów współbieżność w sekcji udostępnionych danych, na przykład sekcji danych, która jest tworzona przez [data_seg](../../preprocessor/data-seg.md) `#pragma` dyrektywy. Obiekt współbieżności, który jest współużytkowany przez granice procesu można umieścić środowiska uruchomieniowego w niezgodne lub ma nieprawidłowy stan.  
  
 [[Górnej](#top)]  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność środowiska wykonawczego — najlepsze praktyki](../../parallel/concrt/concurrency-runtime-best-practices.md)   
 [Biblioteka równoległych wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)   
 [Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)   
 [Porównywanie struktur danych synchronizacji z Windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)   
 [Porady: używanie z funkcji Alloc i Free do poprawiania wydajności pamięci](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)   
 [Porady: używanie Nadsubskrypcji do przesuwania opóźnienia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)   
 [Porady: Korzystanie z klasy kontekstu do wdrażania Kooperatywnego semafora](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)   
 [Wskazówki: Usuwanie pracy z wątku interfejsu użytkownika](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)   
 [Biblioteka wzorów równoległych — najlepsze praktyki](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)   
 [Biblioteka agentów asynchronicznych — najlepsze praktyki](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)
