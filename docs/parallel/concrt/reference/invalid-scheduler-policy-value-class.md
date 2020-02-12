---
title: invalid_scheduler_policy_value — Klasa
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_value
helpviewer_keywords:
- invalid_scheduler_policy_value class
ms.assetid: 8c533e3f-2774-4192-8616-b2313b859bf7
ms.openlocfilehash: 6a66b2b303a4b3b0cb8c2c7a3c515ac8cd1b33a0
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142990"
---
# <a name="invalid_scheduler_policy_value-class"></a>invalid_scheduler_policy_value — Klasa

Ta klasa opisuje wyjątek zgłoszony, gdy klucz zasad obiektu `SchedulerPolicy` jest ustawiony na nieprawidłową wartość dla tego klucza.

## <a name="syntax"></a>Składnia

```cpp
class invalid_scheduler_policy_value : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[invalid_scheduler_policy_value](invalid-scheduler-policy-thread-specification-class.md#ctor|Przeciążone. Konstruuje obiekt `invalid_scheduler_policy_value`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`invalid_scheduler_policy_value`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>invalid_scheduler_policy_value

Konstruuje obiekt `invalid_scheduler_policy_value`.

```cpp
explicit _CRTIMP invalid_scheduler_policy_value(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_value() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[SchedulerPolicy, klasa](schedulerpolicy-class.md)
