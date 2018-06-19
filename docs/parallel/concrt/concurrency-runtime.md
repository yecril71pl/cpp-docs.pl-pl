---
title: Współbieżność środowiska wykonawczego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Concurrency Runtime, getting started
- ConcRT (see Concurrency Runtime)
- Concurrency Runtime
ms.assetid: 874bc58f-8dce-483e-a3a1-4dcc9e52ed2c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc147a2cd0c75bb57f12be4dd5e90e63ab4ec0d2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693526"
---
# <a name="concurrency-runtime"></a>Współbieżność środowiska wykonawczego
Współbieżność środowiska wykonawczego dla języka C++ pomaga zapisu niezawodnych, skalowalnych i reakcji aplikacji równoległych. Uruchamia poziomie abstrakcji, dzięki czemu nie trzeba zarządzać szczegóły infrastruktury, które są związane z współbieżności. Można również użyć do określenia planowania zasad, które spełniają jakości usługi wymagań aplikacji. Dzięki tym zasobom ułatwiające rozpoczęcie pracy z współbieżności środowiska wykonawczego.  
  
 Dokumentację referencyjną dla [odwołania](../../parallel/concrt/reference/reference-concurrency-runtime.md).  
  
> [!TIP]
>  Współbieżność środowiska wykonawczego języka C ++ 11 funkcje rolę odgrywa i przyjmuje nowoczesną styl C++. Aby dowiedzieć się więcej, przeczytaj [języka c++ Zapraszamy ponownie](../../cpp/welcome-back-to-cpp-modern-cpp.md).  
  
## <a name="choosing-concurrency-runtime-features"></a>Wybieranie funkcji współbieżnych środowiska wykonawczego  
  
|||  
|-|-|  
|[Omówienie](../../parallel/concrt/overview-of-the-concurrency-runtime.md)|Zawiera wskazówki, dlaczego ważne jest i opisano najważniejsze funkcje w współbieżności środowiska wykonawczego.|  
|[Porównywanie z innymi modelami współbieżności](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|Pokazuje, jak porównuje współbieżności środowiska wykonawczego z innymi modelami współbieżności, takie jak Windows wątku puli i OpenMP, dzięki czemu można użyć danego modelu współbieżności, które będzie najlepiej dostosowane do wymagań aplikacji.|  
|[Migrowanie z OpenMP do środowiska uruchomieniowego współbieżności](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)|Porównuje OpenMP do współbieżności środowiska wykonawczego i przykłady dotyczące migracji istniejącego kodu OpenMP do współbieżności środowiska wykonawczego.|  
|[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Poznasz PPL, która zapewnia pętle równoległe, zadania i kontenerów równoległych.|  
|[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)|Przedstawiono sposób korzystania z agentów asynchronicznych i przekazywania można łatwo umieścić przepływu danych i przetwarzanie potokowe zadania aplikacji komunikatów.|  
|[Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)|Przedstawiono harmonogram zadań, co pozwala na dostrojenie wydajności aplikacji klasycznych, który korzysta ze współbieżności środowiska wykonawczego.|  
  
## <a name="task-parallelism-in-the-ppl"></a>Proste zadania w PPL  
  
|||  
|-|-|  
|[Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br /><br /> [Instrukcje: używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br /><br /> [Instrukcje: korzystanie z parallel_invoke podczas przeprowadzania operacji równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)<br /><br /> [Instrukcje: tworzenie zadania kończonego po opóźnieniu](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|W tym artykule opisano zadania i grupy zadań, które może pomóc w kodzie asynchroniczne i dekompozycji pracy równoległej na mniejsze części.|  
|[Przewodnik: wdrażanie przyszłych operacji](../../parallel/concrt/walkthrough-implementing-futures.md)|Pokazuje, jak połączyć czymś więcej funkcji współbieżność środowiska wykonawczego.|  
|[Przewodnik: usuwanie pracy z wątku interfejs użytkownika](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)|Pokazuje, jak można przenieść pracy wykonywanego przez wątek interfejsu użytkownika w aplikacji MFC do wątku roboczego.|  
|[Biblioteka wzorów równoległych — najlepsze praktyki](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Środowisko uruchomieniowe współbieżności — najlepsze praktyki ogólne](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Zawiera wskazówki i najlepsze rozwiązania dotyczące pracy z PPL.|  
  
## <a name="data-parallelism-in-the-ppl"></a>Równoległość danych w PPL  
  
|||  
|-|-|  
|[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br /><br /> [Instrukcje: pisanie pętli parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)<br /><br /> [Instrukcje: pisanie pętli parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)<br /><br /> [Instrukcje: równoległe wykonywanie operacji mapowania i zmniejszania](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|W tym artykule opisano `parallel_for`, `parallel_for_each`, `parallel_invoke`i inne algorytmy równoległe. Użyj zgodnych algorytmów równoległych rozwiązać *danych równoległych* problemy z działaniem kolekcji danych.|  
|[Równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md)<br /><br /> [Instrukcje: korzystanie z kontenerów równoległych do zwiększania wydajności](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br /><br /> [Instrukcje: korzystanie z wyników połączonych do poprawiania wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br /><br /> [Instrukcje: korzystanie z wyników połączonych w celu łączenia zestawów](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)|W tym artykule opisano `combinable` klasy, jak również `concurrent_vector`, `concurrent_queue`, `concurrent_unordered_map`i innych kontenerów równoległych. Użyj równoległe kontenery oraz obiekty potrzebują kontenery zapewniające bezpieczne wątkowo dostęp do swoich elementów.|  
|[Biblioteka wzorów równoległych — najlepsze praktyki](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Środowisko uruchomieniowe współbieżności — najlepsze praktyki ogólne](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Zawiera wskazówki i najlepsze rozwiązania dotyczące pracy z PPL.|  
  
## <a name="canceling-tasks-and-parallel-algorithms"></a>Anulowanie zadań i algorytmów równoległych  
  
|||  
|-|-|  
|[Anulowanie w PPL](cancellation-in-the-ppl.md)|Opisuje rolę anulowanie w PPL, łącznie ze sposobem inicjowania i odpowiadać na żądania anulowania.|  
|[Instrukcje: używanie anulowania, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br /><br /> [Instrukcje: używanie obsługi wyjątków, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Pokazuje można anulować pracy równoległe danych na dwa sposoby.|  
  
## <a name="universal-windows-platform-apps"></a>Windows uniwersalnych aplikacji platformy  
  
|||  
|-|-|  
|[Tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy uniwersalnej systemu Windows](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)|Opisano niektóre z najważniejszych należy wziąć pod uwagę w przypadku utworzenia asynchronicznych operacji w aplikacji platformy uniwersalnej systemu Windows za pomocą współbieżności środowiska wykonawczego.|  
|[Przewodnik: łączenie za pomocą zadań i żądań XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)|Pokazuje, jak łączyć zadania PPL z `IXMLHTTPRequest2` i `IXMLHTTPRequest2Callback` interfejsy do wysyłania żądań HTTP GET i POST do usługi sieci web w aplikacji platformy uniwersalnej systemu Windows.|  
|[Przykłady aplikacji do środowiska wykonawczego systemu Windows](http://code.msdn.microsoft.com/windowsapps)|Zawiera przykłady kodu do pobrania i pokaz aplikacji dla systemu Windows 8.x. Przykłady dla języka C++ Użyj współbieżność środowiska wykonawczego funkcje, takie jak PPL zadań do przetwarzania danych w tle do zachowania reakcji środowiska użytkownika.|  
  
## <a name="dataflow-programming-in-the-asynchronous-agents-library"></a>Programowanie przepływu danych w bibliotece agentów asynchronicznych  
  
|||  
|-|-|  
|[Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)<br /><br /> [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br /><br /> [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)<br /><br /> [Instrukcje: implementowanie różnych wzorców producent — konsument](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)<br /><br /> [Instrukcje: zapewnianie funkcji pracy dla wywoływania oraz klasy transformatora](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)<br /><br /> [Instrukcje: używanie transformatora w potoku danych](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br /><br /> [Instrukcje: wybieranie spośród zadań wykonanych](../../parallel/concrt/how-to-select-among-completed-tasks.md)<br /><br /> [Instrukcje: wysyłanie komunikatu w regularnych odstępach czasu](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)<br /><br /> [Instrukcje: korzystanie z filtra bloku komunikatów](../../parallel/concrt/how-to-use-a-message-block-filter.md)|Opisuje agentów asynchronicznych, bloki komunikatów i funkcje przekazywania komunikatów, które są blokami konstrukcyjnymi do wykonywania operacji przepływu danych w współbieżności środowiska wykonawczego.|  
|[Przewodnik: tworzenie aplikacji opartej o agentów](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br /><br /> [Przewodnik: tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)|Przedstawia sposób tworzenia podstawowej aplikacji opartych na agenta.|  
|[Przewodnik: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)|Pokazuje, jak utworzyć sieć bloki komunikatów asynchronicznych, które przetwarzania obrazu.|  
|[Przewodnik: korzystanie ze złączy w celu zapobiegania zakleszczeniom](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)|Używa lokali problem philosophers ilustrujący sposób korzystania ze współbieżności środowiska wykonawczego zapobiegające zakleszczenie w aplikacji.|  
|[Przewodnik: tworzenie niestandardowego bloku komunikatów](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)|Pokazuje, jak utworzyć komunikat niestandardowy typ bloku, któremu porządkuje komunikaty przychodzące według priorytetu.|  
|[Biblioteka agentów asynchronicznych — najlepsze praktyki](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br /><br /> [Środowisko uruchomieniowe współbieżności — najlepsze praktyki ogólne](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Zawiera wskazówki i najlepsze rozwiązania dotyczące pracy z agentami.|  
  
## <a name="exception-handling-and-debugging"></a>Obsługa wyjątków i debugowania  
  
|||  
|-|-|  
|[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Opisuje sposób pracy z wyjątkami współbieżność środowiska wykonawczego.|  
|[Równoległe narzędzia diagnostyczne](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Przedstawienie sposobu dopasowania, aplikacji i najbardziej efektywne wykorzystanie współbieżności środowiska wykonawczego.|  
  
## <a name="tuning-performance"></a>Dostrajanie wydajności  
  
|||  
|-|-|  
|[Równoległe narzędzia diagnostyczne](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Przedstawienie sposobu dopasowania, aplikacji i najbardziej efektywne wykorzystanie współbieżności środowiska wykonawczego.|  
|[Wystąpienia harmonogramu](../../parallel/concrt/scheduler-instances.md)<br /><br /> [Instrukcje: zarządzanie wystąpieniem harmonogramu](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br /><br /> [Zasady harmonogramu](../../parallel/concrt/scheduler-policies.md)<br /><br /> [Instrukcje: określanie specjalnych zasad harmonogramu](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br /><br /> [Instrukcje: tworzenie agentów korzystających ze specjalnych zasad harmonogramu](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)|Pokazuje, jak działa Zarządzanie wystąpienia harmonogramu i zasad harmonogramu. Zasady harmonogramu dla aplikacji klasycznych, umożliwiają skojarzyć określone zasady z określonych rodzajów obciążeń. Na przykład można utworzyć jedno wystąpienie harmonogramu niektórych zadań godzinie priorytetu wątku z podwyższonym poziomem uprawnień i użyć domyślnego harmonogramu do wykonywania innych zadań podczas priorytetu wątku normalnego.|  
|[Grupy harmonogramu](../../parallel/concrt/schedule-groups.md)<br /><br /> [Instrukcje: używanie grup harmonogramu do wywierania wpływu na kolejność wykonywania](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)|Demonstracja używanie grup harmonogramu do affinitize lub grupowania, powiązanych zadań. Na przykład może wymagać wysoki stopień miejscowości między zadania pokrewne, gdy te zadania korzystać z wykonania na tym samym węźle procesora.|  
|[Zadania lekkie](../../parallel/concrt/lightweight-tasks.md)|Wyjaśniono, jak lekkie zadania są przydatne do tworzenia pracy, który nie wymaga równoważenia obciążenia lub anulowanie i jak są one również przydatne w przypadku adaptacja istniejącego kodu do użycia z współbieżności środowiska wykonawczego.|  
|[Konteksty](../../parallel/concrt/contexts.md)<br /><br /> [Instrukcje: korzystanie z klasy kontekstu do wdrażania a kooperatywnego semafora](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br /><br /> [Instrukcje: używanie nadsubskrypcji do przesuwania opóźnienia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)|Zawiera opis sposobu kontrolowania zachowania wątków, które są zarządzane przez współbieżności środowiska wykonawczego.|  
|[Funkcje zarządzania pamięcią](../../parallel/concrt/memory-management-functions.md)<br /><br /> [Instrukcje: używanie z funkcji Alloc i Free do poprawiania wydajności pamięci](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)|Opisuje funkcje zarządzania pamięcią, udostępniające Aby przydzielić i zwolnić pamięć, w sposób równoczesnych współbieżności środowiska wykonawczego.|  
  
## <a name="additional-resources"></a>Dodatkowe zasoby  
  
|||  
|-|-|  
|[Programowanie asynchroniczne wzorce i porad w Hilo (aplikacje ze Sklepu Windows przy użyciu języka C++ i XAML)](http://msdn.microsoft.com/library/windows/apps/jj160321.aspx)|Dowiedz się, jak użyliśmy współbieżności środowiska wykonawczego do wykonania operacji asynchronicznych w Hilo, aplikacji środowiska wykonawczego systemu Windows, przy użyciu języka C++ i języka XAML.|  
|[Przykłady kodu dla współbieżność środowiska wykonawczego i Biblioteka równoległych wzorcem w Visual Studio 2010](http://go.microsoft.com/fwlink/p/?linkid=183875)|Zawiera przykładowe aplikacje i narzędzia, które przedstawiają współbieżności środowiska wykonawczego.|  
|[Programowanie równoległe w blogu kodu natywnego](http://go.microsoft.com/fwlink/p/?linkid=183873)|Udostępnia dodatkowe szczegółowe blogu artykułów na temat Programowanie równoległe w współbieżności środowiska wykonawczego.|  
|[Równoległe Computing forum C++ i kod natywny](http://go.microsoft.com/fwlink/p/?linkid=183874)|Umożliwia udział w dyskusjach społeczności o współbieżności środowiska wykonawczego.|  
|[Programowanie równoległe](/dotnet/standard/parallel-programming/index)|Zawiera informacje na temat równoległych modelu programowania, które są dostępne w [!INCLUDE[dnprdnshort](../../error-messages/tool-errors/includes/dnprdnshort_md.md)].|  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja](../../parallel/concrt/reference/reference-concurrency-runtime.md)


