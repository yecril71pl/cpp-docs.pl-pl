---
title: Schedulegroup — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ScheduleGroup
- CONCRT/concurrency::ScheduleGroup
- CONCRT/concurrency::ScheduleGroup::Id
- CONCRT/concurrency::ScheduleGroup::Reference
- CONCRT/concurrency::ScheduleGroup::Release
- CONCRT/concurrency::ScheduleGroup::ScheduleTask
dev_langs:
- C++
helpviewer_keywords:
- ScheduleGroup class
ms.assetid: 86d380ff-f2e8-411c-b1a8-22bd3079824a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90687a1e0cb77694fce9e60004f3e43d0ea9acf0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427423"
---
# <a name="schedulegroup-class"></a>ScheduleGroup — Klasa

Reprezentuje klasą abstrakcyjną dla grupy harmonogramów. Harmonogram grup organizuje zestaw powiązanych prac, które mają korzyści z zaplanowane blisko siebie czasowo, przez wykonywanie innego zadania w tej samej grupie przed przeniesieniem do innej grupy lub przestrzennie, wykonując wiele elementów w tej samej grupie na tym samym Węzeł NUMA lub fizycznym gnieździe.

## <a name="syntax"></a>Składnia

```
class ScheduleGroup;
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[~ ScheduleGroup — destruktor](#dtor)||

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Id](#id)|Zwraca identyfikator grupy harmonogramu, który jest unikatowy w obrębie harmonogramu, do której należy grupa.|
|[Dokumentacja](#reference)|Zwiększa liczbę odwołań harmonogramu grupy.|
|[Wersja](#release)|Dekrementuje liczbę odwołań harmonogramu grupy.|
|[Scheduletask —](#scheduletask)|Planuje pharmonogramy zadań wagi lekkiej w ramach harmonogramu grupy.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ScheduleGroup`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności

##  <a name="id"></a> Id

Zwraca identyfikator grupy harmonogramu, który jest unikatowy w obrębie harmonogramu, do której należy grupa.

```
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator grupy harmonogramu, który jest unikatowy w obrębie harmonogramu, do której należy grupa.

##  <a name="operator_delete"></a> Usuwanie operatora

A `ScheduleGroup` obiekt jest niszczony, wewnętrznie przez środowisko uruchomieniowe po udostępnieniu wszystkie odwołania zewnętrzne do niego. Go nie może zostać jawnie usunięte.

```
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

##  <a name="reference"></a> Odwołanie

Zwiększa liczbę odwołań harmonogramu grupy.

```
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Licznik odwołań nowo zwiększona.

### <a name="remarks"></a>Uwagi

Służy to zazwyczaj zarządzania okresem istnienia grupy harmonogramu dla kompozycji. Licznik odwołań harmonogramu grupy spadnie do zera, grupa harmonogramu są usuwane w czasie wykonywania. Grupy harmonogramu, utworzony za pomocą [currentscheduler::createschedulegroup —](currentscheduler-class.md#createschedulegroup) metody lub [Scheduler::createschedulegroup —](scheduler-class.md#createschedulegroup) metoda rozpoczyna się od jednego licznika odwołań.

##  <a name="release"></a> Wydania

Dekrementuje liczbę odwołań harmonogramu grupy.

```
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Licznik odwołań nowo zmniejszony.

### <a name="remarks"></a>Uwagi

Służy to zazwyczaj zarządzania okresem istnienia grupy harmonogramu dla kompozycji. Licznik odwołań harmonogramu grupy spadnie do zera, grupa harmonogramu są usuwane w czasie wykonywania. Po wywołaniu `Release` metody określonej liczby razy, aby usunąć tworzenia odwoływać się do liczby i wszelkie dodatkowe informacje, umieszczona przy użyciu `Reference` metody, nie możesz wykorzystywać dodatkowo grupa harmonogramu. Ten sposób spowoduje niezdefiniowane zachowanie.

Grupy harmonogramu jest skojarzony z wystąpieniem określonego harmonogramu. Należy się upewnić, że wszystkie odwołania do grupy harmonogramu są wydawane zanim wszystkie odwołania do usługi scheduler zostaną zwolnione, ponieważ ten ostatni może spowodować harmonogramu niszczone. Sposób, w przeciwnym razie powoduje niezdefiniowane zachowanie.

##  <a name="dtor"></a> ~ScheduleGroup

```
virtual ~ScheduleGroup();
```

##  <a name="scheduletask"></a> Scheduletask —

Planuje pharmonogramy zadań wagi lekkiej w ramach harmonogramu grupy.

```
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;
```

### <a name="parameters"></a>Parametry

*_Proc*<br/>
Wskaźnik do funkcji wykonać, aby wykonać treści zadania lekki.

*_Dane*<br/>
Pusty wskaźnik do danych, które zostaną przekazane jako parametr do treści zadania.

### <a name="remarks"></a>Uwagi

Wywoływanie `ScheduleTask` metoda niejawnie umieszcza licznik odwołań na grupy harmonogramu, który zostanie usunięty w czasie wykonywania w odpowiednim czasie po wykonaniu zadania.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[CurrentScheduler, klasa](currentscheduler-class.md)<br/>
[Scheduler, klasa](scheduler-class.md)<br/>
[Harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)

