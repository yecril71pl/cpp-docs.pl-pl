---
title: OLE DB konsumenci i dostawcy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB providers, OLE DB data architecture
- OLE DB providers
- OLE DB consumers, OLE DB data architecture
- OLE DB consumers
- OLE DB, data model
ms.assetid: 886cb39d-652b-4557-93f0-4b1b0754d8bc
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4f0a0ee77b13d6e5231d002cb444ac5a7847f3d6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ole-db-consumers-and-providers"></a>Konsumenci i dostawcy OLE DB
Architektura OLE DB używa modelu konsumenci i dostawcy. Konsument zgłasza żądania dotyczące danych. Dostawca reaguje na te żądania wprowadzania danych w formacie tabelarycznym i przywróceniem go do użytkownika. Żadnym wywołaniu, które może sprawić, że użytkownik musi być implementowana w dostawcy.  
  
 Technicznie zdefiniowane, klient jest żadnych systemu lub aplikacji kodu (niekoniecznie składnik OLE DB) uzyskuje dostęp do danych za pośrednictwem interfejsów OLE DB. Interfejsy są implementowane u dostawcy. W związku z tym dostawcą jest każdego składnika oprogramowania, który implementuje interfejsy OLE DB do reprezentują dostęp do danych i pozostawić ją do innych obiektów (czyli konsumentów).  
  
 Pod względem ról klient wywołuje metody na interfejsy OLE DB; Dostawca OLE DB implementuje wymaganych interfejsów OLE DB.  
  
 OLE DB pozwala uniknąć warunków klienta i serwera, ponieważ te role nie zawsze mają sensu, szczególnie w sytuacjach n warstwowa. Ponieważ klient może być na warstwę, która służy inny składnik składnik, celu wywołania go klienta składnika będzie trudne. Ponadto dostawcę czasami działa bardziej jak sterownik bazy danych niż serwer.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie OLE DB](../../data/oledb/ole-db-programming.md)   
 [Omówienie programowania OLE DB](../../data/oledb/ole-db-programming-overview.md)