---
title: 'Zestaw rekordów: Filtrowanie rekordów (ODBC) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data [MFC], filtering
- recordsets [C++], filtering
- filtering recordsets
- ODBC recordsets [C++], filtering records
- filters [C++], recordset object
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6cdd5882c259c2f1746d1c6f41572631da4a2788
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079951"
---
# <a name="recordset-filtering-records-odbc"></a>Zestaw rekordów: filtrowanie rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie wyjaśniono, jak filtrować zestaw rekordów, tak, aby wybierało konkretnego podzbioru dostępnych rekordów. Na przykład można zaznaczyć klasy sekcji danego kursu, takich jak MATH101. Filtr jest warunek wyszukiwania zdefiniowane przez zawartość SQL **gdzie** klauzuli. Gdy w ramach dołącza je do instrukcji SQL zestawu rekordów, **gdzie** klauzuli ogranicza wybór.

Po utworzenia obiekt, ale przed wywołaniem, musisz ustanowić filtr obiektem rekordem jego `Open` funkcji składowej (lub przed wywołaniem `Requery` funkcja elementu członkowskiego dla istniejącego zestawu rekordów obiektu, którego `Open` funkcja elementu członkowskiego ma wywołana wcześniej).

#### <a name="to-specify-a-filter-for-a-recordset-object"></a>Aby określić filtr dla obiektu zestawu rekordów

1. Utworzyć nowy obiekt zestawu rekordów (lub Przygotuj się do wywołania `Requery` istniejącego obiektu).

1. Ustaw wartość obiektu [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) element członkowski danych.

   Filtr jest ciąg zakończony znakiem null znajduje się zawartość SQL **gdzie** klauzuli, ale nie — słowo kluczowe **gdzie**. Na przykład użyć:

    ```
    m_pSet->m_strFilter = "CourseID = 'MATH101'";
    ```

   not

    ```
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";
    ```

    > [!NOTE]
    >  Ciąg literału "MATH101" jest wyświetlany w pojedynczy cudzysłów powyżej. W specyfikacji ODBC SQL apostrofy służą do oznaczania literału ciągu znaków. Zajrzyj do dokumentacji sterownika ODBC dla quoting wymagań systemu DBMS w takiej sytuacji. Ta składnia jest również omówiona dalsze pod koniec tego tematu.

1. Ustaw inne opcje, których potrzebujesz, takie jak kolejność sortowania, tryb blokowania lub parametrów. Określenie parametru jest szczególnie przydatne. Aby dowiedzieć się, jak parametryzacja filtru, zobacz [zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Wywołaj `Open` dla nowego obiektu (lub `Requery` wcześniej otwartych obiektu).

> [!TIP]
>  Przy użyciu parametrów w filtrze prawdopodobnie jest to najwydajniejsza metoda pobierania rekordów.

> [!TIP]
>  Zestaw rekordów filtry są przydatne w przypadku [dołączania](../../data/odbc/recordset-performing-a-join-odbc.md) tabel i przy użyciu [parametry](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) na podstawie informacji uzyskanych lub obliczane w czasie wykonywania.

Zestaw rekordów wybiera tylko te rekordy, które spełniają określony warunek wyszukiwania. Na przykład, aby określić filtr kurs opisanych powyżej (zakładając, że zmienna `strCourseID` ustawione, na przykład "MATH101"), wykonaj następujące czynności:

```
// Using the recordset pointed to by m_pSet

// Set the filter
m_pSet->m_strFilter = "CourseID = " + strCourseID;

// Run the query with the filter in place
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )

// Use the recordset
```

Zestaw rekordów zawiera rekordy dla wszystkich sekcji klasy MATH101.

Zwróć uwagę, jak ciąg filtru został ustawiony w powyższym przykładzie, za pomocą zmiennej ciągu. Jest to typowy sposób użycia. Jednak Załóżmy, że chcesz określić wartość literału 100 dla identyfikatora kursu. Poniższy kod przedstawia sposób ustawiania ciągu filtru poprawnie z wartością literału:

```
m_strFilter = "StudentID = '100'";   // correct
```

Zwróć uwagę na użycie znaków pojedynczego cudzysłowu. Jeśli ustawisz ciąg filtru bezpośrednio, ciąg filtru jest **nie**:

```
m_strFilter = "StudentID = 100";   // incorrect for some drivers
```

Cytowanie, pokazanym powyżej jest zgodny ze specyfikacją ODBC, ale niektóre systemów DBMS, może być wymagane inne znaki cudzysłowu. Aby uzyskać więcej informacji, zobacz [SQL: dostosowywanie Your zestawu rekordów instrukcji SQL (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

> [!NOTE]
>  Jeśli zdecydujesz się zastąpić ciąg SQL domyślnego zestawu rekordów, przekazując własne parametry SQL do `Open`, nie należy ustawiać filtr, jeśli zawiera tekst niestandardowy **gdzie** klauzuli. Aby uzyskać więcej informacji na temat zastępowania domyślny kod SQL zobacz [SQL: dostosowywanie Your zestawu rekordów instrukcji SQL (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: sortowanie rekordów (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)<br/>
[Zestaw rekordów: jak zestawy rekordów pobierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Zestaw rekordów: jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[Zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)