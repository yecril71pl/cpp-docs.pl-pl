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
ms.openlocfilehash: bd3d82c06c174c69c60dec33592110f4de72ac99
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141050"
---
# <a name="invalid_link_target-class"></a>invalid_link_target — Klasa

Ta klasa opisuje wyjątek zgłoszony, gdy wywoływana jest metoda `link_target` bloku komunikatów, a blok komunikatów nie może połączyć się z obiektem docelowym. Może to wynikać z przekroczenia liczby linków, do których blok komunikatów jest dozwolony, lub próba łączenia określonego elementu docelowego dwa razy do tego samego źródła.

## <a name="syntax"></a>Składnia

```cpp
class invalid_link_target : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[invalid_link_target](#ctor)|Przeciążone. Konstruuje obiekt `invalid_link_target`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`invalid_link_target`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>invalid_link_target

Konstruuje obiekt `invalid_link_target`.

```cpp
explicit _CRTIMP invalid_link_target(_In_z_ const char* _Message) throw();

invalid_link_target() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md)
