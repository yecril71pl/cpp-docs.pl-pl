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
ms.openlocfilehash: de7393c9186a1572040acd18854b5b3046b239f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552792"
---
# <a name="improperlock-class"></a>improper_lock — Klasa

Ta klasa opisuje wyjątek generowany, gdy jest blokada nieprawidłowo.

## <a name="syntax"></a>Składnia

```
class improper_lock : public std::exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[improper_lock](#ctor)|Przeciążone. Konstruuje `improper_lock exception`.|

## <a name="remarks"></a>Uwagi

Zazwyczaj ten wyjątek jest zgłaszany, gdy podejmowana jest próba uzyskania rekursywnie blokady nie obsługującą, w tym samym kontekście.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`improper_lock`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności

##  <a name="ctor"></a> improper_lock —

Konstruuje `improper_lock exception`.

```
explicit _CRTIMP improper_lock(_In_z_ const char* _Message) throw();

improper_lock() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat dotyczący błędu.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[critical_section, klasa](critical-section-class.md)<br/>
[reader_writer_lock, klasa](reader-writer-lock-class.md)
