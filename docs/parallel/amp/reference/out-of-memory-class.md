---
title: out_of_memory — Klasa
ms.date: 11/04/2016
f1_keywords:
- out_of_memory
- AMPRT/out_of_memory
- AMPRT/Concurrency::out_of_memory::out_of_memory
helpviewer_keywords:
- out_of_memory class
ms.assetid: 3aa7e682-8f13-4ae6-9188-31fb423956e4
ms.openlocfilehash: 2d5d028739bdf1b1ac31fafe3719b7f3a98fbb07
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591899"
---
# <a name="outofmemory-class"></a>out_of_memory — Klasa

Wyjątek, który jest zgłaszany, gdy metoda nie powiedzie się z powodu braku pamięci systemowej lub urządzenia.

## <a name="syntax"></a>Składnia

```
class out_of_memory : public runtime_exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[out_of_memory Constructor](#ctor)|Inicjuje nowe wystąpienie klasy `out_of_memory` klasy.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt.h

**Namespace:** współbieżności
## <a name="ctor"></a> out_of_memory

Inicjuje nowe wystąpienie klasy.

### <a name="syntax"></a>Składnia

```
explicit out_of_memory(
    const char * _Message ) throw();

out_of_memory () throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opis błędu.

### <a name="return-value"></a>Wartość zwracana

Nowe wystąpienie klasy `out_of_memory` klasy.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
