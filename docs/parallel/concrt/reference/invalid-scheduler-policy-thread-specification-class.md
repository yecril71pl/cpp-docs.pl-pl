---
title: invalid_scheduler_policy_thread_specification — Klasa
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_thread_specification
helpviewer_keywords:
- invalid_scheduler_policy_thread_specification class
ms.assetid: 2d0fafb2-18f8-4284-8040-3db640d33303
ms.openlocfilehash: b6c2fd853ae19c48ae04d6601eb47e5afcb71944
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143033"
---
# <a name="invalid_scheduler_policy_thread_specification-class"></a>invalid_scheduler_policy_thread_specification — Klasa

Ta klasa opisuje wyjątek zgłoszony, gdy podejmowana jest próba ustawienia limitów współbieżności obiektu `SchedulerPolicy` w taki sposób, że wartość klucza `MinConcurrency` jest mniejsza niż wartość klucza `MaxConcurrency`.

## <a name="syntax"></a>Składnia

```cpp
class invalid_scheduler_policy_thread_specification : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-value-class.md#ctor|Przeciążone. Konstruuje obiekt `invalid_scheduler_policy_value`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`invalid_scheduler_policy_thread_specification`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>invalid_scheduler_policy_thread_specification

Konstruuje obiekt `invalid_scheduler_policy_value`.

```cpp
explicit _CRTIMP invalid_scheduler_policy_thread_specification(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_thread_specification() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[SchedulerPolicy, klasa](schedulerpolicy-class.md)
