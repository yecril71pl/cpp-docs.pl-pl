---
title: invalid_operation — Klasa
ms.date: 11/04/2016
f1_keywords:
- invalid_operation
- CONCRT/concurrency::invalid_operation
- CONCRT/concurrency::invalid_operation::invalid_operation
helpviewer_keywords:
- invalid_operation class
ms.assetid: 26ba07dc-fcdf-44cb-b748-a31d35205b52
ms.openlocfilehash: e17d530569d16ba0084a58bf0be00d4a8423b7f6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140879"
---
# <a name="invalid_operation-class"></a>invalid_operation — Klasa

Ta klasa opisuje wyjątek zgłoszony w przypadku wykonania nieprawidłowej operacji, która nie jest dokładniej opisana przez inny typ wyjątku zgłoszony przez środowisko uruchomieniowe współbieżności.

## <a name="syntax"></a>Składnia

```cpp
class invalid_operation : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[invalid_operation](#ctor)|Przeciążone. Konstruuje obiekt `invalid_operation`.|

## <a name="remarks"></a>Uwagi

Różne metody, które zgłaszają ten wyjątek, będą na ogół udokumentowane pod kątem tego, jakie okoliczności ich wygenerują.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`invalid_operation`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>invalid_operation

Konstruuje obiekt `invalid_operation`.

```cpp
explicit _CRTIMP invalid_operation(_In_z_ const char* _Message) throw();

invalid_operation() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
