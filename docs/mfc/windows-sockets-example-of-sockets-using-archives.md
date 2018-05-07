---
title: 'Windows Sockets: Przykład gniazd korzystających z archiwów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02cd74a20f0ccc54a366c1a62d913ee30e72471a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows Sockets: przykład gniazd korzystających z archiwów
W tym artykule przedstawiono przykład za pomocą klasy [CSocket —](../mfc/reference/csocket-class.md). Przykład wykorzystuje `CArchive` obiekty do serializowania danych za pośrednictwem gniazda. Należy pamiętać, że nie jest serializacji dokumentu do lub z pliku.  
  
 Poniższy przykład przedstawia, jak za pomocą archiwum wysyłać i odbierać dane za pośrednictwem `CSocket` obiektów. Przykład zaprojektowano tak, aby dwa wystąpienia aplikacji (na tym samym komputerze lub na różnych komputerach w sieci) wymiany danych. Jedno wystąpienie wysyła dane, co inne wystąpienia odbiera i potwierdzeniu. Aplikacja może inicjować programu exchange, a albo może działać jako serwera lub klienta do innej aplikacji. Następująca funkcja jest zdefiniowany w klasie widoku aplikacji:  
  
 [!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]  
  
 Najważniejsze informacje w tym przykładzie jest, że jego struktury równoleżnikami MFC `Serialize` funkcji. **PacketSerialize** funkcji członkowskiej składa się z **Jeśli** instrukcji z **else** klauzuli. Funkcja otrzymuje dwa [CArchive](../mfc/reference/carchive-class.md) odwołania jako parametry: `arData` i `arAck`. Jeśli `arData` obiekt archiwum jest ustawiony do przechowywania (wysyłającym) **Jeśli** gałęzi wykonuje; w przeciwnym razie, jeśli `arData` jest ustawiona dla obciążenia (odbieranie) Funkcja przyjmuje **else** gałęzi. Aby uzyskać więcej informacji na temat serializacja w MFC, zobacz [szeregowanie](../mfc/how-to-make-a-type-safe-collection.md).  
  
> [!NOTE]
>  `arAck` Obiektu archiwum zakłada, że przeciwieństwem `arData`. Jeśli `arData` jest wysyłania, `arAck` odbierze, i odwrotnej ma wartość true.  
  
 Wysyłanie, funkcja przykład pętli określoną liczbę razy, zawsze generowania niektórych losowe dane w celach demonstracyjnych. Aplikacja może uzyskać prawdziwe dane z określonego źródła, na przykład plik. `arData` Operator wstawiania w archiwum (**<<**) służy do wysyłania strumienia trzech kolejnych fragmentów danych:  
  
-   "Nagłówek", który określa rodzaj danych (w tym przypadku wartości `bValue` zmienną i liczbę kopii zostaną wysłane).  
  
     Obie te pozycje są generowane losowo w tym przykładzie.  
  
-   Określona liczba kopii danych.  
  
     Wewnętrzny **dla** pętli wysyła `bValue` określoną liczbę razy.  
  
-   Ciąg o nazwie `strText` wyświetlającego odbiorniku z użytkownikiem.  
  
 Do odbierania, funkcja działa podobnie, z wyjątkiem tego, aby były używane operator wyodrębniania archiwum (**>>**) można pobrać danych z archiwum. Aplikacja odbierająca sprawdza dane odbierze, wyświetlany jest komunikat "Odebrane" końcowego i następnie przesyła komunikat "Wysłane" wysyłania aplikacji do wyświetlenia.  
  
 W tym modelu łączności słowo "Odebrane" wysłać wiadomości `strText` zmiennej, jest do wyświetlenia na końcu komunikacji, więc określa do odbierania użytkownika otrzymano pewna liczba pakietów danych. Odbiornik odpowiedzi z podobnych ciąg znaków "Wysyłane", do wyświetlenia na ekranie adres oryginalnego nadawcy. Otrzymania oba ciągi wskazuje czy łączność.  
  
> [!CAUTION]
>  Jeśli piszesz program kliencki MFC do komunikacji z serwerami ustalonych (z systemem innym niż MFC) nie należy wysyłać obiektów C++ w archiwum. Chyba, że serwer jest aplikacją MFC obsługującą typy obiektów, które chcesz wysyłać, nie będzie mogła odbierać i deserializacji obiektów. Przykład w artykule [Windows Sockets: Określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md) pokazuje komunikację tego typu.  
  
 Aby uzyskać więcej informacji, zobacz Specyfikacja systemu Windows Sockets: **htonl**, **htons**, **ntohl**, **ntohs**. Aby uzyskać więcej informacji, zobacz też:  
  
-   [Gniazda systemu Windows: wyprowadzanie z klas gniazd](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Gniazda systemu Windows: jak działają gniazda z archiwami](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Gniazda systemu Windows: podstawy](../mfc/windows-sockets-background.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Windows Sockets w MFC](../mfc/windows-sockets-in-mfc.md)   
 [CArchive::IsStoring](../mfc/reference/carchive-class.md#isstoring)   
 [CArchive::operator <<](../mfc/reference/carchive-class.md#operator_lt_lt)   
 [CArchive::operator >>](../mfc/reference/carchive-class.md#operator_lt_lt)   
 [CArchive::Flush](../mfc/reference/carchive-class.md#flush)   
 [CObject::Serialize](../mfc/reference/cobject-class.md#serialize)

