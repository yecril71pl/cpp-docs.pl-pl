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
ms.openlocfilehash: 451318bfbcfb9c5e002677556944e3499c0ed5fb
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525413"
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
|[unsupported_feature Constructor](#unsupported_feature)|Tworzy nowe wystąpienie klasy `unsupported_feature` wyjątku.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`runtime_exception`

`unsupported_feature`

## <a name="unsupported_feature"></a> unsupported_feature

  Tworzy nowe wystąpienie klasy `unsupported_feature` wyjątku.

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

**Namespace:** Współbieżność

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
