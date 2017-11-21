---
title: "Zestaw rekordów: Zakładki i położenia bezwzględne (ODBC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SetAbsolutePosition
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b4d703d49173ba950f073342de014127e5696202
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>Zestaw rekordów: zakładki i położenia bezwzględne (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 Podczas nawigowania do zestawu rekordów, często konieczne jest sposób zwracania do określonego rekordu. Zakładka i położenie bezwzględne rekordu Podaj dwa z tych metod.  
  
 W tym temacie opisano:  
  
-   [Jak używać zakładek](#_core_bookmarks_in_mfc_odbc).  
  
-   [Jak ustawić bieżącego rekordu przy użyciu położenia bezwzględne](#_core_absolute_positions_in_mfc_odbc).  
  
##  <a name="_core_bookmarks_in_mfc_odbc"></a>Zakładki w MFC ODBC  
 Zakładki unikatowo określa rekord. Po przejściu do zestawu rekordów, nie zawsze polegać na położenie bezwzględne rekordu ponieważ rekordy, można usunąć z tego zestawu rekordów. Niezawodny sposób, aby śledzić położenie rekord jest użyć jego zakładki. Klasa `CRecordset` udostępnia funkcje elementu członkowskiego dla:  
  
-   Pobieranie zakładki bieżącego rekordu, więc można go zapisać w zmiennej ([GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark)).  
  
-   Szybko przenoszenie do rekordów, określając jego zakładki, która zapisane wcześniej w zmiennej ([SetBookmark](../../mfc/reference/crecordset-class.md#setbookmark)).  
  
 Poniższy przykład przedstawia sposób używania tych funkcji Członkowskich do oznaczania bieżącego rekordu, a później wrócić do niej:  
  
```  
// rs is a CRecordset or  
// CRecordset-derived object  
  
CDBVariant varRecordToReturnTo;  
rs.GetBookmark( varRecordToReturnTo );  
  
// More code in which you  
// move to other records  
  
rs.SetBookmark( varRecordToReturnTo );  
```  
  
 Nie należy wyodrębnić podstawowy typ danych z [cdbvariant — klasa](../../mfc/reference/cdbvariant-class.md) obiektu. Przypisz wartości z `GetBookmark` i wróć do tej zakładki z `SetBookmark`.  
  
> [!NOTE]
>  W zależności od sterownika ODBC i zestaw rekordów typu zakładki może nie być obsługiwany. Użytkownik może łatwo ustalić, czy zakładki są obsługiwane przez wywołanie metody [CRecordset::CanBookmark](../../mfc/reference/crecordset-class.md#canbookmark). Ponadto jeśli zakładki są obsługiwane, należy jawnie wybrać ich implementacji, określając **CRecordset::useBookmarks** opcji [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) funkcję elementu członkowskiego. Należy także sprawdzić trwałości zakładek po pewnych operacji zestawu rekordów. Na przykład jeśli użytkownik **Requery** zestawu rekordów zakładki może nie być już prawidłowe. Wywołanie [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) do sprawdzenia, czy można bezpiecznie wywołać `SetBookmark`.  
  
##  <a name="_core_absolute_positions_in_mfc_odbc"></a>Położenia bezwzględne w MFC ODBC  
 Oprócz zakładki, klasa `CRecordset` można ustawić bieżącego rekordu, określając porządkowym. Jest to bezwzględny.  
  
> [!NOTE]
>  Bezwzględny nie jest dostępna w zestawy rekordów tylko do przodu. Aby uzyskać więcej informacji na temat zestawów rekordów tylko do przodu, zobacz [zestawu rekordów (ODBC)](../../data/odbc/recordset-odbc.md).  
  
 Aby przenieść wskaźnik bieżącego rekordu przy użyciu położenie bezwzględne, należy wywołać [CRecordset::SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition). Podczas przekazywania wartości do `SetAbsolutePosition`, rekord odpowiadający, że porządkowym staje się bieżącego rekordu.  
  
> [!NOTE]
>  Położenie bezwzględne rekordu jest potencjalnie tymczasowy. Jeśli użytkownik usuwa rekordy w zestawie numerem porządkowym o wszelkich zmianach kolejnych rekordu. Zakładki to zalecana metoda przenoszenia bieżącego rekordu. Aby uzyskać więcej informacji, zobacz [zakładki w MFC ODBC](#_core_bookmarks_in_mfc_odbc).  
  
 Aby uzyskać więcej informacji na temat nawigacji zestawu rekordów, zobacz [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)