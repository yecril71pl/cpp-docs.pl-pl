---
title: Klasy MFC do tworzenia klienckich aplikacji internetowych
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, WinInet classes
- WinInet classes [MFC], classes
- classes [MFC], MFC
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
ms.assetid: 67d34117-9839-4f4b-8bb8-0e4a9471c606
ms.openlocfilehash: 578fd5b72e6c04610aa862f1a6631895a32a9bfe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358218"
---
# <a name="mfc-classes-for-creating-internet-client-applications"></a>Klasy MFC do tworzenia klienckich aplikacji internetowych

MFC udostępnia następujące klasy i funkcje globalne do pisania aplikacji klienckich internetowych. Wcięcie wskazuje, że klasa jest pochodną klasy unindented powyżej niego. `CGopherFile`i `CHttpFile` wywodzi się na przykład z `CInternetFile`, na przykład. Te klasy i funkcje globalne są zadeklarowane w AFXINET. H, `CFileFind`z wyjątkiem , który jest zadeklarowany w AFX. H.

## <a name="classes"></a>Klasy

- [Cinternetsession](../mfc/reference/cinternetsession-class.md)

- [Połączenie międzysystemowe CInternet](../mfc/reference/cinternetconnection-class.md)

  - [Cftpconnection](../mfc/reference/cftpconnection-class.md)

  - [Cgopherconnection](../mfc/reference/cgopherconnection-class.md)

  - [CHttpConnection](../mfc/reference/chttpconnection-class.md)

- [Cinternetfile](../mfc/reference/cinternetfile-class.md)

  - [Cgopherfile](../mfc/reference/cgopherfile-class.md)

  - [CHttpFile](../mfc/reference/chttpfile-class.md)

- [Cfilefind](../mfc/reference/cfilefind-class.md)

  - [Cftpfilefind](../mfc/reference/cftpfilefind-class.md)

  - [Cgopherfilefind](../mfc/reference/cgopherfilefind-class.md)

- [CGopherLocator](../mfc/reference/cgopherlocator-class.md)

- [Cinternetexception](../mfc/reference/cinternetexception-class.md)

## <a name="global-functions"></a>Funkcje globalne

- [AfxParseURL (AfxParseURL)](reference/internet-url-parsing-globals.md#afxparseurl)

- [AfxGetInternetHandleType](reference/internet-url-parsing-globals.md#afxgetinternethandletype)

- [AfxThrowInternetEkceptacja](reference/internet-url-parsing-globals.md#afxthrowinternetexception)

## <a name="see-also"></a>Zobacz też

[Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Wymagania wstępne dotyczące klas klientów internetowych](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Pisanie klienckich aplikacji internetowych przy użyciu klas MFC WinInet](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
