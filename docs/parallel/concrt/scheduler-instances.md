---
title: "Wystąpienia harmonogramu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: scheduler instances
ms.assetid: 4819365f-ef99-49cc-963e-50a2a35a8d6b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1688a2b689b3fc3391e617f3d65d3c681f05a84f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="scheduler-instances"></a>Wystąpienia harmonogramu
W tym dokumencie opisano rolę wystąpienia harmonogramu w współbieżności środowiska wykonawczego i sposobu użycia [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) i [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) klasy Tworzenie i zarządzanie nimi wystąpienia harmonogramu. Wystąpienia harmonogramu są przydatne, jeśli chcesz skojarzyć z określonych rodzajów obciążeń jawne zasadami planowania. Na przykład można utworzyć jedno wystąpienie harmonogramu niektórych zadań godzinie priorytetu wątku z podwyższonym poziomem uprawnień i użyć domyślnego harmonogramu do wykonywania innych zadań podczas priorytetu wątku normalnego.  
  
> [!TIP]
>  Współbieżność środowiska wykonawczego zapewnia harmonogram domyślny, i dlatego nie trzeba utworzyć w aplikacji. Harmonogram zadań ułatwia dostrojenie wydajności aplikacji, dlatego zaleca się uruchamiania z [równoległych biblioteki wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md) lub [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) w przypadku jesteś nowym użytkownikiem współbieżności środowiska wykonawczego.  
  
##  <a name="top"></a>Sekcje  
  
-   [Harmonogram i currentscheduler — klasy](#classes)  
  
-   [Tworzenie wystąpienia harmonogramu](#creating)  
  
-   [Zarządzanie okresem istnienia wystąpienia harmonogramu](#managing)  
  
-   [Metody i funkcje](#features)  
  
-   [Przykład](#example)  
  
##  <a name="classes"></a>Harmonogram i currentscheduler — klasy  
 Harmonogram zadań umożliwia aplikacjom użyj jednej lub kilku *wystąpienia harmonogramu* można zaplanować pracę. [Concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) klasa reprezentuje wystąpienie harmonogramu i hermetyzuje funkcjonalność dotyczące planowania zadań.  
  
 Wątek, który jest dołączony do harmonogramu jest nazywany *kontekstu wykonywania*, lub po prostu *kontekstu*. W dowolnym momencie jeden harmonogram może być aktywne w bieżącym kontekście. Aktywnego harmonogramu jest także znana jako *bieżącego harmonogramu*. Współbieżność środowiska wykonawczego używa [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) klasy w celu zapewnienia dostępu do bieżącego harmonogramu. Bieżącego harmonogramu dla jednego kontekstu może się różnić od bieżącego harmonogramu dla innego kontekstu. Środowisko uruchomieniowe nie udostępnia reprezentację poziomie procesu bieżącego harmonogramu.  
  
 Zazwyczaj `CurrentScheduler` klasa jest używana do uzyskania dostępu do bieżącego harmonogramu. `Scheduler` Klasy jest przydatne, gdy trzeba zarządzać harmonogram, który nie jest bieżący.  
  
 W poniższych sekcjach opisano sposób tworzenia i Zarządzanie wystąpieniem harmonogramu. Pełny przykład ilustruje tych zadań, zobacz [porady: Zarządzanie przypadkiem Planisty](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).  
  
 [[Górnej](#top)]  
  
##  <a name="creating"></a>Tworzenie wystąpienia harmonogramu  
 Te trzy sposoby, aby utworzyć `Scheduler` obiektu:  
  
-   Jeśli harmonogram nie istnieje, środowisko uruchomieniowe tworzy domyślnego harmonogramu automatycznie funkcjonalność aparatu plików wykonywalnych, na przykład równoległych algorytm można używać do wykonywania pracy. Harmonogram domyślny staje się bieżącego harmonogramu dla kontekstu, który inicjuje równoległych pracy.  
  

-   [Concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create) metoda tworzy `Scheduler` obiekt, który używa określone zasady i kojarzy tego harmonogramu z bieżącego kontekstu.  
  
-   [Concurrency::Scheduler::Create](reference/scheduler-class.md#create) metoda tworzy `Scheduler` obiekt, który korzysta z określonych zasad, ale nie kojarzyć z bieżącego kontekstu.  

  
 Stosowanie środowiska wykonawczego utworzyć harmonogram domyślny umożliwia wszystkich zadań jednoczesnych na współużytkowanie tego samego harmonogramu. Zazwyczaj funkcjonalności zapewnianej przez [Biblioteka równoległych wzorców](../../parallel/concrt/parallel-patterns-library-ppl.md) (PLL) lub [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) służy do wykonywania pracy równoległych. W związku z tym nie trzeba pracować bezpośrednio z harmonogramu można sterować jego zasady lub okres istnienia. Użycie PPL lub biblioteka agentów, środowiska uruchomieniowego tworzy harmonogram domyślny, jeśli nie istnieje i ułatwia bieżącego harmonogramu dla każdej kontekstu. Podczas tworzenia harmonogramu i ustaw go jako bieżącego harmonogramu, następnie środowiska uruchomieniowego używa tego harmonogramu do planowania zadań. Wystąpienia harmonogramu dodatkowe należy utworzyć tylko wtedy, gdy wymagają określonych zasad dotyczących planowania. Aby uzyskać więcej informacji o zasadach, które są skojarzone z harmonogramu, zobacz [zasad harmonogramu](../../parallel/concrt/scheduler-policies.md).  
  
 [[Górnej](#top)]  
  
##  <a name="managing"></a>Zarządzanie okresem istnienia wystąpienia harmonogramu  
 Środowisko uruchomieniowe używa mechanizmu liczenie odwołań w celu zarządzają okresem istnienia `Scheduler` obiektów.  
  

 Jeśli używasz `CurrentScheduler::Create` metody lub `Scheduler::Create` metodę w celu utworzenia `Scheduler` obiektu środowiska wykonawczego ustawia odwołanie początkowa liczba tego harmonogramu do jednego. Środowisko uruchomieniowe zwiększa liczbę odwołanie podczas wywoływania [concurrency::Scheduler::Attach](reference/scheduler-class.md#attach) metody. `Scheduler::Attach` Stowarzyszonych metody `Scheduler` obiektu wraz z bieżącym kontekście. Dzięki temu bieżącego harmonogramu. Podczas wywoływania `CurrentScheduler::Create` tworzy środowisko uruchomieniowe obie metody `Scheduler` obiektu i dołącza go do bieżącego kontekstu (i ustawia liczbę odwołań do jednego). Można również użyć [concurrency::Scheduler::Reference](reference/scheduler-class.md#reference) metodę, aby zwiększyć liczbę odwołanie `Scheduler` obiektu.  
  
 Zmniejsza środowiska uruchomieniowego liczba odwołanie podczas wywoływania [concurrency::CurrentScheduler::Detach](reference/currentscheduler-class.md#detach) metodę, aby odłączyć bieżącego harmonogramu lub zadzwoń [concurrency::Scheduler::Release](reference/scheduler-class.md#release) metody. Jeśli liczba odwołań do zera, środowisko uruchomieniowe niszczy `Scheduler` obiektu po wszystkich zaplanowanych zadań zakończenia. Bieżące zadanie może zwiększyć liczbę odwołanie do bieżącego harmonogramu. W związku z tym jeśli liczba odwołań osiągnie zero i zadania zwiększa liczbę odwołań, środowisko uruchomieniowe nie niszczy `Scheduler` obiektu, dopóki liczba odwołań ponownie osiągnie zero, a zakończenie wszystkich zadań.  

  
 Środowisko uruchomieniowe przechowuje wewnętrzny stos `Scheduler` obiektów dla każdego kontekstu. Podczas wywoływania `Scheduler::Attach` lub `CurrentScheduler::Create` wypchnięcia metody środowiska uruchomieniowego, które `Scheduler` obiektu na stosie dla bieżącego kontekstu. Dzięki temu bieżącego harmonogramu. Podczas wywoływania `CurrentScheduler::Detach`, środowisko uruchomieniowe POP bieżącego harmonogramu ze stosu dla bieżącego kontekstu i ustawia poprzedni jako bieżącego harmonogramu.  
  
 Środowisko uruchomieniowe udostępnia kilka sposobów zarządzania okres istnienia wystąpienia harmonogramu. W poniższej tabeli przedstawiono odpowiedniej metody, która zwalnia lub odłącza harmonogramu z bieżącego kontekstu dla każdej metody, która tworzy lub dołącza harmonogramu dla bieżącego kontekstu.  
  
|Utwórz lub attach — metoda|Czy zwykłe pliki binarne detach — metoda|  
|-----------------------------|------------------------------|  
|`CurrentScheduler::Create`|`CurrentScheduler::Detach`|  
|`Scheduler::Create`|`Scheduler::Release`|  
|`Scheduler::Attach`|`CurrentScheduler::Detach`|  
|`Scheduler::Reference`|`Scheduler::Release`|  
  
 Wywoływanie niewłaściwe wersji lub odłączyć — metoda i tworzy nieokreślony zachowania w czasie wykonywania.  
  
 Jeśli używane są funkcje, na przykład PPL, powodujący środowiska wykonawczego utworzyć harmonogram domyślny nie wersji lub odłączanie tego harmonogramu. Środowisko uruchomieniowe zarządza czasem istnienia żadnych harmonogramu, który tworzy.  
  

 Ponieważ środowisko uruchomieniowe nie niszczy `Scheduler` obiektu przed zakończeniem wszystkie zadania, można użyć [concurrency::Scheduler::RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent) metody lub [concurrency::CurrentScheduler:: RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent) metody, aby otrzymać powiadomienie w przypadku `Scheduler` obiekt zostanie zniszczony. Jest to przydatne, gdy trzeba poczekać co zadanie, które jest zaplanowane przez `Scheduler` obiekt, aby zakończyć.  
  
 [[Górnej](#top)]  
  
##  <a name="features"></a>Metody i funkcje  
 Ta sekcja zawiera podsumowanie ważne metody `CurrentScheduler` i `Scheduler` klasy.  
  
 Pomyśl o `CurrentScheduler` klasy jako pomocnika dla tworzenia harmonogramu do użycia w bieżącym kontekście. `Scheduler` Klasa umożliwia sterowanie harmonogramu, który należy do innego kontekstu.  
  
 W poniższej tabeli przedstawiono ważne metody, które są zdefiniowane przez `CurrentScheduler` klasy.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Utwórz](reference/currentscheduler-class.md#create)|Tworzy `Scheduler` obiekt, który korzysta z określonych zasad i kojarzy ją z bieżącego kontekstu.|  
|[Pobierz](reference/currentscheduler-class.md#get)|Pobiera wskaźnik do `Scheduler` obiekt, który jest skojarzony z bieżącego kontekstu. Ta metoda nie zwiększa się liczba odwołań z `Scheduler` obiektu.|  
|[Detach](reference/currentscheduler-class.md#detach)|Odłącza bieżącego harmonogramu z bieżącego kontekstu i ustawia poprzedni jako bieżącego harmonogramu.|  
|[RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)|Rejestruje zdarzenie ustawia środowisko uruchomieniowe, gdy zostanie zniszczony bieżącego harmonogramu.|  
|[CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)|Tworzy [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) obiektu w bieżącego harmonogramu.|  
|[ScheduleTask](reference/currentscheduler-class.md#scheduletask)|Dodaje lekkie zadania do kolejki harmonogramu bieżącego harmonogramu.|  
|[GetPolicy](reference/currentscheduler-class.md#getpolicy)|Pobiera kopię zasad, który jest skojarzony z bieżącego harmonogramu.|  
  
 W poniższej tabeli przedstawiono ważne metody, które są zdefiniowane przez `Scheduler` klasy.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Utwórz](reference/scheduler-class.md#create)|Tworzy `Scheduler` obiekt, który korzysta z określonych zasad.|  
|[Attach](reference/scheduler-class.md#attach)|Kojarzy `Scheduler` obiektu wraz z bieżącym kontekście.|  
|[Dokumentacja](reference/scheduler-class.md#reference)|Zwiększa licznik odwołanie `Scheduler` obiektu.|  
|[Wersja](reference/scheduler-class.md#release)|Zmniejsza licznik odwołanie `Scheduler` obiektu.|  
|[RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)|Rejestruje zdarzenie środowiska wykonawczego Ustawia, kiedy `Scheduler` obiekt zostanie zniszczony.|  
|[CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup)|Tworzy [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) obiektu w `Scheduler` obiektu.|  
|[ScheduleTask](reference/scheduler-class.md#scheduletask)|Zaplanowane zadania lekkie `Scheduler` obiektu.|  
|[GetPolicy](reference/scheduler-class.md#getpolicy)|Pobiera kopię zasad, z którym skojarzony jest `Scheduler` obiektu.|  
|[SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy)|Ustawia zasady dla środowiska uruchomieniowego do użycia podczas tworzenia harmonogramu domyślnego.|  
|[ResetDefaultSchedulerPolicy](reference/scheduler-class.md#resetdefaultschedulerpolicy)|Przywraca domyślne zasady do tego, który był aktywny przed wywołaniem do `SetDefaultSchedulerPolicy`. Jeśli harmonogram domyślny jest tworzony po to wywołanie, środowisko uruchomieniowe używa domyślne ustawienia zasad można utworzyć harmonogramu.|  

  
 [[Górnej](#top)]  
  
##  <a name="example"></a>Przykład  
 Podstawowe przykłady sposobu tworzenia i Zarządzanie wystąpieniem harmonogramu, zobacz [porady: Zarządzanie przypadkiem Planisty](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Porady: Zarządzanie przypadkiem Planisty](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)   
 [Zasady harmonogramu](../../parallel/concrt/scheduler-policies.md)   
 [Grupy harmonogramu](../../parallel/concrt/schedule-groups.md)

