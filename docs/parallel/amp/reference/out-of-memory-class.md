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
ms.openlocfilehash: 4edc1db3c1a70a41f9a0493bd3dc484e27f99b44
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126451"
---
# <a name="out_of_memory-class"></a>out_of_memory — Klasa

Wyjątek, który jest generowany, gdy metoda nie powiedzie się z powodu braku pamięci systemowej lub urządzenia.

## <a name="syntax"></a>Składnia

```cpp
class out_of_memory : public runtime_exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Konstruktor out_of_memory](#ctor)|Inicjuje nowe wystąpienie klasy `out_of_memory`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt. h

**Przestrzeń nazw:** Współbieżności
## <a name="ctor"></a>out_of_memory

Inicjuje nowe wystąpienie klasy.

### <a name="syntax"></a>Składnia

```cpp
explicit out_of_memory(
    const char * _Message ) throw();

out_of_memory () throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opis błędu.

### <a name="return-value"></a>Wartość zwrócona

Nowe wystąpienie klasy `out_of_memory`.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
