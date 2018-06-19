---
title: Struktura IScheduler | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- IScheduler structure
ms.assetid: 471de85a-2b1a-4b6d-ab81-2eff2737161e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c78d02ccd5639369ad8b4d0183458da2ba85269
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693994"
---
# <a name="ischeduler-structure"></a>Struktura IScheduler
Interfejs abstrakcję harmonogram pracy. Współbieżność środowiska wykonawczego Resource Manager używa tego interfejsu do komunikowania się z planiści pracy.  
  
## <a name="syntax"></a>Składnia  
  
```
struct IScheduler;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IScheduler::AddVirtualProcessors](#addvirtualprocessors)|Udostępnia harmonogramu z zestawem procesorów wirtualnych katalogów głównych do jej użycia. Każdy `IVirtualProcessorRoot` interfejsu reprezentuje z prawem wykonywania pojedynczego wątku, który można wykonać pracę w imieniu harmonogramu.|  
|[IScheduler::GetId](#getid)|Zwraca unikatowy identyfikator dla harmonogramu.|  
|[IScheduler::GetPolicy](#getpolicy)|Zwraca kopię zasad harmonogramu. Aby uzyskać więcej informacji dotyczących zasad harmonogramu, zobacz [schedulerpolicy —](schedulerpolicy-class.md).|  
|[IScheduler::NotifyResourcesExternallyBusy](#notifyresourcesexternallybusy)|Powiadamia ten harmonogram, który wątków sprzętu reprezentowany przez zestaw głównych procesora wirtualnego w tablicy `ppVirtualProcessorRoots` są obecnie używane przez inne transfery danych.|  
|[IScheduler::NotifyResourcesExternallyIdle](#notifyresourcesexternallyidle)|Powiadamia ten harmonogram, który wątków sprzętu reprezentowany przez zestaw głównych procesora wirtualnego w tablicy `ppVirtualProcessorRoots` nie są używane przez inne transfery danych.|  
|[IScheduler::RemoveVirtualProcessors](#removevirtualprocessors)|Powoduje zainicjowanie usuwania głównych procesorów wirtualnych, które wcześniej zostały przydzielone do tego harmonogramu.|  
|[IScheduler::Statistics](#statistics)|Zawiera informacje dotyczące szybkości odbioru i ukończenia zadania i zmiana długości kolejki harmonogramu.|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku wdrażania harmonogramu niestandardowego, który komunikuje się z Menedżerem zasobów powinien zapewniać implementację elementu `IScheduler` interfejsu. Ten interfejs jest jeden element end dwukierunkowy kanał komunikacji między harmonogramu i Menedżera zasobów. Drugi punkt końcowy jest reprezentowana przez `IResourceManager` i `ISchedulerProxy` interfejsów implementowanych przez Menedżera zasobów.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IScheduler`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrtrm.h  
  
 **Namespace:** współbieżności  
  
##  <a name="addvirtualprocessors"></a>  IScheduler::AddVirtualProcessors — metoda  
 Udostępnia harmonogramu z zestawem procesorów wirtualnych katalogów głównych do jej użycia. Każdy `IVirtualProcessorRoot` interfejsu reprezentuje z prawem wykonywania pojedynczego wątku, który można wykonać pracę w imieniu harmonogramu.  
  
```
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `ppVirtualProcessorRoots`  
 Tablica `IVirtualProcessorRoot` interfejsy reprezentujący procesorów wirtualnych katalogów głównych dodawany do harmonogramu.  
  
 `count`  
 Liczba `IVirtualProcessorRoot` interfejsów w tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Menedżer zasobów wywołuje `AddVirtualProcessor` metody, aby udzielić początkowego zestawu procesorów wirtualnych katalogów głównych harmonogramu. On również może wywołać metody w celu dodania procesorów wirtualnych katalogów głównych do harmonogramu, podczas jej rebalances zasobów między transfery danych.  
  
##  <a name="getid"></a>  IScheduler::GetId — metoda  
 Zwraca unikatowy identyfikator dla harmonogramu.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator unikatowy liczby całkowitej.  
  
### <a name="remarks"></a>Uwagi  
 Należy używać [getschedulerid —](concurrency-namespace-functions.md) funkcji, aby uzyskać unikatowy identyfikator dla obiekt, który implementuje `IScheduler` interfejsu, przed użyciem interfejsu jako parametr metody dostarczone przez Menedżera zasobów. Powinna zwrócić element tego samego identyfikatora po `GetId` funkcja jest wywoływana.  
  
 Identyfikator pochodzi z innego źródła może spowodować niezdefiniowane zachowanie.  
  
##  <a name="getpolicy"></a>  IScheduler::GetPolicy — metoda  
 Zwraca kopię zasad harmonogramu. Aby uzyskać więcej informacji dotyczących zasad harmonogramu, zobacz [schedulerpolicy —](schedulerpolicy-class.md).  
  
```
virtual SchedulerPolicy GetPolicy() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kopia zasad harmonogramu.  
  
##  <a name="notifyresourcesexternallybusy"></a>  IScheduler::NotifyResourcesExternallyBusy — metoda  
 Powiadamia ten harmonogram, który wątków sprzętu reprezentowany przez zestaw głównych procesora wirtualnego w tablicy `ppVirtualProcessorRoots` są obecnie używane przez inne transfery danych.  
  
```
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `ppVirtualProcessorRoots`  
 Tablica `IVirtualProcessorRoot` interfejsy skojarzone z wątków sprzętu, na które stały się inne transfery danych zajęty.  
  
 `count`  
 Liczba `IVirtualProcessorRoot` interfejsów w tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Istnieje możliwość dla wątku konkretnego sprzętu ma być przypisany do wielu transfery danych w tym samym czasie. Jedną z przyczyn tego można, że nie ma wystarczającej liczby wątków sprzętu w systemie, aby spełniać minimalne współbieżności dla wszystkich planiści bez udostępniania zasobów. Inną możliwością jest, czy zasoby są tymczasowo przypisane do inne transfery danych, gdy harmonogram będący właścicielem nie używa ich, na jego korzenie Procesor wirtualny na tym wątku sprzętu dezaktywowany.  
  
 Poziom subskrypcji wątku sprzętu jest wskazywane przez liczbę wątków subskrybowanego i uaktywnione procesorów wirtualnych katalogów głównych skojarzone z tym wątku sprzętu. Z punktu widzenia konkretnego harmonogramu poziom subskrypcji zewnętrznych wątku sprzętu jest częścią inne transfery danych przyczynienie się do subskrypcji. Powiadomienia, że zasoby są zewnętrznie zajęte są wysyłane do harmonogramu, przy poziomie zewnętrznych subskrypcji dla wątku sprzętu są przenoszone z zero dodatnie obszar.  
  
 Tylko wysyłane są powiadomienia za pomocą tej metody do transfery danych, które mają zasad gdzie wartość `MinConcurrency` jest równa wartości dla klucza zasad `MaxConcurrency` klucza zasad. Aby uzyskać więcej informacji dotyczących zasad harmonogramu, zobacz [schedulerpolicy —](schedulerpolicy-class.md).  
  
 Harmonogram, które kwalifikują się do powiadomienia pobiera zestaw powiadomień początkowej podczas jego tworzenia, powiadomienia go, czy zasoby, które właśnie została przypisana zewnętrznie zajęta lub bezczynności.  
  
##  <a name="notifyresourcesexternallyidle"></a>  IScheduler::NotifyResourcesExternallyIdle — metoda  
 Powiadamia ten harmonogram, który wątków sprzętu reprezentowany przez zestaw głównych procesora wirtualnego w tablicy `ppVirtualProcessorRoots` nie są używane przez inne transfery danych.  
  
```
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `ppVirtualProcessorRoots`  
 Tablica `IVirtualProcessorRoot` interfejsy skojarzone z wątków sprzętu, na których mają Bezczynność inne transfery danych.  
  
 `count`  
 Liczba `IVirtualProcessorRoot` interfejsów w tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Istnieje możliwość dla wątku konkretnego sprzętu ma być przypisany do wielu transfery danych w tym samym czasie. Jedną z przyczyn tego można, że nie ma wystarczającej liczby wątków sprzętu w systemie, aby spełniać minimalne współbieżności dla wszystkich planiści bez udostępniania zasobów. Inną możliwością jest, czy zasoby są tymczasowo przypisane do inne transfery danych, gdy harmonogram będący właścicielem nie używa ich, na jego korzenie Procesor wirtualny na tym wątku sprzętu dezaktywowany.  
  
 Poziom subskrypcji wątku sprzętu jest wskazywane przez liczbę wątków subskrybowanego i uaktywnione procesorów wirtualnych katalogów głównych skojarzone z tym wątku sprzętu. Z punktu widzenia konkretnego harmonogramu poziom subskrypcji zewnętrznych wątku sprzętu jest częścią inne transfery danych przyczynienie się do subskrypcji. Powiadomienia, że zasoby są zewnętrznie zajęte są wysyłane do harmonogramu, gdy poziom subskrypcji zewnętrznych dla wątku sprzętu znajduje się na wartość zero z poprzednią wartość dodatnią.  
  
 Tylko wysyłane są powiadomienia za pomocą tej metody do transfery danych, które mają zasad gdzie wartość `MinConcurrency` jest równa wartości dla klucza zasad `MaxConcurrency` klucza zasad. Aby uzyskać więcej informacji dotyczących zasad harmonogramu, zobacz [schedulerpolicy —](schedulerpolicy-class.md).  
  
 Harmonogram, które kwalifikują się do powiadomienia pobiera zestaw powiadomień początkowej podczas jego tworzenia, powiadomienia go, czy zasoby, które właśnie została przypisana zewnętrznie zajęta lub bezczynności.  
  
##  <a name="removevirtualprocessors"></a>  IScheduler::RemoveVirtualProcessors — metoda  
 Powoduje zainicjowanie usuwania głównych procesorów wirtualnych, które wcześniej zostały przydzielone do tego harmonogramu.  
  
```
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `ppVirtualProcessorRoots`  
 Tablica `IVirtualProcessorRoot` interfejsy reprezentujący katalogów głównych procesora wirtualnego do usunięcia.  
  
 `count`  
 Liczba `IVirtualProcessorRoot` interfejsów w tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Menedżer zasobów wywołuje `RemoveVirtualProcessors` metody, aby odzyskać zestaw procesorów wirtualnych katalogów głównych z harmonogramu. Planista powinien wywoływać [Usuń](iexecutionresource-structure.md#remove) metody dla danego interfejsu, gdy jest wykonywane z procesorów wirtualnych katalogów głównych. Nie używaj `IVirtualProcessorRoot` interfejsu po ma wywołać `Remove` dla niego metodę.  
  
 Parametr `ppVirtualProcessorRoots` odwołuje się do tablicy interfejsów. Do zbioru głównych procesora wirtualnego do usunięcia korzenie nigdy nie został aktywowany może być zwracany natychmiast przy użyciu `Remove` metody. Elementy główne, które uaktywnieniu i są albo wykonywania pracy lub zostało zdezaktywowane i oczekiwania na odebranie, pracy powinny być zwracane asynchronicznie. Planista musi być każda próba możliwie jak najszybciej usunąć głównego procesora wirtualnego. Opóźnienie usunięcia głównych procesorów wirtualnych może spowodować przypadkowe nadsubskrypcji w ramach harmonogramu zadań.  
  
##  <a name="statistics"></a>  IScheduler::Statistics — metoda  
 Zawiera informacje dotyczące szybkości odbioru i ukończenia zadania i zmiana długości kolejki harmonogramu.  
  
```
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pTaskCompletionRate`  
 Liczba zadań wykonanych przez harmonogram od czasu ostatniego wywołania tej metody.  
  
 `pTaskArrivalRate`  
 Liczba zadań, które zostały dostarczone w harmonogramie od czasu ostatniego wywołania tej metody.  
  
 `pNumberOfTasksEnqueued`  
 Całkowita liczba zadań we wszystkich kolejkach harmonogramu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez Menedżera zasobów w celu zbierania statystyk dla harmonogramu. Statystyki zebrane w tym miejscu będzie służyć do kierowania algorytmów dynamiczne opinię do określenia, kiedy należy przypisać więcej zasobów do harmonogramu i wykonać optymalizacji zasobów. Wartości dostarczonej przez harmonogram może być optymistycznej i nie trzeba dokładnie odzwierciedla bieżącą liczbę.  
  
 Należy zaimplementować tę metodę, jeśli chcesz Resource Manager do używania swoją opinię na temat czynności, takich jako przyjęcia zadań w celu określenia sposobu równoważenia zasobów między użytkownika harmonogramu i inne transfery danych w zarejestrowany przy użyciu Menedżera zasobów. Jeśli wybierzesz nie zebrać statystykę, można ustawić klucza zasad `DynamicProgressFeedback` wartość `DynamicProgressFeedbackDisabled` w Twojej harmonogram zasad i zasobu menedżera nie wywoła tę metodę w Twojej harmonogramu.  
  
 W przypadku braku informacji statystycznych Menedżer zasobów zostaną użyte sprzętu wątku subskrypcji poziomów do decyzje zasobów alokacji i migracji. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Policyelementkey —](concurrency-namespace-enums.md)   
 [Schedulerpolicy — klasa](schedulerpolicy-class.md)   
 [IExecutionContext Structure](iexecutioncontext-structure.md)   
 [Ithreadproxy — struktura](ithreadproxy-structure.md)   
 [Ivirtualprocessorroot — struktura](ivirtualprocessorroot-structure.md)   
 [IResourceManager, struktura](iresourcemanager-structure.md)
