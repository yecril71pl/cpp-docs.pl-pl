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
ms.openlocfilehash: 0d1c28501abc86d09b683b0ed91f831fe8697306
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462054"
---
# <a name="schedulerpolicy-class"></a>SchedulerPolicy — Klasa

`SchedulerPolicy` Klasa zawiera zestaw pary klucz/wartość, jeden dla każdego elementu zasad, które kontrolują zachowanie wystąpienia harmonogramu.

## <a name="syntax"></a>Składnia

```
class SchedulerPolicy;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[SchedulerPolicy](#ctor)|Przeciążone. Tworzy nową zasadę harmonogramu i wypełnia ją wartościami dla [klucze zasad](concurrency-namespace-enums.md) obsługiwane transfery danych w środowisku uruchomieniowym współbieżności: a Resource Manager.|
|[~ SchedulerPolicy — destruktor](#dtor)|Niszczy zasadę harmonogramu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[GetPolicyValue](#getpolicyvalue)|Pobiera wartość klucza zasad podana jako `key` parametru.|
|[Setconcurrencylimits —](#setconcurrencylimits)|Jednocześnie ustawia `MinConcurrency` i `MaxConcurrency` zasad na `SchedulerPolicy` obiektu.|
|[SetPolicyValue](#setpolicyvalue)|Ustawia wartość klucza zasad podana jako `key` parametr i zwraca starą wartość.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator=](#operator_eq)|Przypisuje zasady harmonogramu z innych zasad harmonogramu.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat zasad, które mogą być kontrolowane za pomocą `SchedulerPolicy` klasy, zobacz [policyelementkey —](concurrency-namespace-enums.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SchedulerPolicy`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h, concrtrm.h

**Namespace:** współbieżności

##  <a name="getpolicyvalue"></a> Getpolicyvalue —

Pobiera wartość klucza zasad podana jako `key` parametru.

```
unsigned int GetPolicyValue(PolicyElementKey key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz zasad w celu pobrania wartości.

### <a name="return-value"></a>Wartość zwracana

Jeśli klucz określony przez `key` parametr jest obsługiwany, rzutować wartość zasady dla klucza `unsigned int`.

### <a name="remarks"></a>Uwagi

Metoda zgłosi [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) dla klucza nieprawidłowe zasady.

##  <a name="operator_eq"></a> operator =

Przypisuje zasady harmonogramu z innych zasad harmonogramu.

```
SchedulerPolicy& operator= (const SchedulerPolicy& _RhsPolicy);
```

### <a name="parameters"></a>Parametry

*_RhsPolicy*<br/>
Zasady można przypisać do tych zasad.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do zasad harmonogramu.

### <a name="remarks"></a>Uwagi

Często Najwygodniejszym sposobem zdefiniowania nowej zasady harmonogramu jest skopiowanie istniejącej zasady i modyfikować za pomocą `SetPolicyValue` lub `SetConcurrencyLimits` metody.

##  <a name="ctor"></a> Schedulerpolicy —

Tworzy nową zasadę harmonogramu i wypełnia ją wartościami dla [klucze zasad](concurrency-namespace-enums.md) obsługiwane transfery danych w środowisku uruchomieniowym współbieżności: a Resource Manager.

```
SchedulerPolicy();

SchedulerPolicy(
    size_t _PolicyKeyCount,
...);

SchedulerPolicy(
    const SchedulerPolicy& _SrcPolicy);
```

### <a name="parameters"></a>Parametry

*_PolicyKeyCount*<br/>
Liczba klucz/wartość pary poniżej `_PolicyKeyCount` parametru.

*_SrcPolicy*<br/>
Zasady źródłowe do skopiowania.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor tworzy nową zasadę harmonogramu, gdzie wszystkie zasady zostaną zainicjowane do ich wartości domyślnych.

Drugi Konstruktor tworzy nową zasadę harmonogramu, który używa stylu o nazwie parametru inicjalizacji. Wartości po `_PolicyKeyCount` parametrze są dostarczane jako pary klucz/wartość. Każdy klucz polityki, który nie jest określony w tym konstruktorze będzie mieć wartość domyślną. Ten konstruktor może wyrzucić [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md), [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) lub [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md).

Trzeci Konstruktor jest konstruktorem kopiującym. Często Najwygodniejszym sposobem zdefiniowania nowej zasady harmonogramu jest skopiowanie istniejącej zasady i modyfikować za pomocą `SetPolicyValue` lub `SetConcurrencyLimits` metody.

##  <a name="dtor"></a> ~SchedulerPolicy

Niszczy zasadę harmonogramu.

```
~SchedulerPolicy();
```

##  <a name="setconcurrencylimits"></a> Setconcurrencylimits —

Jednocześnie ustawia `MinConcurrency` i `MaxConcurrency` zasad na `SchedulerPolicy` obiektu.

```
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```

### <a name="parameters"></a>Parametry

*_MinConcurrency*<br/>
Wartość `MinConcurrency` klucz zasad.

*_MaxConcurrency*<br/>
Wartość `MaxConcurrency` klucz zasad.

### <a name="remarks"></a>Uwagi

Metoda zgłosi [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md) Jeśli wartość określona dla `MinConcurrency` zasad jest większy niż określony dla `MaxConcurrency` zasad.

Metoda może również zgłosić [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) inne nieprawidłowe wartości.

##  <a name="setpolicyvalue"></a> Setpolicyvalue —

Ustawia wartość klucza zasad podana jako `key` parametr i zwraca starą wartość.

```
unsigned int SetPolicyValue(
    PolicyElementKey key,
    unsigned int value);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz zasad można ustawić wartości.

*value*<br/>
Wartość do ustawienia klucza zasad.

### <a name="return-value"></a>Wartość zwracana

Jeśli klucz określony przez `key` parametr jest obsługiwany, stara wartość zasady dla klucza rzutowane na `unsigned int`.

### <a name="remarks"></a>Uwagi

Metoda zgłosi [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) dla klucza nieprawidłowe zasady lub każdy klucz polityki, którego wartość nie może ustawić `SetPolicyValue` metody.

Metoda zgłosi [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) dla wartości, która nie jest obsługiwana dla klucza określonego przez `key` parametru.

Należy zauważyć, że ta metoda nie można ustawić `MinConcurrency` lub `MaxConcurrency` zasad. Aby ustawić te wartości, należy użyć [setconcurrencylimits —](#setconcurrencylimits) metody.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[CurrentScheduler, klasa](currentscheduler-class.md)<br/>
[Scheduler, klasa](scheduler-class.md)<br/>
[Harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)

