---
title: 'Windows Sockets: Określanie kolejności bajtów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18fc3f586c7fc8861bfc29dade7b62e741bb0ffc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="windows-sockets-byte-ordering"></a>Windows Sockets: określanie kolejności bajtów
W tym artykule i dwa artykuły pomocnika opisano kilka problemów w programowaniu Windows Sockets. W tym artykule omówiono określanie kolejności bajtów. Inne problemy zostały omówione w artykułach: [Windows Sockets: Blokowanie](../mfc/windows-sockets-blocking.md) i [Windows Sockets: Konwertowanie ciągów](../mfc/windows-sockets-converting-strings.md).  
  
 Jeśli jest używany lub pochodzi z klasy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), musisz samodzielnie zarządzania tymi problemami. Jeśli jest używany lub pochodzi z klasy [CSocket —](../mfc/reference/csocket-class.md), MFC zarządza nimi automatycznie.  
  
## <a name="byte-ordering"></a>Określanie kolejności bajtów  
 Architektura różnych komputerów są przechowywane danych przy użyciu różnych bajtów zleceń. Na przykład maszyn opartych na Intel przechowywanie danych w odwrotnej kolejności komputery Macintosh (firmie). Kolejność bajtów firmy Intel, nazywany "little-Endian," jest również odwrotna kolejność "big Endian" standardowe sieci. W poniższej tabeli przedstawiono te warunki.  
  
### <a name="big--and-little-endian-byte-ordering"></a>Określanie kolejności bajtów big - i Little-Endian  
  
|Określanie kolejności bajtów|Znaczenie|  
|-------------------|-------------|  
|Big Endian|Najbardziej znaczący bajt jest z lewej strony słów.|  
|Little Endian|Najbardziej znaczący bajt jest na prawym końcu wyrazu.|  
  
 Zazwyczaj nie trzeba martwić o kolejność bajtów konwersji dane są wysyłane i odbierane za pośrednictwem sieci, ale istnieją sytuacje, w których należy przekonwertować bajtów zleceń.  
  
## <a name="when-you-must-convert-byte-orders"></a>Gdy należy przekonwertować zamówień bajtów  
 Należy przekonwertować bajtów zamówień w następujących sytuacjach:  
  
-   Jest przekazanie informacji, który musi zostać zinterpretowany przez sieć, a nie dane, które są wysyłane na innym komputerze. Na przykład może przekazać porty i adresy, które należy zrozumieć sieci.  
  
-   Aplikacja serwera, z którym komunikacji nie jest aplikacji MFC (i nie ma kodu źródłowego dla niego). Powoduje to wywołanie podczas konwersji kolejności bajtów, jeśli dwa komputery nie mają tej samej kolejności bajtów.  
  
## <a name="when-you-do-not-have-to-convert-byte-orders"></a>Jeśli nie masz można przekonwertować bajtów zlecenia  
 Można uniknąć pracy Konwertowanie zamówień bajtów w następujących sytuacjach:  
  
-   Maszyny po obu stronach można zaakceptować nie wymiany bajtów i obie maszyny używać tej samej kolejności bajtów.  
  
-   Serwer, którego komunikują się z jest aplikacji MFC.  
  
-   Masz kod źródłowy dla serwera, który jest komunikacji, dzięki czemu można sprawdzić jawnie czy należy przekonwertować bajtów zamówień lub nie.  
  
-   Można portu serwerowi MFC. Jest dość łatwo zrobić, a wynik jest zwykle mniejszy, szybszy kodu.  
  
 Praca z [CAsyncSocket](../mfc/reference/casyncsocket-class.md), możesz jakiejkolwiek konwersji konieczne kolejności bajtów należy zarządzać. Windows Sockets standaryzuje modelu kolejności bajtów "big Endian" i zawiera funkcje, które umożliwia konwersję pomiędzy to zamówienie i inne. [CArchive —](../mfc/reference/carchive-class.md), jednak używanego z [CSocket —](../mfc/reference/csocket-class.md), używa przeciwnej kolejności ("little-Endian"), ale `CArchive` zajmuje się szczegóły konwersje kolejności bajtów dla Ciebie. Za pomocą tego standardowego kolejności w aplikacji lub przy użyciu funkcji konwersji kolejności bajtów Windows Sockets, możesz wprowadzić kod przenośną.  
  
 Jest idealne rozwiązanie w przypadku używanie gniazd MFC podczas pisania obu końców komunikacji: używanie MFC obu końców. Jeśli piszesz aplikację, która będzie komunikować się z innego typu niż MFC aplikacji, takich jak serwer FTP, prawdopodobnie będzie konieczne zarządzanie wymienianie bajtów samodzielnie przed przekazywania danych do obiektu archiwum przy użyciu procedury konwersji Windows Sockets **ntohs**, **ntohl**, **htons**, i **htonl**. Te funkcje używane w komunikacji z aplikacją innego typu niż MFC jest wyświetlany w dalszej części tego artykułu.  
  
> [!NOTE]
>  Po drugim końcu komunikacja nie jest aplikacją MFC, możesz również należy unikać przesyłania strumieniowego C++ obiektów pochodzących od `CObject` do archiwum ponieważ odbiornik nie będzie mógł je obsłużyć. Zobacz sekcję Uwaga w [Windows Sockets: przy użyciu gniazda z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md).  
  
 Aby uzyskać więcej informacji na temat zamówień bajtów zobacz specyfikację Windows Sockets, dostępne w zestawie Windows SDK.  
  
## <a name="a-byte-order-conversion-example"></a>Przykład konwersji kolejności bajtów  
 Poniższy przykład przedstawia funkcję serializacji dla `CSocket` obiekt, który korzysta z archiwum. Przedstawiono również, przy użyciu funkcji konwersji kolejności bajtów w interfejsie API Windows Sockets.  
  
 W tym przykładzie przedstawiono scenariusz, w którym pisania klienta, który komunikuje się z innego typu niż MFC aplikacji serwera, dla których nie masz dostępu do kodu źródłowego. W tym scenariuszu należy założono, kolejność bajtów standardowe sieci używane przez serwer z systemem innym niż MFC. Z kolei używa aplikacja kliencka MFC `CArchive` obiekt z `CSocket` obiektu i `CArchive` używa kolejność bajtów "little Endian", przeciwieństwem standardowe sieci.  
  
 Załóżmy, że serwer innego typu niż MFC, z którego planujesz do komunikowania się ma ustanowić protokołu pakietu komunikat podobne do poniższych:  
  
 [!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]  
  
 Warunków MFC to może być wyrażona w następujący sposób:  
  
 [!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]  
  
 W języku C++ `struct` jest zasadniczo samym co klasa. `Message` Struktura może mieć funkcji elementów członkowskich, takich jak `Serialize` funkcja członkowska zadeklarowana powyżej. `Serialize` Funkcji członkowskiej może wyglądać następująco:  
  
 [!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]  
  
 W tym przykładzie odwołuje się do konwersji kolejności bajtów danych, ponieważ wystąpiła niezgodność wyczyść między kolejności bajtów aplikacji serwera z systemem innym niż MFC z jednej strony i `CArchive` używane w aplikacji klienta MFC w drugim zakończeniu. Pokazano w przykładzie kilka funkcji konwersji kolejności bajtów, które dostarcza Windows Sockets. W poniższej tabeli opisano te funkcje.  
  
### <a name="windows-sockets-byte-order-conversion-functions"></a>Windows Sockets kolejności bajtów funkcje konwersji  
  
|Funkcja|Cel|  
|--------------|-------------|  
|**ntohs**|Konwertowanie ilość 16-bitowych kolejności bajtów sieci na hoście kolejności bajtów (big-Endian na little Endian).|  
|**ntohl**|Konwertowanie ilość 32-bitowych kolejności bajtów sieci na hosta kolejności bajtów (big-Endian na little Endian).|  
|**Htons**|Konwertowanie ilość 16-bitowych kolejności bajtów hosta na kolejność bajtów sieci (little-Endian do big Endian).|  
|**Htonl**|Konwertowanie ilość 32-bitowych kolejności bajtów hosta na kolejność bajtów sieci (little-Endian do big Endian).|  
  
 Inny punkt, w tym przykładzie jest że gdy aplikacja gniazda na drugim końcu komunikacji jest aplikacją innego typu niż MFC, użytkownik musi unikać postać zbliżoną do następującej:  
  
 `ar << pMsg;`  
  
 gdzie `pMsg` wskaźnik do obiektu C++ pochodzi od klasy `CObject`. To spowoduje wysłanie dodatkowych informacji MFC związane z obiektami i serwer nie będzie zrozumiałe, jak gdyby aplikacji MFC.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Gniazda systemu Windows: używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Gniazda systemu Windows: podstawy](../mfc/windows-sockets-background.md)  
  
-   [Gniazda systemu Windows: gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Gniazda systemu Windows: gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)

