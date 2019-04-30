---
title: 'Windows Sockets: Wyprowadzanie z klas gniazd'
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [MFC], from socket classes
- Windows Sockets [MFC], deriving from socket classes
- sockets [MFC], deriving from socket classes
ms.assetid: 3a26e67a-e323-433b-9b05-eca018799801
ms.openlocfilehash: 12ab66cfd9212cd79752e2f6359b857194c6428c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385261"
---
# <a name="windows-sockets-deriving-from-socket-classes"></a>Windows Sockets: Wyprowadzanie z klas gniazd

W tym artykule opisano niektóre funkcje, które można osiągnąć wyprowadzanie własne klasy z jednej z klas gniazd.

Własne gniazdo klasy mogą dziedziczyć albo [CAsyncSocket](../mfc/reference/casyncsocket-class.md) lub [CSocket](../mfc/reference/csocket-class.md) Aby dodać własne funkcje. W szczególności w ramach tych zajęć, podaj liczbę funkcji wirtualnych elementów członkowskich, które można przesłonić. Funkcje te obejmują [zdarzenia OnReceive](../mfc/reference/casyncsocket-class.md#onreceive), [OnSend](../mfc/reference/casyncsocket-class.md#onsend), [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept), [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect), i [OnClose](../mfc/reference/casyncsocket-class.md#onclose). Możesz przesłonić funkcji w klasie pochodnej gniazda z zalet powiadomienia, które zapewniają po wystąpieniu zdarzenia sieci. Struktura wywołuje te funkcje wywołania zwrotnego powiadomienie informujące o zdarzeń ważne gniazda, takich jak odbieranie danych, można rozpocząć się odczyt. Aby uzyskać więcej informacji na temat funkcji powiadomień, zobacz [Windows Sockets: Gniazda powiadomienia](../mfc/windows-sockets-socket-notifications.md).

Ponadto klasy `CSocket` dostarcza [OnMessagePending](../mfc/reference/csocket-class.md#onmessagepending) funkcji składowej (zaawansowaną możliwością). MFC wywołuje tę funkcję, podczas gdy gniazdo jest przekazywanie komunikatów z systemem Windows. Można zastąpić `OnMessagePending` Wyszukaj określone wiadomości z Windows i Reaguj na nie.

Domyślna wersja `OnMessagePending` dostarczone w klasie `CSocket` sprawdza, czy kolejka komunikatów dla komunikatów WM_PAINT podczas oczekiwania na ukończenie wywołania blokowania. Wywołuje komunikaty dotyczące malowania w celu poprawienia jakości wyświetlania. Oprócz wykonywania coś, co jest przydatne, to przedstawia jeden ze sposobów mogą zastąpić tę funkcję samodzielnie. Inny przykład Rozważ użycie `OnMessagePending` następujące zadania. Załóżmy, że podczas oczekiwania na ukończenie transakcji sieci wyświetlane jest niemodalne okno dialogowe. Okno dialogowe zawiera przycisk Anuluj, którego użytkownik może anulować blokowania transakcji, które zajmuje dużo czasu. Twoje `OnMessagePending` zastąpienie może pompy komunikatów związane z tym niemodalnego okna dialogowego.

W swojej `OnMessagePending` zastąpienia, zwracać albo **TRUE** lub powrót z wywołania do klasy bazowej wersję `OnMessagePending`. Należy wywołać wersję klasy podstawowej, jeśli wykonuje pracy, która nadal chcesz wykonać.

Aby uzyskać więcej informacji, zobacz:

- [Windows Sockets: używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: blokowanie](../mfc/windows-sockets-blocking.md)

- [Windows Sockets: określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets: konwertowanie ciągów](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>Zobacz także

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)
