---
title: runtime_exception — Klasa
ms.date: 03/27/2019
f1_keywords:
- runtime_exception
- AMPRT/runtime_exception
- AMPRT/Concurrency::runtime_exception
- AMPRT/Concurrency::runtime_exception::get_error_code
helpviewer_keywords:
- runtime_exception class
ms.assetid: 8fe3ce2c-3d4c-4b9c-95e8-e592f37adefd
ms.openlocfilehash: 6ad784720833d2ae5de7d653d132ba144aec2677
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126384"
---
# <a name="runtime_exception-class"></a>runtime_exception — Klasa

Typ podstawowy dla wyjątków w przyspieszonej C++ bibliotece o dużej współbieżności (amp).

### <a name="syntax"></a>Składnia

```cpp
class runtime_exception : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Konstruktor runtime_exception](#ctor)|Inicjuje nowe wystąpienie klasy `runtime_exception`.|
|[~ runtime_exception destruktor](#dtor)|Niszczy obiekt `runtime_exception`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[get_error_code](#get_error_code)|Zwraca kod błędu, który spowodował wyjątek.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[operator =](#operator_eq)|Kopiuje zawartość określonego obiektu `runtime_exception` do tego.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`runtime_exception`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt. h

**Przestrzeń nazw:** Współbieżności

## <a name="ctor"></a>Konstruktor runtime_exception

Inicjuje nowe wystąpienie klasy.

### <a name="syntax"></a>Składnia

```cpp
runtime_exception(
    const char * _Message,
    HRESULT _Hresult ) throw();

explicit runtime_exception(
    HRESULT _Hresult ) throw();

runtime_exception(
    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opis błędu, który spowodował wyjątek.

*_Hresult*<br/>
WYNIK HRESULT błędu, który spowodował wyjątek.

*_Other*<br/>
Obiekt `runtime_exception` do skopiowania.

### <a name="return-value"></a>Wartość zwrócona

Obiekt `runtime_exception`.

## <a name="dtor"></a>~ runtime_exception destruktor

Niszczy obiekt.

### <a name="syntax"></a>Składnia

```cpp
virtual ~runtime_exception() throw();
```

## <a name="get_error_code"></a>get_error_code

Zwraca kod błędu, który spowodował wyjątek.

### <a name="syntax"></a>Składnia

```cpp
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>Wartość zwrócona

WYNIK HRESULT błędu, który spowodował wyjątek.

## <a name="operator_eq"></a>operator =
  Kopiuje zawartość określonego obiektu `runtime_exception` do tego.

### <a name="syntax"></a>Składnia

```cpp
runtime_exception & operator= (    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Obiekt `runtime_exception` do skopiowania.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do tego obiektu `runtime_exception`.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
