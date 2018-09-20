---
title: 'Wyjątki: Baza danych wyjątki | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 804e93c45e4fb4d95b097c78d20df6a252626a36
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387370"
---
# <a name="exceptions-database-exceptions"></a>Wyjątki: wyjątki bazy danych

W tym artykule wyjaśniono, jak obsługiwać wyjątki bazy danych. Większość materiały, w tym artykule mają zastosowanie, czy pracujesz z klas MFC Open Database Connectivity (ODBC) lub klas MFC dla obiektów Data Access (DAO). Materiał specyficzne dla jednego lub innego modelu jest jawnie oznaczona. Tematy obejmują:

- [Podejścia do obsługi wyjątków](#_core_approaches_to_exception_handling)

- [Przykład obsługi wyjątków bazy danych](#_core_a_database_exception.2d.handling_example)

##  <a name="_core_approaches_to_exception_handling"></a> Podejścia do obsługi wyjątków

To podejście jest taki sam, czy pracujesz za pomocą DAO lub ODBC.

Należy zawsze wpisać obsługi wyjątków, aby obsłużyć wyjątkowych warunkach.

Najbardziej pragmatyczne podejście do przechwytywania wyjątków bazy danych służy do testowania aplikacji przy użyciu scenariuszy wyjątku. Określ, prawdopodobnie wyjątki, które mogą wystąpić w przypadku operacji w kodzie i wymusić wyjątek występuje. Sprawdź dane wyjściowe śledzenia, aby zobaczyć, jakie wyjątek lub zapoznaj się z informacjami zwrócony kod błędu w debugerze. Dzięki temu można dowiedzieć się, które zwracają kody, które zostaną wyświetlone w scenariuszach wyjątek, którego używasz.

### <a name="error-codes-used-for-odbc-exceptions"></a>Kody błędów wykorzystywane do obsługi wyjątków ODBC

Oprócz kody powrotne zdefiniowana przez strukturę, które mają nazwy w postaci **AFX_SQL_ERROR_XXX**, niektóre [CDBExceptions](../mfc/reference/cdbexception-class.md) opierają się na [ODBC](../data/odbc/odbc-basics.md) kody powrotne. Kody powrotne dla takie wyjątki mają nazwy w postaci **SQL_ERROR_XXX**.

Kody powrotne — zarówno zdefiniowanych, jak i definicja ODBC — klasy bazy danych może zwrócić, opisano w [m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode) element członkowski danych klasy `CDBException`. Dodatkowe informacje na temat kodów powrotnych zdefiniowane przez sterownik ODBC jest dostępna w zestawie SDK ODBC *odwołania programisty* w bibliotece MSDN.

### <a name="error-codes-used-for-dao-exceptions"></a>Kody błędów wykorzystywane do obsługi wyjątków DAO

Wyjątki DAO, więcej informacji znajduje się zwykle. Dostęp do informacji o błędach za pomocą trzech elementów członkowskich danych przechwycony [CDaoException](../mfc/reference/cdaoexception-class.md) obiektu:

- [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) zawiera wskaźnik do [cdaoerrorinfo —](../mfc/reference/cdaoerrorinfo-structure.md) obiekt, który hermetyzuje informacje o błędzie w kolekcji w DAO błąd obiektów skojarzonych z bazą danych.

- [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror) zawiera rozszerzony kod błędu z klas MFC DAO. Te kody błędów, które mają nazwy w postaci **AFX_DAO_ERROR_XXX**, opisano w składowej danych, które w `CDaoException`.

- [m_scode](../mfc/reference/cdaoexception-class.md#m_scode) zawiera OLE **SCODE** obiektów DAO, jeśli ma to zastosowanie. Rzadko potrzebne do pracy z tego kodu błędu, jednak. Zazwyczaj więcej informacji znajduje się w innych elementach członkowskich dwóch danych. Zobacz element członkowski danych, aby uzyskać więcej informacji na temat **SCODE** wartości.

Dodatkowe informacje na temat błędów DAO, typ obiektu DAO błędu i kolekcji DAO błędów jest dostępna w ramach klasy [CDaoException](../mfc/reference/cdaoexception-class.md).

##  <a name="_core_a_database_exception.2d.handling_example"></a> Przykład obsługi wyjątków bazy danych

Poniższy przykład podejmie próbę utworzenia [CRecordset](../mfc/reference/crecordset-class.md)-pochodnych obiektów na stosie przy użyciu **nowe** operatora, a następnie otwórz zestaw rekordów (dla źródła danych ODBC). Aby uzyskać podobny przykład dla klas DAO zobacz "DAO wyjątek przykład" poniżej.

### <a name="odbc-exception-example"></a>Przykład wyjątek ODBC

[Otwórz](../mfc/reference/crecordset-class.md#open) funkcji składowej może zgłosić wyjątek (typu [CDBException](../mfc/reference/cdbexception-class.md) dla klasy ODBC), dlatego ten kod w nawiasach `Open` wywołanie z **spróbuj** bloku. Kolejne **catch** bloku będzie przechwytywać `CDBException`. Można zbadać wyjątek samego obiektu, nazywany `e`, ale w tym przypadku jest wystarczająco dużo, aby dowiedzieć się, że nie można utworzyć zestaw rekordów. **Catch** blok Wyświetla okno komunikatu i czyści, usuwając obiekty zestawów rekordów.

[!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]

### <a name="dao-exception-example"></a>Przykład wyjątek DAO

Przykład DAO jest podobny do przykładu dla ODBC, ale zazwyczaj można pobrać więcej rodzajów informacji. Poniższy kod próbuje również otworzyć zestawu rekordów. Jeśli taka próba zgłasza wyjątek, można sprawdzić, składowa danych klasy obiektu wyjątku, aby uzyskać informacje o błędzie. Ponieważ w poprzednim przykładzie ODBC jest prawdopodobnie wystarczająco, aby wiedzieć, że nie można utworzyć zestaw rekordów.

[!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]

Ten kod pobiera ciąg komunikatu o błędzie z [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) składowej obiektu wyjątku. Po jego zgłasza wyjątek, MFC wprowadza tego elementu członkowskiego.

Omówienie informacji o błędzie zwrócony przez `CDaoException` obiektu, patrz klasy [CDaoException](../mfc/reference/cdaoexception-class.md) i [cdaoerrorinfo —](../mfc/reference/cdaoerrorinfo-structure.md).

Podczas pracy z bazami danych Microsoft Jet (.mdb) i w większości przypadków podczas pracy z ODBC, będzie istnieć tylko jeden obiekt błędu. W rzadkich przypadkach, gdy używasz źródła danych ODBC, i istnieje wiele błędów można pętli za pośrednictwem DAO w kolekcji błędów na podstawie liczby błędy zwrócone przez [CDaoException::GetErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount). Wywołaj każdym wykonaniu pętli [CDaoException::GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo) uzupełnienie `m_pErrorInfo` element członkowski danych.

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)

