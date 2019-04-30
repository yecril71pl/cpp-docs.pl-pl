---
title: task_handle — Klasa
ms.date: 03/27/2019
f1_keywords:
- task_handle
- PPL/concurrency::task_handle
- PPL/concurrency::task_handle::task_handle
helpviewer_keywords:
- task_handle class
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
ms.openlocfilehash: 8528bc212603484be9325ed967e9475e4faa1348
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346156"
---
# <a name="taskhandle-class"></a>task_handle — Klasa

`task_handle` Klasa reprezentuje pojedynczy równoległe element roboczy. Hermetyzuje on instrukcje, jak i dane wymagane do wykonania pracy.

## <a name="syntax"></a>Składnia

```
template<
    typename _Function
>
class task_handle : public ::Concurrency::details::_UnrealizedChore;
```

#### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ obiektu funkcji, który zostanie wywołany do wykonywania pracy, reprezentowane przez `task_handle` obiektu.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[task_handle](#task_handle)|Tworzy nowy `task_handle` obiektu. Praca zadania jest wykonywana przez wywołanie funkcji, określony jako parametr do konstruktora.|
|[~task_handle Destructor](#dtor)|Niszczy `task_handle` obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator()](#task_handle__operator_call)|Operator wywołania funkcji środowiska uruchomieniowego wywołuje w celu wykonania pracy obsługi zadań.|

## <a name="remarks"></a>Uwagi

`task_handle` obiekty mogą być używane w połączeniu z `structured_task_group` lub bardziej ogólnej `task_group` obiekt Rozkładaj pracę do zadań równoległych. Aby uzyskać więcej informacji, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Należy pamiętać, że twórca `task_handle` obiekt jest odpowiedzialna za okres istnienia utworzony `task_handle` obiektu, dopóki nie jest już wymagany w czasie wykonywania współbieżności. Zazwyczaj oznacza to, że `task_handle` obiektu nie musi niszczenia do momentu `wait` lub `run_and_wait` metody `task_group` lub `structured_task_group` została wywołana, do którego jest umieszczane w kolejce.

`task_handle` obiekty są zazwyczaj używane w połączeniu z wyrażenia lambda w języku C++. Ponieważ nie jest znany typ wartość true, wyrażenia lambda, [make_task —](concurrency-namespace-functions.md#make_task) funkcji jest zazwyczaj używany do tworzenia `task_handle` obiektu.

Środowisko uruchomieniowe tworzy kopię ta funkcja pracy, który jest przekazywany do `task_handle` obiektu. W związku z tym, wszelkie zmiany stanu, które występują w funkcji obiektu, były przekazywane do `task_handle` obiektu nie będą widoczne w swoją kopię tego obiektu funkcji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`task_handle`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ppl.h

**Namespace:** współbieżności

##  <a name="task_handle__operator_call"></a> Operator()

Operator wywołania funkcji środowiska uruchomieniowego wywołuje w celu wykonania pracy obsługi zadań.

```
void operator()() const;
```

## <a name="taskhandle"></a>task_handle

Tworzy nowy `task_handle` obiektu. Praca zadania jest wykonywana przez wywołanie funkcji, określony jako parametr do konstruktora.

```
task_handle(const _Function& _Func);
```

### <a name="parameters"></a>Parametry

*_Func*<br/>
Funkcja, która zostanie wywołany do wykonywania pracy, reprezentowane przez `task_handle` obiektu. Może to być funktorem lambda, wskaźnika do funkcji, lub dowolnego obiektu, która obsługuje wersję operator wywołania funkcji z podpisem `void operator()()`.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe tworzy kopię ta funkcja pracy, który jest przekazywany do konstruktora. W związku z tym, wszelkie zmiany stanu, które występują w funkcji obiektu, były przekazywane do `task_handle` obiektu nie będą widoczne w swoją kopię tego obiektu funkcji.

##  <a name="dtor"></a> ~ task_handle

Niszczy `task_handle` obiektu.

```
~task_handle();
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[task_group, klasa](task-group-class.md)<br/>
[structured_task_group, klasa](structured-task-group-class.md)
