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
ms.openlocfilehash: e1cb5df4a93fc642ccf4d500a5eb93690b0b3d75
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86403829"
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC: bezpośrednie wywoływanie funkcji ODBC API

Klasy baz danych udostępniają łatwiejszy interfejs do [źródła danych](../../data/odbc/data-source-odbc.md) niż ODBC. W związku z tym klasy nie hermetyzują wszystkich interfejsów API ODBC. W przypadku wszystkich funkcji, które wykraczają poza możliwości klas, należy bezpośrednio wywołać funkcje interfejsu API ODBC. Na przykład, należy bezpośrednio wywołać funkcje wykazu ODBC ( `::SQLColumns` , `::SQLProcedures` , `::SQLTables` i inne).

> [!NOTE]
> Źródła danych ODBC są dostępne za pośrednictwem klas MFC ODBC, zgodnie z opisem w tym temacie lub za pośrednictwem klas obiektów dostępu do danych MFC (DAO).

Aby bezpośrednio wywołać funkcję interfejsu API ODBC, należy wykonać te same czynności, które należy wykonać w przypadku wykonywania wywołań bez struktury. Kroki te są następujące:

- Przydziel magazyn dla wszystkich wyników zwracanych przez wywołanie.

- Przekazywanie ODBC `HDBC` lub `HSTMT` dojście w zależności od sygnatury parametru funkcji. Aby pobrać uchwyt ODBC, użyj makra [AFXGetHENV](../../mfc/reference/database-macros-and-globals.md#afxgethenv) .

   Zmienne składowe `CDatabase::m_hdbc` i `CRecordset::m_hstmt` są dostępne, aby nie trzeba było samodzielnie przydzielać i inicjować.

- Prawdopodobnie Wywołaj dodatkowe funkcje ODBC, aby przygotować się do głównego wywołania lub wykonać te czynności.

- Cofnij przydział magazynu po zakończeniu.

Aby uzyskać więcej informacji na temat tych kroków, zobacz [informacje dotyczące programisty ODBC](/sql/odbc/reference/odbc-programmer-s-reference).

Oprócz tych kroków należy wykonać dodatkowe kroki w celu sprawdzenia funkcji zwracanych wartości, upewnić się, że program nie oczekuje na zakończenie wywołania asynchronicznego i tak dalej. Te ostatnie kroki można uprościć za pomocą makr AFX_SQL_ASYNC i AFX_SQL_SYNC. Aby uzyskać więcej informacji, zobacz [makra MFC i Globals](../../mfc/reference/mfc-macros-and-globals.md).

## <a name="see-also"></a>Zobacz też

[Podstawowe informacje dotyczące ODBC](../../data/odbc/odbc-basics.md)
