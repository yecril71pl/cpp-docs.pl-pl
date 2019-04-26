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
ms.openlocfilehash: bdf083e2ad418269e49e53dc164f2a60f693d5d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180222"
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification — Struktura

Reprezentuje powiadomienie z Menedżera zasobów, serwer proxy wątku, zablokowany, co wyzwalane powrót do harmonogramu wyznaczony planowania kontekst ma odblokowany i jest gotowy do zaplanowania. Ten interfejs jest nieprawidłowy, gdy zwróciło kontekstu wykonywania skojarzony wątek serwera proxy, `GetContext` zmiany w harmonogramie metody.

## <a name="syntax"></a>Składnia

```
struct IUMSUnblockNotification;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IUMSUnblockNotification::GetContext](#getcontext)|Zwraca `IExecutionContext` interfejs dla kontekstu wykonywania skojarzony z serwerem proxy wątku, który został odblokowany. Po powrocie z tej metody i podstawowych kontekstu wykonywania zaplanowano poprzez wywołanie `IThreadProxy::SwitchTo` metody tego interfejsu nie jest już prawidłowy.|
|[Iumsunblocknotification::getnextunblocknotification —](#getnextunblocknotification)|Zwraca następne `IUMSUnblockNotification` interfejsu w łańcuchu zwrócona przez metodę `IUMSCompletionList::GetUnblockNotifications`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IUMSUnblockNotification`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Namespace:** współbieżności

##  <a name="getcontext"></a>  Iumsunblocknotification::getcontext — metoda

Zwraca `IExecutionContext` interfejs dla kontekstu wykonywania skojarzony z serwerem proxy wątku, który został odblokowany. Po powrocie z tej metody i podstawowych kontekstu wykonywania zaplanowano poprzez wywołanie `IThreadProxy::SwitchTo` metody tego interfejsu nie jest już prawidłowy.

```
virtual IExecutionContext* GetContext() = 0;
```

### <a name="return-value"></a>Wartość zwracana

`IExecutionContext` Interfejs dla kontekstu wykonywania, aby serwer proxy wątku, który został odblokowany.

##  <a name="getnextunblocknotification"></a>  Iumsunblocknotification::getnextunblocknotification — metoda

Zwraca następne `IUMSUnblockNotification` interfejsu w łańcuchu zwrócona przez metodę `IUMSCompletionList::GetUnblockNotifications`.

```
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Następne `IUMSUnblockNotification` interfejsu w łańcuchu zwrócona przez metodę `IUMSCompletionList::GetUnblockNotifications`.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[IUMSScheduler, struktura](iumsscheduler-structure.md)<br/>
[IUMSCompletionList, struktura](iumscompletionlist-structure.md)
