---
title: Odczyt i zapis plików | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d0fd41c085b9498d3f1ebb76378a83cce464142a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404075"
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

## <a name="see-also"></a>Zobacz też

[Pliki](../mfc/files-in-mfc.md)

