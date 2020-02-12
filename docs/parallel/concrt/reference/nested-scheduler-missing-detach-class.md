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
ms.openlocfilehash: 8c9553b036890c4ce28f1060bfe2f58ee1904935
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138858"
---
# <a name="nested_scheduler_missing_detach-class"></a>nested_scheduler_missing_detach — Klasa

Ta klasa opisuje wyjątek zgłoszony, gdy środowisko uruchomieniowe współbieżności wykryje, że wywołała metodę `CurrentScheduler::Detach` w kontekście dołączonym do drugiego harmonogramu przy użyciu metody `Attach` obiektu `Scheduler`.

## <a name="syntax"></a>Składnia

```cpp
class nested_scheduler_missing_detach : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[nested_scheduler_missing_detach](#ctor)|Przeciążone. Konstruuje obiekt `nested_scheduler_missing_detach`.|

## <a name="remarks"></a>Uwagi

Ten wyjątek jest zgłaszany tylko w przypadku zagnieżdżania jednego harmonogramu w innym, wywołując metodę `Attach` obiektu `Scheduler` w kontekście, który jest już własnością lub jest dołączony do innego harmonogramu. Środowisko uruchomieniowe współbieżności zgłasza ten wyjątek odpowiednio Uzgodnij, gdy może wykryć scenariusz jako pomoc w celu zlokalizowania problemu. Nie każde wystąpienie zaniedbania wywołania metody `CurrentScheduler::Detach` jest gwarantowane wygenerowanie tego wyjątku.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`nested_scheduler_missing_detach`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>nested_scheduler_missing_detach

Konstruuje obiekt `nested_scheduler_missing_detach`.

```cpp
explicit _CRTIMP nested_scheduler_missing_detach(_In_z_ const char* _Message) throw();

nested_scheduler_missing_detach() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Scheduler, klasa](scheduler-class.md)
