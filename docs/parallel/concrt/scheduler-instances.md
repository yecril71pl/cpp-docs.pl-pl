---
title: Wystąpienia harmonogramu
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler instances
ms.assetid: 4819365f-ef99-49cc-963e-50a2a35a8d6b
ms.openlocfilehash: e9e9b8124254084ac30191d37d49f2ef72bd677e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142291"
---
# <a name="scheduler-instances"></a>Wystąpienia harmonogramu

W tym dokumencie opisano rolę wystąpień usługi Scheduler w środowisko uruchomieniowe współbieżności oraz sposób używania klas [concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) i [concurrency:: CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) do tworzenia wystąpień harmonogramu i zarządzania nimi. Wystąpienia usługi Scheduler są przydatne, gdy chcesz skojarzyć jawne zasady planowania z określonymi typami obciążeń. Na przykład można utworzyć jedno wystąpienie harmonogramu do uruchamiania niektórych zadań z podwyższonym priorytetem wątku i użyć domyślnego harmonogramu do uruchamiania innych zadań przy normalnym priorytecie wątku.

> [!TIP]
> Środowisko uruchomieniowe współbieżności udostępnia domyślny harmonogram i dlatego nie jest konieczne tworzenie go w aplikacji. Ponieważ Harmonogram zadań ułatwia dostosowanie wydajności aplikacji, zalecamy rozpoczęcie od [biblioteki równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) lub [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) , jeśli są one nowe dla środowisko uruchomieniowe współbieżności.

## <a name="top"></a>Poszczególne

- [Harmonogramy i klasy CurrentScheduler](#classes)

- [Tworzenie wystąpienia harmonogramu](#creating)

- [Zarządzanie okresem istnienia wystąpienia harmonogramu](#managing)

- [Metody i funkcje](#features)

- [Przykład](#example)

## <a name="classes"></a>Harmonogramy i klasy CurrentScheduler

Harmonogram zadań umożliwia aplikacjom używanie co najmniej jednego *wystąpienia harmonogramu* w celu zaplanowania pracy. Klasa [concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) reprezentuje wystąpienie harmonogramu i hermetyzuje funkcjonalność, która jest powiązana z zadaniami planowania.

Wątek, który jest dołączony do harmonogramu, jest znany jako *kontekst wykonywania*lub po prostu *kontekst*. Jeden harmonogram może być aktywny w bieżącym kontekście w dowolnym momencie. Aktywny harmonogram jest również znany jako *bieżący harmonogram*. Środowisko uruchomieniowe współbieżności używa klasy [concurrency:: CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) , aby zapewnić dostęp do bieżącego harmonogramu. Bieżący harmonogram dla jednego kontekstu może różnić się od bieżącego harmonogramu w innym kontekście. Środowisko uruchomieniowe nie zapewnia reprezentacji bieżącego harmonogramu na poziomie procesu.

Zazwyczaj Klasa `CurrentScheduler` jest używana w celu uzyskania dostępu do bieżącego harmonogramu. Klasa `Scheduler` jest przydatna, gdy trzeba zarządzać harmonogramem, który nie jest bieżącym.

W poniższych sekcjach opisano sposób tworzenia wystąpienia harmonogramu i zarządzania nim. Aby zapoznać się z kompletnym przykładem, który ilustruje te zadania, zobacz [How to: Manage a Scheduler instance](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).

[[Top](#top)]

## <a name="creating"></a>Tworzenie wystąpienia harmonogramu

Istnieją trzy sposoby tworzenia `Scheduler` obiektu:

- Jeśli harmonogram nie istnieje, środowisko uruchomieniowe tworzy domyślny harmonogram dla Ciebie, gdy używasz funkcji środowiska uruchomieniowego, na przykład algorytmu równoległego, aby wykonać pracę. Domyślny harmonogram jest bieżącym harmonogramem dla kontekstu inicjującego pracę równoległą.

- [Concurrency:: CurrentScheduler:: Create](reference/currentscheduler-class.md#create) Metoda tworzy obiekt `Scheduler`, który używa określonych zasad i kojarzy ten harmonogram z bieżącym kontekstem.

- Metoda [concurrency:: Scheduler:: Create](reference/scheduler-class.md#create) tworzy obiekt `Scheduler`, który używa określonych zasad, ale nie kojarzy go z bieżącym kontekstem.

Umożliwienie środowisku uruchomieniowemu tworzenia domyślnego harmonogramu umożliwia wszystkim współbieżnym zadaniom współużytkowanie tego samego harmonogramu. Zazwyczaj funkcje dostarczone przez [bibliotekę wzorców równoległych](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) lub [asynchronicznej biblioteki agentów](../../parallel/concrt/asynchronous-agents-library.md) są używane do wykonywania równoległych zadań. W związku z tym nie musisz bezpośrednio korzystać z harmonogramu, aby kontrolować jego zasady lub okres istnienia. W przypadku korzystania z biblioteki PPL lub agentów środowisko uruchomieniowe tworzy domyślny harmonogram, jeśli nie istnieje, i ustawia go jako bieżący harmonogram dla każdego kontekstu. Gdy tworzysz harmonogram i ustawisz go jako bieżący harmonogram, środowisko uruchomieniowe użyje tego harmonogramu do zaplanowania zadań. Utwórz dodatkowe wystąpienia usługi Scheduler tylko wtedy, gdy wymagane są określone zasady planowania. Aby uzyskać więcej informacji na temat zasad skojarzonych z harmonogramem, zobacz [zasady usługi Scheduler](../../parallel/concrt/scheduler-policies.md).

[[Top](#top)]

## <a name="managing"></a>Zarządzanie okresem istnienia wystąpienia harmonogramu

Środowisko uruchomieniowe używa mechanizmu zliczania odwołań do kontrolowania okresu istnienia `Scheduler` obiektów.

W przypadku tworzenia obiektu `Scheduler` przy użyciu metody `CurrentScheduler::Create` lub metody `Scheduler::Create` środowisko uruchomieniowe ustawia początkową liczbę odwołań tego harmonogramu do jednego. Środowisko uruchomieniowe zwiększa liczbę odwołań w przypadku wywołania metody [concurrency:: Scheduler:: Attach](reference/scheduler-class.md#attach) . Metoda `Scheduler::Attach` kojarzy obiekt `Scheduler` wraz z bieżącym kontekstem. Staje się to bieżącym harmonogramem. Po wywołaniu metody `CurrentScheduler::Create` środowisko uruchomieniowe tworzy obiekt `Scheduler` i dołącza go do bieżącego kontekstu (i ustawia liczbę odwołań na jeden). Można również użyć metody [concurrency:: Scheduler:: Reference](reference/scheduler-class.md#reference) , aby zwiększyć liczbę odwołań obiektu `Scheduler`.

Środowisko uruchomieniowe zmniejsza liczbę odwołań w przypadku wywołania metody [concurrency:: CurrentScheduler::D etach](reference/currentscheduler-class.md#detach) w celu odłączenia bieżącego harmonogramu lub wywołania metody [concurrency:: Scheduler:: Release](reference/scheduler-class.md#release) . Gdy liczba odwołań osiągnie wartość zero, środowisko uruchomieniowe niszczy obiekt `Scheduler` po zakończeniu wszystkich zaplanowanych zadań. Uruchomione zadanie może zwiększyć liczbę odwołań bieżącego harmonogramu. W związku z tym, jeśli licznik odwołań osiągnie wartość zero, a zadanie zwiększy liczbę odwołań, środowisko uruchomieniowe nie niszczy obiektu `Scheduler`, dopóki liczba odwołań nie osiągnie wartości zero i zakończy się wszystkie zadania.

Środowisko uruchomieniowe utrzymuje wewnętrzny stos `Scheduler` obiektów dla każdego kontekstu. Po wywołaniu metody `Scheduler::Attach` lub `CurrentScheduler::Create`, środowisko uruchomieniowe wypchnięcie tego obiektu `Scheduler` na stosie dla bieżącego kontekstu. Staje się to bieżącym harmonogramem. Gdy wywołasz `CurrentScheduler::Detach`, środowisko uruchomieniowe wychodzi z bieżącego harmonogramu ze stosu dla bieżącego kontekstu i ustawia poprzednią rolę w bieżącym harmonogramie.

Środowisko uruchomieniowe zapewnia kilka sposobów zarządzania okresem istnienia wystąpienia harmonogramu. W poniższej tabeli przedstawiono odpowiednią metodę, która powoduje wydanie lub odłączenie harmonogramu od bieżącego kontekstu dla każdej metody, która tworzy lub dołącza harmonogram do bieżącego kontekstu.

|Utwórz lub Dołącz metodę|Metoda Release lub odłącz|
|-----------------------------|------------------------------|
|`CurrentScheduler::Create`|`CurrentScheduler::Detach`|
|`Scheduler::Create`|`Scheduler::Release`|
|`Scheduler::Attach`|`CurrentScheduler::Detach`|
|`Scheduler::Reference`|`Scheduler::Release`|

Wywołanie niewłaściwej metody Release lub odłącz powoduje nieokreślone zachowanie w czasie wykonywania.

W przypadku korzystania z funkcji, na przykład PPL, która powoduje, że środowisko uruchomieniowe może utworzyć domyślny harmonogram dla Ciebie, nie zwalniaj ani nie odłączaj tego harmonogramu. Środowisko uruchomieniowe zarządza okresem istnienia dowolnego tworzonego harmonogramu.

Ponieważ środowisko uruchomieniowe nie niszczy obiektu `Scheduler` przed ukończeniem wszystkich zadań, można użyć metody [concurrency:: Scheduler:: RegisterShutdownEvent —](reference/scheduler-class.md#registershutdownevent) lub [concurrency:: CurrentScheduler:: RegisterShutdownEvent —](reference/currentscheduler-class.md#registershutdownevent) , aby otrzymać powiadomienie, gdy obiekt `Scheduler` zostanie zniszczony. Jest to przydatne, gdy trzeba czekać na każde zadanie zaplanowane przez obiekt `Scheduler`.

[[Top](#top)]

## <a name="features"></a>Metody i funkcje

Ta sekcja zawiera podsumowanie ważnych metod klas `CurrentScheduler` i `Scheduler`.

Zastanów się `CurrentScheduler`j klasy jako pomocnika do tworzenia harmonogramu do użycia w bieżącym kontekście. Klasa `Scheduler` pozwala kontrolować harmonogram, który należy do innego kontekstu.

W poniższej tabeli przedstawiono ważne metody, które są zdefiniowane przez klasę `CurrentScheduler`.

|Metoda|Opis|
|------------|-----------------|
|[Tworzenie](reference/currentscheduler-class.md#create)|Tworzy obiekt `Scheduler`, który używa określonych zasad i kojarzy go z bieżącym kontekstem.|
|[Get](reference/currentscheduler-class.md#get)|Pobiera wskaźnik do obiektu `Scheduler`, który jest skojarzony z bieżącym kontekstem. Ta metoda nie zwiększa liczby odwołań obiektu `Scheduler`.|
|[Detach](reference/currentscheduler-class.md#detach)|Odłącza bieżący harmonogram od bieżącego kontekstu i ustawia poprzednią rolę w bieżącym harmonogramie.|
|[RegisterShutdownEvent —](reference/currentscheduler-class.md#registershutdownevent)|Rejestruje zdarzenie, które jest ustawiane przez środowisko uruchomieniowe, gdy bieżący harmonogram został zniszczony.|
|[CreateScheduleGroup —](reference/currentscheduler-class.md#createschedulegroup)|Tworzy obiekt [concurrency:: Schedule](../../parallel/concrt/reference/schedulegroup-class.md) w bieżącym harmonogramie.|
|[ScheduleTask —](reference/currentscheduler-class.md#scheduletask)|Dodaje lekkie zadanie do kolejki planowania bieżącego harmonogramu.|
|[GetPolicy —](reference/currentscheduler-class.md#getpolicy)|Pobiera kopię zasad, która jest skojarzona z bieżącym harmonogramem.|

W poniższej tabeli przedstawiono ważne metody, które są zdefiniowane przez klasę `Scheduler`.

|Metoda|Opis|
|------------|-----------------|
|[Tworzenie](reference/scheduler-class.md#create)|Tworzy obiekt `Scheduler`, który korzysta z określonych zasad.|
|[Attach](reference/scheduler-class.md#attach)|Kojarzy obiekt `Scheduler` wraz z bieżącym kontekstem.|
|[Dokumentacja](reference/scheduler-class.md#reference)|Zwiększa licznik odwołań obiektu `Scheduler`.|
|[Wersja](reference/scheduler-class.md#release)|Zmniejsza licznik odwołań obiektu `Scheduler`.|
|[RegisterShutdownEvent —](reference/scheduler-class.md#registershutdownevent)|Rejestruje zdarzenie, które jest ustawiane przez środowisko uruchomieniowe podczas zniszczenia obiektu `Scheduler`.|
|[CreateScheduleGroup —](reference/scheduler-class.md#createschedulegroup)|Tworzy obiekt [concurrency:: Schedule](../../parallel/concrt/reference/schedulegroup-class.md) w obiekcie `Scheduler`.|
|[ScheduleTask —](reference/scheduler-class.md#scheduletask)|Planuje lekkie zadanie z obiektu `Scheduler`.|
|[GetPolicy —](reference/scheduler-class.md#getpolicy)|Pobiera kopię zasad, która jest skojarzona z obiektem `Scheduler`.|
|[SetDefaultSchedulerPolicy —](reference/scheduler-class.md#setdefaultschedulerpolicy)|Ustawia zasady dla środowiska uruchomieniowego, które mają być używane podczas tworzenia domyślnego harmonogramu.|
|[ResetDefaultSchedulerPolicy —](reference/scheduler-class.md#resetdefaultschedulerpolicy)|Przywraca zasady domyślne, które były aktywne przed wywołaniem `SetDefaultSchedulerPolicy`. Jeśli po wykonaniu tego wywołania zostanie utworzony domyślny harmonogram, środowisko uruchomieniowe użyje domyślnych ustawień zasad w celu utworzenia harmonogramu.|

[[Top](#top)]

## <a name="example"></a>Przyklad

Aby zapoznać się z podstawowymi przykładami tworzenia wystąpienia harmonogramu i zarządzania nim, zobacz [How to: Manage a Scheduler instance](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).

## <a name="see-also"></a>Zobacz też

[Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Instrukcje: zarządzanie wystąpieniem harmonogramu](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[Zasady harmonogramu](../../parallel/concrt/scheduler-policies.md)<br/>
[Grupy harmonogramu](../../parallel/concrt/schedule-groups.md)
