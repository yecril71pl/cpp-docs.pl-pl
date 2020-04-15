---
title: SQL
ms.date: 05/09/2019
helpviewer_keywords:
- database classes [C++], SQL statements
- SQL [C++]
- SQL [C++], ODBC
- ODBC [C++], SQL implementation
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
ms.openlocfilehash: e5ab824f850b6050e11c10734dd709330af416b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376440"
---
# <a name="sql"></a>SQL

SQL (Structured Query Language) to sposób komunikowania się z relacyjną bazą danych, która umożliwia definiowanie, wykonywanie zapytań, modyfikowanie i kontrolowanie danych. Za pomocą składni SQL, można skonstruować instrukcję, która wyodrębnia rekordy zgodnie z kryteriami określonymi.

> [!NOTE]
> Te informacje dotyczą klas Odbc MFC. Jeśli pracujesz z klasami DAO MFC, zobacz temat Porównanie microsoft jet database engine SQL i ANSI SQL w Pomocy DAO.

Instrukcje SQL zaczynają się od zlecenia słowa kluczowego, takiego jak **CREATE** lub **SELECT**. SQL jest bardzo potężnym językiem; pojedyncza instrukcja może mieć wpływ na całą tabelę.

Istnieje wiele wersji języka SQL, z których każda została opracowana z myślą o konkretnym dbms. Klasy bazy danych MFC rozpoznają zestaw instrukcji SQL, które odpowiadają specyfikacji wersji roboczej SQL (CAE) (1991) X/Open i SQL Access Group Common Applications Environment (CAE). Aby uzyskać informacje na temat składni tych instrukcji, zobacz dodatek C w *odwołaniu programisty* *SDK ODBC* na dysku CD biblioteki MSDN.

W tym temacie wyjaśniono:

- [Relacja między ODBC i SQL](#_core_open_database_connectivity_.28.odbc.29).

- [Najczęściej używane przez klasy klas bazy danych słowa kluczowe SQL](#_core_the_database_classes).

- [Jak klasy bazy danych używają języka SQL](#_core_how_the_database_classes_use_sql).

## <a name="open-database-connectivity-odbc"></a><a name="_core_open_database_connectivity_.28.odbc.29"></a>Łączność z otwartą bazą danych (ODBC)

Klasy bazy danych są implementowane za pomocą odbc, który używa SQL w interfejsie na poziomie wywołania, a nie osadzanie poleceń SQL w kodzie. ODBC używa sql do komunikowania się [ze źródłem danych](../../data/odbc/data-source-odbc.md) za pośrednictwem sterowników ODBC. Sterowniki te interpretują sql i tłumaczą go, jeśli to konieczne, do użytku z określonym formatem bazy danych, takim jak Microsoft Access. Aby uzyskać więcej informacji na temat sposobu używania języka SQL przez odbc [i](../../data/odbc/odbc-basics.md) *odwołania programisty* SDK ODBC na dysku CD biblioteki MSDN.

## <a name="database-classes"></a><a name="_core_the_database_classes"></a>Klasy bazy danych

> [!NOTE]
> Kreator konsumenta odbc MFC nie jest dostępny w programie Visual Studio 2019 i nowszych. Nadal można utworzyć konsumenta ręcznie.

Klasy bazy danych są przeznaczone do manipulowania i aktualizowania danych w istniejącym [źródle danych.](../../data/odbc/data-source-odbc.md) [Kreator aplikacji MFC](../../mfc/reference/database-support-mfc-application-wizard.md), [Kreator konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (dostępny za pośrednictwem **dodaj klasę)** i klasy bazy danych konstruują większość instrukcji SQL dla Ciebie.

Klasy bazy danych używają części JĘZYKA SQL znanej jako język manipulowania danymi (DML). Te polecenia umożliwiają pracę z całością lub częścią źródła danych, dodawanie nowych rekordów, edytowanie rekordów i usuwanie rekordów. W poniższej tabeli wymieniono najczęściej używane słowa kluczowe SQL oraz sposoby, w jakie klasy bazy danych z nich korzystają.

### <a name="some-common-sql-keywords"></a>Niektóre typowe słowa kluczowe SQL

|Słowo kluczowe SQL|Używają go kreatorzy i klasy bazy danych|
|-----------------|---------------------------------------------|
|**Wybierz**|Aby określić, które tabele i kolumny w źródle danych mają być używane.|
|**WHERE**|Aby zastosować filtr, który zawęża zaznaczenie.|
|**ORDER BY**|Aby zastosować kolejność sortowania do pliku recordset.|
|**Wstawić**|Aby dodać nowe rekordy do akusu.|
|**Usunąć**|Aby usunąć rekordy z aeutu.|
|**Aktualizacji**|Aby zmodyfikować pola rekordu.|

Ponadto klasy bazy danych rozpoznają instrukcje ODBC **CALL,** których można używać do wywoływania wstępnie zdefiniowanej kwerendy (lub procedury składowanej) w niektórych źródłach danych. Sterownik bazy danych ODBC interpretuje te instrukcje i zastępuje polecenie odpowiednie dla każdego dbms.

> [!NOTE]
> Nie wszystkie dbmss obsługuje **instrukcje CALL.**

Jeśli klasy nie mogą rozpoznać `CRecordset::Open`instrukcji dostarczonej przez użytkownika w , jest interpretowana jako nazwa tabeli.

Aby uzyskać wyjaśnienie, w jaki sposób struktura konstruuje instrukcje SQL, zobacz [Recordset: How Recordsets Select Records (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) i [SQL: Customizing Your Recordset's SQL Statement (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

Bazy danych SQL używają typów danych podobnych do tych używanych w językach C i C++. Aby zapoznać się z tymi podobieństwami, zobacz [SQL: SQL i C++ Data Types (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

Więcej informacji na temat języka SQL można znaleźć w programie SQL, w tym o liście obsługiwanych instrukcji SQL, typach danych, gramatyki rdzenia SQL oraz na liście do czytania zalecanych publikacji dotyczących języka SQL, w *odwołaniu programisty* *SDK ODBC* na dysku CD biblioteki MSDN.

## <a name="how-the-database-classes-use-sql"></a><a name="_core_how_the_database_classes_use_sql"></a>Jak klasy bazy danych używają sql

Zestawy rekordów pochodzące z klas bazy danych używają odbc do komunikowania się ze źródłem danych, a ODBC pobiera rekordy ze źródła danych, wysyłając instrukcje SQL. W tym temacie wyjaśniono relację między klasami bazy danych a sql.

Zestaw rekordów konstruuje instrukcję SQL, budując fragmenty `CString`instrukcji SQL w pliku . Ciąg jest skonstruowany jako **select** instrukcji, która zwraca zestaw rekordów.

Gdy zestaw rekordów wywołuje odbc do wysłania instrukcji SQL do źródła danych, Menedżer sterowników ODBC przekazuje instrukcję do sterownika ODBC i sterownik wysyła go do podstawowego systemu dbms. Usługa DBMS zwraca zestaw rekordów wyników, a sterownik ODBC zwraca rekordy do aplikacji. Klasy bazy danych umożliwiają programowi dostęp do wyników ustawionych w `CRecordset`klasie C++ 30% wywodzącej się z klasy .

Następujące tematy zawierają więcej informacji na temat sposobu używania języka SQL przez klasy bazy danych:

- [SQL: Dostosowywanie instrukcji SQL (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

- [SQL: typy danych SQL i C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)

- [SQL: wykonywanie bezpośrednich wywołań SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)

## <a name="see-also"></a>Zobacz też

[Łączność z otwartą bazą danych (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Podstawy ODBC](../../data/odbc/odbc-basics.md)
