---
title: Grupy harmonogramu
ms.date: 11/04/2016
helpviewer_keywords:
- schedule groups
ms.assetid: 03523572-5891-4d17-89ce-fa795605f28b
ms.openlocfilehash: febcc0a9c7af75801962ea6be687ce87cc5501d4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295980"
---
# <a name="schedule-groups"></a>Grupy harmonogramu

W tym dokumencie opisano rolę grupy harmonogramu, w środowisku uruchomieniowym współbieżności. A *grupa harmonogramu* affinitizes lub grupowanie, informacje o zadaniach pokrewnych. Każdy harmonogram ma co najmniej jedną grupę harmonogramu. Użyj grupy harmonogramu, gdy na przykład wymagają wysokiego stopnia miejscowość spośród zadań, gdy grupa powiązanych zadań korzystają z wykonywane w tym samym węźle procesora. Z drugiej strony Użyj wystąpienia harmonogramu w przypadku aplikacji szczególne wymagania jakościowe, na przykład, jeśli chcesz ograniczyć ilość zasobów przetwarzania, które są przydzielane do zestawu zadań. Aby uzyskać więcej informacji na temat wystąpienia harmonogramu, zobacz [wystąpienia harmonogramu](../../parallel/concrt/scheduler-instances.md).

> [!TIP]
>  Środowisko uruchomieniowe współbieżności zawiera domyślnego harmonogramu, a w związku z tym nie należy utworzyć w aplikacji. Ponieważ Harmonogram zadań ułatwia dostrajania wydajności aplikacji, zalecamy rozpoczęcie od [biblioteki wzorców równoległych (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) lub [bibliotekę asynchronicznych agentów](../../parallel/concrt/asynchronous-agents-library.md) przypadku jesteś nowym użytkownikiem w czasie wykonywania współbieżności.

Każdy `Scheduler` obiekt ma domyślna grupa harmonogramu dla każdego węzła planowania. A *planowania węzła* mapuje źródłową topologię systemu. Środowisko uruchomieniowe tworzy jeden węzeł planowania dla każdego pakietu procesora lub Non-Uniform architektura pamięci (NUMA), niezależnie od liczba jest większa. Jeśli zadanie nie jawnie skojarzona z grupą harmonogramu, harmonogram wybiera grupę, do której można dodać zadania.

`SchedulingProtocol` Zasadę harmonogramu wpływa na kolejność, w którym harmonogramu służy do wykonywania zadań w każdej grupie harmonogramu. Gdy `SchedulingProtocol` ustawiono `EnhanceScheduleGroupLocality` (co jest ustawieniem domyślnym), harmonogram zadań wybiera następnego zadania z grupy harmonogramu, który działa na bieżące zadanie zakończy się lub daje wspólne. Harmonogram zadań wyszukuje bieżącą grupę harmonogram pracy przed przenosi do następnej grupy dostępności. Z drugiej strony, gdy `SchedulingProtocol` ustawiono `EnhanceForwardProgress`, harmonogram przechodzi do następnej grupy harmonogramu, po zakończeniu każdego zadania, lub daje. Na przykład, który porównuje tych zasad, zobacz [jak: Używanie grup harmonogramu do wywierania wpływu na kolejność wykonywania](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

Środowisko wykonawcze używa [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) klasy do reprezentowania grup harmonogramu. Aby utworzyć `ScheduleGroup` obiektu, wywołaj [concurrency::CurrentScheduler::CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup) lub [concurrency::Scheduler::CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup) metody. Środowisko wykonawcze używa mechanizmu zliczanie odwołań, aby kontrolować okres istnienia `ScheduleGroup` obiektów, podobnie jak w przypadku `Scheduler` obiektów. Po utworzeniu `ScheduleGroup` obiektu, środowisko uruchomieniowe ustawia licznik do jednego odwołania. [Concurrency::ScheduleGroup::Reference](reference/schedulegroup-class.md#reference) metody zwiększa licznik odwołań za pomocą jednej. [Concurrency::ScheduleGroup::Release](reference/schedulegroup-class.md#release) metoda zmniejsza licznika odwołań za pomocą jednej.

Wiele typów w środowisku uruchomieniowym współbieżności: umożliwiają skojarzenie obiektu wraz z grupy harmonogramów. Na przykład [concurrency::agent](../../parallel/concrt/reference/agent-class.md) bloku klasy i komunikat klasy, takie jak [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md), [concurrency::join](../../parallel/concrt/reference/join-class.md)i współbieżnością::[ czasomierz](reference/timer-class.md), podać przeciążone wersje konstruktora, które przyjmują `ScheduleGroup` obiektu. Środowisko wykonawcze używa `Scheduler` obiektu, który jest skojarzony z tym `ScheduleGroup` obiektu do zaplanowania zadania.

Można również użyć [concurrency::ScheduleGroup::ScheduleTask](reference/schedulegroup-class.md#scheduletask) metodę, aby zaplanować zadanie, uproszczone. Aby uzyskać więcej informacji na temat zadań lekkich zobacz [zadań lekkich](../../parallel/concrt/lightweight-tasks.md).

## <a name="example"></a>Przykład

Aby uzyskać przykład, że używa Zaplanuj grupy, aby kontrolować kolejność wykonywania zadań, zobacz [jak: Używanie grup harmonogramu do wywierania wpływu na kolejność wykonywania](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

## <a name="see-also"></a>Zobacz także

[Task Scheduler](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Wystąpienia harmonogramu](../../parallel/concrt/scheduler-instances.md)<br/>
[Instrukcje: używanie grup harmonogramu do wywierania wpływu na kolejność wykonywania](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)
