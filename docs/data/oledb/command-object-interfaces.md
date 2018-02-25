---
title: Interfejsy obiektu polecenia | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a26004edcd4b1e32bb7dd960ce927786296ef44b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="command-object-interfaces"></a>Interfejsy obiektu polecenia
Obiekt polecenia używa `IAccessor` interfejs, aby określić powiązania parametrów. Wywołania konsumenta `IAccessor::CreateAccessor`, przekazanie jej przez tablicę `DBBINDING` struktury. `DBBINDING` zawiera informacje dotyczące powiązania kolumny (na przykład typ i długości). Dostawca otrzymuje struktur i określa, jak powinny być przesyłane dane i czy konwersje są niezbędne.  
  
 `ICommandText` Interfejsu pozwala określić w poleceniu tekstowym. `ICommandProperties` Interfejs obsługuje wszystkie właściwości polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)