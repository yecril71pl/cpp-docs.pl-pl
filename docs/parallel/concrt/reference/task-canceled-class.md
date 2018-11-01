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
ms.openlocfilehash: b17050deacd1dee0c1b08ffbc4056e957884cd3a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617454"
---
# <a name="taskcanceled-class"></a>task_canceled — Klasa

Ta klasa opisuje wyjątek generowany przez warstwę zadań PPL, aby wymusić anulowanie bieżącego zadania. Jest to również generowane przez `get()` metody [zadań](/visualstudio/extensibility/debugger/task-class-internal-members), dla anulowanych zadań.

## <a name="syntax"></a>Składnia

```
class task_canceled : public std::exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[task_canceled](#ctor)|Przeciążone. Konstruuje `task_canceled` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`task_canceled`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności

##  <a name="ctor"></a> task_canceled —

Konstruuje `task_canceled` obiektu.

```
explicit _CRTIMP task_canceled(_In_z_ const char* _Message) throw();

task_canceled() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat dotyczący błędu.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
