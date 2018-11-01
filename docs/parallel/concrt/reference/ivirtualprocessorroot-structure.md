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
ms.openlocfilehash: 6e3f874aa7c20494483172d7c7c3efee362cf6a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569874"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot — Struktura

Abstrakcja wątku sprzętu, na którym można wykonać wątek serwera proxy.

## <a name="syntax"></a>Składnia

```
struct IVirtualProcessorRoot : public IExecutionResource;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IVirtualProcessorRoot::Activate](#activate)|Powoduje, że serwer proxy wątku skojarzoną z interfejsem kontekstu wykonania `pContext` można uruchomić wykonywania w tym procesora wirtualnego katalogu głównego.|
|[IVirtualProcessorRoot::Deactivate](#deactivate)|Powoduje, że serwer proxy wątku aktualnie wykonywanych w tym procesora wirtualnego katalogu głównego, aby zatrzymać kontekstu wykonania wysyłki. Wątek serwera proxy zostanie wznowione, wykonując na wywołanie `Activate` metody.|
|[IVirtualProcessorRoot::EnsureAllTasksVisible](#ensurealltasksvisible)|Powoduje, że dane przechowywane w hierarchii pamięci pojedynczych procesorów, które stają się widoczne dla wszystkich procesorów w systemie. Zapewnia, że horyzont pamięci pełną została wykonana we wszystkich procesorach przed powrotem z metody.|
|[IVirtualProcessorRoot::GetId](#getid)|Zwraca unikatowy identyfikator dla procesora wirtualnego katalogu głównego.|

## <a name="remarks"></a>Uwagi

Każdy procesora wirtualnego katalogu głównego ma wykonywania skojarzonych zasobów. `IVirtualProcessorRoot` Interfejs dziedziczy z [iexecutionresource —](iexecutionresource-structure.md) interfejsu. Wiele głównych procesorów wirtualnych może odpowiadać na tym samym wątku sprzętu bazowego.

Menedżer zasobów przyznaje korzeni procesora wirtualnego transfery danych w odpowiedzi na żądania dotyczące zasobów. Harmonogram można użyć procesora wirtualnego katalogu głównego do wykonywania pracy, aktywując go z kontekstu wykonywania.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[IExecutionResource](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Namespace:** współbieżności

##  <a name="activate"></a>  IVirtualProcessorRoot::Activate — metoda

Powoduje, że serwer proxy wątku skojarzoną z interfejsem kontekstu wykonania `pContext` można uruchomić wykonywania w tym procesora wirtualnego katalogu głównego.

```
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Interfejs do kontekstu wykonywania, który zostanie wysłany na tym procesora wirtualnego katalogu głównego.

### <a name="remarks"></a>Uwagi

Menedżer zasobów będzie dostarczać wątek serwera proxy, jeśli nie została skojarzona z interfejsem Kontekst wykonywania `pContext`

`Activate` Metody można użyć, aby rozpocząć wykonywania pracy na nowy katalog główny Procesor wirtualny zwrócony przez Menedżera zasobów lub wznowić proxy wątku w głównym procesorze wirtualnym, który został zdezaktywowany lub ma Dezaktywuj. Zobacz [ivirtualprocessorroot::Deactivate —](#deactivate) więcej informacji na temat dezaktywowania. Gdy trwa wznawianie dezaktywowane procesora wirtualnego katalogu głównego, parametr `pContext` musi być taka sama jak parametru użytego do dezaktywowania procesora wirtualnego katalogu głównego.

Po aktywowaniu po raz pierwszy, pary kolejnych wywołań procesora wirtualnego katalogu głównego `Deactivate` i `Activate` mogą zastępować siebie nawzajem. Oznacza to dopuszczalne dla Menedżera zasobów do odbierania wywołanie `Activate` przed odbierze `Deactivate` miał trafić do wywołania.

Po aktywowaniu procesora wirtualnego katalogu głównego możesz sygnał do Menedżera zasobów, w tym procesora wirtualnego katalogu głównego jest aktualnie zajęte pracy. Jeśli harmonogramu nie może odnaleźć żadnych działań do wykonania w tym folderze głównym, oczekuje się, aby wywołać `Deactivate` metodę informowania Menedżera zasobów procesora wirtualnego katalogu głównego jest w stanie bezczynności. Menedżer zasobów używa tych danych do systemu równoważenia obciążenia.

`invalid_argument` jest generowany, jeśli argument `pContext` ma wartość `NULL`.

`invalid_operation` jest generowany, jeśli argument `pContext` nie reprezentuje kontekście wykonania, która została ostatnio wysyłane przez ten procesora wirtualnego katalogu głównego.

Czynność aktywowanie procesora wirtualnego katalogu głównego zwiększa się o jeden poziom subskrypcji w podstawowym wątku sprzętu. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [iexecutionresource::currentsubscriptionlevel —](iexecutionresource-structure.md#currentsubscriptionlevel).

##  <a name="deactivate"></a>  Ivirtualprocessorroot::Deactivate — metoda

Powoduje, że serwer proxy wątku aktualnie wykonywanych w tym procesora wirtualnego katalogu głównego, aby zatrzymać kontekstu wykonania wysyłki. Wątek serwera proxy zostanie wznowione, wykonując na wywołanie `Activate` metody.

```
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Kontekst, który jest aktualnie wysyłane przez ten katalog główny.

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna. Wartość **true** wskazuje, że serwer proxy wątku zwróciło `Deactivate` metody w odpowiedzi na wywołanie w celu `Activate` metody. Wartość `false` wskazuje, że serwer proxy wątku zwrócona przez metodę w odpowiedzi na zdarzenie otrzymania powiadomienia w usłudze Resource Manager. W trybie użytkownika ustalonych w harmonogramie (UMS) wątku harmonogramu to wskazuje, że elementy pojawiły się na liście uzupełniania harmonogramu i harmonogramu jest wymagana do ich obsługi.

### <a name="remarks"></a>Uwagi

Metoda ta jest przydatna do tymczasowego zatrzymania wykonywania procesora wirtualnego katalogu głównego, gdy nie można odnaleźć żadnych działań do harmonogramu. Wywołanie `Deactivate` metody muszą pochodzić z poziomu `Dispatch` metodę kontekstu wykonywania, z ostatniego uaktywnienia procesora wirtualnego katalogu głównego. Innymi słowy, serwer proxy wątku wywoływania `Deactivate` metoda musi być tą, która jest w trakcie wykonywania w głównym procesorze wirtualnym. Wywołanie metody w głównym procesorze wirtualnym, które nie wykonują na może spowodować niezdefiniowane zachowanie.

Dezaktywowane procesora wirtualnego katalogu głównego, mogą wznawiać wywołaniem `Activate` metody z samym argumentem, która została przekazana do `Deactivate` metody. Usługa scheduler jest odpowiedzialny za zapewnienie, który wywołuje w celu `Activate` i `Deactivate` metody są skojarzone, ale nie są wymagane do odebrania w określonej kolejności. Resource Manager może obsługiwać odbieranie wywołanie `Activate` metoda przed otrzyma wywołanie `Deactivate` miał trafić do metody.

Jeśli awakens procesora wirtualnego katalogu głównego i wartość zwrotną z elementu `Deactivate` metody jest wartością **false**, harmonogram powinien zapytania na liście uzupełniania UMS za pośrednictwem `IUMSCompletionList::GetUnblockNotifications` metody ustawy o te informacje, a następnie następnie wywołaj `Deactivate` ponownie metodą. Powinny to być powtarzane do czasu `Deactivate` metoda zwraca wartość `true`.

`invalid_argument` jest generowany, jeśli argument `pContext` ma wartość NULL.

`invalid_operation` jest generowany, jeśli nigdy nie został aktywowany procesora wirtualnego katalogu głównego, lub argument `pContext` nie reprezentuje kontekście wykonania, która została ostatnio wysyłane przez ten procesora wirtualnego katalogu głównego.

Czynność dezaktywowanie procesora wirtualnego katalogu głównego zmniejsza poziom subskrypcji w podstawowym wątku sprzętu przez jeden. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [iexecutionresource::currentsubscriptionlevel —](iexecutionresource-structure.md#currentsubscriptionlevel).

##  <a name="ensurealltasksvisible"></a>  Ivirtualprocessorroot::ensurealltasksvisible — metoda

Powoduje, że dane przechowywane w hierarchii pamięci pojedynczych procesorów, które stają się widoczne dla wszystkich procesorów w systemie. Zapewnia, że horyzont pamięci pełną została wykonana we wszystkich procesorach przed powrotem z metody.

```
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Kontekst, który jest aktualnie wysyłane przez ten procesora wirtualnego katalogu głównego.

### <a name="remarks"></a>Uwagi

Ta metoda mogą być przydatne, gdy chcesz zsynchronizować dezaktywacji procesora wirtualnego katalogu głównego dodając nowych zadań w ramach harmonogramu zadań. Ze względu na wydajność może zdecydować dodać elementy robocze do harmonogramu bez wykonywania barierę pamięci, co oznacza, elementy robocze dodane przez wątek wykonywania w jednym procesorze nie są natychmiast widoczne dla wszystkich innych procesorów. Za pomocą tej metody w połączeniu z `Deactivate` metody, można upewnić się, że harmonogramu nie dezaktywować jego Procesor wirtualny elementy główne, podczas gdy elementy robocze istnieje w kolekcji usługi scheduler.

Wywołanie `EnsureAllTasksVisibleThe` metody muszą pochodzić z poziomu `Dispatch` metodę kontekstu wykonywania, z ostatniego uaktywnienia procesora wirtualnego katalogu głównego. Innymi słowy, serwer proxy wątku wywoływania `EnsureAllTasksVisible` metoda musi być tą, która jest w trakcie wykonywania w głównym procesorze wirtualnym. Wywołanie metody w głównym procesorze wirtualnym, które nie wykonują na może spowodować niezdefiniowane zachowanie.

`invalid_argument` jest generowany, jeśli argument `pContext` ma wartość `NULL`.

`invalid_operation` jest generowany, jeśli nigdy nie został aktywowany procesora wirtualnego katalogu głównego, lub argument `pContext` nie reprezentuje kontekście wykonania, która została ostatnio wysyłane przez ten procesora wirtualnego katalogu głównego.

##  <a name="getid"></a>  Ivirtualprocessorroot::getid — metoda

Zwraca unikatowy identyfikator dla procesora wirtualnego katalogu głównego.

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator liczby całkowitej.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
