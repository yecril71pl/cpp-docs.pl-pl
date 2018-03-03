---
title: "Jak WinInet ułatwia tworzenie klienckich aplikacji internetowych | Dokumentacja firmy Microsoft"
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
- Windows Sockets [MFC], vs. WinInet
- WinInet classes [MFC], vs. WinSock
- WinInet classes [MFC], Internet client applications
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9c79404f296df09afb177930897064b8455217d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-wininet-makes-it-easier-to-create-internet-client-applications"></a>Jak WinInet ułatwia tworzenie klienckich aplikacji internetowych
Rozszerzenia internetowe Win32 lub WinInet, zapewniają dostęp do wspólnych protokołów internetowych, w tym gopher, FTP i HTTP. Przy użyciu interfejsu WinInet, można napisać klienckie aplikacje internetowe na wyższym poziomie programowania, bez konieczności WinSock, TCP/IP lub szczegóły określonych protokołów internetowych. WinInet zapewnia spójny zestaw funkcji dla wszystkich trzech protokołów, ze znanego interfejsu API systemu Win32. Ta spójności minimalizuje zmiany kodu, który należy upewnić się, jeśli podstawowy protokół ulegnie zmianie (na przykład z FTP HTTP).  
  
 Visual C++ udostępnia dwa sposoby można użyć interfejsu WinInet. Należy bezpośrednio wywoływać funkcje internetowe Win32 (zobacz dokumentację OLE w zestawie SDK systemu Windows, aby uzyskać więcej informacji) lub użyć WinInet za pośrednictwem [klas MFC WinInet](../mfc/mfc-classes-for-creating-internet-client-applications.md).  
  
 **Można użyć interfejsu WinInet do:**  
  
-   Pobierz stron HTML.  
  
     HTTP to protokół używany do przesyłania stron HTML od serwera do przeglądarki klienta.  
  
-   Wysyłanie żądań FTP, przekazywanie lub pobieranie plików lub pobrania zawartości katalogu.  
  
     Typowy żądanie jest anonimowego logowania, aby pobrać plik.  
  
-   Użyj gopher w menu systemu do uzyskiwania dostępu do zasobów w Internecie.  
  
     Elementy menu może być kilka typów, w tym inne menu, indeksowanego bazy danych, które można przeszukiwać, grupę lub pliku.  
  
 Dla wszystkich trzech protokołów nawiązać połączenie, wysyłać żądania do serwera i zamknięcie połączenia.  
  
 **Klasy MFC WinInet ułatwia:**  
  
-   Jako odczyt plików z dysku twardego łatwo odczytać informacji z HTTP, FTP i gopher serwerów.  
  
-   Używa protokołów HTTP, FTP i gopher bez programowania bezpośrednio do WinSock lub TCP/IP.  
  
     Deweloperzy korzystający z funkcji Win32 Internet jest konieczne należy zapoznać się z TCP/IP lub Windows Sockets. Można nadal umieszczonych na poziomie gniazda bezpośrednio, za pomocą protokołów WinSock i TCP/IP, ale jest łatwiejsze do używania klas MFC WinInet dostępu HTTP, FTP i protokoły gopher w Internecie. Wiele typowych operacji deweloperzy nie muszą znajomość konkretnego protokołu, którego używają.  
  
 Wiele operacji, które mogą być wykonywane przez komputer jako klienta na inne komputery w Internecie może zająć dużo czasu. Szybkość tych operacji zwykle jest ograniczona przez szybkość połączenia sieciowego, ale mogą również wpływać na innego ruchu sieciowego i złożoność operacji. Na przykład nawiązywania połączenia z serwerem FTP, wymaga, że komputer najpierw wyszukać nazwę tego serwera, aby znaleźć adres. Aplikacja spróbuje połączyć się z serwerem pod tym adresem. Po otwarciu połączenia komputera i serwera zdalnego zainicjuje konwersację z protokół transferu plików przed połączenia faktycznie służy do pobierania plików.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Jak MFC ułatwia tworzenie klienckich aplikacji internetowych](../mfc/how-mfc-makes-it-easier-to-create-internet-client-applications.md)

