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
ms.openlocfilehash: a61e72f14448d5033d5be9069ffeec7d3bb08061
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142559"
---
# <a name="task_handle-class"></a>task_handle — Klasa

Klasa `task_handle` reprezentuje pojedynczy równoległy element roboczy. Hermetyzuje instrukcje i dane wymagane do wykonania zadania.

## <a name="syntax"></a>Składnia

```cpp
template<
    typename _Function
>
class task_handle : public ::Concurrency::details::_UnrealizedChore;
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ obiektu funkcji, który zostanie wywołany do wykonania pracy reprezentowanej przez obiekt `task_handle`.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[task_handle](#task_handle)|Tworzy nowy obiekt `task_handle`. Zadanie jest wykonywane przez wywołanie funkcji określonej jako parametr do konstruktora.|
|[~ task_handle destruktor](#dtor)|Niszczy obiekt `task_handle`.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[operator ()](#task_handle__operator_call)|Operator wywołania funkcji wywoływany przez środowisko uruchomieniowe w celu wykonania pracy z uchwytem zadania.|

## <a name="remarks"></a>Uwagi

obiektów `task_handle` można używać w połączeniu z `structured_task_group` lub bardziej ogólnym obiektem `task_group`, aby rozłożyć prace na równoległe zadania. Aby uzyskać więcej informacji, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Należy pamiętać, że twórca obiektu `task_handle` jest odpowiedzialny za utrzymanie okresu istnienia utworzonego obiektu `task_handle`, dopóki nie będzie on już wymagany przez środowisko uruchomieniowe współbieżności. Zazwyczaj oznacza to, że obiekt `task_handle` nie może być destruktorem do momentu wywołania metody `wait` lub `run_and_wait` `task_group` lub `structured_task_group`, do której został umieszczony w kolejce.

obiekty `task_handle` są zwykle używane w połączeniu z C++ wyrażeniami lambda. Ponieważ nie znasz prawdziwego typu lambda, funkcja [make_task](concurrency-namespace-functions.md#make_task) jest zwykle używana do tworzenia obiektu `task_handle`.

Środowisko uruchomieniowe tworzy kopię funkcji pracy przekazanej do obiektu `task_handle`. W związku z tym wszystkie zmiany stanu, które występują w obiekcie funkcji przekazywanym do obiektu `task_handle` nie będą wyświetlane w kopii tego obiektu funkcji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`task_handle`

## <a name="requirements"></a>Wymagania

**Nagłówek:** PPL. h

**Przestrzeń nazw:** współbieżność

## <a name="task_handle__operator_call"></a>operator ()

Operator wywołania funkcji wywoływany przez środowisko uruchomieniowe w celu wykonania pracy z uchwytem zadania.

```cpp
void operator()() const;
```

## <a name="task_handle"></a>task_handle

Tworzy nowy obiekt `task_handle`. Zadanie jest wykonywane przez wywołanie funkcji określonej jako parametr do konstruktora.

```cpp
task_handle(const _Function& _Func);
```

### <a name="parameters"></a>Parametry

*_Func*<br/>
Funkcja, która będzie wywoływana w celu wykonania pracy reprezentowanej przez obiekt `task_handle`. Może to być Funktor lambda, wskaźnik do funkcji lub dowolny obiekt obsługujący wersję operatora wywołania funkcji z podpisem `void operator()()`.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe tworzy kopię funkcji pracy przekazanej do konstruktora. W związku z tym wszystkie zmiany stanu, które występują w obiekcie funkcji przekazywanym do obiektu `task_handle` nie będą wyświetlane w kopii tego obiektu funkcji.

## <a name="dtor"></a>~ task_handle

Niszczy obiekt `task_handle`.

```cpp
~task_handle();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[task_group, klasa](task-group-class.md)<br/>
[structured_task_group, klasa](structured-task-group-class.md)
