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
ms.openlocfilehash: 45d65a5e16121d39233c3ceb801933aa1f5a5f8e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138917"
---
# <a name="iexecutioncontext-structure"></a>IExecutionContext — Struktura

Interfejs do kontekstu wykonywania, który może być uruchamiany w danym procesorze wirtualnym i być przełączany w ramach współdziałania z podsiecią.

## <a name="syntax"></a>Składnia

```cpp
struct IExecutionContext;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[IExecutionContext::D ispatch](#dispatch)|Metoda wywoływana, gdy serwer proxy wątku uruchamia wykonywanie określonego kontekstu wykonania. Powinna to być główna procedura procesu roboczego dla harmonogramu.|
|[IExecutionContext:: GetId —](#getid)|Zwraca unikatowy identyfikator kontekstu wykonania.|
|[IExecutionContext:: GetProxy](#getproxy)|Zwraca interfejs do serwera proxy wątku, który wykonuje ten kontekst.|
|[IExecutionContext:: getschedulerer](#getscheduler)|Zwraca interfejs do harmonogramu, do którego należy ten kontekst wykonania.|
|[IExecutionContext:: SetProxy](#setproxy)|Kojarzy serwer proxy wątku z tym kontekstem wykonania. Skojarzony serwer proxy wątku wywołuje tę metodę bezpośrednio przed rozpoczęciem wykonywania metody `Dispatch` kontekstu.|

## <a name="remarks"></a>Uwagi

W przypadku implementowania niestandardowego harmonogramu, który ma interfejsy z Menedżer zasobów środowisko uruchomieniowe współbieżności, należy zaimplementować interfejs `IExecutionContext`. Wątki utworzone przez Menedżer zasobów wykonują pracę w imieniu harmonogramu, wykonując metodę `IExecutionContext::Dispatch`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IExecutionContext`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm. h

**Przestrzeń nazw:** współbieżność

## <a name="dispatch"></a>IExecutionContext::D ispatch — Metoda

Metoda wywoływana, gdy serwer proxy wątku uruchamia wykonywanie określonego kontekstu wykonania. Powinna to być główna procedura procesu roboczego dla harmonogramu.

```cpp
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```

### <a name="parameters"></a>Parametry

*pDispatchState*<br/>
Wskaźnik do stanu, w którym jest wysyłany ten kontekst wykonania. Aby uzyskać więcej informacji o stanie wysyłania, zobacz [DispatchState](dispatchstate-structure.md).

## <a name="getid"></a>IExecutionContext:: GetId —, Metoda

Zwraca unikatowy identyfikator kontekstu wykonania.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Unikatowy identyfikator liczby całkowitej.

### <a name="remarks"></a>Uwagi

Należy użyć metody `GetExecutionContextId`, aby uzyskać unikatowy identyfikator obiektu, który implementuje interfejs `IExecutionContext`, przed użyciem interfejsu jako parametru do metod dostarczonych przez Menedżer zasobów. Po wywołaniu funkcji `GetId` należy zwrócić ten sam identyfikator.

Identyfikator uzyskany z innego źródła może spowodować niezdefiniowane zachowanie.

## <a name="getproxy"></a>IExecutionContext:: GetProxy — Metoda

Zwraca interfejs do serwera proxy wątku, który wykonuje ten kontekst.

```cpp
virtual IThreadProxy* GetProxy() = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Interfejs `IThreadProxy`. Jeśli serwer proxy wątku nie został zainicjowany z wywołaniem `SetProxy`, funkcja musi zwrócić `NULL`.

### <a name="remarks"></a>Uwagi

Menedżer zasobów wywoła metodę `SetProxy` w kontekście wykonywania, przy użyciu interfejsu `IThreadProxy` jako parametru, przed wprowadzeniem metody `Dispatch` w kontekście. Oczekiwany jest zapisanie tego argumentu i zwrócenie go na wywołania `GetProxy()`.

## <a name="getscheduler"></a>IExecutionContext:: GetScheduler — Metoda

Zwraca interfejs do harmonogramu, do którego należy ten kontekst wykonania.

```cpp
virtual IScheduler* GetScheduler() = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Interfejs `IScheduler`.

### <a name="remarks"></a>Uwagi

Musisz zainicjować kontekst wykonywania z prawidłowym interfejsem `IScheduler`, zanim użyjesz go jako parametru do metod dostarczonych przez Menedżer zasobów.

## <a name="setproxy"></a>IExecutionContext:: SetProxy — Metoda

Kojarzy serwer proxy wątku z tym kontekstem wykonania. Skojarzony serwer proxy wątku wywołuje tę metodę bezpośrednio przed rozpoczęciem wykonywania metody `Dispatch` kontekstu.

```cpp
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```

### <a name="parameters"></a>Parametry

*pThreadProxy*<br/>
Interfejs serwera proxy wątku, który ma wprowadzić metodę `Dispatch` w tym kontekście wykonania.

### <a name="remarks"></a>Uwagi

Należy zapisać parametr `pThreadProxy` i zwrócić go w wywołaniu metody `GetProxy`. Menedżer zasobów gwarantuje, że serwer proxy wątku skojarzony z kontekstem wykonywania nie ulegnie zmianie, gdy serwer proxy wątku wykonuje metodę `Dispatch`.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[IScheduler, struktura](ischeduler-structure.md)<br/>
[IThreadProxy, struktura](ithreadproxy-structure.md)
