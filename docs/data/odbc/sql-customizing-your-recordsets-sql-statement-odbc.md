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
ms.openlocfilehash: 083d268d2b2f2eef072809b1afde9d6ea34f6996
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374517"
---
# <a name="sql-customizing-your-recordsets-sql-statement-odbc"></a>SQL: dostosowywanie instrukcji SQL zestawu rekordów (ODBC)

W tym temacie wyjaśniono:

- Jak struktura tworzy instrukcję SQL

- Jak zastąpić instrukcję SQL

> [!NOTE]
> Te informacje dotyczą klas Odbc MFC. Jeśli pracujesz z klasami DAO MFC, zobacz temat "Porównanie sql i SQL ansi programu MICROSOFT Jet Database Engine" w Pomocy DAO.

## <a name="sql-statement-construction"></a>Konstrukcja instrukcji SQL

Zestawienie rekordów opiera wybór rekordów głównie na instrukcji SQL **SELECT.** Podczas deklarowania klasy za pomocą kreatora zapisuje ona `GetDefaultSQL` nadrzędną wersję funkcji elementu członkowskiego, która `CAuthors`wygląda mniej więcej tak (dla klasy menedżera rekordów o nazwie ).

```cpp
CString CAuthors::GetDefaultSQL()
{
    return "AUTHORS";
}
```

Domyślnie to zastąpienie zwraca nazwę tabeli określoną za pomocą kreatora. W tym przykładzie nazwa tabeli to "AUTORZY". Po wywołaniu funkcji `Open` elementu członkowskiego zestawie `Open` rekordów, tworzy końcową instrukcję **SELECT** formularza:

```
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]
       [ORDER BY m_strSort]
```

gdzie `table-name` jest otrzymywany przez wywołanie `GetDefaultSQL` i `rfx-field-list` jest `DoFieldExchange`otrzymywany z wywołań funkcji RFX w . Jest to, co można uzyskać dla **select** instrukcji, chyba że zastąpić go z nadrzędną wersją w czasie wykonywania, chociaż można również zmodyfikować domyślną instrukcję z parametrami lub filtru.

> [!NOTE]
> Jeśli określisz nazwę kolumny zawierającą (lub mogącą zawierać) spacje, należy ją ująć w nawiasy kwadratowe. Na przykład nazwa "Imię" powinna być "[Imię]".

Aby zastąpić domyślną instrukcję **SELECT,** należy przekazać **SELECT** ciąg zawierający `Open`pełną instrukcję SELECT podczas wywoływania . Zamiast konstruowania własnego ciągu domyślnego, plik recordset używa ciągu, który dostarczasz. Jeśli instrukcja zastępowa zawiera klauzulę **WHERE,** nie należy określać filtru, `m_strFilter` ponieważ wówczas mają dwie instrukcje filtru. Podobnie jeśli instrukcja zastępowania zawiera klauzulę **ORDER BY,** nie należy określać sortowania, aby `m_strSort` nie mieć dwóch instrukcji sortowania.

> [!NOTE]
> Jeśli używasz ciągów literałów w filtrach (lub innych częściach instrukcji SQL), może być trzeba "cytat" (ująć w określonych ograniczników) takie ciągi z prefiksem literału specyficzne dla DBMS i literówka znak sufiksu (lub znaków).

Może również wystąpić specjalne wymagania składniowe dla operacji, takich jak sprzężenia zewnętrzne, w zależności od dbms. Użyj funkcji ODBC, aby uzyskać te informacje od sterownika dla systemu DBMS. Na przykład `::SQLGetTypeInfo` wywołać określonego typu danych, takich jak `SQL_VARCHAR`, aby zażądać LITERAL_PREFIX i LITERAL_SUFFIX znaków. Jeśli piszesz kod niezależny od bazy danych, zobacz [dodatek C: Gramatyka SQL](/sql/odbc/reference/appendixes/appendix-c-sql-grammar) w [odwołaniu programisty ODBC, aby](/sql/odbc/reference/odbc-programmer-s-reference) uzyskać szczegółowe informacje o składni.

Obiekt zestawie rekordów konstruuje instrukcję SQL używaną do wybierania rekordów, chyba że przekażesz niestandardową instrukcję SQL. Jak to zrobić zależy głównie od wartości, którą przekazujesz w `Open` *parametrze lpszSQL* funkcji elementu członkowskiego.

Ogólna forma instrukcji SQL **SELECT** jest:

```
SELECT [ALL | DISTINCT] column-list FROM table-list
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]
```

Jednym ze sposobów dodania słowa **kluczowego DISTINCT** do instrukcji SQL zestawie rekordów jest osadzenie `DoFieldExchange`słowa kluczowego w pierwszym wywołaniu funkcji RFX w programie . Przykład:

```
...
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);
...
```

> [!NOTE]
> Tej techniki należy używać tylko w przypadku, gdy jest otwarty jako tylko do odczytu.

## <a name="overriding-the-sql-statement"></a>Zastępowanie instrukcji SQL

W poniższej tabeli przedstawiono możliwości parametru *lpszSQL* do `Open`. Przypadki w tabeli są wyjaśnione po tabeli.

**Parametr lpszSQL i wynikowy ciąg SQL**

|Sprawa|Co przekazać w lpszSQL|Wynikowe SELECT instrukcji|
|----------|------------------------------|------------------------------------|
|1|NULL|**WYBIERZ** *rfx-field-list* **FROM** nazwa *tabeli*<br /><br /> `CRecordset::Open`wywołania, `GetDefaultSQL` aby uzyskać nazwę tabeli. Wynikowy ciąg jest jednym z przypadków od 2 `GetDefaultSQL` do 5, w zależności od tego, co zwraca.|
|2|Nazwa tabeli|**WYBIERZ** *rfx-field-list* **FROM** nazwa *tabeli*<br /><br /> Lista pól jest pobierana z instrukcji `DoFieldExchange`RFX w pliku . Jeśli `m_strFilter` `m_strSort` i nie są puste, dodaje **klauzule WHERE** i/lub **ORDER BY.**|
|3\*|Pełna instrukcja **SELECT,** ale bez klauzuli **WHERE** lub **ORDER BY**|Jak minęło. Jeśli `m_strFilter` `m_strSort` i nie są puste, dodaje **klauzule WHERE** i/lub **ORDER BY.**|
|4\*|Kompletna instrukcja **SELECT** z klauzulą **WHERE** i/lub **ORDER BY**|Jak minęło. `m_strFilter`i/lub `m_strSort` muszą pozostać puste, lub produkowane są dwie instrukcje filtrowania i/lub sortowania.|
|5\*|Wywołanie procedury składowanej|Jak minęło.|

\*`m_nFields` musi być mniejsza lub równa liczbie kolumn określonych w instrukcji **SELECT.** Typ danych każdej kolumny określonej w instrukcji **SELECT** musi być taki sam jak typ danych odpowiedniej kolumny wyjściowej RFX.

### <a name="case-1---lpszsql--null"></a>Przypadek 1 lpszSQL = NULL

Wybór pliku recordset `GetDefaultSQL` zależy `CRecordset::Open` od tego, co zwraca, gdy wywołuje go. Przypadki od 2 do 5 opisują możliwe ciągi.

### <a name="case-2---lpszsql--a-table-name"></a>Przypadek 2 lpszSQL = nazwa tabeli

Zestawienie rekordów używa wymiany pól rekordów (RFX) do tworzenia listy kolumn na podstawie nazw kolumn podanych w `DoFieldExchange`wywołaniach funkcji RFX w zastąpiono klasę zestawie rekordów . Jeśli do zadeklarowania klasy zestawu rekordów użyto kreatora, ten przypadek ma taki sam wynik jak przypadek 1 (pod warunkiem podania tej samej nazwy tabeli określonej w kreatorze). Jeśli nie używasz kreatora do pisania klasy, przypadek 2 jest najprostszym sposobem konstruowania instrukcji SQL.

Poniższy przykład tworzy instrukcję SQL, która wybiera rekordy z aplikacji bazy danych MFC. Gdy framework wywołuje `GetDefaultSQL` funkcję elementu członkowskiego, funkcja zwraca `SECTION`nazwę tabeli, .

```cpp
CString CEnrollSet::GetDefaultSQL()
{
    return "SECTION";
}
```

Aby uzyskać nazwy kolumn dla instrukcji SQL **SELECT,** struktura `DoFieldExchange` wywołuje funkcję elementu członkowskiego.

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

Po zakończeniu instrukcja SQL wygląda następująco:

```sql
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo
    FROM SECTION
```

### <a name="case-3---lpszsql--a-selectfrom-statement"></a>Przypadek 3 lpszSQL = instrukcja SELECT/FROM

Listę kolumn można określić ręcznie, a nie polegać na RFX, aby utworzyć ją automatycznie. Można to zrobić, gdy:

- Chcesz określić słowo kluczowe **DISTINCT** po **SELECT**.

   Lista kolumn powinna być zgodna z nazwami kolumn i `DoFieldExchange`typami w tej samej kolejności, w jakiej są wymienione w pliku .

- Masz powód, aby ręcznie pobierać wartości kolumn `::SQLGetData` przy użyciu funkcji ODBC, a nie polegać na RFX do powiązania i pobierania kolumn dla Ciebie.

   Można na przykład chcieć pomieścić nowe kolumny klienta aplikacji dodane do tabel bazy danych po aplikacji został rozesłany. Należy dodać te dodatkowe elementy członkowskie danych pola, które nie były znane w momencie deklarowania klasy za pomocą kreatora.

   Lista kolumn powinna być zgodna z nazwami kolumn i `DoFieldExchange`typami w tej samej kolejności, w jakiej są wymienione, a następnie nazwami kolumn powiązanych ręcznie. Aby uzyskać więcej informacji, zobacz [Zestaw rekordów: Dynamicznie wiążące kolumny danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

- Chcesz dołączyć do tabel, określając wiele tabel w klauzuli **FROM.**

   Aby uzyskać informacje i przykład, zobacz [Recordset: Performing a Join (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

### <a name="case-4---lpszsql--selectfrom-plus-where-andor-order-by"></a>Przypadek 4 lpszSQL = WYBIERZ/Z Plus GDZIE i/lub ZAMÓW WEDŁUG

Określ wszystko: listę kolumn (na podstawie wywołań RFX w), `DoFieldExchange`listę tabel i zawartość **klauzuli WHERE** i/lub ORDER **BY.** Jeśli określisz klauzule **WHERE** i/lub **ORDER BY** `m_strFilter` w ten `m_strSort`sposób, nie używaj i/lub .

### <a name="case-5---lpszsql--a-stored-procedure-call"></a>Przypadek 5 lpszSQL = wywołanie procedury składowanej

Jeśli chcesz wywołać wstępnie zdefiniowaną kwerendę (taką jak procedura składowana w bazie danych programu Microsoft SQL Server), należy napisać instrukcję **CALL** w ciągu przekazywanym do *programu lpszSQL*. Kreatorzy nie obsługują deklarowania klasy pliku recordset do wywoływania wstępnie zdefiniowanej kwerendy. Nie wszystkie wstępnie zdefiniowane kwerendy zwracają rekordy.

Jeśli wstępnie zdefiniowana kwerenda nie zwraca rekordów, `ExecuteSQL` można użyć funkcji `CDatabase` elementu członkowskiego bezpośrednio. W przypadku wstępnie zdefiniowanej kwerendy, która zwraca rekordy, należy również `DoFieldExchange` ręcznie zapisać wywołania RFX dla wszystkich kolumn zwraca procedurę. Wywołania RFX muszą być w tej samej kolejności i zwracać te same typy, co wstępnie zdefiniowane zapytanie. Aby uzyskać więcej informacji, zobacz [Recordset: Declaring a Class for a Predefined Query (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).

## <a name="see-also"></a>Zobacz też

[SQL: typy danych SQL i C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)<br/>
[SQL: wykonywanie bezpośrednich wywołań SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
