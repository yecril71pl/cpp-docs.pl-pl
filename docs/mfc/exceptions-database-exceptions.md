---
title: 'Wyjątki: wyjątki bazy danych'
ms.date: 09/17/2019
helpviewer_keywords:
- DAO [MFC], exceptions
- exceptions [MFC], database
- exception handling [MFC], databases
- ODBC exceptions [MFC]
- ODBC [MFC], exceptions
- database exceptions [MFC]
- databases [MFC], exception handling
- error codes [MFC], database exception handling
ms.assetid: 28daf260-f824-4be6-aecc-1f859e6dec26
ms.openlocfilehash: 894960338a7e8c293054ade00e0cdf3295648bb7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366625"
---
# <a name="exceptions-database-exceptions"></a>Wyjątki: wyjątki bazy danych

W tym artykule wyjaśniono, jak obsługiwać wyjątki bazy danych. Większość materiałów w tym artykule ma zastosowanie, czy pracujesz z klas MFC dla open database connectivity (ODBC) lub klas MFC dla obiektów dostępu do danych (DAO). Materiał specyficzny dla jednego lub drugiego modelu jest jawnie oznaczony. Tematy obejmują:

- [Podejścia do obsługi wyjątków](#_core_approaches_to_exception_handling)

- [Przykład obsługi wyjątków bazy danych](#_core_a_database_exception.2d.handling_example)

## <a name="approaches-to-exception-handling"></a><a name="_core_approaches_to_exception_handling"></a>Podejścia do obsługi wyjątków

Podejście jest takie samo, niezależnie od tego, czy pracujesz z DAO (przestarzałe) lub ODBC.

Zawsze należy napisać programy obsługi wyjątków do obsługi wyjątkowych warunków.

Najbardziej pragmatyczne podejście do przechwytywania wyjątków bazy danych jest do testowania aplikacji ze scenariuszami wyjątków. Określ prawdopodobne wyjątki, które mogą wystąpić dla operacji w kodzie i wymuś wystąpienie wyjątku. Następnie sprawdź dane wyjściowe śledzenia, aby zobaczyć, jaki wyjątek jest zgłaszany, lub sprawdź zwrócone informacje o błędzie w debugerze. Dzięki temu wiadomo, które kody zwrotne zobaczysz dla scenariuszy wyjątków, których używasz.

### <a name="error-codes-used-for-odbc-exceptions"></a>Kody błędów używane dla wyjątków ODBC

Oprócz kodów zwracanych zdefiniowanych przez strukturę, które mają nazwy formularza **AFX_SQL_ERROR_XXX,** niektóre [cdbexceptions](../mfc/reference/cdbexception-class.md) są oparte na kodach zwrotnych [ODBC.](../data/odbc/odbc-basics.md) Kody zwrotne dla takich wyjątków mają nazwy formularza **SQL_ERROR_XXX**.

Kody zwrotne — zarówno zdefiniowane przez framework, jak i zdefiniowane [m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode) przez ODBC — `CDBException`które klasy bazy danych mogą zwracać, są dokumentowane w m_nRetCode członka danych klasy. Dodatkowe informacje na temat kodów zwrotnych zdefiniowanych przez ODBC są dostępne w *odwołaniu programisty* SDK ODBC w bibliotece MSDN.

### <a name="error-codes-used-for-dao-exceptions"></a>Kody błędów używane dla wyjątków DAO

W przypadku wyjątków DAO zwykle dostępnych jest więcej informacji. Informacje o błędzie można uzyskać za pośrednictwem trzech elementów członkowskich danych przechwyconego obiektu [CDaoException:](../mfc/reference/cdaoexception-class.md)

- [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) zawiera wskaźnik do obiektu [CDaoErrorInfo,](../mfc/reference/cdaoerrorinfo-structure.md) który hermetyzuje informacje o błędzie w kolekcji dao obiektów błędów skojarzonych z bazą danych.

- [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror) zawiera rozszerzony kod błędu z klas DAO MFC. Te kody błędów, które mają nazwy formularza **AFX_DAO_ERROR_XXX,** są dokumentowane w obszarze element członkowski danych w `CDaoException`.

- [m_scode](../mfc/reference/cdaoexception-class.md#m_scode) zawiera kod **OLE** z DAO, jeśli dotyczy. Rzadko jednak trzeba będzie pracować z tym kodem błędu. Zazwyczaj więcej informacji jest dostępnych w pozostałych dwóch elementów członkowskich danych. Zobacz element członkowski danych, aby uzyskać więcej informacji na temat wartości **SCODE.**

Dodatkowe informacje o błędach DAO, typ obiektu błąd DAO i zbieranie błędów DAO są dostępne w ramach klasy [CDaoException](../mfc/reference/cdaoexception-class.md).

## <a name="a-database-exception-handling-example"></a><a name="_core_a_database_exception.2d.handling_example"></a>Przykład obsługi wyjątków bazy danych

Poniższy przykład próbuje skonstruować [CRecordset](../mfc/reference/crecordset-class.md)-pochodna obiektu na stercie z **nowym** operatorem, a następnie otworzyć zestaw rekordów (dla źródła danych ODBC). Podobny przykład dla klas DAO, zobacz "Przykład wyjątku DAO" poniżej.

### <a name="odbc-exception-example"></a>Przykład wyjątku ODBC

[Funkcja open](../mfc/reference/crecordset-class.md#open) elementu członkowskiego może zgłosić wyjątek (typu [CDBException](../mfc/reference/cdbexception-class.md) dla klas `Open` ODBC), więc ten kod nawiasy wywołania z **try** bloku. Kolejny blok **połowu** `CDBException`złapie . Można zbadać sam obiekt wyjątku, o nazwie `e`, ale w tym przypadku wystarczy wiedzieć, że próba utworzenia pliku recordset nie powiodła się. Blok **catch** wyświetla okno komunikatu i czyści się przez usunięcie obiektu pliku recordset.

[!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]

### <a name="dao-exception-example"></a>Przykład wyjątku DAO

Przykład DAO jest podobny do przykładu dla ODBC, ale zazwyczaj można pobrać więcej rodzajów informacji. Poniższy kod próbuje również otworzyć a recordset. Jeśli ta próba zgłasza wyjątek, można sprawdzić element członkowski danych obiektu wyjątku pod kątem informacji o błędzie. Podobnie jak w poprzednim przykładzie ODBC, prawdopodobnie wystarczy wiedzieć, że próba utworzenia pliku recordset nie powiodła się.

[!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]

Ten kod pobiera ciąg komunikatu o błędzie z [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) element członkowski obiektu wyjątku. MFC wypełnia tego elementu członkowskiego, gdy zgłasza wyjątek.

Aby zapoznać się z informacjami `CDaoException` o błędzie zwracanych przez obiekt, zobacz klasy [CDaoException](../mfc/reference/cdaoexception-class.md) i [CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md).

Podczas pracy z bazami danych Microsoft Jet (.mdb) i w większości przypadków podczas pracy z ODBC, będzie tylko jeden obiekt błędu. W rzadkich przypadkach, gdy używasz źródła danych ODBC i istnieje wiele błędów, można zapętlać przez zbieranie błędów DAO na podstawie liczby błędów zwróconych przez [CDaoException::GetErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount). Za każdym razem za pośrednictwem pętli, wywołać [CDaoException::GetErrorInfo,](../mfc/reference/cdaoexception-class.md#geterrorinfo) aby uzupełnić element członkowski `m_pErrorInfo` danych.

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)
