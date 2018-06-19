---
title: Klasy kontekstu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- Context
- CONCRT/concurrency::Context
- CONCRT/concurrency::Context::Block
- CONCRT/concurrency::Context::CurrentContext
- CONCRT/concurrency::Context::GetId
- CONCRT/concurrency::Context::GetScheduleGroupId
- CONCRT/concurrency::Context::GetVirtualProcessorId
- CONCRT/concurrency::Context::Id
- CONCRT/concurrency::Context::IsCurrentTaskCollectionCanceling
- CONCRT/concurrency::Context::IsSynchronouslyBlocked
- CONCRT/concurrency::Context::Oversubscribe
- CONCRT/concurrency::Context::ScheduleGroupId
- CONCRT/concurrency::Context::Unblock
- CONCRT/concurrency::Context::VirtualProcessorId
- CONCRT/concurrency::Context::Yield
dev_langs:
- C++
helpviewer_keywords:
- Context class
ms.assetid: c0d553f3-961d-4ecd-9a29-4fa4351673b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4bf574fc679b879e2fa9084ed6fbd4ed82e66f70
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694183"
---
# <a name="context-class"></a>Context — Klasa
Reprezentuje abstrakcję do kontekstu wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```
class Context;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="protected-constructors"></a>Konstruktory chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[~ Context — destruktor](#dtor)||  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Blok](#block)|Blokuje bieżącego kontekstu.|  
|[CurrentContext](#currentcontext)|Zwraca wskaźnik do bieżącego kontekstu.|  
|[GetId](#getid)|Zwraca identyfikator kontekstu, która jest unikatowa w ramach harmonogramu, do którego należy kontekst.|  
|[GetScheduleGroupId](#getschedulegroupid)|Zwraca identyfikator grupy harmonogram, który aktualnie pracuje kontekstu.|  
|[GetVirtualProcessorId](#getvirtualprocessorid)|Zwraca identyfikator procesora wirtualnego, który kontekstu jest aktualnie wykonywany.|  
|[Id](#id)|Zwraca identyfikator bieżącego kontekstu, która jest unikatowa w ramach harmonogramu, do którego należy bieżący kontekst.|  
|[IsCurrentTaskCollectionCanceling](#iscurrenttaskcollectioncanceling)|Zwraca moduł wskazanie, czy kolekcję zadań, która jest aktualnie wykonywany wbudowany w bieżącym kontekście jest pośrodku active anulowania (lub zostanie wkrótce).|  
|[IsSynchronouslyBlocked](#issynchronouslyblocked)|Określa, czy kontekst synchronicznie jest zablokowany. Kontekst jest uważana za synchronicznie zablokowane, jeśli jawnie wykonać akcji, które doprowadziło do blokowania.|  
|[Oversubscribe](#oversubscribe)|Injects dodatkowych procesorów wirtualnych do harmonogramu, czas trwania bloku kodu, gdy została wywołana w kontekście wykonywanych na jeden z procesorów wirtualnych w tym harmonogramu.|  
|[ScheduleGroupId](#schedulegroupid)|Zwraca identyfikator grupy harmonogram, który pracuje bieżącego kontekstu.|  
|[Odblokowywanie](#unblock)|Odblokowuje kontekstu i powoduje, że usługa będzie do uruchomienia.|  
|[VirtualProcessorId](#virtualprocessorid)|Zwraca identyfikator procesora wirtualnego, który jest wykonywany bieżący kontekst.|  
|[Yield](#yield)|Przekazuje wykonywanie, dzięki czemu możliwe wykonanie innego kontekstu. Jeśli kontekst nie jest dostępny umożliwiające uzyskanie do, harmonogram umożliwia uzyskanie do innego wątku systemu operacyjnego.|  
  
## <a name="remarks"></a>Uwagi  
 Harmonogram współbieżność środowiska wykonawczego (zobacz [harmonogramu](scheduler-class.md)) kontekstów wykonywania używana do wykonywania pracy w kolejce do niej przez aplikację. Wątek Win32 jest przykładem kontekstu wykonywania w systemie operacyjnym Windows.  
  
 W dowolnym momencie poziom współbieżności harmonogramu jest równa liczbie procesorów wirtualnych przyznane przez Menedżera zasobów. Procesor wirtualny jest abstrakcją zasoby przetwarzania i map do wątku sprzętu na podstawowym systemie. W kontekście jednego harmonogramu można wykonywać w procesorów wirtualnych w danym momencie.  
  
 Harmonogram jest współpracy charakteru i kontekst wykonywania może spowodować jego procesorów wirtualnych do innego kontekstu w dowolnym momencie, jeśli chcą, aby przejść w stan oczekiwania. Gdy jej oczekiwania jest spełniony, go nie można wznowić do momentu rozpoczęcia dostępnych procesorów wirtualnych z harmonogramu jej wykonanie.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Context`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="block"></a> Blok 

 Blokuje bieżącego kontekstu.  
  
```
static void __cdecl Block();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda spowoduje procesu domyślnego harmonogramu są tworzone i/lub dołączyć do wywoływania kontekstu, jeśli nie harmonogramu aktualnie skojarzony z kontekstem wywoływania.  
  
 Jeśli kontekst wywołania działa na procesorów wirtualnych, procesora wirtualnego będą dostępne kontekst do uruchomienia na wykonanie lub potencjalnie można utworzyć nowy.  
  
 Po `Block` metoda została wywołana lub zostanie wywołana, sparowaniu jej z wywołaniem do [Odblokuj](#unblock) metody z innego kontekstu wykonywania w celu jej ponowne uruchomienie. Należy pamiętać, że między punktem, w którym kod publikuje jego kontekstu na inny wątek można było wywołać okresie krytycznym `Unblock` — metoda i punkt gdzie wywołanie metody rzeczywiste `Block` staje się. W tym okresie nie należy wywołać dowolnej metody, która z kolei można blokować i odblokowywać własną przyczyn (na przykład uzyskiwanie blokady). Wywołuje się `Block` i `Unblock` metody żądania nie Śledź przyczynę zablokowania i odblokowania. Tylko jeden obiekt powinien mieć prawo własności `Block` -  `Unblock` pary.  
  
 Ta metoda może zgłosić różne wyjątki, w tym [scheduler_resource_allocation_error —](scheduler-resource-allocation-error-class.md).  
  
##  <a name="dtor"></a> ~ Kontekst 

```
virtual ~Context();
```  
  
##  <a name="currentcontext"></a> CurrentContext 

 Zwraca wskaźnik do bieżącego kontekstu.  
  
```
static Context* __cdecl CurrentContext();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bieżącego kontekstu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda spowoduje procesu domyślnego harmonogramu są tworzone i/lub dołączyć do wywoływania kontekstu, jeśli nie harmonogramu aktualnie skojarzony z kontekstem wywoływania.  
  
##  <a name="getid"></a> GetId 

 Zwraca identyfikator kontekstu, która jest unikatowa w ramach harmonogramu, do którego należy kontekst.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator kontekstu, która jest unikatowa w ramach harmonogramu, do którego należy kontekst.  
  
##  <a name="getschedulegroupid"></a> GetScheduleGroupId 

 Zwraca identyfikator grupy harmonogram, który aktualnie pracuje kontekstu.  
  
```
virtual unsigned int GetScheduleGroupId() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator grupy harmonogram kontekście pracuje nad.  
  
### <a name="remarks"></a>Uwagi  
 Wartość zwrócona przez tę metodę jest natychmiastowe próbkowania grupy harmonogram wykonywany w kontekście. Jeśli ta metoda jest wywoływana w kontekście innym niż bieżący kontekst, możliwe wartości starych obecnie jest zwracany i nie może być stosowane. Zwykle ta metoda jest używana do debugowania i śledzenia tylko do celów.  
  
##  <a name="getvirtualprocessorid"></a> GetVirtualProcessorId 

 Zwraca identyfikator procesora wirtualnego, który kontekstu jest aktualnie wykonywany.  
  
```
virtual unsigned int GetVirtualProcessorId() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli kontekst jest aktualnie wykonywanych na procesor wirtualny identyfikator procesora wirtualnego, który kontekstu jest aktualnie wykonywany. w przeciwnym razie wartość `-1`.  
  
### <a name="remarks"></a>Uwagi  
 Wartość zwrócona przez tę metodę jest natychmiastowe próbkowania procesora wirtualnego, wykonywany w kontekście. Ta wartość może być nieodświeżona obecnie jest zwracany i nie może opierać się. Zwykle ta metoda jest używana do debugowania i śledzenia tylko do celów.  
  
##  <a name="id"></a> Id 

 Zwraca identyfikator bieżącego kontekstu, która jest unikatowa w ramach harmonogramu, do którego należy bieżący kontekst.  
  
```
static unsigned int __cdecl Id();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli bieżący kontekst jest dołączony do harmonogramu, identyfikator dla bieżącego kontekstu, która jest unikatowa w ramach harmonogramu, do którego należy bieżący kontekst; w przeciwnym razie wartość `-1`.  
  
##  <a name="iscurrenttaskcollectioncanceling"></a> IsCurrentTaskCollectionCanceling 

 Zwraca moduł wskazanie, czy kolekcję zadań, która jest aktualnie wykonywany wbudowany w bieżącym kontekście jest pośrodku active anulowania (lub zostanie wkrótce).  
  
```
static bool __cdecl IsCurrentTaskCollectionCanceling();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli harmonogramu jest dołączony do wywoływania kontekstu i grupy zadań jest wykonywany wbudowanego zadania w tym kontekście, wskazanie czy tej grupy zadań jest pośrodku active anulowania (lub będzie wkrótce); w przeciwnym razie wartość `false`.  
  
##  <a name="issynchronouslyblocked"></a> IsSynchronouslyBlocked 

 Określa, czy kontekst synchronicznie jest zablokowany. Kontekst jest uważana za synchronicznie zablokowane, jeśli jawnie wykonać akcji, które doprowadziło do blokowania.  
  
```
virtual bool IsSynchronouslyBlocked() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Określa, czy kontekst synchronicznie jest zablokowany.  
  
### <a name="remarks"></a>Uwagi  
 Kontekst jest uważana za synchronicznie zablokowane, jeśli jawnie wykonać akcji, które doprowadziło do blokowania. W harmonogramie wątku oznaczałoby to bezpośrednie wywołanie `Context::Block` metoda lub obiekt synchronizacji, który został utworzony przy użyciu `Context::Block` metody.  
  
 Wartość zwrócona przez tę metodę jest natychmiastowe przykład tego, czy kontekst synchronicznie jest zablokowany. Ta wartość może być przestarzały obecnie jest zwracany i można używać tylko w bardzo określonych warunkach.  
  
##  <a name="operator_delete"></a> Usuwanie operatora 

 A `Context` obiekt zostanie zniszczony wewnętrznie przez środowisko uruchomieniowe. Go może nie zostać jawnie usunięte.  
  
```
void operator delete(void* _PObject);
```  
  
### <a name="parameters"></a>Parametry  
 `_PObject`  
 Wskaźnik do obiektu, który ma zostać usunięty.  
  
##  <a name="oversubscribe"></a> Oversubscribe 

 Injects dodatkowych procesorów wirtualnych do harmonogramu, czas trwania bloku kodu, gdy została wywołana w kontekście wykonywanych na jeden z procesorów wirtualnych w tym harmonogramu.  
  
```
static void __cdecl Oversubscribe(bool _BeginOversubscription);
```  
  
### <a name="parameters"></a>Parametry  
 `_BeginOversubscription`  
 Jeśli `true`, wskazanie, że procesor bardzo wirtualnego należy dodać w czasie trwania nadsubskrypcji. Jeśli `false`, wskazanie, że nadsubskrypcji należy zakończyć i uprzednio dodanych procesorów wirtualnych powinna zostać usunięta.  
  
##  <a name="schedulegroupid"></a> ScheduleGroupId 

 Zwraca identyfikator grupy harmonogram, który pracuje bieżącego kontekstu.  
  
```
static unsigned int __cdecl ScheduleGroupId();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli bieżący kontekst jest dołączona do harmonogramu i pracy w grupie harmonogramu, identyfikator harmonogramu grupy, która bieżącego kontekstu pracuje nad; w przeciwnym razie wartość `-1`.  
  
##  <a name="unblock"></a> Odblokowywanie 

 Odblokowuje kontekstu i powoduje, że usługa będzie do uruchomienia.  
  
```
virtual void Unblock() = 0;
```  
  
### <a name="remarks"></a>Uwagi  
 Doskonale dozwolone wywołania `Unblock` metoda przed odpowiedniego wywołania [bloku](#block) metody. Tak długo, jak wywołania `Block` i `Unblock` metody są poprawnie skojarzone, środowisko uruchomieniowe poprawnie obsługuje fizycznych wyścigu albo kolejności. `Unblock` Wywołania pochodzące przed `Block` wywołania po prostu Negacja efekt `Block` wywołania.  
  
 Istnieje kilka wyjątków, które może zostać wygenerowany przez tę metodę. Jeśli kontekst próby wywołania `Unblock` metody dla samej siebie, [context_self_unblock —](context-self-unblock-class.md) zostanie wygenerowany wyjątek. Jeśli wywołań `Block` i `Unblock` nie są poprawnie skojarzone (na przykład dwa wywołań `Unblock` są wykonywane dla kontekstu, który jest obecnie uruchomiona), [context_unblock_unbalanced —](context-unblock-unbalanced-class.md) zostanie wygenerowany wyjątek.  
  
 Należy pamiętać, że między punktem, w którym kod publikuje jego kontekstu na inny wątek można było wywołać okresie krytycznym `Unblock` — metoda i punkt gdzie wywołanie metody rzeczywiste `Block` staje się. W tym okresie nie należy wywołać dowolnej metody, która z kolei można blokować i odblokowywać własną przyczyn (na przykład uzyskiwanie blokady). Wywołuje się `Block` i `Unblock` metody żądania nie Śledź przyczynę zablokowania i odblokowania. Tylko jeden obiekt powinien mieć prawo własności `Block` i `Unblock` pary.  
  
##  <a name="virtualprocessorid"></a> VirtualProcessorId 

 Zwraca identyfikator procesora wirtualnego, który jest wykonywany bieżący kontekst.  
  
```
static unsigned int __cdecl VirtualProcessorId();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli bieżący kontekst jest dołączony do harmonogramu, identyfikator procesora wirtualnego, wykonywanego w bieżącym kontekście. w przeciwnym razie wartość `-1`.  
  
### <a name="remarks"></a>Uwagi  
 Wartość zwrócona przez tę metodę jest natychmiastowe próbkowania procesora wirtualnego, który jest wykonywany bieżący kontekst. Ta wartość może być nieodświeżona obecnie jest zwracany i nie może opierać się. Zwykle ta metoda jest używana do debugowania i śledzenia tylko do celów.  
  
##  <a name="yield"></a> YIELD 

 Przekazuje wykonywanie, dzięki czemu możliwe wykonanie innego kontekstu. Jeśli kontekst nie jest dostępny umożliwiające uzyskanie do, harmonogram umożliwia uzyskanie do innego wątku systemu operacyjnego.  
  
```
static void __cdecl Yield();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda spowoduje procesu domyślnego harmonogramu są tworzone i/lub dołączyć do wywoływania kontekstu, jeśli nie harmonogramu aktualnie skojarzony z kontekstem wywoływania.  
  
##  <a name="yieldexecution"></a> YieldExecution 

 Przekazuje wykonywanie, dzięki czemu możliwe wykonanie innego kontekstu. Jeśli kontekst nie jest dostępny umożliwiające uzyskanie do, harmonogram umożliwia uzyskanie do innego wątku systemu operacyjnego.  
  
```
static void __cdecl YieldExecution();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda spowoduje procesu domyślnego harmonogramu są tworzone i/lub dołączyć do wywoływania kontekstu, jeśli nie harmonogramu aktualnie skojarzony z kontekstem wywoływania.  
  
 Ta funkcja jest nowa w programie [!INCLUDE[vs_dev14](../../../ide/includes/vs_dev14_md.md)] i takie same jak [Yield](#yield) działać, ale nie powoduje konfliktu z makra Yield w Windows.h.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Klasa harmonogramu](scheduler-class.md)   
 [Harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



