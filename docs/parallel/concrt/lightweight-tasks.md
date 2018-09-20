---
title: Zadania lekkie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- lightweight tasks
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2d7624ce66513bd1447bc264e6c6cc29eab940c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409093"
---
# <a name="lightweight-tasks"></a>Zadania lekkie

W tym dokumencie opisano rolę zadania lekkie środowisko uruchomieniowe współbieżności. A *lekkie zadanie* jest zadaniem, która jest zaplanowania bezpośrednio z `concurrency::Scheduler` lub `concurrency::ScheduleGroup` obiektu. Lekkie zadanie jest podobne funkcja, która zapewnia interfejsu API Windows [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) funkcji. W związku z tym zadań lekkich są przydatne, gdy dostosowanie istniejącego kodu do planowania funkcji środowiska uruchomieniowego współbieżności. Samo środowisko uruchomieniowe współbieżności używa zadań lekkich planować agentów asynchronicznych i wysyłać wiadomości między bloki komunikatów asynchronicznych.

> [!TIP]
>  Środowisko uruchomieniowe współbieżności zawiera domyślnego harmonogramu, a w związku z tym nie należy utworzyć w aplikacji. Ponieważ Harmonogram zadań ułatwia dostrajania wydajności aplikacji, zalecamy rozpoczęcie od [biblioteki wzorców równoległych (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) lub [bibliotekę asynchronicznych agentów](../../parallel/concrt/asynchronous-agents-library.md) przypadku jesteś nowym użytkownikiem w czasie wykonywania współbieżności.

Zadania lekkie mają mniejsze obciążenie niż agentów asynchronicznych i grupy zadań. Na przykład środowisko wykonawcze nie informują po zakończeniu lekkie zadanie. Ponadto środowisko wykonawcze catch lub nie obsługiwać wyjątki, które są generowane przez lekkie zadanie. Aby uzyskać więcej informacji na temat obsługi wyjątków i zadań lekkich zobacz [wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

W przypadku większości zadań zaleca się, czy użyć bardziej niezawodne funkcje, takie jak grupy zadań i algorytmów równoległych, ponieważ umożliwiają one łatwiej przerwać złożonych zadań bardziej z nich. Aby uzyskać więcej informacji o grupach zadań, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Aby uzyskać więcej informacji dotyczących algorytmów równoległych, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

Aby utworzyć zadanie lekkie, wywołaj [concurrency::ScheduleGroup::ScheduleTask](reference/schedulegroup-class.md#scheduletask), [concurrency::CurrentScheduler::ScheduleTask](reference/currentscheduler-class.md#scheduletask), lub [concurrency::Scheduler::ScheduleTask ](reference/scheduler-class.md#scheduletask) metody. Oczekiwania na zakończenie zadania lekkie, poczekaj, aż harmonogram nadrzędnej, aby zamknąć lub używany był mechanizm synchronizacji, takie jak [concurrency::event](../../parallel/concrt/reference/event-class.md) obiektu.

## <a name="example"></a>Przykład

Na przykład, który demonstruje, jak dostosować istniejący kod do użycia lekkiego zadania, zobacz [Instruktaż: dostosowanie istniejącego kodu, aby użyć zadań lekkich](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md).

## <a name="see-also"></a>Zobacz też

[Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Przewodnik: adaptacja istniejącego kodu do potrzeb zadań lekkich](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)

