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
ms.openlocfilehash: 8e5562b028d3d9b7cba4b47716b63fd1392c514f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371096"
---
# <a name="windows-sockets-in-mfc"></a>Windows Sockets w MFC

> [!NOTE]
> MFC obsługuje gniazda systemu Windows 1, ale nie obsługuje [windows sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2). Windows Sockets 2 po raz pierwszy dostarczony z systemem Windows 98 i jest wersją dołączona do systemu Windows 2000.

MFC dostarcza dwa modele do pisania programów komunikacji sieciowej z gniazdami systemu Windows, zawarte w dwóch klasach MFC. W tym artykule opisano te modele i dalsze szczegóły obsługa gniazd MFC. "Gniazdo" jest punktem końcowym komunikacji: obiekt, za pośrednictwem którego aplikacja komunikuje się z innymi systemami Windows Sockets aplikacji w sieci.

Aby uzyskać informacje na temat gniazd systemu Windows, w tym wyjaśnienie pojęcia gniazda, zobacz [Gniazda systemu Windows: Tło](../mfc/windows-sockets-background.md).

## <a name="sockets-programming-models"></a><a name="_core_sockets_programming_models"></a>Modele programowania gniazd

Dwa modele programowania MFC Windows Sockets są obsługiwane przez następujące klasy:

- `CAsyncSocket`

   Ta klasa hermetyzuje interfejs API sockets systemu Windows. [CAsyncSocket](../mfc/reference/casyncsocket-class.md) jest dla programistów, którzy znają programowanie sieciowe i chcą elastyczności programowania bezpośrednio do gniazda INTERFEJSU API, ale także chcą wygody funkcji wywołania zwrotnego do powiadamiania o zdarzeniach sieciowych. Inne niż gniazda pakowania w formie obiektowej do użytku w języku C++, tylko dodatkowe abstrakcji tej klasy dostarcza jest konwersja niektórych komunikatów związanych z gniazdem systemu Windows do wywołań zwrotnych. Aby uzyskać więcej informacji, zobacz [Windows Sockets: Socket Notifications](../mfc/windows-sockets-socket-notifications.md).

- `CSocket`

   Ta klasa, pochodzące z `CAsyncSocket`, dostarcza abstrakcji wyższego poziomu do pracy z gniazdami za pośrednictwem MFC [CArchive](../mfc/reference/carchive-class.md) obiektu. Korzystanie z gniazda z archiwum bardzo przypomina przy użyciu protokołu serializacji plików MFC. Dzięki temu jest łatwiejszy w `CAsyncSocket` użyciu niż model. [CSocket](../mfc/reference/csocket-class.md) dziedziczy wiele `CAsyncSocket` funkcji członkowskich z tego hermetyzowania interfejsów API gniazda systemu Windows; trzeba będzie użyć niektórych z tych funkcji i zrozumieć gniazda programowania ogólnie. Ale `CSocket` zarządza wiele aspektów komunikacji, które trzeba zrobić samodzielnie za pomocą `CAsyncSocket`surowego INTERFEJSU API lub klasy . Co najważniejsze, `CSocket` zapewnia blokowanie (z przetwarzaniem w tle wiadomości systemu Windows), `CArchive`co jest niezbędne do synchronicznego działania .

Tworzenie i `CSocket` używanie `CAsyncSocket` obiektów jest opisane w [gniazdach systemu Windows: Korzystanie z gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md) i [gniazdami systemu Windows: Korzystanie z klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md).

## <a name="windows-sockets-dlls"></a><a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a>Biblioteki DLL socket systemu Windows

Systemy operacyjne Microsoft Windows dostarczają biblioteki dynamiczne (DLL) dla gniazd systemu Windows. Visual C++ dostarcza odpowiednie pliki nagłówka i biblioteki i specyfikacji gniazda systemu Windows.

Aby uzyskać więcej informacji na temat gniazd systemu Windows, zobacz:

- [Gniazda systemu Windows: gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)

- [Gniazda systemu Windows: gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)

- [Gniazda systemu Windows: używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: sekwencja operacji](../mfc/windows-sockets-sequence-of-operations.md)

- [Windows Sockets: przykład gniazd korzystających z archiwów](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows Sockets: jak działają gniazda z archiwami](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Gniazda systemu Windows: używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Gniazda systemu Windows: wyprowadzanie z klas gniazd](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Gniazda systemu Windows: powiadomienia dotyczące gniazd](../mfc/windows-sockets-socket-notifications.md)

- [Gniazda systemu Windows: blokowanie](../mfc/windows-sockets-blocking.md)

- [Gniazda systemu Windows: określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md)

- [Gniazda systemu Windows: konwertowanie ciągów](../mfc/windows-sockets-converting-strings.md)

- [Gniazda systemu Windows: porty i adresy gniazd](../mfc/windows-sockets-ports-and-socket-addresses.md)

## <a name="see-also"></a>Zobacz też

[Gniazda systemu Windows](../mfc/windows-sockets.md)
