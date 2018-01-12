---
title: "Włączanie i wyłączanie usług dla dostawcy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dc6b3d7cc8e80eaa24c2e2dd9b4e23e79dfb09f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>Włączanie i wyłączanie usług dla dostawcy
Usługi OLE DB mogą można włączać lub wyłączać domyślne dla wszystkich aplikacji, które uzyskują dostęp do jednego dostawcy. Jest to realizowane przez dodanie **OLEDB_SERVICES** wpisu rejestru dostawcy na CLSID z `DWORD` wartość określającą usług, aby włączyć lub wyłączyć, jak pokazano w poniższej tabeli.  
  
|Włączone usługi domyślne|Wartość — słowo kluczowe|  
|------------------------------|-------------------|  
|Wszystkie usługi (ustawienie domyślne)|0xFFFFFFFF|  
|Wszystkie z wyjątkiem puli i AutoEnlistment|0xFFFFFFFE|  
|Wszystkie z wyjątkiem kursora klienta|0xfffffffb|  
|Wszystkie z wyjątkiem puli AutoEnlistment i kursora klienta|0xfffffff0|  
|Nie usługi|0x00000000|  
|Nie agregacji wszystkich usług wyłączone|\<Brak klucza >|  
  
## <a name="see-also"></a>Zobacz też  
 [Włączanie i wyłączanie usług OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)