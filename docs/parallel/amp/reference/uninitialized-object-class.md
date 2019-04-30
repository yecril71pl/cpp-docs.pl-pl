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
ms.openlocfilehash: 05c24672531d50fa9bc31587e6c6733fdff21f29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405459"
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
|[uninitialized_object Constructor](#uninitialized_object)|Inicjuje nowe wystąpienie klasy `uninitialized_object` klasy.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`runtime_exception`

`uninitialized_object`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt.h

**Namespace:** Współbieżność

## <a name="uninitializedobject"></a>uninitialized_object

Tworzy nowe wystąpienie klasy `uninitialized_object` wyjątku.

### <a name="syntax"></a>Składnia

```
explicit uninitialized_object(
    const char * _Message ) throw();

uninitialized_object() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opis błędu.

### <a name="return-value"></a>Wartość zwracana

`uninitialized_object` Obiekt wyjątku.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
