---
title: scheduler_resource_allocation_error — Klasa
ms.date: 11/04/2016
f1_keywords:
- scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::get_error_code
helpviewer_keywords:
- scheduler_resource_allocation_error class
ms.assetid: 8b40449a-7abb-4d0a-bb85-c0e9a495ae97
ms.openlocfilehash: 2955320b443fb61f26d9f07ca336a45c620e2aa9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143338"
---
# <a name="scheduler_resource_allocation_error-class"></a>scheduler_resource_allocation_error — Klasa

Ta klasa opisuje wyjątek zgłoszony z powodu niepowodzenia uzyskania zasobu krytycznego w środowisko uruchomieniowe współbieżności.

## <a name="syntax"></a>Składnia

```cpp
class scheduler_resource_allocation_error : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[scheduler_resource_allocation_error](#ctor)|Przeciążone. Konstruuje obiekt `scheduler_resource_allocation_error`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[get_error_code](#get_error_code)|Zwraca kod błędu, który spowodował wyjątek.|

## <a name="remarks"></a>Uwagi

Ten wyjątek jest zazwyczaj generowany w przypadku niepowodzenia wywołania systemu operacyjnego z środowisko uruchomieniowe współbieżności. Kod błędu, który zwykle jest zwracany z wywołania metody Win32 `GetLastError` jest konwertowany na wartość typu `HRESULT` i można go pobrać przy użyciu metody `get_error_code`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`scheduler_resource_allocation_error`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="get_error_code"></a>get_error_code

Zwraca kod błędu, który spowodował wyjątek.

```cpp
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>Wartość zwrócona

Wartość `HRESULT` błędu, który spowodował wyjątek.

## <a name="ctor"></a>scheduler_resource_allocation_error

Konstruuje obiekt `scheduler_resource_allocation_error`.

```cpp
scheduler_resource_allocation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_resource_allocation_error(
    HRESULT _Hresult) throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat o błędzie.

*_Hresult*<br/>
Wartość `HRESULT` błędu, który spowodował wyjątek.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
