---
title: Iumsunblocknotification — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetContext
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetNextUnblockNotification
dev_langs:
- C++
helpviewer_keywords:
- IUMSUnblockNotification structure
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 63dcd78af0804a6921d34a35611591f044c2633f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438031"
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

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[IUMSScheduler, struktura](iumsscheduler-structure.md)<br/>
[IUMSCompletionList, struktura](iumscompletionlist-structure.md)
