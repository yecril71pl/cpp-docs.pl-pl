---
title: 'Porady: używanie grup harmonogramu do wywierania wpływu na kolejność wykonywania'
ms.date: 11/04/2016
helpviewer_keywords:
- schedule groups, using [Concurrency Runtime]
- using schedule groups [Concurrency Runtime]
ms.assetid: 73124194-fc3a-491e-a23f-fbd7b5a4455c
ms.openlocfilehash: 84829664603999893f32caab39af250059bf9788
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141915"
---
# <a name="how-to-use-schedule-groups-to-influence-order-of-execution"></a>Porady: używanie grup harmonogramu do wywierania wpływu na kolejność wykonywania

W środowisko uruchomieniowe współbieżności kolejność, w której zaplanowano zadania, jest niedeterministyczna. Można jednak użyć zasad planowania, aby mieć wpływ na kolejność uruchamiania zadań. W tym temacie pokazano, jak używać grup harmonogramu wraz z zasadami [concurrency:: SchedulingProtocol](reference/concurrency-namespace-enums.md#policyelementkey) Scheduler, aby mieć wpływ na kolejność uruchamiania zadań.

Przykład uruchamia zestaw zadań dwa razy, z których każdy ma inne zasady planowania. Obie zasady ograniczają maksymalną liczbę zasobów przetwarzania do dwóch. Pierwszy przebieg korzysta z zasad `EnhanceScheduleGroupLocality`, które są domyślne, a drugi przebieg korzysta z zasad `EnhanceForwardProgress`. Zgodnie z zasadami `EnhanceScheduleGroupLocality` Scheduler uruchamia wszystkie zadania w jednej grupie harmonogramu do momentu zakończenia każdego zadania lub jego uzyskania. Zgodnie z zasadami `EnhanceForwardProgress` harmonogram przechodzi do następnej grupy harmonogramów w sposób okrężny po zakończeniu lub uzyskaniu tylko jednego zadania.

Gdy każda grupa harmonogramów zawiera powiązane zadania, zasady `EnhanceScheduleGroupLocality` zwykle zwiększają wydajność, ponieważ jest zachowywana lokalna pamięć podręczna między zadaniami. Zasady `EnhanceForwardProgress` umożliwiają wykonywanie zadań do przodu i są przydatne, gdy wymagana jest sprawiedliwe planowanie w grupach harmonogramu.

## <a name="example"></a>Przykład

W tym przykładzie zdefiniowano klasę `work_yield_agent`, która pochodzi od [concurrency:: Agent](../../parallel/concrt/reference/agent-class.md). Klasa `work_yield_agent` wykonuje jednostkę pracy, daje bieżący kontekst, a następnie wykonuje kolejną jednostkę pracy. Agent używa funkcji [concurrency:: wait](reference/concurrency-namespace-functions.md#wait) do współdziałania z bieżącym kontekstem, dzięki czemu można uruchamiać inne konteksty.

Ten przykład tworzy cztery `work_yield_agent` obiektów. Aby zilustrować, jak ustawić zasady harmonogramu mające wpływ na kolejność, w jakiej działają agenci, przykład kojarzy pierwszych dwóch agentów z jedną grupą harmonogramu i innymi dwoma agentami z inną grupą harmonogramu. W przykładzie zastosowano metodę [concurrency:: CurrentScheduler:: SetSchedule](reference/currentscheduler-class.md#createschedulegroup) , aby utworzyć obiekty [concurrency:: Schedule](../../parallel/concrt/reference/schedulegroup-class.md) . W przykładzie jest uruchamiane wszystkich czterech agentów dwa razy, za każdym razem, gdy mają inne zasady planowania.

[!code-cpp[concrt-scheduling-protocol#1](../../parallel/concrt/codesnippet/cpp/how-to-use-schedule-groups-to-influence-order-of-execution_1.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
Using EnhanceScheduleGroupLocality...
group 0,
    task 0: first loop...
group 0,
    task 1: first loop...
group 0,
    task 0: waiting...
group 1,
    task 0: first loop...
group 0,
    task 1: waiting...
group 1,
    task 1: first loop...
group 1,
    task 0: waiting...
group 0,
    task 0: second loop...
group 1,
    task 1: waiting...
group 0,
    task 1: second loop...
group 0,
    task 0: finished...
group 1,
    task 0: second loop...
group 0,
    task 1: finished...
group 1,
    task 1: second loop...
group 1,
    task 0: finished...
group 1,
    task 1: finished...

Using EnhanceForwardProgress...
group 0,
    task 0: first loop...
group 1,
    task 0: first loop...
group 0,
    task 0: waiting...
group 0,
    task 1: first loop...
group 1,
    task 0: waiting...
group 1,
    task 1: first loop...
group 0,
    task 1: waiting...
group 0,
    task 0: second loop...
group 1,
    task 1: waiting...
group 1,
    task 0: second loop...
group 0,
    task 0: finished...
group 0,
    task 1: second loop...
group 1,
    task 0: finished...
group 1,
    task 1: second loop...
group 0,
    task 1: finished...
group 1,
    task 1: finished...
```

Obie zasady tworzą tę samą sekwencję zdarzeń. Jednak zasady, które używają `EnhanceScheduleGroupLocality` uruchamiają obu agentów, którzy są częścią pierwszej grupy harmonogramu przed uruchomieniem agentów, którzy są częścią drugiej grupy. Zasady używające `EnhanceForwardProgress` uruchamiają jednego agenta od pierwszej grupy, a następnie uruchamiają pierwszego agenta w drugiej grupie.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `scheduling-protocol.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **CL. exe/EHsc Scheduling-Protocol. cpp**

## <a name="see-also"></a>Zobacz też

[Grupy harmonogramu](../../parallel/concrt/schedule-groups.md)<br/>
[Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)
