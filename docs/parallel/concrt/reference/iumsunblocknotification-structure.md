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
ms.openlocfilehash: d4fd95b1f11ed6edac26cb03e41e8b650acfafa3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139984"
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification — Struktura

Reprezentuje powiadomienie z Menedżer zasobów, że serwer proxy wątku, który został zablokowany i wyzwolony powrót do wyznaczonego kontekstu planowania harmonogramu został odblokowany i jest gotowy do zaplanowania. Ten interfejs jest nieprawidłowy, gdy kontekst wykonywania skojarzony z serwerem proxy wątku zwrócony przez metodę `GetContext` jest ponownie zaplanowany.

## <a name="syntax"></a>Składnia

```cpp
struct IUMSUnblockNotification;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[IUMSUnblockNotification:: GetContext](#getcontext)|Zwraca interfejs `IExecutionContext` dla kontekstu wykonywania skojarzonego z serwerem proxy wątku, który został odblokowany. Gdy ta metoda zostanie zwrócona, a podstawowy kontekst wykonywania został ponownie zaplanowany za pośrednictwem wywołania metody `IThreadProxy::SwitchTo`, ten interfejs nie jest już prawidłowy.|
|[IUMSUnblockNotification:: GetNextUnblockNotification —](#getnextunblocknotification)|Zwraca następny interfejs `IUMSUnblockNotification` w łańcuchu zwróconym z metody `IUMSCompletionList::GetUnblockNotifications`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IUMSUnblockNotification`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm. h

**Przestrzeń nazw:** współbieżność

## <a name="getcontext"></a>IUMSUnblockNotification:: GetContext — Metoda

Zwraca interfejs `IExecutionContext` dla kontekstu wykonywania skojarzonego z serwerem proxy wątku, który został odblokowany. Gdy ta metoda zostanie zwrócona, a podstawowy kontekst wykonywania został ponownie zaplanowany za pośrednictwem wywołania metody `IThreadProxy::SwitchTo`, ten interfejs nie jest już prawidłowy.

```cpp
virtual IExecutionContext* GetContext() = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Interfejs `IExecutionContext` dla kontekstu wykonywania do serwera proxy wątku, który został odblokowany.

## <a name="getnextunblocknotification"></a>IUMSUnblockNotification:: GetNextUnblockNotification —, Metoda

Zwraca następny interfejs `IUMSUnblockNotification` w łańcuchu zwróconym z metody `IUMSCompletionList::GetUnblockNotifications`.

```cpp
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Następny `IUMSUnblockNotification` interfejs w łańcuchu zwróconym z metody `IUMSCompletionList::GetUnblockNotifications`.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[IUMSScheduler, struktura](iumsscheduler-structure.md)<br/>
[IUMSCompletionList, struktura](iumscompletionlist-structure.md)
