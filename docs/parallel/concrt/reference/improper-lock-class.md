---
title: improper_lock — Klasa
ms.date: 11/04/2016
f1_keywords:
- improper_lock
- CONCRT/concurrency::improper_lock
- CONCRT/concurrency::improper_lock::improper_lock
helpviewer_keywords:
- improper_lock class
ms.assetid: 8f494942-7748-4a2a-8de2-23414bfe6346
ms.openlocfilehash: 886444f3e856234be010715a8ee0c707cf919bb4
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142398"
---
# <a name="improper_lock-class"></a>improper_lock — Klasa

Ta klasa opisuje wyjątek zgłoszony, gdy blokada jest pobrana nieprawidłowo.

## <a name="syntax"></a>Składnia

```cpp
class improper_lock : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[improper_lock](#ctor)|Przeciążone. Konstruuje `improper_lock exception`.|

## <a name="remarks"></a>Uwagi

Zazwyczaj ten wyjątek jest zgłaszany, gdy podejmowana jest próba uzyskania blokady niewspółpracującej cyklicznie w tym samym kontekście.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`improper_lock`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>improper_lock

Konstruuje `improper_lock exception`.

```cpp
explicit _CRTIMP improper_lock(_In_z_ const char* _Message) throw();

improper_lock() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[critical_section, klasa](critical-section-class.md)<br/>
[reader_writer_lock, klasa](reader-writer-lock-class.md)
