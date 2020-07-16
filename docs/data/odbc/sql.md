---
title: SQL
ms.date: 05/09/2019
helpviewer_keywords:
- database classes [C++], SQL statements
- SQL [C++]
- SQL [C++], ODBC
- ODBC [C++], SQL implementation
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
ms.openlocfilehash: cdceec9f4a6a39e9e1a50fc002d4220801e8d15a
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404271"
---
# <a name="sql"></a>SQL

SQL (Structured Query Language) to sposób komunikowania się z relacyjną bazą danych, która umożliwia definiowanie, wykonywanie zapytań, modyfikowanie i kontrolowanie danych. Przy użyciu składni SQL, można utworzyć instrukcję, która wyodrębnia rekordy zgodnie z określonymi kryteriami.

> [!NOTE]
> Te informacje dotyczą klas MFC ODBC. Jeśli pracujesz z klasami MFC DAO, zapoznaj się z tematem porównanie usługi Microsoft Jet Database Engine SQL i ANSI SQL w pomocy DAO.

Instrukcje SQL zaczynają się od zlecenia słowa kluczowego, takiego jak **Create** lub **SELECT**. SQL to bardzo zaawansowany język; Pojedyncza instrukcja może mieć wpływ na całą tabelę.

Istnieje wiele wersji programu SQL, z których każdy został opracowany z konkretnym systemem DBMS. Klasy baz danych MFC rozpoznają zestaw instrukcji SQL, które są zgodne ze specyfikacją projektu X/Open i Microsoft Access Group Common Applications Environment (CAE) SQL (1991). Aby uzyskać informacje o składni tych instrukcji, zobacz Dodatek C w dokumentacji [referencyjnej programu ODBC programmer's](/sql/odbc/reference/odbc-programmer-s-reference) .

W tym temacie objaśniono:

- [Relacja między ODBC i SQL](#_core_open_database_connectivity_.28.odbc.29).

- [Najpopularniejsze słowa kluczowe SQL używane przez klasy baz danych](#_core_the_database_classes).

- [Jak klasy baz danych używają języka SQL](#_core_how_the_database_classes_use_sql).

## <a name="open-database-connectivity-odbc"></a><a name="_core_open_database_connectivity_.28.odbc.29"></a>Open Database Connectivity (ODBC)

Klasy baz danych są implementowane za pomocą ODBC, która używa języka SQL w interfejsie na poziomie wywołań zamiast osadzania poleceń SQL w kodzie. ODBC używa programu SQL do komunikowania się ze [źródłem danych](../../data/odbc/data-source-odbc.md) za pośrednictwem sterowników ODBC. Te sterowniki interpretują dane SQL i tłumaczą je, w razie potrzeby, do użycia z określonym formatem bazy danych, takim jak Microsoft Access. Aby uzyskać więcej informacji na temat sposobu korzystania z programu SQL, zobacz [ODBC](../../data/odbc/odbc-basics.md) i Dokumentacja programu [ODBC programmer's Reference](/sql/odbc/reference/odbc-programmer-s-reference) .

## <a name="database-classes"></a><a name="_core_the_database_classes"></a>Klasy baz danych

> [!NOTE]
> Kreator użytkownika ODBC MFC nie jest dostępny w programie Visual Studio 2019 i nowszych. Nadal można utworzyć konsumenta ręcznie.

Klasy baz danych umożliwiają manipulowanie i aktualizowanie danych w istniejącym [źródle danych](../../data/odbc/data-source-odbc.md). [Kreator aplikacji MFC](../../mfc/reference/database-support-mfc-application-wizard.md), [Kreator użytkownika MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (dostęp za pośrednictwem **klasy Add Class**) i klasy baz danych konstruują większość instrukcji SQL.

Klasy baz danych używają części programu SQL znanej jako język manipulowania danymi (DML). Te polecenia pozwalają korzystać z wszystkich lub części źródła danych, dodawać nowe rekordy, edytować rekordy i usuwać rekordy. W poniższej tabeli wymieniono najpopularniejsze słowa kluczowe SQL i sposoby ich używania przez klasy baz danych.

### <a name="some-common-sql-keywords"></a>Niektóre typowe słowa kluczowe SQL

|Słowo kluczowe SQL|Kreatorzy i klasy baz danych używają go|
|-----------------|---------------------------------------------|
|**ZAZNACZENIA**|Aby określić, które tabele i kolumny w źródle danych mają być używane.|
|**MIEJSCU**|Aby zastosować filtr, który zawęża zaznaczenie.|
|**ORDER BY**|Aby zastosować porządek sortowania do zestawu rekordów.|
|**WSTAWIENIA**|Aby dodać nowe rekordy do zestawu rekordów.|
|**USUNIĘTY**|Aby usunąć rekordy z zestawu rekordów.|
|**AKTUALIZACJI**|Aby zmodyfikować pola rekordu.|

Ponadto klasy baz danych rozpoznają instrukcje **wywołania** ODBC, których można użyć do wywołania wstępnie zdefiniowanego zapytania (lub procedury składowanej) dla niektórych źródeł danych. Sterownik bazy danych ODBC interpretuje te instrukcje i zastępuje polecenie odpowiednie dla każdego systemu DBMS.

> [!NOTE]
> Nie wszystkie systemy DBMS obsługują instrukcje **wywoływania** .

Jeśli klasy nie mogą rozpoznać instrukcji dostarczonej przez użytkownika w programie `CRecordset::Open` , jest interpretowana jako nazwa tabeli.

Aby dowiedzieć się, jak struktura konstruuje instrukcje SQL, zobacz [zestaw rekordów: jak zestawy rekordów wybierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) i [SQL: dostosowywanie instrukcji SQL zestawu rekordów (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

Bazy danych SQL używają typów danych podobnych do tych używanych w językach C i C++. Aby poznać te podobieństwa, zobacz [SQL: SQL i C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

Więcej informacji na temat programu SQL, w tym listę obsługiwanych instrukcji SQL, typów danych, gramatyki SQL Core i odczytywania listy zalecanych publikacji dotyczących języka SQL, można znaleźć w dokumentacji programu [Microsoft SQL](/sql/) .

## <a name="how-the-database-classes-use-sql"></a><a name="_core_how_the_database_classes_use_sql"></a>Jak klasy baz danych używają języka SQL

Zestawy rekordów pochodne od klas baz danych używają ODBC do komunikowania się ze źródłem danych, a ODBC pobiera rekordy ze źródła danych przez wysłanie instrukcji SQL. W tym temacie opisano relację między klasami baz danych i SQL.

Zestaw rekordów tworzy instrukcję SQL, tworząc fragmenty instrukcji SQL w `CString` . Ciąg jest konstruowany jako instrukcja **SELECT** , która zwraca zestaw rekordów.

Gdy zestaw rekordów wywołuje ODBC w celu wysłania instrukcji SQL do źródła danych, Menedżer sterowników ODBC przekazuje instrukcję do sterownika ODBC, a sterownik wysyła go do bazowego systemu DBMS. System DBMS zwraca zestaw wyników rekordów, a sterownik ODBC zwraca rekordy do aplikacji. Klasy baz danych pozwalają programowi na dostęp do zestawu wyników w klasie języka C++ z bezpieczną typem pochodną `CRecordset` .

Poniższe tematy zawierają więcej informacji na temat używania języka SQL przez klasy baz danych:

- [SQL: dostosowywanie instrukcji SQL zestawu rekordów (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

- [SQL: typy danych SQL i C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)

- [SQL: wykonywanie bezpośrednich wywołań SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)

## <a name="see-also"></a>Zobacz też

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Podstawowe informacje dotyczące ODBC](../../data/odbc/odbc-basics.md)
