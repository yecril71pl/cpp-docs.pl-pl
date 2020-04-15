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
ms.openlocfilehash: e716d4952bdb9634cc0d195285d3a65c5c06b0a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336804"
---
# <a name="out_of_memory-class"></a>out_of_memory — Klasa

Wyjątek, który jest zgłaszany, gdy metoda nie powiedzie się z powodu braku pamięci systemu lub urządzenia.

## <a name="syntax"></a>Składnia

```cpp
class out_of_memory : public runtime_exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[konstruktor out_of_memory](#ctor)|Inicjuje nowe wystąpienie klasy `out_of_memory`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt.h

**Obszar nazw:** Współbieżności

## <a name="out_of_memory"></a><a name="ctor"></a>out_of_memory

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

### <a name="return-value"></a>Wartość zwracana

Nowe wystąpienie `out_of_memory` klasy.

## <a name="see-also"></a>Zobacz też

[Obszar nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
