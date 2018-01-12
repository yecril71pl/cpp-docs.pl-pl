---
title: "Porady: Zarządzanie przypadkiem Planisty | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- managing a scheduler instance [Concurrency Runtime]
- scheduler instances, managing [Concurrency Runtime]
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f2e4916e0f563c4034dc27be1e3d911f42a65319
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-manage-a-scheduler-instance"></a>Porady: zarządzanie przypadkiem planisty
Wystąpienia harmonogramu pozwalają skojarzyć określone zasady planowania z różnych rodzajów obciążeń. Ten temat zawiera dwa podstawowe przykłady, które pokazują, jak utworzyć i Zarządzanie wystąpieniem harmonogramu.  
  
 Przykłady tworzenia planiści używające domyślnych zasad harmonogramu. Aby uzyskać przykład tworzenia harmonogramu, który używa niestandardowych zasad, zobacz [porady: Określ konkretne zasady harmonogramu](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).  
  
### <a name="to-manage-a-scheduler-instance-in-your-application"></a>Aby zarządzać przypadkiem planisty w aplikacji  
  
1.  Utwórz [concurrency::SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) wartości obiekt, który zawiera zasady dla harmonogramu do użycia.  
  

2.  Wywołanie [concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create) metody lub [concurrency::Scheduler::Create](reference/scheduler-class.md#create) metodę w celu utworzenia wystąpienia harmonogramu.  
  
     Jeśli używasz `Scheduler::Create` metody, wywołaj [concurrency::Scheduler::Attach](reference/scheduler-class.md#attach) metody, gdy trzeba skojarzyć planista z bieżącego kontekstu.  
  
3.  Wywołanie [CreateEvent](http://msdn.microsoft.com/library/windows/desktop/ms682396) funkcji, aby utworzyć dojścia do obiektu-sygnalizuje, automatyczne resetowanie zdarzenia.  
  
4.  Przekaż uchwyt do obiektu zdarzenia, który został właśnie utworzony do [concurrency::CurrentScheduler::RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent) metody lub [concurrency::Scheduler::RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent) metody. Rejestruje to zdarzenie można ustawić, gdy harmonogram zostanie zniszczony.  
  
5.  Wykonaj zadania, które mają bieżącego harmonogramu do zaplanowania.  
  
6.  Wywołanie [concurrency::CurrentScheduler::Detach](reference/currentscheduler-class.md#detach) metodę, aby odłączyć bieżącego harmonogramu i Przywróć poprzednie harmonogram jako bieżący.  
  
     Jeśli używasz `Scheduler::Create` metody, wywołaj [concurrency::Scheduler::Release](reference/scheduler-class.md#release) metody, aby zmniejszyć liczbę odwołanie `Scheduler` obiektu.  
  
7.  Przekaż dojście do zdarzenia w celu [WaitForSingleObject](http://msdn.microsoft.com/library/windows/desktop/ms687032) funkcja oczekiwania harmonogramu zamknąć.  
  
8.  Wywołanie [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211) funkcji, aby zamknąć uchwytu do obiektu zdarzenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia dwa sposoby Zarządzanie wystąpieniem harmonogramu. Każdy przykładzie najpierw używane domyślny harmonogram do wykonania zadania drukowania Unikatowy identyfikator bieżącego harmonogramu. Każdy przykład następnie używa wystąpienia harmonogramu przeprowadzić to samo zadanie ponownie. Ponadto każdy przykład przywraca harmonogram domyślny jako bieżący i wykonuje zadanie jeszcze raz.  
  
 W pierwszym przykładzie użyto [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) klasę, aby utworzyć wystąpieniem harmonogramu i powiązać ją z bieżącego kontekstu. W drugim przykładzie użyto [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) klasy do wykonania tego samego zadania. Zazwyczaj `CurrentScheduler` klasa jest używana do pracy z bieżącego harmonogramu. Drugi przykład, który używa `Scheduler` klasa, jest przydatne, gdy chcesz kontrolować, gdy harmonogram jest skojarzony z bieżącego kontekstu lub gdy chcesz skojarzyć określonych transfery danych z określonych zadań.  
  
 [!code-cpp[concrt-scheduler-instance#1](../../parallel/concrt/codesnippet/cpp/how-to-manage-a-scheduler-instance_1.cpp)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
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
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `scheduler-instance.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc harmonogramu instance.cpp**  
  
## <a name="see-also"></a>Zobacz też  
 [Wystąpienia harmonogramu](../../parallel/concrt/scheduler-instances.md)   
 [Instrukcje: określanie specjalnych zasad harmonogramu](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)

