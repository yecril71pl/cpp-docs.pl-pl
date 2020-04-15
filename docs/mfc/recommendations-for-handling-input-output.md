---
title: Zalecenia dotyczące obsługi we/wy
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
ms.openlocfilehash: c365120a385c440f09f0ee4c0a2fc52afb55834f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371733"
---
# <a name="recommendations-for-handling-inputoutput"></a>Zalecenia dotyczące obsługi we/wy

To, czy używasz we/wy opartej na plikach, czy nie, zależy od sposobu odpowiadania na pytania w następującym drzewie decyzyjnym:

**Czy dane podstawowe w aplikacji znajdują się w pliku dysku**

- Tak, dane podstawowe znajdują się w pliku dysku:

   **Czy aplikacja odczytuje cały plik do pamięci na File Open i zapisuje cały plik z powrotem na dysk na Zapisz plik**

  - Tak: Jest to domyślna sprawa dokumentu MFC. Użyj `CDocument` serializacji.

  - Nie: zazwyczaj dotyczy to aktualizacji pliku opartej na transakcjach. Aktualizujesz plik na podstawie transakcji i nie `CDocument` potrzebujesz serializacji.

- Nie, dane podstawowe nie znajdują się w pliku dysku:

   **Czy dane znajdują się w źródle danych ODBC**

  - Tak, dane znajdują się w źródle danych ODBC:

      Użyj obsługi bazy danych MFC. Standardowa implementacja MFC dla `CDatabase` tego przypadku zawiera obiekt, jak omówiono w artykule [MFC: Korzystanie z klas bazy danych z dokumentami i widokami](../data/mfc-using-database-classes-with-documents-and-views.md). Aplikacja może również odczytywać i zapisywać plik pomocniczy — cel opcji kreatora aplikacji "zarówno widok bazy danych, jak i obsługa plików". W takim przypadku należy użyć serializacji dla pliku pomocniczego.

  - Nie, dane nie znajdują się w źródle danych ODBC.

      Przykłady tego przypadku: dane znajdują się w dbms innych niż ODBC; dane są odczytywane za pomocą innego mechanizmu, takiego jak OLE lub DDE.

      W takich przypadkach nie będzie używać serializacji, a aplikacja nie będzie miała elementów menu Otwórz i Zapisz. Nadal można użyć `CDocument` jako bazy głównej, podobnie jak aplikacja OdBC MFC używa `CRecordset` dokumentu do przechowywania obiektów. Ale nie będzie używać domyślnej serializacji dokumentu otwierania/zapisywania plików w ramach.

Aby obsługiwać polecenia Otwórz, Zapisz i Zapisz jako w menu Plik, struktura zapewnia serializację dokumentu. Serializacja odczytuje i zapisuje dane, `CObject`w tym obiekty pochodzące z klasy , do magazynu trwałego, zwykle plik dysku. Serializacja jest łatwa w użyciu i służy wielu twoim potrzebom, ale może być nieodpowiednia w wielu aplikacjach dostępu do danych. Aplikacje dostępu do danych zazwyczaj aktualizują dane dla transakcji. Aktualizują rekordy, których dotyczy transakcja, zamiast odczytywania i zapisywania całego pliku danych naraz.

Aby uzyskać informacje na temat serializacji, zobacz [Serializacja](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Zobacz też

[Serializacja: serializacja a dane wejściowe/wyjściowe bazy danych](../mfc/serialization-serialization-vs-database-input-output.md)
