---
title: 'Porady: Zarządzanie wystąpieniem harmonogramu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- managing a scheduler instance [Concurrency Runtime]
- scheduler instances, managing [Concurrency Runtime]
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 20730eb275dd2dd08f7ed7112b42ff1befa8e225
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222760"
---
# <a name="how-to-manage-a-scheduler-instance"></a>Porady: zarządzanie przypadkiem planisty
Wystąpienia harmonogramu umożliwiają kojarzenie określone zasady planowania z różnego rodzaju obciążeń. Ten temat zawiera dwa przykłady pokazujące, jak utworzyć i Zarządzanie wystąpieniem harmonogramu.  
  
 Przykłady tworzenia harmonogramów, używające domyślnych zasad harmonogramu. Aby uzyskać przykład tworzenia harmonogramu, który korzysta z zasad niestandardowych, zobacz [porady: Określanie zasad harmonogramu określonego](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).  
  
### <a name="to-manage-a-scheduler-instance-in-your-application"></a>Aby zarządzać przypadkiem planisty w aplikacji  
  
1.  Tworzenie [concurrency::SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) wartości obiektu, który zawiera zasady harmonogramu do użycia.  
  

2.  Wywołaj [concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create) metody lub [concurrency::Scheduler::Create](reference/scheduler-class.md#create) metodę w celu utworzenia wystąpienia harmonogramu.  
  
     Jeśli używasz `Scheduler::Create` metody, wywołanie [concurrency::Scheduler::Attach](reference/scheduler-class.md#attach) metody, gdy należy skojarzyć harmonogramu przy użyciu bieżącego kontekstu.  
  
3.  Wywołaj [CreateEvent](/windows/desktop/api/synchapi/nf-synchapi-createeventa) funkcji, aby utworzyć uchwytu do obiektu zasygnalizowane resetowaniem automatycznym zdarzeń.  
  
4.  Przekaż uchwytu do obiektu zdarzenia, który został utworzony do [concurrency::CurrentScheduler::RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent) metody lub [concurrency::Scheduler::RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent) metody. Rejestruje to zdarzenie można ustawić, kiedy niszczony jest harmonogram.  
  
5.  Wykonaj zadania, które mają bieżącego harmonogramu do zaplanowania.  
  
6.  Wywołaj [concurrency::CurrentScheduler::Detach](reference/currentscheduler-class.md#detach) metodę, aby odłączyć bieżącego harmonogramu i przywrócić poprzednich harmonogram jako bieżący.  
  
     Jeśli używasz `Scheduler::Create` metody, wywołanie [concurrency::Scheduler::Release](reference/scheduler-class.md#release) metodę, aby zmniejszyć liczbę odwołań `Scheduler` obiektu.  
  
7.  Przekaż dojście do zdarzenia w celu [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) funkcję, aby czekać na harmonogram zamknąć.  
  
8.  Wywołaj [funkcja CloseHandle](https://msdn.microsoft.com/library/windows/desktop/ms724211) funkcję, aby zamknąć dojście do obiektu zdarzenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia dwa sposoby Zarządzanie wystąpieniem harmonogramu. Każdy przykład najpierw używa domyślnego harmonogramu do wykonania zadania, który wyświetla unikatowy identyfikator bieżącego harmonogramu. Każdy przykład następnie używa wystąpienia harmonogramu, przeprowadzić to samo zadanie. Na koniec każdego przykład przywraca domyślnego harmonogramu jak aktualny plan i wykonuje to zadanie jeszcze raz.  
  
 W pierwszym przykładzie użyto [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) klasy, aby utworzyć wystąpienie harmonogramu i skojarzyć ją z bieżącego kontekstu. W drugim przykładzie użyto [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) klasy w celu wykonania tego samego zadania. Zazwyczaj `CurrentScheduler` klasa jest używana do pracy z bieżącego harmonogramu. Drugi przykład, który używa `Scheduler` klasy, jest przydatne, gdy użytkownik chce kontrolować kiedy harmonogram jest skojarzony z bieżącym kontekście lub gdy chcesz skojarzyć określonych harmonogramów z określonych zadań.  
  
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
 Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `scheduler-instance.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.  
  
 **Usługa scheduler-instance.cpp dla cl.exe/ehsc**  
  
## <a name="see-also"></a>Zobacz też  
 [Wystąpienia harmonogramu](../../parallel/concrt/scheduler-instances.md)   
 [Instrukcje: określanie specjalnych zasad harmonogramu](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)

