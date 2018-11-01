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
ms.openlocfilehash: ec3c38ee609dfa7aec8d688269f1183d307be5b2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438210"
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList — Struktura

Reprezentuje listę uzupełniania UMS. Podczas planowania wyznaczony harmonogramu UMS bloki wątku, kontekst jest wywoływane w celu podjęcia decyzji o tym, co należy zaplanować na podstawowego procesora wirtualnego katalogu głównego, gdy oryginalny wątek jest zablokowany. Gdy odblokowuje wątek oryginalnej, system operacyjny umieszcza je w kolejce do listy uzupełniania, który jest dostępny za pośrednictwem tego interfejsu. Harmonogram można badać na liście uzupełniania w wyznaczonym Kontekst harmonogramu lub w innym miejscu, przeszukiwanych do pracy.

## <a name="syntax"></a>Składnia

```
struct IUMSCompletionList;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Iumscompletionlist::getunblocknotifications —](#getunblocknotifications)|Pobiera łańcuch `IUMSUnblockNotification` interfejsów reprezentujący kontekstów wykonanie, którego skojarzonego wątku proxy ma odblokowany od czasu ostatniego ta metoda została wywołana.|

## <a name="remarks"></a>Uwagi

Harmonogramu musi być bardzo ostrożność, jakie działania są wykonane po wykorzystujących kolejki elementów z listy uzupełniania w tym interfejsie. Elementy powinny być umieszczane na harmonogram listę konteksty możliwy do uruchomienia i być możliwie jak ogólnie dostępne. Jest całkowicie możliwe, że jeden z elementów dequeued nadano własność dowolnego blokady. Harmonogram można wprowadzać nie wywołania dowolnych funkcji, które mogą blokować między wywołanie do usuwania z kolejki elementów i rozmieszczenie tych elementów na liście, które są ogólnie dostępne z w obrębie harmonogramu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IUMSCompletionList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Namespace:** współbieżności

##  <a name="getunblocknotifications"></a>  Iumscompletionlist::getunblocknotifications — metoda

Pobiera łańcuch `IUMSUnblockNotification` interfejsów reprezentujący kontekstów wykonanie, którego skojarzonego wątku proxy ma odblokowany od czasu ostatniego ta metoda została wywołana.

```
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Łańcuch `IUMSUnblockNotification` interfejsów.

### <a name="remarks"></a>Uwagi

Zwrócone powiadomień są nieprawidłowe, po kontekstami wykonywania są zaplanowane ponownie.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[IUMSScheduler, struktura](iumsscheduler-structure.md)<br/>
[IUMSUnblockNotification, struktura](iumsunblocknotification-structure.md)
