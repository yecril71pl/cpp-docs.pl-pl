---
title: scheduler_worker_creation_error — Klasa
ms.date: 11/04/2016
f1_keywords:
- scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error::scheduler_worker_creation_error
helpviewer_keywords:
- scheduler_worker_creation_error class
ms.assetid: 4aec1c3e-c32a-41b2-899d-2d898f23b3c7
ms.openlocfilehash: e7f2763d7244be9e5e5b006b31b97c08e213a4f2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142766"
---
# <a name="scheduler_worker_creation_error-class"></a>scheduler_worker_creation_error — Klasa

Ta klasa opisuje wyjątek zgłoszony z powodu błędu tworzenia kontekstu wykonywania procesu roboczego w środowisko uruchomieniowe współbieżności.

## <a name="syntax"></a>Składnia

```cpp
class scheduler_worker_creation_error : public scheduler_resource_allocation_error;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[scheduler_worker_creation_error](#ctor)|Przeciążone. Konstruuje obiekt `scheduler_worker_creation_error`.|

## <a name="remarks"></a>Uwagi

Ten wyjątek jest zazwyczaj generowany, gdy wywołanie systemu operacyjnego w celu utworzenia kontekstów wykonywania z poziomu środowisko uruchomieniowe współbieżności zakończy się niepowodzeniem. Konteksty wykonywania to wątki wykonujące zadania w środowisko uruchomieniowe współbieżności. Kod błędu, który zwykle jest zwracany z wywołania metody Win32 `GetLastError` jest konwertowany na wartość typu `HRESULT` i można go pobrać przy użyciu metody klasy bazowej `get_error_code`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)

`scheduler_worker_creation_error`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>scheduler_worker_creation_error

Konstruuje obiekt `scheduler_worker_creation_error`.

```cpp
scheduler_worker_creation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_worker_creation_error(
    HRESULT _Hresult) throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat o błędzie.

*_Hresult*<br/>
Wartość `HRESULT` błędu, który spowodował wyjątek.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
