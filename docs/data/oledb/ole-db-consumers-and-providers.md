---
title: OLE DB konsumenci i dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, OLE DB data architecture
- OLE DB providers
- OLE DB consumers, OLE DB data architecture
- OLE DB consumers
- OLE DB, data model
ms.assetid: 886cb39d-652b-4557-93f0-4b1b0754d8bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b37a06ec89f0e2e21c4332a480e58c605f0d161f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110721"
---
# <a name="ole-db-consumers-and-providers"></a>Konsumenci i dostawcy OLE DB

Architektura OLE DB używa modelu konsumenci i dostawcy. Konsument wysyła żądania dotyczące danych. Dostawca reaguje na te żądania umieszczenia danych w formacie tabelarycznym i przywróceniem go do użytkownika. Każde wywołanie, który użytkownik może zgłaszać muszą zostać zaimplementowane w dostawcy.  
  
Z technicznego punktu widzenia zdefiniowane, odbiorcy jest każdy systemu lub aplikacji kod (niekoniecznie składnik OLE DB) uzyskuje dostęp do danych za pośrednictwem interfejsów OLE DB. Interfejsy są implementowane w dostawcy. W związku z tym Dostawca to dowolny składnik oprogramowania, który implementuje interfejsy OLE DB hermetyzują dostęp do danych i udostępnić ją do innych obiektów (oznacza to, że konsumenci).  
  
Pod względem ról użytkownik wywołuje metody dla OLE DB interfejsów; Dostawca OLE DB implementuje wymagane interfejsy OLE DB.  
  
OLE DB pozwala uniknąć warunków klienta i serwera, ponieważ te role nie zawsze mają sensu, szczególnie w sytuacji n warstwowej. Ponieważ użytkownik może być składnik na warstwy, która służy inny składnik, jej wywołania klienta składnika byłoby mylące. Ponadto dostawca czasami funkcjonuje bardziej sterownik bazy danych niż serwer.  
  
## <a name="see-also"></a>Zobacz też  

[Programowanie OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Omówienie programowania OLE DB](../../data/oledb/ole-db-programming-overview.md)