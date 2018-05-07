---
title: 'Wyjątki: Wyjątki bazy danych | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 2168bc530accfdde6fad4d41cd68e94d3088f153
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="exceptions-database-exceptions"></a>Wyjątki: wyjątki bazy danych
W tym artykule opisano sposób obsługi wyjątków bazy danych. Większość materiału w tym artykule ma zastosowanie, czy użytkownik pracuje z klas MFC otwarte połączenie bazy danych (ODBC) lub klas MFC dla obiektów DAO (Data Access). Jawnie jest oznaczony jako materiałów specyficzne dla jednej lub innego modelu. Tematy obejmują:  
  
-   [Podejścia do obsługi wyjątków](#_core_approaches_to_exception_handling)  
  
-   [Przykład obsługa wyjątków bazy danych](#_core_a_database_exception.2d.handling_example)  
  
##  <a name="_core_approaches_to_exception_handling"></a> Podejścia do obsługi wyjątków  
 Podejście jest taki sam, czy użytkownik pracuje z DAO lub ODBC.  
  
 Programy obsługi wyjątków do obsługi wyjątkowe warunki zawsze należy zapisać.  
  
 Najbardziej pragmatyczne podejście do przechwytywanie wyjątków bazy danych służy do testowania aplikacji ze scenariuszami wyjątku. Ustal, prawdopodobnie wyjątki, które mogą wystąpić operacji w kodzie i wymuszanie wyjątek występuje. Następnie przejrzyj wyniki śledzenia, aby zobaczyć, jakie wyjątek lub zapoznaj się z informacjami zwrócony kod błędu w debugerze. Pozwoli to ustalić, który zwraca kody zobaczysz w scenariuszach wyjątek, używanego.  
  
### <a name="error-codes-used-for-odbc-exceptions"></a>Kody błędów, używany do ODBC — wyjątki  
 Oprócz kodów powrotnych zdefiniowane przez platformę, które mają nazwy w postaci **AFX_SQL_ERROR_XXX**, niektóre [CDBExceptions](../mfc/reference/cdbexception-class.md) są oparte na [ODBC](../data/odbc/odbc-basics.md) kody powrotne. Kody powrotne takich wyjątków mają nazwy w postaci **SQL_ERROR_XXX**.  
  
 Kody powrotne — zarówno zdefiniowane w ramach, jak i definicja ODBC — klasy baz danych może zwrócić, opisano w [m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode) element członkowski danych klasy `CDBException`. Dodatkowe informacje na temat kodów powrotnych zdefiniowany przez sterownik ODBC jest dostępna w zestawie SDK ODBC *Podręcznik programisty* w bibliotece MSDN.  
  
### <a name="error-codes-used-for-dao-exceptions"></a>Kody błędów używane dla wyjątków DAO  
 Wyjątki DAO więcej informacji znajduje się zwykle. Dostęp do informacji o błędach za pomocą trzech elementów członkowskich danych zgłoszony [CDaoException](../mfc/reference/cdaoexception-class.md) obiektu:  
  
-   [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) zawiera wskaźnik do [cdaoerrorinfo —](../mfc/reference/cdaoerrorinfo-structure.md) obiekt hermetyzujący informacje o błędzie w kolekcji w DAO błąd obiektów skojarzonych z bazy danych.  
  
-   [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror) zawiera kod błędu rozszerzonej z klas MFC DAO. Te kody błędów, które mają nazwy w postaci **AFX_DAO_ERROR_XXX**, opisano w element członkowski danych `CDaoException`.  
  
-   [m_scode](../mfc/reference/cdaoexception-class.md#m_scode) zawiera OLE `SCODE` obiektów DAO, jeśli ma to zastosowanie. Rzadko należy jednak pracować z tego kodu błędu. Zazwyczaj więcej informacji znajduje się w innych elementach członkowskich dwóch danych. Zobacz element członkowski danych, aby uzyskać więcej informacji `SCODE` wartości.  
  
 Dodatkowe informacje na temat błędów, typ obiektu DAO błąd i kolekcji błędów DAO DAO jest dostępnych w ramach klasy [CDaoException](../mfc/reference/cdaoexception-class.md).  
  
##  <a name="_core_a_database_exception.2d.handling_example"></a> Przykład obsługa wyjątków bazy danych  
 Poniższy przykład podejmie próbę utworzenia [crecordset —](../mfc/reference/crecordset-class.md)-pochodnych obiektów na stercie z **nowe** operatora, a następnie otwórz zestaw rekordów (dla źródła danych ODBC). Podobny przykład dla klasy DAO zobacz "DAO wyjątek przykład" poniżej.  
  
### <a name="odbc-exception-example"></a>Przykład wyjątek ODBC  
 [Otwórz](../mfc/reference/crecordset-class.md#open) funkcji członkowskiej może wywoływać wyjątek (typu [CDBException](../mfc/reference/cdbexception-class.md) dla klasy ODBC), dlatego ten kod nawiasy **Otwórz** wywołania z **spróbuj**  bloku. Kolejne **catch** bloku będzie przechwytywać `CDBException`. Można zbadać wyjątek samego obiektu, nazywany `e`, ale w takim przypadku wystarczy wiedzieć, że nie podjęto próbę utworzenia zestawu rekordów. **Catch** blok wyświetla komunikat i czyści przez usunięcie obiektu zestawu rekordów.  
  
 [!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]  
  
### <a name="dao-exception-example"></a>Przykład wyjątek DAO  
 W przykładzie DAO jest podobny do przykład ODBC, ale zazwyczaj można pobrać więcej rodzaje informacji. Poniższy kod również próbuje otworzyć zestaw rekordów. Jeśli taka próba zgłasza wyjątek, można sprawdzić element członkowski danych klasy obiekt wyjątku, aby uzyskać informacje o błędzie. Podobnie jak w poprzednim przykładzie ODBC, jest on prawdopodobnie wystarczająco, aby dowiedzieć się, że próba utworzenia zestawu rekordów nie powiodło się.  
  
 [!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]  
  
 Ten kod pobiera ciąg komunikat błędu z [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) członkiem dla obiekt wyjątku. MFC wypełnia tego elementu członkowskiego, gdy zgłasza wyjątek.  
  
 Omówienie informacji o błędach zwracanych przez `CDaoException` obiektów, zobacz klasy [CDaoException](../mfc/reference/cdaoexception-class.md) i [cdaoerrorinfo —](../mfc/reference/cdaoerrorinfo-structure.md).  
  
 Podczas pracy z bazami danych programu Microsoft Jet (.mdb) i w większości przypadków podczas pracy z ODBC, będą istnieć tylko jeden obiekt błąd. W rzadkich przypadkach, gdy używasz źródła danych ODBC i wiele błędów, może pętli za pośrednictwem DAO w kolekcji błędów na podstawie liczby błędy zwrócone przez [CDaoException::GetErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount). Zawsze przy użyciu pętli, wywołaj [CDaoException::GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo) uzupełnienie `m_pErrorInfo` element członkowski danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)

