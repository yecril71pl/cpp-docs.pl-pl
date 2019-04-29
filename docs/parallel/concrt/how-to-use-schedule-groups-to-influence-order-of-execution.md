---
title: 'Instrukcje: Używanie grup harmonogramu do wywierania wpływu na kolejność wykonywania'
ms.date: 11/04/2016
helpviewer_keywords:
- schedule groups, using [Concurrency Runtime]
- using schedule groups [Concurrency Runtime]
ms.assetid: 73124194-fc3a-491e-a23f-fbd7b5a4455c
ms.openlocfilehash: 99e0383fc8d16f3eeb6e43e59424ab0984ee5c14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367047"
---
# <a name="how-to-use-schedule-groups-to-influence-order-of-execution"></a>Instrukcje: Używanie grup harmonogramu do wywierania wpływu na kolejność wykonywania

W środowisku uruchomieniowym współbieżności kolejność, w którym podzadania są planowane jest niedeterministyczny. Jednak można użyć zasad harmonogramu do wywierania wpływu na kolejność, w którym są uruchomione zadania. W tym temacie pokazano, jak używanie grup harmonogramu wraz z [concurrency::SchedulingProtocol](reference/concurrency-namespace-enums.md#policyelementkey) zasadę harmonogramu do wywierania wpływu na kolejność, w którym są uruchomione zadania.

W przykładzie uruchamiane są zestawu zadań dwa razy, każdy z różnych zasad planowania. Obie zasady ograniczać maksymalną liczbę zasobów do przetwarzania do dwóch. Pierwsze uruchomienie używa `EnhanceScheduleGroupLocality` zasady, co jest ustawieniem domyślnym, a druga Uruchom używa `EnhanceForwardProgress` zasad. W obszarze `EnhanceScheduleGroupLocality` zasad, harmonogram uruchamia wszystkie zadania w grupie jeden harmonogram do momentu każde zadanie zakończy się lub daje. W obszarze `EnhanceForwardProgress` zasady harmonogramu po przenosi do następnej grupy harmonogramu w sposób okrężny tylko jedno zadanie zakończy się lub daje.

Gdy każda grupa harmonogramu zawiera informacje o zadaniach pokrewnych, `EnhanceScheduleGroupLocality` zazwyczaj w wyniku zasad lepszą wydajność, ponieważ lokalizacja pamięci podręcznej jest zachowywana między zadaniami. `EnhanceForwardProgress` Zasad umożliwia zadań w celu wprowadzenia postęp i jest przydatne, gdy potrzebujesz planowania sprawiedliwe między grupami harmonogramu.

## <a name="example"></a>Przykład

Ten przykład definiuje `work_yield_agent` klasy, która jest pochodną [concurrency::agent](../../parallel/concrt/reference/agent-class.md). `work_yield_agent` Klasy wykonuje jednostka pracy, daje bieżącego kontekstu, a następnie inną jednostką pracy. Agent korzysta z [concurrency::wait](reference/concurrency-namespace-functions.md#wait) funkcja wspólne uzyskanie bieżącego kontekstu, aby uruchomić innych kontekstach.

Ten przykład tworzy cztery `work_yield_agent` obiektów. Aby zilustrować, jak ustawić zasady harmonogramu wpływa na kolejność uruchamiania agentów, przykład kojarzy pierwszych dwóch agentów z grupy jeden harmonogram i dwóch agentów z inną grupą harmonogramu. W przykładzie użyto [concurrency::CurrentScheduler::CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup) metodę w celu utworzenia [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) obiektów. W przykładzie uruchamiane są wszystkie cztery agentów dwa razy, za każdym razem, przy użyciu różnych zasad planowania.

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

Obie zasady utworzyć taką samą sekwencję zdarzeń. Jednak zasady używający `EnhanceScheduleGroupLocality` uruchamiania obu agentów, które są częścią pierwszej grupy harmonogramu, zanim zacznie agentów, które są częścią drugiej grupy. Zasady, które używa `EnhanceForwardProgress` jednego agenta jest uruchamiany z pierwszej grupy, a następnie uruchamia pierwszy agent w drugiej grupie.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `scheduling-protocol.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc planowania protocol.cpp**

## <a name="see-also"></a>Zobacz także

[Grupy harmonogramu](../../parallel/concrt/schedule-groups.md)<br/>
[Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)
