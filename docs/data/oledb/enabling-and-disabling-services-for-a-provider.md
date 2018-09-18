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
ms.openlocfilehash: a5db612c836e4b902e7cad83017661246f4b649e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079391"
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>Włączanie i wyłączanie usług dla dostawcy

Poszczególne usługi OLE DB można włączać lub wyłączać domyślnie dla wszystkich aplikacji uzyskujących dostęp do jednego dostawcy. Jest to realizowane przez dodanie wpisu rejestru OLEDB_SERVICES CLSID dostawcy z `DWORD` wartość określającą usług, aby włączyć lub wyłączyć, jak pokazano w poniższej tabeli.  
  
|Włączone usługi domyślne|Wartość — słowo kluczowe|  
|------------------------------|-------------------|  
|Wszystkie usługi (ustawienie domyślne)|0xffffffff|  
|Wszystkie regiony z wyjątkiem puli i AutoEnlistment|0xFFFFFFFE|  
|Wszystkie regiony z wyjątkiem kursor kliencki|0xfffffffb|  
|Wszystkie z wyjątkiem buforowanie AutoEnlistment i kursor kliencki|0xfffffff0|  
|Brak usług|0x00000000|  
|Brak agregacji wszystkie usługi wyłączone|\<Brak klucza >|  
  
## <a name="see-also"></a>Zobacz też  

[Włączanie i wyłączanie usług OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)