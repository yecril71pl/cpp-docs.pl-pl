---
title: 'Wyjątki: Wyjątki bazy danych'
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
ms.openlocfilehash: c279c5b788cc7bd8a68fe36128c116d8df91c2eb
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095816"
---
# <a name="exceptions-database-exceptions"></a>Wyjątki: Wyjątki bazy danych

W tym artykule wyjaśniono, jak obsługiwać wyjątki bazy danych. Większość materiału w tym artykule ma zastosowanie do tego, czy pracujesz z klasami MFC dla Open Database Connectivity (ODBC) czy klas MFC dla obiektów dostępu do danych (DAO). Materiał specyficzny dla jednego lub innego modelu jest jawnie oznaczony. Tematy obejmują:

- [Podejścia do obsługi wyjątków](#_core_approaches_to_exception_handling)

- [Przykład obsługi wyjątku bazy danych](#_core_a_database_exception.2d.handling_example)

##  <a name="_core_approaches_to_exception_handling"></a>Podejścia do obsługi wyjątków

Podejście jest takie samo niezależnie od tego, czy pracujesz z DAO (przestarzałe) czy ODBC.

Należy zawsze pisać programy obsługi wyjątków, aby obsłużyć wyjątkowe warunki.

Najbardziej pragmatycznym podejściem do przechwytywania wyjątków bazy danych jest testowanie aplikacji z scenariuszami wyjątków. Ustal ewentualne wyjątki, które mogą wystąpić w przypadku operacji w kodzie, i wymuś wystąpienie wyjątku. Następnie sprawdź wyniki śledzenia, aby zobaczyć, jaki wyjątek jest zgłaszany, lub sprawdź zwrócone informacje o błędzie w debugerze. Dzięki temu wiadomo, które kody powrotu będą widoczne dla scenariuszy wyjątków, które są używane.

### <a name="error-codes-used-for-odbc-exceptions"></a>Kody błędów używane do wyjątków ODBC

Oprócz kodów powrotu zdefiniowanych przez platformę, które mają nazwy formularza **AFX_SQL_ERROR_XXX**, niektóre [CDBExceptions](../mfc/reference/cdbexception-class.md) są oparte na kodach powrotu [ODBC](../data/odbc/odbc-basics.md) . Kody powrotne dla takich wyjątków mają nazwy formularza **SQL_ERROR_XXX**.

Kody powrotne — zdefiniowane przez platformę i ODBC, które klasy bazy danych mogą zwracać są udokumentowane w elemencie członkowskim danych [m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode) klasy `CDBException`. Dodatkowe informacje na temat kodów powrotnych zdefiniowanych przez ODBC są dostępne w *dokumentacji programisty* zestawu ODBC SDK w bibliotece MSDN.

### <a name="error-codes-used-for-dao-exceptions"></a>Kody błędów używane dla wyjątków DAO

W przypadku wyjątków DAO więcej informacji jest zwykle dostępnych. Informacje o błędzie można uzyskać za pomocą trzech elementów członkowskich danych przechwyconego obiektu [CDaoException](../mfc/reference/cdaoexception-class.md) :

- [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) zawiera wskaźnik do obiektu [CDaoErrorInfo —](../mfc/reference/cdaoerrorinfo-structure.md) , który hermetyzuje informacje o błędach w kolekcji obiektów błędów skojarzonych z bazą danych.

- [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror) zawiera rozszerzony kod błędu z klas MFC DAO. Te kody błędów, które mają nazwy formularza **AFX_DAO_ERROR_XXX**, są udokumentowane w elemencie członkowskim danych w `CDaoException`.

- [m_scode](../mfc/reference/cdaoexception-class.md#m_scode) zawiera OLE **SCODE** z obiektów DAO, jeśli ma zastosowanie. Rzadko konieczna będzie współpraca z tym kodem błędu. Zwykle więcej informacji jest dostępnych w innych elementach członkowskich danych. Zobacz element członkowski danych, aby uzyskać więcej informacji na temat wartości **SCODE** .

Dodatkowe informacje o błędach DAO, typie obiektu błędu DAO i kolekcji błędów DAO są dostępne w klasie [CDaoException](../mfc/reference/cdaoexception-class.md).

##  <a name="_core_a_database_exception.2d.handling_example"></a>Przykład obsługi wyjątku bazy danych

Poniższy przykład próbuje utworzyć obiekt pochodny [CRecordset](../mfc/reference/crecordset-class.md)na stercie przy użyciu operatora **New** , a następnie otworzyć zestaw rekordów (dla źródła danych ODBC). Podobnie jak w przypadku klas DAO, zobacz sekcję "przykład wyjątku DAO" poniżej.

### <a name="odbc-exception-example"></a>Przykład wyjątku ODBC

Funkcja [Open](../mfc/reference/crecordset-class.md#open) member może zgłosić wyjątek (typu [CDBException](../mfc/reference/cdbexception-class.md) dla klas ODBC), dzięki czemu `Open` kod ten przenawiasuje wywołanie z blokiem **try** . Następny blok **catch** będzie przechwytywać `CDBException`. Można sprawdzić, czy sam obiekt wyjątku został wywołany `e`, ale w tym przypadku wystarczy wiedzieć, że próba utworzenia zestawu rekordów zakończyła się niepowodzeniem. Blok **catch** wyświetla okno komunikatu i czyści je, usuwając obiekt zestawu rekordów.

[!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]

### <a name="dao-exception-example"></a>Przykład wyjątku DAO

Przykład DAO jest podobny do przykładu dla ODBC, ale zazwyczaj można pobrać więcej rodzajów informacji. Poniższy kod również próbuje otworzyć zestaw rekordów. Jeśli ta próba zgłasza wyjątek, można przeanalizować element członkowski danych obiektu wyjątku w celu uzyskania informacji o błędzie. Podobnie jak w przypadku poprzedniego przykładu ODBC, prawdopodobnie wystarczy wiedzieć, że próba utworzenia zestawu rekordów nie powiodła się.

[!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]

Ten kod pobiera ciąg komunikatu o błędzie z elementu członkowskiego [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) obiektu Exception. MFC wypełnia ten element członkowski, gdy zgłasza wyjątek.

Aby zapoznać się z informacjami o błędzie zwracanymi przez `CDaoException` obiekt, zobacz klasy [CDaoException](../mfc/reference/cdaoexception-class.md) i [CDaoErrorInfo —](../mfc/reference/cdaoerrorinfo-structure.md).

Podczas pracy z bazami danych Microsoft Jet (. mdb) i w większości przypadków podczas pracy z ODBC, będzie dostępny tylko jeden obiekt błędu. W rzadkich przypadkach, gdy używasz źródła danych ODBC i występuje wiele błędów, można wykonać pętlę przez zbieranie błędów DAO na podstawie liczby błędów zwróconych przez [CDaoException:: GetErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount). Za każdym razem przez pętlę Wywołaj [CDaoException:: GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo) , aby uzupełnić `m_pErrorInfo` element członkowski danych.

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)
