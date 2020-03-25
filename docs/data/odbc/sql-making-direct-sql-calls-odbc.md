---
title: 'SQL: wykonywanie bezpośrednich wywołań SQL (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- SQL, direct calls from ODBC
- SQL, calling directly from ODBC
- ODBC, SQL calls
- SQL calls
- direct SQL calls from ODBC
ms.assetid: 091988d2-f5a5-4c2d-aa09-8779a9fb9607
ms.openlocfilehash: 9240a227cdc4004d1e6e2b7ac26946ca233b71ec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212631"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL: wykonywanie bezpośrednich wywołań SQL (ODBC)

W tym temacie objaśniono:

- Kiedy używać bezpośrednich wywołań SQL.

- [Sposób wykonywania bezpośrednich wywołań SQL do źródła danych](#_core_making_direct_sql_function_calls).

> [!NOTE]
>  Te informacje dotyczą klas MFC ODBC. Jeśli pracujesz z klasami MFC DAO, zapoznaj się z tematem "porównanie usługi Microsoft Jet Database Engine SQL i ANSI SQL" w pomocy DAO.

##  <a name="when-to-call-sql-directly"></a><a name="_core_when_to_call_sql_directly"></a>Kiedy należy bezpośrednio wywołać SQL

Aby utworzyć nowe tabele, porzucić (usunąć) tabele, zmienić istniejące tabele, utworzyć indeksy i wykonać inne funkcje SQL, które zmieniają schemat [źródła danych (ODBC)](../../data/odbc/data-source-odbc.md) , należy wydać instrukcję SQL bezpośrednio do źródła danych przy użyciu języka definicji bazy danych (DDL). Gdy używasz Kreatora do tworzenia zestawu rekordów dla tabeli (w czasie projektowania), możesz wybrać kolumny tabeli do reprezentowania w zestawie rekordów. Nie jest to dozwolone w przypadku kolumn lub innych użytkowników źródła danych, które zostały później dodane do tabeli po skompilowaniu programu. Klasy baz danych nie obsługują języka DDL bezpośrednio, ale nadal można napisać kod, aby powiązać nową kolumnę z zestawem rekordów dynamicznie w czasie wykonywania. Aby uzyskać informacje o tym, jak to zrobić, zobacz [zestaw rekordów: dynamiczne powiązanie kolumn danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Za pomocą samego systemu DBMS można zmienić schemat lub inne narzędzie, które umożliwia wykonywanie funkcji języka DDL. Można również użyć wywołań funkcji ODBC do wysyłania instrukcji SQL, takich jak wywołanie wstępnie zdefiniowanego zapytania (procedura składowana), które nie zwraca rekordów.

##  <a name="making-direct-sql-function-calls"></a><a name="_core_making_direct_sql_function_calls"></a>Wykonywanie bezpośrednich wywołań funkcji SQL

Możesz bezpośrednio wykonać wywołanie SQL przy użyciu obiektu [klasy CDatabase](../../mfc/reference/cdatabase-class.md) . Skonfiguruj ciąg instrukcji SQL (zwykle w `CString`) i przekaż go do funkcji składowej [CDatabase:: ExecuteSql by](../../mfc/reference/cdatabase-class.md#executesql) obiektu `CDatabase`. Jeśli używasz wywołań funkcji ODBC do wysyłania instrukcji SQL, która zwykle zwraca rekordy, rekordy są ignorowane.

## <a name="see-also"></a>Zobacz też

[SQL](../../data/odbc/sql.md)
