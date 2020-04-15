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
ms.openlocfilehash: ccd82b5c5112bc322717f2b58d79d4c8f34f5bbd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368175"
---
# <a name="ischeduler-structure"></a>Struktura IScheduler

Interfejs do abstrakcji harmonogramu pracy. Menedżer zasobów środowiska wykonawczego współbieżności używa tego interfejsu do komunikowania się z harmonogramami pracy.

## <a name="syntax"></a>Składnia

```cpp
struct IScheduler;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IScheduler::AddVirtualProcessors](#addvirtualprocessors)|Udostępnia harmonogram z zestawem katalogów głównych procesora wirtualnego do jego użycia. Każdy `IVirtualProcessorRoot` interfejs reprezentuje prawo do wykonania pojedynczego wątku, który może wykonywać pracę w imieniu harmonogramu.|
|[IScheduler::Identyfikator GetId](#getid)|Zwraca unikatowy identyfikator harmonogramu.|
|[IScheduler::GetPolicy](#getpolicy)|Zwraca kopię zasad harmonogramu. Aby uzyskać więcej informacji na temat zasad harmonogramu, zobacz [Harmonogrampolicy](schedulerpolicy-class.md).|
|[IScheduler::NotifyResourcesExternallyBusy](#notifyresourcesexternallybusy)|Powiadamia ten harmonogram, że wątki sprzętowe reprezentowane przez zestaw katalogów głównych procesora wirtualnego w macierzy `ppVirtualProcessorRoots` są teraz używane przez inne harmonogramy.|
|[IScheduler::NotifyResourcesExternallyIdle](#notifyresourcesexternallyidle)|Powiadamia ten harmonogram, że wątki sprzętowe reprezentowane przez zestaw katalogów głównych procesora wirtualnego w macierzy `ppVirtualProcessorRoots` nie są używane przez inne harmonogramy.|
|[IScheduler::UsuńWirtualneprocesory](#removevirtualprocessors)|Inicjuje usuwanie katalogów głównych procesora wirtualnego, które zostały wcześniej przydzielone do tego harmonogramu.|
|[IScheduler::Statystyki](#statistics)|Zawiera informacje dotyczące wskaźników nadejścia i ukończenia zadania oraz zmiany długości kolejki dla harmonogramu.|

## <a name="remarks"></a>Uwagi

Jeśli implementujesz niestandardowy harmonogram, który komunikuje się z Menedżerem `IScheduler` zasobów, należy podać implementację interfejsu. Ten interfejs jest jednym z końca dwukierunkowego kanału komunikacji między harmonogramem a Menedżerem zasobów. Drugi koniec jest reprezentowany `IResourceManager` `ISchedulerProxy` przez i interfejsy, które są implementowane przez Menedżera zasobów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IScheduler`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Przestrzeń nazw:** współbieżność

## <a name="ischeduleraddvirtualprocessors-method"></a><a name="addvirtualprocessors"></a>IScheduler::AddVirtualProcessors Metoda

Udostępnia harmonogram z zestawem katalogów głównych procesora wirtualnego do jego użycia. Każdy `IVirtualProcessorRoot` interfejs reprezentuje prawo do wykonania pojedynczego wątku, który może wykonywać pracę w imieniu harmonogramu.

```cpp
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Tablica `IVirtualProcessorRoot` interfejsów reprezentujących katalogi główne procesora wirtualnego dodawane do harmonogramu.

*Liczba*<br/>
Liczba interfejsów `IVirtualProcessorRoot` w tablicy.

### <a name="remarks"></a>Uwagi

Menedżer zasobów wywołuje `AddVirtualProcessor` metodę przyznania początkowego zestawu katalogów głównych procesora wirtualnego do harmonogramu. Może również wywołać metodę, aby dodać katalogi główne procesora wirtualnego do harmonogramu, gdy równoważy zasoby wśród harmonogramów.

## <a name="ischedulergetid-method"></a><a name="getid"></a>IScheduler::Metoda GetId

Zwraca unikatowy identyfikator harmonogramu.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Unikatowy identyfikator liczby całkowitej.

### <a name="remarks"></a>Uwagi

Należy użyć [GetSchedulerId](concurrency-namespace-functions.md) funkcji, aby uzyskać unikatowy identyfikator dla `IScheduler` obiektu, który implementuje interfejs, przed użyciem interfejsu jako parametr do metod dostarczonych przez Menedżera zasobów. Oczekuje się, że zwróci ten `GetId` sam identyfikator, gdy funkcja jest wywoływana.

Identyfikator uzyskany z innego źródła może spowodować niezdefiniowane zachowanie.

## <a name="ischedulergetpolicy-method"></a><a name="getpolicy"></a>IScheduler::Metoda GetPolicy

Zwraca kopię zasad harmonogramu. Aby uzyskać więcej informacji na temat zasad harmonogramu, zobacz [Harmonogrampolicy](schedulerpolicy-class.md).

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Kopia zasad harmonogramu.

## <a name="ischedulernotifyresourcesexternallybusy-method"></a><a name="notifyresourcesexternallybusy"></a>IScheduler::NotifyResourcesExternallyBusy Metoda

Powiadamia ten harmonogram, że wątki sprzętowe reprezentowane przez zestaw katalogów głównych procesora wirtualnego w macierzy `ppVirtualProcessorRoots` są teraz używane przez inne harmonogramy.

```cpp
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Tablica `IVirtualProcessorRoot` interfejsów skojarzonych z wątkami sprzętowymi, na których inne harmonogramy stały się zajęte.

*Liczba*<br/>
Liczba interfejsów `IVirtualProcessorRoot` w tablicy.

### <a name="remarks"></a>Uwagi

Jest możliwe dla określonego wątku sprzętowego, które mają być przypisane do wielu harmonogramów w tym samym czasie. Jednym z powodów może być to, że nie ma wystarczającej liczby wątków sprzętowych w systemie, aby spełnić minimalną współbieżność dla wszystkich harmonogramów, bez udostępniania zasobów. Inną możliwością jest to, że zasoby są tymczasowo przypisane do innych harmonogramów, gdy harmonogram będący właścicielem nie używa ich, w drodze wszystkich jego katalogów głównych procesora wirtualnego w tym wątku sprzętowym są dezaktywowane.

Poziom subskrypcji wątku sprzętowego jest oznaczony liczbą subskrybowanych wątków i aktywowanych katalogów głównych procesora wirtualnego skojarzonych z tym wątkiem sprzętowym. Z punktu widzenia określonego harmonogramu poziom subskrypcji zewnętrznego wątku sprzętowego jest częścią subskrypcji innych harmonogramów przyczynić się do. Powiadomienia, że zasoby są zajęte zewnętrznie są wysyłane do harmonogramu, gdy poziom subskrypcji zewnętrznej dla wątku sprzętowego przenosi się z zera na terytorium dodatnie.

Powiadomienia za pośrednictwem tej metody są wysyłane tylko do harmonogramów, które mają zasady, w których wartość klucza `MinConcurrency` zasad jest równa wartości klucza `MaxConcurrency` zasad. Aby uzyskać więcej informacji na temat zasad harmonogramu, zobacz [Harmonogrampolicy](schedulerpolicy-class.md).

Harmonogram, który kwalifikuje się do powiadomień pobiera zestaw początkowych powiadomień podczas jego tworzenia, informując go, czy zasoby, które właśnie zostały przypisane, są zajęte zewnętrznie lub bezczynne.

## <a name="ischedulernotifyresourcesexternallyidle-method"></a><a name="notifyresourcesexternallyidle"></a>Metoda IScheduler::NotifyResourcesExternallyIdle

Powiadamia ten harmonogram, że wątki sprzętowe reprezentowane przez zestaw katalogów głównych procesora wirtualnego w macierzy `ppVirtualProcessorRoots` nie są używane przez inne harmonogramy.

```cpp
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Tablica `IVirtualProcessorRoot` interfejsów skojarzonych z wątkami sprzętowymi, na których inne harmonogramy stały się bezczynne.

*Liczba*<br/>
Liczba interfejsów `IVirtualProcessorRoot` w tablicy.

### <a name="remarks"></a>Uwagi

Jest możliwe dla określonego wątku sprzętowego, które mają być przypisane do wielu harmonogramów w tym samym czasie. Jednym z powodów może być to, że nie ma wystarczającej liczby wątków sprzętowych w systemie, aby spełnić minimalną współbieżność dla wszystkich harmonogramów, bez udostępniania zasobów. Inną możliwością jest to, że zasoby są tymczasowo przypisane do innych harmonogramów, gdy harmonogram będący właścicielem nie używa ich, w drodze wszystkich jego katalogów głównych procesora wirtualnego w tym wątku sprzętowym są dezaktywowane.

Poziom subskrypcji wątku sprzętowego jest oznaczony liczbą subskrybowanych wątków i aktywowanych katalogów głównych procesora wirtualnego skojarzonych z tym wątkiem sprzętowym. Z punktu widzenia określonego harmonogramu poziom subskrypcji zewnętrznego wątku sprzętowego jest częścią subskrypcji innych harmonogramów przyczynić się do. Powiadomienia, że zasoby są zajęte zewnętrznie są wysyłane do harmonogramu, gdy poziom subskrypcji zewnętrznej dla wątku sprzętowego spadnie do zera z poprzedniej wartości dodatniej.

Powiadomienia za pośrednictwem tej metody są wysyłane tylko do harmonogramów, które mają zasady, w których wartość klucza `MinConcurrency` zasad jest równa wartości klucza `MaxConcurrency` zasad. Aby uzyskać więcej informacji na temat zasad harmonogramu, zobacz [Harmonogrampolicy](schedulerpolicy-class.md).

Harmonogram, który kwalifikuje się do powiadomień pobiera zestaw początkowych powiadomień podczas jego tworzenia, informując go, czy zasoby, które właśnie zostały przypisane, są zajęte zewnętrznie lub bezczynne.

## <a name="ischedulerremovevirtualprocessors-method"></a><a name="removevirtualprocessors"></a>IScheduler::RemoveVirtualProcessors Metoda

Inicjuje usuwanie katalogów głównych procesora wirtualnego, które zostały wcześniej przydzielone do tego harmonogramu.

```cpp
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parametry

*ppVirtualProcessorRoots*<br/>
Tablica `IVirtualProcessorRoot` interfejsów reprezentujących katalogi główne procesora wirtualnego do usunięcia.

*Liczba*<br/>
Liczba interfejsów `IVirtualProcessorRoot` w tablicy.

### <a name="remarks"></a>Uwagi

Menedżer zasobów wywołuje `RemoveVirtualProcessors` metodę, aby odzyskać zestaw katalogów głównych procesora wirtualnego z harmonogramu. Harmonogram oczekuje się wywołać [Remove](iexecutionresource-structure.md#remove) metody na każdym interfejsie, gdy odbywa się z katalogami korzeni procesora wirtualnego. Nie należy `IVirtualProcessorRoot` używać interfejsu po wywołaniu `Remove` metody na nim.

Parametr `ppVirtualProcessorRoots` wskazuje na tablicę interfejsów. Wśród zestawu katalogów głównych procesora wirtualnego do usunięcia, korzenie nigdy `Remove` nie zostały aktywowane mogą być zwracane natychmiast przy użyciu metody. Katalogi główne, które zostały aktywowane i wykonują pracę lub zostały dezaktywowane i czekają na pracę, aby dotrzeć, powinny być zwracane asynchronicznie. Harmonogram musi podjąć wszelkie próby usunięcia katalogu głównego procesora wirtualnego tak szybko, jak to możliwe. Opóźnienie usunięcia katalogów głównych procesora wirtualnego może spowodować niezamierzone nadsubskrypcje w harmonogramie.

## <a name="ischedulerstatistics-method"></a><a name="statistics"></a>IScheduler::Metoda statystyk

Zawiera informacje dotyczące wskaźników nadejścia i ukończenia zadania oraz zmiany długości kolejki dla harmonogramu.

```cpp
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```

### <a name="parameters"></a>Parametry

*pTaskCompletionRate (Szybkość poł.*<br/>
Liczba zadań, które zostały ukończone przez harmonogram od ostatniego wywołania tej metody.

*pTaskArrivalRate (Równość małżenażu)*<br/>
Liczba zadań, które dotarły do harmonogramu od ostatniego wywołania tej metody.

*pNumberOfTasksEukietowany*<br/>
Całkowita liczba zadań we wszystkich kolejkach harmonogramu.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez Menedżera zasobów w celu zbierania statystyk dla harmonogramu. Statystyki zebrane w tym miejscu będą używane do kierowania algorytmów dynamicznych sprzężenia zwrotnego, aby określić, kiedy należy przypisać więcej zasobów do harmonogramu i kiedy zabrać zasoby. Wartości podane przez harmonogram mogą być optymistyczne i niekoniecznie muszą dokładnie odzwierciedlać bieżącą liczbę.

Tę metodę należy zaimplementować, jeśli Menedżer zasobów ma używać opinii na temat takich rzeczy, jak przybycie zadań, aby określić sposób równoważenia zasobu między harmonogramem a innymi harmonogramami zarejestrowanymi w Menedżerze zasobów. Jeśli zdecydujesz się nie zbierać statystyk, można `DynamicProgressFeedback` ustawić `DynamicProgressFeedbackDisabled` klucz zasad do wartości w zasadach harmonogramu, a Menedżer zasobów nie będzie wywoływać tej metody w harmonogramie.

W przypadku braku informacji statystycznych Menedżer zasobów użyje poziomów subskrypcji wątku sprzętowego do podejmowania decyzji dotyczących alokacji zasobów i migracji. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="see-also"></a>Zobacz też

[współbieżność Obszar nazw](concurrency-namespace.md)<br/>
[Klawiatura PolicyElementKey](concurrency-namespace-enums.md)<br/>
[Klasa polityki harmonogramu](schedulerpolicy-class.md)<br/>
[IExecutionContext, struktura](iexecutioncontext-structure.md)<br/>
[IThreadProxy, struktura](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot, struktura](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager — Struktura](iresourcemanager-structure.md)
