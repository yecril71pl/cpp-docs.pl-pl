---
title: Zalecenia dotyczące obsługi We / Wy
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
ms.openlocfilehash: 760c213c3af7f9c75374f04e3dfc6b9499eade5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218567"
---
# <a name="recommendations-for-handling-inputoutput"></a>Zalecenia dotyczące obsługi we/wy

Czy używasz opartych na plikach we/wy lub nie zależy od tego, jak odpowiadać na pytania w poniższym drzewie decyzyjnym:

**Podstawowym danych w aplikacji znajdują się w pliku na dysku**

- Tak, podstawowe dane znajdują się w pliku na dysku:

     **Czy aplikacja wczytać całego pliku do pamięci na otwieranie pliku i zapisywać cały plik na dysku na zapisywanie pliku**

   - Tak: Jest to dokument domyślny MFC. Użyj `CDocument` serializacji.

   - Nie: Zazwyczaj jest to przypadek, opartej na transakcjach aktualizowania pliku. Zaktualizuj plik na podstawie każdej transakcji które nie potrzebują `CDocument` serializacji.

- Nie, podstawowe nie znajdują się w pliku na dysku:

     **Dane znajdują się w źródle danych ODBC**

   - Tak, dane znajdują się w źródle danych ODBC:

         Use MFC's database support. The standard MFC implementation for this case includes a `CDatabase` object, as discussed in the article [MFC: Using Database Classes with Documents and Views](../data/mfc-using-database-classes-with-documents-and-views.md). The application might also read and write an auxiliary file — the purpose of the application wizard "both a database view and file support" option. In this case, you'd use serialization for the auxiliary file.

   - Nie, dane nie znajdują się w źródle danych ODBC.

         Examples of this case: the data resides in a non-ODBC DBMS; the data is read via some other mechanism, such as OLE or DDE.

         In such cases, you won't use serialization, and your application won't have Open and Save menu items. You might still want to use a `CDocument` as a home base, just as an MFC ODBC application uses the document to store `CRecordset` objects. But you won't use the framework's default File Open/Save document serialization.

Na potrzeby obsługi Otwórz, Zapisz i Zapisz jako polecenia w menu Plik, struktura udostępnia serializacja dokumentu. Serializacja odczytuje i zapisuje dane, w tym obiekty pochodzi od klasy `CObject`, do trwałego magazynu, zwykle pliku na dysku. Serializacja jest łatwa w użyciu i obsługuje wiele wymagań, ale może być nieodpowiedni w wielu aplikacjach dostęp do danych. Dostęp do danych aplikacji zazwyczaj aktualizacji danych na podstawie każdej transakcji. Zaktualizowanie rekordów wpływ transakcji, a nie odczytywanie i zapisywanie pliku danych całą jednocześnie.

Aby uzyskać informacje o serializacji, zobacz [serializacji](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Zobacz także

[Serializacja: Serializacja programu vs. Dane wejściowe/wyjściowe bazy danych](../mfc/serialization-serialization-vs-database-input-output.md)
