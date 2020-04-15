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
ms.openlocfilehash: 208749438f40eef746a638dd12373397c426d454
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368666"
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC: bezpośrednie wywoływanie funkcji ODBC API

Klasy bazy danych zapewniają prostszy interfejs do [źródła danych](../../data/odbc/data-source-odbc.md) niż ODBC. W rezultacie klasy nie hermetyzują wszystkich interfejsów API ODBC. Dla wszystkich funkcji, które nie sz są poza możliwości klas, należy wywołać funkcje interfejsu API ODBC bezpośrednio. Na przykład należy wywołać funkcje`::SQLColumns`katalogu `::SQLProcedures` `::SQLTables`ODBC ( , , i inne) bezpośrednio.

> [!NOTE]
> Źródła danych ODBC są dostępne za pośrednictwem klas Odbc MFC, zgodnie z opisem w tym temacie lub za pośrednictwem klas obiektu dostępu do danych MFC (DAO).

Aby wywołać funkcję interfejsu API ODBC bezpośrednio, należy wykonać te same kroki, które należy podjąć, jeśli były wykonywanie wywołań bez struktury. Są to kroki:

- Przydziel magazyn dla wszelkich wyników, które zwraca wywołanie.

- Przekaż ODBC `HDBC` `HSTMT` lub dojście, w zależności od podpisu parametru funkcji. Użyj makra [AFXGetHENV,](../../mfc/reference/database-macros-and-globals.md#afxgethenv) aby pobrać uchwyt ODBC.

   Zmienne `CDatabase::m_hdbc` członkowskie `CRecordset::m_hstmt` i są dostępne, dzięki czemu nie trzeba przydzielić i zainicjować je samodzielnie.

- Być może wywołać dodatkowe funkcje ODBC, aby przygotować się do lub kontynuacji głównego połączenia.

- Przydziel przydział miejsca po zakończeniu.

Aby uzyskać więcej informacji na temat tych kroków, zobacz [SDK open database connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) w dokumentacji usługi MSDN.

Oprócz tych kroków należy podjąć dodatkowe kroki, aby sprawdzić wartości zwracane funkcji, upewnij się, że program nie czeka na wywołanie asynchroniczne, aby zakończyć i tak dalej. Ostatnie kroki można uprościć, korzystając z makr AFX_SQL_ASYNC i AFX_SQL_SYNC. Aby uzyskać więcej informacji, zobacz [Makra i globals](../../mfc/reference/mfc-macros-and-globals.md) w *odwołaniu MFC*.

## <a name="see-also"></a>Zobacz też

[Podstawy ODBC](../../data/odbc/odbc-basics.md)
