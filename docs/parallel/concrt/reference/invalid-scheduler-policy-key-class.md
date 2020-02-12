---
title: invalid_scheduler_policy_key — Klasa
ms.date: 11/04/2016
f1_keywords:
- invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key::invalid_scheduler_policy_key
helpviewer_keywords:
- invalid_scheduler_policy_key class
ms.assetid: 6a7c42fe-9bc4-4a02-bebb-99fe9ef9817d
ms.openlocfilehash: 60d5a57ff9cb33a3d522c14514f5107844216852
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143027"
---
# <a name="invalid_scheduler_policy_key-class"></a>invalid_scheduler_policy_key — Klasa

Ta klasa opisuje wyjątek zgłoszony, gdy nieprawidłowy lub nieznany klucz jest przesyłany do konstruktora obiektu `SchedulerPolicy` lub metoda `SetPolicyValue` obiektu `SchedulerPolicy` jest przenoszona jako klucz, który należy zmienić przy użyciu innych metod, takich jak Metoda `SetConcurrencyLimits`.

## <a name="syntax"></a>Składnia

```cpp
class invalid_scheduler_policy_key : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[invalid_scheduler_policy_key](#ctor)|Przeciążone. Konstruuje obiekt `invalid_scheduler_policy_key`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`invalid_scheduler_policy_key`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>invalid_scheduler_policy_key

Konstruuje obiekt `invalid_scheduler_policy_key`.

```cpp
explicit _CRTIMP invalid_scheduler_policy_key(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_key() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[SchedulerPolicy, klasa](schedulerpolicy-class.md)
