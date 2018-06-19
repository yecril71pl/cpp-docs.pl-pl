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
ms.openlocfilehash: 84fc25ab6515b22fa647b3cc32833c791b59f2b8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385515"
---
# <a name="windows-sockets-in-mfc"></a>Windows Sockets w MFC
> [!NOTE]
>  MFC Windows Sockets 1 obsługuje, ale nie obsługuje [Windows Sockets 2](http://msdn.microsoft.com/library/windows/desktop/ms740673). Windows Sockets 2 najpierw dostarczane z systemem Windows 98, a jest to wersja systemu Windows 2000.  
  
 MFC udostępnia dwa modele do pisania programów komunikacji sieciowej z usługi Windows Sockets zawartymi w dwóch klas MFC. W tym artykule opisano te modele i dalsze szczegóły MFC gniazda pomocy technicznej. "Gniazda" jest punktem końcowym komunikacji: obiekt, za pomocą których aplikacja komunikuje się z innych aplikacji Windows Sockets w sieci.  
  
 Aby uzyskać informacje o Windows Sockets, łącznie z wyjaśnieniem koncepcji gniazda, zobacz [Windows Sockets: tła](../mfc/windows-sockets-background.md).  
  
##  <a name="_core_sockets_programming_models"></a> Modele programowania gniazd  
 Dwa MFC Windows Sockets modele programowania są obsługiwane przez następujące klasy:  
  
-   `CAsyncSocket`  
  
     Ta klasa hermetyzuje interfejsu API systemu Windows Sockets. [CAsyncSocket](../mfc/reference/casyncsocket-class.md) dla programistów, którzy znać programowanie dla sieci i elastyczność programowania bezpośrednio do gniazda interfejsu API, ale również wygodne funkcje wywołania zwrotnego dla powiadomień o zdarzeniach w sieci. Inne niż pakowania sockets w zorientowane obiektowo formularza do użycia w języku C++, tylko dodatkowe warstwy abstrakcji przez ta klasa dostarcza konwertuje komunikatów systemu Windows związanych z gniazda do wywołania zwrotne. Aby uzyskać więcej informacji, zobacz [Windows Sockets: powiadomienia dotyczące gniazd](../mfc/windows-sockets-socket-notifications.md).  
  
-   `CSocket`  
  
     Ta klasa pochodzi od `CAsyncSocket`, dostarcza wyższej abstrakcji poziomu do pracy z gniazda za pomocą MFC [CArchive](../mfc/reference/carchive-class.md) obiektu. Przy użyciu gniazda z archiwum znacznie podobny przy użyciu protokołu serializacji pliku MFC. Dzięki temu łatwiejsze niż w `CAsyncSocket` modelu. [CSocket —](../mfc/reference/csocket-class.md) dziedziczy wiele funkcji Członkowskich z `CAsyncSocket` które hermetyzują interfejsów API usługi Windows Sockets; będą musiały korzystać z niektórych z tych funkcji i zrozumieć zazwyczaj programowania gniazd. Ale `CSocket` zarządza wielu aspektów komunikacji, który będzie musiał wykonać samodzielnie przy użyciu raw interfejsu API albo klasy `CAsyncSocket`. Przede wszystkim `CSocket` umożliwia blokowanie (z przetwarzania w tle komunikatów systemu Windows), co jest niezbędne do działania synchroniczne `CArchive`.  
  
 Tworzenie i używanie `CSocket` i `CAsyncSocket` obiektów jest opisany w [Windows Sockets: przy użyciu gniazda z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md) i [Windows Sockets: przy użyciu klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md).  
  
##  <a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a> Windows Sockets bibliotek DLL  
 Systemy operacyjne Microsoft Windows, podaj Windows Sockets biblioteki dołączanej (dynamicznie DLL). Visual C++ dostarcza odpowiednie pliki nagłówkowe i biblioteki i specyfikację Windows Sockets.  
  
 Aby uzyskać więcej informacji na temat usługi Windows Sockets zobacz:  
  
-   [Gniazda systemu Windows: gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Gniazda systemu Windows: gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)  
  
-   [Gniazda systemu Windows: używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Gniazda systemu Windows: sekwencja operacji](../mfc/windows-sockets-sequence-of-operations.md)  
  
-   [Gniazda systemu Windows: przykład gniazd korzystających z archiwów](../mfc/windows-sockets-example-of-sockets-using-archives.md)  
  
-   [Gniazda systemu Windows: jak działają gniazda z archiwami](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Gniazda systemu Windows: używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Gniazda systemu Windows: wyprowadzanie z klas gniazd](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Gniazda systemu Windows: powiadomienia dotyczące gniazd](../mfc/windows-sockets-socket-notifications.md)  
  
-   [Gniazda systemu Windows: blokowanie](../mfc/windows-sockets-blocking.md)  
  
-   [Gniazda systemu Windows: określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Gniazda systemu Windows: konwertowanie ciągów](../mfc/windows-sockets-converting-strings.md)  
  
-   [Gniazda systemu Windows: porty i adresy gniazd](../mfc/windows-sockets-ports-and-socket-addresses.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Gniazda systemu Windows](../mfc/windows-sockets.md)

