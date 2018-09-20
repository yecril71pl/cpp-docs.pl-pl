---
title: 'Porady: Tworzenie zadania kończonego po opóźnieniu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- task_completion_event class, example
- create a task that completes after a delay, example [C++]
ms.assetid: 3fc0a194-3fdb-4eba-8b8a-b890981a985d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 417562d515cb968b392c4480ddfd55c03ae494d1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422574"
---
# <a name="how-to-create-a-task-that-completes-after-a-delay"></a>Porady: tworzenie zadania kończonego po opóźnieniu

W tym przykładzie pokazano, jak używać [concurrency::task](../../parallel/concrt/reference/task-class.md), [concurrency::cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md), [concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md), [ CONCURRENCY::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), [concurrency::timer](../../parallel/concrt/reference/timer-class.md), i [concurrency::call](../../parallel/concrt/reference/call-class.md) klasy, aby tworzenie zadania kończonego po opóźnieniu. Ta metoda służy do tworzenia pętli, które od czasu do czasu sondowania pod kątem danych, wprowadzają limity czasu, opóźnienie obsługę danych wejściowych użytkownika przez wyznaczony czas i tak dalej.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `complete_after` i `cancel_after_timeout` funkcji. `complete_after` Funkcja tworzy `task` obiektów, które kończy się po określonym czasie opóźnienia. Używa ona `timer` obiektu i `call` obiektu w celu ustawienia `task_completion_event` obiektu po określonym czasie opóźnienia. Za pomocą `task_completion_event` klasy, można zdefiniować zadania kończonego po wątku lub inne zadanie sygnalizuje, że wartość jest dostępna. Gdy zdarzenie jest ustawione, kończą się zadania odbiornika a ich kontynuacje są planowane do uruchomienia.

> [!TIP]
>  Aby uzyskać więcej informacji na temat `timer` i `call` klasy, które są częścią bibliotekę asynchronicznych agentów, zobacz [bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md).

`cancel_after_timeout` Funkcja opiera się na `complete_after` funkcję, aby anulować zadanie, jeśli zadanie nie zostanie ukończone przed upływem limitu czasu w danym. `cancel_after_timeout` Funkcja tworzy dwa zadania. Pierwsze zadanie oznacza sukces i kończy się po zakończeniu zadania podane; drugie zadanie wskazuje błąd i kończy się po określonym czasie. `cancel_after_timeout` Funkcja tworzy zadanie kontynuacji, który jest wykonywany po zakończeniu zadania powodzenie lub niepowodzenie. Zadanie błąd wykona pierwszy, kontynuacja anuluje źródło tokenu, anulować całego zadania.

[!code-cpp[concrt-task-delay#1](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_1.cpp)]

## <a name="example"></a>Przykład

Poniższy przykład oblicza liczbę liczb pierwszych, w zakresie [0, 100000] wiele razy. Operacja kończy się niepowodzeniem, jeśli nie zostanie zakończone w określonym terminie. `count_primes` Funkcji pokazuje sposób użycia `cancel_after_timeout` funkcji. Zlicza liczbę blokad w danym zakresie i kończy się niepowodzeniem, jeśli zadanie nie zostanie zakończone w czasie podana. `wmain` Wywołaniach funkcji `count_primes` funkcji wiele razy. Za każdym razem połówki limitu czasu. Program zakończy się po operacji nie zostanie zakończone w bieżącym limitu czasu.

[!code-cpp[concrt-task-delay#2](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_2.cpp)]

Korzystając z tej techniki można anulować zadania z opóźnieniem, wszystkie zadania Nierozpoczęte nie rozpocznie się po ogólnej zadanie zostanie anulowane. Jest ważne w przypadku dowolnego długotrwałych zadań reagowanie na operację anulowania w odpowiednim czasie. Aby uzyskać więcej informacji na temat anulowania zadania, zobacz [anulowanie w PPL](cancellation-in-the-ppl.md).

## <a name="example"></a>Przykład

Oto kompletny kod dla tego przykładu:

[!code-cpp[concrt-task-delay#3](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_3.cpp)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować ten kod, skopiuj go a następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `task-delay.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc zadań delay.cpp**

## <a name="see-also"></a>Zobacz też

[Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[task, klasa (środowisko uruchomieniowe współbieżności)](../../parallel/concrt/reference/task-class.md)<br/>
[cancellation_token_source, klasa](../../parallel/concrt/reference/cancellation-token-source-class.md)<br/>
[cancellation_token, klasa](../../parallel/concrt/reference/cancellation-token-class.md)<br/>
[task_completion_event, klasa](../../parallel/concrt/reference/task-completion-event-class.md)<br/>
[timer, klasa](../../parallel/concrt/reference/timer-class.md)<br/>
[call, klasa](../../parallel/concrt/reference/call-class.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Anulowanie w PPL](cancellation-in-the-ppl.md)

