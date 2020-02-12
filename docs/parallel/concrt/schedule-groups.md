---
title: Grupy harmonogramu
ms.date: 11/04/2016
helpviewer_keywords:
- schedule groups
ms.assetid: 03523572-5891-4d17-89ce-fa795605f28b
ms.openlocfilehash: 1765c10f4cf8fe499aed1a140d2bba1ecaaf2300
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142311"
---
# <a name="schedule-groups"></a>Grupy harmonogramu

W tym dokumencie opisano role grup harmonogramu w środowisko uruchomieniowe współbieżności. *Grupy harmonogramu* skoligaconyą lub grupowo powiązane zadania. Każdy harmonogram ma co najmniej jedną grupę harmonogramów. Używaj grup zaplanowanych, gdy wymagasz wysokiego stopnia zawieszania między zadaniami, na przykład gdy grupa powiązanych zadań korzysta z wykonywania w tym samym węźle procesora. Należy również użyć wystąpień usługi Scheduler, gdy aplikacja ma określone wymagania dotyczące jakości, na przykład, gdy chcesz ograniczyć ilość zasobów przetwarzania przyznanych do zestawu zadań. Aby uzyskać więcej informacji o wystąpieniach harmonogramu, zobacz [wystąpienia usługi Scheduler](../../parallel/concrt/scheduler-instances.md).

> [!TIP]
> Środowisko uruchomieniowe współbieżności udostępnia domyślny harmonogram i dlatego nie jest konieczne tworzenie go w aplikacji. Ponieważ Harmonogram zadań ułatwia dostosowanie wydajności aplikacji, zalecamy rozpoczęcie od [biblioteki równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) lub [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) , jeśli są one nowe dla środowisko uruchomieniowe współbieżności.

Każdy obiekt `Scheduler` ma domyślną grupę harmonogramów dla każdego węzła planowania. *Węzeł planowania* jest mapowany do podstawowej topologii systemu. Środowisko uruchomieniowe tworzy jeden węzeł planowania dla każdego pakietu procesora lub węzła non-uniform Memory Architecture (NUMA), niezależnie od liczby. Jeśli zadanie nie zostanie jawnie skojarzone z grupą harmonogramów, harmonogram wybierze grupę, do której ma zostać dodane zadanie.

Zasady usługi `SchedulingProtocol` Scheduler wpływają na kolejność wykonywania zadań w ramach poszczególnych grup harmonogramu przez harmonogram. Gdy `SchedulingProtocol` jest ustawiona na `EnhanceScheduleGroupLocality` (co jest ustawieniem domyślnym), Harmonogram zadań wybiera następne zadanie z grupy harmonogramów, nad którym pracuje, gdy bieżące zadanie zakończy się lub w spółdzielnie. Harmonogram zadań przeszukuje bieżącą grupę harmonogramów pracy przed przejściem do następnej dostępnej grupy. Z drugiej strony, gdy `SchedulingProtocol` jest ustawiona na `EnhanceForwardProgress`, harmonogram przechodzi do następnej grupy harmonogramów po zakończeniu każdego zadania lub jego uzyskaniu. Aby zapoznać się z przykładem porównującym te zasady, zobacz [jak: używanie grup harmonogramu do wywierania wpływu na kolejność wykonywania](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

Środowisko uruchomieniowe używa klasy [concurrency:: Schedule](../../parallel/concrt/reference/schedulegroup-class.md) Group do reprezentowania grup harmonogramów. Aby utworzyć obiekt `ScheduleGroup`, wywołaj metodę [concurrency:: CurrentScheduler:: SetSchedule](reference/currentscheduler-class.md#createschedulegroup) lub [concurrency:: Scheduler::](reference/scheduler-class.md#createschedulegroup) . Środowisko uruchomieniowe używa mechanizmu zliczania odwołań do kontrolowania okresu istnienia `ScheduleGroup` obiektów, podobnie jak w przypadku obiektów `Scheduler`. Podczas tworzenia obiektu `ScheduleGroup` środowisko uruchomieniowe ustawia licznik odwołania na jeden. Metoda [concurrency:: Schedule](reference/schedulegroup-class.md#reference) ;: Reference zwiększa licznik odwołań o jeden. [Concurrency:: scheduleing:: Release](reference/schedulegroup-class.md#release) Metoda zmniejsza licznik odwołań o jeden.

Wiele typów w środowisko uruchomieniowe współbieżności umożliwia skojarzenie obiektu z grupą harmonogramów. Na przykład Klasa [concurrency:: Agent](../../parallel/concrt/reference/agent-class.md) i blok komunikatów, takie jak [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md), [concurrency:: join](../../parallel/concrt/reference/join-class.md)i concurrency::[Timer](reference/timer-class.md), zapewniają przeciążone wersje konstruktora, które pobierają `ScheduleGroup` obiektu. Środowisko uruchomieniowe używa obiektu `Scheduler`, który jest skojarzony z tym obiektem `ScheduleGroup` w celu zaplanowania zadania.

Można również użyć metody [concurrency:: Schedule:: ScheduleTask —](reference/schedulegroup-class.md#scheduletask) , aby zaplanować lekkie zadanie. Aby uzyskać więcej informacji na temat uproszczonych zadań, zobacz [zadania uproszczone](../../parallel/concrt/lightweight-tasks.md).

## <a name="example"></a>Przykład

Aby zapoznać się z przykładem korzystającym z grup harmonogramu do kontrolowania kolejności wykonywania zadań, zobacz [How to: use Groups Schedule by mieć wpływ na kolejność wykonywania](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

## <a name="see-also"></a>Zobacz też

[Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Wystąpienia harmonogramu](../../parallel/concrt/scheduler-instances.md)<br/>
[Instrukcje: używanie grup harmonogramu do wywierania wpływu na kolejność wykonywania](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)
