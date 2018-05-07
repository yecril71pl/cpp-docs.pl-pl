---
title: 'Windows Sockets: Konwertowanie ciągów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], multibyte character string conversion
- sockets [MFC], multibyte character string conversion issues
- string conversion, multibyte character strings
ms.assetid: 9df522b5-6b23-41e0-bb96-e4e623baf141
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bad57be68ce716cddf2ce44f12e94c545a7bbfd6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="windows-sockets-converting-strings"></a>Windows Sockets: konwertowanie ciągów
W tym artykule i dwa artykuły pomocnika opisano kilka problemów w programowaniu Windows Sockets. W tym artykule omówiono Konwertowanie ciągów. Inne problemy zostały omówione w [Windows Sockets: Blokowanie](../mfc/windows-sockets-blocking.md) i [Windows Sockets: Określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md).  
  
 Jeśli jest używany lub pochodzi z klasy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), musisz samodzielnie zarządzania tymi problemami. Jeśli jest używany lub pochodzi z klasy [CSocket —](../mfc/reference/csocket-class.md), MFC zarządza nimi automatycznie.  
  
## <a name="converting-strings"></a>Konwertowanie ciągów  
 Jeśli do komunikacji między aplikacji, które używają ciągi przechowywane w różnych formatach znaków dwubajtowych, takie jak Unicode lub znaków wielobajtowych ustawia (MBCS) lub jeden z nich i aplikacji przy użyciu ciągów znaków ANSI, należy zarządzać konwersje samodzielnie w obszarze `CAsyncSocket`. `CArchive` Obiekt użyty z `CSocket` obiektu zarządza konwersji dla Ciebie za pośrednictwem funkcji klasy [cstring —](../atl-mfc-shared/reference/cstringt-class.md). Aby uzyskać więcej informacji zobacz specyfikację Windows Sockets, znajduje się w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Gniazda systemu Windows: używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Gniazda systemu Windows: używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Gniazda systemu Windows: podstawy](../mfc/windows-sockets-background.md)  
  
-   [Gniazda systemu Windows: gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Gniazda systemu Windows: gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)

