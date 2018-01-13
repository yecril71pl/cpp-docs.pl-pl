---
title: Interfejsy obiektu polecenia | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3d83f0a14562985386f0f1f75cfcd99518fea6f5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="command-object-interfaces"></a>Interfejsy obiektu polecenia
Obiekt polecenia używa `IAccessor` interfejs, aby określić powiązania parametrów. Wywołania konsumenta `IAccessor::CreateAccessor`, przekazanie jej przez tablicę `DBBINDING` struktury. `DBBINDING`zawiera informacje dotyczące powiązania kolumny (na przykład typ i długości). Dostawca otrzymuje struktur i określa, jak powinny być przesyłane dane i czy konwersje są niezbędne.  
  
 `ICommandText` Interfejsu pozwala określić w poleceniu tekstowym. `ICommandProperties` Interfejs obsługuje wszystkie właściwości polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)