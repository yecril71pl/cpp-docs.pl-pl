---
title: improper_scheduler_reference — Klasa
ms.date: 11/04/2016
f1_keywords:
- improper_scheduler_reference
- CONCRT/concurrency::improper_scheduler_reference
- CONCRT/concurrency::improper_scheduler_reference::improper_scheduler_reference
helpviewer_keywords:
- improper_scheduler_reference class
ms.assetid: 434a7512-7796-4255-92a7-f3bf71c6a7a7
ms.openlocfilehash: 18536043b0d46a6f27f1e5c60778a22af82ad2d3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141109"
---
# <a name="improper_scheduler_reference-class"></a>improper_scheduler_reference — Klasa

Ta klasa opisuje wyjątek zgłoszony, gdy metoda `Reference` jest wywoływana w obiekcie `Scheduler`, który jest zamykany, z kontekstu, który nie jest częścią tego harmonogramu.

## <a name="syntax"></a>Składnia

```cpp
class improper_scheduler_reference : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[improper_scheduler_reference](#ctor)|Przeciążone. Konstruuje obiekt `improper_scheduler_reference`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`improper_scheduler_reference`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>improper_scheduler_reference

Konstruuje obiekt `improper_scheduler_reference`.

```cpp
explicit _CRTIMP improper_scheduler_reference(_In_z_ const char* _Message) throw();

improper_scheduler_reference() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Scheduler, klasa](scheduler-class.md)
