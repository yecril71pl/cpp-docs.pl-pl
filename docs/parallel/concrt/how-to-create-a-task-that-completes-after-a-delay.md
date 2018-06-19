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
ms.openlocfilehash: fca1ba3874f02b44f96fd795b531536a23c8d462
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688414"
---
# <a name="how-to-create-a-task-that-completes-after-a-delay"></a>Porady: tworzenie zadania kończonego po opóźnieniu
Ten przykład przedstawia sposób użycia [concurrency::task](../../parallel/concrt/reference/task-class.md), [concurrency::cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md), [concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md), [ CONCURRENCY::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), [concurrency::timer](../../parallel/concrt/reference/timer-class.md), i [concurrency::call](../../parallel/concrt/reference/call-class.md) klasy Tworzenie zadania kończonego po opóźnieniu. Ta metoda służy do tworzenia pętli od czasu do czasu sondować danych, wprowadzenie limitów czasu, opóźnienie wyznaczonym czasie obsługę danych wejściowych użytkownika, które itd.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `complete_after` i `cancel_after_timeout` funkcji. `complete_after` Funkcja tworzy `task` obiektu kończące się po określonym czasie. Używa `timer` obiektu i `call` obiektu w celu ustawienia `task_completion_event` obiektu po określonym czasie. Za pomocą `task_completion_event` klasy, można zdefiniować zadania kończonego po wątku lub inne zadanie sygnalizuje, że wartość jest dostępna. Gdy zdarzenie jest ustawiona, wykonaj zadania odbiornika, a ich kontynuacje są zaplanowane do uruchomienia.  
  
> [!TIP]
>  Aby uzyskać więcej informacji na temat `timer` i `call` klasy, które są częścią biblioteki agentów asynchronicznych, zobacz [bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md).  
  
 `cancel_after_timeout` Funkcja opiera się na `complete_after` funkcji, aby anulować zadanie, jeśli to zadanie nie zostanie zakończone przed podanego limitu czasu. `cancel_after_timeout` Funkcja tworzy dwa zadania. Pierwszym zadaniem oznacza powodzenie i zakończeniu po ukończeniu zadania podane; drugie zdanie oznacza błąd i kończy działanie po określonym czasie. `cancel_after_timeout` Funkcja tworzy uruchamiany po ukończeniu zadania powodzenie lub niepowodzenie zadania kontynuacji. Niepowodzenie zadań wykona pierwszej, kontynuacji anuluje tokenu źródło, aby anulować zadanie ogólnej.  
  
 [!code-cpp[concrt-task-delay#1](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_1.cpp)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład oblicza liczbę liczb pierwszych w zakresie [0, 100000] wiele razy. Kończy się niepowodzeniem, jeśli nie zostanie zakończone w określonym terminie. `count_primes` Funkcja przedstawiono sposób użycia `cancel_after_timeout` funkcji. Oblicza liczbę blokad w danym zakresie, a nie powiedzie się, jeśli zadanie nie zostanie zakończone w podany czas. `wmain` Wywołania funkcji `count_primes` działać wiele razy. Zawsze, połowy limitu czasu. Ten program zakończy się po operacji nie zostanie zakończone w bieżącym limitu czasu.  
  
 [!code-cpp[concrt-task-delay#2](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_2.cpp)]  
  
 Jeśli ten sposób można anulować zadania z opóźnieniem, wszystkie zadania nierozpoczętych nie uruchamia się po ogólne zadanie zostało anulowane. Jednak jest ważne w przypadku dowolnego długotrwałych zadań odpowiedzieć na anulowanie w odpowiednim czasie. Aby uzyskać więcej informacji na temat anulowanie zadania, zobacz [anulowanie w PPL](cancellation-in-the-ppl.md).  
  
## <a name="example"></a>Przykład  
 W tym miejscu jest kompletny kod dla tego przykładu:  
  
 [!code-cpp[concrt-task-delay#3](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_3.cpp)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować kod, skopiuj go i następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `task-delay.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **zadanie/ehsc cl.exe-delay.cpp**  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Task — klasa (współbieżność środowiska wykonawczego)](../../parallel/concrt/reference/task-class.md)   
 [cancellation_token_source — klasa](../../parallel/concrt/reference/cancellation-token-source-class.md)   
 [cancellation_token — klasa](../../parallel/concrt/reference/cancellation-token-class.md)   
 [task_completion_event — klasa](../../parallel/concrt/reference/task-completion-event-class.md)   
 [Klasa czasomierza](../../parallel/concrt/reference/timer-class.md)   
 [Call — klasa](../../parallel/concrt/reference/call-class.md)   
 [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Anulowanie w PPL](cancellation-in-the-ppl.md)

