---
title: ScheduleGroup — Klasa
ms.date: 11/04/2016
f1_keywords:
- ScheduleGroup
- CONCRT/concurrency::ScheduleGroup
- CONCRT/concurrency::ScheduleGroup::Id
- CONCRT/concurrency::ScheduleGroup::Reference
- CONCRT/concurrency::ScheduleGroup::Release
- CONCRT/concurrency::ScheduleGroup::ScheduleTask
helpviewer_keywords:
- ScheduleGroup class
ms.assetid: 86d380ff-f2e8-411c-b1a8-22bd3079824a
ms.openlocfilehash: 8686b5ef0906e3188a1e683d1190bbe6124cd19e
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417132"
---
# <a name="schedulegroup-class"></a>ScheduleGroup — Klasa

Reprezentuje streszczenie dla grupy harmonogramów. Grupy harmonogramu organizują zestaw pokrewnych zadań, które nie mogą być wykonywane równolegle, przez wykonywanie innego zadania w tej samej grupie przed przechodzeniem do innej grupy lub w dowolnym miejscu, przez wykonanie wielu elementów w tej samej grupie Węzeł NUMA lub gniazdo fizyczne.

## <a name="syntax"></a>Składnia

```cpp
class ScheduleGroup;
```

## <a name="members"></a>Members

### <a name="protected-constructors"></a>Konstruktory chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[~ Destruktor](#dtor)||

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Identyfikator](#id)|Zwraca identyfikator grupy harmonogramu, która jest unikatowa w ramach harmonogramu, do którego należy Grupa.|
|[Dokumentacja](#reference)|Zwiększa liczbę odwołań do grup harmonogramów.|
|[Wersja](#release)|Zmniejsza liczbę odwołań grup harmonogramów.|
|[ScheduleTask —](#scheduletask)|Planuje zadanie lekkiej wagi w ramach grupy harmonogramów.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ScheduleGroup`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="id"></a>#

Zwraca identyfikator grupy harmonogramu, która jest unikatowa w ramach harmonogramu, do którego należy Grupa.

```cpp
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Identyfikator grupy harmonogramu, który jest unikatowy w obrębie harmonogramu, do którego należy Grupa.

## <a name="operator_delete"></a>Usuwanie operatora

Obiekt `ScheduleGroup` jest niszczony wewnętrznie przez środowisko uruchomieniowe, gdy zostaną wydane wszystkie odwołania zewnętrzne. Nie można go jawnie usunąć.

```cpp
void operator delete(
    void* _PObject);

void operator delete(
    void* _PObject,
    int,
const char *,
    int);
```

### <a name="parameters"></a>Parametry

*_PObject*<br/>
Wskaźnik do obiektu, który ma zostać usunięty.

## <a name="reference"></a>Odwoła

Zwiększa liczbę odwołań do grup harmonogramów.

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Nowo zwiększona liczba odwołań.

### <a name="remarks"></a>Uwagi

Jest to zwykle używane do zarządzania okresem istnienia grupy harmonogramu dla kompozycji. Gdy liczba odwołań dla grupy harmonogramów jest równa zero, Grupa harmonogramów jest usuwana przez środowisko uruchomieniowe. Grupa harmonogramów utworzona przy użyciu metody [CurrentScheduler::](currentscheduler-class.md#createschedulegroup) w ramach harmonogramu lub metody [Scheduler:: SetSchedule](scheduler-class.md#createschedulegroup) jest uruchamiana z liczbą odwołań o jednej.

## <a name="release"></a>Usuwanie

Zmniejsza liczbę odwołań grup harmonogramów.

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Nowo zmniejszona liczba odwołań.

### <a name="remarks"></a>Uwagi

Jest to zwykle używane do zarządzania okresem istnienia grupy harmonogramu dla kompozycji. Gdy liczba odwołań dla grupy harmonogramów jest równa zero, Grupa harmonogramów jest usuwana przez środowisko uruchomieniowe. Po wywołaniu metody `Release` określonej liczby prób usunięcia liczby odwołań do tworzenia i dowolnych dodatkowych odwołań przy użyciu metody `Reference` nie można jeszcze użyć grupy harmonogramu. Wykonanie tej czynności spowoduje niezdefiniowane zachowanie.

Grupa harmonogramu jest skojarzona z określonym wystąpieniem harmonogramu. Musisz się upewnić, że wszystkie odwołania do grupy harmonogramów zostaną wydane przed zwolnieniem wszystkich odwołań do harmonogramu, ponieważ to drugie może spowodować zniszczenie usługi Scheduler. W przeciwnym razie wyniki są niezdefiniowane.

## <a name="dtor"></a>~ Schedule

```cpp
virtual ~ScheduleGroup();
```

## <a name="scheduletask"></a>ScheduleTask —

Planuje zadanie lekkiej wagi w ramach grupy harmonogramów.

```cpp
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;
```

### <a name="parameters"></a>Parametry

*_Proc*<br/>
Wskaźnik do funkcji, która ma zostać wykonana, aby wykonać treść zadania o lekkim średnim poziomie.

*_Data*<br/>
Wskaźnik void do danych, które zostaną przesłane jako parametr do treści zadania.

### <a name="remarks"></a>Uwagi

Wywołanie metody `ScheduleTask` niejawnie umieszcza liczbę odwołań w grupie harmonogramów, która jest usuwana przez środowisko uruchomieniowe w odpowiednim czasie po wykonaniu zadania.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[CurrentScheduler, klasa](currentscheduler-class.md)<br/>
[Scheduler, klasa](scheduler-class.md)<br/>
[Harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
