---
title: Włączanie i wyłączanie usług dla dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ef36e35234aa4878e30e70748a5b2ba2975c38dc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099735"
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>Włączanie i wyłączanie usług dla dostawcy
Usługi OLE DB mogą można włączać lub wyłączać domyślne dla wszystkich aplikacji, które uzyskują dostęp do jednego dostawcy. Jest to realizowane przez dodanie **OLEDB_SERVICES** wpisu rejestru dostawcy na CLSID z `DWORD` wartość określającą usług, aby włączyć lub wyłączyć, jak pokazano w poniższej tabeli.  
  
|Włączone usługi domyślne|Wartość — słowo kluczowe|  
|------------------------------|-------------------|  
|Wszystkie usługi (ustawienie domyślne)|0xffffffff|  
|Wszystkie z wyjątkiem puli i AutoEnlistment|0xFFFFFFFE|  
|Wszystkie z wyjątkiem kursora klienta|0xfffffffb|  
|Wszystkie z wyjątkiem puli AutoEnlistment i kursora klienta|0xfffffff0|  
|Nie usługi|0x00000000|  
|Nie agregacji wszystkich usług wyłączone|\<Brak klucza >|  
  
## <a name="see-also"></a>Zobacz też  
 [Włączanie i wyłączanie usług OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)