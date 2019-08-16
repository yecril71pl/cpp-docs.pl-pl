---
title: Zasady harmonogramu
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
ms.openlocfilehash: 5569ed9fb6229373ba59d687f21627ac9415050f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510462"
---
# <a name="scheduler-policies"></a>Zasady harmonogramu

W tym dokumencie opisano role zasad usługi Scheduler w środowisko uruchomieniowe współbieżności. *Zasady harmonogramu* kontrolują strategię używaną przez harmonogram podczas zarządzania zadaniami. Rozważmy na przykład aplikację, która wymaga wykonania `THREAD_PRIORITY_NORMAL` pewnych zadań, i innych zadań do wykonania na. `THREAD_PRIORITY_HIGHEST`  Można utworzyć dwa wystąpienia harmonogramu: takie, które określa `ContextPriority` zasady, które mają być `THREAD_PRIORITY_NORMAL` i inne, które określają te same zasady `THREAD_PRIORITY_HIGHEST`.

Korzystając z zasad usługi Scheduler, można podzielić dostępne zasoby przetwarzania i przypisać do każdego harmonogramu stały zestaw zasobów. Rozważmy na przykład algorytm równoległy, który nie jest skalowany poza czterema procesorami. Można utworzyć zasady harmonogramu, które ograniczają swoje zadania do korzystania z nie więcej niż czterech procesorów jednocześnie.

> [!TIP]
>  Środowisko uruchomieniowe współbieżności udostępnia domyślny harmonogram. W związku z tym nie trzeba go tworzyć w aplikacji. Ponieważ Harmonogram zadań ułatwia dostosowanie wydajności aplikacji, zalecamy rozpoczęcie od [biblioteki równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) lub [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) , jeśli są one nowe dla środowisko uruchomieniowe współbieżności.

W przypadku korzystania z metody [concurrency:: CurrentScheduler:: Create](reference/currentscheduler-class.md#create), [concurrency:: Scheduler:: Create](reference/scheduler-class.md#create)lub [concurrency:: Scheduler:: SetDefaultSchedulerPolicy —](reference/scheduler-class.md#setdefaultschedulerpolicy) w celu utworzenia wystąpienia harmonogramu należy podać [współbieżność:: Obiekt SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) , który zawiera kolekcję par klucz-wartość, które określają zachowanie harmonogramu. `SchedulerPolicy` Konstruktor przyjmuje zmienną liczbę argumentów. Pierwszy argument to liczba elementów zasad, które można określić. Pozostałe argumenty to pary klucz-wartość dla każdego elementu zasad. Poniższy przykład tworzy `SchedulerPolicy` obiekt, który określa trzy elementy zasad. Środowisko uruchomieniowe używa wartości domyślnych dla kluczy zasad, które nie są określone.

[!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/cpp/scheduler-policies_1.cpp)]

[Olicyelementkey "concurrency::P](reference/concurrency-namespace-enums.md#policyelementkey) Enumeration definiuje klucze zasad, które są skojarzone z harmonogram zadań. Poniższa tabela zawiera opis kluczy zasad i wartości domyślnej używanej przez środowisko uruchomieniowe dla każdego z nich.

|Klucz zasad|Opis|Wartość domyślna|
|----------------|-----------------|-------------------|
|`SchedulerKind`|[Concurrency:: SchedulerType](reference/concurrency-namespace-enums.md#schedulertype) wartość określająca typ wątków do użycia w celu planowania zadań.|`ThreadScheduler`(Użyj zwykłych wątków). Jest to jedyna prawidłowa wartość dla tego klucza.|
|`MaxConcurrency`|`unsigned int` Wartość określająca maksymalną liczbę zasobów współbieżności używanych przez harmonogram.|[concurrency:: MaxExecutionResources —](reference/concurrency-namespace-constants1.md#maxexecutionresources)|
|`MinConcurrency`|`unsigned int` Wartość określająca minimalną liczbę zasobów współbieżności używanych przez harmonogram.|`1`|
|`TargetOversubscriptionFactor`|`unsigned int` Wartość określająca liczbę wątków do przydzielenia do każdego zasobu przetwarzania.|`1`|
|`LocalContextCacheSize`|`unsigned int` Wartość określająca maksymalną liczbę kontekstów, które mogą być buforowane w lokalnej kolejce każdego procesora wirtualnego.|`8`|
|`ContextStackSize`|`unsigned int` Wartość określająca rozmiar stosu w kilobajtach, który ma zostać zarezerwowany dla każdego kontekstu.|`0`(Użyj domyślnego rozmiaru stosu)|
|`ContextPriority`|`int` Wartość, która określa priorytet wątku dla każdego kontekstu. Może to być dowolna wartość, którą można przekazać [](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) do SetThreadPriority `INHERIT_THREAD_PRIORITY`lub.|`THREAD_PRIORITY_NORMAL`|

|`SchedulingProtocol`| [Concurrency:: SchedulingProtocolType —](reference/concurrency-namespace-enums.md#schedulingprotocoltype) wartość określająca algorytm planowania do użycia. | `EnhanceScheduleGroupLocality`| | `DynamicProgressFeedback`| [Współbieżność::D ynamicprogressfeedbacktype](reference/concurrency-namespace-enums.md#dynamicprogressfeedbacktype) wartość określająca, czy należy zrównoważyć zasoby zgodnie z informacjami o postępie opartym na statystyce.<br /><br /> **Uwaga** Nie należy ustawiać tych zasad `ProgressFeedbackDisabled` , ponieważ są one zarezerwowane do użytku przez środowisko uruchomieniowe. |`ProgressFeedbackEnabled`|

Każdy harmonogram używa własnych zasad podczas planowania zadań. Zasady skojarzone z jednym harmonogramem nie wpływają na zachowanie innych harmonogramów. Ponadto nie można zmienić zasad harmonogramu po utworzeniu `Scheduler` obiektu.

> [!IMPORTANT]
>  Używaj tylko zasad usługi Scheduler, aby kontrolować atrybuty dla wątków tworzonych przez środowisko uruchomieniowe. Nie należy zmieniać koligacji wątku ani priorytetów wątków tworzonych przez środowisko uruchomieniowe, ponieważ może to spowodować niezdefiniowane zachowanie.

Środowisko uruchomieniowe tworzy domyślnego harmonogramu, jeśli nie zostanie on jawnie utworzony. Jeśli chcesz użyć domyślnego harmonogramu w aplikacji, ale chcesz określić zasady dla tego harmonogramu do użycia, wywołaj metodę [concurrency:: Scheduler:: SetDefaultSchedulerPolicy —](reference/scheduler-class.md#setdefaultschedulerpolicy) przed zaplanowaniem pracy równoległej. Jeśli `Scheduler::SetDefaultSchedulerPolicy` Metoda nie zostanie wywołana, środowisko uruchomieniowe użyje domyślnych wartości zasad z tabeli.

Użyj metody [concurrency:: CurrentScheduler:: GetPolicy](reference/currentscheduler-class.md#getpolicy) i [concurrency:: Scheduler:: GetPolicy](reference/scheduler-class.md#getpolicy) , aby pobrać kopię zasad usługi Scheduler. Wartości zasad otrzymane od tych metod mogą się różnić od wartości zasad określonych podczas tworzenia harmonogramu.

## <a name="example"></a>Przykład

Aby zapoznać się z przykładami korzystającymi z określonych zasad usługi Scheduler w celu kontrolowania zachowania [harmonogramu, zobacz How to: Określ określone zasady](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md) harmonogramu i [instrukcje: Utwórz agentów, którzy korzystają z określonych](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)zasad usługi Scheduler.

## <a name="see-also"></a>Zobacz także

[Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Instrukcje: określanie specjalnych zasad harmonogramu](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br/>
[Instrukcje: tworzenie agentów korzystających ze specjalnych zasad harmonogramu](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)
