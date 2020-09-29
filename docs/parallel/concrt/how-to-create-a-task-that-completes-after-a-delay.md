---
title: 'Porady: tworzenie zadania kończonego po opóźnieniu'
ms.date: 11/04/2016
helpviewer_keywords:
- task_completion_event class, example
- create a task that completes after a delay, example [C++]
ms.assetid: 3fc0a194-3fdb-4eba-8b8a-b890981a985d
ms.openlocfilehash: 80bfdeb7586f9c32592bc408a9de0c9188b77a29
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413791"
---
# <a name="how-to-create-a-task-that-completes-after-a-delay"></a>Porady: tworzenie zadania kończonego po opóźnieniu

W tym przykładzie pokazano, jak użyć metody [concurrency:: Task](../../parallel/concrt/reference/task-class.md), [concurrency:: cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md), [concurrency:: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md), [concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), [concurrency:: Timer](../../parallel/concrt/reference/timer-class.md)i [concurrency:: Call](../../parallel/concrt/reference/call-class.md) Classes, aby utworzyć zadanie, które kończy się po opóźnieniu. Za pomocą tej metody można kompilować pętle, które okazjonalnie sprawdzają dane, wprowadzają limity czasu, opóźniać obsługę danych wejściowych użytkownika przez określony czas i tak dalej.

## <a name="example-complete_after-and-cancel_after_timeout-functions"></a>Przykład: complete_after i funkcje cancel_after_timeout

W poniższym przykładzie przedstawiono `complete_after` funkcje i `cancel_after_timeout` . `complete_after`Funkcja tworzy `task` obiekt, który kończy się po określonym opóźnieniu. Używa `timer` obiektu i `call` obiektu do ustawienia `task_completion_event` obiektu po określonym opóźnieniu. Korzystając z `task_completion_event` klasy, można zdefiniować zadanie, które kończy się po wątku lub inne zadanie sygnalizuje, że wartość jest dostępna. Po ustawieniu zdarzenia zadania odbiornika są wykonywane, a ich kontynuacje są zaplanowane do uruchomienia.

> [!TIP]
> Aby uzyskać więcej informacji na `timer` temat `call` klas i, które są częścią biblioteki agentów asynchronicznych, zobacz [asynchroniczne bloki komunikatów](../../parallel/concrt/asynchronous-message-blocks.md).

`cancel_after_timeout`Funkcja kompiluje funkcję w `complete_after` celu anulowania zadania, jeśli zadanie nie zostanie zakończone przed upływem danego limitu czasu. `cancel_after_timeout`Funkcja tworzy dwa zadania. Pierwsze zadanie wskazuje na powodzenie i zakończenie po zakończeniu podanego zadania; Drugie zadanie wskazuje błąd i kończy się po określonym limicie czasu. `cancel_after_timeout`Funkcja tworzy zadanie kontynuacji, które jest uruchamiane po zakończeniu zadania sukces lub niepowodzenie. Jeśli zadanie niepowodzenia zakończy się najpierw, kontynuacja spowoduje anulowanie źródła tokenu w celu anulowania zadania ogólnego.

[!code-cpp[concrt-task-delay#1](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_1.cpp)]

## <a name="example-compute-count-of-prime-numbers"></a>Przykład: liczba obliczeń liczby pierwszych

Poniższy przykład oblicza liczbę liczb pierwszych z zakresu [0, 100000] wiele razy. Operacja kończy się niepowodzeniem, jeśli nie została ukończona w określonym limicie czasu. `count_primes`Funkcja pokazuje, jak używać `cancel_after_timeout` funkcji. Zlicza on liczbę elementów w podanym zakresie i kończy się niepowodzeniem, jeśli zadanie nie zostało ukończone w danym czasie. `wmain`Funkcja wywołuje `count_primes` funkcję wielokrotnie. Za każdym razem ilość czasu jest mniejsza. Program kończy działanie, gdy operacja nie zostanie zakończona w bieżącym limicie czasu.

[!code-cpp[concrt-task-delay#2](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_2.cpp)]

Gdy ta technika jest używana do anulowania zadań po opóźnieniu, wszystkie zadania, które nie zostały uruchomione, nie zostaną uruchomione po anulowaniu całego zadania. Jednak ważne jest, aby każde długotrwałe zadania odpowiadały na anulowanie w odpowiednim czasie. Aby uzyskać więcej informacji o anulowaniu zadania, zobacz [Anulowanie w PPL](cancellation-in-the-ppl.md).

## <a name="complete-code-example"></a>Pełny przykład kodu

Oto kompletny kod dla tego przykładu:

[!code-cpp[concrt-task-delay#3](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_3.cpp)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować kod, skopiuj go, a następnie wklej w projekcie programu Visual Studio lub wklej go w pliku o nazwie, `task-delay.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**cl.exe/EHsc Task-Delay. cpp**

## <a name="see-also"></a>Zobacz także

[Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Task — Klasa (środowisko uruchomieniowe współbieżności)](../../parallel/concrt/reference/task-class.md)<br/>
[Klasa cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md)<br/>
[Klasa cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md)<br/>
[Klasa task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)<br/>
[Timer — Klasa](../../parallel/concrt/reference/timer-class.md)<br/>
[Call, Klasa](../../parallel/concrt/reference/call-class.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Anulowanie w PPL](cancellation-in-the-ppl.md)
