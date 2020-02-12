---
title: task_canceled — Klasa
ms.date: 11/04/2016
f1_keywords:
- task_canceled
- CONCRT/concurrency::task_canceled
- CONCRT/concurrency::task_canceled::task_canceled
helpviewer_keywords:
- task_canceled class
ms.assetid: c3f0b234-2cc1-435f-a48e-995f45b190be
ms.openlocfilehash: b1436f921343843ee2b50888f00b6d470e513329
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142604"
---
# <a name="task_canceled-class"></a>task_canceled — Klasa

Ta klasa opisuje wyjątek zgłoszony przez warstwę zadań PPL w celu wymuszenia anulowania bieżącego zadania. Jest on również generowany przez metodę `get()` w [zadaniu](/visualstudio/extensibility/debugger/task-class-internal-members)dla anulowanego zadania.

## <a name="syntax"></a>Składnia

```cpp
class task_canceled : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[task_canceled](#ctor)|Przeciążone. Konstruuje obiekt `task_canceled`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`task_canceled`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>task_canceled

Konstruuje obiekt `task_canceled`.

```cpp
explicit _CRTIMP task_canceled(_In_z_ const char* _Message) throw();

task_canceled() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
