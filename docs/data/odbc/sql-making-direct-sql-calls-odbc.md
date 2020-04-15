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
ms.openlocfilehash: e2421e047d217fdc7a138509385399fa37d36a1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374497"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL: wykonywanie bezpośrednich wywołań SQL (ODBC)

W tym temacie wyjaśniono:

- Kiedy używać bezpośrednich wywołań SQL.

- [Sposób wykonywania bezpośrednich wywołań SQL do źródła danych](#_core_making_direct_sql_function_calls).

> [!NOTE]
> Te informacje dotyczą klas Odbc MFC. Jeśli pracujesz z klasami DAO MFC, zobacz temat "Porównanie sql i SQL ansi programu MICROSOFT Jet Database Engine" w Pomocy DAO.

## <a name="when-to-call-sql-directly"></a><a name="_core_when_to_call_sql_directly"></a>Kiedy bezpośrednio dzwonić do SQL

Aby utworzyć nowe tabele, upuścić (usunąć) tabele, zmienić istniejące tabele, utworzyć indeksy i wykonać inne funkcje SQL, które zmieniają schemat [źródła danych (ODBC),](../../data/odbc/data-source-odbc.md) należy wydać instrukcję SQL bezpośrednio do źródła danych przy użyciu języka definicji bazy danych (DDL). Korzystając z kreatora do utworzenia tablicy rekordów dla tabeli (w czasie projektowania), można wybrać kolumny tabeli do reprezentowania w tablicy rekordów. Nie zezwala to na kolumny, które użytkownik lub inny użytkownik źródła danych dodajesz do tabeli później, po skompilowaniu programu. Klasy bazy danych nie obsługują DDL bezpośrednio, ale nadal można napisać kod, aby powiązać nową kolumnę z plikiem rekordów dynamicznie, w czasie wykonywania. Aby uzyskać informacje dotyczące sposobu wykonywania tego powiązania, zobacz [Zestaw rekordów: Dynamicznie wiążące kolumny danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Za pomocą samego systemu dbms można zmienić schemat lub inne narzędzie, które umożliwia wykonywanie funkcji DDL. Można również użyć wywołań funkcji ODBC do wysyłania instrukcji SQL, takich jak wywołanie wstępnie zdefiniowanej kwerendy (procedury składowanej), która nie zwraca rekordów.

## <a name="making-direct-sql-function-calls"></a><a name="_core_making_direct_sql_function_calls"></a>Wykonywanie bezpośrednich wywołań funkcji SQL

Wywołanie SQL można wykonać bezpośrednio przy użyciu obiektu [klasy CDatabase.](../../mfc/reference/cdatabase-class.md) Skonfiguruj ciąg instrukcji `CString`SQL (zwykle w ) i przekaż go do funkcji elementu `CDatabase` członkowskiego [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) obiektu. Jeśli używasz wywołań funkcji ODBC do wysyłania instrukcji SQL, która zwykle zwraca rekordy, rekordy są ignorowane.

## <a name="see-also"></a>Zobacz też

[SQL](../../data/odbc/sql.md)
