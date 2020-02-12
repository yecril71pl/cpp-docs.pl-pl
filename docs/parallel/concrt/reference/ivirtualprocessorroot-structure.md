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
ms.openlocfilehash: 60757b0edea6b60d080c2175d4df4830ffec0cc3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139893"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot — Struktura

Abstrakcja wątku sprzętowego, w którym może być wykonywany serwer proxy wątku.

## <a name="syntax"></a>Składnia

```cpp
struct IVirtualProcessorRoot : public IExecutionResource;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[IVirtualProcessorRoot:: Activate](#activate)|Powoduje, że serwer proxy wątku skojarzony z interfejsem kontekstu wykonywania `pContext` rozpocząć wykonywanie w tym wirtualnym katalogu głównym procesora.|
|[IVirtualProcessorRoot::D eactivate](#deactivate)|Powoduje, że serwer proxy wątku, który jest aktualnie wykonywany na tym wirtualnym komputerze głównym, w celu zatrzymania wysyłania kontekstu wykonania. Serwer proxy wątku wznowi wykonywanie w wywołaniu metody `Activate`.|
|[IVirtualProcessorRoot:: EnsureAllTasksVisible —](#ensurealltasksvisible)|Powoduje, że dane przechowywane w hierarchii pamięci poszczególnych procesorów stają się widoczne dla wszystkich procesorów w systemie. Gwarantuje to, że pełny ogranicznik pamięci został wykonany na wszystkich procesorach przed zwróceniem metody.|
|[IVirtualProcessorRoot:: GetId —](#getid)|Zwraca unikatowy identyfikator katalogu głównego wirtualnego procesora.|

## <a name="remarks"></a>Uwagi

Każdy główny procesor wirtualny ma skojarzony zasób wykonania. Interfejs `IVirtualProcessorRoot` dziedziczy z interfejsu [IExecutionResource](iexecutionresource-structure.md) . Wiele katalogów głównych procesorów wirtualnych może odpowiadać te same bazowego wątku sprzętowego.

Menedżer zasobów przyznaje katalogi wirtualne procesora wirtualnego do harmonogramów w odpowiedzi na żądania dotyczące zasobów. Harmonogram może korzystać z głównego procesora wirtualnego, aby wykonać pracę, aktywując go przy użyciu kontekstu wykonywania.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[IExecutionResource](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm. h

**Przestrzeń nazw:** współbieżność

## <a name="activate"></a>IVirtualProcessorRoot:: Activate — metoda

Powoduje, że serwer proxy wątku skojarzony z interfejsem kontekstu wykonywania `pContext` rozpocząć wykonywanie w tym wirtualnym katalogu głównym procesora.

```cpp
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Interfejs do kontekstu wykonywania, który zostanie wysłany do tego głównego wirtualnego procesora.

### <a name="remarks"></a>Uwagi

Menedżer zasobów będzie dostarczać serwer proxy wątku, jeśli nie zostanie on skojarzony z interfejsem kontekstu wykonywania `pContext`

Metoda `Activate` może służyć do uruchamiania wykonywania pracy w nowym katalogu głównym wirtualnego procesora zwróconym przez Menedżer zasobów lub do wznowienia działania serwera proxy wątku w wirtualnym katalogu głównym procesora, który został zdezaktywowany lub zostanie zdezaktywowany. Aby uzyskać więcej informacji na temat dezaktywacji, zobacz [IVirtualProcessorRoot::D eactivate](#deactivate) . W przypadku wznawiania dezaktywowanego katalogu głównego wirtualnego procesora, parametr `pContext` musi być taki sam, jak parametr używany do dezaktywowania katalogu głównego wirtualnego procesora.

Po aktywowaniu wirtualnego katalogu głównego procesora po raz pierwszy, kolejne pary wywołań do `Deactivate` i `Activate` mogą się od siebie odwoływać. Oznacza to, że możliwe jest, aby Menedżer zasobów otrzymać wywołanie do `Activate`, zanim odbierze połączenie `Deactivate`.

W przypadku aktywowania katalogu głównego wirtualnego procesora należy zasygnalizować Menedżer zasobów, że ten katalog wirtualny tego procesora jest obecnie zajęty przy użyciu pracy. Jeśli harmonogram nie może znaleźć żadnych zadań do wykonania w tym katalogu głównym, oczekuje się, że metoda `Deactivate` informuje Menedżer zasobów, że główny wirtualny procesor jest bezczynny. Menedżer zasobów używa tych danych do równoważenia obciążenia systemu.

`invalid_argument` jest generowany, jeśli argument `pContext` ma wartość `NULL`.

`invalid_operation` jest generowany, jeśli argument `pContext` nie reprezentuje kontekstu wykonywania, który był ostatnio Wysłany przez ten rdzeń procesora wirtualnego.

Czynność aktywowania głównego wirtualnego procesora zwiększa poziom subskrypcji bazowego wątku sprzętowego o jeden. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource:: CurrentSubscriptionLevel —](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="deactivate"></a>IVirtualProcessorRoot::D eactivate Metoda

Powoduje, że serwer proxy wątku, który jest aktualnie wykonywany na tym wirtualnym komputerze głównym, w celu zatrzymania wysyłania kontekstu wykonania. Serwer proxy wątku wznowi wykonywanie w wywołaniu metody `Activate`.

```cpp
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Kontekst, który jest aktualnie wysyłany przez ten element główny.

### <a name="return-value"></a>Wartość zwrócona

Wartość logiczna. Wartość **true** wskazuje, że serwer proxy wątku zwraca z metody `Deactivate` w odpowiedzi na wywołanie metody `Activate`. Wartość `false` wskazuje, że serwer proxy wątku zwraca z metody w odpowiedzi na zdarzenie powiadomienia w Menedżer zasobów. W harmonogramie wątków harmonogramie (UMS) w trybie użytkownika wskazuje, że elementy pojawiły się na liście uzupełniania harmonogramu, a harmonogram jest wymagany do ich obsługi.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby tymczasowo zatrzymać wykonywanie wirtualnego katalogu głównego procesora, gdy nie można znaleźć żadnej pracy w harmonogramie. Wywołanie metody `Deactivate` musi pochodzić z metody `Dispatch` kontekstu wykonywania, który został ostatnio aktywowany przez rdzeń wirtualnego procesora. Innymi słowy, serwer proxy wątku wywołujący metodę `Deactivate` musi być tym, który jest aktualnie wykonywany w katalogu głównym wirtualnego procesora. Wywołanie metody w głównym katalogu wirtualnym procesora, którego nie wykonujesz, może spowodować niezdefiniowane zachowanie.

Zdezaktywowany rdzeń wirtualnego procesora może być wybudzany z wywołaniem metody `Activate`, z tym samym argumentem, który został przekazano do metody `Deactivate`. Harmonogram jest odpowiedzialny za zapewnienie, że wywołania `Activate` i `Deactivate` metody są sparowane, ale nie muszą być odbierane w określonej kolejności. Menedżer zasobów może obsłużyć odbieranie wywołania metody `Activate` przed odebraniem wywołania metody `Deactivate`.

W przypadku wypróbowania głównego wirtualnego procesora i wartości zwracanej z metody `Deactivate` jest wartość **false**, harmonogram powinien wysyłać zapytania do listy uzupełniania UMS za pomocą metody `IUMSCompletionList::GetUnblockNotifications`, działać na tych informacjach, a następnie ponownie wywołać metodę `Deactivate`. Należy to powtórzyć do momentu, w którym Metoda `Deactivate` zwraca wartość `true`.

`invalid_argument` jest generowany, jeśli argument `pContext` ma wartość NULL.

`invalid_operation` jest generowany, jeśli główny wirtualny procesor nie został nigdy aktywowany lub argument `pContext` nie reprezentuje kontekstu wykonywania, który był ostatnio Wysłany przez ten rdzeń procesora wirtualnego.

Czynność dezaktywacji głównego procesora wirtualnego zmniejsza poziom subskrypcji bazowego wątku sprzętowego o jeden. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource:: CurrentSubscriptionLevel —](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ensurealltasksvisible"></a>IVirtualProcessorRoot:: EnsureAllTasksVisible —, Metoda

Powoduje, że dane przechowywane w hierarchii pamięci poszczególnych procesorów stają się widoczne dla wszystkich procesorów w systemie. Gwarantuje to, że pełny ogranicznik pamięci został wykonany na wszystkich procesorach przed zwróceniem metody.

```cpp
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Kontekst, który jest aktualnie wysyłany przez ten rdzeń wirtualnego procesora.

### <a name="remarks"></a>Uwagi

Ta metoda może być przydatna, jeśli chcesz synchronizować dezaktywację wirtualnego katalogu głównego z dodaniem nowej pracy do harmonogramu. Ze względu na wydajność możesz zdecydować się na dodanie elementów roboczych do harmonogramu bez wykonywania bariery pamięci, co oznacza, że elementy robocze dodane przez wątek wykonywane na jednym procesorze nie są natychmiast widoczne dla wszystkich innych procesorów. Za pomocą tej metody w połączeniu z metodą `Deactivate` można upewnić się, że harmonogram nie dezaktywuje wszystkich katalogów głównych procesorów wirtualnych, gdy istnieją elementy robocze w kolekcjach harmonogramu.

Wywołanie metody `EnsureAllTasksVisibleThe` musi pochodzić z metody `Dispatch` kontekstu wykonywania, który został ostatnio aktywowany przez rdzeń wirtualnego procesora. Innymi słowy, serwer proxy wątku wywołujący metodę `EnsureAllTasksVisible` musi być tym, który jest aktualnie wykonywany w katalogu głównym wirtualnego procesora. Wywołanie metody w głównym katalogu wirtualnym procesora, którego nie wykonujesz, może spowodować niezdefiniowane zachowanie.

`invalid_argument` jest generowany, jeśli argument `pContext` ma wartość `NULL`.

`invalid_operation` jest generowany, jeśli główny wirtualny procesor nie został nigdy aktywowany lub argument `pContext` nie reprezentuje kontekstu wykonywania, który był ostatnio Wysłany przez ten rdzeń procesora wirtualnego.

## <a name="getid"></a>IVirtualProcessorRoot:: GetId —, Metoda

Zwraca unikatowy identyfikator katalogu głównego wirtualnego procesora.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Identyfikator liczby całkowitej.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
