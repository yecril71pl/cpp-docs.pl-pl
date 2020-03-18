---
title: Klasy ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [MFC], ODBC
- ODBC classes [MFC]
ms.assetid: 6c40fca8-3033-4873-9abe-7f51725de0e0
ms.openlocfilehash: a4cfa0d7afa197de7b65b6a0bd6b881a09534ef6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447696"
---
# <a name="odbc-classes"></a>Klasy ODBC

Te klasy współpracują z innymi klasami struktury aplikacji, aby zapewnić łatwy dostęp do różnorodnych baz danych, dla których dostępne są sterowniki Open Database Connectivity (ODBC).

Programy korzystające z baz danych ODBC będą mieć co najmniej obiekt `CDatabase` i obiekt `CRecordset`.

[CDatabase](../mfc/reference/cdatabase-class.md)<br/>
Hermetyzuje połączenie ze źródłem danych, za pomocą którego można pracować na źródle danych.

[CRecordset](../mfc/reference/crecordset-class.md)<br/>
Hermetyzuje zestaw rekordów wybranych ze źródła danych. Zestawy rekordów umożliwiają przewijanie rekordów do rekordu, aktualizowanie rekordów (Dodawanie, edytowanie i usuwanie rekordów), zakwalifikowanie zaznaczenia z filtrem, sortowanie zaznaczenia i parametryzacja zaznaczenie z informacjami uzyskanymi lub obliczanymi w czasie wykonywania.

[Formularzy CRecordView](../mfc/reference/crecordview-class.md)<br/>
Udostępnia widok formularza bezpośrednio połączony z obiektem zestawu rekordów. Mechanizm wymiany danych okna dialogowego (DDX) wymienia dane między zestawem rekordów i kontrolkami widoku rekordu. Podobnie jak w przypadku wszystkich widoków formularzy widok rekordu jest oparty na zasobie szablonu okna dialogowego. Widoki rekordów obsługują również przechodzenie z rekordu do rekordu w zestawie rekordów, aktualizowanie rekordów i zamykanie skojarzonego zestawu rekordów, gdy widok rekordu zostanie zamknięty.

[CDBException](../mfc/reference/cdbexception-class.md)<br/>
Wyjątek wynikający z błędów w przetwarzaniu dostępu do danych. Ta klasa służy do tego samego celu, co inne klasy wyjątków w mechanizmie obsługi wyjątków biblioteki klas.

[CFieldExchange](../mfc/reference/cfieldexchange-class.md)<br/>
Dostarcza informacje kontekstu do obsługi wymiany pól rekordów (RFX), które wymieniają dane między elementami członkowskimi danych pola i danymi parametrów obiektu zestawu rekordów i odpowiednimi kolumnami tabeli w źródle danych. Analogiczny do klasy [CDataExchange](../mfc/reference/cdataexchange-class.md), który jest używany podobnie do wymiany danych w oknie dialogowym (DDX).

## <a name="related-classes"></a>Powiązane klasy

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
Hermetyzuje dojście do magazynu dla binarnego dużego obiektu (BLOB), takiego jak mapa bitowa. obiekty `CLongBinary` są używane do zarządzania dużymi obiektami danych przechowywanymi w tabelach bazy danych.

[CDBVariant](../mfc/reference/cdbvariant-class.md)<br/>
Umożliwia przechowywanie wartości bez obaw o typ danych wartości. `CDBVariant` śledzi typ danych bieżącej wartości, który jest przechowywany w Unii.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../mfc/class-library-overview.md)
