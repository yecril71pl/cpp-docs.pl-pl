---
title: context_self_unblock — Klasa
ms.date: 11/04/2016
f1_keywords:
- context_self_unblock
- CONCRT/concurrency::context_self_unblock
- CONCRT/concurrency::context_self_unblock::context_self_unblock
helpviewer_keywords:
- context_self_unblock class
ms.assetid: 9601cd28-4f40-4c2e-89ab-747068956331
ms.openlocfilehash: 883d5630251a6ea13afba1164f221a0da1773c17
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143112"
---
# <a name="context_self_unblock-class"></a>context_self_unblock — Klasa

Ta klasa opisuje wyjątek zgłoszony, gdy metoda `Unblock` obiektu `Context` jest wywoływana z tego samego kontekstu. Spowoduje to wskazanie próby odblokowania przez dany kontekst.

## <a name="syntax"></a>Składnia

```cpp
class context_self_unblock : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[context_self_unblock](#ctor)|Przeciążone. Konstruuje obiekt `context_self_unblock`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`context_self_unblock`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>context_self_unblock

Konstruuje obiekt `context_self_unblock`.

```cpp
explicit _CRTIMP context_self_unblock(_In_z_ const char* _Message) throw();

context_self_unblock() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
