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
ms.openlocfilehash: 2134fc41b604ffd659f9ee075abc9d462ff4f0db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093376"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL: wykonywanie bezpośrednich wywołań SQL (ODBC)
W tym temacie opisano:  
  
-   Kiedy należy używać SQL bezpośrednie wywołania.  
  
-   [Jak należy kierować SQL wywołuje ze źródłem danych](#_core_making_direct_sql_function_calls).  
  
> [!NOTE]
>  Te informacje dotyczą klasach MFC ODBC. Jeśli pracujesz z klas MFC DAO, zobacz temat "Porównanie z bazy danych aparatu SQL i ANSI SQL programu Microsoft Jet" w pomocy DAO.  
  
##  <a name="_core_when_to_call_sql_directly"></a> Kiedy bezpośrednio wywołać metodę SQL  
 Aby utworzyć nowe tabele, upuść tabele (Usuń), alter istniejące tabele, Utwórz indeksy i korzystać z innych funkcji SQL, które zmieniają [źródła danych (ODBC)](../../data/odbc/data-source-odbc.md) schemat, należy wygenerować instrukcję SQL bezpośrednio ze źródłem danych przy użyciu bazy danych Język definicji (DDL). Jeśli użyjesz kreatora, aby utworzyć zestaw rekordów dla tabeli (w czasie projektowania), można wybrać które kolumny tabeli do reprezentowania w zestawie rekordów. To nie zezwala na kolumny źródła danych użytkownika później dodać do tabeli program został skompilowany. Klasy baz danych nie obsługują DDL bezpośrednio, ale nadal można napisać kod, aby powiązać nowej kolumny zestawu rekordów dynamicznie w czasie wykonywania. Aby uzyskać informacje dotyczące wykonywania tego powiązania, zobacz [zestaw rekordów: dynamiczne wiązanie danych kolumn (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
 System DBMS, sama służy do zmiany schematu lub innego narzędzia umożliwiające wykonywanie funkcji DDL. Wywołania funkcji ODBC służy również do wysyłania instrukcji SQL, taką jak wywołanie wstępnie zdefiniowanego zapytania (procedury składowanej), która nie zwraca rekordów.  
  
##  <a name="_core_making_direct_sql_function_calls"></a> Tworzenie bezpośrednie wywołania funkcji SQL  
 Bezpośrednie wykonywanie, wywołania SQL za pomocą [cdatabase — klasa](../../mfc/reference/cdatabase-class.md) obiektu. Konfigurowanie ciągu instrukcji SQL (zazwyczaj w `CString`) i przekaż go do [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) funkcji członkowskiej klasy użytkownika `CDatabase` obiektu. Jeśli używasz wywołania funkcji ODBC do wysyłania instrukcji SQL, która zwykle zwraca rekordy rekordy są ignorowane.  
  
## <a name="see-also"></a>Zobacz też  
 [SQL](../../data/odbc/sql.md)