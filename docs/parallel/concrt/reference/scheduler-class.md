---
title: Klasa harmonogramu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- Scheduler
- CONCRT/concurrency::Scheduler
- CONCRT/concurrency::Scheduler::Scheduler
- CONCRT/concurrency::Scheduler::Attach
- CONCRT/concurrency::Scheduler::Create
- CONCRT/concurrency::Scheduler::CreateScheduleGroup
- CONCRT/concurrency::Scheduler::GetNumberOfVirtualProcessors
- CONCRT/concurrency::Scheduler::GetPolicy
- CONCRT/concurrency::Scheduler::Id
- CONCRT/concurrency::Scheduler::IsAvailableLocation
- CONCRT/concurrency::Scheduler::Reference
- CONCRT/concurrency::Scheduler::RegisterShutdownEvent
- CONCRT/concurrency::Scheduler::Release
- CONCRT/concurrency::Scheduler::ResetDefaultSchedulerPolicy
- CONCRT/concurrency::Scheduler::ScheduleTask
- CONCRT/concurrency::Scheduler::SetDefaultSchedulerPolicy
dev_langs:
- C++
helpviewer_keywords:
- Scheduler class
ms.assetid: 34cf7961-048d-4852-8a5c-a32f823e3506
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97abec33d5fa4b372bc26874fd37397a2b78bb29
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="scheduler-class"></a>Klasa harmonogramu
Reprezentuje abstrakcję harmonogramu współbieżność środowiska wykonawczego.  
  
## <a name="syntax"></a>Składnia  
  
```
class Scheduler;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="protected-constructors"></a>Konstruktory chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Harmonogram](#ctor)|Obiekt `Scheduler` klasy można tylko utworzone za pomocą metody fabryki, albo niejawnie.|  
|[~ Scheduler — destruktor](#dtor)|Obiekt `Scheduler` klasy niejawnie zostanie zniszczony, gdy wszystkie zewnętrzne odwołania do niego przestaną istnieć.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Attach](#attach)|Dołącza planista Kontekst wywołania. Po powrocie z tej metody, wywołujący kontekstu jest zarządzany przez harmonogram i planista staje się bieżącego harmonogramu.|  
|[Utwórz](#create)|Tworzy nowy harmonogram, w których zachowanie jest opisane przez `_Policy` parametr, umieszcza początkowej odwołania na harmonogram i zwraca wskaźnik do niego.|  
|[CreateScheduleGroup](#createschedulegroup)|Przeciążone. Tworzy nową grupę harmonogramu w ramach harmonogramu zadań. Wersja, która przyjmuje parametr `_Placement` powoduje, że zadania w grupie nowo utworzonego harmonogramu, aby być ukierunkowane pod kątem wykonywania w lokalizacji określonej w tym parametrze.|  
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|Zwraca bieżącą liczbę procesorów wirtualnych dla harmonogramu.|  
|[GetPolicy](#getpolicy)|Zwraca kopię planista utworzony za pomocą zasad.|  
|[Id](#id)|Zwraca unikatowy identyfikator dla harmonogramu.|  
|[IsAvailableLocation](#isavailablelocation)|Określa, czy danej lokalizacji jest dostępny w ramach harmonogramu zadań.|  
|[Dokumentacja](#reference)|Zwiększa liczbę odwołanie harmonogramu.|  
|[RegisterShutdownEvent](#registershutdownevent)|Powoduje, że obsługi zdarzeń systemu Windows przekazany `_Event` parametr, aby zostać zgłoszony, gdy harmonogram zamyka i niszczy się. W czasie, które zdarzenie jest sygnalizowane wszystkie pracy, który miał zostało zaplanowane do harmonogramu zostanie zakończona. Za pomocą tej metody można zarejestrować wiele zdarzeń zamknięcia systemu.|  
|[Wersja](#release)|Zmniejsza liczba odwołanie harmonogramu.|  
|[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)|Przywraca domyślne zasady harmonogramu domyślnej środowiska uruchomieniowego. Przy następnym harmonogram domyślny jest tworzony, zostanie użyty domyślne ustawienia zasad środowiska uruchomieniowego.|  
|[ScheduleTask](#scheduletask)|Przeciążone. Zaplanowane zadania lekki w ramach harmonogramu zadań. Zadanie lekki zostaną umieszczone w grupie harmonogram określone przez środowisko uruchomieniowe. Wersja, która przyjmuje parametr `_Placement` powoduje zadania można ukierunkowane pod kątem wykonywania w określonej lokalizacji.|  
|[SetDefaultSchedulerPolicy](#setdefaultschedulerpolicy)|Umożliwia ma być używany do tworzenia harmonogramu domyślne zasady zdefiniowane przez użytkownika. Tę metodę można wywołać tylko wtedy, gdy nie domyślnego harmonogramu istnieje w ramach procesu. Po ustawieniu domyślne zasady obowiązujące pozostaje aż do następnego wywołania nieprawidłowy albo `SetDefaultSchedulerPolicy` lub [ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy) metody.|  
  
## <a name="remarks"></a>Uwagi  
 Harmonogram współbieżność środowiska wykonawczego używa konteksty wykonanie, które mapowania kontekstów wykonywania systemu operacyjnego, takie jak wątek, do wykonywania pracy w kolejce do niej przez aplikację. W dowolnym momencie poziom współbieżności harmonogramu jest równa liczbie procesorów wirtualnych przyznane przez Menedżera zasobów. Procesor wirtualny jest abstrakcją zasoby przetwarzania i map do wątku sprzętu na podstawowym systemie. W kontekście jednego harmonogramu można wykonywać w procesorów wirtualnych w danym momencie.  
  
 Współbieżność środowiska wykonawczego spowoduje utworzenie harmonogramu domyślnej na proces do wykonywania pracy równoległych. Ponadto można utworzyć własny harmonogram wystąpień i manipulowania za pomocą tej klasy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Scheduler`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="attach"></a> Dołącz 

 Dołącza planista Kontekst wywołania. Po powrocie z tej metody, wywołujący kontekstu jest zarządzany przez harmonogram i planista staje się bieżącego harmonogramu.  
  
```
virtual void Attach() = 0;
```  
  
### <a name="remarks"></a>Uwagi  
 Dołączanie harmonogramu niejawnie umieszcza odwołania w harmonogramie.  
  
 W pewnym momencie w przyszłości, należy wywołać [CurrentScheduler::Detach](currentscheduler-class.md#detach) metody, aby umożliwić harmonogramu zamknąć.  
  
 Jeśli ta metoda jest wywoływana z kontekstu, która jest już dołączony do innego harmonogramu, istniejącego harmonogramu jest zapamiętanych jako poprzedniej harmonogram, a nowo utworzonego harmonogramu staje się bieżącego harmonogramu. Podczas wywoływania `CurrentScheduler::Detach` metody w późniejszym czasie, poprzednie harmonogramu jest przywracany jako bieżącego harmonogramu.  
  
 Ta metoda zgłosi [improper_scheduler_attach —](improper-scheduler-attach-class.md) wyjątek, jeśli ten harmonogram jest bieżącego harmonogramu Kontekst wywołania.  
  
##  <a name="create"></a> Utwórz 

 Tworzy nowy harmonogram, w których zachowanie jest opisane przez `_Policy` parametr, umieszcza początkowej odwołania na harmonogram i zwraca wskaźnik do niego.  
  
```
static Scheduler* __cdecl Create(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>Parametry  
 `_Policy`  
 Zasady harmonogramu, które określa zachowanie nowo utworzonego harmonogramu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowo utworzonego harmonogramu. To `Scheduler` obiekt ma liczba początkowa odwołania dla niej.  
  
### <a name="remarks"></a>Uwagi  
 Po utworzeniu harmonogramu z `Create` metody należy wywołać `Release` metody w pewnym momencie w przyszłości, aby usunąć liczebności referencyjnej początkowej i umożliwić harmonogramu zamknąć.  
  
 Harmonogramu utworzone za pomocą tej metody nie jest dołączony do wywoływania kontekstu. Można dołączyć do kontekstu za pomocą [Attach](#attach) metody.  
  
 Ta metoda może zgłosić różne wyjątki, w tym [scheduler_resource_allocation_error —](scheduler-resource-allocation-error-class.md) i [invalid_scheduler_policy_value —](invalid-scheduler-policy-value-class.md).  
  
##  <a name="createschedulegroup"></a> CreateScheduleGroup 

 Tworzy nową grupę harmonogramu w ramach harmonogramu zadań. Wersja, która przyjmuje parametr `_Placement` powoduje, że zadania w grupie nowo utworzonego harmonogramu, aby być ukierunkowane pod kątem wykonywania w lokalizacji określonej w tym parametrze.  
  
```
virtual ScheduleGroup* CreateScheduleGroup() = 0;

virtual ScheduleGroup* CreateScheduleGroup(location& _Placement) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_Placement`  
 Odwołanie do lokalizacji, w którym zadania w grupie harmonogram zostanie ukierunkowane pod kątem wykonywania w.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowo utworzonego harmonogramu grupy. To `ScheduleGroup` obiekt ma liczba początkowa odwołania dla niej.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać [wersji](schedulegroup-class.md#release) metody dla grupy harmonogram po zakończeniu planowania pracy do niego. Planista zniszczy harmonogram grupy podczas pracy w kolejce do niego zostało ukończone.  
  
 Należy pamiętać, że jeśli utworzono jawnie tego harmonogramu, trzeba zwolnić wszystkie odwołania można zaplanować grup, to przed zwolnieniem referencje w harmonogramie.  
  
##  <a name="getnumberofvirtualprocessors"></a> GetNumberOfVirtualProcessors 

 Zwraca bieżącą liczbę procesorów wirtualnych dla harmonogramu.  
  
```
virtual unsigned int GetNumberOfVirtualProcessors() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca liczba procesorów wirtualnych dla harmonogramu.  
  
##  <a name="getpolicy"></a> GetPolicy 

 Zwraca kopię planista utworzony za pomocą zasad.  
  
```
virtual SchedulerPolicy GetPolicy() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kopia planista utworzony za pomocą zasad.  
  
##  <a name="id"></a> Id 

 Zwraca unikatowy identyfikator dla harmonogramu.  
  
```
virtual unsigned int Id() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Unikatowy identyfikator dla harmonogramu.  
  
##  <a name="isavailablelocation"></a> IsAvailableLocation 

 Określa, czy danej lokalizacji jest dostępny w ramach harmonogramu zadań.  
  
```
virtual bool IsAvailableLocation(const location& _Placement) const = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_Placement`  
 Odwołanie do lokalizacji kwerend dotyczących harmonogramu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskazuje, czy lokalizacja określona przez `_Placement` argument jest dostępny w ramach harmonogramu zadań.  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, że wartość zwracana natychmiastowe próbkowania czy dostępny jest danej lokalizacji. Obecności wielu planiści dynamiczne zarządzanie zasobami można dodawać lub odebranie zasobów z planiści w dowolnym momencie. Powinno się to zdarzyć, danej lokalizacji można zmienić dostępności.  
  
##  <a name="reference"></a> Odwołanie 

 Zwiększa liczbę odwołanie harmonogramu.  
  
```
virtual unsigned int Reference() = 0 ;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba odwołań nowo zwiększany.  
  
### <a name="remarks"></a>Uwagi  
 Służy to zwykle zarządzać okres istnienia planista kompozycji. Gdy liczebności referencyjnej harmonogramu spadnie do zera, harmonogram zostanie zamknięty i destruct się po pracy w ramach harmonogramu zadań została ukończona.  
  
 Metoda zgłosi [improper_scheduler_reference —](improper-scheduler-reference-class.md) wyjątek, jeśli liczba odwołanie przed wywołaniem `Reference` metody wynosi zero i połączenie jest nawiązywane z kontekstu, która nie jest właścicielem przez harmonogram.  
  
##  <a name="registershutdownevent"></a> RegisterShutdownEvent 

 Powoduje, że obsługi zdarzeń systemu Windows przekazany `_Event` parametr, aby zostać zgłoszony, gdy harmonogram zamyka i niszczy się. W czasie, które zdarzenie jest sygnalizowane wszystkie pracy, który miał zostało zaplanowane do harmonogramu zostanie zakończona. Za pomocą tej metody można zarejestrować wiele zdarzeń zamknięcia systemu.  
  
```
virtual void RegisterShutdownEvent(HANDLE _Event) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_Event`  
 Dojście do obiektu zdarzeń systemu Windows, która sygnalizuje przez środowisko uruchomieniowe przy planista zamyka i niszczy sam.  
  
##  <a name="release"></a> Zlecenia 

 Zmniejsza liczba odwołanie harmonogramu.  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba odwołań nowo zmniejszany.  
  
### <a name="remarks"></a>Uwagi  
 Służy to zwykle zarządzać okres istnienia planista kompozycji. Gdy liczebności referencyjnej harmonogramu spadnie do zera, harmonogram zostanie zamknięty i destruct się po pracy w ramach harmonogramu zadań została ukończona.  
  
##  <a name="resetdefaultschedulerpolicy"></a> ResetDefaultSchedulerPolicy 

 Przywraca domyślne zasady harmonogramu domyślnej środowiska uruchomieniowego. Przy następnym harmonogram domyślny jest tworzony, zostanie użyty domyślne ustawienia zasad środowiska uruchomieniowego.  
  
```
static void __cdecl ResetDefaultSchedulerPolicy();
```  
  
### <a name="remarks"></a>Uwagi  
 Tę metodę można wywołać podczas harmonogram domyślny istnieje w ramach procesu. Nie zostaną zastosowane zasady istniejący harmonogram domyślny. Jednak jeśli domyślny harmonogram zamknięcia, i zostały nowym domyślnym ma zostać utworzony w późniejszym czasie, nowy harmonogram użyje domyślne ustawienia zasad środowiska uruchomieniowego.  
  
##  <a name="ctor"></a> Harmonogram 

 Obiekt `Scheduler` klasy można tylko utworzone za pomocą metody fabryki, albo niejawnie.  
  
```
Scheduler();
```  
  
### <a name="remarks"></a>Uwagi  
 Harmonogram domyślny procesu jest tworzona niejawnie po wielu funkcji środowiska uruchomieniowego wymagających harmonogramu jest dołączony do wywoływania kontekst wykorzystywać. Metody w ramach `CurrentScheduler` klasy i funkcje warstw PPL i agentów na ogół wykonać niejawnej załącznika.  
  
 Można także utworzyć harmonogram jawnie przy użyciu jednej `CurrentScheduler::Create` metody lub `Scheduler::Create` metody.  
  
##  <a name="dtor"></a> ~ Harmonogramu 

 Obiekt `Scheduler` klasy niejawnie zostanie zniszczony, gdy wszystkie zewnętrzne odwołania do niego przestaną istnieć.  
  
```
virtual ~Scheduler();
```  
  
##  <a name="scheduletask"></a> ScheduleTask 

 Zaplanowane zadania lekki w ramach harmonogramu zadań. Zadanie lekki zostaną umieszczone w grupie harmonogram określone przez środowisko uruchomieniowe. Wersja, która przyjmuje parametr `_Placement` powoduje zadania można ukierunkowane pod kątem wykonywania w określonej lokalizacji.  
  
```
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;

virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_Proc`  
 Wskaźnik do funkcji w celu wykonania do wykonywania zadań lekki treści.  
  
 `_Data`  
 Void wskaźnik do danych, który zostanie przekazany jako parametr do treści zadania.  
  
 `_Placement`  
 Odwołanie do lokalizacji, w którym zadanie lekki będzie można ukierunkowane pod kątem wykonywania w.  
  
##  <a name="setdefaultschedulerpolicy"></a> SetDefaultSchedulerPolicy 

 Umożliwia ma być używany do tworzenia harmonogramu domyślne zasady zdefiniowane przez użytkownika. Tę metodę można wywołać tylko wtedy, gdy nie domyślnego harmonogramu istnieje w ramach procesu. Po ustawieniu domyślne zasady obowiązujące pozostaje aż do następnego wywołania nieprawidłowy albo `SetDefaultSchedulerPolicy` lub [ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy) metody.  
  
```
static void __cdecl SetDefaultSchedulerPolicy(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>Parametry  
 `_Policy`  
 Zasady można ustawić jako domyślne zasady harmonogramu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `SetDefaultSchedulerPolicy` metoda jest wywoływana, gdy domyślnego harmonogramu już istnieje w ramach procesu, zgłosi środowiska uruchomieniowego [default_scheduler_exists —](default-scheduler-exists-class.md) wyjątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Klasa harmonogramu](scheduler-class.md)   
 [Policyelementkey —](concurrency-namespace-enums.md)   
 [Harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



