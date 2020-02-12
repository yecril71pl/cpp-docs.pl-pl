---
title: invalid_multiple_scheduling — Klasa
ms.date: 11/04/2016
f1_keywords:
- invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling::invalid_multiple_scheduling
helpviewer_keywords:
- invalid_multiple_scheduling class
ms.assetid: e9a47cb7-a778-4df7-92b0-3752119fd4c7
ms.openlocfilehash: a8b2a045ce94562dcba0019bc03aaa90c4d384a9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140906"
---
# <a name="invalid_multiple_scheduling-class"></a>invalid_multiple_scheduling — Klasa

Ta klasa opisuje wyjątek zgłoszony, gdy `task_handle` obiektu jest zaplanowana wiele razy przy użyciu metody `run` obiektu `task_group` lub `structured_task_group` bez wywoływania wywołującego metody `wait` lub `run_and_wait`.

## <a name="syntax"></a>Składnia

```cpp
class invalid_multiple_scheduling : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[invalid_multiple_scheduling](#ctor)|Przeciążone. Konstruuje obiekt `invalid_multiple_scheduling`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`invalid_multiple_scheduling`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>invalid_multiple_scheduling

Konstruuje obiekt `invalid_multiple_scheduling`.

```cpp
explicit _CRTIMP invalid_multiple_scheduling(_In_z_ const char* _Message) throw();

invalid_multiple_scheduling() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[task_handle, klasa](task-handle-class.md)<br/>
[task_group, klasa](task-group-class.md)<br/>
[wykonane](task-group-class.md)<br/>
[trwa](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[structured_task_group, klasa](structured-task-group-class.md)
