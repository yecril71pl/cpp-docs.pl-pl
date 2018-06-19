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
ms.openlocfilehash: c03ae586e346be2ba1e7c71475b69318ded0dd18
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385219"
---
# <a name="windows-sockets-how-sockets-with-archives-work"></a>Windows Sockets: jak działają gniazda z archiwami
W tym artykule opisano sposób [CSocket —](../mfc/reference/csocket-class.md) obiektu, [CSocketFile](../mfc/reference/csocketfile-class.md) obiektu, a [CArchive](../mfc/reference/carchive-class.md) obiektu połączone uprościć wysyłania i odbierania danych za pośrednictwem systemu Windows Gniazda.  
  
 Artykuł [Windows Sockets: przykład z gniazda przy użyciu archiwa](../mfc/windows-sockets-example-of-sockets-using-archives.md) przedstawia **PacketSerialize** funkcji. Obiekt archiwum w **PacketSerialize** przykład działa podobne jak w przypadku obiektu archiwum przekazany do MFC [serializacja](../mfc/reference/cobject-class.md#serialize) funkcji. Różnica niezbędne jest, czy dla gniazda, archiwum została dołączona nie do standardowego [cfile —](../mfc/reference/cfile-class.md) obiektu (zazwyczaj skojarzonych z plikiem dysku) ale do `CSocketFile` obiektu. Zamiast łączyć się plik dysku z `CSocketFile` łączy się z obiektu `CSocket` obiektu.  
  
 A `CArchive` obiektu zarządza buforu. Jeśli bufor przechowywania archiwum (wysyłającym) jest pełna, skojarzony `CFile` dokonuje zawartości buforu zapisu obiektu. Opróżnianie buforu archiwum dołączony do gniazda jest odpowiednikiem wysyłania komunikatu. Po zapełnieniu buforu archiwum (odbieranie) podczas ładowania `CFile` obiektu zatrzymuje odczytu do momentu bufor jest ponownie dostępny.  
  
 Klasa `CSocketFile` pochodną `CFile`, ale nie obsługuje [cfile —](../mfc/reference/cfile-class.md) funkcji elementów członkowskich, takich jak funkcje pozycjonowania (`Seek`, `GetLength`, `SetLength`i tak dalej), blokowania funkcji () `LockRange`, `UnlockRange`), lub `GetPosition` funkcji. Wszystkie [CSocketFile](../mfc/reference/csocketfile-class.md) wykonaj obiektu jest zapisu lub odczytu sekwencji bajtów do lub z skojarzony `CSocket` obiektu. Ponieważ plik nie jest elementem, operacje, takie jak `Seek` i `GetPosition` nie ma sensu. `CSocketFile` jest pochodną `CFile`, dlatego zazwyczaj będzie dziedziczyć wszystkie te funkcje Członkowskie. Aby temu zapobiec, nieobsługiwaną `CFile` funkcje Członkowskie zostały przesłonięte w `CSocketFile` wyrzucenie [CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md).  
  
 `CSocketFile` Obiektu wywołuje element członkowski funkcji jego `CSocket` obiekt do wysyłania i odbierania danych.  
  
 Na poniższej ilustracji przedstawiono relacje między tymi obiektami po obu stronach komunikacji.  
  
 ![CArchive — CSocketFile i CSocket —](../mfc/media/vc38ia1.gif "vc38ia1")  
CArchive — CSocketFile i CSocket —  
  
 Ta jawnego złożoności ma na celu można zabezpieczyć przed z konieczność zarządzania szczegóły gniazda samodzielnie. Tworzenie gniazda, pliku i archiwum, a następnie Rozpocznij wysyłanie lub odbieranie danych przez wstawieniu ich do archiwum lub wyodrębniania go z archiwum. [CArchive —](../mfc/reference/carchive-class.md), [CSocketFile](../mfc/reference/csocketfile-class.md), i [CSocket —](../mfc/reference/csocket-class.md) Zarządzanie szczegółami w tle.  
  
 A `CSocket` obiektu jest aktualnie obiektem dwustanowy: czasami asynchroniczne (zwykle stan) i czasami synchronicznych. W stanie asynchroniczne gniazda można otrzymywać powiadomienia asynchroniczne zwrócony przez strukturę. Jednak podczas operacji, takich jak odbieranie i wysyłanie danych gniazda staje się synchronicznego. Oznacza to, że gniazda zostaną wyświetlone żadne dodatkowe asynchroniczne powiadomienia, aż do zakończenia operacji synchronicznych. Ponieważ przełączenie tryby, można na przykład można wykonać postać zbliżoną do następującej:  
  
 [!code-cpp[NVC_MFCSimpleSocket#2](../mfc/codesnippet/cpp/windows-sockets-how-sockets-with-archives-work_1.cpp)]  
  
 Jeśli `CSocket` nie zostały zaimplementowane jako obiekt dwustanowy może być możliwe otrzymają dodatkowych powiadomień dla tego samego rodzaju zdarzenia w czasie zostały przetwarzania poprzedniej powiadomienia. Na przykład można uzyskać `OnReceive` powiadomień podczas przetwarzania `OnReceive`. W powyższym fragmentu kodu wyodrębniania `str` z archiwum może prowadzić do rekursji. Przełączając stanów, `CSocket` uniemożliwia rekursji, zapobiegając dodatkowe powiadomienia. Ogólną zasadą jest brak powiadomień w ramach powiadomienia.  
  
> [!NOTE]
>  A `CSocketFile` może również służyć jako plik (ograniczone) bez `CArchive` obiektu. Domyślnie `CSocketFile` konstruktora `bArchiveCompatible` parametr jest **TRUE**. Określa, że obiekt pliku jest przeznaczona do użytku z archiwum. Aby użyć obiektu pliku bez archiwizacji, należy przekazać **FALSE** w `bArchiveCompatible` parametru.  
  
 W trybie "compatible Archiwizuj" `CSocketFile` obiektu zapewnia lepszą wydajność i zmniejsza zagrożenie "zakleszczenie." Zakleszczenie występuje, gdy gniazd nadawczych i odbiorczych oczekiwanie na siebie lub Oczekiwanie na wspólnej zasobów. Taka sytuacja może wystąpić, jeśli `CArchive` obiektu doświadczenie z `CSocketFile` sposób za pomocą `CFile` obiektu. Z `CFile`, archiwum można założyć, że jeśli odbierze mniej bajtów niż zażądała na końcu pliku został osiągnięty. Z `CSocketFile`, jednak dane są na podstawie komunikatu; bufor może zawierać wiele komunikatów, więc odbieranie mniej niż żądana liczba bajtów nie oznacza koniec pliku. Aplikacji nie są blokowane w tym przypadku na przykład z `CFile`, i będzie możliwe kontynuowanie, odczytywanie wiadomości z buforu, dopóki bufor jest pusty. [IsBufferEmpty](../mfc/reference/carchive-class.md#isbufferempty) działać w `CArchive` jest przydatna do monitorowania stanu buforu archiwum w takim przypadku.  
  
 Aby uzyskać więcej informacji, zobacz [Windows Sockets: przy użyciu gniazda z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Windows Sockets w MFC](../mfc/windows-sockets-in-mfc.md)   
 [CObject::Serialize](../mfc/reference/cobject-class.md#serialize)

