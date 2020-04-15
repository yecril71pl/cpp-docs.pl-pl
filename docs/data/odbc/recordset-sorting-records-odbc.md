---
title: 'Zestaw rekordów: sortowanie rekordów (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
ms.openlocfilehash: 8b4deea1d8cbd4abe01ccc7a4114131378abe463
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366925"
---
# <a name="recordset-sorting-records-odbc"></a>Zestaw rekordów: sortowanie rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie wyjaśniono, jak sortować swój rekord. Można określić jedną lub więcej kolumn, na których ma być opierać sortowanie, i można określić kolejność rosnącą lub malejącą (**ASC** lub **DESC**; **ASC** jest ustawieniem domyślnym) dla każdej określonej kolumny. Na przykład jeśli określisz dwie kolumny, rekordy są sortowane najpierw w pierwszej kolumnie o nazwie, a następnie w drugiej kolumnie o nazwie. Klauzula SQL **ORDER BY** definiuje sortowanie. Gdy struktura dołącza **order by** klauzuli do kwerendy SQL pliku recordset, klauzula kontroluje kolejność zaznaczenia.

Należy ustanowić kolejność sortowania pliku recordset po skonstruowaniu `Open` obiektu, ale przed wywołaniem jego funkcji elementu członkowskiego (lub przed wywołaniem funkcji `Requery` elementu członkowskiego dla istniejącego obiektu pliku rekordów, którego `Open` funkcja elementu członkowskiego została wcześniej wywołana).

#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>Aby określić kolejność sortowania obiektu obiektu aktu rekordów

1. Skonstruuj nowy obiekt pliku `Requery` recordset (lub przygotuj się do wywołania istniejącego).

1. Ustaw wartość elementu członkowskiego [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) danych obiektu.

   Sortowanie jest ciągiem zakończonym z wartością null. Zawiera zawartość klauzuli **ORDER BY,** ale nie słowo kluczowe **ORDER BY**. Możesz na przykład użyć następujących usług:

    ```
    recordset.m_strSort = "LastName DESC, FirstName DESC";
    ```

   not

    ```
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";
    ```

1. Ustaw inne potrzebne opcje, takie jak filtr, tryb blokowania lub parametry.

1. Wywołanie `Open` nowego obiektu `Requery` (lub istniejącego obiektu).

Wybrane rekordy są uporządkowane w sposób określony. Na przykład, aby posortować zestaw rekordów uczniów w kolejności malejącej według nazwiska, a następnie imienia, wykonaj następujące czynności:

```cpp
// Construct the recordset
CStudentSet rsStudent( NULL );
// Set the sort
rsStudent.m_strSort = "LastName DESC, FirstName DESC";
// Run the query with the sort in place
rsStudent.Open( );
```

Plik recordset zawiera wszystkie rekordy uczniów, posortowane w kolejności malejącej (Z do A) według nazwiska, a następnie według imienia.

> [!NOTE]
> Jeśli zdecydujesz się zastąpić domyślny ciąg SQL zestawu rekordów, przekazując własny ciąg SQL do `Open`, nie ustawiaj sortowania, jeśli ciąg niestandardowy ma klauzulę ORDER **BY.**

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Zestaw rekordów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
