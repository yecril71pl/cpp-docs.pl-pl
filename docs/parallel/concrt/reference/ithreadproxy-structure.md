---
title: IThreadProxy — Struktura
ms.date: 11/04/2016
f1_keywords:
- IThreadProxy
- CONCRTRM/concurrency::IThreadProxy
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::GetId
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchOut
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchTo
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::YieldToSystem
helpviewer_keywords:
- IThreadProxy structure
ms.assetid: feb89241-a555-4e61-ad48-40add54daeca
ms.openlocfilehash: fc2fb2df06225a5c963fe39178c1b4a10f77953d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368126"
---
# <a name="ithreadproxy-structure"></a>IThreadProxy — Struktura

Abstrakcja dla wątku wykonania. W zależności `SchedulerType` od klucza zasad utworzonego harmonogramu Menedżer zasobów przyzna ci serwer proxy wątku, który jest wspierany przez zwykły wątek Win32 lub wątek w trybie UMS (UMS). Wątki UMS są obsługiwane w 64-bitowych systemach operacyjnych w wersji Windows 7 lub nowszej.

## <a name="syntax"></a>Składnia

```cpp
struct IThreadProxy;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IThreadProxy::GetId](#getid)|Zwraca unikatowy identyfikator serwera proxy wątku.|
|[IThreadProxy::SwitchOut](#switchout)|Disassociates kontekstu z podstawowego katalogu głównego procesora wirtualnego.|
|[IThreadProxy::SwitchTo](#switchto)|Wykonuje przełączanie kontekstu współpracy z aktualnie wykonywanego kontekstu do innego.|
|[IThreadProxy::YieldToSystem](#yieldtosystem)|Powoduje, że wątek wywołujący do wykonania do innego wątku, który jest gotowy do uruchomienia na bieżącym procesorze. System operacyjny wybiera następny wątek do wykonania.|

## <a name="remarks"></a>Uwagi

Serwery proxy wątku są powiązane z kontekstami `IExecutionContext` wykonywania reprezentowane przez interfejs jako środek wysyłki pracy.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IThreadProxy`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Przestrzeń nazw:** współbieżność

## <a name="ithreadproxygetid-method"></a><a name="getid"></a>IThreadProxy::Metoda GetId

Zwraca unikatowy identyfikator serwera proxy wątku.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Unikatowy identyfikator liczby całkowitej.

## <a name="ithreadproxyswitchout-method"></a><a name="switchout"></a>IThreadProxy::Metoda wyłączenia

Disassociates kontekstu z podstawowego katalogu głównego procesora wirtualnego.

```cpp
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```

### <a name="parameters"></a>Parametry

*switchState*<br/>
Wskazuje stan serwera proxy wątku, który wykonuje przełącznik. Parametr jest typu `SwitchingProxyState`.

### <a name="remarks"></a>Uwagi

Użyj, `SwitchOut` jeśli chcesz odłączyć kontekst od katalogu głównego procesora wirtualnego, na który jest wykonywany, z jakiegokolwiek powodu. W zależności od wartości przekazywania do parametru `switchState`i tego, czy jest on wykonywany w katalogu głównym procesora wirtualnego, wywołanie zwróci natychmiast lub zablokuje serwer proxy wątku skojarzony z kontekstem. Jest to błąd, `SwitchOut` aby wywołać `Idle`z parametrem ustawionym na . Spowoduje to [wyjątek invalid_argument.](../../../standard-library/invalid-argument-class.md)

`SwitchOut`jest to przydatne, gdy chcesz zmniejszyć liczbę katalogów głównych procesora wirtualnego, które ma harmonogram, ponieważ Menedżer zasobów polecił ci to zrobić, lub ponieważ zażądano tymczasowego katalogu głównego procesora wirtualnego z nadmierną subskrypcją i są z nim wykonywane. W takim przypadku należy wywołać metodę [IVirtualProcessorRoot::Usuń](iexecutionresource-structure.md#remove) w katalogu głównym `SwitchOut` procesora `switchState` wirtualnego, przed wywołaniem z parametrem ustawionym na `Blocking`. Spowoduje to zablokowanie serwera proxy wątku i wznowi wykonanie, gdy inny katalog główny procesora wirtualnego w harmonogramie jest dostępny do jego wykonania. Blokowanie serwera proxy wątku można wznowić, wywołując funkcję, `SwitchTo` aby przełączyć się do kontekstu wykonywania tego serwera proxy wątku. Można również wznowić proxy wątku, używając skojarzonego kontekstu, aby aktywować katalog główny procesora wirtualnego. Aby uzyskać więcej informacji na temat tego, zobacz [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate).

`SwitchOut`może być również używany, gdy chcesz ponownie zainicjować procesor wirtualny, aby mógł zostać aktywowany w przyszłości podczas blokowania serwera proxy wątku lub tymczasowego odłączenia go od katalogu głównego procesora wirtualnego, na którym jest uruchomiony, i harmonogram, dla którego wysyła pracę. Użyj `SwitchOut` z `switchState` parametrem `Blocking` ustawionym na, jeśli chcesz zablokować serwer proxy wątku. Później można go wznowić `SwitchTo` za `IVirtualProcessorRoot::Activate` pomocą jednego lub jak wspomniano powyżej. Użyj `SwitchOut` z parametrem `Nesting` ustawionym na to, kiedy chcesz tymczasowo odłączyć ten serwer proxy wątku od katalogu głównego procesora wirtualnego, na którym jest uruchomiony, i harmonogramu, z którym jest skojarzony procesor wirtualny. Wywołanie `SwitchOut` z `switchState` parametrem ustawionym na `Nesting` podczas wykonywania na głównym procesorze wirtualnym spowoduje ponowne zainicjowanie katalogu głównego i kontynuowanie wykonywania bieżącego serwera proxy wątku bez konieczności ich wykonywania. Serwer proxy wątku jest uważany za opuścił harmonogram, dopóki nie wywołuje [IThreadProxy::SwitchOut](#switchout) metody w `Blocking` późniejszym momencie w czasie. Drugie wywołanie `SwitchOut` z parametrem `Blocking` ustawionym na ma na celu zwrócenie kontekstu do stanu `SwitchTo` zablokowanego, dzięki czemu można go wznowić przez albo lub `IVirtualProcessorRoot::Activate` w harmonogramie, od którego jest odłączony. Ponieważ nie był wykonywany na głównym procesorze wirtualnym, nie ma miejsca ponowne zainicjowanie.

Ponownie zainicjowany katalog główny procesora wirtualnego nie różni się od nowego katalogu głównego procesora wirtualnego, który został przyznany przez Menedżera zasobów. Można go użyć do wykonania, aktywując `IVirtualProcessorRoot::Activate`go w kontekście wykonania przy użyciu .

`SwitchOut`musi być wywoływana w interfejsie, `IThreadProxy` który reprezentuje aktualnie wykonywany wątek lub wyniki są niezdefiniowane.

W bibliotekach i nagłówkach dostarczanych z programem Visual Studio 2010 ta metoda nie została uwzględniona i nie zainicjowała ponownie katalogu głównego procesora wirtualnego. Aby zachować stare zachowanie, `Blocking` podana jest domyślna wartość parametru.

## <a name="ithreadproxyswitchto-method"></a><a name="switchto"></a>IThreadProxy::SwitchTo Metoda

Wykonuje przełączanie kontekstu współpracy z aktualnie wykonywanego kontekstu do innego.

```cpp
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```

### <a name="parameters"></a>Parametry

*Pcontext*<br/>
Kontekst wykonywania, do który można wspólnie przełączyć.

*switchState*<br/>
Wskazuje stan serwera proxy wątku, który wykonuje przełącznik. Parametr jest typu `SwitchingProxyState`.

### <a name="remarks"></a>Uwagi

Ta metoda służy do przełączania z jednego kontekstu wykonywania do innego, z [IExecutionContext::Dispatch](iexecutioncontext-structure.md#dispatch) metody pierwszego kontekstu wykonywania. Metoda kojarzy kontekst `pContext` wykonywania z serwerem proxy wątku, jeśli nie jest już skojarzony z jednym. Własność bieżącego serwera proxy wątku jest określana `switchState` przez wartość określoną dla argumentu.

Użyj tej `Idle` wartości, jeśli chcesz zwrócić aktualnie wykonywany serwer proxy wątku do Menedżera zasobów. Wywołanie `SwitchTo` z `switchState` parametrem ustawionym na `Idle` spowoduje kontekst `pContext` wykonywania, aby rozpocząć wykonywanie na zasób wykonywania podstawowej. Własność tego serwera proxy wątku jest przenoszona do Menedżera zasobów i `Dispatch` oczekuje się, że wkrótce po `SwitchTo` zwrocie z kontekstu wykonania nastąpi powrót z metody kontekstu wykonania, aby zakończyć transfer. Kontekst wykonywania, który wysyłał serwer proxy wątku, jest odłączony od serwera proxy wątku, a harmonogram może go ponownie użyć lub zniszczyć zgodnie z jego potrzebą.

Użyj wartości, `Blocking` jeśli ten serwer proxy wątku ma wejść w stan zablokowany. Wywołanie `SwitchTo` z `switchState` parametrem ustawionym na `Blocking` spowoduje kontekst `pContext` wykonywania, aby rozpocząć wykonywanie i zablokować bieżący serwer proxy wątku, dopóki nie zostanie wznowiony. Harmonogram zachowuje własność serwera proxy wątku, gdy serwer `Blocking` proxy wątku jest w stanie. Blokowanie serwera proxy wątku można wznowić, wywołując funkcję, `SwitchTo` aby przełączyć się do kontekstu wykonywania tego serwera proxy wątku. Można również wznowić proxy wątku, używając skojarzonego kontekstu, aby aktywować katalog główny procesora wirtualnego. Aby uzyskać więcej informacji na temat tego, zobacz [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate).

Użyj wartości, `Nesting` gdy chcesz tymczasowo odłączyć ten serwer proxy wątku od katalogu głównego procesora wirtualnego, na którym jest uruchomiony, i harmonogram, dla którego jest wywoływany. Wywołanie `SwitchTo` z `switchState` parametrem ustawionym na `Nesting` spowoduje kontekst `pContext` wykonywania, aby rozpocząć wykonywanie i bieżącego serwera proxy wątku również kontynuuje wykonywanie bez konieczności stosowania katalogu głównego procesora wirtualnego. Serwer proxy wątku jest uważany za opuścił harmonogram, dopóki nie wywoła [IThreadProxy::SwitchOut](#switchout) metody w późniejszym momencie w czasie. Metoda `IThreadProxy::SwitchOut` może zablokować serwer proxy wątku, dopóki katalog główny procesora wirtualnego nie będzie dostępny do ponownego jego przełkowego.

`SwitchTo`musi być wywoływana w interfejsie, `IThreadProxy` który reprezentuje aktualnie wykonywany wątek lub wyniki są niezdefiniowane. Funkcja jest `invalid_argument` zgłaszana, `pContext` jeśli `NULL`parametr jest ustawiony na .

## <a name="ithreadproxyyieldtosystem-method"></a><a name="yieldtosystem"></a>IThreadProxy::YieldToSystem Metoda

Powoduje, że wątek wywołujący do wykonania do innego wątku, który jest gotowy do uruchomienia na bieżącym procesorze. System operacyjny wybiera następny wątek do wykonania.

```cpp
virtual void YieldToSystem() = 0;
```

### <a name="remarks"></a>Uwagi

Po wywołaniu przez serwer proxy wątku `YieldToSystem` wspierany przez zwykły wątek systemu Windows, zachowuje się dokładnie tak, jak funkcja `SwitchToThread`systemu Windows . Jednak po wywołaniu z trybie użytkownika schedulable (UMS) wątków, `SwitchToThread` funkcja deleguje zadanie pobrania następnego wątku do uruchomienia do harmonogramu trybu użytkownika, a nie systemu operacyjnego. Aby osiągnąć pożądany efekt przełączania się na inny `YieldToSystem`gotowy wątek w systemie, użyj .

`YieldToSystem`musi być wywoływana w interfejsie, `IThreadProxy` który reprezentuje aktualnie wykonywany wątek lub wyniki są niezdefiniowane.

## <a name="see-also"></a>Zobacz też

[współbieżność Obszar nazw](concurrency-namespace.md)<br/>
[IExecutionContext, struktura](iexecutioncontext-structure.md)<br/>
[IScheduler, struktura](ischeduler-structure.md)<br/>
[IVirtualProcessorRoot, struktura](ivirtualprocessorroot-structure.md)
