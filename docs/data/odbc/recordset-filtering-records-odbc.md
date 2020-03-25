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
ms.openlocfilehash: 2e742ee02e142fd87df3f149379d9971c4acd166
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212914"
---
# <a name="recordset-filtering-records-odbc"></a>Zestaw rekordów: filtrowanie rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie wyjaśniono sposób filtrowania zestawu rekordów w taki sposób, aby wybierał tylko określony podzestaw dostępnych rekordów. Na przykład można wybrać tylko sekcje klasy dla określonego kursu, takie jak MATH101. Filtr to warunek wyszukiwania zdefiniowany przez zawartość klauzuli **WHERE** języka SQL. Gdy struktura dołącza go do instrukcji SQL zestawu rekordów, klauzula **WHERE** ogranicza wybór.

Należy ustanowić filtr obiektu zestawu rekordów po utworzeniu obiektu, ale przed wywołaniem funkcji składowej `Open` (lub przed wywołaniem `Requery` funkcji składowej dla istniejącego obiektu zestawu rekordów, którego funkcja członkowska `Open` została wcześniej wywołana).

#### <a name="to-specify-a-filter-for-a-recordset-object"></a>Aby określić filtr dla obiektu zestawu rekordów

1. Utwórz nowy obiekt zestawu rekordów (lub Przygotuj do wywołania `Requery` dla istniejącego obiektu).

1. Ustaw wartość elementu członkowskiego danych [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) obiektu.

   Filtr jest ciągiem zakończonym wartością null, który zawiera zawartość klauzuli **WHERE** języka SQL, ale nie słowo kluczowe **WHERE**. Możesz na przykład użyć następujących usług:

    ```
    m_pSet->m_strFilter = "CourseID = 'MATH101'";
    ```

   not

    ```
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";
    ```

    > [!NOTE]
    >  Ciąg literału "MATH101" jest pokazywany w pojedynczym cudzysłowie powyżej. W specyfikacji ODBC SQL pojedyncze cudzysłowy są używane do określenia literału ciągu znaków. W tej sytuacji należy zapoznać się z dokumentacją sterownika ODBC dotyczącą wymagań w systemie DBMS. Ta składnia jest również omówiona w dalszej części końca tego tematu.

1. Ustaw inne potrzebne opcje, takie jak porządek sortowania, tryb blokowania lub parametry. Określanie parametru jest szczególnie przydatne. Aby uzyskać informacje o parametryzacja filtru, zobacz [zestaw rekordów: parametryzacja a zestaw rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Wywołaj `Open` dla nowego obiektu (lub `Requery` dla wcześniej otwartego obiektu).

> [!TIP]
>  Używanie parametrów w filtrze jest potencjalnie najbardziej wydajną metodą pobierania rekordów.

> [!TIP]
>  Filtry zestawu rekordów są przydatne w przypadku [sprzęgania](../../data/odbc/recordset-performing-a-join-odbc.md) tabel i używania [parametrów](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) na podstawie informacji uzyskanych lub obliczanych w czasie wykonywania.

Zestaw rekordów wybiera tylko te rekordy, które spełniają określony warunek wyszukiwania. Na przykład, aby określić filtr kurs opisany powyżej (przy założeniu, że zmienna `strCourseID` obecnie ustawiona na wartość "MATH101"), wykonaj następujące czynności:

```
// Using the recordset pointed to by m_pSet

// Set the filter
m_pSet->m_strFilter = "CourseID = " + strCourseID;

// Run the query with the filter in place
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )

// Use the recordset
```

Zestaw rekordów zawiera rekordy dla wszystkich sekcji klasy dla MATH101.

Zwróć uwagę, jak ciąg filtru został ustawiony w powyższym przykładzie przy użyciu zmiennej ciągu. Jest to typowy sposób użycia. Ale Załóżmy, że chcemy określić wartość literału 100 dla identyfikatora kursu. Poniższy kod pokazuje, jak prawidłowo ustawić ciąg filtru z wartością literału:

```
m_strFilter = "StudentID = '100'";   // correct
```

Zwróć uwagę na użycie znaków pojedynczego cudzysłowu; Jeśli ustawisz ciąg filtru bezpośrednio, ciąg filtru **nie**będzie:

```
m_strFilter = "StudentID = 100";   // incorrect for some drivers
```

Cytowane pokazane powyżej jest zgodne ze specyfikacją ODBC, ale niektóre systemy DBMS mogą wymagać innych znaków cudzysłowu. Aby uzyskać więcej informacji, zobacz [SQL: dostosowywanie instrukcji SQL zestawu rekordów (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

> [!NOTE]
>  Jeśli zdecydujesz się zastąpić domyślny ciąg SQL zestawu rekordów, przekazując własny ciąg SQL do `Open`, nie należy ustawiać filtru, jeśli niestandardowy ciąg zawiera klauzulę **WHERE** . Aby uzyskać więcej informacji na temat przesłaniania domyślnego SQL, zobacz [SQL: dostosowywanie instrukcji SQL zestawu rekordów (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: sortowanie rekordów (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)<br/>
[Zestaw rekordów: jak zestawy rekordów pobierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Zestaw rekordów: jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[Zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
