---
title: SQL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- database classes [C++], SQL statements
- SQL [C++]
- SQL [C++], ODBC
- ODBC [C++], SQL implementation
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 17403899d5ace5f4e5fd3263da936d6665e331a9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053257"
---
# <a name="sql"></a>SQL

SQL (Structured Query Language) jest sposób komunikowania się z relacyjnej bazy danych, który pozwala zdefiniować zapytanie, modyfikować i kontrolowanie danych. Przy użyciu składni SQL, można skonstruować instrukcję, która wyodrębnia rekordów zgodnie z kryteriami, które określisz.

> [!NOTE]
>  Te informacje dotyczą klas MFC ODBC. Pracy przy użyciu klas MFC DAO, zobacz temat porównania programu Microsoft Jet aparat SQL Database i ANSI SQL w Pomocy programu DAO.

Instrukcje SQL zaczynają się od zlecenie — słowo kluczowe takich jak **Utwórz** lub **wybierz**. SQL jest bardzo zaawansowanym językiem; pojedynczej instrukcji może mieć wpływ na całą tabelę.

Istnieje wiele wersji programu SQL Server, każde rozwinięte z określonego systemu DBMS na uwadze. Klasy bazy danych MFC rozpoznaje zestaw instrukcji SQL, które odnosi się do X / Open i specyfikacja wersja robocza SQL dostępu grupy typowych aplikacji środowiska wspomaganych Komputerowo SQL (1991). Aby uzyskać informacje na temat składni te instrukcje, zobacz dodatek C w *ODBC SDK* *odwołania programisty* na dysku CD z biblioteki MSDN.

W tym temacie opisano:

- [Relacja między ODBC i SQL](#_core_open_database_connectivity_.28.odbc.29).

- [Najbardziej typowe słów kluczowych SQL używane przez klasy bazy danych](#_core_the_database_classes).

- [Jak korzystanie z klas baz danych SQL](#_core_how_the_database_classes_use_sql).

##  <a name="_core_open_database_connectivity_.28.odbc.29"></a> Open Database Connectivity (ODBC)

Klasy bazy danych są implementowane za pomocą ODBC, która używa języka SQL w poziomie wywołań za pomocą interfejsu zamiast osadzania poleceń SQL w kodzie. ODBC używa języka SQL do komunikowania się z [źródła danych](../../data/odbc/data-source-odbc.md) za pomocą sterowników ODBC. Te sterowniki interpretacji języka SQL i tłumaczenie, jeśli to konieczne, do użycia w formacie określonej bazy danych, takich jak program Microsoft Access. Aby uzyskać więcej informacji o używaniu ODBC SQL, zobacz [ODBC](../../data/odbc/odbc-basics.md) i zestawu SDK ODBC *odwołania programisty* na dysku CD z biblioteki MSDN.

##  <a name="_core_the_database_classes"></a> Klasy bazy danych

Klasy bazy danych są przeznaczone do umożliwiają manipulowanie i aktualizowanie danych w istniejącym [źródła danych](../../data/odbc/data-source-odbc.md). [Kreator aplikacji MFC](../../mfc/reference/database-support-mfc-application-wizard.md), [Kreator użytkownika interfejsu ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (dostępne za pośrednictwem **Dodaj klasę**), i klasy baz danych konstruowania większość instrukcji SQL dla Ciebie.

Klasy bazy danych użyj części programu SQL Server, znane jako język manipulacji danych (DML). Te polecenia pozwalają pracować w całości lub części źródła danych, dodawać nowe rekordy, edytowania rekordów i usuwania rekordów. W poniższej tabeli wymieniono najbardziej typowe słów kluczowych SQL, i sposoby klas baz danych, używać ich.

### <a name="some-common-sql-keywords"></a>Niektóre typowe słowa kluczowe SQL

|SQL — słowo kluczowe|Kreatory i klasy baz danych go używać|
|-----------------|---------------------------------------------|
|**SELECT**|Aby zidentyfikować, które tabele i kolumny w źródle danych mają być używane.|
|**WHERE**|Aby zastosować filtr, który Zawęża zaznaczenie.|
|**ORDER BY**|Aby zastosować kolejność sortowania do zestawu rekordów.|
|**WSTAW**|Aby dodać nowych rekordów do zestawu rekordów.|
|**USUŃ**|Do usuwania rekordów z zestawu rekordów.|
|**AKTUALIZACJA**|Aby zmodyfikować pola rekordu.|

Oprócz klas baz danych rozpoznaje ODBC **WYWOŁANIA** instrukcji, których można użyć, aby wywołać wstępnie zdefiniowanego zapytania (lub procedura składowana) dla niektórych źródeł danych. Sterownik bazy danych ODBC interpretuje tych instrukcji i zastępuje tego polecenia odpowiednio dla każdego systemu DBMS.

> [!NOTE]
>  Nie wszystkie obsługują systemów DBMS **WYWOŁANIA** instrukcji.

Jeśli klasy nie może rozpoznać oświadczenie dostarczone przez użytkownika w `CRecordset::Open`, będzie interpretowany jako nazwy tabeli.

Aby wyjaśnienie, jak struktura konstruuje instrukcje SQL, zobacz [zestaw rekordów: jak zestawy rekordów wybierz rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) i [SQL: dostosowywanie Your zestawu rekordów instrukcji SQL (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

Bazy danych SQL używać typów danych, podobne do tych w C i C++. Omówienie tych podobieństwa, zobacz [SQL: SQL i typów danych języka C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

Można znaleźć więcej informacji na temat języka SQL, w tym listę obsługiwanych instrukcji języka SQL, typy danych, Gramatyka języka SQL podstawowych i przeczytania zalecane publikacji o SQL, w *ODBC SDK* *Podręcznik programisty*  na dysku CD z biblioteki MSDN.

##  <a name="_core_how_the_database_classes_use_sql"></a> Jak korzystanie z klas baz danych SQL

Zestawy rekordów, które pochodzą z klasy bazy danych używanie ODBC do komunikowania się ze źródłem danych, a ODBC pobiera rekordy ze źródła danych, wysyłając instrukcji języka SQL. W tym temacie opisano relację między klasami bazy danych i SQL.

Zestaw rekordów konstruuje instrukcji języka SQL, budowanie rodzajów instrukcję SQL do `CString`. Ten ciąg jest konstruowany jako **wybierz** instrukcję, która zwraca zestaw rekordów.

Gdy zestaw rekordów wywołuje ODBC, aby wysłać instrukcję SQL do źródła danych, Menedżera sterowników ODBC przekazuje instrukcji ze sterownikiem ODBC i sterownik wysyła je do odpowiedniego systemu DBMS. Systemu DBMS zwraca zestaw wyników rekordów i sterownik ODBC zwraca rekordy do aplikacji. Klasy bazy danych umożliwiają dostęp programu zestawu wyników w bezpieczny klasy języka C++ jest pochodną `CRecordset`.

Więcej informacji na temat sposobu korzystanie z klas baz danych SQL można znaleźć w następujących tematach:

- [SQL: Dostosowywanie instrukcji SQL zestawu rekordów (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

- [SQL: typy danych SQL i C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)

- [SQL: wykonywanie bezpośrednich wywołań SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)

## <a name="see-also"></a>Zobacz też

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Podstawy ODBC](../../data/odbc/odbc-basics.md)