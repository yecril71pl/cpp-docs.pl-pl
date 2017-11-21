---
title: "Współbieżność środowiska wykonawczego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Concurrency Runtime, getting started
- ConcRT (see Concurrency Runtime)
- Concurrency Runtime
ms.assetid: 874bc58f-8dce-483e-a3a1-4dcc9e52ed2c
caps.latest.revision: "40"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 87521d761a0355903408debe3ff27d26a006368b
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
|[Migrowanie z OpenMP do współbieżności środowiska wykonawczego](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)|Porównuje OpenMP do współbieżności środowiska wykonawczego i przykłady dotyczące migracji istniejącego kodu OpenMP do współbieżności środowiska wykonawczego.|  
|[Biblioteka równoległych wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Poznasz PPL, która zapewnia pętle równoległe, zadania i kontenerów równoległych.|  
|[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)|Przedstawiono sposób korzystania z agentów asynchronicznych i przekazywania można łatwo umieścić przepływu danych i przetwarzanie potokowe zadania aplikacji komunikatów.|  
|[Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)|Przedstawiono harmonogram zadań, co pozwala na dostrojenie wydajności aplikacji klasycznych, który korzysta ze współbieżności środowiska wykonawczego.|  
  
## <a name="task-parallelism-in-the-ppl"></a>Proste zadania w PPL  
  
|||  
|-|-|  
|[Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br /><br /> [Porady: używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br /><br /> [Porady: Korzystanie z parallel_invoke do przeprowadzania operacji równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)<br /><br /> [Porady: Tworzenie zadania kończonego po opóźnieniu](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|W tym artykule opisano zadania i grupy zadań, które może pomóc w kodzie asynchroniczne i dekompozycji pracy równoległej na mniejsze części.|  
|[Wskazówki: Wdrażanie przyszłych operacji](../../parallel/concrt/walkthrough-implementing-futures.md)|Pokazuje, jak połączyć czymś więcej funkcji współbieżność środowiska wykonawczego.|  
|[Wskazówki: Usuwanie pracy z wątku interfejsu użytkownika](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)|Pokazuje, jak można przenieść pracy wykonywanego przez wątek interfejsu użytkownika w aplikacji MFC do wątku roboczego.|  
|[Biblioteka wzorów równoległych — najlepsze praktyki](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Najlepsze praktyki ogólne współbieżności środowiska wykonawczego](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Zawiera wskazówki i najlepsze rozwiązania dotyczące pracy z PPL.|  
  
## <a name="data-parallelism-in-the-ppl"></a>Równoległość danych w PPL  
  
|||  
|-|-|  
|[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br /><br /> [Porady: pisanie pętli parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)<br /><br /> [Porady: pisanie pętli parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)<br /><br /> [Porady: wykonywanie mapowania i zmniejszanie operacji wykonywane równolegle](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|W tym artykule opisano `parallel_for`, `parallel_for_each`, `parallel_invoke`i inne algorytmy równoległe. Użyj zgodnych algorytmów równoległych rozwiązać *danych równoległych* problemy z działaniem kolekcji danych.|  
|[Równoległe kontenery i obiekty](../../parallel/concrt/parallel-containers-and-objects.md)<br /><br /> [Porady: Korzystanie z kontenerów równoległych do zwiększania wydajności](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br /><br /> [Porady: Korzystanie z wyników połączonych do poprawiania wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br /><br /> [Porady: Korzystanie z wyników połączonych w celu łączenia zestawów](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)|W tym artykule opisano `combinable` klasy, jak również `concurrent_vector`, `concurrent_queue`, `concurrent_unordered_map`i innych kontenerów równoległych. Użyj równoległe kontenery oraz obiekty potrzebują kontenery zapewniające bezpieczne wątkowo dostęp do swoich elementów.|  
|[Biblioteka wzorów równoległych — najlepsze praktyki](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Najlepsze praktyki ogólne współbieżności środowiska wykonawczego](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Zawiera wskazówki i najlepsze rozwiązania dotyczące pracy z PPL.|  
  
## <a name="canceling-tasks-and-parallel-algorithms"></a>Anulowanie zadań i algorytmów równoległych  
  
|||  
|-|-|  
|[Anulowanie w PPL](cancellation-in-the-ppl.md)|Opisuje rolę anulowanie w PPL, łącznie ze sposobem inicjowania i odpowiadać na żądania anulowania.|  
|[Porady: Użyj anulowania, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br /><br /> [Porady: Użyj obsługi aby przerwać pętlę równoległą wyjątków](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Pokazuje można anulować pracy równoległe danych na dwa sposoby.|  
  
## <a name="windows-store-apps"></a>Aplikacje Windows Store  
  
|||  
|-|-|  
|[Tworzenie operacji asynchronicznych w języku C++ dla aplikacji ze Sklepu Windows](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)|W tym artykule opisano niektóre z najważniejszych należy wziąć pod uwagę korzystania ze współbieżności środowiska wykonawczego wygenerowało operacji asynchronicznych w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji.|  
|[Wskazówki: Łączenie za pomocą zadań i żądań XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)|Pokazuje, jak łączyć zadania PPL z `IXMLHTTPRequest2` i `IXMLHTTPRequest2Callback` interfejsy do wysyłania żądań HTTP GET i POST do usługi sieci web w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji.|  
|[Przykłady aplikacji do Sklepu Windows](http://code.msdn.microsoft.com/windowsapps)|Zawiera przykłady kodu do pobrania i pokaz aplikacji dla [!INCLUDE[win8](../../build/reference/includes/win8_md.md)]. Przykłady dla języka C++ Użyj współbieżność środowiska wykonawczego funkcje, takie jak PPL zadań do przetwarzania danych w tle do zachowania reakcji środowiska użytkownika.|  
  
## <a name="dataflow-programming-in-the-asynchronous-agents-library"></a>Programowanie przepływu danych w bibliotece agentów asynchronicznych  
  
|||  
|-|-|  
|[Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)<br /><br /> [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br /><br /> [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)<br /><br /> [Porady: Implementowanie różnych wzorców producent — konsument](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)<br /><br /> [Porady: zapewnianie funkcji pracy wywoływania oraz klasy transformatora](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)<br /><br /> [Porady: używanie transformatora w potoku danych](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br /><br /> [Porady: Wybieranie spośród zadań wykonanych](../../parallel/concrt/how-to-select-among-completed-tasks.md)<br /><br /> [Porady: wysyłanie komunikatu w regularnych odstępach czasu](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)<br /><br /> [Porady: Użyj filtra bloku komunikatów](../../parallel/concrt/how-to-use-a-message-block-filter.md)|Opisuje agentów asynchronicznych, bloki komunikatów i funkcje przekazywania komunikatów, które są blokami konstrukcyjnymi do wykonywania operacji przepływu danych w współbieżności środowiska wykonawczego.|  
|[Wskazówki: Tworzenie aplikacji opartej o agentów](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br /><br /> [Wskazówki: Tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)|Przedstawia sposób tworzenia podstawowej aplikacji opartych na agenta.|  
|[Wskazówki: Tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)|Pokazuje, jak utworzyć sieć bloki komunikatów asynchronicznych, które przetwarzania obrazu.|  
|[Wskazówki: Używanie w celu zapobiegania zakleszczeniom](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)|Używa lokali problem philosophers ilustrujący sposób korzystania ze współbieżności środowiska wykonawczego zapobiegające zakleszczenie w aplikacji.|  
|[Wskazówki: Tworzenie niestandardowego bloku komunikatów](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)|Pokazuje, jak utworzyć komunikat niestandardowy typ bloku, któremu porządkuje komunikaty przychodzące według priorytetu.|  
|[Biblioteki agentów asynchronicznych — najlepsze praktyki](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br /><br /> [Najlepsze praktyki ogólne współbieżności środowiska wykonawczego](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Zawiera wskazówki i najlepsze rozwiązania dotyczące pracy z agentami.|  
  
## <a name="exception-handling-and-debugging"></a>Obsługa wyjątków i debugowania  
  
|||  
|-|-|  
|[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Opisuje sposób pracy z wyjątkami współbieżność środowiska wykonawczego.|  
|[Równoległe narzędzia diagnostyczne](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Przedstawienie sposobu dopasowania, aplikacji i najbardziej efektywne wykorzystanie współbieżności środowiska wykonawczego.|  
  
## <a name="tuning-performance"></a>Dostrajanie wydajności  
  
|||  
|-|-|  
|[Równoległe narzędzia diagnostyczne](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Przedstawienie sposobu dopasowania, aplikacji i najbardziej efektywne wykorzystanie współbieżności środowiska wykonawczego.|  
|[Wystąpienia harmonogramu](../../parallel/concrt/scheduler-instances.md)<br /><br /> [Porady: Zarządzanie przypadkiem Planisty](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br /><br /> [Zasady harmonogramu](../../parallel/concrt/scheduler-policies.md)<br /><br /> [Porady: Określanie specjalnych zasad harmonogramu](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br /><br /> [Porady: tworzenie agentów korzystających ze specjalnych zasad harmonogramu](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)|Pokazuje, jak działa Zarządzanie wystąpienia harmonogramu i zasad harmonogramu. Zasady harmonogramu dla aplikacji klasycznych, umożliwiają skojarzyć określone zasady z określonych rodzajów obciążeń. Na przykład można utworzyć jedno wystąpienie harmonogramu niektórych zadań godzinie priorytetu wątku z podwyższonym poziomem uprawnień i użyć domyślnego harmonogramu do wykonywania innych zadań podczas priorytetu wątku normalnego.|  
|[Grupy harmonogramu](../../parallel/concrt/schedule-groups.md)<br /><br /> [Porady: Używanie grup harmonogramu do wywierania wpływu na kolejność wykonywania](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)|Demonstracja używanie grup harmonogramu do affinitize lub grupowania, powiązanych zadań. Na przykład może wymagać wysoki stopień miejscowości między zadania pokrewne, gdy te zadania korzystać z wykonania na tym samym węźle procesora.|  
|[Zadania lekkie](../../parallel/concrt/lightweight-tasks.md)|Wyjaśniono, jak lekkie zadania są przydatne do tworzenia pracy, który nie wymaga równoważenia obciążenia lub anulowanie i jak są one również przydatne w przypadku adaptacja istniejącego kodu do użycia z współbieżności środowiska wykonawczego.|  
|[Konteksty](../../parallel/concrt/contexts.md)<br /><br /> [Porady: Korzystanie z klasy kontekstu do wdrażania Kooperatywnego semafora](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br /><br /> [Porady: używanie Nadsubskrypcji do przesuwania opóźnienia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)|Zawiera opis sposobu kontrolowania zachowania wątków, które są zarządzane przez współbieżności środowiska wykonawczego.|  
|[Funkcje zarządzania pamięcią](../../parallel/concrt/memory-management-functions.md)<br /><br /> [Porady: używanie z funkcji Alloc i Free do poprawiania wydajności pamięci](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)|Opisuje funkcje zarządzania pamięcią, udostępniające Aby przydzielić i zwolnić pamięć, w sposób równoczesnych współbieżności środowiska wykonawczego.|  
  
## <a name="additional-resources"></a>Dodatkowe zasoby  
  
|||  
|-|-|  
|[Programowanie asynchroniczne wzorce i porad w Hilo (aplikacje ze Sklepu Windows przy użyciu języka C++ i XAML)](http://msdn.microsoft.com/library/windows/apps/jj160321.aspx)|Dowiedz się, jak użyliśmy współbieżności środowiska wykonawczego do wykonania operacji asynchronicznych w Hilo, [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji przy użyciu języka C++ i języka XAML.|  
|[Przykłady kodu dla współbieżność środowiska wykonawczego i Biblioteka równoległych wzorcem w Visual Studio 2010](http://go.microsoft.com/fwlink/linkid=183875)|Zawiera przykładowe aplikacje i narzędzia, które przedstawiają współbieżności środowiska wykonawczego.|  
|[Programowanie równoległe w blogu kodu natywnego](http://go.microsoft.com/fwlink/linkid=183873)|Udostępnia dodatkowe szczegółowe blogu artykułów na temat Programowanie równoległe w współbieżności środowiska wykonawczego.|  
|[Równoległe Computing forum C++ i kod natywny](http://go.microsoft.com/fwlink/linkid=183874)|Umożliwia udział w dyskusjach społeczności o współbieżności środowiska wykonawczego.|  
|[Programowanie równoległe](/dotnet/standard/parallel-programming/index)|Zawiera informacje na temat równoległych modelu programowania, które są dostępne w [!INCLUDE[dnprdnshort](../../error-messages/tool-errors/includes/dnprdnshort_md.md)].|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie](../../parallel/concrt/reference/reference-concurrency-runtime.md)


