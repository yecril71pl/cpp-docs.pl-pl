---
title: 'Windows Sockets: Konwertowanie ciągów'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], multibyte character string conversion
- sockets [MFC], multibyte character string conversion issues
- string conversion, multibyte character strings
ms.assetid: 9df522b5-6b23-41e0-bb96-e4e623baf141
ms.openlocfilehash: eaf278fc2689f0afa9ab6ff30f1294c36de5d7ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62217394"
---
# <a name="windows-sockets-converting-strings"></a>Windows Sockets: Konwertowanie ciągów

W tym artykule i dwa artykuły pomocnika opisano kilka problemów w programowaniu Windows Sockets. W tym artykule opisano konwersji ciągów. Inne problemy zostały omówione w [Windows Sockets: Blokowanie](../mfc/windows-sockets-blocking.md) i [Windows Sockets: Określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md).

Jeśli używasz lub pochodzić od klasy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), musisz samodzielnie zarządzania tymi problemami. Jeśli używasz lub pochodzić od klasy [CSocket](../mfc/reference/csocket-class.md), MFC zarządza je dla Ciebie.

## <a name="converting-strings"></a>Konwertowanie ciągów

Jeśli komunikacji między aplikacje, które używają ciągów przechowywanych w różnych formatach szerokich znaków, takich jak Unicode lub znaków wielobajtowych zestawy znaków (MBCS) lub między jeden z nich i aplikacji przy użyciu ciągów znaków ANSI musi zarządzać konwersje samodzielnie w obszarze `CAsyncSocket`. `CArchive` Obiekt użyty z `CSocket` tę konwersję dla Ciebie za pomocą funkcji klasy zarządza obiekt [CString](../atl-mfc-shared/reference/cstringt-class.md). Aby uzyskać więcej informacji zobacz specyfikację Windows Sockets, znajduje się w zestawie Windows SDK.

Aby uzyskać więcej informacji, zobacz:

- [Windows Sockets: Używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: Tło](../mfc/windows-sockets-background.md)

- [Windows Sockets: Gniazda Stream](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Zobacz także

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)
