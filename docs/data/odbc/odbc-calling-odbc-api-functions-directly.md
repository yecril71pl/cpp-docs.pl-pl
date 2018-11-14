---
title: 'ODBC: bezpośrednie wywoływanie funkcji ODBC API'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC API functions [C++], calling
- ODBC [C++], catalog functions
- ODBC API functions [C++]
- APIs [C++], calling
- ODBC classes [C++], vs. ODBC API
- direct ODBC API calls
- catalog functions (ODBC)
- catalog functions (ODBC), calling
- ODBC [C++], API functions
ms.assetid: 4295f1d9-4528-4d2e-bd6a-c7569953c7fa
ms.openlocfilehash: e76ff4da090a00409465333f8cbc9816ab4c4de6
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518349"
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC: bezpośrednie wywoływanie funkcji ODBC API

Klasy bazy danych zapewniają interfejs prostsze [źródła danych](../../data/odbc/data-source-odbc.md) niż ODBC. W rezultacie klasy nie hermetyzacji wszystkich interfejsów API ODBC. Dla żadnej funkcji, która znajduje się poza możliwościami klas możesz bezpośrednio wywołać funkcje interfejsu API ODBC. Na przykład, należy wywołać funkcje katalogu ODBC (`::SQLColumns`, `::SQLProcedures`, `::SQLTables`i inne) bezpośrednio.

> [!NOTE]
>  ODBC — źródła danych są dostępne za pośrednictwem klas MFC ODBC, zgodnie z opisem w tym temacie lub przy użyciu klas MFC obiekt DAO (Data Access).

Wywołanie funkcji interfejsu API ODBC bezpośrednio, należy wykonać te same czynności, które trzeba podjąć, jeśli zostały wywołań bez struktury. Są to czynności:

- Przydziel magazyn do żadnych wyników, które zwraca wywołanie.

- Przekaż ODBC `HDBC` lub `HSTMT` obsługi, w zależności od tego, podpis parametru funkcji. Użyj [afxgethenv —](../../mfc/reference/database-macros-and-globals.md#afxgethenv) makra można pobrać dojścia ODBC.

   Zmienne Członkowskie `CDatabase::m_hdbc` i `CRecordset::m_hstmt` są dostępne, dzięki czemu nie musisz przydzielić i zainicjować te samodzielnie.

- Być może wywołać dodatkowe funkcje ODBC, aby przygotować się do lub monitowanie główne wywołanie.

- Po zakończeniu, cofnięcie przydziału magazynu.

Aby uzyskać więcej informacji na temat tych kroków, zobacz [Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) zestawu SDK w dokumentacji MSDN.

Oprócz tych kroków musisz wykonać dodatkowe czynności, aby sprawdzić wartości zwracane przez funkcję, upewnij się, że program nie czeka na wywołanie asynchroniczne zakończyć i tak dalej. AFX_SQL_ASYNC i AFX_SQL_SYNC makra można uprościć te ostatnie kroki. Aby uzyskać więcej informacji, zobacz [makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md) w *odwołanie MFC*.

## <a name="see-also"></a>Zobacz też

[Podstawy ODBC](../../data/odbc/odbc-basics.md)
