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
ms.openlocfilehash: 02382ef4606a6e73804fcbd5ce7735ecf2f0dcc7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140046"
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList — Struktura

Reprezentuje listę uzupełniania UMS. Po zablokowaniu wątku UMS, wyznaczoną w harmonogramie kontekst planowania jest wysyłany w celu podjęcia decyzji o tym, co należy zaplanować na źródłowym głównym procesorze wirtualnym, gdy oryginalny wątek jest zablokowany. Gdy oryginalny wątek zostanie odblokowany, system operacyjny kolejkuje go do listy uzupełniania dostępnej za pomocą tego interfejsu. Harmonogram może wysyłać zapytania do listy uzupełniania w wydzielonym kontekście planowania lub innym miejscu, w którym szuka pracy.

## <a name="syntax"></a>Składnia

```cpp
struct IUMSCompletionList;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[IUMSCompletionList:: GetUnblockNotifications —](#getunblocknotifications)|Pobiera łańcuch interfejsów `IUMSUnblockNotification` reprezentujących konteksty wykonywania, których skojarzone serwery proxy wątków zostały odblokowane od czasu ostatniego wywołania tej metody.|

## <a name="remarks"></a>Uwagi

W harmonogramie należy bardzo uważnie informacje o akcjach wykonywanych po użyciu tego interfejsu do usuwania elementów z listy uzupełniania. Elementy powinny być umieszczone na liście kontekstów możliwy do uruchomienia i być ogólnie dostępne tak szybko, jak to możliwe. Jest to w pełni możliwe, że jeden z elementów usuniętych z kolejki uzyskał własność arbitralnej blokady. Harmonogram może nie wprowadzać żadnych dowolnych wywołań funkcji, które mogą blokować między wywołaniem elementu unqueueing a umieszczeniem tych elementów na liście, do której można uzyskać ogólne dostęp z poziomu harmonogramu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IUMSCompletionList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm. h

**Przestrzeń nazw:** współbieżność

## <a name="getunblocknotifications"></a>IUMSCompletionList:: GetUnblockNotifications —, Metoda

Pobiera łańcuch interfejsów `IUMSUnblockNotification` reprezentujących konteksty wykonywania, których skojarzone serwery proxy wątków zostały odblokowane od czasu ostatniego wywołania tej metody.

```cpp
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Łańcuch interfejsów `IUMSUnblockNotification`.

### <a name="remarks"></a>Uwagi

Zwrócone powiadomienia są nieprawidłowe po przeplanowaniu kontekstów wykonywania.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[IUMSScheduler, struktura](iumsscheduler-structure.md)<br/>
[IUMSUnblockNotification, struktura](iumsunblocknotification-structure.md)
