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
ms.openlocfilehash: ab1ddc58ec6cc2b67e5843f46afbead3ead54eba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324262"
---
# <a name="reading-and-writing-files"></a>Odczytywanie i zapisywanie danych pliku

Jeśli używano funkcji obsługi plików biblioteki wykonawczej języka C, MFC, operacji odczytu i zapisu pojawi się zapoznać. W tym artykule opisuje odczytywanie bezpośrednio z oraz zapisywanie bezpośrednio do `CFile` obiektu. Użytkownik może również buforowane operacji We/Wy pliku przy użyciu [CArchive](../mfc/reference/carchive-class.md) klasy.

#### <a name="to-read-from-and-write-to-the-file"></a>Aby odczytywać i zapisywać do pliku

1. Użyj `Read` i `Write` funkcji elementów członkowskich, aby odczytywać i zapisywać dane w pliku.

     —lub—

1. `Seek` Funkcja elementu członkowskiego jest również dostępna dotyczące przechodzenia na określone przesunięcie w pliku.

`Read` pobiera wskaźnik do buforu i liczby bajtów do odczytania i zwraca rzeczywista liczba bajtów, które zostały odczytane. Jeśli wymagana liczba bajtów nie można odczytać, ponieważ plik końcowy (EOF) zostanie osiągnięty, zwracany jest rzeczywista liczba odczytanych bajtów. Jeśli wystąpi jakiś błąd odczytu, jest zgłaszany wyjątek. `Write` jest podobny do `Read`, ale nie jest zwracana liczba zapisanych bajtów. Jeśli wystąpi błąd, w tym bez zapisywania wszystkich bajtów, które są określone, jest zgłaszany wyjątek. Jeśli masz prawidłową `CFile` obiektu można odczytać z niego lub zapisanie w nim jak pokazano w poniższym przykładzie:

[!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]

> [!NOTE]
>  Zwykle należy przeprowadzić operacji wejścia/wyjścia w ramach **spróbuj**/**catch** bloku obsługi wyjątków. Aby uzyskać więcej informacji, zobacz [obsługi wyjątków (MFC)](../mfc/exception-handling-in-mfc.md).

## <a name="see-also"></a>Zobacz także

[Pliki](../mfc/files-in-mfc.md)
