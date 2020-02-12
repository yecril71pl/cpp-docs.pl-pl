---
title: invalid_oversubscribe_operation — Klasa
ms.date: 11/04/2016
f1_keywords:
- invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation::invalid_oversubscribe_operation
helpviewer_keywords:
- invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
ms.openlocfilehash: 7a879fc2da2f963cd4b5ea5fcd7e9506f86ce051
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140834"
---
# <a name="invalid_oversubscribe_operation-class"></a>invalid_oversubscribe_operation — Klasa

Ta klasa opisuje wyjątek zgłoszony, gdy metoda `Context::Oversubscribe` jest wywoływana z parametrem `_BeginOversubscription` ustawionym na **wartość false** bez wcześniejszego wywołania metody `Context::Oversubscribe` z parametrem `_BeginOversubscription` ustawionym na **wartość true**.

## <a name="syntax"></a>Składnia

```cpp
class invalid_oversubscribe_operation : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[invalid_oversubscribe_operation](#ctor)|Przeciążone. Konstruuje obiekt `invalid_oversubscribe_operation`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`invalid_oversubscribe_operation`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>invalid_oversubscribe_operation

Konstruuje obiekt `invalid_oversubscribe_operation`.

```cpp
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

invalid_oversubscribe_operation() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
