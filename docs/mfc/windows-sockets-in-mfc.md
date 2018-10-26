---
title: Windows Sockets w MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- WINSOCK.DLL
- sockets [MFC], programming models
- MFC, Windows Sockets
- Windows Sockets [MFC], MFC support
- Windows Sockets [MFC], programming models
- WSOCK32.DLL
- sockets [MFC], MFC
ms.assetid: 1f3c476a-9c68-49fe-9a25-d22971a334d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a460870887f3a012bf02ee6518ba70c65881c804
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50081420"
---
# <a name="windows-sockets-in-mfc"></a>Windows Sockets w MFC

> [!NOTE]
>  MFC obsługuje Windows Sockets 1, ale nie obsługuje [Windows Sockets 2](/windows/desktop/WinSock/windows-sockets-start-page-2). Windows Sockets 2 najpierw dostarczane z programem Windows 98 i jest w wersji uwzględniony w systemie Windows 2000.

MFC udostępnia dwa modele do pisania programów łączności sieciowej z Windows Sockets, zawarte w dwóch klas MFC. W tym artykule opisano te modele i dalsze szczegóły MFC gniazd pomocy technicznej. "Gniazda" jest punktem końcowym komunikacji: obiekt, za pomocą którego aplikacja komunikuje się z innymi aplikacjami Windows Sockets w sieci.

Informacji na temat Windows Sockets, wyjaśnienie pojęcia gniazda, w tym temacie [Windows Sockets: tła](../mfc/windows-sockets-background.md).

##  <a name="_core_sockets_programming_models"></a> Modele programowania gniazd

Dwa gniazda Windows MFC modeli programowania są obsługiwane przez następujące klasy:

- `CAsyncSocket`

   Ta klasa hermetyzuje interfejs API Windows Sockets. [CAsyncSocket](../mfc/reference/casyncsocket-class.md) dla programistów, którzy znać programowanie dla sieci i elastyczność programowania bezpośrednio do gniazda interfejsu API, ale również wygodne funkcje wywołania zwrotnego dla powiadomień o zdarzeniach w sieci. Inne niż pakowania gniazda w postaci zorientowane obiektowo, do użytku w języku C++, jedynymi dodatkowymi abstrakcji, który dostarcza tej klasy jest konwersji niektóre komunikaty dotyczące gniazd Windows do wywołania zwrotne. Aby uzyskać więcej informacji, zobacz [Windows Sockets: powiadomienia dotyczące gniazd](../mfc/windows-sockets-socket-notifications.md).

- `CSocket`

   Ta klasa jest pochodną `CAsyncSocket`, dostarcza wyższe poziomu abstrakcji do pracy z gniazda za pomocą MFC [CArchive](../mfc/reference/carchive-class.md) obiektu. Przy użyciu gniazdo archiwum znacznie przypomina przy użyciu protokołu serializacji pliku MCF. To sprawia, że łatwiej niż korzystanie z `CAsyncSocket` modelu. [CSocket](../mfc/reference/csocket-class.md) dziedziczy wiele funkcji elementów członkowskich z `CAsyncSocket` które hermetyzują Windows Sockets API; trzeba będzie korzystać z niektórych z tych funkcji i zrozumieć ogólnie programowania gniazd. Ale `CSocket` zarządza wieloma aspektami komunikacji, który będzie trzeba samodzielnie przy użyciu surowego interfejsu API lub klasy `CAsyncSocket`. Co najważniejsze `CSocket` umożliwia blokowanie (z przetwarzania w tle komunikatów Windows), co jest niezbędne dla operacji synchronicznych `CArchive`.

Tworzenie i używanie `CSocket` i `CAsyncSocket` obiektów jest opisana w [Windows Sockets: przy użyciu gniazda z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md) i [Windows Sockets: przy użyciu klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md).

##  <a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a> Windows Sockets biblioteki dll

Systemy operacyjne Microsoft Windows, podaj Windows Sockets bibliotek dołączanych dynamicznie (DLL). Visual C++ dostarcza odpowiednie nagłówki i biblioteki i specyfikacja Windows Sockets.

Aby uzyskać więcej informacji na temat Windows Sockets zobacz:

- [Gniazda systemu Windows: gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)

- [Gniazda systemu Windows: gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)

- [Gniazda systemu Windows: używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Gniazda systemu Windows: sekwencja operacji](../mfc/windows-sockets-sequence-of-operations.md)

- [Gniazda systemu Windows: przykład gniazd korzystających z archiwów](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Gniazda systemu Windows: jak działają gniazda z archiwami](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Gniazda systemu Windows: używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Gniazda systemu Windows: wyprowadzanie z klas gniazd](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Gniazda systemu Windows: powiadomienia dotyczące gniazd](../mfc/windows-sockets-socket-notifications.md)

- [Gniazda systemu Windows: blokowanie](../mfc/windows-sockets-blocking.md)

- [Gniazda systemu Windows: określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md)

- [Gniazda systemu Windows: konwertowanie ciągów](../mfc/windows-sockets-converting-strings.md)

- [Gniazda systemu Windows: porty i adresy gniazd](../mfc/windows-sockets-ports-and-socket-addresses.md)

## <a name="see-also"></a>Zobacz też

[Gniazda systemu Windows](../mfc/windows-sockets.md)

