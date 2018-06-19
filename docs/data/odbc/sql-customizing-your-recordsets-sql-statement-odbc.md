---
title: 'SQL: Dostosowywanie instrukcji SQL zestawu rekordów (ODBC) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- recordsets, SQL statements
- ODBC recordsets, SQL statements
- SQL statements, customizing
- SQL statements, recordset
- customizing SQL statements
- overriding, SQL statements
- SQL, opening recordsets
ms.assetid: 72293a08-cef2-4be2-aa1c-30565fcfbaf9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f385127d1b61e1453eb7a079963da727f82f1874
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098592"
---
# <a name="sql-customizing-your-recordsets-sql-statement-odbc"></a>SQL: dostosowywanie instrukcji SQL zestawu rekordów (ODBC)
W tym temacie opisano:  
  
-   Jak tworzy instrukcję SQL w ramach  
  
-   Jak zastąpić instrukcji SQL  
  
> [!NOTE]
>  Te informacje dotyczą klasach MFC ODBC. Jeśli pracujesz z klas MFC DAO, zobacz temat "Porównanie z bazy danych aparatu SQL i ANSI SQL programu Microsoft Jet" w pomocy DAO.  
  
## <a name="sql-statement-construction"></a>Konstrukcja instrukcji SQL  
 Wybór rekordów przede wszystkim na SQL podstawowych zestawu rekordów **wybierz** instrukcji. Przy deklarowaniu klasy za pomocą Kreatora zapisuje zastępowanie wersji `GetDefaultSQL` funkcji członkowskiej, która wygląda następująco (klasa zestaw rekordów o nazwie `CAuthors`).  
  
```  
CString CAuthors::GetDefaultSQL()  
{  
    return "AUTHORS";  
}  
```  
  
 Domyślnie to zastąpienie zwraca nazwy tabeli określone przy użyciu kreatora. W tym przykładzie nazwa tabeli jest "AUTORÓW." Dzwoniąc później w zestawie rekordów **Otwórz** funkcji członkowskiej **Otwórz** tworzy końcowe **wybierz** instrukcji w postaci:  
  
```  
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]   
       [ORDER BY m_strSort]  
```  
  
 gdzie `table-name` są uzyskiwane przez wywołanie metody `GetDefaultSQL` i `rfx-field-list` są uzyskiwane z wywołania funkcji RFX w `DoFieldExchange`. Jest to, co możesz uzyskać **wybierz** instrukcji chyba, że można zastąpić go zastępowanie wersji w czasie wykonywania, mimo że można również zmodyfikować instrukcji domyślne parametry lub filtr.  
  
> [!NOTE]
>  Określ nazwę kolumny, która zawiera (lub może zawierać) spacji, należy należy wpisać nazwę w nawiasy kwadratowe. Na przykład nazwa "Imię" powinna być "[Nazwa pierwszego]".  
  
 Aby zastąpić domyślne **wybierz** instrukcji, przekazać ciąg zawierający pełnego **wybierz** instrukcji podczas wywoływania **Otwórz**. Zamiast tworzenia własnego domyślny ciąg, zestawu rekordów używa podanego ciągu. Jeśli zawiera instrukcję zastępczy **gdzie** klauzuli bez określania filtru w **m_strFilter** ponieważ użytkownik będzie zmuszony filtrować dwóch instrukcje. Podobnie jeśli zawiera instrukcję zastępczy **ORDER BY** klauzuli, nie należy określać sortowania w `m_strSort` tak, aby nie ma dwa sortowania instrukcje.  
  
> [!NOTE]
>  Użycie literałów ciągów w filtry (lub innych części instrukcji SQL), może być konieczne "oferta" (należy ująć w określonych ograniczników) sufiks takich ciągów z prefiksem literału specyficznych dla systemu DBMS i literału znaku (lub znaków).  
  
 Specjalne wymagania składni dla operacji, takich jak sprzężenia zewnętrzne, może wystąpić także w zależności od systemu DBMS. Użyj funkcji ODBC, aby uzyskać te informacje z sterownik dla systemu DBMS. Na przykład wywołać **:: SQLGetTypeInfo** dla określonego typu danych, takich jak **SQL_VARCHAR**, aby zażądać **LITERAL_PREFIX** i **LITERAL_SUFFIX** znaków. Jeśli piszesz kod niezależny od bazy danych, zobacz dodatek C w *ODBC SDK ** Podręcznik programisty* na dysku CD biblioteki MSDN, aby uzyskać szczegółowe informacje o składni.  
  
 Obiekty zestawów rekordów tworzy instrukcji SQL, która jest używana do wybierania rekordów, chyba że przekazujesz niestandardową instrukcję SQL. Jak to zrobić zależy głównie od wartości przekazywane w `lpszSQL` parametr **Otwórz** funkcję elementu członkowskiego.  
  
 Ogólny kształt SQL **wybierz** instrukcja jest:  
  
```  
SELECT [ALL | DISTINCT] column-list FROM table-list  
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]  
```  
  
 Aby dodać **DISTINCT** — słowo kluczowe do instrukcji SQL zestawu rekordów jest osadzenie słowo kluczowe w pierwszym wywołaniu funkcji RFX w `DoFieldExchange`. Na przykład:  
  
```  
...  
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);  
...  
```  
  
> [!NOTE]
>  Użyj tej techniki tylko w zestawie rekordów otwarty jako tylko do odczytu.  
  
## <a name="overriding-the-sql-statement"></a>Zastępowanie instrukcji SQL  
 W poniższej tabeli przedstawiono możliwości `lpszSQL` parametr **Otwórz**. Przypadki, w tabeli opisano w poniższej tabeli.  
  
 **LpszSQL parametru i wynikowy ciąg SQL**  
  
|Case|Przekaż w lpszSQL|Wynikowa instrukcji SELECT|  
|----------|------------------------------|------------------------------------|  
|1|**NULL**|**Wybierz** *rfx pole listy* **FROM** *nazwy tabeli*<br /><br /> `CRecordset::Open` wywołania `GetDefaultSQL` można pobrać nazwy tabeli. Wynikowy ciąg jest jednym z przypadków 2 do 5, w zależności od tego, co `GetDefaultSQL` zwraca.|  
|2|Nazwa tabeli|**Wybierz** *rfx pole listy* **FROM** *nazwy tabeli*<br /><br /> W oknie Lista pól jest pobierana z instrukcji RFX w `DoFieldExchange`. Jeśli **m_strFilter** i `m_strSort` nie są puste, dodaje **gdzie** i/lub **ORDER BY** klauzul.|  
|3 *|Kompletna **wybierz** instrukcji ale bez **gdzie** lub **ORDER BY** — klauzula|Jako zakończony pomyślnie. Jeśli **m_strFilter** i `m_strSort` nie są puste, dodaje **gdzie** i/lub **ORDER BY** klauzul.|  
|4 *|Kompletna **wybierz** instrukcji z **gdzie** i/lub **ORDER BY** — klauzula|Jako zakończony pomyślnie. **m_strFilter** i/lub `m_strSort` musi pozostać pusta lub dwóch filtru i/lub są produkowane instrukcje sortowania.|  
|5 *|Wywołanie procedury składowanej|Jako zakończony pomyślnie.|  
  
 \* `m_nFields` musi być mniejsza niż liczba kolumn określona w **wybierz** instrukcji. Typ danych każdej kolumny określone w **wybierz** instrukcja musi być taki sam jak typ danych w odpowiadającej mu kolumny RFX w danych wyjściowych.  
  
### <a name="case-1---lpszsql--null"></a>Przypadek 1 lpszSQL = NULL  
 Wybór rekordów jest zależna od co `GetDefaultSQL` po `CRecordset::Open` wywołuje go. Przypadków 2 do 5 opisano możliwe ciągów.  
  
### <a name="case-2---lpszsql--a-table-name"></a>LpszSQL przypadku 2 = Nazwa tabeli  
 Zestaw rekordów używa wymiana pól rekordów (RFX) do tworzenia listy kolumn z nazw kolumn, pod warunkiem w RFX funkcja wywołuje w przesłonięciu klasy zestawu rekordów `DoFieldExchange`. Jeśli użyjesz kreatora do zadeklarowania klasy rekordów przypadek ma ten sam rezultat jako przypadek 1 (pod warunkiem, że należy przekazać tę samą nazwę tabeli określonej w kreatorze). Jeśli użyjesz kreatora nie można zapisać klasy, przypadek 2 jest najprostszym sposobem tworzenia instrukcji SQL.  
  
 Poniższy przykład tworzy instrukcję SQL, która wybiera rekordy z bazy danych aplikacji MFC. Gdy struktura wywołuje `GetDefaultSQL` funkcji członkowskiej, funkcja zwraca nazwę tabeli, `SECTION`.  
  
```  
CString CEnrollSet::GetDefaultSQL()  
{  
    return "SECTION";  
}  
```  
  
 Uzyskaj nazwy kolumn dla SQL **wybierz** instrukcji, wywołania framework `DoFieldExchange` funkcję elementu członkowskiego.  
  
```  
void CEnrollSet::DoFieldExchange(CFieldExchange* pFX)  
{  
    pFX->SetFieldType(CFieldExchange::outputColumn);  
    RFX_Text(pFX, "CourseID", m_strCourseID);  
    RFX_Text(pFX, "InstructorID", m_strInstructorID);  
    RFX_Text(pFX, "RoomNo", m_strRoomNo);  
    RFX_Text(pFX, "Schedule", m_strSchedule);  
    RFX_Text(pFX, "SectionNo", m_strSectionNo);  
}  
```  
  
 Po ukończeniu instrukcji SQL wygląda następująco:  
  
```  
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo   
    FROM SECTION  
```  
  
### <a name="case-3---lpszsql--a-selectfrom-statement"></a>W przypadku 3 lpszSQL = SELECT / z instrukcji  
 Określa listy kolumn jest ręcznie zamiast polegania na RFX skonstruowanie automatycznie. Możesz chcieć od tego, czy podczas:  
  
-   Aby określić **DISTINCT** następujące słowa kluczowego **wybierz**.  
  
     Listy kolumny powinna być zgodna nazwy kolumn i typy w tej samej kolejności wymienionych w `DoFieldExchange`.  
  
-   Masz powód, aby ręcznie pobrać wartości w kolumnie przy użyciu funkcji ODBC **:: Procedura SQLGetData** zamiast polegania na RFX powiązania i pobrać kolumn.  
  
     Na przykład, warto uwzględnić nowe kolumny dodania klienta aplikacji w tabelach bazy danych po przeprowadzono aplikacji. Należy dodać te dodatkowe elementy członkowskie danych pola, które nie były znane w czasie tej klasy jest zadeklarowany za pomocą kreatora.  
  
     Listy kolumny powinna być zgodna nazwy kolumn i typy w tej samej kolejności wymienionych w `DoFieldExchange`, a następnie według nazwy ręcznie powiązane kolumny. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: dynamiczne wiązanie danych kolumn (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
-   Chcesz dołączyć, określając wielu tabel w tabel do **FROM** klauzuli.  
  
     Informacje i przykładem, zobacz [zestaw rekordów: wykonywanie Join (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).  
  
### <a name="case-4---lpszsql--selectfrom-plus-where-andor-order-by"></a>W przypadku 4 lpszSQL = wybierz / z oraz gdy i/lub ORDER BY  
 Określ wszystkie: Lista kolumn (oparte na wywołania RFX w `DoFieldExchange`), listy tabel i zawartość **gdzie** i/lub **ORDER BY** klauzuli. Jeśli określisz Twojej **gdzie** i/lub **ORDER BY** klauzule w ten sposób nie należy używać **m_strFilter** i/lub `m_strSort`.  
  
### <a name="case-5---lpszsql--a-stored-procedure-call"></a>W przypadku 5 lpszSQL = przechowywane wywoływania  
 Jeśli należy wywołać wstępnie zdefiniowanego zapytania (na przykład procedury przechowywanej w bazie danych programu Microsoft SQL Server), należy napisać **WYWOŁAĆ** instrukcji w ciągu, są przekazywane do `lpszSQL`. Kreatorzy nie obsługują deklarowanie klasy dla wstępnie zdefiniowanego zapytania podczas wywoływania zestawu rekordów. Nie wszystkie wstępnie zdefiniowane zapytania zwraca rekordów.  
  
 Jeśli wstępnie zdefiniowanego zapytania nie zwraca rekordy, można użyć `CDatabase` funkcji członkowskiej `ExecuteSQL` bezpośrednio. Dla wstępnie zdefiniowanego zapytania, która zwraca rekordy, musisz też ręcznie napisać odwołuje się RFX `DoFieldExchange` dla każdej kolumny zwraca procedury. Wywołania RFX musi znajdować się w tej samej kolejności i zwracać ten sam typ jako wstępnie zdefiniowanego zapytania. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: deklarowanie klasy dla wstępnie zdefiniowanego zapytania (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [SQL: SQL i typy danych języka C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)   
 [SQL: wykonywanie bezpośrednich wywołań SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
