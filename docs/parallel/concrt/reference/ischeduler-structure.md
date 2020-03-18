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
ms.openlocfilehash: cd7b04b0dc5ca1bc496ce87a6459d00ed5813bf7
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422221"
---
# <a name="ischeduler-structure"></a>Struktura IScheduler

Interfejs do abstrakcji harmonogramu pracy. Menedżer zasobów środowisko uruchomieniowe współbieżności używa tego interfejsu do komunikowania się z harmonogramami służbowymi.

## <a name="syntax"></a>Składnia

```cpp
struct IScheduler;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[IScheduler:: AddVirtualProcessors —](#addvirtualprocessors)|Udostępnia harmonogram z zestawem katalogów głównych procesorów wirtualnych do użytku. Każdy interfejs `IVirtualProcessorRoot` reprezentuje prawo do wykonania pojedynczego wątku, który może wykonywać pracę w imieniu harmonogramu.|
|[IScheduler:: GetId —](#getid)|Zwraca unikatowy identyfikator dla harmonogramu.|
|[IScheduler:: GetPolicy](#getpolicy)|Zwraca kopię zasad harmonogramu. Aby uzyskać więcej informacji na temat zasad usługi Scheduler, zobacz [SchedulerPolicy](schedulerpolicy-class.md).|
|[IScheduler:: NotifyResourcesExternallyBusy —](#notifyresourcesexternallybusy)|Powiadamia ten harmonogram, że wątki sprzętowe reprezentowane przez zestaw katalogów głównych procesorów wirtualnych w tablicy `ppVirtualProcessorRoots` są teraz używane przez innych harmonogramów.|
|[IScheduler:: NotifyResourcesExternallyIdle —](#notifyresourcesexternallyidle)|Powiadamia ten harmonogram, że wątki sprzętowe reprezentowane przez zbiór katalogów głównych procesorów wirtualnych w tablicy `ppVirtualProcessorRoots` nie są używane przez inne harmonogramy.|
|[IScheduler:: RemoveVirtualProcessors —](#removevirtualprocessors)|Inicjuje Usuwanie katalogów głównych procesorów wirtualnych, które zostały wcześniej przydzielono do tego harmonogramu.|
|[IScheduler:: Statistics](#statistics)|Zawiera informacje dotyczące szybkości przybycia i ukończenia zadania oraz zmiany długości kolejki dla harmonogramu.|

## <a name="remarks"></a>Uwagi

W przypadku wdrażania niestandardowego harmonogramu, który komunikuje się z Menedżer zasobów, należy podać implementację interfejsu `IScheduler`. Ten interfejs jest jednym końcem dwukierunkowego kanału komunikacji między harmonogramem i Menedżer zasobów. Druga końcowa jest reprezentowana przez `IResourceManager` i `ISchedulerProxy` interfejsów, które są implementowane przez Menedżer zasobów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IScheduler`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm. h

**Przestrzeń nazw:** współbieżność

## <a name="addvirtualprocessors"></a>IScheduler:: AddVirtualProcessors —, Metoda

Udostępnia harmonogram z zestawem katalogów głównych procesorów wirtualnych do użytku. Każdy interfejs `IVirtualProcessorRoot` reprezentuje prawo do wykonania pojedynczego wątku, który może wykonywać pracę w imieniu harmonogramu.

```cpp
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Tablica interfejsów `IVirtualProcessorRoot` reprezentujących katalogi główne procesora wirtualnego dodawane do harmonogramu.

*count*<br/>
Liczba interfejsów `IVirtualProcessorRoot` w tablicy.

### <a name="remarks"></a>Uwagi

Menedżer zasobów wywołuje metodę `AddVirtualProcessor` w celu przyznania wstępnego zestawu katalogów głównych procesorów wirtualnych do harmonogramu. Może również wywołać metodę dodawania katalogów głównych procesorów wirtualnych do harmonogramu w przypadku zrównoważenia zasobów między harmonogramami.

## <a name="getid"></a>IScheduler:: GetId —, Metoda

Zwraca unikatowy identyfikator dla harmonogramu.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Unikatowy identyfikator liczby całkowitej.

### <a name="remarks"></a>Uwagi

Należy użyć funkcji [GetSchedulerId —](concurrency-namespace-functions.md) , aby uzyskać unikatowy identyfikator obiektu, który implementuje interfejs `IScheduler`, przed użyciem interfejsu jako parametru do metod dostarczonych przez Menedżer zasobów. Po wywołaniu funkcji `GetId` należy zwrócić ten sam identyfikator.

Identyfikator uzyskany z innego źródła może spowodować niezdefiniowane zachowanie.

## <a name="getpolicy"></a>IScheduler:: GetPolicy — Metoda

Zwraca kopię zasad harmonogramu. Aby uzyskać więcej informacji na temat zasad usługi Scheduler, zobacz [SchedulerPolicy](schedulerpolicy-class.md).

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Kopia zasad usługi Scheduler.

## <a name="notifyresourcesexternallybusy"></a>IScheduler:: NotifyResourcesExternallyBusy —, Metoda

Powiadamia ten harmonogram, że wątki sprzętowe reprezentowane przez zestaw katalogów głównych procesorów wirtualnych w tablicy `ppVirtualProcessorRoots` są teraz używane przez innych harmonogramów.

```cpp
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Tablica interfejsów `IVirtualProcessorRoot` skojarzonych ze wątkami sprzętowymi, w których inne harmonogramy stają się zajęte.

*count*<br/>
Liczba interfejsów `IVirtualProcessorRoot` w tablicy.

### <a name="remarks"></a>Uwagi

Istnieje możliwość przypisania określonego wątku sprzętowego do wielu harmonogramów w tym samym czasie. Jedną z przyczyn tego problemu może być brak wystarczającej liczby wątków sprzętowych w systemie w celu zaspokojenia minimalnych współbieżności dla wszystkich harmonogramów bez udostępniania zasobów. Kolejną możliwością jest to, że zasoby są tymczasowo przypisywane do innych harmonogramów, gdy nie są one używane przez tego samego procesora wirtualnego w ramach tego wątku sprzętowego.

Poziom subskrypcji wątku sprzętowego jest określany na podstawie liczby wątków subskrybowanych i aktywowanych katalogów głównych procesora wirtualnego skojarzonych z tym wątkiem sprzętowym. Z punktu widzenia określonego harmonogramu, zewnętrzny poziom subskrypcji wątku sprzętowego jest częścią subskrypcji, do której należy program. Powiadomienia, które zasoby są zajęte zewnętrznie, są wysyłane do harmonogramu, gdy poziom subskrypcji zewnętrznej dla wątku sprzętowego przesunie się z zera na pozytywne terytorium.

Powiadomienia za pośrednictwem tej metody są wysyłane tylko do harmonogramów mających zasady, w których wartość klucza zasad `MinConcurrency` jest równa wartości klucza zasad `MaxConcurrency`. Aby uzyskać więcej informacji na temat zasad usługi Scheduler, zobacz [SchedulerPolicy](schedulerpolicy-class.md).

Harmonogram, który kwalifikuje się do powiadomień, Pobiera zestaw początkowych powiadomień podczas jego tworzenia, informując o tym, czy zasoby, które zostały właśnie przypisane, są z zewnątrz zajęte lub bezczynne.

## <a name="notifyresourcesexternallyidle"></a>IScheduler:: NotifyResourcesExternallyIdle —, Metoda

Powiadamia ten harmonogram, że wątki sprzętowe reprezentowane przez zbiór katalogów głównych procesorów wirtualnych w tablicy `ppVirtualProcessorRoots` nie są używane przez inne harmonogramy.

```cpp
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Tablica interfejsów `IVirtualProcessorRoot` skojarzonych ze wątkami sprzętowymi, w których inne harmonogramy staną się bezczynne.

*count*<br/>
Liczba interfejsów `IVirtualProcessorRoot` w tablicy.

### <a name="remarks"></a>Uwagi

Istnieje możliwość przypisania określonego wątku sprzętowego do wielu harmonogramów w tym samym czasie. Jedną z przyczyn tego problemu może być brak wystarczającej liczby wątków sprzętowych w systemie w celu zaspokojenia minimalnych współbieżności dla wszystkich harmonogramów bez udostępniania zasobów. Kolejną możliwością jest to, że zasoby są tymczasowo przypisywane do innych harmonogramów, gdy nie są one używane przez tego samego procesora wirtualnego w ramach tego wątku sprzętowego.

Poziom subskrypcji wątku sprzętowego jest określany na podstawie liczby wątków subskrybowanych i aktywowanych katalogów głównych procesora wirtualnego skojarzonych z tym wątkiem sprzętowym. Z punktu widzenia określonego harmonogramu, zewnętrzny poziom subskrypcji wątku sprzętowego jest częścią subskrypcji, do której należy program. Powiadomienia, które zasoby są zajęte zewnętrznie, są wysyłane do harmonogramu, gdy poziom subskrypcji zewnętrznej dla wątku sprzętowego przypada na zero od poprzedniej wartości dodatniej.

Powiadomienia za pośrednictwem tej metody są wysyłane tylko do harmonogramów mających zasady, w których wartość klucza zasad `MinConcurrency` jest równa wartości klucza zasad `MaxConcurrency`. Aby uzyskać więcej informacji na temat zasad usługi Scheduler, zobacz [SchedulerPolicy](schedulerpolicy-class.md).

Harmonogram, który kwalifikuje się do powiadomień, Pobiera zestaw początkowych powiadomień podczas jego tworzenia, informując o tym, czy zasoby, które zostały właśnie przypisane, są z zewnątrz zajęte lub bezczynne.

## <a name="removevirtualprocessors"></a>IScheduler:: RemoveVirtualProcessors —, Metoda

Inicjuje Usuwanie katalogów głównych procesorów wirtualnych, które zostały wcześniej przydzielono do tego harmonogramu.

```cpp
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Tablica interfejsów `IVirtualProcessorRoot` reprezentujących katalogi główne procesora wirtualnego do usunięcia.

*count*<br/>
Liczba interfejsów `IVirtualProcessorRoot` w tablicy.

### <a name="remarks"></a>Uwagi

Menedżer zasobów wywołuje metodę `RemoveVirtualProcessors` w celu przywrócenia zestawu katalogów głównych procesorów wirtualnych z harmonogramu. Harmonogram powinien wywołać metodę [Remove](iexecutionresource-structure.md#remove) dla każdego interfejsu, gdy zostanie on wykonany przy użyciu katalogów głównych procesora wirtualnego. Nie należy używać interfejsu `IVirtualProcessorRoot` po wywołaniu metody `Remove`.

Parametr `ppVirtualProcessorRoots` wskazuje tablicę interfejsów. Poza zestawem katalogów głównych procesorów wirtualnych, które mają zostać usunięte, elementy główne nigdy nie zostały aktywowane mogą być zwracane natychmiast przy użyciu metody `Remove`. Elementy główne, które zostały aktywowane i są wykonywane w pracy lub zostały zdezaktywowane i oczekują na nadejście pracy, powinny być zwracane asynchronicznie. Harmonogram musi wykonać każdą próbę usunięcia katalogu głównego wirtualnego procesora tak szybko, jak to możliwe. Opóźnienie usunięcia katalogów głównych procesorów wirtualnych może skutkować niezamierzoną subskrypcją w ramach harmonogramu.

## <a name="statistics"></a>IScheduler:: Statistics — Metoda

Zawiera informacje dotyczące szybkości przybycia i ukończenia zadania oraz zmiany długości kolejki dla harmonogramu.

```cpp
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```

### <a name="parameters"></a>Parametry

*pTaskCompletionRate*<br/>
Liczba zadań ukończonych przez harmonogram od momentu ostatniego wywołania tej metody.

*pTaskArrivalRate*<br/>
Liczba zadań, które dotarły do harmonogramu od momentu ostatniego wywołania tej metody.

*pNumberOfTasksEnqueued*<br/>
Całkowita liczba zadań we wszystkich kolejkach harmonogramu.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez Menedżer zasobów w celu zbierania statystyk dla harmonogramu. Przedstawione tutaj dane statystyczne zostaną użyte do określenia dynamicznych algorytmów przesyłania opinii, aby określić, kiedy należy przypisać więcej zasobów do harmonogramu i kiedy należy zająć się zasobami. Wartości podane w harmonogramie mogą być optymistyczne i niekoniecznie odzwierciedlać aktualną liczbę.

Ta metoda powinna zostać zaimplementowana, jeśli chcesz, aby Menedżer zasobów do przesyłania opinii na temat takich czynności jak w przypadku przybycia zadania, aby określić, jak zrównoważyć zasób między harmonogramem i innymi harmonogramami zarejestrowanymi w Menedżer zasobów. Jeśli zdecydujesz się nie zbierać statystyk, możesz ustawić klucz zasad `DynamicProgressFeedback` na wartość `DynamicProgressFeedbackDisabled` w zasadach harmonogramu, a Menedżer zasobów nie wywoła tej metody w harmonogramie.

W przypadku braku informacji statystycznych, Menedżer zasobów będzie używać poziomów subskrypcji wątków sprzętowych do podejmowania decyzji dotyczących alokacji zasobów i migracji. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource:: CurrentSubscriptionLevel —](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[PolicyElementKey —](concurrency-namespace-enums.md)<br/>
[SchedulerPolicy, klasa](schedulerpolicy-class.md)<br/>
[IExecutionContext, struktura](iexecutioncontext-structure.md)<br/>
[IThreadProxy, struktura](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot, struktura](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager, struktura](iresourcemanager-structure.md)
