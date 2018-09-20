---
title: invalid_multiple_scheduling — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling::invalid_multiple_scheduling
dev_langs:
- C++
helpviewer_keywords:
- invalid_multiple_scheduling class
ms.assetid: e9a47cb7-a778-4df7-92b0-3752119fd4c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71898449447595db5df66ce619c423d62f2410be
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384922"
---
# <a name="invalidmultiplescheduling-class"></a>invalid_multiple_scheduling — Klasa

Ta klasa opisuje wyjątek generowany, gdy `task_handle` obiekt jest zaplanowane wiele razy, używając `run` metody `task_group` lub `structured_task_group` obiekt bez interwencyjnego wywołania `wait` lub `run_and_wait` metody.

## <a name="syntax"></a>Składnia

```
class invalid_multiple_scheduling : public std::exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[invalid_multiple_scheduling](#ctor)|Przeciążone. Konstruuje `invalid_multiple_scheduling` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`invalid_multiple_scheduling`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności

##  <a name="ctor"></a> invalid_multiple_scheduling —

Konstruuje `invalid_multiple_scheduling` obiektu.

```
explicit _CRTIMP invalid_multiple_scheduling(_In_z_ const char* _Message) throw();

invalid_multiple_scheduling() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat dotyczący błędu.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[task_handle, klasa](task-handle-class.md)<br/>
[task_group — klasa](task-group-class.md)<br/>
[run](task-group-class.md)<br/>
[Czekaj](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[structured_task_group, klasa](structured-task-group-class.md)
