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
ms.openlocfilehash: d602f83cfe2da6bc1506e07720d3ef021ebce04a
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687416"
---
# <a name="lightweight-tasks"></a>Zadania lekkie
Ten dokument zawiera opis roli zadań lekkich współbieżność środowiska wykonawczego. A *zadań lekkich* to zadanie, które można planować bezpośrednio z `concurrency::Scheduler` lub `concurrency::ScheduleGroup` obiektu. Zadania lekkie podobny funkcji, które świadczą interfejsu API systemu Windows [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) funkcji. W związku z tym potrzeb zadań lekkich są przydatne, gdy dostosowania istniejącego kodu do korzystania z funkcji planowania programu współbieżności środowiska wykonawczego. Współbieżność środowiska wykonawczego sam używa zadań lekkich zaplanować agentów asynchronicznych i wysyłanie komunikatów między bloki komunikatów asynchronicznych.  
  
> [!TIP]
>  Współbieżność środowiska wykonawczego zapewnia harmonogram domyślny, i dlatego nie trzeba utworzyć w aplikacji. Harmonogram zadań ułatwia dostrojenie wydajności aplikacji, dlatego zaleca się uruchamiania z [równoległych biblioteki wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md) lub [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) w przypadku jesteś nowym użytkownikiem współbieżności środowiska wykonawczego.  
  
 Zadania lekkie przenosić mniejsze koszty niż agentów asynchronicznych i grupy zadań. Na przykład środowisko uruchomieniowe nie informują po zakończeniu zadania lekkie. Ponadto środowisko uruchomieniowe catch lub nie obsługi wyjątków, które są generowane z lekkie zadania. Aby uzyskać więcej informacji na temat obsługi wyjątków i zadania lekkie zobacz [obsługi wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
 W przypadku większości zadań zaleca się, użyj bardziej niezawodne funkcje, takie jak grupy zadań i algorytmy równoległe, ponieważ umożliwiają one łatwiej Podziel złożone zadania na bardziej z nich. Aby uzyskać więcej informacji na temat grupy zadań, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Aby uzyskać więcej informacji na temat algorytmy równoległe, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).  
  
 Aby utworzyć zadanie lekkie, należy wywołać [concurrency::ScheduleGroup::ScheduleTask](reference/schedulegroup-class.md#scheduletask), [concurrency::CurrentScheduler::ScheduleTask](reference/currentscheduler-class.md#scheduletask), lub [concurrency::Scheduler::ScheduleTask ](reference/scheduler-class.md#scheduletask) metody. Oczekiwanie na zakończenie zadania lekkie, poczekaj, aż harmonogramu nadrzędnego zamknięcia lub korzysta z mechanizmu synchronizacji, takie jak [concurrency::event](../../parallel/concrt/reference/event-class.md) obiektu.  
  
## <a name="example"></a>Przykład  
 Na przykład, który demonstruje sposób dostosowania istniejącego kodu do lekkie zadań, zobacz [wskazówki: adaptacja istniejącego kodu do potrzeb zadań lekkich użyj](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Przewodnik: adaptacja istniejącego kodu do potrzeb zadań lekkich](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)

