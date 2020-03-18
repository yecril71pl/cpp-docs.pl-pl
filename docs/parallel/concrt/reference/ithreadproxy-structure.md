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
ms.openlocfilehash: b87694393af4634ec97d05070aa5513cd132098a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417160"
---
# <a name="ithreadproxy-structure"></a>IThreadProxy — Struktura

Abstrakcja wątku wykonania. W zależności od klucza zasad `SchedulerType` utworzonego przez użytkownika harmonogramu Menedżer zasobów przyznaje Ci wątek proxy wątku, który jest obsługiwany przez zwykły wątek Win32 lub wątek harmonogramie (UMS) w trybie użytkownika. Wątki UMS są obsługiwane w 64-bitowych systemach operacyjnych z wersją Windows 7 i nowszą.

## <a name="syntax"></a>Składnia

```cpp
struct IThreadProxy;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[IThreadProxy:: GetId —](#getid)|Zwraca unikatowy identyfikator dla serwera proxy wątku.|
|[IThreadProxy:: SwitchOut —](#switchout)|Usuwa kontekst z bazowego głównego procesora wirtualnego.|
|[IThreadProxy:: SwitchTo —](#switchto)|Wykonuje przełączenie kontekstu wspólnego z aktualnie wykonywanego kontekstu do innego.|
|[IThreadProxy:: YieldToSystem —](#yieldtosystem)|Powoduje, że wątek wywołujący przekazuje wykonywanie do innego wątku, który jest gotowy do uruchomienia na bieżącym procesorze. System operacyjny wybiera następny wątek do wykonania.|

## <a name="remarks"></a>Uwagi

Serwery proxy wątków są połączone z kontekstami wykonywania reprezentowanymi przez interfejs `IExecutionContext` jako sposób wysyłania zadań.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IThreadProxy`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm. h

**Przestrzeń nazw:** współbieżność

## <a name="getid"></a>IThreadProxy:: GetId —, Metoda

Zwraca unikatowy identyfikator dla serwera proxy wątku.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Unikatowy identyfikator liczby całkowitej.

## <a name="switchout"></a>IThreadProxy:: SwitchOut —, Metoda

Usuwa kontekst z bazowego głównego procesora wirtualnego.

```cpp
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```

### <a name="parameters"></a>Parametry

*switchState*<br/>
Wskazuje stan serwera proxy wątku wykonującego przełącznik. Parametr jest typu `SwitchingProxyState`.

### <a name="remarks"></a>Uwagi

Użyj `SwitchOut`, jeśli chcesz usunąć skojarzenie kontekstu z głównego wirtualnego procesora, który jest wykonywany z dowolnego powodu. W zależności od wartości przekazywanej do parametru `switchState`i bez względu na to, czy jest ona wykonywana w katalogu głównym procesora wirtualnego, wywołanie zwróci natychmiast lub zablokuje serwer proxy wątku skojarzony z kontekstem. Wystąpił błąd podczas wywoływania `SwitchOut` z parametrem ustawionym na `Idle`. Wykonanie tej czynności spowoduje wyjątek [invalid_argument](../../../standard-library/invalid-argument-class.md) .

`SwitchOut` jest przydatne, gdy chcesz zmniejszyć liczbę katalogów głównych wirtualnego procesora, z których korzysta Twój harmonogram, ponieważ Menedżer zasobów zalecił to, lub ponieważ zażądano tymczasowego, nadsubskrybowanego wirtualnego dysku nadrzędnego, i są one gotowe do użycia. W takim przypadku należy wywołać metodę [IVirtualProcessorRoot:: Remove](iexecutionresource-structure.md#remove) w katalogu głównym wirtualnego procesora przed wywołaniem `SwitchOut` z parametrem `switchState` ustawionym na `Blocking`. Spowoduje to zablokowanie serwera proxy wątku, który zostanie wznowiony, gdy będzie dostępny inny wirtualny rdzeń procesora w harmonogramie. Blokowanie serwera proxy wątku można wznowić, wywołując funkcję `SwitchTo`, aby przełączyć się do kontekstu wykonywania tego wątku. Możesz również wznowić serwer proxy wątku przy użyciu skojarzonego z nim kontekstu, aby aktywować rdzeń wirtualnego procesora. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate).

`SwitchOut` można również użyć, jeśli chcesz ponownie zainicjować procesor wirtualny, aby można go było aktywować w przyszłości, jednocześnie blokując serwer proxy wątku lub tymczasowo odłączając go od głównego wirtualnego procesora, w którym jest uruchomiona, i harmonogramu, dla którego jest wysyłana. Użyj `SwitchOut` z parametrem `switchState` ustawionym na `Blocking`, jeśli chcesz zablokować serwer proxy wątku. Można go później wznowić przy użyciu `SwitchTo` lub `IVirtualProcessorRoot::Activate`, jak wspomniano powyżej. Użyj `SwitchOut` z parametrem ustawionym na `Nesting`, gdy chcesz tymczasowo odłączyć ten serwer proxy wątku od wirtualnego procesora, w którym jest uruchomiony, oraz do harmonogramu, z którym jest skojarzony procesor wirtualny. Wywoływanie `SwitchOut` z parametrem `switchState` ustawionym na `Nesting`, gdy jest wykonywane w katalogu głównym procesora wirtualnego, spowoduje ponowne zainicjowanie katalogu głównego i bieżący wątek proxy wątku, aby kontynuować wykonywanie bez potrzeby jednego z nich. Serwer proxy wątku jest uznawany za pozostawiony przez program Scheduler do momentu wywołania metody [IThreadProxy:: SwitchOut —](#switchout) z `Blocking` w późniejszym czasie. Drugie wywołanie `SwitchOut` z parametrem ustawionym na `Blocking` jest przeznaczone do zwrócenia kontekstu do zablokowanego stanu, dzięki czemu może zostać wznowione przez `SwitchTo` lub `IVirtualProcessorRoot::Activate` w harmonogramie odłączonym od. Ponieważ nie został wykonany w katalogu głównym wirtualnego procesora, nie ma żadnego ponownego inicjowania.

Ponownie zainicjowany katalog główny wirtualnego procesora nie różni się od nowego głównego wirtualnego procesora, który został przyznany przez Menedżer zasobów. Można jej użyć do wykonania, aktywując ją z kontekstem wykonywania przy użyciu `IVirtualProcessorRoot::Activate`.

należy wywołać `SwitchOut` w interfejsie `IThreadProxy`, który reprezentuje aktualnie wykonywany wątek lub wyniki są niezdefiniowane.

W bibliotekach i nagłówkach, które zostały dostarczone z programem Visual Studio 2010, ta metoda nie przyjmuje parametru i nie zainicjowała ponownie głównego wirtualnego procesora. Aby zachować stare zachowanie, zostanie podana domyślna wartość parametru `Blocking`.

## <a name="switchto"></a>IThreadProxy:: SwitchTo —, Metoda

Wykonuje przełączenie kontekstu wspólnego z aktualnie wykonywanego kontekstu do innego.

```cpp
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Kontekst wykonywania, aby wspólnie przełączać się do.

*switchState*<br/>
Wskazuje stan serwera proxy wątku wykonującego przełącznik. Parametr jest typu `SwitchingProxyState`.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby przełączyć się z jednego kontekstu wykonywania na inny, z metody [IExecutionContext::D ispatch](iexecutioncontext-structure.md#dispatch) w pierwszym kontekście wykonania. Metoda kojarzy kontekst wykonywania `pContext` z serwerem proxy wątku, jeśli nie jest już skojarzony z jednym. Własność bieżącego elementu pośredniczącego wątku jest określana przez wartość określoną dla argumentu `switchState`.

Użyj wartości `Idle`, gdy chcesz zwrócić aktualnie wykonywany serwer proxy wątków do Menedżer zasobów. Wywołanie `SwitchTo` z parametrem `switchState` ustawionym na `Idle` spowoduje, że kontekst wykonywania `pContext` rozpocząć wykonywanie na podstawowym zasobie wykonania. Własność tego serwera proxy wątku jest przekazywana do Menedżer zasobów i oczekuje się, że z metody `Dispatch` kontekstu wykonywania wkrótce po `SwitchTo` zwróci, aby zakończyć transfer. Kontekst wykonywania, który został wysłany przez serwer proxy wątku, jest nieskojarzony z serwerem proxy wątku, a harmonogram jest bezpłatny, aby można go było ponownie wykorzystać lub zniszczyć go zgodnie z oczekiwaniami.

Użyj wartości `Blocking`, jeśli chcesz, aby ten wątek proxy był w stanie zablokowany. Wywołanie `SwitchTo` z parametrem `switchState` ustawionym na `Blocking` spowoduje, że kontekst wykonywania `pContext` rozpocząć wykonywanie i zablokuje bieżący serwer proxy wątku do momentu wznowienia działania. Harmonogram zachowuje własność serwera proxy wątku, gdy serwer proxy wątku jest w stanie `Blocking`. Blokowanie serwera proxy wątku można wznowić, wywołując funkcję `SwitchTo`, aby przełączyć się do kontekstu wykonywania tego wątku. Możesz również wznowić serwer proxy wątku przy użyciu skojarzonego z nim kontekstu, aby aktywować rdzeń wirtualnego procesora. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate).

Użyj wartości `Nesting`, gdy chcesz tymczasowo odłączyć ten serwer proxy wątku od wirtualnego procesora, w którym jest uruchomiona, i harmonogramu, dla którego jest wysyłana. Wywołanie `SwitchTo` z parametrem `switchState` ustawionym na `Nesting` spowoduje, że kontekst wykonywania `pContext` rozpoczyna wykonywanie, a bieżący serwer proxy wątku będzie również kontynuował wykonywanie bez potrzeby wirtualnego procesora. Serwer proxy wątku jest uznawany za pozostawiony przez program Scheduler do momentu wywołania metody [IThreadProxy:: SwitchOut —](#switchout) w późniejszym momencie. Metoda `IThreadProxy::SwitchOut` może zablokować serwer proxy wątku do momentu udostępnienia katalogu głównego wirtualnego procesora, aby go ponownie zaplanować.

należy wywołać `SwitchTo` w interfejsie `IThreadProxy`, który reprezentuje aktualnie wykonywany wątek lub wyniki są niezdefiniowane. Funkcja zgłasza `invalid_argument`, jeśli parametr `pContext` jest ustawiony na `NULL`.

## <a name="yieldtosystem"></a>IThreadProxy:: YieldToSystem —, Metoda

Powoduje, że wątek wywołujący przekazuje wykonywanie do innego wątku, który jest gotowy do uruchomienia na bieżącym procesorze. System operacyjny wybiera następny wątek do wykonania.

```cpp
virtual void YieldToSystem() = 0;
```

### <a name="remarks"></a>Uwagi

Gdy wywoływany przez serwer proxy wątku, którego kopia zapasowa jest regularnym wątkiem systemu Windows, `YieldToSystem` zachowuje się dokładnie tak, jak `SwitchToThread`funkcji systemu Windows. Jednak po wywołaniu z wątków harmonogramie (UMS) w trybie użytkownika funkcja `SwitchToThread` deleguje zadanie wybierania następnego wątku do uruchomienia w harmonogramie trybu użytkownika, a nie w systemie operacyjnym. Aby osiągnąć żądany efekt przełączenia do innego gotowego wątku w systemie, użyj `YieldToSystem`.

należy wywołać `YieldToSystem` w interfejsie `IThreadProxy`, który reprezentuje aktualnie wykonywany wątek lub wyniki są niezdefiniowane.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[IExecutionContext, struktura](iexecutioncontext-structure.md)<br/>
[IScheduler, struktura](ischeduler-structure.md)<br/>
[IVirtualProcessorRoot, struktura](ivirtualprocessorroot-structure.md)
