---
title: Zadania lekkie
ms.date: 11/04/2016
helpviewer_keywords:
- lightweight tasks
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
ms.openlocfilehash: be417052ffab19c1bc2d2ba6f35094f98e315812
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141851"
---
# <a name="lightweight-tasks"></a>Zadania lekkie

W tym dokumencie opisano rolę uproszczonych zadań w środowisko uruchomieniowe współbieżności. *Uproszczone zadanie* to zadanie, które można zaplanować bezpośrednio z obiektu `concurrency::Scheduler` lub `concurrency::ScheduleGroup`. Uproszczone zadanie jest podobne do funkcji dostarczanej do funkcji [wielowątkowości](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) interfejsu API systemu Windows. W związku z tym lekkie zadania są przydatne podczas dostosowywania istniejącego kodu do korzystania z funkcji planowania środowisko uruchomieniowe współbieżności. Środowisko uruchomieniowe współbieżności sam używa uproszczonych zadań do zaplanowania agentów asynchronicznych i wysyłania komunikatów między blokami komunikatów asynchronicznych.

> [!TIP]
> Środowisko uruchomieniowe współbieżności udostępnia domyślny harmonogram i dlatego nie jest konieczne tworzenie go w aplikacji. Ponieważ Harmonogram zadań ułatwia dostosowanie wydajności aplikacji, zalecamy rozpoczęcie od [biblioteki równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) lub [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) , jeśli są one nowe dla środowisko uruchomieniowe współbieżności.

Lekkie zadania zajmują mniej obciążenia niż agentów asynchronicznych i grup zadań. Na przykład środowisko uruchomieniowe nie informuje użytkownika o zakończeniu lekkiego zadania. Ponadto środowisko uruchomieniowe nie przechwytuje ani nie obsługuje wyjątków, które są generowane przez lekkie zadanie. Aby uzyskać więcej informacji na temat obsługi wyjątków i uproszczonych zadań, zobacz [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

W przypadku większości zadań zalecamy korzystanie z bardziej niezawodnych funkcji, takich jak grupy zadań i algorytmy równoległe, ponieważ umożliwiają one łatwiejsze przerywanie złożonych zadań do bardziej podstawowych. Aby uzyskać więcej informacji na temat grup zadań, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Aby uzyskać więcej informacji na temat algorytmów równoległych, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

Aby utworzyć lekkie zadanie, wywołaj metodę [concurrency:: Schedule:: ScheduleTask —](reference/schedulegroup-class.md#scheduletask), [concurrency:: CurrentScheduler:: ScheduleTask —](reference/currentscheduler-class.md#scheduletask)lub [concurrency:: Scheduler](reference/scheduler-class.md#scheduletask) :: ScheduleTask —. Aby poczekać na zakończenie lekkiego zadania, poczekaj na zamknięcie nadrzędnego harmonogramu lub Użyj mechanizmu synchronizacji, takiego jak obiekt [concurrency:: Event](../../parallel/concrt/reference/event-class.md) .

## <a name="example"></a>Przykład

Aby zapoznać się z przykładem, który pokazuje, jak dostosować istniejący kod do korzystania z uproszczonego zadania, zobacz [Przewodnik: Dostosowywanie istniejącego kodu do korzystania z uproszczonych zadań](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md).

## <a name="see-also"></a>Zobacz też

[Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Przewodnik: adaptacja istniejącego kodu do potrzeb zadań lekkich](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)
