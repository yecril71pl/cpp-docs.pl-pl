---
title: Pisanie klienckich aplikacji internetowych przy użyciu klas MFC WinInet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Internet client applications [MFC]
- WinInet classes [MFC], programming
- Internet client applications [MFC], writing
- Internet applications [MFC], WinInet
- Internet applications [MFC], client applications
- MFC, Internet applications
ms.assetid: a2c4a40c-a94e-4b3e-9dbf-f8a8dc8e5428
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 822b75ec71d79b6e40ec6b61a77239707c32ce39
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384439"
---
# <a name="writing-an-internet-client-application-using-mfc-wininet-classes"></a>Pisanie klienckich aplikacji internetowych przy użyciu klas MFC WinInet
Podstawą co klienckich aplikacji internetowych jest sesji internetowej. MFC implementuje sesji internetowej jako obiektów klasy [CInternetSession](../mfc/reference/cinternetsession-class.md). Za pomocą tej klasy, można utworzyć sesji Internet jeden lub kilka jednoczesnych sesji.  
  
 Aby komunikować się z serwerem, należy [CInternetConnection](../mfc/reference/cinternetconnection-class.md) obiektu, a także `CInternetSession`. Można utworzyć `CInternetConnection` za pomocą [CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection), [CInternetSession::GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection), lub [CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection). Każdy z tych wywołań jest określone dla wybranego typu protokołu. Tych wywołań nie należy otwierać plik na serwerze do odczytu lub zapisu. Jeśli zamierzasz odczytu lub zapisu danych, należy otworzyć plik w osobnym kroku.  
  
 Dla większości sesji internetowej `CInternetSession` obiekt działa ręcznie w ręcznie z [CInternetFile](../mfc/reference/cinternetfile-class.md) obiektu:  
  
-   Dla sesji Internet, należy utworzyć wystąpienie [CInternetSession](../mfc/reference/cinternetsession-class.md).  
  
-   Jeśli sesja Internet odczytuje i zapisuje dane, należy utworzyć wystąpienie `CInternetFile` (lub jej podklasy [CHttpFile](../mfc/reference/chttpfile-class.md) lub [cgopherfile —](../mfc/reference/cgopherfile-class.md)). Najprostszym sposobem odczytu danych jest wywołać [CInternetSession::OpenURL](../mfc/reference/cinternetsession-class.md#openurl). Ta funkcja analizuje uniwersalnych (adres URL Resource Locator) dostarczone przez użytkownika, otwiera połączenie z serwerem wskazanym przez adres URL i zwraca tylko do odczytu `CInternetFile` obiektu. `CInternetSession::OpenURL` nie jest specyficzne dla typu jeden protokół — działa to samo wywołanie dla dowolnego FTP, HTTP lub gopher adresu URL. `CInternetSession::OpenURL` nawet współpracuje z plików lokalnych (przekazujących `CStdioFile` zamiast `CInternetFile`).  
  
-   Jeśli Internetu sesji nie odczytu lub zapisu danych, ale wykonywania innych zadań, takich jak usuwanie plików w katalogu FTP może trzeba utworzyć wystąpienia `CInternetFile`.  
  
 Istnieją dwa sposoby tworzenia `CInternetFile` obiektu:  
  
-   Jeśli używasz `CInternetSession::OpenURL` nawiązać połączenie z serwerem, wywołanie `OpenURL` zwraca `CStdioFile`.  
  
-   Jeśli użyj **CInternetSession::GetFtpConnection**, `GetGopherConnection`, lub `GetHttpConnection` nawiązać połączenie z serwerem, należy wywołać `CFtpConnection::OpenFile`, `CGopherConnection::OpenFile`, lub **CHttpConnection::OpenRequest,**  odpowiednio do zwrócenia `CInternetFile`, `CGopherFile`, lub `CHttpFile`odpowiednio.  
  
 Kroki implementowania klienckich aplikacji internetowych się różnić w zależności od tego, czy tworzyć ogólnego klienta internetowego na podstawie **OpenURL** lub przy użyciu jednej z klienta oparte na protokole **GetConnection** funkcje.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Jak napisać klienckich aplikacji internetowych objęty współpracujące z FTP, HTTP i gopher](../mfc/steps-in-a-typical-internet-client-application.md)  
  
-   [Jak napisać aplikację klienta FTP, który otworzy plik](../mfc/steps-in-a-typical-ftp-client-application.md)  
  
-   [Jak tworzyć aplikacje klienta FTP nie powoduje otwarcia pliku, która wykonuje operację katalogu, takich jak usuwanie pliku](../mfc/steps-in-a-typical-ftp-client-application-to-delete-a-file.md)  
  
-   [Jak napisać aplikacji klienckiej gopher](../mfc/steps-in-a-typical-gopher-client-application.md)  
  
-   [Jak napisać aplikację klienta HTTP](../mfc/steps-in-a-typical-http-client-application.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Klasy MFC do tworzenia klienckich aplikacji internetowych](../mfc/mfc-classes-for-creating-internet-client-applications.md)   
 [Wymagania wstępne dotyczące klas klientów internetowych](../mfc/prerequisites-for-internet-client-classes.md)
