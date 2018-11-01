---
title: 'Windows Sockets: przykład gniazd korzystających z archiwów'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
ms.openlocfilehash: 285053c79b13ebea23aedc7dae52eabe85f55a12
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436273"
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows Sockets: przykład gniazd korzystających z archiwów

W tym artykule przedstawiono przykład użycia klasy [CSocket](../mfc/reference/csocket-class.md). Przykład wykorzystuje `CArchive` obiekty do serializowania danych za pośrednictwem gniazd. Należy pamiętać, że nie jest serializacja dokumentu do lub z pliku.

W poniższym przykładzie pokazano, jak używać archiwum do wysyłania i odbierania danych za pośrednictwem `CSocket` obiektów. Przykład jest zaprojektowana tak, że dwa wystąpienia aplikacji (w tym samym komputerze lub na różnych komputerach w sieci) wymiany danych. Jedno wystąpienie wysyła dane, które inne wystąpienie odbiera i przyjmuje do wiadomości. Aplikacja może zainicjować wymiany i albo może działać jako serwer lub klienta do innej aplikacji. Następująca funkcja jest zdefiniowana w klasie widoku aplikacji:

[!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]

Najważniejsze informacje w tym przykładzie jest, że jego strukturę równoleżnikami MFC `Serialize` funkcji. `PacketSerialize` Funkcja elementu członkowskiego, który składa się z **Jeśli** instrukcję, określając **else** klauzuli. Funkcja otrzymuje dwa [CArchive](../mfc/reference/carchive-class.md) odwołania jako parametry: *arData* i *arAck*. Jeśli *arData* archiwum obiekt jest ustawiony do przechowywania (wysyłającym) **Jeśli** gałęzi wykonuje; w przeciwnym razie, jeśli *arData* jest ustawiona dla obciążenia (odbieranie) Funkcja przyjmuje **else** gałęzi. Aby uzyskać więcej informacji na temat serializacja w MFC, zobacz [serializacji](../mfc/how-to-make-a-type-safe-collection.md).

> [!NOTE]
>  *ArAck* obiektu archiwum będzie traktowana jako przeciwieństwo *arData*. Jeśli *arData* jest wysyłana, *arAck* odbierze, i wartość true, jest to prawdą.

Wysyłanie, aby uzyskać przykład funkcja w pętli określoną liczbę razy, za każdym razem, generowania kilka losowych danych dla celów demonstracyjnych. Aplikacja będzie uzyskać prawdziwe dane z określonego źródła, takiego jak plik. *ArData* operator wstawiania archiwum (**<<**) służy do wysyłania strumienia trzech kolejnych fragmentów danych:

- "header", który określa rodzaj danych (w tym przypadku wartość *bDane wartości* zmienną i będą wysyłane liczbę kopii).

   Oba elementy są generowane losowo w tym przykładzie.

- Określona liczba kopii danych.

   Wewnętrzny **dla** pętla wysyła *bDane wartości* określoną liczbę razy.

- Ciąg o nazwie *strText* wyświetlającą odbiornika z użytkownikiem.

Do odbierania, funkcja działa podobnie, z tą różnicą, że używa operatora wyodrębniania archiwum (**>>**) można pobrać danych z archiwum. Aplikacja odbierająca sprawdza dane odbierze, wyświetla komunikat końcowy "Odebrane" i następnie wysyła z powrotem komunikat z informacją "Wysłane" wysyłania aplikacji do wyświetlenia.

W tym modelu łączności słowo "Odebrane" wysłana wiadomość *strText* zmiennej, jest do wyświetlenia na drugim końcu komunikacji, więc określa odbieranie użytkownika zostały pewne pakiety danych odebrane. Odbiornik odpowiedzi przy użyciu podobnych ciąg, który jest wyświetlany komunikat "Wysłano", do wyświetlenia na ekranie oryginalnego nadawcy. Otrzymania obu ciągów wskazuje że pomyślnej komunikacji.

> [!CAUTION]
>  Jeśli piszesz program kliencki MFC do komunikacji z serwerami ustanowionych (inne niż MFC), nie będą wysyłane obiektów C++ w archiwum. Serwer nie działa aplikacji MFC, która rozumie rodzaje obiektów, które chcesz wysłać, nie będzie mogła odbierać i deserializacji obiektów. Przykład w artykule [Windows Sockets: Określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md) pokazuje komunikat tego typu.

Aby uzyskać więcej informacji, zobacz Windows Sockets specyfikacji: **htonl**, **htons**, **ntohl**, **ntohs**. Aby uzyskać więcej informacji, zobacz też:

- [Gniazda systemu Windows: wyprowadzanie z klas gniazd](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Gniazda systemu Windows: jak działają gniazda z archiwami](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Gniazda systemu Windows: podstawy](../mfc/windows-sockets-background.md)

## <a name="see-also"></a>Zobacz też

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CArchive::IsStoring](../mfc/reference/carchive-class.md#isstoring)<br/>
[CArchive::operator <<](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::operator >>](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::Flush](../mfc/reference/carchive-class.md#flush)<br/>
[CObject::Serialize](../mfc/reference/cobject-class.md#serialize)

