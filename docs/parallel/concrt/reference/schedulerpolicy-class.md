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
ms.openlocfilehash: b7b99dae2ffb58123c05a65872e4c71e149ac12c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219576"
---
# <a name="schedulerpolicy-class"></a>SchedulerPolicy — Klasa

`SchedulerPolicy`Klasa zawiera zestaw par klucz/wartość, jeden dla każdego elementu zasad, kontrolujący zachowanie wystąpienia harmonogramu.

## <a name="syntax"></a>Składnia

```cpp
class SchedulerPolicy;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[SchedulerPolicy](#ctor)|Przeciążone. Konstruuje nowe zasady harmonogramu i wypełnia je wartościami [kluczy zasad](concurrency-namespace-enums.md) obsługiwanymi przez środowisko uruchomieniowe współbieżności harmonogramy i Menedżer zasobów.|
|[~ SchedulerPolicy destruktor](#dtor)|Niszczy zasady usługi Scheduler.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[GetPolicyValue —](#getpolicyvalue)|Pobiera wartość klucza zasad podanego jako `key` parametr.|
|[SetConcurrencyLimits —](#setconcurrencylimits)|Jednocześnie ustawia `MinConcurrency` zasady i `MaxConcurrency` dla `SchedulerPolicy` obiektu.|
|[SetPolicyValue —](#setpolicyvalue)|Ustawia wartość klucza zasad dostarczonego jako `key` parametr i zwraca starą wartość.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator =](#operator_eq)|Przypisuje zasady harmonogramu z innych zasad usługi Scheduler.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat zasad, które mogą być kontrolowane za pomocą `SchedulerPolicy` klasy, zobacz [PolicyElementKey —](concurrency-namespace-enums.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SchedulerPolicy`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h, concrtrm. h

**Przestrzeń nazw:** współbieżność

## <a name="getpolicyvalue"></a><a name="getpolicyvalue"></a>GetPolicyValue —

Pobiera wartość klucza zasad podanego jako `key` parametr.

```cpp
unsigned int GetPolicyValue(PolicyElementKey key) const;
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Klucz zasad, dla którego ma zostać pobrana wartość.

### <a name="return-value"></a>Wartość zwracana

Jeśli klucz określony przez `key` parametr jest obsługiwany, wartość zasad dla klucza jest rzutowana na **`unsigned int`** .

### <a name="remarks"></a>Uwagi

Metoda zgłosi [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) dla nieprawidłowego klucza zasad.

## <a name="operator"></a><a name="operator_eq"></a>operator =

Przypisuje zasady harmonogramu z innych zasad usługi Scheduler.

```cpp
SchedulerPolicy& operator= (const SchedulerPolicy& _RhsPolicy);
```

### <a name="parameters"></a>Parametry

*_RhsPolicy*<br/>
Zasady do przypisania do tych zasad.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do zasad usługi Scheduler.

### <a name="remarks"></a>Uwagi

Często Najwygodniejszym sposobem zdefiniowania nowych zasad harmonogramu jest skopiowanie istniejących zasad i zmodyfikowanie ich przy użyciu `SetPolicyValue` `SetConcurrencyLimits` metod lub.

## <a name="schedulerpolicy"></a><a name="ctor"></a>SchedulerPolicy

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
Liczba par klucz/wartość, które są zgodne z `_PolicyKeyCount` parametrem.

*_SrcPolicy*<br/>
Zasady źródłowe do skopiowania.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor tworzy nowe zasady harmonogramu, w przypadku których wszystkie zasady zostaną zainicjowane do ich wartości domyślnych.

Drugi Konstruktor tworzy nowe zasady harmonogramu, które używają stylu parametru inicjującego. Wartości po `_PolicyKeyCount` parametrze są podawane jako pary klucz/wartość. Każdy klucz zasad, który nie jest określony w tym konstruktorze, będzie miał jego wartość domyślną. Ten konstruktor może zgłosić wyjątki [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md), [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) lub [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md).

Trzeci konstruktor jest konstruktorem kopiującym. Często Najwygodniejszym sposobem zdefiniowania nowych zasad harmonogramu jest skopiowanie istniejących zasad i zmodyfikowanie ich przy użyciu `SetPolicyValue` `SetConcurrencyLimits` metod lub.

## <a name="schedulerpolicy"></a><a name="dtor"></a>~ SchedulerPolicy

Niszczy zasady usługi Scheduler.

```cpp
~SchedulerPolicy();
```

## <a name="setconcurrencylimits"></a><a name="setconcurrencylimits"></a>SetConcurrencyLimits —

Jednocześnie ustawia `MinConcurrency` zasady i `MaxConcurrency` dla `SchedulerPolicy` obiektu.

```cpp
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```

### <a name="parameters"></a>Parametry

*_MinConcurrency*<br/>
Wartość `MinConcurrency` klucza zasad.

*_MaxConcurrency*<br/>
Wartość `MaxConcurrency` klucza zasad.

### <a name="remarks"></a>Uwagi

Metoda spowoduje zgłoszenie [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md) , jeśli wartość określona dla `MinConcurrency` zasad jest większa niż określona dla `MaxConcurrency` zasad.

Metoda może również generować [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) dla innych nieprawidłowych wartości.

## <a name="setpolicyvalue"></a><a name="setpolicyvalue"></a>SetPolicyValue —

Ustawia wartość klucza zasad dostarczonego jako `key` parametr i zwraca starą wartość.

```cpp
unsigned int SetPolicyValue(
    PolicyElementKey key,
    unsigned int value);
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Klucz zasad, dla którego ma zostać ustawiona wartość.

*wartościami*<br/>
Wartość, dla której ma zostać ustawiony klucz zasad.

### <a name="return-value"></a>Wartość zwracana

Jeśli klucz określony przez `key` parametr jest obsługiwany, stara wartość zasad dla klucza rzutowanego na **`unsigned int`** .

### <a name="remarks"></a>Uwagi

Metoda zgłosi [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) dla nieprawidłowego klucza zasad lub dowolnego klucza zasad, którego wartość nie może zostać ustawiona przez `SetPolicyValue` metodę.

Metoda zgłosi [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) dla wartości, która nie jest obsługiwana dla klucza określonego przez `key` parametr.

Należy zauważyć, że ta metoda nie może ustawiać `MinConcurrency` zasad ani `MaxConcurrency` . Aby ustawić te wartości, użyj metody [SetConcurrencyLimits —](#setconcurrencylimits) .

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[PolicyElementKey —](concurrency-namespace-enums.md)<br/>
[Klasa CurrentScheduler](currentscheduler-class.md)<br/>
[Scheduler — Klasa](scheduler-class.md)<br/>
[Harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
