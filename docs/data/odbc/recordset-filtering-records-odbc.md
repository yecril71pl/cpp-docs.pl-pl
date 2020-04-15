---
title: 'Zestaw rekordów: filtrowanie rekordów (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- data [MFC], filtering
- recordsets [C++], filtering
- filtering recordsets
- ODBC recordsets [C++], filtering records
- filters [C++], recordset object
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
ms.openlocfilehash: 56b8c4f52ec294f58a760e1309d32aa81286ddec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367015"
---
# <a name="recordset-filtering-records-odbc"></a>Zestaw rekordów: filtrowanie rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie wyjaśniono, jak filtrować zestaw rekordów, tak aby wybierał tylko określony podzbiór dostępnych rekordów. Na przykład można wybrać tylko sekcje klasy dla określonego kursu, takich jak MATH101. Filtr jest warunkiem wyszukiwania zdefiniowanym przez zawartość klauzuli SQL **WHERE.** Gdy struktura dołącza go do instrukcji SQL zestawie rekordów, klauzula **WHERE** ogranicza wybór.

Należy ustanowić filtr obiektu pliku recordset po skonstruowaniu obiektu, ale przed wywołaniem jego `Open` funkcji elementu członkowskiego (lub przed wywołaniem funkcji `Requery` elementu członkowskiego dla istniejącego obiektu pliku rekordów, którego `Open` funkcja elementu członkowskiego została wcześniej wywołana).

#### <a name="to-specify-a-filter-for-a-recordset-object"></a>Aby określić filtr dla obiektu obiektu afiliowania

1. Skonstruuj nowy obiekt pliku `Requery` recordset (lub przygotuj się do wywołania istniejącego obiektu).

1. Ustaw wartość elementu członkowskiego [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) danych obiektu.

   Filtr jest ciągiem zakończonym zerem, który zawiera zawartość klauzuli SQL **WHERE,** ale nie słowo kluczowe **WHERE**. Możesz na przykład użyć następujących usług:

    ```
    m_pSet->m_strFilter = "CourseID = 'MATH101'";
    ```

   not

    ```
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";
    ```

    > [!NOTE]
    >  Literał "MATH101" jest wyświetlany z pojedynczymi cudzysłowami powyżej. W specyfikacji SQL ODBC pojedyncze cudzysłowy są używane do oznaczania literału ciągu znaków. Sprawdź w dokumentacji sterownika ODBC wymagania dotyczące cytowaniowania dbms w tej sytuacji. Ta składnia jest również omówiona dalej pod koniec tego tematu.

1. Ustaw inne potrzebne opcje, takie jak kolejność sortowania, tryb blokowania lub parametry. Określenie parametru jest szczególnie przydatne. Aby uzyskać informacje dotyczące parametryzacji filtru, zobacz [Recordset: Parametrizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Wywołanie `Open` nowego obiektu `Requery` (lub wcześniej otwartego obiektu).

> [!TIP]
> Korzystanie z parametrów w filtrze jest potencjalnie najbardziej efektywną metodą pobierania rekordów.

> [!TIP]
> Filtry zestawu rekordów są przydatne do [łączenia](../../data/odbc/recordset-performing-a-join-odbc.md) tabel i [używania parametrów](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) na podstawie informacji uzyskanych lub obliczonych w czasie wykonywania.

Wakus rejestruje wybiera tylko te rekordy, które spełniają określony warunek wyszukiwania. Na przykład, aby określić filtr kursu opisany `strCourseID` powyżej (przy założeniu, że zmienna aktualnie ustawiona, na przykład, na "MATH101"), wykonaj następujące czynności:

```
// Using the recordset pointed to by m_pSet

// Set the filter
m_pSet->m_strFilter = "CourseID = " + strCourseID;

// Run the query with the filter in place
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )

// Use the recordset
```

Plik recordset zawiera rekordy dla wszystkich sekcji klas dla MATH101.

Zwróć uwagę, jak ciąg filtru został ustawiony w powyższym przykładzie, przy użyciu zmiennej ciągu. Jest to typowe użycie. Ale załóżmy, że chcesz określić dosłowną wartość 100 dla identyfikatora kursu. Poniższy kod pokazuje, jak poprawnie ustawić ciąg filtru z wartością literału:

```
m_strFilter = "StudentID = '100'";   // correct
```

Zwróć uwagę na użycie pojedynczych znaków cudzysłowu; jeśli ustawisz ciąg filtru bezpośrednio, ciąg filtru **nie**jest:

```
m_strFilter = "StudentID = 100";   // incorrect for some drivers
```

Cytowanie pokazane powyżej jest zgodne ze specyfikacją ODBC, ale niektóre dbmsss może wymagać innych znaków cudzysłowu. Aby uzyskać więcej informacji, zobacz [SQL: Customizing Your Recordset's SQL Statement (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

> [!NOTE]
> Jeśli zdecydujesz się zastąpić domyślny ciąg SQL zestawu rekordów, przekazując własny ciąg SQL do programu , nie należy ustawiać `Open`filtru, jeśli ciąg niestandardowy ma klauzulę **WHERE.** Aby uzyskać więcej informacji na temat zastępowania domyślnego języka SQL, zobacz [SQL: Customizing Your Recordset's SQL Statement (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: sortowanie rekordów (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)<br/>
[Zestaw rekordów: jak zestawy rekordów pobierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Zestaw rekordów: jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[Zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
