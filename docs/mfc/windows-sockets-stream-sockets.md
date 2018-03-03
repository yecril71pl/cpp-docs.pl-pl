---
title: 'Windows Sockets: Strumienia Sockets | Dokumentacja firmy Microsoft'
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
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- stream sockets [MFC]
ms.assetid: 31faaa34-a995-493f-a30b-b8115293d619
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bc112bd3cfbf1194a2898afecb513edcbc456747
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-stream-sockets"></a>Windows Sockets: gniazda strumieni
W tym artykule opisano gniazda strumieni, jeden z dwóch typów gniazda Windows dostępne. (Jest innego typu [gniazdo datagramu](../mfc/windows-sockets-datagram-sockets.md).)  
  
 Gniazda strumieni podanie przepływu danych, bez rekordów granice: strumień bajtów, które mogą być dwukierunkowe (aplikacja jest pełny dupleks: można zarówno przesyłania i odbierania za pośrednictwem gniazda). Strumienie mogą być stosowane w celu dostarczania danych Sekwencyjna, unduplicated. ("Sekwencjonowania" oznacza, że pakiety są dostarczane w kolejności wysłane. "Unduplicated" oznacza tylko raz pobrać określonego pakietu). Jest gwarantowana w komunikatach strumienia i strumieni dobrze nadają się do obsługi dużych ilości danych.  
  
 Warstwa transportu sieciowego może podzielić lub grupowania danych w pakiety odpowiednie rozmiary. `CSocket` Klasy obsłuży pakowania i rozpakowywania dla Ciebie.  
  
 Strumienie są oparte na jawne połączeń: gniazda A żądania połączenia gniazda B; gniazda B zaakceptuje lub odrzuci połączenia.  
  
 Połączenia telefonicznego zapewnia dobre odpowiednio dla strumienia. W normalnych okolicznościach otrzymującej rejestrował głos mówiącego powiedzieć w kolejności powiedzieć, bez duplikowania i utraty. Gniazda strumieni są odpowiednie, na przykład w przypadku implementacji takich jak protokół FTP (File Transfer), ułatwiający przesyłania ASCII lub plików binarnych dowolnego rozmiaru.  
  
 Gniazda strumieni są preferowane w porównaniu do gniazda do przesyłania datagramów, gdy dane należy zagwarantować odebranie i gdy rozmiar danych jest duży. Aby uzyskać więcej informacji na temat gniazda strumieni zobacz specyfikację Windows Sockets. Specyfikacja jest dostępne w zestawie Windows SDK.  
  
 Korzystanie z gniazda strumieni może być większa niż aplikacji przeznaczonych do użycia przez gniazdo datagramu dla emisji do wszystkich gniazda odbierania w sieci, ponieważ  
  
-   Model emisji podlega problemy z siecią powódź (lub "storm").  
  
-   Modelu klient serwer późniejsze jest bardziej wydajny.  
  
-   Model strumienia dostarcza transferu danych niezawodne, gdzie modelu datagram nie.  
  
-   Ostatecznego modelu wykorzystuje komunikację między Unicode i ANSI gniazda aplikacje tej klasy, które CArchive jest przydatna do klasy CSocket —.  
  
    > [!NOTE]
    >  Jeśli używasz klasy `CSocket`, należy użyć strumienia. Potwierdzenie MFC zakończy się niepowodzeniem, jeśli określony typ gniazda jako **SOCK_DGRAM**.  
  
## <a name="see-also"></a>Zobacz też  
 [Windows Sockets w MFC](../mfc/windows-sockets-in-mfc.md)   
 [Gniazda systemu Windows: podstawy](../mfc/windows-sockets-background.md)

