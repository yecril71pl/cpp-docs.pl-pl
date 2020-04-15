---
title: IExecutionContext — Struktura
ms.date: 11/04/2016
f1_keywords:
- IExecutionContext
- CONCRTRM/concurrency::IExecutionContext
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::Dispatch
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetId
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetProxy
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetScheduler
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::SetProxy
helpviewer_keywords:
- IExecutionContext structure
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
ms.openlocfilehash: 532247ca1776452ad32476d2bcdfafcee3481058
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358801"
---
# <a name="iexecutioncontext-structure"></a>IExecutionContext — Struktura

Interfejs do kontekstu wykonywania, który można uruchomić na danym procesorze wirtualnym i być przełączane kontekstu współpracy.

## <a name="syntax"></a>Składnia

```cpp
struct IExecutionContext;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IExecutionContext::Dispatch](#dispatch)|Metoda, która jest wywoływana, gdy serwer proxy wątku rozpoczyna wykonywanie kontekstu określonego wykonywania. Powinno to być głównym procedury procesu roboczego dla harmonogramu.|
|[IExecutionContext::GetId](#getid)|Zwraca unikatowy identyfikator kontekstu wykonywania.|
|[IExecutionContext::GetProxy](#getproxy)|Zwraca interfejs do serwera proxy wątku, który wykonuje ten kontekst.|
|[IExecutionContext::GetScheduler](#getscheduler)|Zwraca interfejs do harmonogramu, do którego należy ten kontekst wykonywania.|
|[IExecutionContext::SetProxy](#setproxy)|Kojarzy serwer proxy wątku z tym kontekstem wykonywania. Skojarzony serwer proxy wątku wywołuje tę metodę tuż przed `Dispatch` rozpoczęciem wykonywania metody kontekstu.|

## <a name="remarks"></a>Uwagi

Jeśli implementujesz niestandardowy harmonogram, który łączy się z Menedżerem zasobów środowiska wykonawczego współbieżności, należy zaimplementować `IExecutionContext` interfejs. Wątki utworzone przez Menedżera zasobów wykonują pracę w imieniu harmonogramu, wykonując `IExecutionContext::Dispatch` metodę.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IExecutionContext`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Przestrzeń nazw:** współbieżność

## <a name="iexecutioncontextdispatch-method"></a><a name="dispatch"></a>IExecutionContext::Dispatch Metoda

Metoda, która jest wywoływana, gdy serwer proxy wątku rozpoczyna wykonywanie kontekstu określonego wykonywania. Powinno to być głównym procedury procesu roboczego dla harmonogramu.

```cpp
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```

### <a name="parameters"></a>Parametry

*pSAsat*<br/>
Wskaźnik do stanu, w którym ten kontekst wykonywania jest wywoływany. Aby uzyskać więcej informacji na temat stanu wysyłki, zobacz [DispatchState](dispatchstate-structure.md).

## <a name="iexecutioncontextgetid-method"></a><a name="getid"></a>IExecutionContext::Metoda GetId

Zwraca unikatowy identyfikator kontekstu wykonywania.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Unikatowy identyfikator liczby całkowitej.

### <a name="remarks"></a>Uwagi

Należy użyć tej `GetExecutionContextId` metody, aby uzyskać unikatowy identyfikator `IExecutionContext` dla obiektu, który implementuje interfejs, przed użyciem interfejsu jako parametru do metod dostarczonych przez Menedżera zasobów. Oczekuje się, że zwróci ten `GetId` sam identyfikator, gdy funkcja jest wywoływana.

Identyfikator uzyskany z innego źródła może spowodować niezdefiniowane zachowanie.

## <a name="iexecutioncontextgetproxy-method"></a><a name="getproxy"></a>IExecutionContext::Metoda GetProxy

Zwraca interfejs do serwera proxy wątku, który wykonuje ten kontekst.

```cpp
virtual IThreadProxy* GetProxy() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Interfejs. `IThreadProxy` Jeśli serwer proxy wątku kontekstu wykonania nie został `SetProxy`zainicjowany za `NULL`pomocą wywołania, funkcja musi zwrócić .

### <a name="remarks"></a>Uwagi

Menedżer zasobów wywoła `SetProxy` metodę w kontekście wykonywania, `IThreadProxy` z interfejsem jako parametr, `Dispatch` przed wprowadzeniem metody w kontekście. Oczekuje się, że ten argument zostanie `GetProxy()`przesłaniany i zwracany w zaproszeniach do .

## <a name="iexecutioncontextgetscheduler-method"></a><a name="getscheduler"></a>IExecutionContext::Metoda GetSchedulera

Zwraca interfejs do harmonogramu, do którego należy ten kontekst wykonywania.

```cpp
virtual IScheduler* GetScheduler() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Interfejs. `IScheduler`

### <a name="remarks"></a>Uwagi

Przed użyciem go jako parametru do `IScheduler` metod dostarczonych przez Menedżera zasobów jest wymagane zainicjowanie kontekstu wykonania przy użyciu prawidłowego interfejsu.

## <a name="iexecutioncontextsetproxy-method"></a><a name="setproxy"></a>IExecutionContext::Metoda SetProxy

Kojarzy serwer proxy wątku z tym kontekstem wykonywania. Skojarzony serwer proxy wątku wywołuje tę metodę tuż przed `Dispatch` rozpoczęciem wykonywania metody kontekstu.

```cpp
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```

### <a name="parameters"></a>Parametry

*pThreadProxy*<br/>
Interfejs do serwera proxy wątku, `Dispatch` który ma zamiar wprowadzić metodę w tym kontekście wykonywania.

### <a name="remarks"></a>Uwagi

Oczekuje się, aby `pThreadProxy` zapisać parametr i zwrócić `GetProxy` go na wywołanie metody. Menedżer zasobów gwarantuje, że serwer proxy wątku skojarzony z kontekstem wykonywania `Dispatch` nie ulegnie zmianie podczas wykonywania metody przez serwer proxy wątku.

## <a name="see-also"></a>Zobacz też

[współbieżność Obszar nazw](concurrency-namespace.md)<br/>
[IScheduler, struktura](ischeduler-structure.md)<br/>
[IThreadProxy, struktura](ithreadproxy-structure.md)
