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
ms.openlocfilehash: 76ccb2ec126ae57e39b1a4fab3a0bff82a353d71
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953765"
---
# <a name="windows-sockets-deriving-from-socket-classes"></a>Windows Sockets: wyprowadzanie z klas gniazd
W tym artykule opisano niektóre funkcje, które można uzyskać przez wyprowadzanie własne klasy z jednej z klas gniazd.  
  
 Własnych klas gniazd może pochodzić z jednej [CAsyncSocket](../mfc/reference/casyncsocket-class.md) lub [CSocket —](../mfc/reference/csocket-class.md) Dodawanie własnych funkcji. W szczególności tych klas, podaj liczbę funkcji wirtualnego elementu członkowskiego, które można zastąpić. Te funkcje obejmują [zdarzenia OnReceive](../mfc/reference/casyncsocket-class.md#onreceive), [OnSend](../mfc/reference/casyncsocket-class.md#onsend), [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept), [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect), i [OnClose](../mfc/reference/casyncsocket-class.md#onclose). W klasie pochodnej gniazda przeprowadzać powiadomienia, które zapewniają po wystąpieniu zdarzenia sieci można zastąpić funkcji. Struktura wywołuje te funkcje wywołania zwrotnego powiadomień informujący o ważnych gniazda zdarzeń, takich jak odbieranie danych rozpocząć odczyt. Aby uzyskać więcej informacji na temat funkcji powiadomień, zobacz [Windows Sockets: powiadomienia dotyczące gniazd](../mfc/windows-sockets-socket-notifications.md).  
  
 Ponadto klasa `CSocket` dostarcza [OnMessagePending](../mfc/reference/csocket-class.md#onmessagepending) funkcji członkowskiej (zaawansowane możliwym do zastąpienia). MFC wywołania tej funkcji, gdy gniazda jest przekazywanie komunikatów systemu Windows. Można zastąpić `OnMessagePending` Aby znaleźć określone wiadomości z systemu Windows i nie odpowiadają.  
  
 Domyślna wersja `OnMessagePending` podany w klasie `CSocket` sprawdza kolejki komunikatów dla komunikatów WM_PAINT podczas oczekiwania na blokadzie wywołania do wykonania. Wywołuje komunikaty dotyczące malowania w celu poprawienia jakości wyświetlania. Jako uzupełnienie robi przydatne to przedstawiono jeden sposób może zastąpić funkcję samodzielnie. Innym przykładem, należy rozważyć użycie `OnMessagePending` następujące zadania. Załóżmy, że wyświetlane jest niemodalne okno dialogowe podczas oczekiwania na zakończenie transakcji sieci. Okno dialogowe zawiera przycisk Anuluj, którego użytkownik może anulować blokowania transakcje, które zbyt długo. Twoje `OnMessagePending` zastąpienie może pompa komunikaty dotyczące tego niemodalnego okna dialogowego.  
  
 W Twojej `OnMessagePending` zastępowania, zwracać **TRUE** lub powrót z wywołania do klasy podstawowej wersji `OnMessagePending`. Wywołuje wersji klasy podstawowej, jeśli wykonuje pracę, aby nadal chcesz wykonać.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Gniazda systemu Windows: używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Gniazda systemu Windows: używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Gniazda systemu Windows: blokowanie](../mfc/windows-sockets-blocking.md)  
  
-   [Gniazda systemu Windows: określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Gniazda systemu Windows: konwertowanie ciągów](../mfc/windows-sockets-converting-strings.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)

