---
title: 'Zestaw rekordów: zakładki i położenia bezwzględne (ODBC)'
ms.date: 11/04/2016
f1_keywords:
- SetAbsolutePosition
helpviewer_keywords:
- CDBVariant class, bookmarks
- absolute positions, ODBC recordsets
- bookmarks, CDBVariant
- bookmarks, ODBC recordsets
- ODBC recordsets, absolute positions
- ODBC recordsets, bookmarks
- cursors [ODBC], absolute position in recordsets
- recordsets, bookmarks
- bookmarks
- SetAbsolutePosition method
- recordsets, absolute positions
- positioning records
- SetBookmark method
- record positioning
- GetBookmark method
- SetAbsolutePosition method, bookmarks
ms.assetid: 189788d6-33c1-41c5-9265-97db2a5d43cc
ms.openlocfilehash: 77c8bbaf7c0bc21dab62c3785364e72656287815
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367067"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>Zestaw rekordów: zakładki i położenia bezwzględne (ODBC)

Ten temat dotyczy klas MFC ODBC.

Podczas nawigacji po a recordset, często trzeba sposób powrotu do określonego rekordu. Zakładka rekordu i pozycja bezwzględna zapewniają dwie takie metody.

W tym temacie wyjaśniono:

- [Jak korzystać z zakładek](#_core_bookmarks_in_mfc_odbc).

- [Jak ustawić bieżący rekord przy użyciu pozycji bezwzględnych](#_core_absolute_positions_in_mfc_odbc).

## <a name="bookmarks-in-mfc-odbc"></a><a name="_core_bookmarks_in_mfc_odbc"></a>Zakładki w MFC ODBC

Zakładka jednoznacznie identyfikuje rekord. Podczas nawigacji po rekordzie nie zawsze można polegać na pozycji bezwzględnej rekordu, ponieważ rekordy można usunąć z akusety. Niezawodnym sposobem śledzenia pozycji rekordu jest użycie jego zakładki. Klasa `CRecordset` dostarcza funkcje członkowskie dla:

- Pobierz zakładkę bieżącego rekordu, dzięki czemu można zapisać go w zmiennej ([GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark)).

- Szybkie przejście do danego rekordu, określając jego zakładkę, która została zapisana wcześniej w zmiennej ([SetBookmark](../../mfc/reference/crecordset-class.md#setbookmark)).

Poniższy przykład ilustruje, jak używać tych funkcji członkowskich do oznaczania bieżącego rekordu, a później do niego powracać:

```cpp
// rs is a CRecordset or
// CRecordset-derived object

CDBVariant varRecordToReturnTo;
rs.GetBookmark( varRecordToReturnTo );

// More code in which you
// move to other records

rs.SetBookmark( varRecordToReturnTo );
```

Nie trzeba wyodrębniać podstawowy typ danych z [CDBVariant Class](../../mfc/reference/cdbvariant-class.md) obiektu. Przypisz wartość `GetBookmark` z tą zakładką `SetBookmark`i wróć do niego za pomocą pliku .

> [!NOTE]
> W zależności od sterownika ODBC i typu pliku recordset zakładki mogą nie być obsługiwane. Można łatwo określić, czy zakładki są obsługiwane przez wywołanie [CRecordset::CanBookmark](../../mfc/reference/crecordset-class.md#canbookmark). Ponadto jeśli zakładki są obsługiwane, należy jawnie wybrać do ich `CRecordset::useBookmarks` zaimplementowania, określając opcję w [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) funkcji elementu członkowskiego. Należy również sprawdzić trwałość zakładek po niektórych operacjach nastawy rekordów. Na przykład jeśli `Requery` jesteś rekordem, zakładki mogą nie być już prawidłowe. Wywołanie [CDatabase::GetBookmarkPersistence,](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) aby sprawdzić, czy można bezpiecznie wywołać `SetBookmark`.

## <a name="absolute-positions-in-mfc-odbc"></a><a name="_core_absolute_positions_in_mfc_odbc"></a>Pozycje bezwzględne w MFC ODBC

Oprócz zakładek, `CRecordset` klasa umożliwia ustawienie bieżącego rekordu przez określenie pozycji porządkowej. Nazywa się to pozycjonowaniem absolutnym.

> [!NOTE]
> Pozycjonowanie bezwzględne nie jest dostępne w rekordach tylko do przodu. Aby uzyskać więcej informacji na temat rekordów tylko do przodu, zobacz [Recordset (ODBC)](../../data/odbc/recordset-odbc.md).

Aby przenieść bieżący wskaźnik rekordu przy użyciu pozycji bezwzględnej, zadzwoń [do CRecordset::SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition). Po przełożeniu `SetAbsolutePosition`wartości do rekordu odpowiadającego tej pozycji porządkowej staje się bieżący rekord.

> [!NOTE]
> Bezwzględna pozycja rekordu jest potencjalnie zawodna. Jeśli użytkownik usunie rekordy ze świata rekordów, zmieni się położenie porządkowe każdego kolejnego rekordu. Zakładki są zalecaną metodą przenoszenia bieżącego rekordu. Aby uzyskać więcej informacji, zobacz [Zakładki w MFC ODBC](#_core_bookmarks_in_mfc_odbc).

Aby uzyskać więcej informacji na temat nawigacji w forsach [rekordów, zobacz Tablica rekordów: Przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)
