---
title: 'Porady: zarządzanie przypadkiem planisty'
ms.date: 11/04/2016
helpviewer_keywords:
- managing a scheduler instance [Concurrency Runtime]
- scheduler instances, managing [Concurrency Runtime]
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
ms.openlocfilehash: c7ec321eaf0960dc14b61bbd8fdc76b53a31f8c5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141724"
---
# <a name="how-to-manage-a-scheduler-instance"></a>Porady: zarządzanie przypadkiem planisty

Wystąpienia usługi Scheduler umożliwiają kojarzenie określonych zasad planowania z różnymi rodzajami obciążeń. Ten temat zawiera dwa podstawowe przykłady, które pokazują, jak utworzyć wystąpienie harmonogramu i zarządzać nim.

Przykłady tworzą harmonogramy korzystające z domyślnych zasad usługi Scheduler. Przykład tworzenia harmonogramu korzystającego z zasad niestandardowych można znaleźć w temacie [How to: Określanie określonych zasad usługi Scheduler](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).

## <a name="to-manage-a-scheduler-instance-in-your-application"></a>Aby zarządzać przypadkiem planisty w aplikacji

1. Utwórz obiekt [concurrency:: SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) , który zawiera wartości zasad dla harmonogramu do użycia.

1. Wywołaj metodę [concurrency:: CurrentScheduler:: Create](reference/currentscheduler-class.md#create) lub [concurrency:: Scheduler:: Create](reference/scheduler-class.md#create) , aby utworzyć wystąpienie usługi Scheduler.

   Jeśli używasz metody `Scheduler::Create`, wywołaj metodę [concurrency:: Scheduler:: Attach](reference/scheduler-class.md#attach) , gdy zachodzi potrzeba skojarzenia harmonogramu z bieżącym kontekstem.

1. Wywołaj funkcję [CreateEvent](/windows/win32/api/synchapi/nf-synchapi-createeventw) , aby utworzyć dojście do niesygnalizowanego obiektu zdarzenia autoresetowania.

1. Przekaż dojście do obiektu zdarzenia, który właśnie został utworzony, do metody [concurrency:: CurrentScheduler:: RegisterShutdownEvent —](reference/currentscheduler-class.md#registershutdownevent) lub [concurrency:: Scheduler:: RegisterShutdownEvent —](reference/scheduler-class.md#registershutdownevent) . Spowoduje to zarejestrowanie zdarzenia do ustawienia podczas zniszczenia harmonogramu.

1. Wykonaj zadania, które mają być zaplanowane przez bieżący harmonogram.

1. Wywołaj metodę [concurrency:: CurrentScheduler::D etach](reference/currentscheduler-class.md#detach) , aby odłączyć bieżący harmonogram i przywrócić poprzedni harmonogram jako bieżący.

   Jeśli używasz metody `Scheduler::Create`, wywołaj metodę [concurrency:: Scheduler:: Release](reference/scheduler-class.md#release) , aby zmniejszyć liczbę odwołań do obiektu `Scheduler`.

1. Przekaż dojście do zdarzenia do funkcji [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject) , aby zaczekać, aż harmonogram zostanie zamknięty.

1. Wywołaj funkcję [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) , aby zamknąć uchwyt do obiektu zdarzenia.

## <a name="example"></a>Przykład

Poniższy kod przedstawia dwa sposoby zarządzania wystąpieniem usługi Scheduler. Każdy przykład najpierw używa domyślnego harmonogramu do wykonywania zadania, które drukuje unikatowy identyfikator bieżącego harmonogramu. Każdy przykład używa wystąpienia harmonogramu do wykonania tego samego zadania ponownie. Na koniec każdy przykład przywraca domyślny harmonogram jako bieżący i wykonuje zadanie jeszcze raz.

Pierwszy przykład używa klasy [concurrency:: CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) do tworzenia wystąpienia harmonogramu i kojarzenia go z bieżącym kontekstem. Drugi przykład używa klasy [concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) , aby wykonać to samo zadanie. Zazwyczaj Klasa `CurrentScheduler` jest używana do pracy z bieżącym harmonogramem. Drugi przykład, który używa klasy `Scheduler`, jest przydatne, gdy chcesz kontrolować, kiedy harmonogram jest skojarzony z bieżącym kontekstem lub jeśli chcesz skojarzyć określone harmonogramy z określonymi zadaniami.

[!code-cpp[concrt-scheduler-instance#1](../../parallel/concrt/codesnippet/cpp/how-to-manage-a-scheduler-instance_1.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
Using CurrentScheduler class...

Current scheduler id: 0
Creating and attaching scheduler...
Current scheduler id: 1
Detaching scheduler...
Current scheduler id: 0

Using Scheduler class...

Current scheduler id: 0
Creating scheduler...
Attaching scheduler...
Current scheduler id: 2
Detaching scheduler...
Current scheduler id: 0
```

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `scheduler-instance.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **CL. exe/EHsc Scheduler-instance. cpp**

## <a name="see-also"></a>Zobacz też

[Wystąpienia harmonogramu](../../parallel/concrt/scheduler-instances.md)<br/>
[Instrukcje: określanie specjalnych zasad harmonogramu](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)
