---
title: uninitialized_object — Klasa
ms.date: 03/27/2019
f1_keywords:
- uninitialized_object
- AMPRT/uninitialized_object
- AMPRT/Concurrency::uninitialized_object
helpviewer_keywords:
- uninitialized_object class
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
ms.openlocfilehash: ef7ded0bf925d3430b70064c4979b75e08f9cf45
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127702"
---
# <a name="uninitialized_object-class"></a>uninitialized_object — Klasa

Wyjątek, który jest generowany, gdy jest używany Niezainicjowany obiekt.

## <a name="syntax"></a>Składnia

```cpp
class uninitialized_object : public runtime_exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Konstruktor uninitialized_object](#uninitialized_object)|Inicjuje nowe wystąpienie klasy `uninitialized_object`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`runtime_exception`

`uninitialized_object`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt. h

**Przestrzeń nazw:** Współbieżności

## <a name="uninitialized_object"></a>uninitialized_object

Tworzy nowe wystąpienie wyjątku `uninitialized_object`.

### <a name="syntax"></a>Składnia

```cpp
explicit uninitialized_object(
    const char * _Message ) throw();

uninitialized_object() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opis błędu.

### <a name="return-value"></a>Wartość zwrócona

Obiekt wyjątku `uninitialized_object`.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
