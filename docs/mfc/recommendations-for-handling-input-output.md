---
title: Zalecenia dotyczące obsługi We Wy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ee88b7784abb6ca622e72a9dfb31efc39fa7816
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930943"
---
# <a name="recommendations-for-handling-inputoutput"></a>Zalecenia dotyczące obsługi we/wy
Przy użyciu operacji We/Wy na podstawie pliku lub nie zależy od tego, jak odpowiedzieć na pytania w następującym algorytmem:  
  
 **Podstawowy danych w aplikacji znajdują się w pliku na dysku**  
  
-   Tak, podstawowe znajduje się w pliku na dysku:  
  
     **Aplikacji wczytać całego pliku do pamięci na otwieranie pliku i ponownie zapisać cały plik na dysku na zapisywanie pliku**  
  
    -   Tak: Jest to domyślny MFC dokumentu. Użyj `CDocument` szeregowanie.  
  
    -   Nie: To jest typowe w przypadku opartej na transakcjach aktualizacji pliku. Zaktualizuj plik na podstawie każdą transakcję i nie wymagają `CDocument` szeregowanie.  
  
-   Nie, podstawowe nie znajdują się w pliku na dysku:  
  
     **Dane ma w źródle danych ODBC**  
  
    -   Tak, dane znajdują się w źródle danych ODBC:  
  
         Użyj MFC obsługi bazy danych. Standardowa implementacja MFC dla tego przypadku obejmuje `CDatabase` obiektu, zgodnie z opisem w artykule [MFC: przy użyciu klasy baz danych z dokumentami i widokami](../data/mfc-using-database-classes-with-documents-and-views.md). Aplikacja może również Odczyt i zapis plików pomocniczych — celem Kreatora aplikacji opcję "obsługuje zarówno widoku bazy danych, jak i plik". W takim przypadku użyje serializacji dla dodatkowego pliku.  
  
    -   Nie, danych nie znajdują się w źródle danych ODBC.  
  
         Przykładem tego przypadku: dane znajdują się w innej niż — ODBC DBMS; dane są odczytywane za pomocą innego mechanizmu, takiego jak OLE lub DDE.  
  
         W takich przypadkach nie będzie można użyć serializacji, a aplikacja nie będzie otwarte i zapisać elementów menu. Można nadal używać `CDocument` jako podstawa głównej, podobnie jak MFC ODBC aplikacja używa dokumentu do przechowywania `CRecordset` obiektów. Ale nie będzie używać w ramach domyślnego pliku Otwórz/Zapisz dokument serializacji.  
  
 Do obsługi otwartej, Zapisz i Zapisz jako polecenia w menu Plik, framework zapewnia serializacji dokumentu. Serializacja odczytuje i zapisuje dane, wraz z jej obiektami pochodzi od klasy `CObject`, stałe do magazynu, zwykle pliku na dysku. Serializacja jest łatwy w użyciu i obsługuje wiele potrzeb, ale może być nieodpowiednie w wiele aplikacji dostęp do danych. Dostęp do danych aplikacji zazwyczaj aktualizacji danych na podstawie każdą transakcję. Zaktualizowanie zmodyfikowanych transakcji zamiast odczytywania i zapisywania pliku danych całego jednocześnie rekordów.  
  
 Aby uzyskać informacje o serializacji, zobacz [szeregowanie](../mfc/serialization-in-mfc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja: serializacja a Bazy danych we/wy](../mfc/serialization-serialization-vs-database-input-output.md)
