---
title: Klasy ODBC
ms.date: 11/04/2016
f1_keywords:
- vc.classes.data
helpviewer_keywords:
- database classes [MFC], ODBC
- ODBC classes [MFC]
ms.assetid: 6c40fca8-3033-4873-9abe-7f51725de0e0
ms.openlocfilehash: f0ff337a7193093456ab4f5de2f6087d88ca12df
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518524"
---
# <a name="odbc-classes"></a>Klasy ODBC

Te klasy działają z innych aplikacji framework klasami, aby zapewnić łatwy dostęp do szerokiej gamy baz danych, dla których dostępne są sterowników Open Database Connectivity (ODBC).

Programy, które korzystają z baz danych ODBC będzie mieć co najmniej jeden `CDatabase` obiektu i `CRecordset` obiektu.

[CDatabase](../mfc/reference/cdatabase-class.md)<br/>
Hermetyzuje połączenie ze źródłem danych, dzięki któremu można działać na źródle danych.

[CRecordset](../mfc/reference/crecordset-class.md)<br/>
Hermetyzuje zestaw rekordów wybranych ze źródła danych. Zestawy rekordów włączyć przewijanie między rekordami, aktualizowania rekordów (Dodawanie, edytowanie i usuwanie rekordów), kwalifikujących się zaznaczenie za pomocą filtru, sortowania zaznaczenie i parametryzacja zaznaczenia z informacjami o uzyskany lub obliczane w czasie wykonywania.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Formularz zawiera widok podłączone bezpośrednio do obiektu zestawu rekordów. Danych w oknie dialogowym programu exchange (DDX) mechanizm wymiany danych między zestawu rekordów i kontrolki widoku rekordu. Podobnie jak wszystkie widoki formularzy widoku rekordu zależy od zasobu szablonu okna dialogowego. Widoki rekordów obsługują także przenoszenia między rekordami w zestawie rekordów, aktualizowania rekordów i zamyka skojarzony zestaw rekordów, po zamknięciu widoku rekordu.

[CDBException](../mfc/reference/cdbexception-class.md)<br/>
Wyjątek wyniku przetwarzania błędów dostępu do danych. Ta klasa obsługuje tę samą funkcję co inne klasy wyjątku w mechanizm obsługi wyjątków biblioteki klas.

[CFieldExchange](../mfc/reference/cfieldexchange-class.md)<br/>
Dostarcza informacje o kontekście do obsługi wymiana pól rekordów (RFX), który wymienia dane między elementy członkowskie danych pola i elementy członkowskie danych parametru obiekty zestawów rekordów i odpowiednie kolumny tabeli w źródle danych. Analogiczny do klasy [CDataExchange](../mfc/reference/cdataexchange-class.md), która jest użyta podobnie wymiana danych okna dialogowego (DDX).

## <a name="related-classes"></a>Klasy pokrewne

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
Hermetyzuje dojścia do magazynu w celu duży obiekt binarny (BLOB), takie jak mapy bitowej. `CLongBinary` obiekty są używane do zarządzania obiektami dużych ilości danych przechowywanych w tabelach bazy danych.

[CDBVariant](../mfc/reference/cdbvariant-class.md)<br/>
Służy do przechowywania wartości bez martwienia się o typ danych wartości. `CDBVariant` śledzi bieżącą wartość przechowywaną w Unii typ danych.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

