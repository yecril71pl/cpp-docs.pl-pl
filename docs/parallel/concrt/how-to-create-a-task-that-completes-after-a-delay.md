---
title: 'Porady: tworzenie zadania kończonego po opóźnieniu'
ms.date: 11/04/2016
helpviewer_keywords:
- task_completion_event class, example
- create a task that completes after a delay, example [C++]
ms.assetid: 3fc0a194-3fdb-4eba-8b8a-b890981a985d
ms.openlocfilehash: 76189f45eb486e06b040155f6697bf003659b474
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141745"
---
# <a name="how-to-create-a-task-that-completes-after-a-delay"></a>Porady: tworzenie zadania kończonego po opóźnieniu

W tym przykładzie pokazano, jak użyć metody [concurrency:: Task](../../parallel/concrt/reference/task-class.md), [concurrency:: cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md), [concurrency:: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md), [concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), [concurrency:: Timer](../../parallel/concrt/reference/timer-class.md)i [concurrency:: Call](../../parallel/concrt/reference/call-class.md) Classes, aby utworzyć zadanie, które kończy się po opóźnieniu. Za pomocą tej metody można kompilować pętle, które okazjonalnie sprawdzają dane, wprowadzają limity czasu, opóźniać obsługę danych wejściowych użytkownika przez określony czas i tak dalej.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono funkcje `complete_after` i `cancel_after_timeout`. Funkcja `complete_after` tworzy obiekt `task`, który kończy się po określonym opóźnieniu. Używa obiektu `timer` i obiektu `call` do ustawiania obiektu `task_completion_event` po określonym opóźnieniu. Korzystając z klasy `task_completion_event`, można zdefiniować zadanie, które kończy się po wątku lub inne zadanie sygnalizuje, że wartość jest dostępna. Po ustawieniu zdarzenia zadania odbiornika są wykonywane, a ich kontynuacje są zaplanowane do uruchomienia.

> [!TIP]
> Aby uzyskać więcej informacji na temat klas `timer` i `call`, które są częścią biblioteki agentów asynchronicznych, zobacz [asynchroniczne bloki komunikatów](../../parallel/concrt/asynchronous-message-blocks.md).

Funkcja `cancel_after_timeout` kompiluje w funkcji `complete_after`, aby anulować zadanie, jeśli to zadanie nie zostanie zakończone przed upływem danego limitu czasu. Funkcja `cancel_after_timeout` tworzy dwa zadania. Pierwsze zadanie wskazuje na powodzenie i zakończenie po zakończeniu podanego zadania; Drugie zadanie wskazuje błąd i kończy się po określonym limicie czasu. Funkcja `cancel_after_timeout` tworzy zadanie kontynuacji, które jest uruchamiane po zakończeniu zadania sukcesu lub niepowodzenia. Jeśli zadanie niepowodzenia zakończy się najpierw, kontynuacja spowoduje anulowanie źródła tokenu w celu anulowania zadania ogólnego.

[!code-cpp[concrt-task-delay#1](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_1.cpp)]

## <a name="example"></a>Przykład

Poniższy przykład oblicza liczbę liczb pierwszych z zakresu [0, 100000] wiele razy. Operacja kończy się niepowodzeniem, jeśli nie została ukończona w określonym limicie czasu. Funkcja `count_primes` pokazuje, jak używać funkcji `cancel_after_timeout`. Zlicza on liczbę elementów w podanym zakresie i kończy się niepowodzeniem, jeśli zadanie nie zostało ukończone w danym czasie. Funkcja `wmain` wywołuje funkcję `count_primes` wiele razy. Za każdym razem ilość czasu jest mniejsza. Program kończy działanie, gdy operacja nie zostanie zakończona w bieżącym limicie czasu.

[!code-cpp[concrt-task-delay#2](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_2.cpp)]

Gdy ta technika jest używana do anulowania zadań po opóźnieniu, wszystkie zadania, które nie zostały uruchomione, nie zostaną uruchomione po anulowaniu całego zadania. Jednak ważne jest, aby każde długotrwałe zadania odpowiadały na anulowanie w odpowiednim czasie. Aby uzyskać więcej informacji o anulowaniu zadania, zobacz [Anulowanie w PPL](cancellation-in-the-ppl.md).

## <a name="example"></a>Przykład

Oto kompletny kod dla tego przykładu:

[!code-cpp[concrt-task-delay#3](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_3.cpp)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować kod, skopiuj go, a następnie wklej w projekcie programu Visual Studio lub wklej go w pliku o nazwie `task-delay.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**CL. exe/EHsc Task-Delay. cpp**

## <a name="see-also"></a>Zobacz też

[Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[task, klasa (środowisko uruchomieniowe współbieżności)](../../parallel/concrt/reference/task-class.md)<br/>
[cancellation_token_source, klasa](../../parallel/concrt/reference/cancellation-token-source-class.md)<br/>
[cancellation_token, klasa](../../parallel/concrt/reference/cancellation-token-class.md)<br/>
[task_completion_event, klasa](../../parallel/concrt/reference/task-completion-event-class.md)<br/>
[timer, klasa](../../parallel/concrt/reference/timer-class.md)<br/>
[call, klasa](../../parallel/concrt/reference/call-class.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Anulowanie w PPL](cancellation-in-the-ppl.md)
