---
title: Tworzenie prostego dostawcy tylko do odczytu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6b5f840a6f401d8eb1bcca598d86622deb8f86cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-simple-read-only-provider"></a>Tworzenie prostego dostawcy tylko do odczytu
Po utworzeniu dostawcy OLE DB przy użyciu Kreator projektu ATL i ATL OLE DB Provider kreatora możesz dodać inne funkcje, które mają być obsługiwane. Uruchom projektowania, sprawdzając jakiego rodzaju dane będą wysyłane do użytkownika i pod jakimi warunkami dostawcy. Jest to szczególnie ważne określić, czy wymagana jest obsługa polecenia, transakcje i inne opcjonalne obiekty. Na początku dobry projekt przyspieszy wdrażania i testowania.  
  
 Przykład został przedstawiony w dwóch częściach:  
  
-   W pierwszej części pokazano sposób [Tworzenie prostego dostawcy tylko do odczytu](../../data/oledb/implementing-the-simple-read-only-provider.md) które odczytuje pary ciągów.  
  
-   W drugiej części pokazano sposób [ułatwienia prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md) przez dodanie `IRowsetLocate` interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)