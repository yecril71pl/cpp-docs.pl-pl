---
title: 'Wskazówki: Adaptacja istniejącego kodu do potrzeb zadań lekkich | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- using lightweight tasks [Concurrency Runtime]
- lightweight tasks, using [Concurrency Runtime]
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4fe3bb4b576bd1f9160b4a3cdc3142be5cdff05
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="walkthrough-adapting-existing-code-to-use-lightweight-tasks"></a>Wskazówki: adaptacja istniejącego kodu do potrzeb zadań lekkich
W tym temacie pokazano, jak dostosować istniejący kod, który używa interfejsu API systemu Windows do tworzenia i wykonywania wątku w celu użyć zadania lekkie.  
  
 A *zadań lekkich* to zadanie, które można planować bezpośrednio z [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) lub [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) obiektu. Zadania lekkie jest przydatna w przypadku dostosowania istniejącego kodu do korzystania z funkcji planowania programu współbieżności środowiska wykonawczego.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Przed skorzystaniem z tego przewodnika, przeczytaj temat [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład przedstawia typowy sposób tworzenie i wykonywanie przez wątek interfejsu API systemu Windows. W tym przykładzie użyto [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) funkcji do wywołania `MyThreadFunction` w oddzielnym wątku.  
  
### <a name="code"></a>Kod  
 [!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]  
  
### <a name="comments"></a>Komentarze  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
```Output  
Parameters = 50, 100  
```  
  
 Poniższe kroki przedstawiają sposób dostosowania przykładu kodu na potrzeby wykonania tego samego zadania współbieżności środowiska wykonawczego.  
  
### <a name="to-adapt-the-example-to-use-a-lightweight-task"></a>Aby dostosować przykład użycia lekkiego zadania  
  
1.  Dodaj `#include` dyrektywy dla concrt.h pliku nagłówka.  
  
 [!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]  
  
2.  Dodaj `using` dyrektywy dla `concurrency` przestrzeni nazw.  
  
 [!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]  
  
3.  Zmień deklarację elementu `MyThreadFunction` do używania `__cdecl` konwencji wywoływania oraz `void`.  
  
 [!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]  
  
4.  Modyfikowanie `MyData` struktury, aby uwzględnić [concurrency::event](../../parallel/concrt/reference/event-class.md) obiekt, który sygnały do aplikacji głównej, że zadanie zostało zakończone.  
  
 [!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]  
  
5.  Zastąp wywołanie `CreateThread` wywołaniem [concurrency::CurrentScheduler::ScheduleTask](reference/currentscheduler-class.md#scheduletask) metody.  

  
 [!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]  
  

6.  Zastąp wywołanie `WaitForSingleObject` wywołaniem [concurrency::event::wait](reference/event-class.md#wait) metody oczekiwania na zakończenie zadania.  

 [!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]  
  
7.  Usuń wywołanie `CloseHandle`.  
  
8.  Zmienianie podpisu definicji `MyThreadFunction` odpowiadające krok 3.  
  
 [!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]  
  
9. Na koniec `MyThreadFunction` funkcji, należy wywołać [concurrency::event::set](reference/event-class.md#set) metody sygnalizują do aplikacji głównej, że zadanie zostało zakończone.  
  
 [!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]  
  
10. Usuń `return` instrukcji z `MyThreadFunction`.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie ukończone pokazano kod, który używa zadań lekkich wywołać `MyThreadFunction` funkcji.  
  
### <a name="code"></a>Kod  
 [!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]  
  
### <a name="comments"></a>Komentarze  
  
## <a name="see-also"></a>Zobacz też  
 [Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Scheduler, klasa](../../parallel/concrt/reference/scheduler-class.md)
