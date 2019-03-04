---
title: Współbieżność środowiska wykonawczego
ms.date: 07/20/2018
helpviewer_keywords:
- Concurrency Runtime, getting started
- ConcRT (see Concurrency Runtime)
- Concurrency Runtime
ms.assetid: 874bc58f-8dce-483e-a3a1-4dcc9e52ed2c
ms.openlocfilehash: 245984d9702c997f16601bf5e2a9bd049ae5fed9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258336"
---
# <a name="concurrency-runtime"></a>Współbieżność środowiska wykonawczego

Współbieżność środowiska wykonawczego języka C++ pomaga zapisu niezawodnych, skalowalnych i szybko reagujących aplikacji równoległych. Tak, aby nie trzeba zarządzać szczegóły infrastruktury, that are related to współbieżności, podnosi poziom abstrakcji. Można również użyć do określenia planowania zasad, które spełniają jakości wymagań usługi aplikacji. Dzięki tym zasobom, które ułatwią rozpoczęcie pracy w środowisku uruchomieniowym współbieżności.

Aby uzyskać dokumentację referencyjną, zobacz [odwołania](../../parallel/concrt/reference/reference-concurrency-runtime.md).

> [!TIP]
>  Środowisko uruchomieniowe współbieżności silnie zależy od funkcji C ++ 11 i przyjmuje więcej współczesny styl C++. Aby dowiedzieć się więcej, przeczytaj [powitalnej zwrotnie do C++](../../cpp/welcome-back-to-cpp-modern-cpp.md).

## <a name="choosing-concurrency-runtime-features"></a>Wybieranie funkcji współbieżnych środowiska wykonawczego

|||
|-|-|
|[Omówienie](../../parallel/concrt/overview-of-the-concurrency-runtime.md)|Uczy się, dlaczego współbieżność środowiska wykonawczego jest ważna, a w tym artykule opisano najważniejsze funkcje.|
|[Porównywanie z innymi modelami współbieżności](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|Przedstawia porównanie środowiska uruchomieniowego współbieżności z innymi modelami współbieżności, takie jak Windows wątek puli i OpenMP, dzięki czemu możesz skorzystać z modelu współbieżności, która najlepiej pasuje do wymagań aplikacji.|
|[Migrowanie z OpenMP do środowiska uruchomieniowego współbieżności](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)|Porównuje OpenMP do współbieżności środowiska wykonawczego i zawiera przykłady dotyczące migracji istniejącego kodu OpenMP do współbieżności środowiska wykonawczego.|
|[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Poznasz PPL, która zapewnia pętle równoległe, zadania i kontenerów równoległych.|
|[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)|Przedstawiono sposób używania agentów asynchronicznych i komunikatów przekazywania można łatwo umieścić przepływu danych i przetwarzanie potokowe zadania w swoich aplikacjach.|
|[Task Scheduler](../../parallel/concrt/task-scheduler-concurrency-runtime.md)|Poznasz harmonogramu zadań, która umożliwia dostrojenie wydajności aplikacji klasycznych, która używa środowiska uruchomieniowego współbieżności.|

## <a name="task-parallelism-in-the-ppl"></a>Proste zadania w PPL

|||
|-|-|
|[Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br /><br /> [Instrukcje: używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br /><br /> [Instrukcje: wykonywanie operacji równoległych za pomocą elementu Parallel.Invoke](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)<br /><br /> [Instrukcje: tworzenie zadania kończonego po opóźnieniu](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|W tym artykule opisano zadania i grupy zadań, które mogą ułatwić pisania kodu asynchronicznego i rozkładać równoległą pracę na mniejsze części.|
|[Przewodnik: wdrażanie przyszłych operacji](../../parallel/concrt/walkthrough-implementing-futures.md)|Pokazuje, jak połączyć czymś więcej funkcji środowiska uruchomieniowego współbieżności.|
|[Przewodnik: usuwanie pracy z wątku interfejs użytkownika](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)|Pokazuje, jak przenieść pracę wykonywaną przez wątek interfejsu użytkownika w aplikacji MFC do wątku roboczego.|
|[Biblioteka wzorów równoległych — najlepsze praktyki](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Środowisko uruchomieniowe współbieżności — najlepsze praktyki ogólne](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Zawiera wskazówki i najlepsze rozwiązania dotyczące pracy z PPL.|

## <a name="data-parallelism-in-the-ppl"></a>Równoległość danych w PPL

|||
|-|-|
|[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br /><br /> [Instrukcje: pisanie pętli parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)<br /><br /> [Instrukcje: pisanie pętli parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)<br /><br /> [Instrukcje: równoległe wykonywanie operacji mapowania i zmniejszania](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|W tym artykule opisano `parallel_for`, `parallel_for_each`, `parallel_invoke`, a inne algorytmy równoległe. Użyj zgodnych algorytmów równoległych rozwiązać *danych równoległych* problemy z działaniem zbiory danych.|
|[Równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md)<br /><br /> [Instrukcje: korzystanie z kontenerów równoległych do zwiększania wydajności](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br /><br /> [Instrukcje: korzystanie z wyników połączonych do poprawiania wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br /><br /> [Instrukcje: korzystanie z wyników połączonych w celu łączenia zestawów](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)|W tym artykule opisano `combinable` klasy, a także `concurrent_vector`, `concurrent_queue`, `concurrent_unordered_map`i innych kontenerów równoległych. Użyj równoległe kontenery oraz obiekty, gdy potrzebujesz kontenerów, które można podać metodą o bezpiecznych wątkach dostęp do swoich elementów.|
|[Biblioteka wzorów równoległych — najlepsze praktyki](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Środowisko uruchomieniowe współbieżności — najlepsze praktyki ogólne](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Zawiera wskazówki i najlepsze rozwiązania dotyczące pracy z PPL.|

## <a name="canceling-tasks-and-parallel-algorithms"></a>Anulowanie zadań i algorytmów równoległych

|||
|-|-|
|[Anulowanie w PPL](cancellation-in-the-ppl.md)|W tym artykule opisano rolę anulowanie w PPL, w tym sposobu inicjowania i odpowiadać na żądania anulowania.|
|[Instrukcje: używanie anulowania, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br /><br /> [Instrukcje: używanie obsługi wyjątków, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Przedstawia dwa sposoby na anulowanie pracy danych równoległych.|

## <a name="universal-windows-platform-apps"></a>Windows Universal apps platformy

|||
|-|-|
|[Tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy uniwersalnej systemu Windows](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)|Opisano niektóre kluczowe punkty, których należy pamiętać, korzystając ze współbieżności środowiska wykonawczego do wygenerowania operacji asynchronicznych w aplikacji platformy uniwersalnej systemu Windows.|
|[Przewodnik: łączenie za pomocą zadań i żądań XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)|Pokazuje, jak łączyć zadania PPL z `IXMLHTTPRequest2` i `IXMLHTTPRequest2Callback` interfejsy do wysyłania żądań HTTP GET i POST do usługi sieci web w aplikacji platformy uniwersalnej systemu Windows.|
|[Przykłady aplikacji Windows Runtime](http://code.msdn.microsoft.com/windowsapps)|Zawiera przykłady kodu do pobrania i wersji demonstracyjnej aplikacji dla Windows 8.x. Przykłady języka C++ Użyj funkcji środowiska uruchomieniowego współbieżności, takich jak zadania PPL do przetwarzania danych w tle, aby zachować środowiska użytkownika dynamiczne.|

## <a name="dataflow-programming-in-the-asynchronous-agents-library"></a>Programowanie przepływu danych w bibliotece agentów asynchronicznych

|||
|-|-|
|[Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)<br /><br /> [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br /><br /> [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)<br /><br /> [Instrukcje: implementowanie różnych wzorców producent — konsument](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)<br /><br /> [Instrukcje: zapewnianie funkcji pracy dla wywoływania oraz klasy transformatora](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)<br /><br /> [Instrukcje: używanie transformatora w potoku danych](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br /><br /> [Instrukcje: wybieranie spośród zadań wykonanych](../../parallel/concrt/how-to-select-among-completed-tasks.md)<br /><br /> [Instrukcje: wysyłanie komunikatu w regularnych odstępach czasu](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)<br /><br /> [Instrukcje: korzystanie z filtra bloku komunikatów](../../parallel/concrt/how-to-use-a-message-block-filter.md)|W tym artykule opisano agentów asynchronicznych, bloki komunikatów i funkcje przekazywania komunikatów, które są blokami konstrukcyjnymi do wykonywania operacji przepływu danych w środowisku uruchomieniowym współbieżności.|
|[Przewodnik: tworzenie aplikacji opartej o agentów](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br /><br /> [Przewodnik: tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)|Pokazuje, jak tworzyć podstawowe aplikacje oparte na agentach.|
|[Przewodnik: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)|Pokazuje, jak utworzyć sieć bloki komunikatów asynchronicznych, wykonujących przetwarzanie obrazu.|
|[Przewodnik: korzystanie ze złączy w celu zapobiegania zakleszczeniom](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)|Używa problem ucztujących filozofów w celu zilustrowania sposobu korzystania ze współbieżności środowiska wykonawczego w celu uniknięcia zakleszczenia w aplikacji.|
|[Przewodnik: tworzenie niestandardowego bloku komunikatów](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)|Przedstawia sposób tworzenia komunikatów niestandardowy typ bloku, które porządkuje przychodzące wiadomości według priorytetu.|
|[Biblioteka agentów asynchronicznych — najlepsze praktyki](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br /><br /> [Środowisko uruchomieniowe współbieżności — najlepsze praktyki ogólne](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Zawiera wskazówki i najlepsze rozwiązania dotyczące pracy z agentami.|

## <a name="exception-handling-and-debugging"></a>Obsługa wyjątków i debugowania

|||
|-|-|
|[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|W tym artykule opisano sposób pracy z wyjątków w środowisku uruchomieniowym współbieżności.|
|[Równoległe narzędzia diagnostyczne](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Dowiesz się, jak dostosowywać aplikacje i najbardziej efektywnie wykorzystać w czasie wykonywania współbieżności.|

## <a name="tuning-performance"></a>Dostrajanie wydajności

|||
|-|-|
|[Równoległe narzędzia diagnostyczne](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Dowiesz się, jak dostosowywać aplikacje i najbardziej efektywnie wykorzystać w czasie wykonywania współbieżności.|
|[Wystąpienia harmonogramu](../../parallel/concrt/scheduler-instances.md)<br /><br /> [Instrukcje: zarządzanie wystąpieniem harmonogramu](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br /><br /> [Zasady harmonogramu](../../parallel/concrt/scheduler-policies.md)<br /><br /> [Instrukcje: określanie specjalnych zasad harmonogramu](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br /><br /> [Instrukcje: tworzenie agentów korzystających ze specjalnych zasad harmonogramu](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)|Pokazuje, jak działa Zarządzanie wystąpienia harmonogramu i zasad harmonogramu. Zasady harmonogramu dla aplikacji klasycznych umożliwiają skojarzenie określone zasady za pomocą określonych rodzajów obciążeń. Na przykład można utworzyć jedno wystąpienie usługi scheduler do uruchamiania niektórych zadań priorytetem wątku z podwyższonym poziomem uprawnień i używają domyślnego harmonogramu uruchomienie innych zadań priorytetem normalne wątku.|
|[Grupy harmonogramu](../../parallel/concrt/schedule-groups.md)<br /><br /> [Instrukcje: używanie grup harmonogramu do wywierania wpływu na kolejność wykonywania](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)|Pokazuje, jak używanie grup harmonogramu do affinitize lub pogrupować, informacje o zadaniach pokrewnych. Na przykład wymagają wysokiego stopnia miejscowość między informacje o zadaniach pokrewnych, gdy te zadania korzystają z wykonywane w tym samym węźle procesora.|
|[Zadania lekkie](../../parallel/concrt/lightweight-tasks.md)|Wyjaśnia, jak lekkie zadanie są przydatne do tworzenia zadania, które nie wymagają równoważenia obciążenia lub anulowania i jak są one również przydatne w przypadku dostosowania istniejący kod do użycia w środowisku uruchomieniowym współbieżności.|
|[Konteksty](../../parallel/concrt/contexts.md)<br /><br /> [Instrukcje: korzystanie z klasy kontekstu do wdrażania a kooperatywnego semafora](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br /><br /> [Instrukcje: używanie nadsubskrypcji do przesuwania opóźnienia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)|Zawiera opis sposobu kontrolowania zachowania wątków, które są zarządzane przez środowisko uruchomieniowe współbieżności.|
|[Funkcje zarządzania pamięcią](../../parallel/concrt/memory-management-functions.md)<br /><br /> [Instrukcje: używanie z funkcji Alloc i Free do poprawiania wydajności pamięci](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)|W tym artykule opisano funkcje zarządzania pamięcią, udostępnianych przez środowisko uruchomieniowe współbieżności ułatwiające przydzielają i zwalniają pamięć w sposób współbieżnych.|

## <a name="additional-resources"></a>Dodatkowe zasoby

|||
|-|-|
|[Programowanie asynchroniczne wzorców i porady w Hilo (aplikacje Windows Store przy użyciu języków C++ i XAML)](https://msdn.microsoft.com/library/windows/apps/jj160321.aspx)|Dowiedz się, jak firma Microsoft umożliwia środowisku uruchomieniowym współbieżności: implementowania asynchronicznych operacji w Hilo, aplikacji środowiska wykonawczego Windows, korzystając z C++ i XAML.|
|[Przykłady kodu dla środowiska uruchomieniowego współbieżności i Biblioteka równoległych wzorcem w Visual Studio 2010](http://go.microsoft.com/fwlink/p/?linkid=183875)|Zawiera przykładowe aplikacje i narzędzia, które pokazują, w czasie wykonywania współbieżności.|
|[Programowanie równoległe w kodzie macierzystym bloga](http://go.microsoft.com/fwlink/p/?linkid=183873)|Udostępnia dodatkowe szczegółowy blog artykuły dotyczące programowania równoległego w środowisku uruchomieniowym współbieżności.|
|[Przetwarzania równoległego na forum C++ i kodu natywnego](http://go.microsoft.com/fwlink/p/?linkid=183874)|Można uczestniczyć w dyskusjach społeczności o środowisku uruchomieniowym współbieżności.|
|[Programowanie równoległe](/dotnet/standard/parallel-programming/index)|Zawiera informacje na temat równoległych model programowania, który jest dostępny w programie .NET Framework.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja](../../parallel/concrt/reference/reference-concurrency-runtime.md)
