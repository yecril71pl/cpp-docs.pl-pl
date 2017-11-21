---
title: "Kroki w typowej aplikacji klienckiej FTP do usunięcia pliku | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Internet client applications [MFC], FTP delete
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 2c347a96-c0a4-4827-98fe-668406e552bc
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d9da0db842267e12f9697f2416783286300b84b9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="steps-in-a-typical-ftp-client-application-to-delete-a-file"></a>Procedura usuwania pliku w typowej aplikacji klienckiej FTP
W poniższej tabeli przedstawiono kroki, które można wykonywać w typowej aplikacji klienckiej FTP, która usuwa plik.  
  
|Poznasz|Czynności|Efekty|  
|---------------|----------------------|-------------|  
|Rozpocznij sesję FTP.|Utwórz [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu.|Inicjuje WinInet i łączy się z serwerem.|  
|Nawiązuje połączenie z serwerem FTP.|Użyj [CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection).|Zwraca [CFtpConnection](../mfc/reference/cftpconnection-class.md) obiektu.|  
|Sprawdź, upewnij się, że jesteś w prawo katalogu na serwerze FTP.|Użyj [CFtpConnection::GetCurrentDirectory](../mfc/reference/cftpconnection-class.md#getcurrentdirectory) lub [CFtpConnection::GetCurrentDirectoryAsURL](../mfc/reference/cftpconnection-class.md#getcurrentdirectoryasurl).|Zwraca nazwę lub adres URL katalogu, którego jesteś obecnie podłączony do na serwerze, w zależności od funkcji członkowskiej wybrane.|  
|Przejdź do nowego katalogu FTP na serwerze.|Użyj [CFtpConnection::SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|Zmienia nazwę katalogu, którego jesteś obecnie podłączony do na serwerze.|  
|Znajdź pierwszy plik w katalogu FTP.|Użyj [CFtpFileFind::FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|Znajduje pierwszy plik. Zwraca wartość FAŁSZ, jeśli nie są można odnaleźć plików.|  
|Znajdź następny plik w katalogu FTP.|Użyj [CFtpFileFind::FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Znajduje następny plik. Zwraca wartość FAŁSZ, jeśli plik nie został znaleziony.|  
|Usuń plik został znaleziony przez klasę **FindFile** lub `FindNextFile`.|Użyj [CFtpConnection::Remove](../mfc/reference/cftpconnection-class.md#remove), przy użyciu nazwy pliku zwracane przez **FindFile** lub `FindNextFile`.|Usuwa plik na serwerze do odczytu lub zapisu.|  
|Obsługa wyjątków.|Użyj [CInternetException](../mfc/reference/cinternetexception-class.md) klasy.|Obsługuje wszystkie popularne typy wyjątków Internet.|  
|Kończenie sesji FTP.|Usuwa [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu.|Automatycznie oczyszcza dojścia do plików Otwórz i połączeń.|  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Wymagania wstępne dotyczące klas klientów internetowych](../mfc/prerequisites-for-internet-client-classes.md)   
 [Pisanie klienckich aplikacji internetowych przy użyciu klas MFC WinInet](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
