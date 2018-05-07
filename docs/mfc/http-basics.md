---
title: Podstawy HTTP | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTTP [MFC], return codes
- return codes [MFC]
- HTTP requests [MFC], return codes
ms.assetid: 5b7421bf-42c8-4f3a-8566-8ff5957f58cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 56a2692edd9d41f80023e44f4ca8172cba8f9d00
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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

