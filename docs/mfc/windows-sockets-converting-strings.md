---
title: "Windows Sockets: Konwertowanie ciągów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows Sockets [MFC], multibyte character string conversion
- sockets [MFC], multibyte character string conversion issues
- string conversion, multibyte character strings
ms.assetid: 9df522b5-6b23-41e0-bb96-e4e623baf141
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4b0b66cb83dc13f74e5417cab7f8cec0fe65b73a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="windows-sockets-converting-strings"></a>Windows Sockets: konwertowanie ciągów
W tym artykule i dwa artykuły pomocnika opisano kilka problemów w programowaniu Windows Sockets. W tym artykule omówiono Konwertowanie ciągów. Inne problemy zostały omówione w [Windows Sockets: Blokowanie](../mfc/windows-sockets-blocking.md) i [Windows Sockets: Określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md).  
  
 Jeśli jest używany lub pochodzi z klasy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), musisz samodzielnie zarządzania tymi problemami. Jeśli jest używany lub pochodzi z klasy [CSocket —](../mfc/reference/csocket-class.md), MFC zarządza nimi automatycznie.  
  
## <a name="converting-strings"></a>Konwertowanie ciągów  
 Jeśli do komunikacji między aplikacji, które używają ciągi przechowywane w różnych formatach znaków dwubajtowych, takie jak Unicode lub znaków wielobajtowych ustawia (MBCS) lub jeden z nich i aplikacji przy użyciu ciągów znaków ANSI, należy zarządzać konwersje samodzielnie w obszarze `CAsyncSocket`. `CArchive` Obiekt użyty z `CSocket` obiektu zarządza konwersji dla Ciebie za pośrednictwem funkcji klasy [cstring —](../atl-mfc-shared/reference/cstringt-class.md). Aby uzyskać więcej informacji zobacz specyfikację Windows Sockets, znajduje się w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Windows Sockets: Używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets: tła](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets: Gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Windows Sockets w MFC](../mfc/windows-sockets-in-mfc.md)

