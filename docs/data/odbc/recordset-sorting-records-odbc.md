---
title: 'Zestaw rekordów: Sortowanie rekordów (ODBC) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ddb92016b7b911fc86f2feab27a698ce7fa55c45
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-sorting-records-odbc"></a>Zestaw rekordów: sortowanie rekordów (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 W tym temacie opisano sposób sortowania zestawu rekordów. Można określić jedną lub więcej kolumn, na którym można oprzeć sortowania i można określić kolejności rosnącej lub malejącej (`ASC` lub **DESC**; `ASC` jest ustawieniem domyślnym) dla każdego określonego kolumny. Na przykład jeśli określisz dwie kolumny rekordy są najpierw posortowane w pierwszej kolumnie o nazwie, a następnie w drugiej kolumnie o nazwie. SQL **ORDER BY** klauzuli definiuje sortowania. Gdy dołącza platformę **ORDER BY** zapytania klauzuli SQL zestawu rekordów, formanty klauzuli zaznaczenie do porządkowania.  
  
 Należy ustanowić porządek sortowania zestawu rekordów po konstruowania obiektu, ale przed wywołaniem jego **Otwórz** funkcji członkowskiej (lub przed wywołaniem **Requery** funkcji członkowskiej istniejącego obiektu zestawu rekordów którego **Otwórz** została wywołana funkcja członkowska wcześniej).  
  
#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>Aby określić kolejność sortowania dla obiekt zestawu rekordów  
  
1.  Utworzyć nowy obiekt zestawu rekordów (lub przygotowania do wywołania **Requery** dla istniejącego).  
  
2.  Ustaw wartość obiektu [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) element członkowski danych.  
  
     Sortowanie jest ciąg znaków zakończony znakiem null. Zawiera zawartość **ORDER BY** klauzuli, ale nie — słowo kluczowe **ORDER BY**. Na przykład użyć:  
  
    ```  
    recordset.m_strSort = "LastName DESC, FirstName DESC";  
    ```  
  
     not  
  
    ```  
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";  
    ```  
  
3.  Ustaw inne opcje, które są potrzebne, takie jak filtr, tryb blokowania lub parametrów.  
  
4.  Wywołanie **Otwórz** dla nowego obiektu (lub **Requery** istniejącego obiektu).  
  
 Wybrane rekordy są uporządkowane jak określono. Na przykład aby posortować zestawu rekordów uczniów w kolejności malejącej według nazwisko, a następnie imię, wykonaj następujące czynności:  
  
```  
// Construct the recordset  
CStudentSet rsStudent( NULL );  
// Set the sort  
rsStudent.m_strSort = "LastName DESC, FirstName DESC";  
// Run the query with the sort in place  
rsStudent.Open( );  
```  
  
 Zestaw rekordów zawiera wszystkie rekordy studentów, posortowane w kolejności malejącej (Z do A) według nazwiska, następnie według imienia.  
  
> [!NOTE]
>  Jeśli chcesz zastąpić ciąg SQL domyślnego zestawu rekordów przez przekazanie własny ciąg SQL do **Otwórz**, nie należy ustawiać sortowania, jeśli ma tekst niestandardowy **ORDER BY** klauzuli.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Zestaw rekordów: Parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)   
 [Zestaw rekordów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)