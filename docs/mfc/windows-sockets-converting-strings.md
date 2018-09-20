---
title: 'Windows Sockets: Konwertowanie ciągów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], multibyte character string conversion
- sockets [MFC], multibyte character string conversion issues
- string conversion, multibyte character strings
ms.assetid: 9df522b5-6b23-41e0-bb96-e4e623baf141
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b23d2149659cdad320a58bdff0f42ba113b5696
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378944"
---
# <a name="windows-sockets-converting-strings"></a>Windows Sockets: konwertowanie ciągów

W tym artykule i dwa artykuły pomocnika opisano kilka problemów w programowaniu Windows Sockets. W tym artykule opisano konwersji ciągów. Inne problemy zostały omówione w [Windows Sockets: Blokowanie](../mfc/windows-sockets-blocking.md) i [Windows Sockets: Określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md).

Jeśli używasz lub pochodzić od klasy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), musisz samodzielnie zarządzania tymi problemami. Jeśli używasz lub pochodzić od klasy [CSocket](../mfc/reference/csocket-class.md), MFC zarządza je dla Ciebie.

## <a name="converting-strings"></a>Konwertowanie ciągów

Jeśli komunikacji między aplikacje, które używają ciągów przechowywanych w różnych formatach szerokich znaków, takich jak Unicode lub znaków wielobajtowych zestawy znaków (MBCS) lub między jeden z nich i aplikacji przy użyciu ciągów znaków ANSI musi zarządzać konwersje samodzielnie w obszarze `CAsyncSocket`. `CArchive` Obiekt użyty z `CSocket` tę konwersję dla Ciebie za pomocą funkcji klasy zarządza obiekt [CString](../atl-mfc-shared/reference/cstringt-class.md). Aby uzyskać więcej informacji zobacz specyfikację Windows Sockets, znajduje się w zestawie Windows SDK.

Aby uzyskać więcej informacji, zobacz:

- [Gniazda systemu Windows: używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Gniazda systemu Windows: używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Gniazda systemu Windows: podstawy](../mfc/windows-sockets-background.md)

- [Gniazda systemu Windows: gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)

- [Gniazda systemu Windows: gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Zobacz też

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)

