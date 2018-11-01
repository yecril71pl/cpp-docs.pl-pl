---
title: Struktura IScheduler
ms.date: 11/04/2016
f1_keywords:
- IScheduler
- CONCRTRM/concurrency::IScheduler
- CONCRTRM/concurrency::IScheduler::IScheduler::AddVirtualProcessors
- CONCRTRM/concurrency::IScheduler::IScheduler::GetId
- CONCRTRM/concurrency::IScheduler::IScheduler::GetPolicy
- CONCRTRM/concurrency::IScheduler::IScheduler::NotifyResourcesExternallyBusy
- CONCRTRM/concurrency::IScheduler::IScheduler::NotifyResourcesExternallyIdle
- CONCRTRM/concurrency::IScheduler::IScheduler::RemoveVirtualProcessors
- CONCRTRM/concurrency::IScheduler::IScheduler::Statistics
helpviewer_keywords:
- IScheduler structure
ms.assetid: 471de85a-2b1a-4b6d-ab81-2eff2737161e
ms.openlocfilehash: dd280884ab106bcf878b06c94e2ea3d0d99be2e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603220"
---
# <a name="ischeduler-structure"></a>Struktura IScheduler

Interfejs abstrakcję harmonogram pracy. Menedżer zasobów w środowisku uruchomieniowym współbieżności używa ten interfejs do komunikacji z harmonogramów pracy.

## <a name="syntax"></a>Składnia

```
struct IScheduler;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IScheduler::AddVirtualProcessors](#addvirtualprocessors)|Udostępnia harmonogramu z zestawem korzeni procesora wirtualnego do jego użycia. Każdy `IVirtualProcessorRoot` interfejs reprezentuje prawo do wykonania jednego wątku, które może wykonywać pracę w imieniu usługi scheduler.|
|[IScheduler::GetId](#getid)|Zwraca unikatowy identyfikator dla harmonogramu.|
|[IScheduler::GetPolicy](#getpolicy)|Zwraca kopię obiektu zasadę harmonogramu. Aby uzyskać więcej informacji na temat zasad harmonogramu, zobacz [SchedulerPolicy](schedulerpolicy-class.md).|
|[IScheduler::NotifyResourcesExternallyBusy](#notifyresourcesexternallybusy)|Powiadamia ten harmonogram, który wątków sprzętu reprezentowany przez zestaw korzeni procesora wirtualnego w tablicy `ppVirtualProcessorRoots` są obecnie używane przez inne transfery danych.|
|[Ischeduler::notifyresourcesexternallyidle —](#notifyresourcesexternallyidle)|Powiadamia ten harmonogram, który wątków sprzętu reprezentowany przez zestaw korzeni procesora wirtualnego w tablicy `ppVirtualProcessorRoots` nie są używane przez inne transfery danych.|
|[Ischeduler::removevirtualprocessors —](#removevirtualprocessors)|Powoduje zainicjowanie usuwania głównych procesorów wirtualnych, które wcześniej zostały przydzielone do tego harmonogramu.|
|[Ischeduler::statistics —](#statistics)|Zawiera informacje dotyczące stawek przybycia i ukończenia zadania w celu zmiany długości kolejki dla harmonogramu.|

## <a name="remarks"></a>Uwagi

Przed zaimplementowaniem Niestandardowy harmonogram, który komunikuje się z usługą Resource Manager, należy podać implementacja `IScheduler` interfejsu. Ten interfejs jest jeden z punktów końcowych dwukierunkowy kanał komunikacji między harmonogramu i Menedżera zasobów. Drugi punkt końcowy jest reprezentowany przez `IResourceManager` i `ISchedulerProxy` interfejsów, które są implementowane przez Menedżera zasobów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IScheduler`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Namespace:** współbieżności

##  <a name="addvirtualprocessors"></a>  Ischeduler::addvirtualprocessors — metoda

Udostępnia harmonogramu z zestawem korzeni procesora wirtualnego do jego użycia. Każdy `IVirtualProcessorRoot` interfejs reprezentuje prawo do wykonania jednego wątku, które może wykonywać pracę w imieniu usługi scheduler.

```
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Tablica `IVirtualProcessorRoot` interfejsów reprezentujący Procesor wirtualny obiektów głównych dodawany do harmonogramu.

*Liczba*<br/>
Liczba `IVirtualProcessorRoot` interfejsów w tablicy.

### <a name="remarks"></a>Uwagi

Menedżer zasobów wywołuje `AddVirtualProcessor` metodę, aby udzielić początkowy zestaw głównych procesorów wirtualnych do harmonogramu. Można go również wywoływać metody w celu dodania do harmonogramu korzeni procesora wirtualnego, podczas jego rebalances zasobów między transfery danych.

##  <a name="getid"></a>  Ischeduler::getid — metoda

Zwraca unikatowy identyfikator dla harmonogramu.

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator unikatowy liczby całkowitej.

### <a name="remarks"></a>Uwagi

Należy używać [getschedulerid —](concurrency-namespace-functions.md) funkcję, aby uzyskać unikatowy identyfikator obiektu, który implementuje `IScheduler` interfejsu, zanim użyjesz interfejsu jako parametr do metody dostarczone przez Menedżera zasobów. Powinna zwrócić element tego samego identyfikatora po `GetId` wywołaniu funkcji.

Identyfikator pochodzi z innego źródła może spowodować niezdefiniowane zachowanie.

##  <a name="getpolicy"></a>  Ischeduler::getpolicy — metoda

Zwraca kopię obiektu zasadę harmonogramu. Aby uzyskać więcej informacji na temat zasad harmonogramu, zobacz [SchedulerPolicy](schedulerpolicy-class.md).

```
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Kopia zasadę harmonogramu.

##  <a name="notifyresourcesexternallybusy"></a>  Ischeduler::notifyresourcesexternallybusy — metoda

Powiadamia ten harmonogram, który wątków sprzętu reprezentowany przez zestaw korzeni procesora wirtualnego w tablicy `ppVirtualProcessorRoots` są obecnie używane przez inne transfery danych.

```
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Tablica `IVirtualProcessorRoot` interfejsów skojarzonych z wątków sprzętu, na których inne transfery danych stały się zajęty.

*Liczba*<br/>
Liczba `IVirtualProcessorRoot` interfejsów w tablicy.

### <a name="remarks"></a>Uwagi

Istnieje możliwość dla wątku określonego sprzętu, który ma być przypisane do wielu harmonogramów w tym samym czasie. Jedną z przyczyn tego może być, że nie istnieją mała liczba wątków sprzętu w systemie, aby spełniać minimalne współbieżności dla wszystkich harmonogramów bez udostępniania zasobów. Inną możliwością jest, że zasoby tymczasowo są przypisywane do inne transfery danych, podczas będąca właścicielem harmonogram nie używa ich, za pomocą jego korzeni procesora wirtualnego wątek sprzętu dezaktywowane.

Poziom subskrypcji wątku sprzętu jest oznaczona liczba wątków subskrybowanego i aktywowane korzeni procesora wirtualnego skojarzonego z tym wątkiem sprzętu. Z punktu widzenia określonego harmonogramu poziom subskrypcji zewnętrzny wątek sprzętu jest częścią subskrypcji, którą Współtworzenie inne transfery danych. Powiadomienia, że zasoby są zajęte zewnętrznie są wysyłane do harmonogramu, gdy poziom subskrypcji zewnętrzny wątek sprzętu porusza się od zera dodatnia terytorium.

Powiadomienia za pośrednictwem tej metody są wysyłane tylko do których mają zasady gdzie wartość `MinConcurrency` klucz zasad jest równa wartości dla `MaxConcurrency` klucz zasad. Aby uzyskać więcej informacji na temat zasad harmonogramu, zobacz [SchedulerPolicy](schedulerpolicy-class.md).

Harmonogram, który jest uprawniony do powiadomienia pobiera zestaw powiadomień w początkowej podczas jego tworzenia, powiadamiając go, czy zasoby, które właśnie zostało przypisane zewnętrznie zajęta lub bezczynności.

##  <a name="notifyresourcesexternallyidle"></a>  Ischeduler::notifyresourcesexternallyidle — metoda

Powiadamia ten harmonogram, który wątków sprzętu reprezentowany przez zestaw korzeni procesora wirtualnego w tablicy `ppVirtualProcessorRoots` nie są używane przez inne transfery danych.

```
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Tablica `IVirtualProcessorRoot` interfejsów skojarzonych z wątków sprzętu, na których inne transfery danych mają przejdzie w stan bezczynności.

*Liczba*<br/>
Liczba `IVirtualProcessorRoot` interfejsów w tablicy.

### <a name="remarks"></a>Uwagi

Istnieje możliwość dla wątku określonego sprzętu, który ma być przypisane do wielu harmonogramów w tym samym czasie. Jedną z przyczyn tego może być, że nie istnieją mała liczba wątków sprzętu w systemie, aby spełniać minimalne współbieżności dla wszystkich harmonogramów bez udostępniania zasobów. Inną możliwością jest, że zasoby tymczasowo są przypisywane do inne transfery danych, podczas będąca właścicielem harmonogram nie używa ich, za pomocą jego korzeni procesora wirtualnego wątek sprzętu dezaktywowane.

Poziom subskrypcji wątku sprzętu jest oznaczona liczba wątków subskrybowanego i aktywowane korzeni procesora wirtualnego skojarzonego z tym wątkiem sprzętu. Z punktu widzenia określonego harmonogramu poziom subskrypcji zewnętrzny wątek sprzętu jest częścią subskrypcji, którą Współtworzenie inne transfery danych. Powiadomienia, że zasoby są zajęte zewnętrznie są wysyłane do harmonogramu, gdy poziom subskrypcji zewnętrzny wątek sprzętu znajduje się na wartość zero z poprzednią wartość dodatnią.

Powiadomienia za pośrednictwem tej metody są wysyłane tylko do których mają zasady gdzie wartość `MinConcurrency` klucz zasad jest równa wartości dla `MaxConcurrency` klucz zasad. Aby uzyskać więcej informacji na temat zasad harmonogramu, zobacz [SchedulerPolicy](schedulerpolicy-class.md).

Harmonogram, który jest uprawniony do powiadomienia pobiera zestaw powiadomień w początkowej podczas jego tworzenia, powiadamiając go, czy zasoby, które właśnie zostało przypisane zewnętrznie zajęta lub bezczynności.

##  <a name="removevirtualprocessors"></a>  Ischeduler::removevirtualprocessors — metoda

Powoduje zainicjowanie usuwania głównych procesorów wirtualnych, które wcześniej zostały przydzielone do tego harmonogramu.

```
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Tablica `IVirtualProcessorRoot` interfejsów reprezentujący korzeni procesora wirtualnego, który ma zostać usunięty.

*Liczba*<br/>
Liczba `IVirtualProcessorRoot` interfejsów w tablicy.

### <a name="remarks"></a>Uwagi

Menedżer zasobów wywołuje `RemoveVirtualProcessors` metody, aby odzyskać zbiór korzeni procesora wirtualnego z harmonogramu. Harmonogram oczekuje się, aby wywołać [Usuń](iexecutionresource-structure.md#remove) metoda dla każdego interfejsu, gdy wszystko będzie gotowe, za pomocą korzeni procesora wirtualnego. Nie używaj `IVirtualProcessorRoot` interfejsu po wywołanych `Remove` metody na nim.

Parametr `ppVirtualProcessorRoots` wskazuje na tablicy interfejsów. Między zestawem głównych procesorów wirtualnych do usunięcia obiektów głównych nigdy nie został aktywowany mogą być zwrócone bezpośrednio za pomocą `Remove` metody. Elementy główne, które zostały aktywowane i są albo wykonywanej pracy, lub został zdezaktywowany i oczekuje na pracy zostanie dostarczona, ma zostać zwrócony asynchronicznie. Harmonogram musi zapewnić każda próba usunięcia procesora wirtualnego katalogu głównego tak szybko, jak to możliwe. Opóźniania usuwania głównych procesorów wirtualnych może spowodować niezamierzone nadsubskrypcji w obrębie harmonogramu.

##  <a name="statistics"></a>  Ischeduler::statistics — metoda

Zawiera informacje dotyczące stawek przybycia i ukończenia zadania w celu zmiany długości kolejki dla harmonogramu.

```
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```

### <a name="parameters"></a>Parametry

*pTaskCompletionRate*<br/>
Liczba zadań wykonanych przez harmonogram od czasu ostatniego wywołania tej metody.

*pTaskArrivalRate*<br/>
Liczba zadań, które zostały dostarczone w ramach harmonogramu zadań od momentu ostatniego wywołania tej metody.

*pNumberOfTasksEnqueued*<br/>
Całkowita liczba zadań we wszystkich kolejkach harmonogramu.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez Menedżera zasobów w celu zbierania statystyk dla harmonogramu. Dane statystyczne zebrane w tym miejscu będzie służyć do kierowania algorytmy dynamiczne opinii można określić, kiedy należy przypisać więcej zasobów do harmonogramu i natychmiast wykonać zasobów. Wartości podane przez harmonogram może być optymistyczne i nie musisz dokładnie odzwierciedlają bieżącą liczbę.

Należy zaimplementować tę metodę, jeśli chcesz, aby Menedżer zasobów na potrzeby swoją opinię na temat takich zadań jako zadanie przybycia ustalić sposób równoważenia zasobów między harmonogramu i innych harmonogramów zarejestrowane przy użyciu usługi Resource Manager. Jeśli wybierzesz nie zebrać dane statystyczne, można ustawić klucza zasad `DynamicProgressFeedback` wartość `DynamicProgressFeedbackDisabled` w zasady usługi harmonogramu i zasobów Manager nie będzie wywołania tej metody na harmonogramu.

W przypadku braku informacji statystycznych Menedżer zasobów użyje poziomy subskrypcji wątków sprzętu podjąć decyzje dotyczące zasobów alokacji i migracji. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [iexecutionresource::currentsubscriptionlevel —](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[SchedulerPolicy, klasa](schedulerpolicy-class.md)<br/>
[IExecutionContext, struktura](iexecutioncontext-structure.md)<br/>
[IThreadProxy, struktura](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot, struktura](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager, struktura](iresourcemanager-structure.md)
