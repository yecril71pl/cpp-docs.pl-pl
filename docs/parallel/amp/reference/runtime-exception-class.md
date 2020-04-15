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
ms.openlocfilehash: ff54357055d373db98f469b071edc75fce75e0b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336796"
---
# <a name="runtime_exception-class"></a>runtime_exception — Klasa

Typ podstawowy dla wyjątków w bibliotece C++ Accelerated Massive Parallelism (AMP).

### <a name="syntax"></a>Składnia

```cpp
class runtime_exception : public std::exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[konstruktor runtime_exception](#ctor)|Inicjuje nowe wystąpienie klasy `runtime_exception`.|
|[~runtime_exception Destruktor](#dtor)|Niszczy `runtime_exception` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get_error_code](#get_error_code)|Zwraca kod błędu, który spowodował wyjątek.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator=](#operator_eq)|Kopiuje zawartość określonego `runtime_exception` obiektu do tego obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`runtime_exception`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt.h

**Obszar nazw:** Współbieżności

## <a name="runtime_exception-constructor"></a><a name="ctor"></a>konstruktor runtime_exception

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
HRESULT błędu, który spowodował wyjątek.

*_Other*<br/>
Obiekt `runtime_exception` do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Obiekt `runtime_exception`.

## <a name="runtime_exception-destructor"></a><a name="dtor"></a>~runtime_exception Destruktor

Niszczy obiekt.

### <a name="syntax"></a>Składnia

```cpp
virtual ~runtime_exception() throw();
```

## <a name="get_error_code"></a><a name="get_error_code"></a>get_error_code

Zwraca kod błędu, który spowodował wyjątek.

### <a name="syntax"></a>Składnia

```cpp
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>Wartość zwracana

HRESULT błędu, który spowodował wyjątek.

## <a name="operator"></a><a name="operator_eq"></a>operator=

Kopiuje zawartość określonego `runtime_exception` obiektu do tego obiektu.

### <a name="syntax"></a>Składnia

```cpp
runtime_exception & operator= (    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Obiekt `runtime_exception` do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `runtime_exception` tego obiektu.

## <a name="see-also"></a>Zobacz też

[Obszar nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
