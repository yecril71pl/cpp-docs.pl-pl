---
title: 'Zestaw rekordów: sortowanie rekordów (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
ms.openlocfilehash: 708ba8e851fa81ef2adb4360fe582880acd23c31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621277"
---
# <a name="recordset-sorting-records-odbc"></a>Zestaw rekordów: sortowanie rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie opisano sposób sortowanie rekordów. Można określić co najmniej jedną kolumnę, na którym można oprzeć sortowania, a można określić w kolejności rosnącej lub malejącej (**ASC** lub **DESC**; **ASC** jest ustawieniem domyślnym) dla każdej określonej kolumny. Na przykład jeśli określono dwiema kolumnami, rekordy są sortowane najpierw w pierwszej kolumnie o nazwie, a następnie w drugiej kolumnie o nazwie. SQL **ORDER BY** klauzuli definiowane jest sortowanie. Kiedy struktura dołącza **ORDER BY** klauzuli SQL zestawu rekordów na kwerendy, formanty klauzuli zaznaczenie w kolejności.

Po utworzenia obiekt, ale przed wywołaniem, musisz ustanowić porządek sortowania w zestawie rekordów jego `Open` funkcja elementu członkowskiego (lub przed wywołaniem `Requery` funkcja elementu członkowskiego dla istniejącego zestawu rekordów obiektu, którego `Open` została funkcja elementu członkowskiego wywołuje się wcześniej).

#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>Aby określić kolejność sortowania dla obiektu zestawu rekordów

1. Utworzyć nowy obiekt zestawu rekordów (lub Przygotuj się do wywołania `Requery` na jeden z istniejących).

1. Ustaw wartość obiektu [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) element członkowski danych.

   Sortowanie jest ciąg zakończony znakiem null. Zawiera ona zawartość **ORDER BY** klauzuli, ale nie — słowo kluczowe **ORDER BY**. Na przykład użyć:

    ```
    recordset.m_strSort = "LastName DESC, FirstName DESC";
    ```

   not

    ```
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";
    ```

1. Ustaw inne opcje, których potrzebujesz, takie jak filtr, tryb blokowania lub parametrów.

1. Wywołaj `Open` dla nowego obiektu (lub `Requery` istniejącego obiektu).

Wybrane rekordy są uporządkowane jako określony. Na przykład aby posortować zestawu rekordów dla uczniów w kolejności malejącej według nazwiska, a następnie imię, wykonaj następujące czynności:

```cpp
// Construct the recordset
CStudentSet rsStudent( NULL );
// Set the sort
rsStudent.m_strSort = "LastName DESC, FirstName DESC";
// Run the query with the sort in place
rsStudent.Open( );
```

Zestaw rekordów zawiera wszystkie rekordy dla uczniów, posortowane w kolejności malejącej (Z do A) według nazwiska, następnie według imienia.

> [!NOTE]
>  Jeśli zdecydujesz się zastąpić ciąg SQL domyślnego zestawu rekordów, przekazując własne parametry SQL do `Open`, nie należy ustawiać sortowania, jeśli zawiera tekst niestandardowy **ORDER BY** klauzuli.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Zestaw rekordów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)