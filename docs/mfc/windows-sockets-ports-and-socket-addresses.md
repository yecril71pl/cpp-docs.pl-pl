---
title: 'Windows Sockets: Porty i adresy gniazd | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ports [MFC], definition
- Windows Sockets [MFC], ports
- Windows Sockets [MFC], addresses
- ports [MFC]
- addresses [MFC], socket
- sockets [MFC], addresses
- sockets [MFC], ports
ms.assetid: e050261a-9285-4f31-a1c5-6c8033af5b4a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 42ea9b8a39de8d36ecb621164d98e072a4041211
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows Sockets: porty i adresy gniazd
W tym artykule opisano terminy "port" i "address" jak używać z usługi Windows Sockets.  
  
##  <a name="_core_port"></a> Port  
 Port identyfikuje unikatowy proces, dla którego można podać usługi. W kontekście obecne port jest skojarzony z aplikacją, która obsługuje Windows Sockets. Koncepcja jest jednoznacznie zidentyfikować każdej aplikacji Windows Sockets, więc można dodać więcej niż jedną aplikację usługi Windows Sockets uruchomione na komputerze, w tym samym czasie.  
  
 Niektóre porty są zastrzeżone dla wspólnych usług, takich jak FTP. Należy unikać używania tych portów, chyba że udostępniasz typu usługi. Specyfikacja Windows Sockets zawiera szczegóły dotyczące tych portami zarezerwowanymi. Plik WINSOCK. H wyświetla je.  
  
 Aby umożliwić biblioteki DLL systemu Windows Sockets wybierz portu można używać dla Ciebie, Przekaż 0 jako wartość portu. MFC wybiera port wartość większą niż 1024 dziesiętną. Można pobrać wartości portu, który MFC wybrany przez wywołanie metody [CAsyncSocket::GetSockName](../mfc/reference/casyncsocket-class.md#getsockname) funkcję elementu członkowskiego.  
  
##  <a name="_core_socket_address"></a> Adres gniazda  
 Każdy obiekt gniazda jest skojarzona z adresem Internet Protocol (IP) w sieci. Ten adres jest zwykle nazwę komputera, na przykład "pod adresem" lub liczbą kropkami, takie jak "128.56.22.8".  
  
 Podczas wyszukiwania można utworzyć gniazda, zwykle nie trzeba określić własnego adresu.  
  
> [!NOTE]
>  Możliwe, że ten komputer ma wiele kart sieciowych (lub aplikacji kiedyś mogą być uruchamiane w takie maszyny) reprezentujący z inną siecią. Jeśli tak, może być konieczne podać adres, aby określić, która karta sieciowa będzie używana gniazda. To jest pewne, zaawansowanych funkcji i możliwości przenoszenia problemu.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Gniazda systemu Windows: używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Gniazda systemu Windows: używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Gniazda systemu Windows: jak działają gniazda z archiwami](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Gniazda systemu Windows: gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Gniazda systemu Windows: gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)

