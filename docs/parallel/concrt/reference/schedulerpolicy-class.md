---
title: SchedulerPolicy — Klasa
ms.date: 11/04/2016
f1_keywords:
- SchedulerPolicy
- concrt/concurrency::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::GetPolicyValue
- concrt/concurrency::SchedulerPolicy::SetConcurrencyLimits
- concrt/concurrency::SchedulerPolicy::SetPolicyValue
helpviewer_keywords:
- SchedulerPolicy class
ms.assetid: bcebf51a-65f8-45a3-809b-d1ff93527dc4
ms.openlocfilehash: fed33c198502b75e824bcaf698227d283f4b85f9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142749"
---
# <a name="schedulerpolicy-class"></a>SchedulerPolicy — Klasa

Klasa `SchedulerPolicy` zawiera zestaw par klucz/wartość, jeden dla każdego elementu zasad, kontrolujący zachowanie wystąpienia harmonogramu.

## <a name="syntax"></a>Składnia

```cpp
class SchedulerPolicy;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[SchedulerPolicy](#ctor)|Przeciążone. Konstruuje nowe zasady harmonogramu i wypełnia je wartościami [kluczy zasad](concurrency-namespace-enums.md) obsługiwanymi przez środowisko uruchomieniowe współbieżności harmonogramy i Menedżer zasobów.|
|[~ SchedulerPolicy destruktor](#dtor)|Niszczy zasady usługi Scheduler.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[GetPolicyValue —](#getpolicyvalue)|Pobiera wartość klucza zasad podanego jako parametr `key`.|
|[SetConcurrencyLimits —](#setconcurrencylimits)|Jednocześnie ustawia zasady `MinConcurrency` i `MaxConcurrency` w obiekcie `SchedulerPolicy`.|
|[SetPolicyValue —](#setpolicyvalue)|Ustawia wartość klucza zasad podaną jako parametr `key` i zwraca starą wartość.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[operator =](#operator_eq)|Przypisuje zasady harmonogramu z innych zasad usługi Scheduler.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat zasad, które mogą być kontrolowane za pomocą klasy `SchedulerPolicy`, zobacz [PolicyElementKey —](concurrency-namespace-enums.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SchedulerPolicy`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h, concrtrm. h

**Przestrzeń nazw:** współbieżność

## <a name="getpolicyvalue"></a>GetPolicyValue —

Pobiera wartość klucza zasad podanego jako parametr `key`.

```cpp
unsigned int GetPolicyValue(PolicyElementKey key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz zasad, dla którego ma zostać pobrana wartość.

### <a name="return-value"></a>Wartość zwrócona

Jeśli klucz określony przez parametr `key` jest obsługiwany, wartość zasad dla klucza rzutowania na `unsigned int`.

### <a name="remarks"></a>Uwagi

Metoda zgłosi [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) dla nieprawidłowego klucza zasad.

## <a name="operator_eq"></a>operator =

Przypisuje zasady harmonogramu z innych zasad usługi Scheduler.

```cpp
SchedulerPolicy& operator= (const SchedulerPolicy& _RhsPolicy);
```

### <a name="parameters"></a>Parametry

*_RhsPolicy*<br/>
Zasady do przypisania do tych zasad.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do zasad usługi Scheduler.

### <a name="remarks"></a>Uwagi

Często Najwygodniejszym sposobem zdefiniowania nowych zasad harmonogramu jest skopiowanie istniejących zasad i zmodyfikowanie ich przy użyciu metod `SetPolicyValue` lub `SetConcurrencyLimits`.

## <a name="ctor"></a>SchedulerPolicy

Konstruuje nowe zasady harmonogramu i wypełnia je wartościami [kluczy zasad](concurrency-namespace-enums.md) obsługiwanymi przez środowisko uruchomieniowe współbieżności harmonogramy i Menedżer zasobów.

```cpp
SchedulerPolicy();

SchedulerPolicy(
    size_t _PolicyKeyCount,
...);

SchedulerPolicy(
    const SchedulerPolicy& _SrcPolicy);
```

### <a name="parameters"></a>Parametry

*_PolicyKeyCount*<br/>
Liczba par klucz/wartość, które są zgodne z parametrem `_PolicyKeyCount`.

*_SrcPolicy*<br/>
Zasady źródłowe do skopiowania.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor tworzy nowe zasady harmonogramu, w przypadku których wszystkie zasady zostaną zainicjowane do ich wartości domyślnych.

Drugi Konstruktor tworzy nowe zasady harmonogramu, które używają stylu parametru inicjującego. Wartości po parametrze `_PolicyKeyCount` są podawane jako pary klucz/wartość. Każdy klucz zasad, który nie jest określony w tym konstruktorze, będzie miał jego wartość domyślną. Ten konstruktor może zgłosić wyjątki [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md), [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) lub [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md).

Trzeci konstruktor jest konstruktorem kopiującym. Często Najwygodniejszym sposobem zdefiniowania nowych zasad harmonogramu jest skopiowanie istniejących zasad i zmodyfikowanie ich przy użyciu metod `SetPolicyValue` lub `SetConcurrencyLimits`.

## <a name="dtor"></a>~ SchedulerPolicy

Niszczy zasady usługi Scheduler.

```cpp
~SchedulerPolicy();
```

## <a name="setconcurrencylimits"></a>SetConcurrencyLimits —

Jednocześnie ustawia zasady `MinConcurrency` i `MaxConcurrency` w obiekcie `SchedulerPolicy`.

```cpp
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```

### <a name="parameters"></a>Parametry

*_MinConcurrency*<br/>
Wartość klucza zasad `MinConcurrency`.

*_MaxConcurrency*<br/>
Wartość klucza zasad `MaxConcurrency`.

### <a name="remarks"></a>Uwagi

Metoda spowoduje zgłoszenie [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md) , jeśli wartość określona dla zasad `MinConcurrency` jest większa niż określona dla zasad `MaxConcurrency`.

Metoda może również generować [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) dla innych nieprawidłowych wartości.

## <a name="setpolicyvalue"></a>SetPolicyValue —

Ustawia wartość klucza zasad podaną jako parametr `key` i zwraca starą wartość.

```cpp
unsigned int SetPolicyValue(
    PolicyElementKey key,
    unsigned int value);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz zasad, dla którego ma zostać ustawiona wartość.

*value*<br/>
Wartość, dla której ma zostać ustawiony klucz zasad.

### <a name="return-value"></a>Wartość zwrócona

Jeśli klucz określony przez parametr `key` jest obsługiwany, stara wartość zasad dla klucza rzutowania na `unsigned int`.

### <a name="remarks"></a>Uwagi

Metoda zgłosi [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) dla nieprawidłowego klucza zasad lub dowolnego klucza zasad, którego wartość nie może być ustawiona przez metodę `SetPolicyValue`.

Metoda zgłosi [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) dla wartości, która nie jest obsługiwana dla klucza określonego przez parametr `key`.

Należy zauważyć, że ta metoda nie jest dozwolona do ustawiania zasad `MinConcurrency` lub `MaxConcurrency`. Aby ustawić te wartości, użyj metody [SetConcurrencyLimits —](#setconcurrencylimits) .

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[PolicyElementKey —](concurrency-namespace-enums.md)<br/>
[CurrentScheduler, klasa](currentscheduler-class.md)<br/>
[Scheduler, klasa](scheduler-class.md)<br/>
[Harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
