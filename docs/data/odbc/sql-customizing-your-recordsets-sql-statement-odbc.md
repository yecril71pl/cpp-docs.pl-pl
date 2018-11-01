---
title: 'SQL: dostosowywanie instrukcji SQL zestawu rekordów (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, SQL statements
- ODBC recordsets, SQL statements
- SQL statements, customizing
- SQL statements, recordset
- customizing SQL statements
- overriding, SQL statements
- SQL, opening recordsets
ms.assetid: 72293a08-cef2-4be2-aa1c-30565fcfbaf9
ms.openlocfilehash: 84ce18ccbf3cc59dd9c94826366595d2f128784f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459934"
---
# <a name="sql-customizing-your-recordsets-sql-statement-odbc"></a>SQL: dostosowywanie instrukcji SQL zestawu rekordów (ODBC)

W tym temacie opisano:

- Jak struktura tworzy instrukcji języka SQL

- Jak przesłonić instrukcji SQL

> [!NOTE]
>  Te informacje dotyczą klas MFC ODBC. Pracy przy użyciu klas MFC DAO, zobacz temat "Porównanie programu Microsoft Jet bazy danych aparatu SQL i ANSI SQL" w Pomocy programu DAO.

## <a name="sql-statement-construction"></a>Konstrukcja instrukcji SQL

Rekordów baz wybór rekordów przede wszystkim na SQL **wybierz** instrukcji. Kiedy Deklarujesz klasy za pomocą Kreatora zapisuje nadrzędnych wersję `GetDefaultSQL` funkcja elementu członkowskiego, który wygląda następująco (dla klasy zestaw rekordów o nazwie `CAuthors`).

```cpp
CString CAuthors::GetDefaultSQL()
{
    return "AUTHORS";
}
```

Domyślnie to zastąpienie zwraca nazwę tabeli, który określono za pomocą kreatora. W tym przykładzie nazwa tabeli to "Autorzy". Gdy później wywołana w zestawie rekordów `Open` funkcja elementu członkowskiego `Open` tworzy końcowe **wybierz** instrukcji formularza:

```
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]
       [ORDER BY m_strSort]
```

gdzie `table-name` można uzyskać przez wywołanie `GetDefaultSQL` i `rfx-field-list` są uzyskiwane z wywołania funkcji RFX w `DoFieldExchange`. Jest to, co można uzyskać **wybierz** instrukcję, chyba że jego zastąpienie przy użyciu nadrzędnych wersji w czasie wykonywania, mimo że można również zmodyfikować domyślna deklaracja przy użyciu parametrów lub filtru.

> [!NOTE]
>  Jeśli określisz nazwę kolumny, która zawiera (lub mogą zawierać) miejsca do magazynowania, należy ująć nazwę w nawiasy kwadratowe. Na przykład nazwa "Imię" powinna być "[First Name]".

Aby zastąpić domyślne **wybierz** instrukcji, przekazać ciąg zawierający pełną **wybierz** instrukcji po wywołaniu `Open`. Zestaw rekordów zamiast tworzenia własnej domyślny ciąg, korzysta z ciąg, który podasz. Jeśli zawiera zestawienie zastąpienie **gdzie** klauzuli nie zostanie określony filtr w `m_strFilter` ponieważ użytkownik będzie zmuszony filtrowania dwóch instrukcji. Podobnie jeśli zawiera zestawienie zastąpienie **ORDER BY** klauzuli, nie określaj sortowania w `m_strSort` tak, aby nie trzeba posortować dwóch instrukcji.

> [!NOTE]
>  Jeśli używasz ciągów literałów w filtry (lub innymi częściami instrukcji SQL), może być konieczne "oferta" (należy ująć w określonych ograniczników) takie ciągi z prefiksem literału specyficznych dla systemu DBMS i literał sufiks znak (lub znaki).

W zależności od systemu DBMS, mogą wystąpić specjalnych wymagań składni dla operacji, takich jak sprzężenia zewnętrzne. Aby uzyskać te informacje ze sterownika systemu DBMS, należy użyć funkcji ODBC. Na przykład wywołać `::SQLGetTypeInfo` dla określonego typu danych, takich jak `SQL_VARCHAR`, aby zażądać LITERAL_PREFIX do LITERAL_SUFFIX znaków. Jeśli piszesz kod niezależny od bazy danych, zobacz [Gramatyka języka SQL C: dodatku](/sql/odbc/reference/appendixes/appendix-c-sql-grammar) w [odwołania programisty ODBC](/sql/odbc/reference/odbc-programmer-s-reference) uzyskać szczegółowe informacje o składni.

Obiekty zestawów rekordów tworzy instrukcję SQL, która używa do wybierania rekordów, chyba że przyjmie niestandardową instrukcję SQL. Jak to zrobić zależy głównie od wartości przekazanej *lpszSQL* parametru `Open` funkcja elementu członkowskiego.

Ogólna postać SQL **wybierz** instrukcja jest:

```
SELECT [ALL | DISTINCT] column-list FROM table-list
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]
```

Jednym sposobem dodania **DISTINCT** — słowo kluczowe do instrukcji SQL zestawu rekordów jest osadzenie słowa kluczowego w pierwszym wywołaniu funkcji RFX w `DoFieldExchange`. Na przykład:

```
...
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);
...
```

> [!NOTE]
>  Tej techniki należy używać tylko w przypadku zestawu rekordów otwarty jako tylko do odczytu.

## <a name="overriding-the-sql-statement"></a>Zastępowanie instrukcji SQL

W poniższej tabeli przedstawiono możliwości *lpszSQL* parametr `Open`. Przypadki, w tabeli zostały wyjaśnione poniżej tabeli.

**LpszSQL parametru i wynikowy ciąg SQL**

|przypadek|Co to są przekazywane w lpszSQL|Wynikowa instrukcja SELECT|
|----------|------------------------------|------------------------------------|
|1|NULL|**Wybierz** *rfx pole listy* **FROM** *Nazwa tabeli*<br /><br /> `CRecordset::Open` wywołania `GetDefaultSQL` można pobrać nazwy tabeli. Wynikowy ciąg jest jednym z przypadków 2 do 5, w zależności od tego, co `GetDefaultSQL` zwraca.|
|2|Nazwa tabeli|**Wybierz** *rfx pole listy* **FROM** *Nazwa tabeli*<br /><br /> Lista pól jest pobierana z instrukcji RFX w `DoFieldExchange`. Jeśli `m_strFilter` i `m_strSort` nie są puste, dodaje **gdzie** i/lub **ORDER BY** klauzul.|
|3 \*|Kompletna **wybierz** instrukcji ale bez **gdzie** lub **ORDER BY** — klauzula|Jako zakończony powodzeniem. Jeśli `m_strFilter` i `m_strSort` nie są puste, dodaje **gdzie** i/lub **ORDER BY** klauzul.|
|4 \*|Kompletna **wybierz** instrukcję, określając **gdzie** i/lub **ORDER BY** — klauzula|Jako zakończony powodzeniem. `m_strFilter` i/lub `m_strSort` musi pozostać pusta lub dwóch filtru i/lub instrukcje sortowania są tworzone.|
|5 \*|Wywołanie procedury składowanej|Jako zakończony powodzeniem.|

\* `m_nFields` musi być mniejsza niż liczba kolumn określona w **wybierz** instrukcji. Typ danych każdej kolumny określone w **wybierz** instrukcja musi być taki sam jak typ danych w odpowiadającej jej kolumny RFX w danych wyjściowych.

### <a name="case-1---lpszsql--null"></a>Przypadek 1 lpszSQL = NULL

Wybór zestawu rekordów jest zależna od co `GetDefaultSQL` po `CRecordset::Open` ją wywołuje. Przypadków 2 do 5 opisano możliwe ciągów.

### <a name="case-2---lpszsql--a-table-name"></a>Przypadek 2 lpszSQL = Nazwa tabeli

Zestaw rekordów używa wymiana pól rekordów (RFX) do tworzenia listy kolumn z nazw kolumn, pod warunkiem w RFX funkcja wywołuje w przesłonięciu klasy zestawu rekordów z `DoFieldExchange`. Jeśli Kreator jest używany do deklarowania klasy zestawu rekordów, ten przypadek ma ten sam wynik jako przypadek 1 (pod warunkiem, że należy przekazać tę samą nazwę tabeli, które określiłeś w kreatorze). Jeśli nie używasz kreatora do zapisywania klasy przypadek 2 jest najprostszym sposobem konstruowania instrukcji SQL.

Poniższy przykład tworzy instrukcję SQL, która wybiera rekordy z bazy danych aplikacji MFC. Kiedy struktura wywołuje `GetDefaultSQL` funkcji członkowskiej, funkcja zwraca nazwę tabeli, `SECTION`.

```cpp
CString CEnrollSet::GetDefaultSQL()
{
    return "SECTION";
}
```

Uzyskiwanie nazwy kolumn dla SQL **wybierz** instrukcji, struktura wywołuje `DoFieldExchange` funkcja elementu członkowskiego.

```cpp
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

Po wykonaniu instrukcji SQL wygląda następująco:

```sql
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo
    FROM SECTION
```

### <a name="case-3---lpszsql--a-selectfrom-statement"></a>Przypadek 3 dotyczący lpszSQL = SELECT / z instrukcji

Określa listy kolumn są ręcznie zamiast polegać na RFX utworzyć automatycznie. Możesz chcieć od tego, czy podczas:

- Aby określić **DISTINCT** następujące słowa kluczowego **wybierz**.

   Twoja lista kolumn powinna odpowiadać nazwy kolumn i typy w tej samej kolejności wymienionych w `DoFieldExchange`.

- Masz powód, aby ręcznie pobrać wartości kolumny za pomocą funkcji ODBC `::SQLGetData` zamiast polegać na RFX powiązać, a następnie pobrać kolumn dla Ciebie.

   Na przykład, warto uwzględnić nowe kolumny, które po aplikacji została dystrybuowana do tabel bazy danych dodane klienta Twojej aplikacji. Należy dodać te dodatkowe pola danych elementów członkowskich, które nie były znane w czasie tej klasy jest zadeklarowana za pomocą kreatora.

   Twoja lista kolumn powinna odpowiadać nazwy kolumn i typy w tej samej kolejności wymienionych w `DoFieldExchange`, a następnie nazwy ręcznie powiązanych kolumn. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: dynamiczne powiązanie danych kolumn (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

- Chcesz dołączyć do tabel, określając wielu tabel w **FROM** klauzuli.

   Aby uzyskać informacje i obejrzeć przykład, zobacz [zestaw rekordów: wykonywanie Join (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

### <a name="case-4---lpszsql--selectfrom-plus-where-andor-order-by"></a>LpszSQL przypadku 4 = SELECT / z oraz gdzie i/lub ORDER BY

Określasz wszystko: Lista kolumn (wywołania RFX w oparciu o `DoFieldExchange`), listy tabel i zawartość **gdzie** i/lub **ORDER BY** klauzuli. Jeśli określisz swoje **gdzie** i/lub **ORDER BY** klauzule w ten sposób nie należy używać `m_strFilter` i/lub `m_strSort`.

### <a name="case-5---lpszsql--a-stored-procedure-call"></a>W przypadku 5 lpszSQL = przechowywane wywoływania

Jeśli musisz wywołać wstępnie zdefiniowanego zapytania (np. procedurę składowaną w bazie danych programu Microsoft SQL Server), należy napisać **WYWOŁANIA** instrukcji w ciągu, są przekazywane do *lpszSQL*. Kreatory nie obsługują deklarowanie klasy dla wstępnie zdefiniowanego zapytania podczas wywoływania zestawu rekordów. Nie wszystkie wstępnie zdefiniowanych zapytań zwracają rekordy.

Jeśli wstępnie zdefiniowane zapytanie nie zwraca rekordy, można użyć `CDatabase` funkcja elementu członkowskiego `ExecuteSQL` bezpośrednio. Dla wstępnie zdefiniowanego zapytania, które zwracają rekordy, należy również ręcznie napisać wywołuje RFX `DoFieldExchange` dla każdej kolumny zwraca procedury. Wywołania RFX musi znajdować się w tej samej kolejności i zwracać ten sam typ jako wstępnie zdefiniowanego zapytania. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: deklarowanie klasy dla wstępnie zdefiniowanego zapytania (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).

## <a name="see-also"></a>Zobacz też

[SQL: typy danych SQL i C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)<br/>
[SQL: wykonywanie bezpośrednich wywołań SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
