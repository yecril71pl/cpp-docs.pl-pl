---
title: IUMSCompletionList — Struktura
ms.date: 11/04/2016
f1_keywords:
- IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList::IUMSCompletionList::GetUnblockNotifications
helpviewer_keywords:
- IUMSCompletionList structure
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
ms.openlocfilehash: c388cc98aedbd35b2d0e00a4653a85a47abcb838
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368119"
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList — Struktura

Reprezentuje listę uzupełnień UMS. Gdy blokuje wątek UMS, kontekst planowania wyznaczonego harmonogramu jest wywoływany w celu podjęcia decyzji, co zaplanować w katalogu głównym procesora wirtualnego, gdy oryginalny wątek jest zablokowany. Gdy oryginalny wątek odblokowuje, system operacyjny kolejkuje go do listy zakończenia, która jest dostępna za pośrednictwem tego interfejsu. Harmonogram może zbadać listę uzupełnień w wyznaczonym kontekście planowania lub w dowolnym innym miejscu, wyszukuje pracę.

## <a name="syntax"></a>Składnia

```cpp
struct IUMSCompletionList;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Lista IUMSCompletion::GetUnblockNotifications](#getunblocknotifications)|Pobiera łańcuch interfejsów `IUMSUnblockNotification` reprezentujących konteksty wykonywania, których skojarzone serwery proxy wątku zostały odblokowane od czasu ostatniego wywołania tej metody.|

## <a name="remarks"></a>Uwagi

Harmonogram musi być niezwykle ostrożny, jakie akcje są wykonywane po użyciu tego interfejsu do usuwania elementów z listy zakończenia. Elementy powinny być umieszczone na liście harmonogramu kontekstów runnable i być ogólnie dostępne tak szybko, jak to możliwe. Jest całkowicie możliwe, że jeden z de-ekued elementów został przekazany własności dowolnego zamka. Harmonogram nie można wykonywać żadnych wywołań funkcji dowolnego, które mogą blokować między wywołaniem do usunięcia zowolenia elementów i umieszczenie tych elementów na liście, które są ogólnie dostępne z poziomu harmonogramu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IUMSCompletionList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Przestrzeń nazw:** współbieżność

## <a name="iumscompletionlistgetunblocknotifications-method"></a><a name="getunblocknotifications"></a>IUMSCompletionList::Metoda GetUnblockNotifications

Pobiera łańcuch interfejsów `IUMSUnblockNotification` reprezentujących konteksty wykonywania, których skojarzone serwery proxy wątku zostały odblokowane od czasu ostatniego wywołania tej metody.

```cpp
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Łańcuch interfejsów. `IUMSUnblockNotification`

### <a name="remarks"></a>Uwagi

Zwrócone powiadomienia są nieprawidłowe po przełożonym kontekstów wykonywania.

## <a name="see-also"></a>Zobacz też

[współbieżność Obszar nazw](concurrency-namespace.md)<br/>
[IUMSScheduler, struktura](iumsscheduler-structure.md)<br/>
[IUMSUnblockNotification, struktura](iumsunblocknotification-structure.md)
