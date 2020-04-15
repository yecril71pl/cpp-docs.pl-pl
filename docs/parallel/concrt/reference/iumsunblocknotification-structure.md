---
title: IUMSUnblockNotification — Struktura
ms.date: 11/04/2016
f1_keywords:
- IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetContext
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetNextUnblockNotification
helpviewer_keywords:
- IUMSUnblockNotification structure
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
ms.openlocfilehash: 0b88ddd4184e982a5e07c536efc301eaa16f4a41
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368072"
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification — Struktura

Reprezentuje powiadomienie z Menedżera zasobów, że serwer proxy wątku, który zablokował i wyzwolił powrót do wyznaczonego kontekstu planowania harmonogramu, odblokował się i jest gotowy do zaplanowania. Ten interfejs jest nieprawidłowy, gdy kontekst wykonywania skojarzonego `GetContext` serwera proxy wątku, zwrócony z metody, jest przełożony.

## <a name="syntax"></a>Składnia

```cpp
struct IUMSUnblockNotification;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IUMSUnblockNotification::GetContext](#getcontext)|Zwraca `IExecutionContext` interfejs dla kontekstu wykonywania skojarzonego z serwerem proxy wątku, który został odblokowany. Gdy ta metoda zwraca i kontekst wykonywania podstawowej został przełożony `IThreadProxy::SwitchTo` za pośrednictwem wywołania metody, ten interfejs nie jest już prawidłowy.|
|[IUMSUnblockNotification::GetNextUnblockNotification IUMSUnblockNotification ::GetNextUnblockNotification IUMSUnblockNotification::GetNextUnblockNotification IUM](#getnextunblocknotification)|Zwraca następny `IUMSUnblockNotification` interfejs w łańcuchu `IUMSCompletionList::GetUnblockNotifications`zwrócony z metody .|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IUMSUnblockNotification`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Przestrzeń nazw:** współbieżność

## <a name="iumsunblocknotificationgetcontext-method"></a><a name="getcontext"></a>IUMSUnblockNotification::Metoda GetContext

Zwraca `IExecutionContext` interfejs dla kontekstu wykonywania skojarzonego z serwerem proxy wątku, który został odblokowany. Gdy ta metoda zwraca i kontekst wykonywania podstawowej został przełożony `IThreadProxy::SwitchTo` za pośrednictwem wywołania metody, ten interfejs nie jest już prawidłowy.

```cpp
virtual IExecutionContext* GetContext() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Interfejs `IExecutionContext` kontekstu wykonywania do serwera proxy wątku, który został odblokowany.

## <a name="iumsunblocknotificationgetnextunblocknotification-method"></a><a name="getnextunblocknotification"></a>IUMSUnblockNotification::GetNextUnblockNotification Metoda

Zwraca następny `IUMSUnblockNotification` interfejs w łańcuchu `IUMSCompletionList::GetUnblockNotifications`zwrócony z metody .

```cpp
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Następny `IUMSUnblockNotification` interfejs w łańcuchu zwrócił `IUMSCompletionList::GetUnblockNotifications`z metody .

## <a name="see-also"></a>Zobacz też

[współbieżność Obszar nazw](concurrency-namespace.md)<br/>
[IUMSScheduler, struktura](iumsscheduler-structure.md)<br/>
[IUMSCompletionList — Struktura](iumscompletionlist-structure.md)
