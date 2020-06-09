---
title: Klasy ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [MFC], ODBC
- ODBC classes [MFC]
ms.assetid: 6c40fca8-3033-4873-9abe-7f51725de0e0
ms.openlocfilehash: 18b6e3a0ea20dbd352a61c4faab52c35b852dcb3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622182"
---
# <a name="odbc-classes"></a>Klasy ODBC

Te klasy współpracują z innymi klasami struktury aplikacji, aby zapewnić łatwy dostęp do różnorodnych baz danych, dla których dostępne są sterowniki Open Database Connectivity (ODBC).

Programy korzystające z baz danych ODBC będą mieć co najmniej `CDatabase` obiekt i `CRecordset` obiekt.

[CDatabase](reference/cdatabase-class.md)<br/>
Hermetyzuje połączenie ze źródłem danych, za pomocą którego można pracować na źródle danych.

[CRecordset](reference/crecordset-class.md)<br/>
Hermetyzuje zestaw rekordów wybranych ze źródła danych. Zestawy rekordów umożliwiają przewijanie rekordów do rekordu, aktualizowanie rekordów (Dodawanie, edytowanie i usuwanie rekordów), zakwalifikowanie zaznaczenia z filtrem, sortowanie zaznaczenia i parametryzacja zaznaczenie z informacjami uzyskanymi lub obliczanymi w czasie wykonywania.

[Formularzy CRecordView](reference/crecordview-class.md)<br/>
Udostępnia widok formularza bezpośrednio połączony z obiektem zestawu rekordów. Mechanizm wymiany danych okna dialogowego (DDX) wymienia dane między zestawem rekordów i kontrolkami widoku rekordu. Podobnie jak w przypadku wszystkich widoków formularzy widok rekordu jest oparty na zasobie szablonu okna dialogowego. Widoki rekordów obsługują również przechodzenie z rekordu do rekordu w zestawie rekordów, aktualizowanie rekordów i zamykanie skojarzonego zestawu rekordów, gdy widok rekordu zostanie zamknięty.

[CDBException](reference/cdbexception-class.md)<br/>
Wyjątek wynikający z błędów w przetwarzaniu dostępu do danych. Ta klasa służy do tego samego celu, co inne klasy wyjątków w mechanizmie obsługi wyjątków biblioteki klas.

[CFieldExchange](reference/cfieldexchange-class.md)<br/>
Dostarcza informacje kontekstu do obsługi wymiany pól rekordów (RFX), które wymieniają dane między elementami członkowskimi danych pola i danymi parametrów obiektu zestawu rekordów i odpowiednimi kolumnami tabeli w źródle danych. Analogiczny do klasy [CDataExchange](reference/cdataexchange-class.md), który jest używany podobnie do wymiany danych w oknie dialogowym (DDX).

## <a name="related-classes"></a>Powiązane klasy

[CLongBinary](reference/clongbinary-class.md)<br/>
Hermetyzuje dojście do magazynu dla binarnego dużego obiektu (BLOB), takiego jak mapa bitowa. `CLongBinary`obiekty służą do zarządzania dużymi obiektami danych przechowywanymi w tabelach bazy danych.

[CDBVariant](reference/cdbvariant-class.md)<br/>
Umożliwia przechowywanie wartości bez obaw o typ danych wartości. `CDBVariant`śledzi typ danych bieżącej wartości, który jest przechowywany w Unii.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](class-library-overview.md)
