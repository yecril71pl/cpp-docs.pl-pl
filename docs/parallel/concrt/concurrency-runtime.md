---
title: Współbieżność środowiska wykonawczego
ms.date: 07/20/2018
helpviewer_keywords:
- Concurrency Runtime, getting started
- ConcRT (see Concurrency Runtime)
- Concurrency Runtime
ms.assetid: 874bc58f-8dce-483e-a3a1-4dcc9e52ed2c
ms.openlocfilehash: a17b4439baaec9caacfeca08983d0255b5a145de
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141620"
---
# <a name="concurrency-runtime"></a>Współbieżność środowiska wykonawczego

Środowisko uruchomieniowe współbieżności dla programu C++ ułatwia pisanie niezawodnych, skalowalnych i szybko działających aplikacji równoległych. Podnosi poziom abstrakcji, aby nie trzeba było zarządzać szczegółami infrastruktury związanymi z współbieżnością. Można go również użyć do określenia zasad planowania, które spełniają wymagania dotyczące jakości usług aplikacji. Użyj tych zasobów, aby pomóc Ci rozpocząć pracę z środowisko uruchomieniowe współbieżności.

Dokumentacja referencyjna znajduje się w temacie [Reference](../../parallel/concrt/reference/reference-concurrency-runtime.md).

> [!TIP]
> Środowisko uruchomieniowe współbieżności opiera się na funkcjach C++ 11 i wdraża bardziej nowoczesny C++ styl. Aby dowiedzieć się więcej, przeczytaj temat [Witamy z powrotem do C++ ](../../cpp/welcome-back-to-cpp-modern-cpp.md).

## <a name="choosing-concurrency-runtime-features"></a>Wybieranie funkcji współbieżnych środowiska wykonawczego

|||
|-|-|
|[Omówienie](../../parallel/concrt/overview-of-the-concurrency-runtime.md)|Uczy, dlaczego środowisko uruchomieniowe współbieżności jest ważna i opisuje jej najważniejsze funkcje.|
|[Porównywanie z innymi modelami współbieżności](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|Pokazuje, w jaki sposób środowisko uruchomieniowe współbieżności porównuje się z innymi modelami współbieżności, takimi jak Pula wątków systemu Windows i OpenMP, aby można było użyć modelu współbieżności, który najlepiej spełnia wymagania aplikacji.|
|[Migrowanie z OpenMP do środowiska uruchomieniowego współbieżności](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)|Porównuje wartość OpenMP z środowisko uruchomieniowe współbieżności i zawiera przykłady dotyczące sposobu migrowania istniejącego kodu OpenMP w celu użycia środowisko uruchomieniowe współbieżności.|
|[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Wprowadza do PPL, który zapewnia pętle równoległe, zadania i kontenery równoległe.|
|[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)|W tym temacie przedstawiono sposób używania asynchronicznych agentów i komunikatów, które umożliwiają łatwe dołączanie zadań przepływu danych i potokowych w aplikacjach.|
|[Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)|Wprowadza do Harmonogram zadań, co umożliwia precyzyjne dostosowanie wydajności aplikacji klasycznych, które korzystają z środowisko uruchomieniowe współbieżności.|

## <a name="task-parallelism-in-the-ppl"></a>Proste zadania w PPL

|||
|-|-|
|[Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br /><br /> [Instrukcje: używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br /><br /> [Instrukcje: korzystanie z parallel_invoke podczas przeprowadzania operacji równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)<br /><br /> [Instrukcje: tworzenie zadania kończonego po opóźnieniu](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Opisuje zadania i grupy zadań, które mogą ułatwić pisanie kodu asynchronicznego i rozkładanie pracy równoległej na mniejsze części.|
|[Przewodnik: wdrażanie przyszłych operacji](../../parallel/concrt/walkthrough-implementing-futures.md)|Pokazuje, jak połączyć funkcje środowisko uruchomieniowe współbieżności, aby zrobić coś więcej.|
|[Przewodnik: usuwanie pracy z wątku interfejs użytkownika](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)|Pokazuje, w jaki sposób przenieść zadania wykonywane przez wątek interfejsu użytkownika w aplikacji MFC do wątku roboczego.|
|[Biblioteka wzorów równoległych — najlepsze praktyki](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Środowisko uruchomieniowe współbieżności — najlepsze praktyki ogólne](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Zawiera wskazówki i najlepsze rozwiązania dotyczące pracy z PPL.|

## <a name="data-parallelism-in-the-ppl"></a>Równoległość danych w PPL

|||
|-|-|
|[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br /><br /> [Instrukcje: pisanie pętli parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)<br /><br /> [Instrukcje: pisanie pętli parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)<br /><br /> [Instrukcje: równoległe wykonywanie operacji mapowania i zmniejszania](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Opisuje `parallel_for`, `parallel_for_each`, `parallel_invoke`i innych algorytmów równoległych. Algorytmy równoległe służą do rozwiązywania problemów *równoległych dotyczących danych* , które obejmują kolekcje danych.|
|[Równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md)<br /><br /> [Instrukcje: korzystanie z kontenerów równoległych do zwiększania wydajności](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br /><br /> [Instrukcje: korzystanie z wyników połączonych do poprawiania wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br /><br /> [Instrukcje: korzystanie z wyników połączonych w celu łączenia zestawów](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)|Opisuje klasę `combinable`, a także `concurrent_vector`, `concurrent_queue`, `concurrent_unordered_map`i innych kontenerów równoległych. Używaj kontenerów równoległych i obiektów, gdy wymagane są kontenery zapewniające bezpieczny wątkowy dostęp do ich elementów.|
|[Biblioteka wzorów równoległych — najlepsze praktyki](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Środowisko uruchomieniowe współbieżności — najlepsze praktyki ogólne](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Zawiera wskazówki i najlepsze rozwiązania dotyczące pracy z PPL.|

## <a name="canceling-tasks-and-parallel-algorithms"></a>Anulowanie zadań i algorytmów równoległych

|||
|-|-|
|[Anulowanie w PPL](cancellation-in-the-ppl.md)|Opisuje rolę anulowania w PPL, w tym sposób inicjowania i reagowania na żądania anulowania.|
|[Instrukcje: używanie anulowania, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br /><br /> [Instrukcje: używanie obsługi wyjątków, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Ilustruje dwa sposoby anulowania pracy równoległej z danymi.|

## <a name="universal-windows-platform-apps"></a>Windows Universal apps platformy

|||
|-|-|
|[Tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy uniwersalnej systemu Windows](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)|W tym artykule opisano niektóre kluczowe kwestie, które należy wziąć pod uwagę podczas tworzenia asynchronicznych operacji w aplikacji platformy UWP przy użyciu środowisko uruchomieniowe współbieżności.|
|[Przewodnik: łączenie za pomocą zadań i żądań XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)|Pokazuje, w jaki sposób połączyć zadania PPL z interfejsami `IXMLHTTPRequest2` i `IXMLHTTPRequest2Callback`, aby wysyłać żądania HTTP GET i POST do usługi sieci Web w aplikacji platformy UWP.|
|[Przykłady aplikacji środowisko wykonawcze systemu Windows](https://code.msdn.microsoft.com/windowsapps)|Zawiera przykłady kodu do pobrania i aplikacje demonstracyjne dla systemu Windows 8. x. C++ Przykłady wykorzystują środowisko uruchomieniowe współbieżności funkcje, takie jak zadania PPL do przetwarzania danych w tle, aby zapewnić REAGOWANIe środowiska pracy.|

## <a name="dataflow-programming-in-the-asynchronous-agents-library"></a>Programowanie przepływu danych w bibliotece agentów asynchronicznych

|||
|-|-|
|[Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)<br /><br /> [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br /><br /> [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)<br /><br /> [Instrukcje: implementowanie różnych wzorców producent — konsument](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)<br /><br /> [Instrukcje: zapewnianie funkcji pracy dla wywoływania oraz klasy transformatora](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)<br /><br /> [Instrukcje: używanie transformatora w potoku danych](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br /><br /> [Instrukcje: wybieranie spośród zadań wykonanych](../../parallel/concrt/how-to-select-among-completed-tasks.md)<br /><br /> [Instrukcje: wysyłanie komunikatu w regularnych odstępach czasu](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)<br /><br /> [Instrukcje: korzystanie z filtra bloku komunikatów](../../parallel/concrt/how-to-use-a-message-block-filter.md)|Opisuje agentów asynchronicznych, bloków komunikatów i funkcji przekazywania komunikatów, które są blokami konstrukcyjnymi do wykonywania operacji przepływu danych w środowisko uruchomieniowe współbieżności.|
|[Przewodnik: tworzenie aplikacji opartej o agentów](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br /><br /> [Przewodnik: tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)|Pokazuje, jak tworzyć podstawowe aplikacje oparte na agentach.|
|[Przewodnik: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)|Pokazuje, jak utworzyć sieć asynchronicznych bloków komunikatów, które wykonują przetwarzanie obrazu.|
|[Przewodnik: korzystanie ze złączy w celu zapobiegania zakleszczeniom](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)|Używa problemu rekomendowanych lokali ucztujących, aby zilustrować, w jaki sposób używać środowisko uruchomieniowe współbieżności, aby zapobiec zakleszczeniom w aplikacji.|
|[Przewodnik: tworzenie niestandardowego bloku komunikatów](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)|Pokazuje, jak utworzyć niestandardowy typ bloku komunikatów, który porządkuje wiadomości przychodzące według priorytetu.|
|[Biblioteka agentów asynchronicznych — najlepsze praktyki](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br /><br /> [Środowisko uruchomieniowe współbieżności — najlepsze praktyki ogólne](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Zawiera wskazówki i najlepsze rozwiązania dotyczące pracy z agentami.|

## <a name="exception-handling-and-debugging"></a>Obsługa wyjątków i debugowania

|||
|-|-|
|[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Opisuje sposób pracy z wyjątkami w środowisko uruchomieniowe współbieżności.|
|[Równoległe narzędzia diagnostyczne](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Uczysz się, jak dostosować aplikacje i korzystać z środowisko uruchomieniowe współbieżności.|

## <a name="tuning-performance"></a>Dostrajanie wydajności

|||
|-|-|
|[Równoległe narzędzia diagnostyczne](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Uczysz się, jak dostosować aplikacje i korzystać z środowisko uruchomieniowe współbieżności.|
|[Wystąpienia harmonogramu](../../parallel/concrt/scheduler-instances.md)<br /><br /> [Instrukcje: zarządzanie wystąpieniem harmonogramu](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br /><br /> [Zasady harmonogramu](../../parallel/concrt/scheduler-policies.md)<br /><br /> [Instrukcje: określanie specjalnych zasad harmonogramu](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br /><br /> [Instrukcje: tworzenie agentów korzystających ze specjalnych zasad harmonogramu](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)|Pokazuje, jak korzystać z zarządzania wystąpieniami harmonogramu i zasadami harmonogramu. W przypadku aplikacji klasycznych zasady harmonogramu umożliwiają kojarzenie określonych reguł z określonymi typami obciążeń. Na przykład można utworzyć jedno wystąpienie harmonogramu do uruchamiania niektórych zadań z podwyższonym priorytetem wątku i użyć domyślnego harmonogramu do uruchamiania innych zadań przy normalnym priorytecie wątku.|
|[Grupy harmonogramu](../../parallel/concrt/schedule-groups.md)<br /><br /> [Instrukcje: używanie grup harmonogramu do wywierania wpływu na kolejność wykonywania](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)|Demonstruje sposób używania grup harmonogramu do koligacji lub grupowania powiązanych zadań razem. Można na przykład wymagać wysokiego stopnia zaistnienia między powiązanymi zadaniami, gdy te zadania korzystają z wykonywania w tym samym węźle procesora.|
|[Zadania lekkie](../../parallel/concrt/lightweight-tasks.md)|Wyjaśnia, w jaki sposób uproszczone zadania są przydatne do tworzenia pracy, która nie wymaga równoważenia obciążenia ani anulowania oraz jak są również przydatne do adaptacji istniejącego kodu do użycia z środowisko uruchomieniowe współbieżności.|
|[Konteksty](../../parallel/concrt/contexts.md)<br /><br /> [Instrukcje: korzystanie z klasy kontekstu do wdrażania a kooperatywnego semafora](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br /><br /> [Instrukcje: używanie nadsubskrypcji do przesuwania opóźnienia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)|Opisuje sposób sterowania zachowaniem wątków zarządzanych przez środowisko uruchomieniowe współbieżności.|
|[Funkcje zarządzania pamięcią](../../parallel/concrt/memory-management-functions.md)<br /><br /> [Instrukcje: używanie z funkcji Alloc i Free do poprawiania wydajności pamięci](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)|Opisuje funkcje zarządzania pamięcią, które zapewnia środowisko uruchomieniowe współbieżności, aby pomóc w współbieżnym przydzielaniu i wolnej pamięci.|

## <a name="additional-resources"></a>Dodatkowe zasoby

|||
|-|-|
|[Wzorce programowania asynchronicznego i porady w Hilo (aplikacje ze sklepu Windows C++ przy użyciu i XAML)](/previous-versions/windows/apps/jj160321(v=win.10))|Dowiedz się, w jaki sposób używamy środowisko uruchomieniowe współbieżności do implementowania operacji asynchronicznych w C++ programie Hilo, aplikacji środowisko wykonawcze systemu Windows przy użyciu i języka XAML.|
|[Programowanie równoległe w kodzie natywnym blogu](https://go.microsoft.com/fwlink/p/?linkid=183873)|Oferuje dodatkowe szczegółowe artykuły w blogu dotyczące programowania równoległego w środowisko uruchomieniowe współbieżności.|
|[Przetwarzanie równoległe C++ na forum i w kodzie natywnym](https://go.microsoft.com/fwlink/p/?linkid=183874)|Umożliwia uczestnictwo w dyskusjach społeczności dotyczących środowisko uruchomieniowe współbieżności.|
|[Programowanie równoległe](/dotnet/standard/parallel-programming/index)|Uczy o modelu programowania równoległego, który jest dostępny w .NET Framework.|

## <a name="see-also"></a>Zobacz też

[Dokumentacja](../../parallel/concrt/reference/reference-concurrency-runtime.md)
