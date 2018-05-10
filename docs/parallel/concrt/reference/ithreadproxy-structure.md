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
ms.openlocfilehash: fbf59302a73374f08f1c226c1e7e56202654dcfb
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="ithreadproxy-structure"></a>IThreadProxy — Struktura
Abstrakcja dla wątku wykonywania. W zależności od `SchedulerType` klucza zasad harmonogramu tworzenia, Menedżer zasobów zostanie przyznać użytkownikowi proxy wątku, który nie jest obsługiwana przez regularne wątku Win32 lub schedulable wątku trybu użytkownika (UMS). UMS wątki są obsługiwane w 64-bitowych systemach operacyjnych z wersji Windows 7 lub nowszy.  
  
## <a name="syntax"></a>Składnia  
  
```
struct IThreadProxy;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IThreadProxy::GetId](#getid)|Zwraca unikatowy identyfikator dla serwera proxy wątku.|  
|[IThreadProxy::SwitchOut](#switchout)|Usuwa skojarzenia kontekstu z podstawowej procesora wirtualnego katalogu głównego.|  
|[IThreadProxy::SwitchTo](#switchto)|Wykonuje przełączanie kontekstu współpracy z aktualnie wykonywane kontekstu do innego.|  
|[IThreadProxy::YieldToSystem](#yieldtosystem)|Powoduje, że wątek wywołujący umożliwiające uzyskanie wykonywania do innego wątku, który jest gotowy do uruchomienia na bieżącym procesora. System operacyjny wybierze następnego wątku do wykonania.|  
  
## <a name="remarks"></a>Uwagi  
 Wątek serwery proxy są powiązane do wykonywania kontekstów reprezentowany przez interfejs `IExecutionContext` jako sposób wysyłania pracy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IThreadProxy`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrtrm.h  
  
 **Namespace:** współbieżności  
  
##  <a name="getid"></a>  IThreadProxy::GetId — metoda  
 Zwraca unikatowy identyfikator dla serwera proxy wątku.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator unikatowy liczby całkowitej.  
  
##  <a name="switchout"></a>  IThreadProxy::SwitchOut — metoda  
 Usuwa skojarzenia kontekstu z podstawowej procesora wirtualnego katalogu głównego.  
  
```
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `switchState`  
 Wskazuje stan serwera proxy w wątku, który jest wykonywany przełącznika. Parametr jest typu `SwitchingProxyState`.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `SwitchOut` Jeśli musisz usunąć skojarzenie kontekstu z procesora wirtualnego katalogu głównego wykonywania jakiejkolwiek przyczyny. W zależności od wartości przekazywane w celu parametr `switchState`, i czy jej wykonywania w folderze głównym procesora wirtualnego, wywołanie zostanie natychmiast zwraca lub Blokuj proxy wątek skojarzony z kontekstem. Błąd do wywołania `SwitchOut` z parametrem ustawioną `Idle`. W ten sposób spowoduje [invalid_argument —](../../../standard-library/invalid-argument-class.md) wyjątku.  
  
 `SwitchOut` jest przydatne, gdy chcesz zmniejszyć liczbę procesorów wirtualnych katalogów głównych, ma użytkownika harmonogramu, ponieważ Menedżer zasobów zalecił Aby to zrobić, lub żądanie głównego tymczasowego oversubscribed procesora wirtualnego, a jego. W takim przypadku należy wywołać metodę [IVirtualProcessorRoot::Remove](http://msdn.microsoft.com/en-us/ad699b4a-1972-4390-97ee-9c083ba7d9e4) w katalogu głównym procesora wirtualnego, przed wykonaniem połączenia do `SwitchOut` z parametrem `switchState` ustawioną `Blocking`. Spowoduje to zablokowanie proxy wątku i wykonywania zostanie wznowione po udostępnieniu wykonania głównego różnych procesorów wirtualnych w harmonogramie. Blokowanie proxy wątku można wznawiać przez wywołanie funkcji `SwitchTo` Aby przełączyć się do kontekstu wykonywania tego wątku serwera proxy. Można również wznowić proxy wątku przy użyciu jego skojarzony żaden kontekst do aktywowania procesora wirtualnego katalogu głównego. Aby uzyskać więcej informacji, jak to zrobić, zobacz [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate).  
  
 `SwitchOut` może również należy ponownie zainicjować procesorów wirtualnych, więc go może zachodzić w przyszłości podczas albo blokowania proxy wątku lub tymczasowo odłączenia z procesora wirtualnego katalogu głównego jest uruchomiona na i harmonogramu, jego wysyła pracy. Użyj `SwitchOut` z parametrem `switchState` ustawioną `Blocking` Jeśli chcesz zablokować proxy wątku. Później można wznowić, za pomocą `SwitchTo` lub `IVirtualProcessorRoot::Activate` wspomnianego powyżej. Użyj `SwitchOut` z parametrem ustawioną `Nesting` gdy chcesz tymczasowo odłączyć proxy tego wątku z procesora wirtualnego katalogu głównego jest uruchomiona na i harmonogram procesora wirtualnego jest skojarzony z. Wywoływanie `SwitchOut` z parametrem `switchState` ustawioną `Nesting` podczas wykonywania w folderze głównym procesora wirtualnego spowoduje katalogu głównym, aby można ponownie zainicjować i bieżącego serwera proxy wątku, aby kontynuować bez konieczności dla jednego. Proxy wątek jest uważany za jeszcze harmonogramu, aż wywołuje [IThreadProxy::SwitchOut](#switchout) metody z `Blocking` w późniejszym momencie. Drugie wywołanie `SwitchOut` z parametrem ustawioną `Blocking` ma na celu wróć kontekstu do stanu zablokowanych, aby może zostać wznowiony przez `SwitchTo` lub `IVirtualProcessorRoot::Activate` w harmonogramie ona odłączona od. Ponieważ nie powodowała w folderze głównym procesora wirtualnego, nie działa bez ponownego inicjowania.  
  
 Ponownie zainicjować procesora wirtualnego katalogu głównego nie różni się od nowego głównego procesora wirtualnego użytkownika harmonogramu zostały przyznane przez Menedżera zasobów. Można użyć do wykonania aktywować go z kontekstu wykonywania przy użyciu `IVirtualProcessorRoot::Activate`.  
  
 `SwitchOut` musi zostać wywołana w `IThreadProxy` interfejs, który reprezentuje aktualnie wykonywane wątku lub wyniki są niezdefiniowane.  
  
 W bibliotekach i nagłówki dostarczonych z programem Visual Studio 2010 ta metoda nie zostały parametrem i nie ponownie zainicjować głównego procesora wirtualnego. Aby zachować stare zachowanie, domyślna wartość parametru `Blocking` podano.  
  
##  <a name="switchto"></a>  IThreadProxy::SwitchTo — metoda  
 Wykonuje przełączanie kontekstu współpracy z aktualnie wykonywane kontekstu do innego.  
  
```
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pContext`  
 Aby przełączyć się wspólnie do kontekstu wykonywania.  
  
 `switchState`  
 Wskazuje stan serwera proxy w wątku, który jest wykonywany przełącznika. Parametr jest typu `SwitchingProxyState`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia przełączenie z kontekstu wykonywania jednego do drugiego, w z [IExecutionContext::Dispatch](iexecutioncontext-structure.md#dispatch) metody pierwszy kontekstu wykonywania. Metoda kojarzy kontekstu wykonywania `pContext` proxy wątku, jeśli nie jest już skojarzony z jednym. Własność bieżącego wątku serwera proxy jest określana przez wartość określona dla `switchState` argumentu.  
  
 Użyj wartości `Idle` Jeśli chcesz przywrócić aktualnie wykonywane proxy wątek Menedżera zasobów. Wywoływanie `SwitchTo` z parametrem `switchState` ustawioną `Idle` spowoduje, że kontekstu wykonywania `pContext` można uruchomić wykonywanie podstawowych zasobu wykonywania. Własności tego wątku serwera proxy są przesyłane do Menedżera zasobów i powinna zwrócić element z kontekstu wykonywania `Dispatch` metody wkrótce po `SwitchTo` zwraca, aby można było zakończyć transferu. Kontekst wykonywania, który proxy wątek został wysyłki jest oddzielone od serwera proxy wątku i harmonogram będzie mógł użyć go ponownie lub zniszcz go jako za stosowny.  
  
 Użyj wartości `Blocking` zużycia ten serwer proxy wątku, aby wprowadzić stan blokady. Wywoływanie `SwitchTo` z parametrem `switchState` ustawioną `Blocking` spowoduje, że kontekstu wykonywania `pContext` do uruchamiania wykonywania i zablokować bieżącego wątku serwera proxy, dopóki nie zostanie wznowione. Planista zachowuje własność proxy wątku, gdy wątek jest w `Blocking` stanu. Blokowanie proxy wątku można wznawiać przez wywołanie funkcji `SwitchTo` Aby przełączyć się do kontekstu wykonywania tego wątku serwera proxy. Można również wznowić proxy wątku przy użyciu jego skojarzony żaden kontekst do aktywowania procesora wirtualnego katalogu głównego. Aby uzyskać więcej informacji, jak to zrobić, zobacz [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate).  
  
 Użyj wartości `Nesting` gdy chcesz tymczasowo odłączyć proxy tego wątku z procesora wirtualnego katalogu głównego jest uruchomiona na i harmonogramu, jego wysyła pracy. Wywoływanie `SwitchTo` z parametrem `switchState` ustawioną `Nesting` spowoduje, że kontekstu wykonywania `pContext` rozpocząć wykonywania i bieżącego wątku proxy również kontynuuje wykonywanie bez konieczności procesora wirtualnego katalogu głównego. Proxy wątek jest uważany za jeszcze harmonogramu, aż wywołuje [IThreadProxy::SwitchOut](#switchout) metody w późniejszym momencie. `IThreadProxy::SwitchOut` — Metoda można zablokować proxy wątku do czasu udostępnienia je ponownie zaplanować procesora wirtualnego katalogu głównego.  
  
 `SwitchTo` musi zostać wywołana w `IThreadProxy` interfejs, który reprezentuje aktualnie wykonywane wątku lub wyniki są niezdefiniowane. Funkcja zwraca `invalid_argument` Jeśli parametr `pContext` ma ustawioną wartość `NULL`.  
  
##  <a name="yieldtosystem"></a>  IThreadProxy::YieldToSystem — metoda  
 Powoduje, że wątek wywołujący umożliwiające uzyskanie wykonywania do innego wątku, który jest gotowy do uruchomienia na bieżącym procesora. System operacyjny wybierze następnego wątku do wykonania.  
  
```
virtual void YieldToSystem() = 0;
```  
  
### <a name="remarks"></a>Uwagi  
 Po wywołaniu przez serwer proxy wątku przez wątek regularne Windows `YieldToSystem` zachowuje się tak samo jak funkcja Windows `SwitchToThread`. Jednakże, gdy jest wywoływana z schedulable wątków trybu użytkownika (UMS), `SwitchToThread` funkcja deleguje zadanie pobrania następnego wątku Uruchamianie harmonogramu trybu użytkownika, nie systemu operacyjnego. Aby osiągnąć żądany wpływ przełączenie do innego wątku gotowości w systemie, należy użyć `YieldToSystem`.  
  
 `YieldToSystem` musi zostać wywołana w `IThreadProxy` interfejs, który reprezentuje aktualnie wykonywane wątku lub wyniki są niezdefiniowane.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [IExecutionContext Structure](iexecutioncontext-structure.md)   
 [Struktura IScheduler](ischeduler-structure.md)   
 [IVirtualProcessorRoot, struktura](ivirtualprocessorroot-structure.md)
