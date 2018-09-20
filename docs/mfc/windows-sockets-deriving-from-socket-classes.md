---
title: 'Windows Sockets: Wyprowadzanie z klas gniazd | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- derived classes [MFC], from socket classes
- Windows Sockets [MFC], deriving from socket classes
- sockets [MFC], deriving from socket classes
ms.assetid: 3a26e67a-e323-433b-9b05-eca018799801
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c562a8d6bf1c3f00f3812f6c25a4afd70276c64f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418960"
---
# <a name="windows-sockets-deriving-from-socket-classes"></a>Windows Sockets: wyprowadzanie z klas gniazd

W tym artykule opisano niektóre funkcje, które można osiągnąć wyprowadzanie własne klasy z jednej z klas gniazd.

Własne gniazdo klasy mogą dziedziczyć albo [CAsyncSocket](../mfc/reference/casyncsocket-class.md) lub [CSocket](../mfc/reference/csocket-class.md) Aby dodać własne funkcje. W szczególności w ramach tych zajęć, podaj liczbę funkcji wirtualnych elementów członkowskich, które można przesłonić. Funkcje te obejmują [zdarzenia OnReceive](../mfc/reference/casyncsocket-class.md#onreceive), [OnSend](../mfc/reference/casyncsocket-class.md#onsend), [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept), [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect), i [OnClose](../mfc/reference/casyncsocket-class.md#onclose). Możesz przesłonić funkcji w klasie pochodnej gniazda z zalet powiadomienia, które zapewniają po wystąpieniu zdarzenia sieci. Struktura wywołuje te funkcje wywołania zwrotnego powiadomienie informujące o zdarzeń ważne gniazda, takich jak odbieranie danych, można rozpocząć się odczyt. Aby uzyskać więcej informacji na temat funkcji powiadomień, zobacz [Windows Sockets: powiadomienia dotyczące gniazd](../mfc/windows-sockets-socket-notifications.md).

Ponadto klasy `CSocket` dostarcza [OnMessagePending](../mfc/reference/csocket-class.md#onmessagepending) funkcji składowej (zaawansowaną możliwością). MFC wywołuje tę funkcję, podczas gdy gniazdo jest przekazywanie komunikatów z systemem Windows. Można zastąpić `OnMessagePending` Wyszukaj określone wiadomości z Windows i Reaguj na nie.

Domyślna wersja `OnMessagePending` dostarczone w klasie `CSocket` sprawdza, czy kolejka komunikatów dla komunikatów WM_PAINT podczas oczekiwania na ukończenie wywołania blokowania. Wywołuje komunikaty dotyczące malowania w celu poprawienia jakości wyświetlania. Oprócz wykonywania coś, co jest przydatne, to przedstawia jeden ze sposobów mogą zastąpić tę funkcję samodzielnie. Inny przykład Rozważ użycie `OnMessagePending` następujące zadania. Załóżmy, że podczas oczekiwania na ukończenie transakcji sieci wyświetlane jest niemodalne okno dialogowe. Okno dialogowe zawiera przycisk Anuluj, którego użytkownik może anulować blokowania transakcji, które zajmuje dużo czasu. Twoje `OnMessagePending` zastąpienie może pompy komunikatów związane z tym niemodalnego okna dialogowego.

W swojej `OnMessagePending` zastąpienia, zwracać albo **TRUE** lub powrót z wywołania do klasy bazowej wersję `OnMessagePending`. Należy wywołać wersję klasy podstawowej, jeśli wykonuje pracy, która nadal chcesz wykonać.

Aby uzyskać więcej informacji, zobacz:

- [Gniazda systemu Windows: używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Gniazda systemu Windows: używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Gniazda systemu Windows: blokowanie](../mfc/windows-sockets-blocking.md)

- [Gniazda systemu Windows: określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md)

- [Gniazda systemu Windows: konwertowanie ciągów](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>Zobacz też

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)

