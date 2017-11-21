---
title: Klasy MFC do tworzenia klienckich aplikacji internetowych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, WinInet classes
- WinInet classes [MFC], classes
- classes [MFC], MFC
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
ms.assetid: 67d34117-9839-4f4b-8bb8-0e4a9471c606
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cc7999791b52ade2b657c8602fbb9b7693c277de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-classes-for-creating-internet-client-applications"></a>Klasy MFC do tworzenia klienckich aplikacji internetowych
MFC udostępnia następujące klasy i funkcje globalne dla pisanie klienckich aplikacji internetowych. Wcięcie oznacza, że klasa pochodzi od klasy niewciętego powyżej. `CGopherFile`i `CHttpFile` pochodzi od `CInternetFile`, np. Te klasy i funkcje globalne są zadeklarowane w AFXINET. H, z wyjątkiem `CFileFind`, która jest zadeklarowana w AFX. H.  
  
## <a name="classes"></a>Klasy  
  
-   [CInternetSession](../mfc/reference/cinternetsession-class.md)  
  
-   [CInternetConnection](../mfc/reference/cinternetconnection-class.md)  
  
    -   [CFtpConnection](../mfc/reference/cftpconnection-class.md)  
  
    -   [CGopherConnection](../mfc/reference/cgopherconnection-class.md)  
  
    -   [CHttpConnection](../mfc/reference/chttpconnection-class.md)  
  
-   [CInternetFile](../mfc/reference/cinternetfile-class.md)  
  
    -   [Cgopherfile —](../mfc/reference/cgopherfile-class.md)  
  
    -   [CHttpFile](../mfc/reference/chttpfile-class.md)  
  
-   [CFileFind](../mfc/reference/cfilefind-class.md)  
  
    -   [CFtpFileFind](../mfc/reference/cftpfilefind-class.md)  
  
    -   [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)  
  
-   [CGopherLocator](../mfc/reference/cgopherlocator-class.md)  
  
-   [CInternetException](../mfc/reference/cinternetexception-class.md)  
  
## <a name="global-functions"></a>Globalne funkcje  
  
-   [Afxparseurl —](reference/internet-url-parsing-globals.md#afxparseurl)  
  
-   [Afxgetinternethandletype —](reference/internet-url-parsing-globals.md#afxgetinternethandletype)  
  
-   [Afxthrowinternetexception —](reference/internet-url-parsing-globals.md#afxthrowinternetexception)  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Wymagania wstępne dotyczące klas klientów internetowych](../mfc/prerequisites-for-internet-client-classes.md)   
 [Pisanie klienckich aplikacji internetowych przy użyciu klas MFC WinInet](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
