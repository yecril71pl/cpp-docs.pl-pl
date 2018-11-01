---
title: invalid_scheduler_policy_thread_specification — Klasa
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_thread_specification
helpviewer_keywords:
- invalid_scheduler_policy_thread_specification class
ms.assetid: 2d0fafb2-18f8-4284-8040-3db640d33303
ms.openlocfilehash: b74439d1fca9ea990258ca5f7e36c865a2c49455
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491341"
---
# <a name="invalidschedulerpolicythreadspecification-class"></a>invalid_scheduler_policy_thread_specification — Klasa

Ta klasa opisuje wyjątek generowany, gdy podejmowana jest próba można ustawić limity współbieżności `SchedulerPolicy` obiektu taki sposób, że wartość `MinConcurrency` klucz jest mniejsza niż wartość `MaxConcurrency` klucza.

## <a name="syntax"></a>Składnia

```
class invalid_scheduler_policy_thread_specification : public std::exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-value-class.md#ctor|Przeciążone. Konstruuje `invalid_scheduler_policy_value` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`invalid_scheduler_policy_thread_specification`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności
##  <a name="ctor"></a> invalid_scheduler_policy_thread_specification

Konstruuje `invalid_scheduler_policy_value` obiektu.

```
explicit _CRTIMP invalid_scheduler_policy_thread_specification(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_thread_specification() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat dotyczący błędu.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[SchedulerPolicy, klasa](schedulerpolicy-class.md)
