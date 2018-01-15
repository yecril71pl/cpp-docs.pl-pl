---
title: Zasady harmonogramu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: scheduler policies
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6c2e669a429bebbfde19f54200610819d0849d8f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="scheduler-policies"></a>Zasady harmonogramu
Ten dokument zawiera opis roli zasad harmonogramu współbieżność środowiska wykonawczego. A *zasad harmonogramu* steruje strategii, używany w harmonogramie podczas zarządzania zadaniami. Rozważmy na przykład aplikację, która wymaga niektórych zadań do wykonania w `THREAD_PRIORITY_NORMAL` i innych zadań do wykonania w `THREAD_PRIORITY_HIGHEST`.  Można tworzyć dwa wystąpienia harmonogramu: jedną, która określa `ContextPriority` zasadach `THREAD_PRIORITY_NORMAL` oraz inne, które określa jednych zasad można `THREAD_PRIORITY_HIGHEST`.  
  
 Za pomocą zasad harmonogramu, można podzielić zasoby dostępne przetwarzania i przypisać do każdego harmonogramu stały zestaw zasobów. Rozważmy na przykład równoległych algorytmu, który nie obsługuje więcej niż cztery procesory. Możesz utworzyć zasady harmonogram, który ogranicza zadań jednocześnie używać nie więcej niż cztery procesory.  
  
> [!TIP]
>  Współbieżność środowiska wykonawczego zawiera harmonogram domyślny. W związku z tym nie trzeba utworzyć w aplikacji. Harmonogram zadań ułatwia dostrojenie wydajności aplikacji, dlatego zaleca się uruchamiania z [równoległych biblioteki wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md) lub [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) w przypadku jesteś nowym użytkownikiem współbieżności środowiska wykonawczego.  
  
 Jeśli używasz [concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create), [concurrency::Scheduler::Create](reference/scheduler-class.md#create), lub [concurrency::Scheduler::SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) metodę w celu utworzenia wystąpienia harmonogramu, musisz podać [concurrency::SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) obiekt, który zawiera kolekcję par klucz wartość, które określają zachowanie harmonogramu. `SchedulerPolicy` Konstruktor przyjmuje zmienną liczbę argumentów. Pierwszym argumentem jest liczba elementów zasad, które można określić. Pozostałe argumenty są pary klucz wartość dla każdego elementu zasad. Poniższy przykład tworzy `SchedulerPolicy` obiekt, który określa trzy elementy zasad. Środowisko uruchomieniowe są używane wartości domyślne dla kluczy zasad, które nie zostały określone.  

  
 [!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/cpp/scheduler-policies_1.cpp)]  
  

 [Concurrency::PolicyElementKey](reference/concurrency-namespace-enums.md#policyelementkey) wyliczenie definiuje klucze zasad, które są skojarzone z harmonogramu zadań. W poniższej tabeli opisano klucze zasad i wartość domyślną, która używa środowiska uruchomieniowego dla każdego z nich.  
  
|Klucz zasad|Opis|Wartość domyślna|  
|----------------|-----------------|-------------------|  
|`SchedulerKind`|A [concurrency::SchedulerType](reference/concurrency-namespace-enums.md#schedulertype) wartość, która określa typ wątków używanych do planowania zadań.|`ThreadScheduler`(Użyj normalnej wątki). To jest jedyną poprawną wartością dla tego klucza.|  
|`MaxConcurrency`|`unsigned int` Wartość, która określa maksymalną liczbę zasobów współbieżności, które korzysta z harmonogramu.|[CONCURRENCY::MaxExecutionResources](reference/concurrency-namespace-constants1.md#maxexecutionresources)|  
|`MinConcurrency`|`unsigned int` Wartość, która określa minimalną liczbę zasobów współbieżności, które korzysta z harmonogramu.|`1`|  
|`TargetOversubscriptionFactor`|`unsigned int` Wartość, która określa liczbę wątków ma zostać przydzielone do każdego zasobu przetwarzania.|`1`|  
|`LocalContextCacheSize`|`unsigned int` Wartość, która określa maksymalną liczbę kontekstach, które mogą być buforowane w lokalnej kolejce każdego procesora wirtualnego.|`8`|  
|`ContextStackSize`|`unsigned int` Wartość określająca rozmiar stosu, w kilobajtach, aby go zarezerwować dla każdego kontekstu.|`0`(Użyj domyślny rozmiar stosu)|  
|`ContextPriority`|`int` Wartość, która określa priorytet wątku każdego kontekstu. Może to być dowolna wartość, które można przekazać do [wykonanie funkcji SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) lub `INHERIT_THREAD_PRIORITY`.|`THREAD_PRIORITY_NORMAL`|  

|`SchedulingProtocol`| A [concurrency::SchedulingProtocolType](reference/concurrency-namespace-enums.md#schedulingprotocoltype) wartość, która określa planowania algorytm używany. |`EnhanceScheduleGroupLocality`|  
|`DynamicProgressFeedback`| A [concurrency::DynamicProgressFeedbackType](reference/concurrency-namespace-enums.md#dynamicprogressfeedbacktype) wartość, która określa, czy należy przeprowadzić ponowne równoważenie zasobów zgodnie z informacje o postępie na podstawie statystyk.<br /><br /> **Uwaga** ta zasada nie jest ustawiona `ProgressFeedbackDisabled` , ponieważ jest on zarezerwowany do użytku przez środowisko uruchomieniowe. |`ProgressFeedbackEnabled`|  

  
 Każdy harmonogramu używa własnych zasad podczas jego harmonogramy zadań. Zasady, które są skojarzone z jednego harmonogramu nie wpływają na zachowanie innych harmonogramu. Ponadto nie można zmienić zasad harmonogramu po utworzeniu `Scheduler` obiektu.  
  
> [!IMPORTANT]
>  Używaj tylko zasady harmonogramu do kontrolowania atrybutów dla wątków, które tworzy środowiska uruchomieniowego. Nie należy zmieniać koligacji wątku lub priorytetu wątków, które są tworzone w czasie wykonywania, ponieważ, która może spowodować niezdefiniowane zachowanie.  
  
 Środowisko uruchomieniowe tworzy domyślne harmonogramu dla Ciebie nie jawnie utworzysz jeden. Jeśli chcesz użyć domyślnego harmonogramu w aplikacji, ale aby określić zasady dla tego harmonogramu do użycia, wywołaj [concurrency::Scheduler::SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) metoda przed zaplanować równoległego pracy. Jeśli nie zostanie wywołana `Scheduler::SetDefaultSchedulerPolicy` metoda, używa środowiska wykonawczego domyślnych zasad wartości z tabeli.  
  
 Użyj [concurrency::CurrentScheduler::GetPolicy](reference/currentscheduler-class.md#getpolicy) i [concurrency::Scheduler::GetPolicy](reference/scheduler-class.md#getpolicy) metod do pobrania kopii zasad harmonogramu. Wartości zasad, które z tych metod może się różnić od wartości zasad, które można określić podczas tworzenia harmonogramu.  
  
## <a name="example"></a>Przykład  
 Badanie przykłady, które umożliwia kontrolowanie zachowania planista specjalnych zasad harmonogramu, zobacz [jak: Określ konkretne zasady harmonogramu](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md) i [porady: tworzenie agentów tego użyć określonego harmonogramu zasad](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Porady: Określanie specjalnych zasad harmonogramu](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)   
 [Instrukcje: tworzenie agentów korzystających ze specjalnych zasad harmonogramu](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)

