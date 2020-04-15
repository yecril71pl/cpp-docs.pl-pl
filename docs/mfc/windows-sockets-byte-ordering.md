---
title: 'Windows Sockets: określanie kolejności bajtów'
ms.date: 11/04/2016
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
ms.openlocfilehash: 50548202483c4d9d4471ad2c600270c4df4503e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371065"
---
# <a name="windows-sockets-byte-ordering"></a>Windows Sockets: określanie kolejności bajtów

W tym artykule i dwóch artykułach towarzyszących wyjaśniono kilka problemów związanych z programowaniem w systemach Windows Sockets. W tym artykule omówiono zamawianie bajtów. Inne problemy są omówione w artykułach: [Windows Sockets: Blokowanie](../mfc/windows-sockets-blocking.md) i [Windows Sockets: Konwersja ciągów](../mfc/windows-sockets-converting-strings.md).

Jeśli używasz lub pochodzisz z klasy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), musisz samodzielnie zarządzać tymi problemami. Jeśli używasz lub pochodzisz z klasy [CSocket](../mfc/reference/csocket-class.md), MFC zarządza nimi za Ciebie.

## <a name="byte-ordering"></a>określanie kolejności bajtów

Różne architektury maszyn czasami przechowują dane przy użyciu różnych zamówień bajtów. Na przykład maszyny z procesorem Intel przechowują dane w odwrotnej kolejności komputerów Macintosh (Motorola). Kolejność bajtów Intela, zwana "little-Endian", jest również odwrotnością standardowego porządku sieciowego "big-Endian". W poniższej tabeli wyjaśniono te terminy.

### <a name="big--and-little-endian-byte-ordering"></a>Duże i Mało-Endian Byte Zamawianie

|określanie kolejności bajtów|Znaczenie|
|-------------------|-------------|
|Big-Endian (Big-Endian)|Najważniejszy bajt znajduje się po lewej stronie wyrazu.|
|Mały Endian|Najważniejszy bajt znajduje się po prawej stronie wyrazu.|

Zazwyczaj nie musisz się martwić o konwersję kolejności bajtów dla danych wysyłanych i odbieranych za pośrednictwem sieci, ale zdarzają się sytuacje, w których należy konwertować zamówienia bajtów.

## <a name="when-you-must-convert-byte-orders"></a>Kiedy należy przekonwertować zamówienia bajtów

Zamówienia bajtów należy przekonwertować w następujących sytuacjach:

- Przekazujesz informacje, które muszą być interpretowane przez sieć, w przeciwieństwie do danych wysyłanych do innego komputera. Na przykład można przekazać porty i adresy, które sieć musi zrozumieć.

- Aplikacja serwera, z którą się komunikujesz, nie jest aplikacją MFC (i nie masz dla niej kodu źródłowego). Wymaga to konwersji kolejności bajtów, jeśli dwie maszyny nie współużytkują tej samej kolejności bajtów.

## <a name="when-you-do-not-have-to-convert-byte-orders"></a>Kiedy nie trzeba konwertować zamówień bajtowych

Można uniknąć pracy konwersji zamówień bajtów w następujących sytuacjach:

- Maszyny na obu końcach mogą zgodzić się nie wymieniać bajtów, a obie maszyny używają tego samego zamówienia bajtowego.

- Serwer, z którego komunikujesz się, jest aplikacją MFC.

- Masz kod źródłowy dla serwera, z którego komunikujesz się, dzięki czemu można jednoznacznie powiedzieć, czy należy konwertować zamówienia bajtów, czy nie.

- Serwer można przenieść do MFC. Jest to dość łatwe do zrobienia, a wynik jest zwykle mniejszy, szybszy kod.

Praca z [CAsyncSocket](../mfc/reference/casyncsocket-class.md), należy samodzielnie zarządzać wszelkimi niezbędnymi konwersjami bajtów. Windows Sockets standaryzuje model "big-Endian" byte-order i udostępnia funkcje do konwersji między tą kolejnością a innymi. [CArchive](../mfc/reference/carchive-class.md), jednak, który używasz z [CSocket](../mfc/reference/csocket-class.md), używa odwrotnej ("little-Endian") kolejność, ale `CArchive` dba o szczegóły konwersji bajtów zamówienia dla Ciebie. Korzystając z tej standardowej kolejności w aplikacjach lub przy użyciu funkcji konwersji bajtów w systemie Windows Sockets, można uczynić kod bardziej przenośnym.

Idealnym przypadkiem przy użyciu gniazd MFC jest podczas pisania obu końcach komunikacji: przy użyciu MFC na obu końcach. Jeśli piszesz aplikację, która będzie komunikować się z aplikacjami innych niż MFC, takich jak serwer FTP, prawdopodobnie trzeba będzie zarządzać bajt-swapping siebie przed przekazaniem danych do obiektu archiwum, za pomocą procedur konwersji Windows Sockets **ntohs**, **ntohl**, **htons**i **htonl**. Przykład tych funkcji używanych w komunikacji z aplikacją nie MFC pojawia się w dalszej części tego artykułu.

> [!NOTE]
> Gdy drugi koniec komunikacji nie jest aplikacją MFC, należy również unikać przesyłania `CObject` strumieniowego obiektów języka C++ pochodzących z archiwum, ponieważ odbiorca nie będzie w stanie ich obsłużyć. Zobacz notatkę w windows [sockets: Using Sockets with Archives](../mfc/windows-sockets-using-sockets-with-archives.md).

Aby uzyskać więcej informacji na temat zamówień bajtów, zobacz specyfikację windows sockets dostępną w zestaw Windows SDK.

## <a name="a-byte-order-conversion-example"></a>Przykład konwersji kolejności bajtowej

W poniższym przykładzie przedstawiono `CSocket` funkcję serializacji dla obiektu, który używa archiwum. Ilustruje również przy użyciu funkcji konwersji kolejności bajtów w interfejsie API windows sockets.

W tym przykładzie przedstawiono scenariusz, w którym piszesz klienta, który komunikuje się z aplikacją serwera innych niż MFC, dla których nie masz dostępu do kodu źródłowego. W tym scenariuszu należy założyć, że serwer nie MFC używa standardowej kolejności bajtów sieciowych. Natomiast aplikacja kliencka MFC `CArchive` używa obiektu `CSocket` z `CArchive` obiektem i używa "little-Endian" kolejność bajtów, przeciwieństwo standardu sieci.

Załóżmy, że serwer nienawiązany do MFC, z którym zamierzasz się komunikować, ma ustalony protokół dla pakietu wiadomości, podobny do następującego:

[!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]

W kategoriach MFC, byłoby to wyrażone w następujący sposób:

[!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]

W języku C++ **struktura** jest zasadniczo taka sama jak klasa. Struktura `Message` może mieć funkcje członkowskie, takie jak funkcja `Serialize` elementu członkowskiego zadeklarowana powyżej. Funkcja `Serialize` elementu członkowskiego może wyglądać następująco:

[!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]

W tym przykładzie wywołania konwersji danych w kolejności bajtów, ponieważ istnieje wyraźna niezgodność między kolejność bajtów aplikacji serwera innych niż MFC na jednym końcu i `CArchive` używane w aplikacji klienckiej MFC na drugim końcu. W przykładzie przedstawiono kilka funkcji konwersji kolejności bajtów, które dostarcza system Windows Sockets. W poniższej tabeli opisano te funkcje.

### <a name="windows-sockets-byte-order-conversion-functions"></a>Funkcje konwersji kolejności bajtów systemu Windows

|Funkcja|Przeznaczenie|
|--------------|-------------|
|**ntohs**|Konwertuj 16-bitową ilość z zamówienia bajtów sieciowych na zlecenie bajtów hosta (big-Endian na little-Endian).|
|**ntohl ( ntohl )**|Konwertuj 32-bitową ilość z zamówienia bajtów sieciowych na zlecenie bajtów hosta (big-Endian na little-Endian).|
|**Htons ( Htons )**|Konwertuj 16-bitową ilość z zamówienia bajtów hosta na kolejność bajtów sieciowych (little-Endian na big-Endian).|
|**Okręg wyborczy Htonl**|Konwertuj 32-bitową ilość z zamówienia bajtów hosta na kolejność bajtów sieciowych (little-Endian na big-Endian).|

Innym punktem w tym przykładzie jest to, że gdy aplikacja gniazda na drugim końcu komunikacji jest aplikacją inną niż MFC, należy unikać wykonywania czegoś podobnego:

`ar << pMsg;`

gdzie `pMsg` jest wskaźnikiem do obiektu C++ `CObject`pochodzącego z klasy . Spowoduje to wysłanie dodatkowych informacji MFC skojarzonych z obiektami, a serwer nie zrozumie go, tak jak gdyby była to aplikacja MFC.

Aby uzyskać więcej informacji, zobacz:

- [Gniazda systemu Windows: używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Gniazda systemu Windows: podstawy](../mfc/windows-sockets-background.md)

- [Gniazda systemu Windows: gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)

- [Gniazda systemu Windows: gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Zobacz też

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)
