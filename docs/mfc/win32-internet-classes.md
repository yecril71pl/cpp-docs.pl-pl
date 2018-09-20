---
title: Klasy internetowe Win32 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.win32
dev_langs:
- C++
helpviewer_keywords:
- Internet classes [MFC]
- WinInet classes [MFC], classes
- Win32 [MFC], Internet classes
- Windows API [MFC], Internet classes
ms.assetid: b49601d5-3025-4068-9408-316b54ee4375
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a1b4adb3de5c6ec57b9f6bc2c48385916c3e5076
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445701"
---
# <a name="win32-internet-classes"></a>Klasy internetowe Win32

MFC opakowuje internetowe Win32 (WinInet) i technologii ActiveX, aby ułatwić Programowanie w Internecie.

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które wypierają ActiveX zobacz [formantów ActiveX](activex-controls.md).


[CInternetSession](../mfc/reference/cinternetsession-class.md)<br/>
Tworzy i inicjuje sesji internetowej jeden lub kilka jednoczesnych sesji internetowej, a jeśli to konieczne, w tym artykule opisano połączenie z serwerem proxy.

[CInternetConnection](../mfc/reference/cinternetconnection-class.md)<br/>
Zarządza połączeniem z serwerem Internet.

[CInternetFile](../mfc/reference/cinternetfile-class.md)<br/>
Ta klasa i jej klasy pochodne zezwolić na dostęp do plików w systemach zdalnych, które korzystają z protokołów internetowych.

[CHttpConnection](../mfc/reference/chttpconnection-class.md)<br/>
Zarządza połączeniem z serwerem HTTP.

[CHttpFile](../mfc/reference/chttpfile-class.md)<br/>
Oferuje funkcje w celu odnalezienia i odczytania plików na serwerze HTTP.

[CGopherFile](../mfc/reference/cgopherfile-class.md)<br/>
Oferuje funkcje w celu odnalezienia i odczytania plików na serwerze gophera.

[CFtpConnection](../mfc/reference/cftpconnection-class.md)<br/>
Zarządza połączeniem z serwerem FTP.

[CGopherConnection](../mfc/reference/cgopherconnection-class.md)<br/>
Zarządza połączeniem z serwerem gopher.

[CFileFind](../mfc/reference/cfilefind-class.md)<br/>
Przeprowadza lokalne i internetowych plikach wyszukiwania.

[CFtpFileFind](../mfc/reference/cftpfilefind-class.md)<br/>
Pomoc Internetowych plikach wyszukiwania serwerów FTP.

[CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)<br/>
Pomoc Internetowych plikach wyszukiwania serwerów gopher.

[CGopherLocator](../mfc/reference/cgopherlocator-class.md)<br/>
Pobiera "Lokalizator" gopher z serwera gopher, określa typ lokalizatora i udostępnia go do `CGopherFileFind`.

[CInternetException](../mfc/reference/cinternetexception-class.md)<br/>
Przedstawia warunek wyjątku związany z operacją Internet.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

