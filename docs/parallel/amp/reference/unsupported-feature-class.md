---
title: unsupported_feature — Klasa
ms.date: 03/27/2019
f1_keywords:
- unsupported_feature
- AMPRT/unsupported_feature
- AMPRT/Concurrency::unsupported_feature
helpviewer_keywords:
- unsupported_feature class
ms.assetid: 6b1ab917-df13-48c7-9648-7cb2465a0ff5
ms.openlocfilehash: 561f0a258943f6d7e1c0f1b5cae716592c931fbc
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127715"
---
# <a name="unsupported_feature-class"></a>unsupported_feature — Klasa

Wyjątek, który jest generowany w przypadku użycia nieobsługiwanej funkcji.

## <a name="syntax"></a>Składnia

```cpp
class unsupported_feature : public runtime_exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Konstruktor unsupported_feature](#unsupported_feature)|Tworzy nowe wystąpienie wyjątku `unsupported_feature`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`runtime_exception`

`unsupported_feature`

## <a name="unsupported_feature"></a>unsupported_feature

  Tworzy nowe wystąpienie wyjątku `unsupported_feature`.

### <a name="syntax"></a>Składnia

```cpp
explicit unsupported_feature(
    const char * _Message ) throw();

unsupported_feature() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opis błędu.

### <a name="return-value"></a>Wartość zwrócona

Obiekt `unsupported_feature`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt. h

**Przestrzeń nazw:** Współbieżności

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
