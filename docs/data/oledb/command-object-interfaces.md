---
title: Interfejsy obiektu polecenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9c597cc30e23ffce2787eac6c13f6ba8c53f96c1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="command-object-interfaces"></a>Interfejsy obiektu polecenia
Obiekt polecenia używa `IAccessor` interfejs, aby określić powiązania parametrów. Wywołania konsumenta `IAccessor::CreateAccessor`, przekazanie jej przez tablicę `DBBINDING` struktury. `DBBINDING` zawiera informacje dotyczące powiązania kolumny (na przykład typ i długości). Dostawca otrzymuje struktur i określa, jak powinny być przesyłane dane i czy konwersje są niezbędne.  
  
 `ICommandText` Interfejsu pozwala określić w poleceniu tekstowym. `ICommandProperties` Interfejs obsługuje wszystkie właściwości polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)