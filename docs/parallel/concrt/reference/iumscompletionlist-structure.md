---
title: Iumscompletionlist — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList::IUMSCompletionList::GetUnblockNotifications
dev_langs:
- C++
helpviewer_keywords:
- IUMSCompletionList structure
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6ee957355510a2f62f5317d330403dc246ee8f2e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687078"
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList — Struktura
Reprezentuje listę uzupełniania UMS. Podczas planowania wyznaczony harmonogramu UMS wątku bloków, aby podjąć decyzję dotyczącą tego, jaki można zaplanować na komputerze podstawowym głównego procesora wirtualnego podczas oryginalnego wątek jest zablokowany wywoływane jest kontekstu. Gdy odblokowuje oryginalnego wątku, system operacyjny kolejek do listy zakończenia, która jest dostępna za pośrednictwem tego interfejsu. Harmonogram można badać listy uzupełniania na wyznaczonych kontekstu planowania lub w innym miejscu przeszukiwanych do pracy.  
  
## <a name="syntax"></a>Składnia  
  
```
struct IUMSCompletionList;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IUMSCompletionList::GetUnblockNotifications](#getunblocknotifications)|Pobiera łańcuch `IUMSUnblockNotification` interfejsy reprezentujący kontekstów wykonywania, których skojarzone wątku proxy ma odblokowany od czasu ostatniego ta metoda została wywołana.|  
  
## <a name="remarks"></a>Uwagi  
 Harmonogramu musi być bardzo ostrożność, jakie akcje wykonywane po przy użyciu tego interfejsu do usuwania z kolejki elementów na liście uzupełniania. Elementy powinny być umieszczane na harmonogram listę konteksty do uruchomienia i być ogólnie dostępne tak szybko, jak to możliwe. Jest całkowicie możliwe, że jeden z elementów dequeued została podana własność dowolnego blokady. Planista wprowadzić nie wywołania dowolnych funkcji, które mogą zablokować między wywołania do usuwania z kolejki elementów i rozmieszczenie tych elementów na liście, ogólnie dostępny od w ramach harmonogramu zadań.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IUMSCompletionList`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrtrm.h  
  
 **Namespace:** współbieżności  
  
##  <a name="getunblocknotifications"></a>  IUMSCompletionList::GetUnblockNotifications — metoda  
 Pobiera łańcuch `IUMSUnblockNotification` interfejsy reprezentujący kontekstów wykonywania, których skojarzone wątku proxy ma odblokowany od czasu ostatniego ta metoda została wywołana.  
  
```
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Łańcuch `IUMSUnblockNotification` interfejsów.  
  
### <a name="remarks"></a>Uwagi  
 Zwracane powiadomień są nieprawidłowe po kontekstów wykonywania są zaplanowane ponownie.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Struktura IUMSScheduler](iumsscheduler-structure.md)   
 [IUMSUnblockNotification, struktura](iumsunblocknotification-structure.md)
