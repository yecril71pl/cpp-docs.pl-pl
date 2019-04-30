---
title: nested_scheduler_missing_detach — Klasa
ms.date: 11/04/2016
f1_keywords:
- nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach::nested_scheduler_missing_detach
helpviewer_keywords:
- nested_scheduler_missing_detach class
ms.assetid: 65d3f277-6d43-4160-97ef-caf8b26c1641
ms.openlocfilehash: db51f7b083cc0cbd9337fbbe5c672d190208f328
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394393"
---
# <a name="nestedschedulermissingdetach-class"></a>nested_scheduler_missing_detach — Klasa

Ta klasa opisuje wyjątek generowany, gdy w środowisku uruchomieniowym współbieżności: wykrywa, czy możesz zwrócenia przez niego do wywołania `CurrentScheduler::Detach` metody na poziomie kontekstu, który dołączony do drugiego za pomocą harmonogramu `Attach` metody `Scheduler` obiektu.

## <a name="syntax"></a>Składnia

```
class nested_scheduler_missing_detach : public std::exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[nested_scheduler_missing_detach](#ctor)|Przeciążone. Konstruuje `nested_scheduler_missing_detach` obiektu.|

## <a name="remarks"></a>Uwagi

Ten wyjątek jest zgłaszany tylko wtedy, gdy zagnieździć jednego harmonogramu wewnątrz innego przez wywołanie metody `Attach` metody `Scheduler` obiektów na poziomie kontekstu, który jest już właścicielem lub dołączone do innej usługi scheduler. Środowisko uruchomieniowe współbieżności zgłosi wyjątek, ten wyjątek tylko wtedy kiedy scenariusz może wykryć jako pomoc do lokalizowania problem. Nie każde wystąpienie pominięcie wywołać `CurrentScheduler::Detach` metody jest gwarantowane, generują ten wyjątek.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`nested_scheduler_missing_detach`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności

##  <a name="ctor"></a> nested_scheduler_missing_detach

Konstruuje `nested_scheduler_missing_detach` obiektu.

```
explicit _CRTIMP nested_scheduler_missing_detach(_In_z_ const char* _Message) throw();

nested_scheduler_missing_detach() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat dotyczący błędu.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Scheduler, klasa](scheduler-class.md)
