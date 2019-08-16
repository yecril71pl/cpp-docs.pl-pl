---
title: Windows Sockets w MFC
ms.date: 11/04/2016
helpviewer_keywords:
- WINSOCK.DLL
- sockets [MFC], programming models
- MFC, Windows Sockets
- Windows Sockets [MFC], MFC support
- Windows Sockets [MFC], programming models
- WSOCK32.DLL
- sockets [MFC], MFC
ms.assetid: 1f3c476a-9c68-49fe-9a25-d22971a334d0
ms.openlocfilehash: 44a4838a1cd863bd484701966a156be9f61f8988
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510624"
---
# <a name="windows-sockets-in-mfc"></a>Windows Sockets w MFC

> [!NOTE]
>  MFC obsługuje system Windows Sockets 1, ale nie obsługuje [Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2). Windows Sockets 2 po raz pierwszy dostarczany z systemem Windows 98 i jest wersją dołączoną do systemu Windows 2000.

MFC oferuje dwa modele do pisania programów komunikacji sieciowej z Windows Sockets, zawarte w dwóch klasach MFC. W tym artykule opisano te modele oraz dokładniejsze informacje o obsłudze usługi MFC Sockets. "Socket" to punkt końcowy komunikacji: obiekt, za pomocą którego aplikacja komunikuje się z innymi aplikacjami Windows Sockets w sieci.

Aby uzyskać informacje dotyczące Windows Sockets, w tym wyjaśnienie koncepcji gniazda, zobacz [Windows Sockets: Tło](../mfc/windows-sockets-background.md).

##  <a name="_core_sockets_programming_models"></a>Modele programowania gniazd

Dwa modele programowania MFC Windows Sockets są obsługiwane przez następujące klasy:

- `CAsyncSocket`

   Ta klasa hermetyzuje interfejs API usługi Windows Sockets. [CAsyncSocket](../mfc/reference/casyncsocket-class.md) jest przeznaczony dla programistów, którzy znają programowanie sieci i chcą elastycznie programowania bezpośrednio w interfejsie API usługi Sockets, ale również chcą wygodę funkcji wywołania zwrotnego dla powiadomień o zdarzeniach sieciowych. Oprócz gniazd opakowaniowych w formie zorientowanej obiektowo do użycia w C++programie jedynym dodatkowym abstrakcją jest konwersja niektórych komunikatów systemu Windows związanych z gniazdem na wywołania zwrotne. Aby uzyskać więcej informacji, [zobacz Windows Sockets: Powiadomienia](../mfc/windows-sockets-socket-notifications.md)gniazda.

- `CSocket`

   Ta klasa, która pochodzi `CAsyncSocket`z, dostarcza abstrakcję wyższego poziomu do pracy z gniazdami za pośrednictwem obiektu MFC [CArchive](../mfc/reference/carchive-class.md) . Używanie gniazd z archiwum znacznie przypomina korzystanie z protokołu serializacji plików MFC. Ułatwia to użycie niż `CAsyncSocket` model. [CSocket](../mfc/reference/csocket-class.md) dziedziczy wiele funkcji `CAsyncSocket` składowych, które hermetyzują interfejsy API usługi Windows Sockets. należy użyć niektórych z tych funkcji i ogólnie zrozumieć programowanie gniazd. Program `CSocket` zarządza jednak wieloma aspektami komunikacji, które trzeba wykonać samodzielnie przy użyciu raw API lub klasy. `CAsyncSocket` Co najważniejsze, `CSocket` zapewnia blokowanie (z przetwarzaniem w tle komunikatów systemu Windows), co jest niezbędne do synchronicznej `CArchive`operacji.

Tworzenie i używanie `CSocket` obiektów `CAsyncSocket` oraz obiekty są opisane [w Windows Sockets: Używanie gniazd z](../mfc/windows-sockets-using-sockets-with-archives.md) archiwami [i Windows Sockets: Korzystanie z klasy](../mfc/windows-sockets-using-class-casyncsocket.md)CAsyncSocket.

##  <a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a>Biblioteki DLL Windows Sockets

Systemy operacyjne Microsoft Windows zapewniają biblioteki dołączane dynamicznie (DLL) dla systemu Windows Sockets. Wizualizacja C++ dostarcza odpowiednich plików nagłówkowych i bibliotek oraz specyfikację Windows Sockets.

Aby uzyskać więcej informacji o usłudze Windows Sockets, zobacz:

- [Windows Sockets: gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)

- [Windows Sockets: używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: sekwencja operacji](../mfc/windows-sockets-sequence-of-operations.md)

- [Windows Sockets: przykład gniazd korzystających z archiwów](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows Sockets: jak działają gniazda z archiwami](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: wyprowadzanie z klas gniazd](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets: powiadomienia dotyczące gniazd](../mfc/windows-sockets-socket-notifications.md)

- [Windows Sockets: blokowanie](../mfc/windows-sockets-blocking.md)

- [Windows Sockets: określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets: konwertowanie ciągów](../mfc/windows-sockets-converting-strings.md)

- [Windows Sockets: porty i adresy gniazd](../mfc/windows-sockets-ports-and-socket-addresses.md)

## <a name="see-also"></a>Zobacz także

[Gniazda systemu Windows](../mfc/windows-sockets.md)
