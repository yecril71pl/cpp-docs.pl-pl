---
title: "Currentscheduler — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CurrentScheduler
- CONCRT/concurrency::CurrentScheduler
- CONCRT/concurrency::CurrentScheduler::Create
- CONCRT/concurrency::CurrentScheduler::CreateScheduleGroup
- CONCRT/concurrency::CurrentScheduler::Detach
- CONCRT/concurrency::CurrentScheduler::Get
- CONCRT/concurrency::CurrentScheduler::GetNumberOfVirtualProcessors
- CONCRT/concurrency::CurrentScheduler::GetPolicy
- CONCRT/concurrency::CurrentScheduler::Id
- CONCRT/concurrency::CurrentScheduler::IsAvailableLocation
- CONCRT/concurrency::CurrentScheduler::RegisterShutdownEvent
- CONCRT/concurrency::CurrentScheduler::ScheduleTask
dev_langs: C++
helpviewer_keywords: CurrentScheduler class
ms.assetid: 31c20e0e-4cdf-49b4-8220-d726130aad2b
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ad1d49bb90a5f3c0732fd81851e34485e95f3ccb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="currentscheduler-class"></a>CurrentScheduler — Klasa
Reprezentuje abstrakcję dla bieżącego harmonogramu, skojarzone z kontekstem wywołującego.  
  
## <a name="syntax"></a>Składnia  
  
```
class CurrentScheduler;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Utwórz](#create)|Tworzy nowy harmonogram, w których zachowanie jest opisane przez `_Policy` parametru i dołącza go do kontekstu wywołania. Nowo utworzony harmonogram będzie bieżącego harmonogramu dla kontekstu wywołania.|  
|[CreateScheduleGroup](#createschedulegroup)|Przeciążone. Tworzy nową grupę harmonogramu w ramach harmonogramu, skojarzone z kontekstem wywołującego. Wersja, która przyjmuje parametr `_Placement` powoduje, że zadania w grupie nowo utworzonego harmonogramu, aby być ukierunkowane pod kątem wykonywania w lokalizacji określonej w tym parametrze.|  
|[Odłączanie](#detach)|Odłącza bieżącego harmonogramu z kontekstu wywołania i przywraca wcześniej dołączone harmonogram jako bieżącego harmonogramu, jeśli taka istnieje. Po powrocie z tej metody, kontekst wywołania jest wtedy zarządzana przez harmonogram, który wcześniej był dołączony do kontekstu za pomocą `CurrentScheduler::Create` lub `Scheduler::Attach` metody.|  
|[Pobierz](#get)|Zwraca wskaźnik do harmonogramu, skojarzone z wywołania kontekstem, nazywane również bieżącego harmonogramu.|  
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|Zwraca bieżącą liczbę procesorów wirtualnych harmonogramu, skojarzone z kontekstem wywołującego.|  
|[GetPolicy](#getpolicy)|Zwraca kopię bieżącego harmonogramu utworzony za pomocą zasad.|  
|[Identyfikator](#id)|Zwraca unikatowy identyfikator dla bieżącego harmonogramu.|  
|[IsAvailableLocation](#isavailablelocation)|Określa, czy w danej lokalizacji jest dostępny w bieżącego harmonogramu.|  
|[RegisterShutdownEvent](#registershutdownevent)|Powoduje, że obsługi zdarzeń systemu Windows przekazany `_ShutdownEvent` parametr, aby zostać zgłoszony, gdy harmonogramu, skojarzone z bieżącym kontekście zamyka i niszczy samej siebie. W czasie, które zdarzenie jest sygnalizowane wszystkie pracy, który miał zostało zaplanowane do harmonogramu zostanie zakończona. Za pomocą tej metody można zarejestrować wiele zdarzeń zamknięcia systemu.|  
|[ScheduleTask](#scheduletask)|Przeciążone. Planuje lekki zadania w ramach harmonogramu, skojarzone z kontekstem wywołującego. Zadanie lekki zostaną umieszczone w grupie harmonogram określone przez środowisko uruchomieniowe. Wersja, która przyjmuje parametr `_Placement` powoduje zadania można ukierunkowane pod kątem wykonywania w określonej lokalizacji.|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku harmonogramu nie (zobacz [harmonogramu](scheduler-class.md)) skojarzony z kontekstem wywołującego, wiele metod w `CurrentScheduler` załącznika procesu domyślnego harmonogramu spowoduje klasy. Może również to utworzenia procesu domyślnego harmonogramu podczas takiego połączenia.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CurrentScheduler`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="create"></a>Utwórz 

 Tworzy nowy harmonogram, w których zachowanie jest opisane przez `_Policy` parametru i dołącza go do kontekstu wywołania. Nowo utworzony harmonogram będzie bieżącego harmonogramu dla kontekstu wywołania.  
  
```
static void __cdecl Create(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>Parametry  
 `_Policy`  
 Zasady harmonogramu, które określa zachowanie nowo utworzonego harmonogramu.  
  
### <a name="remarks"></a>Uwagi  
 Dołączanie harmonogramu do Kontekst wywołania niejawnie umieszcza liczba odwołań w harmonogramie.  
  
 Po utworzeniu harmonogramu z `Create` metody należy wywołać [CurrentScheduler::Detach](#detach) metody w pewnym momencie w przyszłości, aby umożliwić harmonogramu zamknąć.  
  
 Jeśli ta metoda jest wywoływana z kontekstu, która jest już dołączony do innego harmonogramu, istniejącego harmonogramu jest zapamiętanych jako poprzedniej harmonogram, a nowo utworzonego harmonogramu staje się bieżącego harmonogramu. Podczas wywoływania `CurrentScheduler::Detach` metody w późniejszym czasie, poprzednie harmonogramu jest przywracany jako bieżącego harmonogramu.  
  
 Ta metoda może zgłosić różne wyjątki, w tym [scheduler_resource_allocation_error —](scheduler-resource-allocation-error-class.md) i [invalid_scheduler_policy_value —](invalid-scheduler-policy-value-class.md).  
  
##  <a name="createschedulegroup"></a>CreateScheduleGroup 

 Tworzy nową grupę harmonogramu w ramach harmonogramu, skojarzone z kontekstem wywołującego. Wersja, która przyjmuje parametr `_Placement` powoduje, że zadania w grupie nowo utworzonego harmonogramu, aby być ukierunkowane pod kątem wykonywania w lokalizacji określonej w tym parametrze.  
  
```
static ScheduleGroup* __cdecl CreateScheduleGroup();

static ScheduleGroup* __cdecl CreateScheduleGroup(location& _Placement);
```  
  
### <a name="parameters"></a>Parametry  
 `_Placement`  
 Odwołanie do lokalizacji, w którym zadania w grupie harmonogram będzie można ukierunkowane pod kątem wykonywanych w.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowo utworzonego harmonogramu grupy. To `ScheduleGroup` obiekt ma liczba początkowa odwołania dla niej.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda spowoduje procesu domyślnego harmonogramu są tworzone i/lub dołączyć do wywoływania kontekstu, jeśli nie harmonogramu aktualnie skojarzony z kontekstem wywoływania.  
  
 Należy wywołać [wersji](schedulegroup-class.md#release) metody dla grupy harmonogram po zakończeniu planowania pracy do niego. Planista zniszczy harmonogram grupy podczas pracy w kolejce do niego zostało ukończone.  
  
 Należy pamiętać, że jeśli utworzono jawnie tego harmonogramu, trzeba zwolnić wszystkie odwołania można zaplanować grup, to przed zwolnieniem użytkownikowi w harmonogramie, przez odłączenie bieżącego kontekstu z niego.  
  
##  <a name="detach"></a>Odłączanie 

 Odłącza bieżącego harmonogramu z kontekstu wywołania i przywraca wcześniej dołączone harmonogram jako bieżącego harmonogramu, jeśli taka istnieje. Po powrocie z tej metody, kontekst wywołania jest wtedy zarządzana przez harmonogram, który wcześniej był dołączony do kontekstu za pomocą `CurrentScheduler::Create` lub `Scheduler::Attach` metody.  
  
```
static void __cdecl Detach();
```  
  
### <a name="remarks"></a>Uwagi  
 `Detach` Metoda niejawnie usuwa liczba odwołań z harmonogramu.  
  
 Jeśli nie ma żadnych harmonogramu dołączyć do kontekstu wywołania, wywołanie tej metody spowoduje [scheduler_not_attached —](scheduler-not-attached-class.md) zgłaszanego wyjątku.  
  
 Wywołanie tej metody z kontekstu jest wewnętrzny i zarządzane przez harmonogramu lub kontekst dołączonego przy użyciu metody inne niż [Scheduler::Attach](scheduler-class.md#attach) lub [CurrentScheduler::Create](#create) metod wynikiem będzie [improper_scheduler_detach —](improper-scheduler-detach-class.md) zgłaszanego wyjątku.  
  
##  <a name="get"></a>Pobierz 

 Zwraca wskaźnik do harmonogramu, skojarzone z wywołania kontekstem, nazywane również bieżącego harmonogramu.  
  
```
static Scheduler* __cdecl Get();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do harmonogramu, skojarzone z kontekstem wywołującym (bieżącego harmonogramu).  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda spowoduje procesu domyślnego harmonogramu są tworzone i/lub dołączyć do wywoływania kontekstu, jeśli nie harmonogramu aktualnie skojarzony z kontekstem wywoływania. Żadne dodatkowe odwołanie jest umieszczona na `Scheduler` obiektu zwróconego przez tę metodę.  
  
##  <a name="getnumberofvirtualprocessors"></a>GetNumberOfVirtualProcessors 

 Zwraca bieżącą liczbę procesorów wirtualnych harmonogramu, skojarzone z kontekstem wywołującego.  
  
```
static unsigned int __cdecl GetNumberOfVirtualProcessors();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli harmonogramu jest skojarzony z kontekstem wywołującego, bieżąca liczba procesorów wirtualnych dla tego harmonogramu; w przeciwnym razie wartość `-1`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda nie spowoduje załącznika harmonogramu, jeśli kontekst wywołania nie jest już skojarzony z harmonogramu.  
  
 Wartość zwrócona przez tę metodę jest natychmiastowe próbkowania liczba procesorów wirtualnych harmonogramu, skojarzone z kontekstem wywołującego. Ta wartość może być nieodświeżona moment, który jest zwracany.  
  
##  <a name="getpolicy"></a>GetPolicy 

 Zwraca kopię bieżącego harmonogramu utworzony za pomocą zasad.  
  
```
static SchedulerPolicy __cdecl GetPolicy();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kopia zasady czy utworzono bieżącego harmonogramu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda spowoduje procesu domyślnego harmonogramu są tworzone i/lub dołączyć do wywoływania kontekstu, jeśli nie harmonogramu aktualnie skojarzony z kontekstem wywoływania.  
  
##  <a name="id"></a>Identyfikator 

 Zwraca unikatowy identyfikator dla bieżącego harmonogramu.  
  
```
static unsigned int __cdecl Id();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli harmonogramu jest skojarzony z kontekstem wywołującego, unikatowy identyfikator dla tego harmonogramu; w przeciwnym razie wartość `-1`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda nie spowoduje załącznika harmonogramu, jeśli kontekst wywołania nie jest już skojarzony z harmonogramu.  
  
##  <a name="isavailablelocation"></a>IsAvailableLocation 

 Określa, czy w danej lokalizacji jest dostępny w bieżącego harmonogramu.  
  
```
static bool __cdecl IsAvailableLocation(const location& _Placement);
```  
  
### <a name="parameters"></a>Parametry  
 `_Placement`  
 Odwołanie do lokalizacji zapytanie dotyczące bieżącego harmonogramu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskazuje, czy lokalizacja określona przez `_Placement` argument jest dostępny na bieżącego harmonogramu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda nie spowoduje załącznika harmonogramu, jeśli kontekst wywołania nie jest już skojarzony z harmonogramu.  
  
 Należy pamiętać, że wartość zwracana natychmiastowe próbkowania czy dostępny jest danej lokalizacji. Obecności wielu planiści dynamiczne zarządzanie zasobami można dodawać lub odebranie zasobów z planiści w dowolnym momencie. Powinno się to zdarzyć, danej lokalizacji można zmienić dostępności.  
  
##  <a name="registershutdownevent"></a>RegisterShutdownEvent 

 Powoduje, że obsługi zdarzeń systemu Windows przekazany `_ShutdownEvent` parametr, aby zostać zgłoszony, gdy harmonogramu, skojarzone z bieżącym kontekście zamyka i niszczy samej siebie. W czasie, które zdarzenie jest sygnalizowane wszystkie pracy, który miał zostało zaplanowane do harmonogramu zostanie zakończona. Za pomocą tej metody można zarejestrować wiele zdarzeń zamknięcia systemu.  
  
```
static void __cdecl RegisterShutdownEvent(HANDLE _ShutdownEvent);
```  
  
### <a name="parameters"></a>Parametry  
 `_ShutdownEvent`  
 Dojście do obiektu zdarzeń systemu Windows, która sygnalizuje przez środowisko uruchomieniowe przy harmonogramu, skojarzone z bieżącym kontekście zamyka i niszczy sam.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie ma żadnych harmonogramu dołączyć do kontekstu wywołania, wywołanie tej metody spowoduje [scheduler_not_attached —](scheduler-not-attached-class.md) zgłaszanego wyjątku.  
  
##  <a name="scheduletask"></a>ScheduleTask 

 Planuje lekki zadania w ramach harmonogramu, skojarzone z kontekstem wywołującego. Zadanie lekki zostaną umieszczone w grupie harmonogram określone przez środowisko uruchomieniowe. Wersja, która przyjmuje parametr `_Placement` powoduje zadania można ukierunkowane pod kątem wykonywania w określonej lokalizacji.  
  
```
static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data);

static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement);
```  
  
### <a name="parameters"></a>Parametry  
 `_Proc`  
 Wskaźnik do funkcji w celu wykonania do wykonywania zadań lekki treści.  
  
 `_Data`  
 Void wskaźnik do danych, który zostanie przekazany jako parametr do treści zadania.  
  
 `_Placement`  
 Odwołanie do lokalizacji, w którym zadanie lekki będzie można ukierunkowane pod kątem wykonywania w.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda spowoduje procesu domyślnego harmonogramu są tworzone i/lub dołączyć do wywoływania kontekstu, jeśli nie harmonogramu aktualnie skojarzony z kontekstem wywoływania.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Klasa harmonogramu](scheduler-class.md)   
 [Policyelementkey —](concurrency-namespace-enums.md)   
 [Harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



