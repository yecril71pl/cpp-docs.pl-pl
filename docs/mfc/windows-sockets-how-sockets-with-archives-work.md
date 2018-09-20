---
title: 'Windows Sockets: Jak działają gniazda z archiwami | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], synchronous
- sockets [MFC], synchronous operation
- sockets [MFC], with archives
- synchronous state socket
- Windows Sockets [MFC], with archives
- two-state socket object
ms.assetid: d8ae4039-391d-44f0-a19b-558817affcbb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 080d72622d8963fc8dded8ffa6ab789a0f716aa1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400032"
---
# <a name="windows-sockets-how-sockets-with-archives-work"></a>Windows Sockets: jak działają gniazda z archiwami

W tym artykule opisano sposób [CSocket](../mfc/reference/csocket-class.md) obiektu, [CSocketFile](../mfc/reference/csocketfile-class.md) obiektu i [CArchive](../mfc/reference/carchive-class.md) obiektu są łączone w celu uproszczenia wysyłania i odbierania danych za pośrednictwem Windows Gniazda.

Artykuł [Windows Sockets: przykład z gniazda przy użyciu archiwa](../mfc/windows-sockets-example-of-sockets-using-archives.md) przedstawia `PacketSerialize` funkcji. Obiekt archiwum w `PacketSerialize` przykład działa podobnie do archiwum obiekt przekazany do MFC [Serialize](../mfc/reference/cobject-class.md#serialize) funkcji. Zasadnicza różnica jest to, że dla gniazda, archiwum została dołączona nie do standardowego [CFile](../mfc/reference/cfile-class.md) obiektu (zwykle skojarzone z plikiem dyskowym) ale do `CSocketFile` obiektu. Zamiast nawiązywania połączenia z plikiem dyskowym `CSocketFile` łączy się z obiektu `CSocket` obiektu.

Element `CArchive` obiektu zarządza buforu. Po zapełnieniu buforu zapisywanie archiwum (wysyłającym), skojarzoną `CFile` obiekt zapisuje poza zawartość buforu. Opróżnianie buforu archiwum dołączone do gniazda jest odpowiednikiem wysyłania komunikatu. Po zapełnieniu buforu archiwum (odbieranie) podczas ładowania `CFile` obiektu zatrzymuje odczytu, dopóki rozmiar buforu jest ponownie dostępny.

Klasa `CSocketFile` pochodzi od klasy `CFile`, ale nie obsługuje [CFile](../mfc/reference/cfile-class.md) funkcji elementów członkowskich, takich jak funkcje położenia (`Seek`, `GetLength`, `SetLength`i tak dalej), blokowanie funkcji () `LockRange`, `UnlockRange`), lub `GetPosition` funkcji. Wszystkie [CSocketFile](../mfc/reference/csocketfile-class.md) obiektu należy wykonać zapisu lub odczytu sekwencji bajtów do lub z powiązanego `CSocket` obiektu. Ponieważ plik nie jest zaangażowana, operacje takie jak `Seek` i `GetPosition` nie ma sensu. `CSocketFile` jest tworzony na podstawie `CFile`, dlatego zwykle będzie dziedziczyć wszystkie te funkcje elementów członkowskich. Aby temu zapobiec, nieobsługiwaną `CFile` elementów członkowskich są zastępowane w `CSocketFile` zgłosić [CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md).

`CSocketFile` Obiektu wywołuje element członkowski funkcji jego `CSocket` obiekt do wysyłania lub odbierania danych.

Na poniższej ilustracji przedstawiono relacje między tymi obiektami po obu stronach komunikacji.

![CArchive CSocketFile i CSocket](../mfc/media/vc38ia1.gif "vc38ia1") CArchive CSocketFile i CSocket

Tę złożoność jawnego ma na celu włączyć osłony dla z konieczności zarządzania szczegóły gniazda samodzielnie. Tworzenie gniazda, pliku i archiwum, a następnie Rozpocznij wysyłanie lub odbieranie danych od wstawiania ich do archiwum lub wyodrębniania go z archiwum. [CArchive](../mfc/reference/carchive-class.md), [CSocketFile](../mfc/reference/csocketfile-class.md), i [CSocket](../mfc/reference/csocket-class.md) Zarządzanie szczegółami w tle.

A `CSocket` obiekt jest rzeczywiście obiektem dwustanowy: czasami asynchroniczne (zwykle stan) i czasami synchronicznych. W stanie asynchronicznego gniazda można odbieranie powiadomień asynchronicznych, w ramach. Jednak podczas operacji takich jak odbieranie i wysyłanie danych gniazda staje się synchroniczne. Oznacza to, że gniazda będą wysyłane żadne dodatkowe asynchronicznego powiadomienia, dopóki nie zakończy się operacja synchroniczna. Ponieważ przełączniki tryby, można na przykład, można wykonać podobny do poniższego:

[!code-cpp[NVC_MFCSimpleSocket#2](../mfc/codesnippet/cpp/windows-sockets-how-sockets-with-archives-work_1.cpp)]

Jeśli `CSocket` nie zostały zaimplementowane jako obiekt dwoma stanami, może być możliwe, aby otrzymać dodatkowe powiadomienia dla tego samego typu zdarzenia, podczas gdy zostały przetwarza poprzednie powiadomienie. Na przykład, możesz otrzymać `OnReceive` powiadomień podczas przetwarzania `OnReceive`. W powyższym fragmencie kodu wyodrębniania `str` z archiwum może prowadzić do rekursji. Przełączając stanów `CSocket` zapobiega rekursji poprzez uniemożliwienie dodatkowe powiadomienia. Ogólną zasadą jest brak powiadomień w ramach powiadomienia.

> [!NOTE]
>  A `CSocketFile` może również służyć jako plik (ograniczone) bez `CArchive` obiektu. Domyślnie `CSocketFile` firmy Konstruktor *bArchiveCompatible* parametr jest **TRUE**. Określa, że plik jest do użytku z archiwum. Aby użyć obiektu pliku bez archiwum, Przekaż **FALSE** w *bArchiveCompatible* parametru.

W trybie "archiwum compatible" `CSocketFile` obiekt zapewnia lepszą wydajność i zmniejsza zagrożenie "zakleszczenie." Zakleszczenie występuje, gdy gniazd nadawczych i Oczekiwanie na siebie nawzajem lub oczekując na zasób wspólnej. Taka sytuacja może wystąpić, jeśli `CArchive` obiektu doświadczenie z `CSocketFile` sposób, jak za pomocą `CFile` obiektu. Za pomocą `CFile`, archiwum, można założyć, że jeśli odbierze mniej bajtów niż żądana go, na końcu pliku został osiągnięty. Za pomocą `CSocketFile`, jednak dane są na podstawie komunikatu; bufor może zawierać wiele komunikatów, więc odbieranie mniej niż żądana liczba bajtów nie oznacza koniec pliku. Aplikacja nie są blokowane w tym przypadku na przykład za pomocą `CFile`, i można kontynuować, odczytywanie wiadomości z buforu, dopóki rozmiar buforu jest pusty. [IsBufferEmpty](../mfc/reference/carchive-class.md#isbufferempty) działa w programach `CArchive` przydaje się do monitorowania stanu bufora archiwum w takiej sytuacji.

Aby uzyskać więcej informacji, zobacz [Windows Sockets: przy użyciu gniazda z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)

## <a name="see-also"></a>Zobacz też

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CObject::Serialize](../mfc/reference/cobject-class.md#serialize)

