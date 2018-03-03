---
title: Podstawy HTTP | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- HTTP [MFC], return codes
- return codes [MFC]
- HTTP requests [MFC], return codes
ms.assetid: 5b7421bf-42c8-4f3a-8566-8ff5957f58cc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 67921e0667267b99b3787d55fa7ff564aa543ae7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="http-basics"></a>Podstawy HTTP
Podczas pisania aplikacji internetowej, możesz często zbadać i dodać do informacji w nagłówku HTTP. Kody powrotu oznaczają powodzenie lub niepowodzenie żądane zdarzenie. Kilka typowych kody powrotu są wymienione w poniższej tabeli.  
  
|Kod powrotu|Znaczenie|  
|-----------------|-------------|  
|200|Adres URL znajduje się, sposób przekazywania|  
|400|Żądanie niezrozumiałe|  
|404|Żądany adres URL nie znaleźć.|  
|405|Serwer nie obsługuje żądanego — metoda|  
|500|Nieznany błąd serwera|  
|503|Usługa jest niedostępna|  
  
 Odpowiedzi HTTP są grupowane, jak pokazano w poniższej tabeli.  
  
|Grupa|Znaczenie|  
|-----------|-------------|  
|200-299|Powodzenie|  
|300-399|Informacje|  
|400-499|Błąd żądania|  
|500-599|Błąd serwera|  
  
 Protokół HTTP (Hypertext Transfer) to protokół poziomu aplikacji hipermedialnych systemów informatycznych. Aby uzyskać więcej informacji na temat HTTP i sposobu komunikacji między przeglądarkami i serwerami zobacz specyfikację protokołu HTTP (Hypertext Transfer):  
  
 [http://www.w3.org/pub/WWW/Protocols/](http://www.w3.org/pub/www/protocols/)  
  
## <a name="see-also"></a>Zobacz też  
 [MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)

