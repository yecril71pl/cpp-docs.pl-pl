---
title: uninitialized_object — Klasa
ms.date: 11/04/2016
f1_keywords:
- uninitialized_object
- AMPRT/uninitialized_object
- AMPRT/Concurrency::uninitialized_object
helpviewer_keywords:
- uninitialized_object class
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
ms.openlocfilehash: 1c431364aee0f1d1e75059abdb023ae52cf92155
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279344"
---
# <a name="uninitializedobject-class"></a>uninitialized_object — Klasa

Wyjątek, który jest zgłaszany, gdy używany jest obiekt niezainicjowany.

## <a name="syntax"></a>Składnia

```
class uninitialized_object : public runtime_exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[uninitialized_object Constructor](#ctor)|Inicjuje nowe wystąpienie klasy `uninitialized_object` klasy.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`runtime_exception`

`uninitialized_object`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt.h

**Namespace:** Współbieżność
## <a name="uninitialized_object__ctor"></a> unsupported_feature

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

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
