---
title: missing_wait — Klasa
ms.date: 11/04/2016
f1_keywords:
- missing_wait
- CONCRT/concurrency::missing_wait
- CONCRT/concurrency::missing_wait::missing_wait
helpviewer_keywords:
- missing_wait class
ms.assetid: ff981875-bd43-47e3-806f-b03c9f418b18
ms.openlocfilehash: cf81d1ee6c144da210da5b1f37aca7910ae37bc8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142390"
---
# <a name="missing_wait-class"></a>missing_wait — Klasa

Ta klasa opisuje wyjątek zgłoszony, gdy istnieją zadania, które są nadal zaplanowane do `task_group` lub `structured_task_group` obiektu w czasie wykonywania destruktora obiektu. Ten wyjątek nigdy nie zostanie wygenerowany, jeśli destruktor zostanie osiągnięty z powodu odwinięcia stosu w wyniku wyjątku.

## <a name="syntax"></a>Składnia

```cpp
class missing_wait : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[missing_wait](#ctor)|Przeciążone. Konstruuje obiekt `missing_wait`.|

## <a name="remarks"></a>Uwagi

Nieobecny przepływ wyjątku, użytkownik jest odpowiedzialny za wywoływanie metody `wait` lub `run_and_wait` obiektu `task_group` lub `structured_task_group` przed umożliwieniem temu obiektowi. Środowisko uruchomieniowe zgłasza ten wyjątek jako wskazanie, że nie można wywołać metody `wait` lub `run_and_wait`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`missing_wait`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>missing_wait

Konstruuje obiekt `missing_wait`.

```cpp
explicit _CRTIMP missing_wait(_In_z_ const char* _Message) throw();

missing_wait() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[task_group, klasa](task-group-class.md)<br/>
[trwa](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[structured_task_group, klasa](structured-task-group-class.md)
