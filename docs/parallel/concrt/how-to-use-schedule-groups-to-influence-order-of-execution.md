---
title: "Porady: Używanie grup harmonogramu do wywierania wpływu na kolejność wykonywania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- schedule groups, using [Concurrency Runtime]
- using schedule groups [Concurrency Runtime]
ms.assetid: 73124194-fc3a-491e-a23f-fbd7b5a4455c
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fcb37c1c14a9d09230bfa5d4fdce1da5eddfb4f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-schedule-groups-to-influence-order-of-execution"></a>Porady: używanie grup harmonogramu do wywierania wpływu na kolejność wykonywania
Współbieżność środowiska wykonawczego kolejność zaplanowane zadania jest deterministyczna. Jednak służy zasad harmonogramu do wywierania wpływu na kolejność, w którym są uruchomione zadania. W tym temacie przedstawiono sposób używanie grup harmonogramu razem z [concurrency::SchedulingProtocol](reference/concurrency-namespace-enums.md#policyelementkey) zasad harmonogramu do wywierania wpływu na kolejność, w którym są uruchomione zadania.  

  
 Przykład działa zestawu zadań dwa razy z różnych zasad harmonogramu. Obie zasady Ogranicz maksymalną liczbę przetwarzania zasobów do dwóch. Pierwsze uruchomienie używa `EnhanceScheduleGroupLocality` zasady, co jest ustawieniem domyślnym i drugi Uruchom używa `EnhanceForwardProgress` zasad. W obszarze `EnhanceScheduleGroupLocality` zasad, harmonogram uruchamia wszystkie zadania w grupie jeden harmonogram każdego zadania zakończenie lub daje w wyniku. W obszarze `EnhanceForwardProgress` zasad, harmonogram po przenosi do następnej grupy harmonogramu w sposób okrężnego tylko jedno zadanie zakończy lub daje w wyniku.  
  
 Gdy każda grupa harmonogramu zawiera zadania pokrewne `EnhanceScheduleGroupLocality` zasad zwykle powoduje zwiększoną wydajność ponieważ lokalizację pamięci podręcznej są zachowywane między zadaniami. `EnhanceForwardProgress` Zasad umożliwia zadań w celu wprowadzenia postęp i jest przydatne, gdy potrzebujesz planowania sprawiedliwe przydzielanie zasobów między grupami harmonogramu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie definiuje `work_yield_agent` klasy, która jest pochodną [concurrency::agent](../../parallel/concrt/reference/agent-class.md). `work_yield_agent` Klasa wykonuje jednostka pracy, daje bieżącego kontekstu, a następnie innej jednostki pracy. Agent używa [concurrency::wait](reference/concurrency-namespace-functions.md#wait) funkcji, aby wspólnie yield bieżącego kontekstu, co umożliwia uruchamianie innych kontekstach.  
  
 W tym przykładzie tworzy cztery `work_yield_agent` obiektów. Aby zilustrować, jak ustawić harmonogram zasad wpływa na kolejność uruchamiania agentów, przykładzie kojarzy pierwszych dwóch agentów z jeden harmonogram grupy i dwaj agenci z inną grupą harmonogramu. W przykładzie użyto [concurrency::CurrentScheduler::CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup) metodę w celu utworzenia [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) obiektów. W przykładzie uruchamiane są wszystkie cztery agentów dwa razy, zawsze za pomocą różnych zasad harmonogramu.  
  
 [!code-cpp[concrt-scheduling-protocol#1](../../parallel/concrt/codesnippet/cpp/how-to-use-schedule-groups-to-influence-order-of-execution_1.cpp)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
```Output  
Using EnhanceScheduleGroupLocality...  
group 0,
    task 0: first loop...  
group 0,
    task 1: first loop...  
group 0,
    task 0: waiting...  
group 1,
    task 0: first loop...  
group 0,
    task 1: waiting...  
group 1,
    task 1: first loop...  
group 1,
    task 0: waiting...  
group 0,
    task 0: second loop...  
group 1,
    task 1: waiting...  
group 0,
    task 1: second loop...  
group 0,
    task 0: finished...  
group 1,
    task 0: second loop...  
group 0,
    task 1: finished...  
group 1,
    task 1: second loop...  
group 1,
    task 0: finished...  
group 1,
    task 1: finished...  
 
Using EnhanceForwardProgress...  
group 0,
    task 0: first loop...  
group 1,
    task 0: first loop...  
group 0,
    task 0: waiting...  
group 0,
    task 1: first loop...  
group 1,
    task 0: waiting...  
group 1,
    task 1: first loop...  
group 0,
    task 1: waiting...  
group 0,
    task 0: second loop...  
group 1,
    task 1: waiting...  
group 1,
    task 0: second loop...  
group 0,
    task 0: finished...  
group 0,
    task 1: second loop...  
group 1,
    task 0: finished...  
group 1,
    task 1: second loop...  
group 0,
    task 1: finished...  
group 1,
    task 1: finished...  
```  
  
 Obie zasady utworzyć taką samą sekwencję zdarzeń. Jednak zasady używającą `EnhanceScheduleGroupLocality` uruchamiania obu agentów, które są częścią pierwszej grupy harmonogramu, przed rozpoczęciem agentów, które są częścią drugiej grupy. Zasady, która używa `EnhanceForwardProgress` zaczyna się jeden agent w pierwszej grupy, a następnie uruchamia pierwszego agenta w drugiej grupy.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `scheduling-protocol.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Planowanie/ehsc cl.exe-protocol.cpp**  
  
## <a name="see-also"></a>Zobacz też  
 [Grupy harmonogramu](../../parallel/concrt/schedule-groups.md)   
 [Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)

