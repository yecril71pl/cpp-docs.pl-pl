---
title: Wystąpienia harmonogramu
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler instances
ms.assetid: 4819365f-ef99-49cc-963e-50a2a35a8d6b
ms.openlocfilehash: 19bd871857dcef6aaef153798388c0272239fa1f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180170"
---
# <a name="scheduler-instances"></a>Wystąpienia harmonogramu

W tym dokumencie opisano rolę wystąpienia harmonogramu w środowisku uruchomieniowym współbieżności i sposobu używania [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) i [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) klasy, aby tworzyć i zarządzać nimi wystąpienia harmonogramu. Wystąpienia harmonogramu są przydatne, jeśli chcesz skojarzyć z określonych typów obciążenia jawne zasadami planowania. Na przykład można utworzyć jedno wystąpienie usługi scheduler do uruchamiania niektórych zadań priorytetem wątku z podwyższonym poziomem uprawnień i używają domyślnego harmonogramu uruchomienie innych zadań priorytetem normalne wątku.

> [!TIP]
>  Środowisko uruchomieniowe współbieżności zawiera domyślnego harmonogramu, a w związku z tym nie należy utworzyć w aplikacji. Ponieważ Harmonogram zadań ułatwia dostrajania wydajności aplikacji, zalecamy rozpoczęcie od [biblioteki wzorców równoległych (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) lub [bibliotekę asynchronicznych agentów](../../parallel/concrt/asynchronous-agents-library.md) przypadku jesteś nowym użytkownikiem w czasie wykonywania współbieżności.

##  <a name="top"></a> Sekcje

- [Harmonogram i currentscheduler — klasy](#classes)

- [Tworzenie wystąpienia usługi Scheduler](#creating)

- [Zarządzanie okresem istnienia wystąpienia harmonogramu](#managing)

- [Metody i funkcje](#features)

- [Przykład](#example)

##  <a name="classes"></a> Harmonogram i currentscheduler — klasy

Harmonogram zadań umożliwia aplikacjom używanie co najmniej jeden *wystąpienia harmonogramu* do planowania pracy. [Concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) klasa reprezentuje wystąpienie harmonogramu i hermetyzuje funkcjonalność związany z usługą planowania zadań.

Wątek, który jest dołączony do harmonogramu jest znany jako *kontekstu wykonania*, lub po prostu *kontekstu*. Jeden harmonogram może być aktywny w bieżącym kontekście w dowolnym momencie. Aktywne harmonogram jest także znana jako *bieżącego harmonogramu*. Środowisko uruchomieniowe współbieżności używa [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) klasy w celu zapewnienia dostępu do bieżącego harmonogramu. Bieżący harmonogram jednym kontekście może się różnić od bieżącego harmonogramu w innym kontekście. Środowisko wykonawcze nie udostępnia reprezentację bieżącego harmonogramu w poziomie procesu.

Zazwyczaj `CurrentScheduler` klasa jest używana do dostępu do bieżącego harmonogramu. `Scheduler` Klasy jest przydatne w przypadku, gdy trzeba zarządzać harmonogram, który jest inny niż bieżąca.

Poniżej opisano sposób tworzenia i Zarządzanie wystąpieniem harmonogramu. Aby uzyskać pełny przykład ilustrujący te zadania, zobacz [jak: Zarządzanie wystąpieniem harmonogramu](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).

[[Górnej](#top)]

##  <a name="creating"></a> Tworzenie wystąpienia usługi Scheduler

Te trzy sposoby, aby utworzyć `Scheduler` obiektu:

- Jeśli harmonogram nie istnieje, środowisko uruchomieniowe tworzy domyślnego harmonogramu dla Ciebie podczas wykonywania pracy przy użyciu funkcji środowiska uruchomieniowego, na przykład algorytmu równoległego. Domyślnego harmonogramu staje się bieżącego harmonogramu dla kontekstu, który inicjuje równoległą pracę.

- [Concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create) metoda tworzy `Scheduler` obiekt, który korzysta z określonych zasad i kojarzy tego harmonogramu z bieżącego kontekstu.

- [Concurrency::Scheduler::Create](reference/scheduler-class.md#create) metoda tworzy `Scheduler` obiekt, który korzysta z określonych zasad, ale nie tworzy skojarzenia z bieżącego kontekstu.

Środowiska uruchomieniowego utworzyć domyślny harmonogram co pozwala na udostępnianie tego samego harmonogramu wszystkich zadań jednoczesnych. Zwykle funkcje, które są dostarczane przez [biblioteki wzorców równoległych](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) lub [bibliotekę asynchronicznych agentów](../../parallel/concrt/asynchronous-agents-library.md) służy do wykonywania pracy równoległej. W związku z tym nie trzeba pracować bezpośrednio z harmonogram, który ma kontrolę nad jego zasad i okresu istnienia. Gdy używasz PPL lub biblioteki agentów, środowisko uruchomieniowe tworzy domyślnego harmonogramu, jeśli nie istnieje i sprawia, że bieżącego harmonogramu dla każdego kontekstu. Podczas tworzenia harmonogramu i ustawić go jako bieżącego harmonogramu, a następnie na podstawie środowisko uruchomieniowe ten harmonogram do planowania zadań. Tworzenie wystąpienia harmonogramu dodatkowe tylko wtedy, gdy potrzebujesz określone zasady harmonogramu. Aby uzyskać więcej informacji na temat zasad, które są skojarzone z harmonogramu, zobacz [zasad harmonogramu](../../parallel/concrt/scheduler-policies.md).

[[Górnej](#top)]

##  <a name="managing"></a> Zarządzanie okresem istnienia wystąpienia harmonogramu

Środowisko wykonawcze używa mechanizmu zliczanie odwołań, aby kontrolować okres istnienia `Scheduler` obiektów.

Zastosowania `CurrentScheduler::Create` metody lub `Scheduler::Create` metodę w celu utworzenia `Scheduler` obiektu, środowisko uruchomieniowe ustawia licznik odwołań początkową tego harmonogramu równą jeden. Środowisko uruchomieniowe zwiększa liczbę odwołań po wywołaniu [concurrency::Scheduler::Attach](reference/scheduler-class.md#attach) metody. `Scheduler::Attach` Metoda kojarzy `Scheduler` obiektu wraz z bieżącym kontekście. Dzięki temu bieżącego harmonogramu. Gdy wywołujesz `CurrentScheduler::Create` tworzy środowisko uruchomieniowe obie metody `Scheduler` obiektu i dołącza go do bieżącego kontekstu (i ustawia liczbę odwołań do jednego). Można również użyć [concurrency::Scheduler::Reference](reference/scheduler-class.md#reference) metodę, aby zwiększyć licznik odwołań `Scheduler` obiektu.

Środowiska uruchomieniowego Dekrementuje, liczbę odwołań, gdy zostanie wywołana [concurrency::CurrentScheduler::Detach](reference/currentscheduler-class.md#detach) metodę, aby odłączyć bieżącego harmonogramu, lub zadzwoń [concurrency::Scheduler::Release](reference/scheduler-class.md#release) metody. Gdy licznik odwołań osiągnie zero, środowisko uruchomieniowe niszczy `Scheduler` obiektu po wszystkich zakończenie zadania według harmonogramu. Bieżące zadanie może zwiększyć licznik odwołań bieżącego harmonogramu. W związku z tym, jeśli licznik odwołań osiągnie zero, a zadanie zwiększa liczbę odwołań, środowisko wykonawcze nie niszczy `Scheduler` obiektu, aż licznik odwołań ponownie osiągnie zero, a zakończenie wszystkich zadań.

Środowisko uruchomieniowe przechowuje wewnętrznego stosu `Scheduler` obiektów dla każdego kontekstu. Gdy wywołujesz `Scheduler::Attach` lub `CurrentScheduler::Create` metody, środowisko uruchomieniowe wypchnięć, które zakończyły `Scheduler` obiektów na stosie dla bieżącego kontekstu. Dzięki temu bieżącego harmonogramu. Gdy wywołujesz `CurrentScheduler::Detach`, środowisko uruchomieniowe POP bieżącego harmonogramu ze stosu dla bieżącego kontekstu i ustawia poprzedni jako bieżącego harmonogramu.

Środowisko wykonawcze zapewnia kilka sposobów, aby zarządzać okresem istnienia wystąpienia harmonogramu. W poniższej tabeli przedstawiono odpowiedniej metody, które zwalnia lub odłącza harmonogramu z bieżącego kontekstu dla poszczególnych metod, które tworzy i dołącza harmonogramu dla bieżącego kontekstu.

|Tworzenie lub attach — metoda|Wydania lub detach — metoda|
|-----------------------------|------------------------------|
|`CurrentScheduler::Create`|`CurrentScheduler::Detach`|
|`Scheduler::Create`|`Scheduler::Release`|
|`Scheduler::Attach`|`CurrentScheduler::Detach`|
|`Scheduler::Reference`|`Scheduler::Release`|

Wywoływanie niewłaściwe wersji lub odłącz metoda generuje nieokreślone zachowanie w środowisku uruchomieniowym.

Korzystając z funkcji, na przykład PPL, który powoduje, że środowisko uruchomieniowe utworzyć domyślny harmonogram dla Ciebie, wersji lub nie odłączyć ten harmonogram. Środowisko uruchomieniowe zarządza czasem istnienia dowolnej harmonogram, który tworzy.

Ponieważ środowisko wykonawcze nie niszczy `Scheduler` obiektu przed zakończeniem wszystkich zadań, można użyć [concurrency::Scheduler::RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent) metody lub [concurrency::CurrentScheduler:: Registershutdownevent —](reference/currentscheduler-class.md#registershutdownevent) metodę, aby otrzymać powiadomienie po `Scheduler` niszczony jest obiekt. Jest to przydatne, gdy należy poczekać dla każdego zadania, które jest zaplanowane przez `Scheduler` obiektu, aby zakończyć.

[[Górnej](#top)]

##  <a name="features"></a> Metody i funkcje

Ta sekcja zawiera podsumowanie ważne metody `CurrentScheduler` i `Scheduler` klasy.

Traktować `CurrentScheduler` klasy jako pomocnika dla tworzenia harmonogramu do użytku w bieżącym kontekście. `Scheduler` Klasy umożliwia sterowanie harmonogramu, który należy do innego kontekstu.

W poniższej tabeli przedstawiono ważne metody, które są definiowane przez `CurrentScheduler` klasy.

|Metoda|Opis|
|------------|-----------------|
|[Tworzenie](reference/currentscheduler-class.md#create)|Tworzy `Scheduler` obiekt, który korzysta z określonymi zasadami i kojarzy ją z bieżącego kontekstu.|
|[Get](reference/currentscheduler-class.md#get)|Pobiera wskaźnik do `Scheduler` obiektu, który jest skojarzony z bieżącym kontekstem. Ta metoda nie zwiększa licznik odwołań `Scheduler` obiektu.|
|[Detach](reference/currentscheduler-class.md#detach)|Odłącza bieżącego harmonogramu z bieżącego kontekstu i ustawia poprzedni jako bieżącego harmonogramu.|
|[RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)|Rejestruje zdarzenie, które ustawia środowisko uruchomieniowe, kiedy niszczony jest bieżącego harmonogramu.|
|[CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)|Tworzy [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) obiektów w ramach bieżącego harmonogramu zadań.|
|[Scheduletask —](reference/currentscheduler-class.md#scheduletask)|Dodaje lekkie zadanie do harmonogramu kolejki bieżącego harmonogramu.|
|[GetPolicy](reference/currentscheduler-class.md#getpolicy)|Pobiera kopię zasad, który jest skojarzony z bieżącego harmonogramu.|

W poniższej tabeli przedstawiono ważne metody, które są definiowane przez `Scheduler` klasy.

|Metoda|Opis|
|------------|-----------------|
|[Tworzenie](reference/scheduler-class.md#create)|Tworzy `Scheduler` obiekt, który korzysta z określonymi zasadami.|
|[Attach](reference/scheduler-class.md#attach)|Kojarzy `Scheduler` obiektu wraz z bieżącym kontekście.|
|[Dokumentacja](reference/scheduler-class.md#reference)|Zwiększa licznik odwołań `Scheduler` obiektu.|
|[Wersja](reference/scheduler-class.md#release)|Dekrementuje licznikiem odwołań `Scheduler` obiektu.|
|[RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)|Rejestruje zdarzenie, które ustawia środowisko uruchomieniowe, kiedy `Scheduler` niszczony jest obiekt.|
|[CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup)|Tworzy [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) obiektu `Scheduler` obiektu.|
|[Scheduletask —](reference/scheduler-class.md#scheduletask)|Planuje zadania lekkie `Scheduler` obiektu.|
|[GetPolicy](reference/scheduler-class.md#getpolicy)|Pobiera kopię zasad, z którym skojarzony jest `Scheduler` obiektu.|
|[SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy)|Ustawia zasady dla środowiska uruchomieniowego do użycia podczas tworzenia harmonogramu domyślnego.|
|[ResetDefaultSchedulerPolicy](reference/scheduler-class.md#resetdefaultschedulerpolicy)|Przywrócenie domyślnych zasad do tego, który był aktywny przed wywołaniem do `SetDefaultSchedulerPolicy`. Jeśli domyślnego harmonogramu zostanie utworzony po tym wywołaniu, środowisko uruchomieniowe używa domyślnych ustawień zasad do utworzenia harmonogramu.|

[[Górnej](#top)]

##  <a name="example"></a> Przykład

Podstawowe przykłady sposobu tworzenia i Zarządzanie wystąpieniem harmonogramu, zobacz [jak: Zarządzanie wystąpieniem harmonogramu](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).

## <a name="see-also"></a>Zobacz także

[Task Scheduler](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Instrukcje: zarządzanie wystąpieniem harmonogramu](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[Zasady harmonogramu](../../parallel/concrt/scheduler-policies.md)<br/>
[Grupy harmonogramu](../../parallel/concrt/schedule-groups.md)
