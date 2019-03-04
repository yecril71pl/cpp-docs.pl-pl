---
title: 'Przewodnik: Dostosowanie istniejącego kodu do zadań lekkich'
ms.date: 11/04/2016
helpviewer_keywords:
- using lightweight tasks [Concurrency Runtime]
- lightweight tasks, using [Concurrency Runtime]
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
ms.openlocfilehash: 43e928e7d82b41b83fde5e8a7abaeeeb8d6fefa9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261222"
---
# <a name="walkthrough-adapting-existing-code-to-use-lightweight-tasks"></a>Przewodnik: Dostosowanie istniejącego kodu do zadań lekkich

W tym temacie pokazano, jak dostosować istniejący kod, który używa interfejsu API Windows do tworzenia i wykonywanie wątku w celu użycia lekkiego zadania.

A *lekkie zadanie* jest zadaniem, która jest zaplanowania bezpośrednio z [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) lub [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) obiektu. Zadania lekkie są przydatne, gdy dostosowanie istniejącego kodu do planowania funkcji środowiska uruchomieniowego współbieżności.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego instruktażu, przeczytaj temat [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład ilustruje użycie typowego interfejsu Windows API do tworzenia i wykonywanie wątku. W tym przykładzie użyto [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) funkcji do wywołania `MyThreadFunction` w oddzielnym wątku.

### <a name="code"></a>Kod

[!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]

### <a name="comments"></a>Komentarze

Ten przykład generuje następujące dane wyjściowe.

```Output
Parameters = 50, 100
```

Poniższe kroki pokazują jak dostosować ten przykład kodu do korzystania ze środowiska uruchomieniowego współbieżności do wykonania tego samego zadania.

### <a name="to-adapt-the-example-to-use-a-lightweight-task"></a>Aby dostosować przykład użycia lekkiego zadania

1. Dodaj `#include` dyrektywy dla concrt.h pliku nagłówka.

[!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]

1. Dodaj `using` dyrektywy dla `concurrency` przestrzeni nazw.

[!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]

1. Zmień deklarację `MyThreadFunction` używać `__cdecl` konwencji wywoływania i zwrócić `void`.

[!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]

1. Modyfikowanie `MyData` struktury, aby uwzględnić [concurrency::event](../../parallel/concrt/reference/event-class.md) obiektów, które sygnalizują aplikacji głównej, czy zadanie zostało zakończone.

[!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]

1. Zastąp wywołanie `CreateThread` wywołaniem [concurrency::CurrentScheduler::ScheduleTask](reference/currentscheduler-class.md#scheduletask) metody.

[!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]

1. Zastąp wywołanie `WaitForSingleObject` wywołaniem [concurrency::event::wait](reference/event-class.md#wait) metodę, aby czekać na zakończenie zadania.

[!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]

1. Usuń wywołanie funkcji `CloseHandle`.

1. Zmień sygnaturę definicji `MyThreadFunction` do dopasowania krok 3.

[!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]

9. Na koniec `MyThreadFunction` funkcji, wywołania [concurrency::event::set](reference/event-class.md#set) metody w celu zasygnalizowania do aplikacji głównej, że zadanie zostało zakończone.

[!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]

10. Usuń `return` instrukcji z `MyThreadFunction`.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

W poniższym przykładzie ukończone pokazano kod, który używa lekkie zadanie w celu wywołania `MyThreadFunction` funkcji.

### <a name="code"></a>Kod

[!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]

### <a name="comments"></a>Komentarze

## <a name="see-also"></a>Zobacz także

[Task Scheduler](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Scheduler, klasa](../../parallel/concrt/reference/scheduler-class.md)
