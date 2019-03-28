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
ms.openlocfilehash: 024ede0f05dfd646bcebe7acd2cfb86b5c54f6d1
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565496"
---
# <a name="runtimeexception-class"></a>runtime_exception — Klasa

Typ podstawowy dla wyjątków w bibliotece C++ Accelerated Massive Parallelism (AMP).

### <a name="syntax"></a>Składnia

```
class runtime_exception : public std::exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[runtime_exception — Konstruktor](#ctor)|Inicjuje nowe wystąpienie klasy `runtime_exception` klasy.|
|[~ runtime_exception — destruktor](#dtor)|Niszczy `runtime_exception` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get_error_code](#get_error_code)|Zwraca kod błędu, który spowodował wyjątek.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator=](#operator_eq)|Kopiuje zawartość określonego `runtime_exception` obiektu do wskazanego.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`runtime_exception`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt.h

**Namespace:** Współbieżność

## <a name="ctor"></a>  runtime_exception — Konstruktor

Inicjuje nowe wystąpienie klasy.

### <a name="syntax"></a>Składnia

```
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

*_Inne*<br/>
`runtime_exception` Obiektu do skopiowania.

### <a name="return-value"></a>Wartość zwracana

`runtime_exception` Obiektu.

## <a name="dtor"></a>  ~ runtime_exception — destruktor

Niszczy obiekt.

### <a name="syntax"></a>Składnia

```
virtual ~runtime_exception() throw();
```

## <a name="geterrorcode"></a>get_error_code

Zwraca kod błędu, który spowodował wyjątek.

### <a name="syntax"></a>Składnia

```
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>Wartość zwracana

HRESULT błędu, który spowodował wyjątek.

## <a name="operator_eq"></a>  operator =
  Kopiuje zawartość określonego `runtime_exception` obiektu do wskazanego.

### <a name="syntax"></a>Składnia

```
runtime_exception & operator= (    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
`runtime_exception` Obiektu do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `runtime_exception` obiektu.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
