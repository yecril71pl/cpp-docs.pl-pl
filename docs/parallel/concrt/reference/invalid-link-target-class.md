---
title: invalid_link_target — Klasa
ms.date: 11/04/2016
f1_keywords:
- invalid_link_target
- CONCRT/concurrency::invalid_link_target
- CONCRT/concurrency::invalid_link_target::invalid_link_target
helpviewer_keywords:
- invalid_link_target class
ms.assetid: 33b64885-34d8-4d4e-a893-02e9f19c958e
ms.openlocfilehash: 3ef34ab7607c444044b6dde17f3db3f73d0d7086
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62205659"
---
# <a name="invalidlinktarget-class"></a>invalid_link_target — Klasa

Ta klasa opisuje wyjątek generowany, gdy `link_target` zostanie wywołana metoda Blok obsługi wiadomości i bloku obsługi wiadomości nie jest w stanie połączyć się z obiektem docelowym. Może to być wynikiem przekroczenie liczby łącza, blok komunikatów jest dozwolone, czy próba połączyć określony element docelowy dwa razy tego samego źródła.

## <a name="syntax"></a>Składnia

```
class invalid_link_target : public std::exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[invalid_link_target](#ctor)|Przeciążone. Konstruuje `invalid_link_target` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`invalid_link_target`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności

##  <a name="ctor"></a> invalid_link_target —

Konstruuje `invalid_link_target` obiektu.

```
explicit _CRTIMP invalid_link_target(_In_z_ const char* _Message) throw();

invalid_link_target() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat dotyczący błędu.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md)
