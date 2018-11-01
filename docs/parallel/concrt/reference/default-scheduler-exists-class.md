---
title: default_scheduler_exists — Klasa
ms.date: 11/04/2016
f1_keywords:
- default_scheduler_exists
- CONCRT/concurrency::default_scheduler_exists
- CONCRT/concurrency::default_scheduler_exists::default_scheduler_exists
helpviewer_keywords:
- default_scheduler_exists class
ms.assetid: f6e575e2-4e0f-455a-9e06-54f462ce0c1c
ms.openlocfilehash: 149a220ba9498b1e1c3b7f09cef94c76c34ac4b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501975"
---
# <a name="defaultschedulerexists-class"></a>default_scheduler_exists — Klasa

Ta klasa opisuje wyjątek generowany, gdy `Scheduler::SetDefaultSchedulerPolicy` metoda jest wywoływana, gdy domyślnego harmonogramu już istnieje w ramach procesu.

## <a name="syntax"></a>Składnia

```
class default_scheduler_exists : public std::exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[default_scheduler_exists](#ctor)|Przeciążone. Konstruuje `default_scheduler_exists` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`default_scheduler_exists`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności

##  <a name="ctor"></a> default_scheduler_exists —

Konstruuje `default_scheduler_exists` obiektu.

```
explicit _CRTIMP default_scheduler_exists(_In_z_ const char* _Message) throw();

default_scheduler_exists() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat dotyczący błędu.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
