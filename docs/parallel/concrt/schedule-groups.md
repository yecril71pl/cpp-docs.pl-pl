---
title: Grupy harmonogramu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: schedule groups
ms.assetid: 03523572-5891-4d17-89ce-fa795605f28b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a61566878adc539af21e1645844eff27c5a8aec0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="schedule-groups"></a>Grupy harmonogramu
Ten dokument zawiera opis roli grup harmonogramu współbieżność środowiska wykonawczego. A *grupy harmonogram* sposób tworzą koligacje lub grup, zadań powiązanych ze sobą. Każdy harmonogram ma jedną lub więcej grup harmonogramu. Grupy harmonogramu Użyj, jeśli wymagane jest wysoki stopień miejscowości spośród zadań, na przykład, gdy grupa powiązanych zadań korzystać z wykonania na tym samym węźle procesora. Z drugiej strony należy użyć wystąpienia harmonogramu, po aplikacji jakości określone wymagania, na przykład, jeśli chcesz ograniczyć ilość zasobów przetwarzania, które są przydzielone do zestawu zadań. Aby uzyskać więcej informacji na temat wystąpień harmonogramu, zobacz [wystąpienia harmonogramu](../../parallel/concrt/scheduler-instances.md).  
  
> [!TIP]
>  Współbieżność środowiska wykonawczego zapewnia harmonogram domyślny, i dlatego nie trzeba utworzyć w aplikacji. Harmonogram zadań ułatwia dostrojenie wydajności aplikacji, dlatego zaleca się uruchamiania z [równoległych biblioteki wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md) lub [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) w przypadku jesteś nowym użytkownikiem współbieżności środowiska wykonawczego.  
  
 Każdy `Scheduler` obiekt ma domyślnej grupy harmonogramu dla każdego węzła planowania. A *planowania węzła* mapy źródłowej topologii systemu. Środowisko uruchomieniowe tworzy jeden węzeł planowania dla każdego pakietu procesora lub Non-Uniform architektura pamięci (NUMA), niezależnie od liczba jest większa. Jeśli zadanie nie jawnie skojarzona z grupą harmonogram, harmonogram wybiera grupę, aby dodać zadanie.  
  
 `SchedulingProtocol` Harmonogram zasad wpływa na kolejność, w którym planista wykonuje zadania w każdej grupie harmonogramu. Gdy `SchedulingProtocol` ma ustawioną wartość `EnhanceScheduleGroupLocality` (jest to wartość domyślna), harmonogram zadań wybiera następnego zadania z grupy harmonogram, który działa na bieżące zadanie zakończy lub wspólnie daje w wyniku. Harmonogram zadań wyszukuje bieżącą grupę harmonogram pracy przed przesyłane do następnej grupy dostępności. Z drugiej strony, gdy `SchedulingProtocol` ma ustawioną wartość `EnhanceForwardProgress`, planista przechodzi do następnej grupy harmonogramu po zakończeniu każdego zadania, lub daje w wyniku. Na przykład, który porównuje tych zasad, zobacz [porady: użycie grup harmonogramu do wpływ kolejność wykonywania](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).  
  

 Środowisko wykonawcze używa [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) klasy do reprezentowania grupy harmonogramu. Aby utworzyć `ScheduleGroup` obiekt, należy wywołać [concurrency::CurrentScheduler::CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup) lub [concurrency::Scheduler::CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup) metody. Środowisko uruchomieniowe używa mechanizmu liczenie odwołań w celu zarządzają okresem istnienia `ScheduleGroup` obiekty, podobnie jak w przypadku `Scheduler` obiektów. Po utworzeniu `ScheduleGroup` obiektu środowiska wykonawczego ustawia licznik do jednego odwołania. [Concurrency::ScheduleGroup::Reference](reference/schedulegroup-class.md#reference) metody zwiększa licznik odwołanie o jeden. [Concurrency::ScheduleGroup::Release](reference/schedulegroup-class.md#release) zmniejsza metody licznika odwołanie o jeden.  
  
 Wiele typów współbieżność środowiska wykonawczego pozwalają skojarzyć obiektu wraz z grupą harmonogramu. Na przykład [concurrency::agent](../../parallel/concrt/reference/agent-class.md) klasy i komunikat bloku klas takich jak [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md), [concurrency::join](../../parallel/concrt/reference/join-class.md)i współbieżność::[ czasomierz](reference/timer-class.md), podaj zastąpionej wersji konstruktora przyjmujących `ScheduleGroup` obiektu. Środowisko wykonawcze używa `Scheduler` obiekt, który jest skojarzony z tym `ScheduleGroup` obiektu do zaplanowania zadania.  
  
 Można również użyć [concurrency::ScheduleGroup::ScheduleTask](reference/schedulegroup-class.md#scheduletask) metodę, aby zaplanować zadanie lightweight. Aby uzyskać więcej informacji na temat zadań lekkich, zobacz [zadań lekkich](../../parallel/concrt/lightweight-tasks.md).  

  
## <a name="example"></a>Przykład  
 Na przykład, że używa Zaplanuj grupy, aby kontrolować kolejność wykonywania zadań, zobacz [porady: użycie grup harmonogramu do wpływ kolejność wykonywania](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Wystąpienia harmonogramu](../../parallel/concrt/scheduler-instances.md)   
 [Instrukcje: używanie grup harmonogramu do wywierania wpływu na kolejność wykonywania](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)

