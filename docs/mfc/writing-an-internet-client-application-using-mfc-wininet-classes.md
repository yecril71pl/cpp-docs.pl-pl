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
ms.openlocfilehash: 4e048ff64632c2ffdb263e7dcf33a51b9d50d528
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443868"
---
# <a name="writing-an-internet-client-application-using-mfc-wininet-classes"></a>Pisanie klienckich aplikacji internetowych przy użyciu klas MFC WinInet

Podstawa każda aplikacja kliencka Internet jest sesji internetowej. MFC implementuje sesji internetowej jako obiekty klasy [CInternetSession](../mfc/reference/cinternetsession-class.md). Korzystając z tej klasy, można utworzyć sesji internetowej jeden lub kilka jednoczesnych sesji.

Aby komunikować się z serwerem, musisz mieć [CInternetConnection](../mfc/reference/cinternetconnection-class.md) obiektu, a także `CInternetSession`. Możesz utworzyć `CInternetConnection` przy użyciu [CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection), [CInternetSession::GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection), lub [CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection). Każdy z tych wywołań jest specyficzny dla typu protokołu. Te wywołania nie należy otwierać plik na serwerze do odczytu lub zapisu. Aby przeprowadzić odczytu lub zapisu danych, należy otworzyć plik w osobnym kroku.

Dla większości sesji internetowej `CInternetSession` obiekt działa ręcznie likwidacji [CInternetFile](../mfc/reference/cinternetfile-class.md) obiektu:

- Dla sesji Internet, należy utworzyć wystąpienie [CInternetSession](../mfc/reference/cinternetsession-class.md).

- Jeśli sesja Internet operacja odczytu lub zapisu danych, należy utworzyć wystąpienie `CInternetFile` (lub jej podklasach [CHttpFile](../mfc/reference/chttpfile-class.md) lub [CGopherFile](../mfc/reference/cgopherfile-class.md)). Najprostszym sposobem odczytu danych jest wywołać [CInternetSession::OpenURL](../mfc/reference/cinternetsession-class.md#openurl). Ta funkcja analizuje Universal (adres URL Resource Locator) podane przez użytkownika, otwiera połączenie z serwerem wskazanym przez adres URL i zwraca tylko do odczytu `CInternetFile` obiektu. `CInternetSession::OpenURL` nie jest specyficzne dla typu jeden protokół — to samo wywołanie działa w przypadku dowolnego adresu URL protokołu FTP, HTTP lub gopher. `CInternetSession::OpenURL` działa to również plików lokalnych (przekazujących `CStdioFile` zamiast `CInternetFile`).

- Jeśli w sieci Internet, sesja nie odczytu lub zapisu danych, ale wykonuje inne zadania, takie jak usuwanie pliku w katalogu FTP nie konieczne może być utworzenie wystąpienia `CInternetFile`.

Istnieją dwa sposoby tworzenia `CInternetFile` obiektu:

- Jeśli używasz `CInternetSession::OpenURL` nawiązać połączenie z serwerem, wywołanie `OpenURL` zwraca `CStdioFile`.

- Jeśli użyj `CInternetSession::GetFtpConnection`, `GetGopherConnection`, lub `GetHttpConnection` nawiązać połączenie z serwerem, należy wywołać `CFtpConnection::OpenFile`, `CGopherConnection::OpenFile`, lub `CHttpConnection::OpenRequest`, odpowiednio, aby zwrócić `CInternetFile`, `CGopherFile`, lub `CHttpFile`, odpowiednio.

Kroki opisane we wdrażaniu klienckich aplikacji internetowych różnią się w zależności od tego, czy tworzysz ogólnego klienta internetowego, na podstawie `OpenURL` lub przy użyciu jednej z klienta oparte na protokole `GetConnection` funkcji.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Jak napisać aplikację klienta internetowego, która działa w ogólnej przy użyciu protokołu FTP, HTTP i gopher](../mfc/steps-in-a-typical-internet-client-application.md)

- [Jak pisać aplikacji klienckiej FTP, który otworzy plik](../mfc/steps-in-a-typical-ftp-client-application.md)

- [Jak napisać aplikację klienta FTP nie powoduje otwarcia pliku, która wykonuje operację katalogu, takie jak usuwanie pliku](../mfc/steps-in-a-typical-ftp-client-application-to-delete-a-file.md)

- [Jak napisać aplikacji klienckiej gopher](../mfc/steps-in-a-typical-gopher-client-application.md)

- [Jak napisać aplikację klienta HTTP](../mfc/steps-in-a-typical-http-client-application.md)

## <a name="see-also"></a>Zobacz też

[Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Klasy MFC do tworzenia klienckich aplikacji internetowych](../mfc/mfc-classes-for-creating-internet-client-applications.md)<br/>
[Wymagania wstępne dotyczące klas klientów internetowych](../mfc/prerequisites-for-internet-client-classes.md)
