---
title: IVirtualProcessorRoot — Struktura
ms.date: 11/04/2016
f1_keywords:
- IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Activate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Deactivate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::EnsureAllTasksVisible
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::GetId
helpviewer_keywords:
- IVirtualProcessorRoot structure
ms.assetid: 5ef371b8-9e4f-4fef-bb0d-49099693dd2b
ms.openlocfilehash: f642a29d0a80568f7a5f2a5e89f6951d4819243e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364258"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot — Struktura

Abstrakcja wątku sprzętowego, na którym można wykonać serwer proxy wątku.

## <a name="syntax"></a>Składnia

```cpp
struct IVirtualProcessorRoot : public IExecutionResource;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IVirtualProcessorRoot::Aktywuj](#activate)|Powoduje, że serwer proxy wątku `pContext` skojarzony z interfejsem kontekstu wykonywania, aby rozpocząć wykonywanie na tym katalogu głównym procesora wirtualnego.|
|[IVirtualProcessorRoot::Daktywować](#deactivate)|Powoduje, że serwer proxy wątku aktualnie wykonywany w tym katalogu głównym procesora wirtualnego, aby zatrzymać wysyłanie kontekstu wykonywania. Serwer proxy wątku wznowi wykonywanie wywołania `Activate` metody.|
|[IVirtualProcessorRoot::EnsureAllTasksVisible](#ensurealltasksvisible)|Powoduje, że dane przechowywane w hierarchii pamięci poszczególnych procesorów stają się widoczne dla wszystkich procesorów w systemie. Zapewnia, że pełne ogrodzenie pamięci zostało wykonane na wszystkich procesorach, zanim metoda powróci.|
|[IVirtualProcessorRoot::GetId](#getid)|Zwraca unikatowy identyfikator katalogu głównego procesora wirtualnego.|

## <a name="remarks"></a>Uwagi

Każdy katalog główny procesora wirtualnego ma skojarzony zasób wykonywania. Interfejs `IVirtualProcessorRoot` dziedziczy z [interfejsu IExecutionResource.](iexecutionresource-structure.md) Wiele katalogów głównych procesora wirtualnego może odpowiadać temu samemu podstawowemu wątkowi sprzętowego.

Menedżer zasobów udziela katalogów głównych procesorów wirtualnych harmonogramom w odpowiedzi na żądania dotyczące zasobów. Harmonogram można użyć katalogu głównego procesora wirtualnego do wykonywania pracy, aktywując go w kontekście wykonywania.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[IWykonanie Źródła](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Przestrzeń nazw:** współbieżność

## <a name="ivirtualprocessorrootactivate-method"></a><a name="activate"></a>IVirtualProcessorRoot::Metoda aktywacji

Powoduje, że serwer proxy wątku `pContext` skojarzony z interfejsem kontekstu wykonywania, aby rozpocząć wykonywanie na tym katalogu głównym procesora wirtualnego.

```cpp
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*Pcontext*<br/>
Interfejs do kontekstu wykonywania, który zostanie wysłany w tym katalogu głównym procesora wirtualnego.

### <a name="remarks"></a>Uwagi

Menedżer zasobów dostarczy serwer proxy wątku, jeśli nie jest skojarzony z interfejsem kontekstu wykonywania`pContext`

Metoda `Activate` ta może służyć do rozpoczęcia wykonywania pracy nad nowym katalogiem głównym procesora wirtualnego zwróconego przez Menedżera zasobów lub do wznowienia serwera proxy wątku w katalogu głównym procesora wirtualnego, który został dezaktywowany lub ma zostać dezaktywowany. Zobacz [IVirtualProcessorRoot::Daktywuj, aby](#deactivate) uzyskać więcej informacji na temat dezaktywacji. Po wznowieniu dezaktywacji katalogu głównego procesora wirtualnego parametr `pContext` musi być taki sam jak parametr używany do dezaktywacji katalogu głównego procesora wirtualnego.

Po pierwszym uruchomieniu katalogu głównego procesora wirtualnego kolejne pary `Deactivate` połączeń `Activate` do i mogą ścigać się ze sobą. Oznacza to, że jest dopuszczalne dla `Activate` Menedżera zasobów, `Deactivate` aby odebrać połączenie przed odebraniem wywołania, który był przeznaczony dla.

Po aktywowaniu katalogu głównego procesora wirtualnego należy zasygnalizować Menedżerowi zasobów, że ten katalog główny procesora wirtualnego jest obecnie zajęty pracą. Jeśli harmonogram nie może znaleźć żadnej pracy do wykonania w tym `Deactivate` katalogu głównym, oczekuje się, że wywoła metodę informującą Menedżera zasobów, że katalog główny procesora wirtualnego jest bezczynny. Menedżer zasobów używa tych danych do równoważenia obciążenia systemu.

`invalid_argument`jest generowany, `pContext` jeśli argument `NULL`ma wartość .

`invalid_operation`jest generowany, `pContext` jeśli argument nie reprezentuje kontekstu wykonywania, który został ostatnio wysłany przez ten katalog główny procesora wirtualnego.

Czynność aktywacji katalogu głównego procesora wirtualnego zwiększa poziom subskrypcji wątku sprzętowego o jeden. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ivirtualprocessorrootdeactivate-method"></a><a name="deactivate"></a>IVirtualProcessorRoot::D metoda aktywacji

Powoduje, że serwer proxy wątku aktualnie wykonywany w tym katalogu głównym procesora wirtualnego, aby zatrzymać wysyłanie kontekstu wykonywania. Serwer proxy wątku wznowi wykonywanie wywołania `Activate` metody.

```cpp
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*Pcontext*<br/>
Kontekst, który jest obecnie wywoływany przez ten katalog główny.

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna. Wartość **true** wskazuje, że serwer proxy `Deactivate` wątku zwrócił z metody `Activate` w odpowiedzi na wywołanie metody. Wartość `false` wskazuje, że serwer proxy wątku zwrócił z metody w odpowiedzi na zdarzenie powiadomień w Menedżerze zasobów. W harmonogramie wątków w trybie użytkownika (UMS) oznacza to, że elementy pojawiły się na liście ukończenia harmonogramu, a harmonogram jest wymagany do ich obsługi.

### <a name="remarks"></a>Uwagi

Ta metoda służy do tymczasowego zatrzymania wykonywania katalogu głównego procesora wirtualnego, gdy nie można znaleźć żadnej pracy w harmonogramie. Wywołanie `Deactivate` metody musi pochodzić `Dispatch` z metody kontekstu wykonywania, z którego ostatnio aktywowano katalog główny procesora wirtualnego. Innymi słowy serwer proxy wątku `Deactivate` wywołujący metodę musi być tym, który jest obecnie wykonywany w katalogu głównym procesora wirtualnego. Wywołanie metody w katalogu głównym procesora wirtualnego, na który nie wykonujesz, może spowodować niezdefiniowane zachowanie.

Dezaktywowany katalog główny procesora wirtualnego `Activate` może zostać obudzony za pomocą `Deactivate` wywołania metody, z tym samym argumentem, który został przekazany do metody. Harmonogram jest odpowiedzialny za zapewnienie, że `Activate` `Deactivate` wywołania i metody są sparowane, ale nie muszą być odbierane w określonej kolejności. Menedżer zasobów może obsługiwać odbieranie `Activate` wywołania metody, zanim `Deactivate` otrzyma wywołanie metody, dla jakiej była przeznaczona.

Jeśli katalog główny procesora wirtualnego `Deactivate` budzi się, a wartość zwracana z metody jest wartością **false,** harmonogram powinien zbadać listę uzupełnień usługi UMS za pomocą `IUMSCompletionList::GetUnblockNotifications` metody, działać na podstawie tych informacji, a następnie ponownie wywołać `Deactivate` metodę. Należy to powtórzyć do czasu, `Deactivate` gdy `true`metoda zwraca wartość .

`invalid_argument`jest generowany, `pContext` jeśli argument ma wartość NULL.

`invalid_operation`jest generowany, jeśli katalog główny procesora wirtualnego `pContext` nigdy nie został aktywowany lub argument nie reprezentuje kontekstu wykonywania, który został ostatnio wysłany przez ten katalog główny procesora wirtualnego.

Czynność dezaktywacji katalogu głównego procesora wirtualnego zmniejsza poziom subskrypcji wątku sprzętowego o jeden. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ivirtualprocessorrootensurealltasksvisible-method"></a><a name="ensurealltasksvisible"></a>IVirtualProcessorRoot::EnsureAllTasksVisible Metoda

Powoduje, że dane przechowywane w hierarchii pamięci poszczególnych procesorów stają się widoczne dla wszystkich procesorów w systemie. Zapewnia, że pełne ogrodzenie pamięci zostało wykonane na wszystkich procesorach, zanim metoda powróci.

```cpp
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*Pcontext*<br/>
Kontekst, który jest obecnie wywoływany przez ten katalog główny procesora wirtualnego.

### <a name="remarks"></a>Uwagi

Ta metoda może okazać się przydatna, gdy chcesz zsynchronizować dezaktywację katalogu głównego procesora wirtualnego z dodatkiem nowej pracy do harmonogramu. Ze względu na wydajność można zdecydować o dodaniu elementów roboczych do harmonogramu bez wykonywania bariery pamięci, co oznacza, że elementy robocze dodane przez wątek wykonywany na jednym procesorze nie są natychmiast widoczne dla wszystkich innych procesorów. Za pomocą tej metody `Deactivate` w połączeniu z metodą można zapewnić, że harmonogram nie dezaktywuje wszystkie jego katalogi główne procesora wirtualnego, podczas gdy elementy robocze istnieją w kolekcji harmonogramu.

Wywołanie `EnsureAllTasksVisibleThe` metody musi pochodzić `Dispatch` z metody kontekstu wykonywania, z którego ostatnio aktywowano katalog główny procesora wirtualnego. Innymi słowy serwer proxy wątku `EnsureAllTasksVisible` wywołujący metodę musi być tym, który jest obecnie wykonywany w katalogu głównym procesora wirtualnego. Wywołanie metody w katalogu głównym procesora wirtualnego, na który nie wykonujesz, może spowodować niezdefiniowane zachowanie.

`invalid_argument`jest generowany, `pContext` jeśli argument `NULL`ma wartość .

`invalid_operation`jest generowany, jeśli katalog główny procesora wirtualnego `pContext` nigdy nie został aktywowany lub argument nie reprezentuje kontekstu wykonywania, który został ostatnio wysłany przez ten katalog główny procesora wirtualnego.

## <a name="ivirtualprocessorrootgetid-method"></a><a name="getid"></a>IVirtualProcessorRoot::Metoda GetId

Zwraca unikatowy identyfikator katalogu głównego procesora wirtualnego.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator liczby całkowitej.

## <a name="see-also"></a>Zobacz też

[współbieżność Obszar nazw](concurrency-namespace.md)
