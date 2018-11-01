---
title: unsupported_feature — Klasa
ms.date: 11/04/2016
f1_keywords:
- unsupported_feature
- AMPRT/unsupported_feature
- AMPRT/Concurrency::unsupported_feature
helpviewer_keywords:
- unsupported_feature class
ms.assetid: 6b1ab917-df13-48c7-9648-7cb2465a0ff5
ms.openlocfilehash: 155e96762d47b340ac078fad791f3078dba9a871
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497151"
---
# <a name="unsupportedfeature-class"></a>unsupported_feature — Klasa

Wyjątek, który jest zgłaszany, gdy używana jest nieobsługiwana funkcja.

## <a name="syntax"></a>Składnia

```
class unsupported_feature : public runtime_exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[unsupported_feature — Konstruktor](#ctor)|Tworzy nowe wystąpienie klasy `unsupported_feature` wyjątku.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`runtime_exception`

`unsupported_feature`

## <a name="unsupported_feature__ctor"></a> unsupported_feature

  Tworzy nowe wystąpienie nieobsługiwanego wyjątku unsupported_feature.

### <a name="syntax"></a>Składnia

```
explicit unsupported_feature(
    const char * _Message ) throw();

unsupported_feature() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opis błędu.

### <a name="return-value"></a>Wartość zwracana

`unsupported_feature` Obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt.h

**Namespace:** współbieżności

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
