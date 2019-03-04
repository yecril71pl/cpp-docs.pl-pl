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
ms.openlocfilehash: 9992d2054c04eea1b3b63d591601acf0091acb5e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266790"
---
# <a name="windows-sockets-in-mfc"></a>Windows Sockets w MFC

> [!NOTE]
>  MFC obsługuje Windows Sockets 1, ale nie obsługuje [Windows Sockets 2](/windows/desktop/WinSock/windows-sockets-start-page-2). Windows Sockets 2 najpierw dostarczane z programem Windows 98 i jest w wersji uwzględniony w systemie Windows 2000.

MFC udostępnia dwa modele do pisania programów łączności sieciowej z Windows Sockets, zawarte w dwóch klas MFC. W tym artykule opisano te modele i dalsze szczegóły MFC gniazd pomocy technicznej. "Gniazda" jest punktem końcowym komunikacji: obiekt, za pomocą którego aplikacja komunikuje się z innymi aplikacjami Windows Sockets w sieci.

Informacji na temat Windows Sockets, wyjaśnienie pojęcia gniazda, w tym temacie [Windows Sockets: Tło](../mfc/windows-sockets-background.md).

##  <a name="_core_sockets_programming_models"></a> Modele programowania gniazd

Dwa gniazda Windows MFC modeli programowania są obsługiwane przez następujące klasy:

- `CAsyncSocket`

   Ta klasa hermetyzuje interfejs API Windows Sockets. [CAsyncSocket](../mfc/reference/casyncsocket-class.md) dla programistów, którzy znać programowanie dla sieci i elastyczność programowania bezpośrednio do gniazda interfejsu API, ale również wygodne funkcje wywołania zwrotnego dla powiadomień o zdarzeniach w sieci. Inne niż pakowania gniazda w postaci zorientowane obiektowo, do użytku w języku C++, jedynymi dodatkowymi abstrakcji, który dostarcza tej klasy jest konwersji niektóre komunikaty dotyczące gniazd Windows do wywołania zwrotne. Aby uzyskać więcej informacji, zobacz [Windows Sockets: Gniazda powiadomienia](../mfc/windows-sockets-socket-notifications.md).

- `CSocket`

   Ta klasa jest pochodną `CAsyncSocket`, dostarcza wyższe poziomu abstrakcji do pracy z gniazda za pomocą MFC [CArchive](../mfc/reference/carchive-class.md) obiektu. Przy użyciu gniazdo archiwum znacznie przypomina przy użyciu protokołu serializacji pliku MCF. To sprawia, że łatwiej niż korzystanie z `CAsyncSocket` modelu. [CSocket](../mfc/reference/csocket-class.md) dziedziczy wiele funkcji elementów członkowskich z `CAsyncSocket` które hermetyzują Windows Sockets API; trzeba będzie korzystać z niektórych z tych funkcji i zrozumieć ogólnie programowania gniazd. Ale `CSocket` zarządza wieloma aspektami komunikacji, który będzie trzeba samodzielnie przy użyciu surowego interfejsu API lub klasy `CAsyncSocket`. Co najważniejsze `CSocket` umożliwia blokowanie (z przetwarzania w tle komunikatów Windows), co jest niezbędne dla operacji synchronicznych `CArchive`.

Tworzenie i używanie `CSocket` i `CAsyncSocket` obiektów jest opisana w [Windows Sockets: Używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md) i [Windows Sockets: Używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md).

##  <a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a> Windows Sockets biblioteki dll

Systemy operacyjne Microsoft Windows, podaj Windows Sockets bibliotek dołączanych dynamicznie (DLL). Visual C++ dostarcza odpowiednie nagłówki i biblioteki i specyfikacja Windows Sockets.

Aby uzyskać więcej informacji na temat Windows Sockets zobacz:

- [Windows Sockets: Gniazda Stream](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)

- [Windows Sockets: Używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: Sekwencja operacji](../mfc/windows-sockets-sequence-of-operations.md)

- [Windows Sockets: Przykład gniazd korzystających z archiwów](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows Sockets: Jak działają gniazda z archiwami](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: Używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Wyprowadzanie z klas gniazd](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets: Powiadomienia dotyczące gniazd](../mfc/windows-sockets-socket-notifications.md)

- [Windows Sockets: Blokowanie](../mfc/windows-sockets-blocking.md)

- [Windows Sockets: Określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets: Konwertowanie ciągów](../mfc/windows-sockets-converting-strings.md)

- [Windows Sockets: Porty i adresy gniazd](../mfc/windows-sockets-ports-and-socket-addresses.md)

## <a name="see-also"></a>Zobacz także

[Gniazda systemu Windows](../mfc/windows-sockets.md)
