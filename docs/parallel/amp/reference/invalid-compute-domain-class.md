---
title: invalid_compute_domain — Klasa
ms.date: 11/04/2016
f1_keywords:
- invalid_compute_domain
- AMPRT/invalid_compute_domain
- AMPRT/Concurrency::invalid_compute_domain::invalid_compute_domain
helpviewer_keywords:
- invalid_compute_domain class
ms.assetid: ac7a7166-8bdb-4db1-8caf-ea129ab5117e
ms.openlocfilehash: 51fcd9e42bc4497131da5adb3dff72efb46537b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351722"
---
# <a name="invalidcomputedomain-class"></a>invalid_compute_domain — Klasa

Wyjątek, który jest zgłaszany, gdy środowisko uruchomieniowe nie może uruchomić jądra używając domeny obliczeniowej określonej w [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each) wywołania.

## <a name="syntax"></a>Składnia

```
class invalid_compute_domain : public runtime_exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[invalid_compute_domain Constructor](#ctor)|Inicjuje nowe wystąpienie klasy `invalid_compute_domain` klasy.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`runtime_exception`

`invalid_compute_domain`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt.h

**Namespace:** Współbieżność

## <a name="ctor"></a> invalid_compute_domain

Inicjuje nowe wystąpienie klasy.

## <a name="syntax"></a>Składnia

```
explicit invalid_compute_domain(
    const char * _Message ) throw();

invalid_compute_domain() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opis błędu.

### <a name="return-value"></a>Wartość zwracana

Wystąpienie `invalid_compute_domain` klasy

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
