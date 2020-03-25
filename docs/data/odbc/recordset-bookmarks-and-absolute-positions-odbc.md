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
ms.openlocfilehash: 9a25c0fe4c1f08d376824fbc02211d22c7c14435
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212969"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>Zestaw rekordów: zakładki i położenia bezwzględne (ODBC)

Ten temat dotyczy klas MFC ODBC.

Podczas przechodzenia przez zestaw rekordów często potrzebny jest sposób powrotu do określonego rekordu. Zakładka i położenie absolutne rekordu zawierają dwie takie metody.

W tym temacie objaśniono:

- [Jak używać zakładek](#_core_bookmarks_in_mfc_odbc).

- [Jak ustawić bieżący rekord przy użyciu pozycji bezwzględnych](#_core_absolute_positions_in_mfc_odbc).

##  <a name="bookmarks-in-mfc-odbc"></a><a name="_core_bookmarks_in_mfc_odbc"></a>Zakładki w MFC ODBC

Zakładka jednoznacznie identyfikuje rekord. Po przejściu przez zestaw rekordów nie zawsze można polegać na pozycji bezwzględnej rekordu, ponieważ rekordy można usunąć z zestawu rekordów. Niezawodnym sposobem śledzenia pozycji rekordu jest użycie jej zakładki. Klasy `CRecordset` udostępniają funkcje członkowskie dla:

- Pobieranie zakładki bieżącego rekordu, dzięki czemu można ją zapisać w zmiennej ([GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark)).

- Szybkie przeniesienie do danego rekordu przez określenie jego zakładki, która została zapisana wcześniej w zmiennej ([SetBookmark](../../mfc/reference/crecordset-class.md#setbookmark)).

Poniższy przykład ilustruje sposób używania tych funkcji elementów członkowskich do oznaczania bieżącego rekordu i późniejszego powrotu do niego:

```cpp
// rs is a CRecordset or
// CRecordset-derived object

CDBVariant varRecordToReturnTo;
rs.GetBookmark( varRecordToReturnTo );

// More code in which you
// move to other records

rs.SetBookmark( varRecordToReturnTo );
```

Nie jest konieczne wyodrębnienie bazowego typu danych z obiektu [klasy CDBVariant](../../mfc/reference/cdbvariant-class.md) . Przypisz wartość `GetBookmark` i wróć do tej zakładki z `SetBookmark`.

> [!NOTE]
>  W zależności od sterownika ODBC i typu zestawu rekordów zakładki mogą nie być obsługiwane. Można łatwo określić, czy zakładki są obsługiwane przez wywołanie [CRecordset:: debookmark](../../mfc/reference/crecordset-class.md#canbookmark). Ponadto jeśli zakładki są obsługiwane, należy jawnie wybrać ich implementację, określając opcję `CRecordset::useBookmarks` w funkcji elementu członkowskiego [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) . Należy również sprawdzić trwałość zakładek po pewnych operacjach zestawu rekordów. Na przykład jeśli `Requery` zestaw rekordów, zakładki mogą nie być już prawidłowe. Wywołaj [CDatabase:: GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) , aby sprawdzić, czy można bezpiecznie wywołać `SetBookmark`.

##  <a name="absolute-positions-in-mfc-odbc"></a><a name="_core_absolute_positions_in_mfc_odbc"></a>Położenia bezwzględne w MFC ODBC

Poza zakładkami, Klasa `CRecordset` umożliwia ustawienie bieżącego rekordu przez określenie pozycji porządkowej. Jest to nazywane rozmieszczeniem bezwzględnym.

> [!NOTE]
>  Pozycjonowanie bezwzględne nie jest dostępne w zestawach rekordów tylko do przodu. Aby uzyskać więcej informacji na temat zestawów rekordów tylko do przesyłania dalej, zobacz [zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md).

Aby przenieść bieżący wskaźnik rekordu przy użyciu pozycji absolutnej, wywołaj [CRecordset:: SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition). W przypadku przekazania wartości do `SetAbsolutePosition`rekord odpowiadający tej pozycji porządkowej stanie się bieżącym rekordem.

> [!NOTE]
>  Bezwzględne położenie rekordu jest potencjalnie zawodne. Jeśli użytkownik usunie rekordy z zestawu rekordów, pozycja porządkowa każdego kolejnego rekordu zmieni się. Zakładka jest zalecaną metodą przeniesienia bieżącego rekordu. Aby uzyskać więcej informacji, zobacz [zakładki w MFC ODBC](#_core_bookmarks_in_mfc_odbc).

Aby uzyskać więcej informacji na temat nawigowania po zestawach rekordów, zobacz [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)
