---
title: Odczytywanie i zapisywanie danych pliku
ms.date: 11/04/2016
helpviewer_keywords:
- CFile class [MFC], objects
- examples [MFC], reading files
- files [MFC], writing to
- examples [MFC], writing to files
- files [MFC], reading
- MFC, file operations
- CFile class [MFC], reading and writing CFile objects
- reading files
- writing to files [MFC]
ms.assetid: cac0c826-ba56-495f-99b3-ce6336f65763
ms.openlocfilehash: f68fd5c48bce214329437cc13fc39da0c3ca7d2b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228586"
---
# <a name="reading-and-writing-files"></a>Odczytywanie i zapisywanie danych pliku

Jeśli użyto funkcji obsługi plików biblioteki wykonawczej języka C, operacje odczytu i zapisu MFC będą wyświetlane jako znane. W tym artykule opisano odczyt bezpośrednio z i zapis bezpośrednio do `CFile` obiektu. Można również wykonywać buforowane we/wy pliku za pomocą klasy [CArchive](../mfc/reference/carchive-class.md) .

#### <a name="to-read-from-and-write-to-the-file"></a>Aby odczytać i zapisać w pliku

1. Użyj `Read` funkcji i, `Write` aby odczytywać i zapisywać dane w pliku.

     -lub-

1. `Seek`Funkcja członkowska jest również dostępna do przejścia do określonego przesunięcia w pliku.

`Read`przyjmuje wskaźnik do buforu i liczbę bajtów do odczytania i zwraca rzeczywistą liczbę odczytanych bajtów. Jeśli wymagana liczba bajtów nie może zostać odczytana, ponieważ zostanie osiągnięty koniec pliku (EOF), zwracana jest rzeczywista liczba odczytanych bajtów. Jeśli wystąpi błąd odczytu, zostanie zgłoszony wyjątek. `Write`jest podobny do `Read` , ale liczba zapisanych bajtów nie jest zwracana. Jeśli wystąpi błąd zapisu, łącznie z niepisaniem wszystkich określonych bajtów, zgłaszany jest wyjątek. Jeśli masz prawidłowy `CFile` obiekt, możesz go odczytać lub zapisać w nim, jak pokazano w następującym przykładzie:

[!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]

> [!NOTE]
> Zwykle powinny być wykonywane operacje wejścia/wyjścia w **`try`** / **`catch`** bloku obsługi wyjątków. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków (MFC)](../mfc/exception-handling-in-mfc.md).

## <a name="see-also"></a>Zobacz także

[Plikach](../mfc/files-in-mfc.md)
