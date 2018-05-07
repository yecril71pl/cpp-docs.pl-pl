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
ms.openlocfilehash: 4b4860726fa77d7b852290d8ea4680fe1bbbd86f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-filtering-records-odbc"></a>Zestaw rekordów: filtrowanie rekordów (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 W tym temacie wyjaśniono, jak do filtrowania zestawu rekordów tak, aby wybierało konkretnego podzestawu dostępne rekordy. Można na przykład wybierz klasy sekcje określonego ciągu, takich jak MATH101. Filtr jest warunek wyszukiwania zdefiniowane przez zawartość SQL **gdzie** klauzuli. Gdy w ramach dołącza go do instrukcji SQL zestawu rekordów, **gdzie** klauzuli ogranicza zaznaczenia.  
  
 Należy ustanowić filtru obiektu zestawu rekordów po konstruowania obiektu, ale przed wywołaniem jego **Otwórz** funkcji członkowskiej (lub przed wywołaniem **Requery** funkcji członkowskiej dla istniejącego zestawu rekordów obiekt, którego **Otwórz** została wywołana funkcja członkowska wcześniej).  
  
#### <a name="to-specify-a-filter-for-a-recordset-object"></a>Aby określić filtr dla obiekt zestawu rekordów  
  
1.  Utworzyć nowy obiekt zestawu rekordów (lub przygotowania do wywołania **Requery** istniejącego obiektu).  
  
2.  Ustaw wartość obiektu [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) element członkowski danych.  
  
     Filtr jest zerem ciąg, który zawiera zawartość SQL **gdzie** klauzuli, ale nie — słowo kluczowe **gdzie**. Na przykład użyć:  
  
    ```  
    m_pSet->m_strFilter = "CourseID = 'MATH101'";  
    ```  
  
     not  
  
    ```  
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";  
    ```  
  
    > [!NOTE]
    >  Ciąg literału "MATH101" jest wyświetlany w pojedynczy cudzysłów powyżej. W specyfikacji ODBC SQL apostrofy służą do oznaczania literału ciągu znaków. Zajrzyj do dokumentacji sterownika ODBC quoting wymagania w zakresie systemu DBMS w takiej sytuacji. Ta składnia jest również omówiona dalsze pod koniec w tym temacie.  
  
3.  Ustaw inne opcje, które są potrzebne, takie jak porządek sortowania, tryb blokowania lub parametrów. Określenie parametru jest szczególnie przydatne. Aby dowiedzieć się, jak ustawianie filtru, zobacz [zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
4.  Wywołanie **Otwórz** dla nowego obiektu (lub **Requery** dla obiekt wcześniej otwartych).  
  
> [!TIP]
>  Przy użyciu parametrów w filtrze jest potencjalnie najbardziej wydajne pobierania rekordów.  
  
> [!TIP]
>  Zestaw rekordów filtry są przydatne w przypadku [dołączenie](../../data/odbc/recordset-performing-a-join-odbc.md) tabel a za pomocą [parametry](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) na podstawie informacji uzyskanych lub obliczane w czasie wykonywania.  
  
 Zestaw rekordów wybiera tylko te rekordy, które spełniają określony warunek wyszukiwania. Na przykład, aby określić filtr kursu opisane powyżej (zakładając, że zmienna `strCourseID` obecnie ustawioną, na przykład "MATH101"), wykonaj następujące czynności:  
  
```  
// Using the recordset pointed to by m_pSet  
  
// Set the filter  
m_pSet->m_strFilter = "CourseID = " + strCourseID;   
  
// Run the query with the filter in place  
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )  
  
// Use the recordset  
```  
  
 Zestaw rekordów zawiera rekordy wszystkich sekcji klasy MATH101.  
  
 Zwróć uwagę, jak ciąg filtru został ustawiony w przykładzie przedstawionym powyżej przy użyciu zmiennej ciągu. To typowy sposób. Ale Załóżmy, że chcesz określić wartość literału 100 dla porach identyfikatora. Poniższy kod przedstawia sposób ustawiania ciąg filtru poprawnie z wartością literału:  
  
```  
m_strFilter = "StudentID = '100'";   // correct  
```  
  
 Zwróć uwagę na użycie znaków ujęty w apostrofy. Jeśli ustawisz ciąg filtru bezpośrednio, ciąg filtru jest **nie**:  
  
```  
m_strFilter = "StudentID = 100";   // incorrect for some drivers  
```  
  
 Zamykający pokazanym powyżej jest zgodny ze specyfikacją ODBC, ale w niektórych systemach DBMS może wymagać innych znaków cudzysłowu. Aby uzyskać więcej informacji, zobacz [SQL: dostosowywanie Your zestawu rekordów instrukcji SQL (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).  
  
> [!NOTE]
>  Jeśli chcesz zastąpić ciąg SQL domyślnego zestawu rekordów przez przekazanie własny ciąg SQL do **Otwórz**, nie należy ustawiać filtru, jeśli ma tekst niestandardowy **gdzie** klauzuli. Aby uzyskać więcej informacji na temat Zastępowanie domyślnego SQL, zobacz [SQL: dostosowywanie Your zestawu rekordów instrukcji SQL (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Zestaw rekordów: Sortowanie rekordów (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)   
 [Zestaw rekordów: Jak zestawy rekordów pobierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)   
 [Zestaw rekordów: Jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)   
 [Zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)