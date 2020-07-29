---
title: 'Windows Sockets: przykład gniazd korzystających z archiwów'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
ms.openlocfilehash: 275a6c274648225fedcec9d42c280f77af68158e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226779"
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows Sockets: przykład gniazd korzystających z archiwów

W tym artykule przedstawiono przykład użycia klasy [CSocket](../mfc/reference/csocket-class.md). W przykładzie zastosowano `CArchive` obiekty do serializacji danych za pomocą gniazda. Należy zauważyć, że nie jest to Serializacja dokumentu do lub z pliku.

Poniższy przykład ilustruje sposób użycia archiwum do wysyłania i odbierania danych za pomocą `CSocket` obiektów. Przykład został zaprojektowany tak, aby dwa wystąpienia aplikacji (na tym samym komputerze lub na różnych komputerach w sieci) wymieniali dane. Jedno wystąpienie wysyła dane, które drugie wystąpienie odbiera i potwierdza. Aplikacja może inicjować wymianę i może działać jako serwer lub jako klient dla innej aplikacji. Następująca funkcja jest zdefiniowana w klasie widoku aplikacji:

[!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]

Najważniejszym elementem tego przykładu jest to, że jego struktura jest równoległa do `Serialize` funkcji MFC. `PacketSerialize`Funkcja członkowska składa się z **`if`** instrukcji z **`else`** klauzulą. Funkcja otrzymuje dwa odwołania [CArchive](../mfc/reference/carchive-class.md) jako parametry: *arData* i *arAck*. Jeśli obiekt archiwum *arData* jest ustawiony do przechowywania (wysyłania), gałąź jest **`if`** wykonywana; w przeciwnym razie, jeśli *arData* jest ustawiona na potrzeby ładowania (otrzymywanie), funkcja przyjmuje **`else`** gałąź. Aby uzyskać więcej informacji na temat serializacji w MFC, zobacz [serializacji](../mfc/how-to-make-a-type-safe-collection.md).

> [!NOTE]
> Założono, że obiekt archiwum *arAck* jest przeciwieństwem elementu *arData*. Jeśli *arData* jest do wysłania, *arAck* odbiera i ma wartość true.

W przypadku operacji wysyłania Przykładowa pętla działa przez określoną liczbę razy, za każdym razem, gdy w celach demonstracyjnych są generowane pewne dane losowe. Aplikacja będzie uzyskiwać prawdziwe dane z niektórych źródeł, takich jak plik. Operator wstawiania Archiwum *arData* () służy **<<** do wysyłania strumienia trzech kolejnych fragmentów danych:

- "Nagłówek", który określa charakter danych (w tym przypadku wartość zmiennej *bValue* oraz liczbę kopii do wysłania).

   Oba elementy są generowane losowo dla tego przykładu.

- Określona liczba kopii danych.

   **`for`** Pętla wewnętrzna wysyła *bValue* określoną liczbę razy.

- Ciąg o nazwie *strText* , który odbiorca wyświetla dla użytkownika.

W przypadku odbioru funkcja działa podobnie, z tą różnicą, że używa operatora wyodrębniania archiwum ( **>>** ) w celu pobierania danych z archiwum. Aplikacja odbierająca weryfikuje otrzymane dane, wyświetla końcowy komunikat "Received", a następnie odsyła komunikat "wysłano", aby można było wyświetlić aplikację wysyłającą.

W tym modelu komunikacyjnym słowo "Received", komunikat wysłany w zmiennej *strText* , jest do wyświetlenia na drugim końcu komunikacji, więc określa użytkownika, że otrzymano określoną liczbę pakietów danych. Odbiorca otrzymuje odpowiedzi o podobnym ciągu "wysłane", aby wyświetlić na ekranie oryginalnego nadawcy. Otrzymanie obu ciągów wskazuje, że wystąpiła pomyślna komunikacja.

> [!CAUTION]
> W przypadku pisania programu klienckiego MFC w celu komunikowania się z ustalonymi serwerami (bez MFC) nie należy wysyłać obiektów C++ za pomocą archiwum. Chyba że serwer jest aplikacją MFC, która zrozumie rodzaje obiektów, które chcesz wysłać, nie będzie można odbierać i deserializować obiektów. Przykład w artykule [Windows Sockets: porządkowanie bajtów](../mfc/windows-sockets-byte-ordering.md) pokazuje komunikację tego typu.

Aby uzyskać więcej informacji, zobacz Specyfikacja Windows Sockets: **htonl**, **htons**, **ntohl**, **ntohs**. Ponadto, aby uzyskać więcej informacji, zobacz:

- [Windows Sockets: wyprowadzanie z klas gniazd](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets: jak działają gniazda z archiwami](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: Tło](../mfc/windows-sockets-background.md)

## <a name="see-also"></a>Zobacz także

[Windows Sockets w MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CArchive:: isprzechowywanie](../mfc/reference/carchive-class.md#isstoring)<br/>
[CArchive:: operator <<](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive:: operator >>](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive:: Flush](../mfc/reference/carchive-class.md#flush)<br/>
[CObject:: serializować](../mfc/reference/cobject-class.md#serialize)
