---
title: Zasady harmonogramu
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
ms.openlocfilehash: 0f90b461ecba702501c2f6919572dc828c80907f
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142279"
---
# <a name="scheduler-policies"></a>Zasady harmonogramu

W tym dokumencie opisano role zasad usługi Scheduler w środowisko uruchomieniowe współbieżności. *Zasady harmonogramu* kontrolują strategię używaną przez harmonogram podczas zarządzania zadaniami. Rozważmy na przykład aplikację, która wymaga wykonania pewnych zadań w `THREAD_PRIORITY_NORMAL` i innych zadań do wykonania w `THREAD_PRIORITY_HIGHEST`.  Można utworzyć dwa wystąpienia harmonogramu: takie, które określa zasady `ContextPriority`, które mają być `THREAD_PRIORITY_NORMAL` i inne, które określają te same zasady, które mają być `THREAD_PRIORITY_HIGHEST`.

Korzystając z zasad usługi Scheduler, można podzielić dostępne zasoby przetwarzania i przypisać do każdego harmonogramu stały zestaw zasobów. Rozważmy na przykład algorytm równoległy, który nie jest skalowany poza czterema procesorami. Można utworzyć zasady harmonogramu, które ograniczają swoje zadania do korzystania z nie więcej niż czterech procesorów jednocześnie.

> [!TIP]
> Środowisko uruchomieniowe współbieżności udostępnia domyślny harmonogram. W związku z tym nie trzeba go tworzyć w aplikacji. Ponieważ Harmonogram zadań ułatwia dostosowanie wydajności aplikacji, zalecamy rozpoczęcie od [biblioteki równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) lub [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) , jeśli są one nowe dla środowisko uruchomieniowe współbieżności.

W przypadku korzystania z metody [concurrency:: CurrentScheduler:: Create](reference/currentscheduler-class.md#create), [concurrency:: Scheduler:: Create](reference/scheduler-class.md#create)lub [concurrency:: Scheduler:: SetDefaultSchedulerPolicy —](reference/scheduler-class.md#setdefaultschedulerpolicy) w celu utworzenia wystąpienia harmonogramu należy podać obiekt [concurrency:: SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) , który zawiera kolekcję par klucz-wartość, które określają zachowanie harmonogramu. Konstruktor `SchedulerPolicy` przyjmuje zmienną liczbę argumentów. Pierwszy argument to liczba elementów zasad, które można określić. Pozostałe argumenty to pary klucz-wartość dla każdego elementu zasad. Poniższy przykład tworzy obiekt `SchedulerPolicy`, który określa trzy elementy zasad. Środowisko uruchomieniowe używa wartości domyślnych dla kluczy zasad, które nie są określone.

[!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/cpp/scheduler-policies_1.cpp)]

[Olicyelementkey "concurrency::P](reference/concurrency-namespace-enums.md#policyelementkey) Enumeration definiuje klucze zasad, które są skojarzone z harmonogram zadań. Poniższa tabela zawiera opis kluczy zasad i wartości domyślnej używanej przez środowisko uruchomieniowe dla każdego z nich.

|Klucz zasad|Opis|Wartość domyślna|
|----------------|-----------------|-------------------|
|`SchedulerKind`|[Concurrency:: SchedulerType](reference/concurrency-namespace-enums.md#schedulertype) wartość określająca typ wątków do użycia w celu planowania zadań.|`ThreadScheduler` (Użyj zwykłych wątków). Jest to jedyna prawidłowa wartość dla tego klucza.|
|`MaxConcurrency`|Wartość `unsigned int`, która określa maksymalną liczbę zasobów współbieżności używanych przez harmonogram.|[concurrency:: MaxExecutionResources —](reference/concurrency-namespace-constants1.md#maxexecutionresources)|
|`MinConcurrency`|Wartość `unsigned int`, która określa minimalną liczbę zasobów współbieżności używanych przez harmonogram.|`1`|
|`TargetOversubscriptionFactor`|Wartość `unsigned int`, która określa liczbę wątków do przydzielenia do każdego zasobu przetwarzania.|`1`|
|`LocalContextCacheSize`|Wartość `unsigned int`, która określa maksymalną liczbę kontekstów, które mogą być buforowane w lokalnej kolejce każdego procesora wirtualnego.|`8`|
|`ContextStackSize`|Wartość `unsigned int`, która określa rozmiar stosu w kilobajtach, do zarezerwowania dla każdego kontekstu.|`0` (Użyj domyślnego rozmiaru stosu)|
|`ContextPriority`|Wartość `int`, która określa priorytet wątku dla każdego kontekstu. Może to być dowolna wartość, którą można przekazać do [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) lub `INHERIT_THREAD_PRIORITY`.|`THREAD_PRIORITY_NORMAL`|

|`SchedulingProtocol`| [Concurrency:: SchedulingProtocolType —](reference/concurrency-namespace-enums.md#schedulingprotocoltype) wartość określająca algorytm planowania do użycia. |`EnhanceScheduleGroupLocality`| |`DynamicProgressFeedback`| [Współbieżność::D ynamicprogressfeedbacktype](reference/concurrency-namespace-enums.md#dynamicprogressfeedbacktype) wartość określająca, czy należy zrównoważyć zasoby zgodnie z informacjami o postępie opartym na statystyce.<br /><br /> **Uwaga** Nie ustawiaj tych zasad na `ProgressFeedbackDisabled`, ponieważ są zarezerwowane do użytku przez środowisko uruchomieniowe. |`ProgressFeedbackEnabled`|

Każdy harmonogram używa własnych zasad podczas planowania zadań. Zasady skojarzone z jednym harmonogramem nie wpływają na zachowanie innych harmonogramów. Ponadto nie można zmienić zasad harmonogramu po utworzeniu obiektu `Scheduler`.

> [!IMPORTANT]
> Używaj tylko zasad usługi Scheduler, aby kontrolować atrybuty dla wątków tworzonych przez środowisko uruchomieniowe. Nie należy zmieniać koligacji wątku ani priorytetów wątków tworzonych przez środowisko uruchomieniowe, ponieważ może to spowodować niezdefiniowane zachowanie.

Środowisko uruchomieniowe tworzy domyślnego harmonogramu, jeśli nie zostanie on jawnie utworzony. Jeśli chcesz użyć domyślnego harmonogramu w aplikacji, ale chcesz określić zasady dla tego harmonogramu do użycia, wywołaj metodę [concurrency:: Scheduler:: SetDefaultSchedulerPolicy —](reference/scheduler-class.md#setdefaultschedulerpolicy) przed zaplanowaniem pracy równoległej. Jeśli nie wywołasz metody `Scheduler::SetDefaultSchedulerPolicy`, środowisko uruchomieniowe użyje domyślnych wartości zasad z tabeli.

Użyj metody [concurrency:: CurrentScheduler:: GetPolicy](reference/currentscheduler-class.md#getpolicy) i [concurrency:: Scheduler:: GetPolicy](reference/scheduler-class.md#getpolicy) , aby pobrać kopię zasad usługi Scheduler. Wartości zasad otrzymane od tych metod mogą się różnić od wartości zasad określonych podczas tworzenia harmonogramu.

## <a name="example"></a>Przykład

Aby zapoznać się z przykładami korzystającymi z określonych zasad usługi Scheduler w celu kontrolowania zachowania harmonogramu, zobacz [How to: Określanie określonych zasad harmonogramu](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md) i [instrukcje: Tworzenie agentów](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)korzystających z określonych zasad usługi Scheduler.

## <a name="see-also"></a>Zobacz też

[Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Instrukcje: określanie specjalnych zasad harmonogramu](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br/>
[Instrukcje: tworzenie agentów korzystających ze specjalnych zasad harmonogramu](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)
