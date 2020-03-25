---
title: Widoki rekordów (dostęp do danych MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], record views
- ODBC recordsets [C++], record views
- databases [C++], record views
- record views [C++]
- forms [C++], data access tasks
ms.assetid: 562122d9-01d8-4284-acf6-ea109ab0408d
ms.openlocfilehash: 31dbd92219f263c625050524279b97ef38ba9ba1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209134"
---
# <a name="record-views--mfc-data-access"></a>Widoki rekordów (dostęp do danych MFC)

Ta sekcja dotyczy tylko klas MFC ODBC. Aby uzyskać informacje o widokach rekordów OLE DB, zobacz [COleDBRecordView](../mfc/reference/coledbrecordview-class.md) i [Korzystanie z widoków rekordów OLE DB](../data/oledb/using-ole-db-record-views.md).

Aby obsługiwać aplikacje dostępu do danych oparte na formularzach, Biblioteka klas zawiera klasy [formularzy CRecordView](../mfc/reference/crecordview-class.md). Widok rekordu jest obiektem widoku formularza, którego formanty są mapowane bezpośrednio do elementów członkowskich danych obiektu [zestawu rekordów](../data/odbc/recordset-odbc.md) (i pośrednio do odpowiednich kolumn w wyniku zapytania lub tabeli w źródle danych). Podobnie jak w przypadku klasy bazowej [CFormView](../mfc/reference/cformview-class.md), `CRecordView` opiera się na zasobie szablonu okna dialogowego.

## <a name="form-uses"></a>Formularz używa

Formularze są przydatne w przypadku różnych zadań dostępu do danych:

- Wprowadzanie danych

- Wykonywanie analizy danych tylko do odczytu

- Aktualizowanie danych

## <a name="further-reading-about-record-views"></a>Dalsze informacje o widokach rekordów

Materiał w tematach dotyczy zarówno klas ODBC, jak i opartych na obiektach DAO. Użyj `CRecordView` dla ODBC i `CDaoRecordView` dla obiektów DAO.

Tematy obejmują:

- [Funkcje klas widoków rekordów](../data/features-of-record-view-classes-mfc-data-access.md)

- [Wymiana danych dla widoków rekordów](../data/data-exchange-for-record-views-mfc-data-access.md)

- [Twoja rola w pracy z widokiem rekordu](../data/your-role-in-working-with-a-record-view-mfc-data-access.md)

- [Projektowanie i Tworzenie widoku rekordu](../data/designing-and-creating-a-record-view-mfc-data-access.md)

- [Korzystanie z widoku rekordu](../data/using-a-record-view-mfc-data-access.md)

## <a name="see-also"></a>Zobacz też

[Programowanie dostępu do danych (MFC/ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[Lista sterowników ODBC](../data/odbc/odbc-driver-list.md)
