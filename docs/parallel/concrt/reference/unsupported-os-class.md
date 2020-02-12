---
title: unsupported_os — Klasa
ms.date: 11/04/2016
f1_keywords:
- unsupported_os
- CONCRT/concurrency::unsupported_os
- CONCRT/concurrency::unsupported_os::unsupported_os
helpviewer_keywords:
- unsupported_os class
ms.assetid: 6fa57636-341b-4b51-84cc-261d283ff736
ms.openlocfilehash: 253cd76182e1b6f85be3701663bd10c86c10e6ba
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142340"
---
# <a name="unsupported_os-class"></a>unsupported_os — Klasa

Ta klasa opisuje wyjątek zgłoszony, gdy używany jest nieobsługiwany system operacyjny.

## <a name="syntax"></a>Składnia

```cpp
class unsupported_os : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[unsupported_os](#ctor)|Przeciążone. Konstruuje obiekt `unsupported_os`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`unsupported_os`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>unsupported_os

Konstruuje obiekt `unsupported_os`.

### <a name="syntax"></a>Składnia

```cpp
explicit _CRTIMP unsupported_os(_In_z_ const char* _Message) throw();

unsupported_os() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
