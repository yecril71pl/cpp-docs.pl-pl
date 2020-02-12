---
title: scheduler_not_attached — Klasa
ms.date: 11/04/2016
f1_keywords:
- scheduler_not_attached
- CONCRT/concurrency::scheduler_not_attached
- CONCRT/concurrency::scheduler_not_attached::scheduler_not_attached
helpviewer_keywords:
- scheduler_not_attached class
ms.assetid: 26001970-b400-463b-be3d-8623359c399a
ms.openlocfilehash: a3b1c113e5c6c5feb5b2fa1940ee9b984233e4af
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142208"
---
# <a name="scheduler_not_attached-class"></a>scheduler_not_attached — Klasa

Ta klasa opisuje wyjątek zgłoszony podczas wykonywania operacji, który wymaga dołączenia harmonogramu do bieżącego kontekstu, a jeden nie jest.

## <a name="syntax"></a>Składnia

```cpp
class scheduler_not_attached : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[scheduler_not_attached](#ctor)|Przeciążone. Konstruuje obiekt `scheduler_not_attached`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`scheduler_not_attached`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>scheduler_not_attached

Konstruuje obiekt `scheduler_not_attached`.

```cpp
explicit _CRTIMP scheduler_not_attached(_In_z_ const char* _Message) throw();

scheduler_not_attached() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Scheduler, klasa](scheduler-class.md)
