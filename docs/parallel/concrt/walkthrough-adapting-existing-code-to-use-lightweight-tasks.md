---
title: 'Wskazówki: adaptacja istniejącego kodu do potrzeb zadań lekkich'
ms.date: 04/25/2019
helpviewer_keywords:
- using lightweight tasks [Concurrency Runtime]
- lightweight tasks, using [Concurrency Runtime]
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
ms.openlocfilehash: e7c6096829a1cd45cfdb849a1899d6b4a2d4cb78
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141997"
---
# <a name="walkthrough-adapting-existing-code-to-use-lightweight-tasks"></a>Wskazówki: adaptacja istniejącego kodu do potrzeb zadań lekkich

W tym temacie pokazano, jak dostosować istniejący kod, który używa interfejsu API systemu Windows do tworzenia i wykonywania wątku w celu korzystania z uproszczonego zadania.

*Lekkie zadanie* to zadanie, które można zaplanować bezpośrednio z obiektu [concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) lub [concurrency:: Schedule](../../parallel/concrt/reference/schedulegroup-class.md) . Uproszczone zadania są przydatne podczas dostosowywania istniejącego kodu do korzystania z funkcji planowania środowisko uruchomieniowe współbieżności.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego instruktażu zapoznaj się z tematem [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="example"></a>Przykład

Poniższy przykład ilustruje typowy sposób użycia interfejsu API systemu Windows do tworzenia i wykonywania wątku. W tym przykładzie funkcja [myFunction wywołuje](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) `MyThreadFunction` w osobnym wątku.

### <a name="initial-code"></a>Kod początkowy

[!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
Parameters = 50, 100
```

Poniższe kroki pokazują, jak dostosować przykład kodu, aby użyć środowisko uruchomieniowe współbieżności do wykonania tego samego zadania.

### <a name="to-adapt-the-example-to-use-a-lightweight-task"></a>Aby dostosować przykład użycia lekkiego zadania

1. Dodaj `#include` dyrektywę dla pliku nagłówkowego ConcRT. h.

[!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]

1. Dodaj `using` dyrektywę dla przestrzeni nazw `concurrency`.

[!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]

1. Zmień deklarację `MyThreadFunction`, aby użyć konwencji wywoływania `__cdecl` i zwrócić `void`.

[!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]

1. Zmodyfikuj strukturę `MyData` w taki sposób, aby obejmowała obiekt [concurrency:: Event](../../parallel/concrt/reference/event-class.md) , który sygnalizuje główną aplikację, że zadanie zostało zakończone.

[!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]

1. Zastąp wywołanie do `CreateThread` za pomocą wywołania metody [concurrency:: CurrentScheduler:: ScheduleTask —](reference/currentscheduler-class.md#scheduletask) .

[!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]

1. Zastąp wywołanie do `WaitForSingleObject` za pomocą wywołania metody [concurrency:: Event:: wait](reference/event-class.md#wait) , aby poczekać na zakończenie zadania.

[!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]

1. Usuń wywołanie do `CloseHandle`.

1. Zmień sygnaturę definicji `MyThreadFunction`, aby pasowała do kroku 3.

[!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]

1. Na końcu funkcji `MyThreadFunction` Wywołaj metodę [concurrency:: Event:: Set](reference/event-class.md#set) , aby sygnalizować główną aplikację, że zadanie zostało zakończone.

[!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]

1. Usuń instrukcję `return` z `MyThreadFunction`.

### <a name="completed-code"></a>Ukończony kod

W poniższym przykładzie pokazano kod, który używa lekkiego zadania do wywołania funkcji `MyThreadFunction`.

[!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]

## <a name="see-also"></a>Zobacz też

[Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Scheduler, klasa](../../parallel/concrt/reference/scheduler-class.md)
