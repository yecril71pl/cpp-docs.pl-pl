---
title: Współbieżność środowiska wykonawczego
ms.date: 07/20/2018
helpviewer_keywords:
- Concurrency Runtime, getting started
- ConcRT (see Concurrency Runtime)
- Concurrency Runtime
ms.assetid: 874bc58f-8dce-483e-a3a1-4dcc9e52ed2c
ms.openlocfilehash: ce75d7a78fec69922c08479f6c130c6b6ccec566
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845513"
---
# <a name="concurrency-runtime"></a>Współbieżność środowiska wykonawczego

Środowisko uruchomieniowe współbieżności dla języka C++ ułatwia pisanie niezawodnych, skalowalnych i wydajnych aplikacji równoległych. Podnosi poziom abstrakcji, aby nie trzeba było zarządzać szczegółami infrastruktury związanymi z współbieżnością. Można go również użyć do określenia zasad planowania, które spełniają wymagania dotyczące jakości usług aplikacji. Użyj tych zasobów, aby pomóc Ci rozpocząć pracę z środowisko uruchomieniowe współbieżności.

Dokumentacja referencyjna znajduje się w temacie [Reference](../../parallel/concrt/reference/reference-concurrency-runtime.md).

> [!TIP]
> Środowisko uruchomieniowe współbieżności opiera się na funkcjach języka C++ 11 i przyjmuje bardziej nowoczesny styl języka C++. Aby dowiedzieć się więcej, przeczytaj artykuł  [Witamy ponownie w języku C++](../../cpp/welcome-back-to-cpp-modern-cpp.md).

## <a name="choosing-concurrency-runtime-features"></a>Wybieranie funkcji współbieżnych środowiska wykonawczego

|Artykuł|Opis|
|-|-|
|[Omówienie](../../parallel/concrt/overview-of-the-concurrency-runtime.md)|Uczy, dlaczego środowisko uruchomieniowe współbieżności jest ważna i opisuje jej najważniejsze funkcje.|
|[Porównywanie z innymi modelami współbieżności](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|Pokazuje, w jaki sposób środowisko uruchomieniowe współbieżności porównuje się z innymi modelami współbieżności, takimi jak Pula wątków systemu Windows i OpenMP, aby można było użyć modelu współbieżności, który najlepiej spełnia wymagania aplikacji.|
|[Migrowanie z OpenMP do współbieżności środowiska wykonawczego](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)|Porównuje wartość OpenMP z środowisko uruchomieniowe współbieżności i zawiera przykłady dotyczące sposobu migrowania istniejącego kodu OpenMP w celu użycia środowisko uruchomieniowe współbieżności.|
|[Biblioteka równoległych wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Wprowadza do PPL, który zapewnia pętle równoległe, zadania i kontenery równoległe.|
|[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)|W tym temacie przedstawiono sposób używania asynchronicznych agentów i komunikatów, które umożliwiają łatwe dołączanie zadań przepływu danych i potokowych w aplikacjach.|
|[Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)|Wprowadza do Harmonogram zadań, co umożliwia precyzyjne dostosowanie wydajności aplikacji klasycznych, które korzystają z środowisko uruchomieniowe współbieżności.|

## <a name="task-parallelism-in-the-ppl"></a>Proste zadania w PPL

|Artykuł|Opis|
|-|-|
|[Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br /><br /> [Instrukcje: używanie parallel_invoke do pisania równoległej procedury sortowania](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br /><br /> [Instrukcje: używanie parallel_invoke do wykonywania operacji równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)<br /><br /> [Instrukcje: Tworzenie zadania, które kończy się po opóźnieniu](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Opisuje zadania i grupy zadań, które mogą ułatwić pisanie kodu asynchronicznego i rozkładanie pracy równoległej na mniejsze części.|
|[Przewodnik: wdrażanie przyszłych](../../parallel/concrt/walkthrough-implementing-futures.md)|Pokazuje, jak połączyć funkcje środowisko uruchomieniowe współbieżności, aby zrobić coś więcej.|
|[Przewodnik: usuwanie pracy z wątku interfejsu użytkownika](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)|Pokazuje, w jaki sposób przenieść zadania wykonywane przez wątek interfejsu użytkownika w aplikacji MFC do wątku roboczego.|
|[Najlepsze rozwiązania w bibliotece równoległych wzorców](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Ogólne najlepsze rozwiązania w środowisko uruchomieniowe współbieżności](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Zawiera wskazówki i najlepsze rozwiązania dotyczące pracy z PPL.|

## <a name="data-parallelism-in-the-ppl"></a>Równoległość danych w PPL

|Artykuł|Opis|
|-|-|
|[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br /><br /> [Instrukcje: pisanie pętli parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)<br /><br /> [Instrukcje: pisanie pętli parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)<br /><br /> [Instrukcje: wykonywanie map i zmniejszanie operacji równolegle](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Opisuje `parallel_for` , `parallel_for_each` , `parallel_invoke` i inne algorytmy równoległe. Algorytmy równoległe służą do rozwiązywania problemów *równoległych dotyczących danych* , które obejmują kolekcje danych.|
|[Równoległe kontenery i obiekty](../../parallel/concrt/parallel-containers-and-objects.md)<br /><br /> [Instrukcje: korzystanie z kontenerów równoległych w celu zwiększenia wydajności](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br /><br /> [Instrukcje: używanie kombinacji w celu poprawy wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br /><br /> [Instrukcje: używanie kombinacji do łączenia zestawów](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)|Zawiera opis `combinable` klasy,, `concurrent_vector` `concurrent_queue` `concurrent_unordered_map` i innych kontenerów równoległych. Używaj kontenerów równoległych i obiektów, gdy wymagane są kontenery zapewniające bezpieczny wątkowy dostęp do ich elementów.|
|[Najlepsze rozwiązania w bibliotece równoległych wzorców](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Ogólne najlepsze rozwiązania w środowisko uruchomieniowe współbieżności](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Zawiera wskazówki i najlepsze rozwiązania dotyczące pracy z PPL.|

## <a name="canceling-tasks-and-parallel-algorithms"></a>Anulowanie zadań i algorytmów równoległych

|Artykuł|Opis|
|-|-|
|[Anulowanie w PPL](cancellation-in-the-ppl.md)|Opisuje rolę anulowania w PPL, w tym sposób inicjowania i reagowania na żądania anulowania.|
|[Jak użyć anulowania, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br /><br /> [Instrukcje: korzystanie z obsługi wyjątków, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Ilustruje dwa sposoby anulowania pracy równoległej z danymi.|

## <a name="universal-windows-platform-apps"></a>Aplikacje platforma uniwersalna systemu Windows

|Artykuł|Opis|
|-|-|
|[Tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)|W tym artykule opisano niektóre kluczowe kwestie, które należy wziąć pod uwagę podczas tworzenia asynchronicznych operacji w aplikacji platformy UWP przy użyciu środowisko uruchomieniowe współbieżności.|
|[Wskazówki: łączenie za pomocą zadań i żądań HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)|Pokazuje, w jaki sposób połączyć zadania PPL `IXMLHTTPRequest2` z `IXMLHTTPRequest2Callback` interfejsami i, aby wysyłać żądania HTTP GET i post do usługi sieci Web w aplikacji platformy UWP.|
|[Przykłady aplikacji środowisko wykonawcze systemu Windows](/samples/browse/?languages=cpp&expanded=windows&products=windows-uwp)|Zawiera przykłady kodu do pobrania i aplikacje demonstracyjne dla środowisko wykonawcze systemu Windows.|

## <a name="dataflow-programming-in-the-asynchronous-agents-library"></a>Programowanie przepływu danych w bibliotece agentów asynchronicznych

|Artykuł|Opis|
|-|-|
|[Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)<br /><br /> [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br /><br /> [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)<br /><br /> [Instrukcje: implementowanie różnych wzorców producentów i konsumentów](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)<br /><br /> [Instrukcje: zapewnianie funkcji pracy dla klas wywołania i transformatora](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)<br /><br /> [Instrukcje: używanie transformatora w potoku danych](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br /><br /> [Instrukcje: wybieranie spośród ukończonych zadań](../../parallel/concrt/how-to-select-among-completed-tasks.md)<br /><br /> [Instrukcje: Wysyłanie komunikatu w regularnych odstępach czasu](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)<br /><br /> [Instrukcje: korzystanie z filtru bloku komunikatów](../../parallel/concrt/how-to-use-a-message-block-filter.md)|Opisuje agentów asynchronicznych, bloków komunikatów i funkcji przekazywania komunikatów, które są blokami konstrukcyjnymi do wykonywania operacji przepływu danych w środowisko uruchomieniowe współbieżności.|
|[Przewodnik: Tworzenie aplikacji opartej na agencie](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br /><br /> [Przewodnik: tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)|Pokazuje, jak tworzyć podstawowe aplikacje oparte na agentach.|
|[Przewodnik: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)|Pokazuje, jak utworzyć sieć asynchronicznych bloków komunikatów, które wykonują przetwarzanie obrazu.|
|[Przewodnik: używanie sprzężenia w celu zapobiegania zakleszczeniom](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)|Używa problemu rekomendowanych lokali ucztujących, aby zilustrować, w jaki sposób używać środowisko uruchomieniowe współbieżności, aby zapobiec zakleszczeniom w aplikacji.|
|[Przewodnik: Tworzenie niestandardowego bloku komunikatów](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)|Pokazuje, jak utworzyć niestandardowy typ bloku komunikatów, który porządkuje wiadomości przychodzące według priorytetu.|
|[Najlepsze rozwiązania w bibliotece agentów asynchronicznych](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br /><br /> [Ogólne najlepsze rozwiązania w środowisko uruchomieniowe współbieżności](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Zawiera wskazówki i najlepsze rozwiązania dotyczące pracy z agentami.|

## <a name="exception-handling-and-debugging"></a>Obsługa wyjątków i debugowania

|Artykuł|Opis|
|-|-|
|[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Opisuje sposób pracy z wyjątkami w środowisko uruchomieniowe współbieżności.|
|[narzędzia diagnostyczne równoległe](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Uczysz się, jak dostosować aplikacje i korzystać z środowisko uruchomieniowe współbieżności.|

## <a name="tuning-performance"></a>Dostrajanie wydajności

|Artykuł|Opis|
|-|-|
|[narzędzia diagnostyczne równoległe](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Uczysz się, jak dostosować aplikacje i korzystać z środowisko uruchomieniowe współbieżności.|
|[Wystąpienia harmonogramu](../../parallel/concrt/scheduler-instances.md)<br /><br /> [Instrukcje: Zarządzanie wystąpieniem harmonogramu](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br /><br /> [Zasady usługi Scheduler](../../parallel/concrt/scheduler-policies.md)<br /><br /> [Instrukcje: Określanie określonych zasad harmonogramu](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br /><br /> [Instrukcje: Tworzenie agentów korzystających z określonych zasad usługi Scheduler](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)|Pokazuje, jak korzystać z zarządzania wystąpieniami harmonogramu i zasadami harmonogramu. W przypadku aplikacji klasycznych zasady harmonogramu umożliwiają kojarzenie określonych reguł z określonymi typami obciążeń. Na przykład można utworzyć jedno wystąpienie harmonogramu do uruchamiania niektórych zadań z podwyższonym priorytetem wątku i użyć domyślnego harmonogramu do uruchamiania innych zadań przy normalnym priorytecie wątku.|
|[Zaplanuj grupy](../../parallel/concrt/schedule-groups.md)<br /><br /> [Instrukcje: używanie grup harmonogramu do wywierania wpływu na kolejność wykonywania](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)|Demonstruje sposób używania grup harmonogramu do koligacji lub grupowania powiązanych zadań razem. Można na przykład wymagać wysokiego stopnia zaistnienia między powiązanymi zadaniami, gdy te zadania korzystają z wykonywania w tym samym węźle procesora.|
|[Zadania lekkie](../../parallel/concrt/lightweight-tasks.md)|Wyjaśnia, w jaki sposób uproszczone zadania są przydatne do tworzenia pracy, która nie wymaga równoważenia obciążenia ani anulowania oraz jak są również przydatne do adaptacji istniejącego kodu do użycia z środowisko uruchomieniowe współbieżności.|
|[Konteksty](../../parallel/concrt/contexts.md)<br /><br /> [Instrukcje: korzystanie z klasy kontekstu w celu zaimplementowania współdziałania ze wspólnym semaforem](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br /><br /> [Instrukcje: używanie nadsubskrypcji do opóźnienia przesunięcia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)|Opisuje sposób sterowania zachowaniem wątków zarządzanych przez środowisko uruchomieniowe współbieżności.|
|[Funkcje zarządzania pamięcią](../../parallel/concrt/memory-management-functions.md)<br /><br /> [Instrukcje: korzystanie z Alloc i Free w celu zwiększenia wydajności pamięci](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)|Opisuje funkcje zarządzania pamięcią, które zapewnia środowisko uruchomieniowe współbieżności, aby pomóc w współbieżnym przydzielaniu i wolnej pamięci.|

## <a name="additional-resources"></a>Dodatkowe zasoby

|Artykuł|Opis|
|-|-|
|[Wzorce programowania asynchronicznego i porady w Hilo (aplikacje do sklepu Windows przy użyciu języka C++ i języka XAML)](/previous-versions/windows/apps/jj160321(v=win.10))|Dowiedz się, w jaki sposób używamy środowisko uruchomieniowe współbieżności do implementowania operacji asynchronicznych w programie Hilo, aplikacji środowisko wykonawcze systemu Windows przy użyciu języka C++ i języka XAML.|
|[Programowanie równoległe w kodzie natywnym blogu](/archive/blogs/nativeconcurrency)|Oferuje dodatkowe szczegółowe artykuły w blogu dotyczące programowania równoległego w środowisko uruchomieniowe współbieżności.|
|[Obliczenia równoległe na platformie C++ i w natywnym forum kodu](https://go.microsoft.com/fwlink/p/?linkid=183874)|Umożliwia uczestnictwo w dyskusjach społeczności dotyczących środowisko uruchomieniowe współbieżności.|
|[Programowanie równoległe](/dotnet/standard/parallel-programming/index)|Uczy o modelu programowania równoległego, który jest dostępny w .NET Framework.|

## <a name="see-also"></a>Zobacz też

[Odwołanie](../../parallel/concrt/reference/reference-concurrency-runtime.md)
