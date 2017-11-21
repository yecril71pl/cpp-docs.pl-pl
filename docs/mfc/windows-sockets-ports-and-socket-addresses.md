---
title: 'Windows Sockets: Porty i adresy gniazd | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ports [MFC], definition
- Windows Sockets [MFC], ports
- Windows Sockets [MFC], addresses
- ports [MFC]
- addresses [MFC], socket
- sockets [MFC], addresses
- sockets [MFC], ports
ms.assetid: e050261a-9285-4f31-a1c5-6c8033af5b4a
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 768ccdc197df8d38cb594c2408bb6fc6998dfdcb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows Sockets: porty i adresy gniazd
W tym artykule opisano terminy "port" i "address" jak używać z usługi Windows Sockets.  
  
##  <a name="_core_port"></a>Port  
 Port identyfikuje unikatowy proces, dla którego można podać usługi. W kontekście obecne port jest skojarzony z aplikacją, która obsługuje Windows Sockets. Koncepcja jest jednoznacznie zidentyfikować każdej aplikacji Windows Sockets, więc można dodać więcej niż jedną aplikację usługi Windows Sockets uruchomione na komputerze, w tym samym czasie.  
  
 Niektóre porty są zastrzeżone dla wspólnych usług, takich jak FTP. Należy unikać używania tych portów, chyba że udostępniasz typu usługi. Specyfikacja Windows Sockets zawiera szczegóły dotyczące tych portami zarezerwowanymi. Plik WINSOCK. H wyświetla je.  
  
 Aby umożliwić biblioteki DLL systemu Windows Sockets wybierz portu można używać dla Ciebie, Przekaż 0 jako wartość portu. MFC wybiera port wartość większą niż 1024 dziesiętną. Można pobrać wartości portu, który MFC wybrany przez wywołanie metody [CAsyncSocket::GetSockName](../mfc/reference/casyncsocket-class.md#getsockname) funkcję elementu członkowskiego.  
  
##  <a name="_core_socket_address"></a>Adres gniazda  
 Każdy obiekt gniazda jest skojarzona z adresem Internet Protocol (IP) w sieci. Ten adres jest zwykle nazwę komputera, na przykład "pod adresem" lub liczbą kropkami, takie jak "128.56.22.8".  
  
 Podczas wyszukiwania można utworzyć gniazda, zwykle nie trzeba określić własnego adresu.  
  
> [!NOTE]
>  Możliwe, że ten komputer ma wiele kart sieciowych (lub aplikacji kiedyś mogą być uruchamiane w takie maszyny) reprezentujący z inną siecią. Jeśli tak, może być konieczne podać adres, aby określić, która karta sieciowa będzie używana gniazda. To jest pewne, zaawansowanych funkcji i możliwości przenoszenia problemu.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Windows Sockets: Używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets: Jak działają gniazda z archiwami](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets: Gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Windows Sockets w MFC](../mfc/windows-sockets-in-mfc.md)

