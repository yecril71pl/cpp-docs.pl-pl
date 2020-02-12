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
ms.openlocfilehash: 2f5ad16893a898d4258762b25fea3d557607a3f8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141153"
---
# <a name="improper_scheduler_detach-class"></a>improper_scheduler_detach — Klasa

Ta klasa opisuje wyjątek zgłoszony, gdy metoda `CurrentScheduler::Detach` jest wywoływana w kontekście, który nie został dołączony do żadnego harmonogramu przy użyciu metody `Attach` obiektu `Scheduler`.

## <a name="syntax"></a>Składnia

```cpp
class improper_scheduler_detach : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[improper_scheduler_detach](#ctor)|Przeciążone. Konstruuje obiekt `improper_scheduler_detach`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`improper_scheduler_detach`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>improper_scheduler_detach

Konstruuje obiekt `improper_scheduler_detach`.

```cpp
explicit _CRTIMP improper_scheduler_detach(_In_z_ const char* _Message) throw();

improper_scheduler_detach() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Scheduler, klasa](scheduler-class.md)
