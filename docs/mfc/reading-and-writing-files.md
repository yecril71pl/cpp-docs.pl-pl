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
ms.openlocfilehash: 6c4b2b21bbfa19fb73997f8475cfa9a4047dc0ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371800"
---
# <a name="reading-and-writing-files"></a>Odczytywanie i zapisywanie danych pliku

Jeśli używano funkcji obsługi plików biblioteki w czasie wykonywania języka C, operacje odczytu i zapisu MFC będą znane. W tym artykule opisano czytanie bezpośrednio `CFile` z i pisanie bezpośrednio do obiektu. Można również wykonać buforowane we/wy pliku z [CArchive](../mfc/reference/carchive-class.md) klasy.

#### <a name="to-read-from-and-write-to-the-file"></a>Aby odczytać i zapisać do pliku

1. Użyj `Read` funkcji `Write` i członków do odczytu i zapisu danych w pliku.

     — lub —

1. Funkcja `Seek` elementu członkowskiego jest również dostępna do przenoszenia do określonego przesunięcia w pliku.

`Read`pobiera wskaźnik do buforu i liczbę bajtów do odczytu i zwraca rzeczywistą liczbę bajtów, które zostały odczytane. Jeśli nie można odczytać wymaganej liczby bajtów z powodu osiągnięcia wartości końcowego pliku (EOF), zwracana jest rzeczywista liczba odczytanych bajtów. Jeśli wystąpi błąd odczytu, zostanie zgłoszony wyjątek. `Write`jest podobny `Read`do , ale liczba bajtów zapisanych nie jest zwracana. Jeśli wystąpi błąd zapisu, w tym nie pisanie wszystkich bajtów określonych, wyjątek. Jeśli masz prawidłowy `CFile` obiekt, możesz odczytać z niego lub zapisać do niego, jak pokazano w poniższym przykładzie:

[!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]

> [!NOTE]
> Zwykle należy przeprowadzić operacje wejścia/wyjścia w ramach bloku obsługi wyjątków **try**/**catch.** Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków (MFC)](../mfc/exception-handling-in-mfc.md).

## <a name="see-also"></a>Zobacz też

[Pliki](../mfc/files-in-mfc.md)
