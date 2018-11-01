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
ms.openlocfilehash: 8c6781e0ff49b026e3b969f062f01e9923eb0a6c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665702"
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

Aby uzyskać więcej informacji na temat tych kroków, zobacz [Open Database Connectivity (ODBC)](/previous-versions/windows/desktop/ms710252) zestawu SDK w dokumentacji MSDN.

Oprócz tych kroków musisz wykonać dodatkowe czynności, aby sprawdzić wartości zwracane przez funkcję, upewnij się, że program nie czeka na wywołanie asynchroniczne zakończyć i tak dalej. AFX_SQL_ASYNC i AFX_SQL_SYNC makra można uprościć te ostatnie kroki. Aby uzyskać więcej informacji, zobacz [makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md) w *odwołanie MFC*.

## <a name="see-also"></a>Zobacz też

[Podstawy ODBC](../../data/odbc/odbc-basics.md)
