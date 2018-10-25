---
title: 'SQL: Wykonywanie bezpośrednich wywołań SQL (ODBC) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SQL, direct calls from ODBC
- SQL, calling directly from ODBC
- ODBC, SQL calls
- SQL calls
- direct SQL calls from ODBC
ms.assetid: 091988d2-f5a5-4c2d-aa09-8779a9fb9607
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2201a8936c1f28221bfcb628139a979e042715b9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079223"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL: wykonywanie bezpośrednich wywołań SQL (ODBC)

W tym temacie opisano:

- Kiedy należy używać SQL bezpośrednich wywołań.

- [Jak utworzyć bezpośrednie SQL wywołania do źródła danych](#_core_making_direct_sql_function_calls).

> [!NOTE]
>  Te informacje dotyczą klas MFC ODBC. Pracy przy użyciu klas MFC DAO, zobacz temat "Porównanie programu Microsoft Jet bazy danych aparatu SQL i ANSI SQL" w Pomocy programu DAO.

##  <a name="_core_when_to_call_sql_directly"></a> Kiedy wywołania SQL bezpośrednio

Aby utworzyć nowe tabele, porzucić tabel (Usuń), zmienić istniejące tabele, tworzenie indeksów i wykonywać inne funkcje programu SQL, które zmieniają [źródła danych (ODBC)](../../data/odbc/data-source-odbc.md) schemat, należy wygenerować instrukcji SQL bezpośrednio do źródła danych przy użyciu bazy danych Język definicji (DDL). Korzystając z kreatora, aby utworzyć zestaw rekordów dla tabeli (w czasie projektowania), można wybrać kolumny tabeli do reprezentowania zestawu rekordów. To nie zezwala na kolumnach Ty lub inny użytkownik źródła danych do tabeli później dodać program został skompilowany. Klasy bazy danych nie obsługują bezpośrednio DDL, ale nadal można napisać kod, aby powiązać nową kolumnę rekordów dynamicznie w czasie wykonywania. Aby uzyskać informacji dotyczących sposobu wykonania tego powiązania, zobacz [zestaw rekordów: dynamiczne powiązanie danych kolumn (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Można użyć systemu DBMS, sama zmienić schemat lub innego narzędzia, które umożliwia wykonywanie funkcji języka DDL. Umożliwia także wywołania funkcji ODBC wysłać instrukcje SQL, takich jak wywoływanie wstępnie zdefiniowanego zapytania (procedura składowana), która nie zwraca rekordy.

##  <a name="_core_making_direct_sql_function_calls"></a> Wykonanie bezpośrednich wywołań funkcji SQL

Bezpośrednie wykonywanie, wywołania SQL przy użyciu [klasa CDatabase](../../mfc/reference/cdatabase-class.md) obiektu. Konfigurowanie usługi parametry instrukcji SQL (zwykle w `CString`) i przekazać ją do [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) funkcji składowej typu usługi `CDatabase` obiektu. Jeśli używasz wywołania funkcji ODBC do wysyłania instrukcji SQL, które zwykle zwraca rekordy, rekordy zostaną zignorowane.

## <a name="see-also"></a>Zobacz też

[SQL](../../data/odbc/sql.md)