---
title: SQL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- database classes [C++], SQL statements
- SQL [C++]
- SQL [C++], ODBC
- ODBC [C++], SQL implementation
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0c4283e73b800ac0fd4d448d5137372807f893d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="sql"></a>SQL
SQL (Structured Query Language) to sposób komunikowania się z relacyjnej bazy danych, który pozwala zdefiniować, zapytania, modyfikowania i kontrolowanie danych. Przy użyciu składni SQL, można utworzyć instrukcję, która wyodrębnia rekordów w zależności od określonych kryteriów.  
  
> [!NOTE]
>  Te informacje dotyczą klasach MFC ODBC. Podczas pracy z klas MFC DAO, zobacz temat porównanie z bazy danych aparatu SQL programu Microsoft Jet i ANSI SQL w pomocy DAO.  
  
 Instrukcje SQL zaczynać zlecenie — słowo kluczowe takich jak **Utwórz** lub **wybierz**. SQL jest bardzo zaawansowaną języka; pojedyncza instrukcja może mieć wpływ na całą tabelę.  
  
 Istnieje wiele wersji programu SQL Server, każde rozwinięte z określonego systemu DBMS pamiętać. Klasy baz danych MFC rozpoznaje zestaw instrukcji SQL, które odpowiada x / Open i specyfikacja wersji roboczej SQL SQL dostępu grupy typowych aplikacji środowiska (CAE) (1991). Aby uzyskać informacje na temat składni te instrukcje, zobacz dodatek C w *ODBC SDK* *Podręcznik programisty* na dysku CD biblioteki MSDN.  
  
 W tym temacie opisano:  
  
-   [Relacja między ODBC i SQL](#_core_open_database_connectivity_.28.odbc.29).  
  
-   [Najbardziej typowe słów kluczowych SQL używane przez klasy baz danych](#_core_the_database_classes).  
  
-   [Jak korzystać z klasami baz danych SQL](#_core_how_the_database_classes_use_sql).  
  
##  <a name="_core_open_database_connectivity_.28.odbc.29"></a>Otwórz połączenie z bazą danych (ODBC)  
 Klasy baz danych są wdrażane z ODBC, który używa programu SQL w interfejsu poziom wywołania zamiast osadzania poleceń SQL w kodzie. ODBC używa SQL do komunikowania się z [źródła danych](../../data/odbc/data-source-odbc.md) za pomocą sterowników ODBC. Te sterowniki interpretacji SQL i tłumaczyć, jeśli jest to niezbędne do używania formatu określoną bazę danych, takich jak program Microsoft Access. Aby uzyskać więcej informacji o używaniu ODBC SQL, zobacz [ODBC](../../data/odbc/odbc-basics.md) i zestawu SDK ODBC *Podręcznik programisty* na dysku CD biblioteki MSDN.  
  
##  <a name="_core_the_database_classes"></a>Klasy baz danych  
 Klasy baz danych mają możliwość manipulowania i aktualizacji danych w istniejącym [źródła danych](../../data/odbc/data-source-odbc.md). [Kreator aplikacji MFC](../../mfc/reference/database-support-mfc-application-wizard.md), [Kreator konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (dostępnej za pośrednictwem **Dodaj klasę**), i klasy baz danych utworzyć większości instrukcji SQL dla Ciebie.  
  
 Klasy baz danych za pomocą część SQL znane jako manipulowania języka DML (Data). Te polecenia pozwalają pracować z całość lub część źródła danych, dodawać nowe rekordy edytowania rekordów i usuwania rekordów. Poniższa tabela zawiera listę typowych słów kluczowych SQL i metod klasy baz danych ich używać.  
  
### <a name="some-common-sql-keywords"></a>Niektóre typowe słów kluczowych SQL  
  
|Słowa kluczowego SQL|Używany kreatorów i klasy baz danych|  
|-----------------|---------------------------------------------|  
|**SELECT**|Aby określić, które tabele i kolumny w źródle danych mają być używane.|  
|**WHERE**|Aby zastosować filtr, który znajduje się w zakresie zaznaczenia.|  
|**ORDER BY**|Aby zastosować kolejność sortowania do zestawu rekordów.|  
|**WSTAW**|Dodawanie nowych rekordów do zestawu rekordów.|  
|**USUŃ**|Do usuwania rekordów z zestawu rekordów.|  
|**AKTUALIZACJA**|Aby zmodyfikować pola rekordu.|  
  
 Ponadto klasy baz danych rozpoznaje ODBC **WYWOŁAĆ** instrukcje, które można wywołać wstępnie zdefiniowanego zapytania (lub procedurę składowaną) dla niektórych źródeł danych. Sterownik bazy danych ODBC interpretuje tych instrukcji i zastępuje polecenie odpowiednie dla każdego systemu DBMS.  
  
> [!NOTE]
>  Nie wszystkie obsługują systemach DBMS **WYWOŁAĆ** instrukcje.  
  
 Jeśli klasy nie może rozpoznać instrukcję dostarczone przez użytkownika w `CRecordset::Open`, jest interpretowany jako nazwy tabeli.  
  
 Aby wyjaśnienie, jak w ramach tworzy instrukcji SQL, zobacz [zestaw rekordów: jak zestawy rekordów wybierz rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) i [SQL: instrukcja SQL Dostosowywanie Your w zestawie rekordów (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).  
  
 Bazy danych SQL Użyj typów danych, podobne do tych używanych w C i C++. Aby uzyskać informacje dotyczące tych podobieństwa, zobacz [SQL: SQL i typy danych języka C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).  
  
 Można znaleźć więcej informacji na temat SQL, łącznie z listą obsługiwanych instrukcji SQL, typy danych gramatyki SQL rdzeni i odczytu wykaz zalecanych publikacji o SQL, w *ODBC SDK* *Podręcznik programisty*  na dysku CD biblioteki MSDN.  
  
##  <a name="_core_how_the_database_classes_use_sql"></a>Jak korzystać z klasami baz danych SQL  
 Zestawy rekordów, który pochodzi od klasy baz danych używanie ODBC do komunikowania się ze źródłem danych i ODBC pobiera rekordy ze źródła danych, wysyłając instrukcji SQL. W tym temacie wyjaśniono relację między klasami baz danych i SQL.  
  
 Zestaw rekordów tworzy instrukcję SQL przez tworzenie części instrukcję SQL do `CString`. Ten ciąg jest tworzony jako **wybierz** instrukcja, która zwraca zestaw rekordów.  
  
 Gdy zestaw rekordów wywołuje ODBC do wysyłania instrukcję SQL w źródle danych, Menedżera sterowników ODBC przekazuje instrukcji do sterownika ODBC i sterownik wysyła go do odpowiedniego systemu DBMS. Systemu DBMS zwraca zestaw wyników rekordów i sterownik ODBC zwraca rekordy do aplikacji. Klasy baz danych let pochodną zestawu wyników w klasie C++ bezpieczny dostęp programu `CRecordset`.  
  
 Więcej informacji na temat jak korzystać z klasami baz danych SQL można znaleźć w następujących tematach:  
  
-   [SQL: Dostosowywanie instrukcji SQL zestawu rekordów (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)  
  
-   [SQL: typy danych SQL i C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)  
  
-   [SQL: wykonywanie bezpośrednich wywołań SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Otwórz połączenie z bazą danych (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Podstawy ODBC](../../data/odbc/odbc-basics.md)