---
title: Klasy MFC do tworzenia klienckich aplikacji internetowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, WinInet classes
- WinInet classes [MFC], classes
- classes [MFC], MFC
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
ms.assetid: 67d34117-9839-4f4b-8bb8-0e4a9471c606
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0e2365c0009bee3974cefcb7e9cb77f57045d712
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388743"
---
# <a name="mfc-classes-for-creating-internet-client-applications"></a>Klasy MFC do tworzenia klienckich aplikacji internetowych

Biblioteka MFC zawiera następujące klasy i funkcje globalne do tworzenia klienckich aplikacji internetowych. Wcięcie wskazuje, że klasa jest pochodną klasy niewciętego nad nim. `CGopherFile` i `CHttpFile` dziedziczyć `CInternetFile`, na przykład. Te klasy i funkcje globalne są deklarowane w AFXINET. Godz., z wyjątkiem `CFileFind`, która jest zadeklarowana w AFX. H.

## <a name="classes"></a>Klasy

- [CInternetSession](../mfc/reference/cinternetsession-class.md)

- [CInternetConnection](../mfc/reference/cinternetconnection-class.md)

   - [CFtpConnection](../mfc/reference/cftpconnection-class.md)

   - [CGopherConnection](../mfc/reference/cgopherconnection-class.md)

   - [CHttpConnection](../mfc/reference/chttpconnection-class.md)

- [CInternetFile](../mfc/reference/cinternetfile-class.md)

   - [CGopherFile](../mfc/reference/cgopherfile-class.md)

   - [CHttpFile](../mfc/reference/chttpfile-class.md)

- [CFileFind](../mfc/reference/cfilefind-class.md)

   - [CFtpFileFind](../mfc/reference/cftpfilefind-class.md)

   - [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)

- [CGopherLocator](../mfc/reference/cgopherlocator-class.md)

- [CInternetException](../mfc/reference/cinternetexception-class.md)

## <a name="global-functions"></a>Funkcje globalne

- [Afxparseurl —](reference/internet-url-parsing-globals.md#afxparseurl)

- [Afxgetinternethandletype —](reference/internet-url-parsing-globals.md#afxgetinternethandletype)

- [Afxthrowinternetexception —](reference/internet-url-parsing-globals.md#afxthrowinternetexception)

## <a name="see-also"></a>Zobacz też

[Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Wymagania wstępne dotyczące klas klientów internetowych](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Pisanie klienckich aplikacji internetowych przy użyciu klas MFC WinInet](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
