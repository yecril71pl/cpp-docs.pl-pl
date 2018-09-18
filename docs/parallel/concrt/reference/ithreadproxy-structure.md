---
title: Ithreadproxy — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IThreadProxy
- CONCRTRM/concurrency::IThreadProxy
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::GetId
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchOut
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchTo
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::YieldToSystem
dev_langs:
- C++
helpviewer_keywords:
- IThreadProxy structure
ms.assetid: feb89241-a555-4e61-ad48-40add54daeca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3be0a32de4e0e5b57471722ffa2cf8fcea5fd6c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027859"
---
# <a name="ithreadproxy-structure"></a>IThreadProxy — Struktura
Abstrakcja wątku wykonywania. W zależności od `SchedulerType` klucza zasad harmonogramu tworzenia, Menedżer zasobów spowoduje przyznanie Ci proxy wątku, która jest wspierana przez regularne wątek Win32 lub wątku (UMS) ustalonych w harmonogramie trybu użytkownika. UMS wątki są obsługiwane w systemie 64-bitowych systemach operacyjnych z wersji Windows 7 lub nowszy.  
  
## <a name="syntax"></a>Składnia  
  
```
struct IThreadProxy;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IThreadProxy::GetId](#getid)|Zwraca unikatowy identyfikator dla serwera proxy wątku.|  
|[IThreadProxy::SwitchOut](#switchout)|Usuwa kontekst z podstawowego procesora wirtualnego katalogu głównego.|  
|[IThreadProxy::SwitchTo](#switchto)|Wykonuje przełączanie kontekstu współpracy z wykonywanym kontekstu do innego.|  
|[IThreadProxy::YieldToSystem](#yieldtosystem)|Powoduje, że wątek wywołujący, umożliwiające uzyskanie wykonywania do innego wątku, który jest gotowy do uruchomienia na bieżącym procesora. System operacyjny wybiera następny wątek do wykonania.|  
  
## <a name="remarks"></a>Uwagi  
 Serwery proxy wątku są ściśle do kontekstów wykonanie reprezentowany przez interfejs `IExecutionContext` jako środek wywołujący pracę.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IThreadProxy`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrtrm.h  
  
 **Namespace:** współbieżności  
  
##  <a name="getid"></a>  Ithreadproxy::getid — metoda  
 Zwraca unikatowy identyfikator dla serwera proxy wątku.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator unikatowy liczby całkowitej.  
  
##  <a name="switchout"></a>  IThreadProxy::SwitchOut — metoda  
 Usuwa kontekst z podstawowego procesora wirtualnego katalogu głównego.  
  
```
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```  
  
### <a name="parameters"></a>Parametry  
*switchState*<br/>
Wskazuje stan wątku proxy, który jest wykonywany przełącznika. Parametr jest typu `SwitchingProxyState`.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `SwitchOut` Jeśli musisz usunąć skojarzenie kontekstu z procesora wirtualnego katalogu głównego, wykonuje z jakiegokolwiek powodu. W zależności od wartości przekazanej do parametru `switchState`, i czy wykonywania w głównym procesorze wirtualnym, wywołanie zostanie niezwłocznie zawrócone lub zablokuje proxy wątku skojarzonego z kontekstem. Jest to błąd, aby wywołać `SwitchOut` z parametrem ustawionym `Idle`. Ten sposób spowoduje [invalid_argument](../../../standard-library/invalid-argument-class.md) wyjątku.  
  
 `SwitchOut` jest przydatne, gdy chcesz ograniczyć liczbę korzeni procesora wirtualnego, która ma swój harmonogram, ponieważ Menedżer zasobów nakazał Ci tak zrobić, lub żądany tymczasowe zażądałeś procesora wirtualnego katalogu głównego i skończyłeś. W takim przypadku należy wywołać metodę [IVirtualProcessorRoot::Remove](iexecutionresource-structure.md#remove) w głównym procesorze wirtualnym, przed wykonaniem połączenia do `SwitchOut` z parametrem `switchState` równa `Blocking`. Będzie to blok proxy wątku i wykonanie zostanie wznowione po udostępnieniu do wykonania go innemu głównemu procesorowi wirtualnemu w ramach harmonogramu zadań. Blokowanie serwera proxy wątku może być wznowione przez wywołanie funkcji `SwitchTo` Aby przełączyć się do kontekstu wykonania tego wątku serwera proxy. Można również wznowić proxy wątku za pomocą jego skojarzonego kontekstu, aby aktywować procesora wirtualnego katalogu głównego. Aby uzyskać więcej informacji na temat jak to zrobić, zobacz [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate).  
  
 `SwitchOut` można także gdy chcesz ponownie zainicjować Procesor wirtualny, aby mógł być aktywny w przyszłości podczas albo blokowania serwera proxy wątku lub tymczasowego odłączenia go od głównego procesora wirtualnego jest uruchomiona, a harmonogram wywołujący pracę dla. Użyj `SwitchOut` z parametrem `switchState` równa `Blocking` Jeśli chcesz blokować wątek serwera proxy. Później można wznowić, przy użyciu `SwitchTo` lub `IVirtualProcessorRoot::Activate` wymienionych powyżej. Użyj `SwitchOut` z parametrem ustawionym `Nesting` kiedy chcesz tymczasowo odłączyć ten serwer proxy wątku z procesora wirtualnego katalogu głównego, którym jest uruchomiony, a harmonogram procesora wirtualnego jest skojarzony z. Wywoływanie `SwitchOut` z parametrem `switchState` równa `Nesting` podczas wykonywania w głównym procesorze wirtualnym spowoduje, że główny należy ponownie zainicjować oraz bieżący wątek serwera proxy, aby kontynuować bez przeszkód. Serwer proxy wątku jest uważany za opuścił harmonogram, dopóki nie wywoła [IThreadProxy::SwitchOut](#switchout) metody z `Blocking` w dowolnym momencie w czasie. Drugie wywołanie `SwitchOut` z parametrem ustawionym `Blocking` jest przeznaczony do zwracania kontekstu zablokowanego stanu tak, aby może być wznowione przez którykolwiek `SwitchTo` lub `IVirtualProcessorRoot::Activate` dzięki usłudze scheduler jest odłączony. Ponieważ nie wykonuje się w głównym procesorze wirtualnym, nie odbywa się.  
  
 Ponownie zainicjalizowany Procesor wirtualny katalogu głównego nie różni się od całkiem nowe głównym procesorze wirtualnym, które usługi został przyznany do harmonogramu przez Menedżera zasobów. Można użyć do wykonania Aktywując go z kontekstu wykonania za pomocą `IVirtualProcessorRoot::Activate`.  
  
 `SwitchOut` musi zostać wywołana w `IThreadProxy` interfejs, który reprezentuje aktualnie wykonywany wątek lub wyniki są niezdefiniowane.  
  
 W bibliotekach i nagłówkach dostarczonych wraz z programem Visual Studio 2010 ta metoda nie podjęła parametru i nie inicjowała ponownie procesora wirtualnego katalogu głównego. Aby zachować stare zachowanie, domyślna wartość parametru `Blocking` jest dostarczany.  
  
##  <a name="switchto"></a>  Ithreadproxy::switchto — metoda  
 Wykonuje przełączanie kontekstu współpracy z wykonywanym kontekstu do innego.  
  
```
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```  
  
### <a name="parameters"></a>Parametry  
*pContext*<br/>
Kontekst wykonywania wspólne powoduje.  
  
*switchState*<br/>
Wskazuje stan wątku proxy, który jest wykonywany przełącznika. Parametr jest typu `SwitchingProxyState`.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby przełączyć się z kontekstu wykonania jednego do drugiego, z [iexecutioncontext::Dispatch —](iexecutioncontext-structure.md#dispatch) metoda pierwszy kontekstu wykonywania. Metoda kojarzy kontekstu wykonania `pContext` przy użyciu serwera proxy wątku, jeśli nie jest już skojarzony z jednym. Własność bieżący wątek serwera proxy jest określana przez wartość określona dla `switchState` argumentu.  
  
 Użyj wartości `Idle` gdy zachodzi potrzeba zwraca aktualnie wykonywany wątek serwera proxy do usługi Resource Manager. Wywoływanie `SwitchTo` z parametrem `switchState` równa `Idle` spowoduje, że kontekst wykonywania `pContext` można uruchomić wykonywania w bazowego zasobu wykonywania. Własności tego wątku serwera proxy są przesyłane do usługi Resource Manager i powinny zwracać z kontekstu wykonania `Dispatch` metoda wkrótce po `SwitchTo` zwraca, aby można było ukończyć przeniesienie. Kontekst wykonania wysyłki został wątek serwera proxy jest oddzielone od serwera proxy wątku, a harmonogram może użyć go ponownie lub zniszcz go, jak za stosowny.  
  
 Użyj wartości `Blocking` , aby ten serwer proxy wątku można wprowadzić stan blokady. Wywoływanie `SwitchTo` z parametrem `switchState` równa `Blocking` spowoduje, że kontekst wykonywania `pContext` rozpocząć wykonywanie i zablokować bieżący wątek serwera proxy, dopóki nie zostanie wznowione. Harmonogram zachowuje własność nad wątek serwera proxy, gdy wątek serwera proxy w `Blocking` stanu. Blokowanie serwera proxy wątku może być wznowione przez wywołanie funkcji `SwitchTo` Aby przełączyć się do kontekstu wykonania tego wątku serwera proxy. Można również wznowić proxy wątku za pomocą jego skojarzonego kontekstu, aby aktywować procesora wirtualnego katalogu głównego. Aby uzyskać więcej informacji na temat jak to zrobić, zobacz [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate).  
  
 Użyj wartości `Nesting` gdy chcesz tymczasowo odłączyć ten serwer proxy wątku z procesora wirtualnego katalogu głównego, którym jest uruchomiony, a harmonogram wywołujący pracę dla. Wywoływanie `SwitchTo` z parametrem `switchState` równa `Nesting` spowoduje, że kontekst wykonywania `pContext` rozpoczęcie wykonywania i bieżący wątek serwera proxy również kontynuuje wykonywanie bez konieczności procesora wirtualnego katalogu głównego. Serwer proxy wątku jest uważany za opuścił harmonogram, dopóki nie wywoła [IThreadProxy::SwitchOut](#switchout) metody w dowolnym momencie w czasie. `IThreadProxy::SwitchOut` Metoda może zablokować wątek serwera proxy do czasu udostępnienia je ponownie zaplanować procesora wirtualnego katalogu głównego.  
  
 `SwitchTo` musi zostać wywołana w `IThreadProxy` interfejs, który reprezentuje aktualnie wykonywany wątek lub wyniki są niezdefiniowane. Funkcja zgłasza `invalid_argument` Jeśli parametr `pContext` ustawiono `NULL`.  
  
##  <a name="yieldtosystem"></a>  Ithreadproxy::yieldtosystem — metoda  
 Powoduje, że wątek wywołujący, umożliwiające uzyskanie wykonywania do innego wątku, który jest gotowy do uruchomienia na bieżącym procesora. System operacyjny wybiera następny wątek do wykonania.  
  
```
virtual void YieldToSystem() = 0;
```  
  
### <a name="remarks"></a>Uwagi  
 Po wywołaniu przez serwer proxy wątku, wspierane przez regularne wątku Windows `YieldToSystem` zachowuje się tak samo jak funkcja Windows `SwitchToThread`. Jednakże, gdy wywoływane z wątków ustalonych w harmonogramie (UMS) trybu użytkownika `SwitchToThread` funkcja deleguje zadania pobrania następny wątek, aby uruchomić harmonogram trybu użytkownika, nie od systemu operacyjnego. Aby osiągnąć żądany wpływ przełączenie do innego wątku gotowe w systemie, należy użyć `YieldToSystem`.  
  
 `YieldToSystem` musi zostać wywołana w `IThreadProxy` interfejs, który reprezentuje aktualnie wykonywany wątek lub wyniki są niezdefiniowane.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [IExecutionContext Structure](iexecutioncontext-structure.md)   
 [IScheduler, struktura](ischeduler-structure.md)   
 [IVirtualProcessorRoot, struktura](ivirtualprocessorroot-structure.md)
