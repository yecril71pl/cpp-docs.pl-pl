---
title: Kroki w typowej aplikacji klienckiej FTP | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Internet client applications [MFC], FTP table
- FTP (File Transfer Protocol)
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 70bed7b5-6040-40d1-bc77-702e63a698f2
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d707d2b4903394b6b3b70367184767cce28ea1d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="steps-in-a-typical-ftp-client-application"></a>Kroki wykonywane w typowej aplikacji klienckiej FTP
Tworzy w typowej aplikacji klienckiej FTP [CInternetSession](../mfc/reference/cinternetsession-class.md) i [CFtpConnection](../mfc/reference/cftpconnection-class.md) obiektu. Należy pamiętać, że tych klas MFC WinInet nie faktycznie kontroli typ ustawień serwera proxy; Wykonuje usług IIS.  
  
 Zobacz też następujące artykuły bazy wiedzy Knowledge Base:  
  
-   Porada: FTP z serwerem Proxy na podstawie CERN, przy użyciu interfejsu API WinInet (identyfikator artykułu: Q166961)  
  
-   PRZYKŁAD: FTP z haseł oparte na CERN chronionego serwera Proxy (identyfikator artykułu: Q216214)  
  
-   Nie powiodło się Menedżer pokazanie zainstalowany serwer Proxy usług usług internetowych (identyfikator artykułu: Q216802)  
  
 W poniższej tabeli przedstawiono kroki, które mogą wykonywać w typowej aplikacji klienckiej FTP.  
  
|Poznasz|Czynności|Efekty|  
|---------------|----------------------|-------------|  
|Rozpocznij sesję FTP.|Utwórz [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu.|Inicjuje WinInet i łączy się z serwerem.|  
|Nawiązuje połączenie z serwerem FTP.|Użyj [CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection).|Zwraca [CFtpConnection](../mfc/reference/cftpconnection-class.md) obiektu.|  
|Przejdź do nowego katalogu FTP na serwerze.|Użyj [CFtpConnection::SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|Zmienia nazwę katalogu, którego jesteś obecnie podłączony do na serwerze.|  
|Znajdź pierwszy plik w katalogu FTP.|Użyj [CFtpFileFind::FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|Znajduje pierwszy plik. Zwraca wartość FAŁSZ, jeśli nie są można odnaleźć plików.|  
|Znajdź następny plik w katalogu FTP.|Użyj [CFtpFileFind::FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Znajduje następny plik. Zwraca wartość FAŁSZ, jeśli plik nie został znaleziony.|  
|Otwórz plik został znaleziony przez klasę **FindFile** lub `FindNextFile` do odczytu lub zapisu.|Użyj [CFtpConnection::OpenFile](../mfc/reference/cftpconnection-class.md#openfile), przy użyciu nazwy pliku zwracane przez [FindFile](../mfc/reference/cftpfilefind-class.md#findfile) lub [FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Otwiera plik na serwerze do odczytu lub zapisu. Zwraca [CInternetFile](../mfc/reference/cinternetfile-class.md) obiektu.|  
|Odczytywanie i zapisywanie do pliku.|Użyj [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read) lub [CInternetFile::Write](../mfc/reference/cinternetfile-class.md#write).|Odczytuje i zapisuje określoną liczbę bajtów, przy użyciu podanego buforu.|  
|Obsługa wyjątków.|Użyj [CInternetException](../mfc/reference/cinternetexception-class.md) klasy.|Obsługuje wszystkie popularne typy wyjątków Internet.|  
|Kończenie sesji FTP.|Usuwa [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu.|Automatycznie oczyszcza dojścia do plików Otwórz i połączeń.|  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Wymagania wstępne dotyczące klas klientów internetowych](../mfc/prerequisites-for-internet-client-classes.md)   
 [Pisanie klienckich aplikacji internetowych przy użyciu klas MFC WinInet](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
