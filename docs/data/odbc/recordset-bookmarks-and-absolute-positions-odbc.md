---
title: 'Zestaw rekordów: Zakładki i położenia bezwzględne (ODBC) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
f1_keywords:
- SetAbsolutePosition
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 07c888550cbe0d46443147ac9052872df2ab3181
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118150"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>Zestaw rekordów: zakładki i położenia bezwzględne (ODBC)

Ten temat dotyczy klas MFC ODBC.  
  
Podczas przechodzenia przez zestaw rekordów, potrzebny jest często sposób wracania do określonego rekordu. Zakładki i położenia bezwzględne rekordu Podaj dwie z tych metod.  
  
W tym temacie opisano:  
  
- [Jak używać zakładek](#_core_bookmarks_in_mfc_odbc).  
  
- [Jak ustawić bieżącego rekordu przy użyciu położenia bezwzględne](#_core_absolute_positions_in_mfc_odbc).  
  
##  <a name="_core_bookmarks_in_mfc_odbc"></a> Zakładki w MFC ODBC  

Zakładki jednoznacznie identyfikuje rekord. Po przejściu do zestawu rekordów nie zawsze polegasz absolutną pozycję elementów rekord ponieważ rekordy mogą być usunięte z zestawu rekordów. Niezawodny sposób, aby śledzić położenie rekord jest użyć jej zakładki. Klasa `CRecordset` dostarcza funkcji elementów członkowskich dla:  
  
- Wprowadzenie zakładki bieżącego rekordu, więc Zapisz go w zmiennej ([getbookmark —](../../mfc/reference/crecordset-class.md#getbookmark)).  
  
- Przenoszenie szybko do danego rekordu, określając jego zakładki, który został zapisany we wcześniejszej części zmienną ([setbookmark —](../../mfc/reference/crecordset-class.md#setbookmark)).  
  
Poniższy przykład ilustruje sposób używania te funkcje elementów członkowskich do oznaczania bieżącego rekordu i później wrócić do niego:  
  
```cpp  
// rs is a CRecordset or  
// CRecordset-derived object  
  
CDBVariant varRecordToReturnTo;  
rs.GetBookmark( varRecordToReturnTo );  
  
// More code in which you  
// move to other records  
  
rs.SetBookmark( varRecordToReturnTo );  
```  
  
Nie musisz wyodrębnić odpowiedniego typu danych z [klasa CDBVariant](../../mfc/reference/cdbvariant-class.md) obiektu. Przypisz wartość z `GetBookmark` i wróć do tej zakładki z `SetBookmark`.  
  
> [!NOTE]
>  W zależności od sterownik ODBC i typ zbioru rekordów zakładek nie mogą być obsługiwane. Można łatwo określić, czy zakładki są obsługiwane przez wywołanie metody [CRecordset::CanBookmark](../../mfc/reference/crecordset-class.md#canbookmark). Ponadto, jeśli zakładki są obsługiwane, należy jawnie wybierzesz do zaimplementowania je, określając `CRecordset::useBookmarks` opcji [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) funkcja elementu członkowskiego. Należy także sprawdzić stan trwały zakładek, po niektórych operacjach zestawu rekordów. Na przykład jeśli użytkownik `Requery` zestaw rekordów zakładek może nie być już prawidłowa. Wywołaj [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) do sprawdzenia, czy można bezpiecznie wywołać `SetBookmark`.  
  
##  <a name="_core_absolute_positions_in_mfc_odbc"></a> Położenia bezwzględne w MFC ODBC  

Oprócz zakładek, klasy `CRecordset` można ustawić bieżącego rekordu, określając porządkowym. Jest to nazywane pozycjonowanie absolutne.  
  
> [!NOTE]
>  Pozycjonowanie absolutne nie jest dostępna w zestawach rekordów tylko do przodu. Aby uzyskać więcej informacji na temat zestawów rekordów tylko do przodu, zobacz [zestawu rekordów (ODBC)](../../data/odbc/recordset-odbc.md).  
  
Aby przenieść bieżący wskaźnik rekordu przy użyciu położenie bezwzględne, należy wywołać [CRecordset::SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition). Podczas przekazywania wartości do `SetAbsolutePosition`, rekord odpowiadający, że porządkowym staje się bieżącym rekordem.  
  
> [!NOTE]
>  Położenie bezwzględne rekordu jest potencjalnie zawodnych. Jeśli użytkownik usuwa rekordy w zestawie porządkowym kolejnych rekord zmiany. Zakładki są zalecaną metodą przeniesienie bieżącego rekordu. Aby uzyskać więcej informacji, zobacz [zakładki w MFC ODBC](#_core_bookmarks_in_mfc_odbc).  
  
Aby uzyskać więcej informacji na temat rekordów nawigacji zobacz [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
## <a name="see-also"></a>Zobacz też  

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)