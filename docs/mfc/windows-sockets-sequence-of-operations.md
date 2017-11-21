---
title: 'Windows Sockets: Sekwencja operacji | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows Sockets [MFC], operations
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- sockets [MFC], operations
- stream sockets [MFC]
ms.assetid: 43ce76f5-aad3-4247-b8a6-16cc7d012796
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6568582b7e6ea44298e5a332a16c22ae54b12cc8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="windows-sockets-sequence-of-operations"></a>Windows Sockets: sekwencja operacji
W tym artykule przedstawiono obok siebie, sekwencja operacji przy gniazda serwera i klienta gniazda. Ponieważ jest używany przez gniazdami `CArchive` obiekty, są zawsze [strumienia sockets](../mfc/windows-sockets-stream-sockets.md).  
  
## <a name="sequence-of-operations-for-a-stream-socket-communication"></a>Sekwencja operacji przy komunikacji gniazda strumieni  
 Do tworzenia punktu `CSocketFile` obiekt następująca sekwencja jest dokładna (z kilku różnic parametru) dla obu `CAsyncSocket` i `CSocket`. Od tego momentu kolejności jest ściśle dla `CSocket`. W poniższej tabeli przedstawiono sekwencja operacji przy Konfigurowanie komunikacji między klientem serwerem.  
  
### <a name="setting-up-communication-between-a-server-and-a-client"></a>Konfigurowanie komunikacji między serwerem klientem  
  
|Serwer|Klient|  
|------------|------------|  
|`// construct a socket`<br /><br /> `CSocket sockSrvr;`|`// construct a socket`<br /><br /> `CSocket sockClient;`|  
|`// create the SOCKET`<br /><br /> `sockSrvr.Create(nPort);`1,2|`// create the SOCKET`<br /><br /> `sockClient.Create( );`2|  
|`// start listening`<br /><br /> `sockSrvr.Listen( );`||  
||`// seek a connection`<br /><br /> `sockClient.Connect(strAddr, nPort);`3,4|  
|`// construct a new, empty socket`<br /><br /> `CSocket sockRecv;`<br /><br /> `// accept connection`<br /><br /> `sockSrvr.Accept( sockRecv );` 5||  
|`// construct file object`<br /><br /> `CSocketFile file(&sockRecv);`|`// construct file object`<br /><br /> `CSocketFile file(&sockClient);`|  
|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> —lub—<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> - lub -|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> —lub—<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> - lub -|  
|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> —lub—<br /><br /> `arOut << dwValue;`6|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> —lub—<br /><br /> `arOut << dwValue;`6|  
  
 1. Gdzie `nPort` numer portu. Zobacz [Windows Sockets: porty i adresy gniazd](../mfc/windows-sockets-ports-and-socket-addresses.md) szczegółowe informacje o portach.  
  
 2. Serwer zawsze należy określić port, więc klienci mogą łączyć się. **Utwórz** wywołanie określa również czasami adres. Po stronie klienta Użyj parametrów domyślnych, które poproś MFC do użycia dowolny dostępny port.  
  
 3. Gdzie `nPort` numer portu i *strAddr* jest adres komputera lub adres Internet Protocol (IP).  
  
 4. Adresy komputera może potrwać kilka formularzy: "pod adresem", "microsoft.com". Adresy IP formularz "kropkami numer" "127.54.67.32". **Connect** funkcja sprawdza, czy adres jest liczbą kropkami (choć nie sprawdza upewnij się, liczba jest nieprawidłowa maszyny w sieci). Jeśli nie, **Connect** przyjmuje nazwę komputera z jednym z innych formularzy.  
  
 5. Podczas wywoływania **Akceptuj** po stronie serwera, należy przekazać odwołanie do nowego obiektu gniazda. Należy najpierw utworzyć ten obiekt, ale nie należy wywoływać **Utwórz** dla niego. Należy pamiętać, że jeśli ten obiekt gniazda trafia zakresu, zamyka połączenie. Nowy obiekt do łączy MFC **GNIAZDA** obsługi. Można utworzyć gniazda na stosie, jak pokazano lub na stosie.  
  
 6. Archiwum i plik gniazda są zamknięte, gdy przejdą poza zakresem. Obiekt gniazda destruktor również wywoła [Zamknij](../mfc/reference/casyncsocket-class.md#close) funkcji członkowskiej dla obiekt gniazda podczas wykracza poza zakres lub usunięcia obiektu.  
  
## <a name="additional-notes-about-the-sequence"></a>Dodatkowe uwagi dotyczące sekwencji  
 Sekwencja wywołań przedstawione w powyższej tabeli jest dla gniazda strumienia. Gniazda do przesyłania datagramów, które są bez połączenia, nie wymagają [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect), [nasłuchiwania](../mfc/reference/casyncsocket-class.md#listen), i [Akceptuj](../mfc/reference/casyncsocket-class.md#accept) wywołania (mimo że można używać **Połączyć**). Zamiast tego Jeśli używasz klasy `CAsyncSocket`, datagram gniazda korzystają `CAsyncSocket::SendTo` i `ReceiveFrom` funkcji elementów członkowskich. (Jeśli używasz **Connect** z gniazdem datagram używasz **wysyłania** i **Receive**.) Ponieważ `CArchive` nie działa z datagramy, nie używaj `CSocket` z archiwum jeśli datagram gniazda.  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md) nie obsługuje wszystkich `CFile`jego funkcjonalności. `CFile` elementów członkowskich, takich jak `Seek`, który nie ma sensu komunikacji gniazda, są niedostępne. W związku z tym niektóre domyślne MFC `Serialize` funkcje nie są zgodne z `CSocketFile`. Jest to szczególnie istotne w `CEditView` klasy. Nie należy próbować serializować `CEditView` danych za pośrednictwem `CArchive` obiekt dołączony do `CSocketFile` przy użyciu `CEditView::SerializeRaw`; użyj **CEditView::Serialize** zamiast (Nieudokumentowany). [SerializeRaw](../mfc/reference/ceditview-class.md#serializeraw) funkcja oczekuje obiektu pliku ma funkcje, takie jak `Seek`, że `CSocketFile` nie obsługuje.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Windows Sockets: Używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets: Używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Porty i adresy gniazd](../mfc/windows-sockets-ports-and-socket-addresses.md)  
  
-   [Windows Sockets: Gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Windows Sockets w MFC](../mfc/windows-sockets-in-mfc.md)   
 [CSocket — klasa](../mfc/reference/csocket-class.md)   
 [CAsyncSocket::Create](../mfc/reference/casyncsocket-class.md#create)   
 [CAsyncSocket::Close](../mfc/reference/casyncsocket-class.md#close)

