---
title: Zasady harmonogramu
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
ms.openlocfilehash: df045f7df9d0640b96ae1227c65c65aa7e432350
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668744"
---
# <a name="scheduler-policies"></a>Zasady harmonogramu

W tym dokumencie opisano rolę zasad harmonogramu w środowisku uruchomieniowym współbieżności. A *zasadę harmonogramu* kontroluje strategii, używany w harmonogramie podczas zarządzania zadaniami. Rozważmy na przykład aplikację, która wymaga niektórych zadań do wykonania w `THREAD_PRIORITY_NORMAL` i innych zadań do wykonania w `THREAD_PRIORITY_HIGHEST`.  Można utworzyć dwa wystąpienia harmonogramu: taki, który określa `ContextPriority` zasady `THREAD_PRIORITY_NORMAL` , a drugi określającą te same zasady jako `THREAD_PRIORITY_HIGHEST`.

Za pomocą zasad harmonogramu, można podzielić przetwarzania dostępnych zasobów i przypisać stały zestaw zasobów do każdej usługi scheduler. Na przykład należy wziąć pod uwagę algorytmu równoległego, który nie skalować poza cztery procesory. Można utworzyć zasadę harmonogram, który ogranicza jego zadań podrzędnych pod kątem równoległego użycia nie więcej niż cztery procesory.

> [!TIP]
>  Środowisko uruchomieniowe współbieżności zawiera domyślnego harmonogramu. W związku z tym nie trzeba utworzyć w aplikacji. Ponieważ Harmonogram zadań ułatwia dostrajania wydajności aplikacji, zalecamy rozpoczęcie od [biblioteki wzorców równoległych (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) lub [bibliotekę asynchronicznych agentów](../../parallel/concrt/asynchronous-agents-library.md) przypadku jesteś nowym użytkownikiem w czasie wykonywania współbieżności.

Kiedy używasz [concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create), [concurrency::Scheduler::Create](reference/scheduler-class.md#create), lub [concurrency::Scheduler::SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) metodę w celu utworzenia wystąpienia harmonogramu, należy podać [concurrency::SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) obiekt, który zawiera kolekcję par klucz wartość, które określają zachowanie harmonogramu. `SchedulerPolicy` Konstruktor przyjmuje zmienną liczbę argumentów. Pierwszy argument jest liczbą elementów zasad, które chcesz określić. Pozostałe argumenty są pary klucz wartość dla każdego elementu zasad. Poniższy przykład tworzy `SchedulerPolicy` obiektu, który określa trzy elementy zasad. Środowisko wykonawcze używa domyślnych wartości kluczy zasad, które nie zostały określone.

[!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/cpp/scheduler-policies_1.cpp)]

[Concurrency::PolicyElementKey](reference/concurrency-namespace-enums.md#policyelementkey) wyliczenie definiuje klucze zasad, które są skojarzone z harmonogramu zadań. W poniższej tabeli opisano klucze zasad i wartość domyślną, która na podstawie środowisko uruchomieniowe dla każdego z nich.

|Klucz zasad|Opis|Wartość domyślna|
|----------------|-----------------|-------------------|
|`SchedulerKind`|A [concurrency::SchedulerType](reference/concurrency-namespace-enums.md#schedulertype) wartość, która określa typ wątków używanych do planowania zadań.|`ThreadScheduler` (Użyj wątków normalny). Jest to jedyna prawidłowa wartość dla tego klucza.|
|`MaxConcurrency`|`unsigned int` Wartość, która określa maksymalną liczbę zasobów współbieżności, których używa usługi scheduler.|[CONCURRENCY::MaxExecutionResources](reference/concurrency-namespace-constants1.md#maxexecutionresources)|
|`MinConcurrency`|`unsigned int` Wartość, która określa minimalną liczbę zasobów współbieżności, których używa usługi scheduler.|`1`|
|`TargetOversubscriptionFactor`|`unsigned int` Wartość, która określa, jak wiele wątków można przydzielić do każdego zasobu przetwarzania.|`1`|
|`LocalContextCacheSize`|`unsigned int` Wartość, która określa maksymalną liczbę kontekstów, które mogą być buforowane w lokalnej kolejce każdy procesor wirtualny.|`8`|
|`ContextStackSize`|`unsigned int` Wartość określającą rozmiar stosu, w kilobajtach, aby zarezerwować dla każdego kontekstu.|`0` (Użyj domyślny rozmiar stosu)|
|`ContextPriority`|`int` Wartość, która określa priorytet wątku w każdym kontekście. Może to być dowolna wartość, którą można przekazać do [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) lub `INHERIT_THREAD_PRIORITY`.|`THREAD_PRIORITY_NORMAL`|

|`SchedulingProtocol`| A [concurrency::SchedulingProtocolType](reference/concurrency-namespace-enums.md#schedulingprotocoltype) wartość, która określa planowania algorytm ma być używany. | `EnhanceScheduleGroupLocality`| | `DynamicProgressFeedback`| A [concurrency::DynamicProgressFeedbackType](reference/concurrency-namespace-enums.md#dynamicprogressfeedbacktype) wartość, która określa, czy należy przeprowadzić ponowne równoważenie zasobów zgodnie z informacji o postępie na podstawie danych statystycznych.<br /><br /> **Uwaga** ta zasada nie jest ustawiona `ProgressFeedbackDisabled` , ponieważ jest on zarezerwowany do użytku przez środowisko uruchomieniowe. |`ProgressFeedbackEnabled`|

Każdy harmonogram używa własnych zasad, gdy planuje ona zadania. Zasady, które są skojarzone z jednego harmonogramu nie wpływają na działanie innych harmonogramu. Ponadto po utworzeniu nie można zmienić zasady harmonogramu `Scheduler` obiektu.

> [!IMPORTANT]
>  Do kontrolowania atrybutów dla wątków, które tworzy środowisko uruchomieniowe, należy użyć tylko zasad harmonogramu. Nie zmieniaj koligacji wątku lub priorytet wątki, które są tworzone w czasie wykonywania, ponieważ, może spowodować niezdefiniowane zachowanie.

Środowisko uruchomieniowe tworzy domyślnego harmonogramu dla Ciebie, jeśli nie zostanie jawnie utworzony jeden. Jeśli chcesz użyć domyślnego harmonogramu w aplikacji, ale chcesz określić zasady dla tego harmonogramu, do użycia, wywołaj [concurrency::Scheduler::SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) metoda przed zaplanować równoległą pracę. Jeśli nie zostanie wywołana `Scheduler::SetDefaultSchedulerPolicy` metody, używa środowiska uruchomieniowego zasady domyślne wartości z tabeli.

Użyj [concurrency::CurrentScheduler::GetPolicy](reference/currentscheduler-class.md#getpolicy) i [concurrency::Scheduler::GetPolicy](reference/scheduler-class.md#getpolicy) metody, aby pobrać kopię zasadę harmonogramu. Wartości zasad, które z tych metod może różnić się od wartości zasad, które można określić podczas tworzenia harmonogramu.

## <a name="example"></a>Przykład

Aby zbadać przykłady z zastosowaniem specjalnych zasad harmonogramu do sterowania zachowaniem harmonogramu, zobacz [jak: Określ konkretne zasady harmonogramu](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md) i [jak: tworzenie agentów tego używać określonych zasad harmonogramu](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).

## <a name="see-also"></a>Zobacz też

[Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Instrukcje: określanie specjalnych zasad harmonogramu](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br/>
[Instrukcje: tworzenie agentów korzystających ze specjalnych zasad harmonogramu](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)

