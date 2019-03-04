---
title: improper_scheduler_detach — Klasa
ms.date: 11/04/2016
f1_keywords:
- improper_scheduler_detach
- CONCRT/concurrency::improper_scheduler_detach
- CONCRT/concurrency::improper_scheduler_detach::improper_scheduler_detach
helpviewer_keywords:
- improper_scheduler_detach class
ms.assetid: 30132102-c900-4951-a470-b63b4e3aa2d2
ms.openlocfilehash: 7e85ff8ea7ffb817c141094649cd39b8becccf53
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285038"
---
# <a name="improperschedulerdetach-class"></a>improper_scheduler_detach — Klasa

Ta klasa opisuje wyjątek generowany, gdy `CurrentScheduler::Detach` metoda jest wywoływana w kontekście, który nie został dołączony do dowolnej harmonogramu przy użyciu `Attach` metody `Scheduler` obiektu.

## <a name="syntax"></a>Składnia

```
class improper_scheduler_detach : public std::exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[improper_scheduler_detach](#ctor)|Przeciążone. Konstruuje `improper_scheduler_detach` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`improper_scheduler_detach`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności

##  <a name="ctor"></a> improper_scheduler_detach —

Konstruuje `improper_scheduler_detach` obiektu.

```
explicit _CRTIMP improper_scheduler_detach(_In_z_ const char* _Message) throw();

improper_scheduler_detach() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat dotyczący błędu.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Scheduler, klasa](scheduler-class.md)
