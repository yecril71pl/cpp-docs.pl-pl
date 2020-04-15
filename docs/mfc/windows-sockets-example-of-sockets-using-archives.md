---
title: 'Windows Sockets: przykład gniazd korzystających z archiwów'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
ms.openlocfilehash: 253a65430ae230fbc4deeb9bd5288f28237310d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371085"
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows Sockets: przykład gniazd korzystających z archiwów

W tym artykule przedstawiono przykład użycia klasy [CSocket](../mfc/reference/csocket-class.md). W przykładzie `CArchive` wykorzystuje obiekty do serializacji danych za pośrednictwem gniazda. Należy zauważyć, że nie jest to serializacja dokumentu do lub z pliku.

Poniższy przykład ilustruje sposób używania archiwum `CSocket` do wysyłania i odbierania danych za pośrednictwem obiektów. Przykład jest zaprojektowany tak, aby dwa wystąpienia aplikacji (na tym samym komputerze lub na różnych komputerach w sieci) wymieniać dane. Jedno wystąpienie wysyła dane, które inne wystąpienie odbiera i potwierdza. Każda aplikacja może zainicjować wymianę i może działać jako serwer lub jako klient innej aplikacji. Następująca funkcja jest zdefiniowana w klasie widoku aplikacji:

[!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]

Najważniejszą rzeczą w tym przykładzie jest to, że `Serialize` jego struktura jest równoległa do funkcji MFC. Funkcja `PacketSerialize` elementu członkowskiego składa się z **if** instrukcji z **else** klauzuli. Funkcja odbiera dwa [CArchive](../mfc/reference/carchive-class.md) odwołania jako parametry: *arData* i *arAck*. Jeśli obiekt archiwum *arData* jest ustawiony do przechowywania (wysyłania), **jeśli** gałąź jest wykonywana; w przeciwnym razie, jeśli *arData* jest ustawiona do ładowania (odbierania) funkcja przyjmuje gałąź **else.** Aby uzyskać więcej informacji na temat serializacji w MFC, zobacz [Serializacja](../mfc/how-to-make-a-type-safe-collection.md).

> [!NOTE]
> Zakłada się, że obiekt archiwum *arAck* jest przeciwieństwem *arData*. Jeśli arData jest do *wysyłania,* *arAck* odbiera, a odwrotność jest prawdziwa.

Do wysyłania przykładowe pętle funkcji dla określonej liczby razy, za każdym razem generowania niektórych losowych danych do celów demonstracyjnych. Aplikacja będzie uzyskać rzeczywiste dane z jakiegoś źródła, takich jak plik. Operator wstawiania archiwum danych**<<** *arData* ( ) służy do wysyłania strumienia trzech kolejnych fragmentów danych:

- "Nagłówek", który określa charakter danych (w tym przypadku wartość zmiennej *bValue* i liczbę kopii zostanie wysłanych).

   Oba elementy są generowane losowo w tym przykładzie.

- Określona liczba kopii danych.

   Wewnętrzna **pętla for** wysyła *bWartość* określoną liczbę razy.

- Ciąg o nazwie *strText,* który odbiorca wyświetla jego użytkownikowi.

Do odbierania funkcja działa podobnie, z tą różnicą, że używa**>>** operatora wyodrębniania archiwum ( ) do pobierania danych z archiwum. Aplikacja odbierająca weryfikuje dane, które otrzymuje, wyświetla ostateczną wiadomość "Odebrane", a następnie odsyła komunikat z napisem "Wysłane" dla aplikacji wysyłającej do wyświetlenia.

W tym modelu komunikacji słowo "Odebrane", wiadomość wysłana w zmiennej *strText,* jest wyświetlane na drugim końcu komunikacji, więc określa użytkownikowi odbierającemu, że odebrano określoną liczbę pakietów danych. Odbiorca odpowiada podobnym ciągiem z napisem "Wysłane", aby wyświetlić go na ekranie oryginalnego nadawcy. Odbiór obu ciągów wskazuje, że nastąpiła pomyślna komunikacja.

> [!CAUTION]
> Jeśli piszesz program kliencki MFC do komunikowania się z ustalonymi serwerami (nie-MFC), nie wysyłaj obiektów C++ za pośrednictwem archiwum. Chyba że serwer jest aplikacją MFC, która rozumie rodzaje obiektów, które chcesz wysłać, nie będzie w stanie odbierać i deserializacji obiektów. Przykład w artykule [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md) pokazuje komunikację tego typu.

Aby uzyskać więcej informacji, zobacz Windows Sockets Specyfikacja: **htonl**, **htons**, **ntohl**, **ntohs**. Aby uzyskać więcej informacji, zobacz:

- [Gniazda systemu Windows: wyprowadzanie z klas gniazd](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets: jak działają gniazda z archiwami](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Gniazda systemu Windows: podstawy](../mfc/windows-sockets-background.md)

## <a name="see-also"></a>Zobacz też

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CArchive::IsStoring](../mfc/reference/carchive-class.md#isstoring)<br/>
[CArchive::operator <<](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::operator >>](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::Flush](../mfc/reference/carchive-class.md#flush)<br/>
[CObject::Serialize](../mfc/reference/cobject-class.md#serialize)
