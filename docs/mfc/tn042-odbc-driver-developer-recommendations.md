---
title: "TN042: Zalecenia dla deweloperów sterowników ODBC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.odbc
dev_langs:
- C++
helpviewer_keywords:
- ODBC drivers [MFC], writing
- databases [MFC], ODBC
- TN042
ms.assetid: ecc6b5d9-f480-4582-9e22-8309fe561dad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ad6361266ebf2f09b8f34d150de835b25c55720b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tn042-odbc-driver-developer-recommendations"></a>TN042: zalecenia dla deweloperów sterowników ODBC
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 Ta uwaga wskazówki autorzy sterownika ODBC. Go przedstawiono ogólne wymagania i założenia ODBC funkcje, które należy klasy baz danych MFC i różnych szczegółów semantycznego oczekiwanego. Wymagane funkcje sterownika obsługujące trzech `CRecordset` Otwórz tryby (**forwardOnly**, **migawki** i **dynamiczny**) opisano.  
  
## <a name="odbcs-cursor-library"></a>Biblioteka kursorów ODBC firmy  
 Klasy baz danych MFC przedstawia funkcji użytkownika, dla którego w wielu przypadkach przekracza funkcje udostępniane przez większość sterowników ODBC poziomu 1. Na szczęście — Biblioteka kursorów ODBC firmy warstwy się między klasami bazy danych i sterownik i automatycznie udostępnić znacznie to dodatkowe funkcje.  
  
 Na przykład większość sterowników 1.0 nie obsługują przewijanie do tyłu. Biblioteka kursorów, można wykrywać i będzie pamięci podręcznej wierszy w sterowniku i przedstawia je zgodnie z wymaganiami dla wywołań FETCH_PREV w **procedury SQLExtendedFetch**.  
  
 Innym przykładem ważne zależność biblioteki kursora jest Aktualizacje pozycjonowane. Większość sterowników 1.0 również nie mają aktualizacje pozycjonowane, ale z biblioteki kursorów wygeneruje instrukcje aktualizacji, które identyfikują wiersz docelowy w źródle danych, na podstawie jego bieżące wartości danych z pamięci podręcznej lub wartość znacznika czasu pamięci podręcznej.  
  
 Biblioteka klas nigdy nie korzysta z wielu zestawów wierszy. W związku z tym kilka **SQLSetPos** instrukcje są zawsze stosowane do wiersza 1 zestawu wierszy.  
  
## <a name="cdatabases"></a>CDatabases  
 Każdy `CDatabase` przydziela pojedynczy **HDBC**. (Jeśli `CDatabase`w `ExecuteSQL` funkcja jest używana, **HSTMT** tymczasowo został przydzielony.) Dlatego w przypadku wielu `CDatabase`firmy są wymagane, wiele **HDBC**s na **HENV** muszą być obsługiwane.  
  
 Klasy baz danych wymaga z biblioteki kursorów. Znajduje to odzwierciedlenie w **SQLSetConnections** wywołać **SQL_ODBC_CURSORS**, **SQL_CUR_USE_ODBC**.  
  
 **SQLDriverConnect**, **SQL_DRIVER_COMPLETE** jest używany przez `CDatabase::Open` do nawiązania połączenia ze źródłem danych.  
  
 Sterownik musi obsługiwać **SQLGetInfo SQL_ODBC_API_CONFORMANCE** >= **SQL_OAC_LEVEL1**, **SQLGetInfo SQL_ODBC_SQL_CONFORMANCE**  >=  **SQL_OSC_MINIMUM**.  
  
 Aby transakcji do obsługi dla `CDatabase` i jego zależne zestawy rekordów **SQLGetInfo SQL_CURSOR_COMMIT_BEHAVIOR** i **SQL_CURSOR_ROLLBACK_BEHAVIOR** musi mieć **SQL_CR_PRESERVE**. W przeciwnym razie próby wykonania transakcji formantu zostanie zignorowany.  
  
 **SQLGetInfo SQL_DATA_SOURCE_READ_ONLY** muszą być obsługiwane. Jeśli zwróci ona "Y", zostaną wykonane żadne operacje aktualizacji w źródle danych.  
  
 Jeśli `CDatabase` jest otwarta tylko do odczytu, aby ustawić źródło danych do odczytu tylko zostanie podjęta o **SQLSetConnectOption SQL_ACCESS_MODE**, **SQL_MODE_READ_ONLY**.  
  
 Jeśli identyfikatory wymagają zamykający, te informacje powinny być zwracane w sterowniku z **SQLGetInfo SQL_IDENTIFIER_QUOTE_CHAR** wywołania.  
  
 Na potrzeby debugowania, **SQLGetInfo SQL_DBMS_VER** i **SQL_DBMS_NAME** są pobierane z sterownika.  
  
 **SQLSetStmtOption SQL_QUERY_TIMEOUT** i **SQL_ASYNC_ENABLE** może być wywołana dla `CDatabase`w **HDBC**.  
  
 **SQLError** może zostać wywołana z argumentami lub wszystkie wartości NULL.  
  
 Oczywiście **SQLAllocEnv**, **SQLAllocConnect**, **SQLDisconnect** i **SQLFreeConnect** muszą być obsługiwane.  
  
## <a name="executesql"></a>ExecuteSQL  
 Oprócz przydzielanie i zwalnianie tymczasowej **HSTMT**, `ExecuteSQL` wywołania **SQLExecDirect**, **SQLFetch**, **SQLNumResultCol**i `SQLMoreResults`. **SQLCancel** może być wywołana dla **HSTMT**.  
  
## <a name="getdatabasename"></a>GetDatabaseName  
 **SQLGetInfo SQL_DATABASE_NAME** zostanie wywołana.  
  
## <a name="begintrans-committrans-rollback"></a>BeginTrans, CommitTrans, wycofywania  
 **SQLSetConnectOption SQL_AUTOCOMMIT** i **SQLTransact SQL_COMMIT**, **SQL_ROLLBACK** i **SQL_AUTOCOMMIT** można wywołać, jeśli transakcji żądań.  
  
## <a name="crecordsets"></a>CRecordsets  
 **SQLAllocStmt**, **SQLPrepare**, **SQLExecute** (dla **Otwórz** i **Requery**), **SQLExecDirect**  (dla operacji aktualizowania) **SQLFreeStmt** muszą być obsługiwane. **SQLNumResultCols** i **SQLDescribeCol** zostanie wywołana na wyniki, ustaw w różnym czasie.  
  
 **SQLSetParam** jest często używana do wiązania danych parametru i **DATA_AT_EXEC** funkcji.  
  
 **Procedura SQLBindCol** jest często używane do rejestrowania danych wyjściowych lokalizacji przechowywania danych kolumny z ODBC.  
  
 Dwa **Procedura SQLGetData** wywołania są używane do pobierania **SQL_LONG_VARCHAR** i **SQL_LONG_VARBINARY** danych. Pierwsze wywołanie próbuje odnaleźć całkowita długość wartości kolumny przez wywołanie metody **Procedura SQLGetData** cbMaxValue 0, ale pcbValue prawidłowe. Jeśli przechowuje pcbValue **SQL_NO_TOTAL**, jest zgłaszany wyjątek. W przeciwnym razie `HGLOBAL` została przydzielona i innym **Procedura SQLGetData** wywołania do pobrania całego wyników.  
  
## <a name="updating"></a>Aktualizowanie  
 Jeśli żądanie pesymistyczne blokowanie **SQLGetInfo SQL_LOCK_TYPES** będzie można wykonać zapytania. Jeśli **SQL_LCK_EXCLUSIVE** jest nieobsługiwana, zostanie wygenerowany wyjątek.  
  
 Próbuje zaktualizować `CRecordset` (**migawki** lub **dynamiczny**) spowoduje, że drugi **HSTMT** do przydzielenia. Sterowniki, które nie obsługują drugiego **HSTMT**, Biblioteka kursorów przeprowadzić symulację tej funkcji. Niestety, oznacza to, mogą czasami wymuszania bieżącego zapytania w pierwszym **HSTMT** do wykonania przed rozpoczęciem przetwarzania drugi **HSTMT**na żądanie.  
  
 **SQLFreeStmt SQL_CLOSE** i **SQL_RESET_PARAMS** i **SQLGetCursorName** zostanie wywołana podczas operacji update.  
  
 Jeśli istnieją **CLongBinarys** w **outputColumns**, ODBC firmy **DATA_AT_EXEC** funkcji muszą być obsługiwane. Dotyczy to również zwracanie **SQL_NEED_DATA** z **SQLExecDirect**, **SQLParamData** i **SQLPutData**.  
  
 **SQLRowCount** jest wywoływana po wykonaniu, aby sprawdzić, czy tylko 1 rekord został zaktualizowany przez **SQLExecDirect**.  
  
## <a name="forwardonly-cursors"></a>Kursory ForwardOnly  
 Tylko **SQLFetch** jest wymagany dla **Przenieś** operacji. Należy pamiętać, że **forwardOnly** kursory nie obsługują aktualizacji.  
  
## <a name="snapshot-cursors"></a>Kursory migawki  
 Funkcja migawki wymaga **procedury SQLExtendedFetch** obsługuje. Jak wspomniano powyżej, gdy sterownik nie obsługuje wykrywa z biblioteki kursorów ODBC **procedury SQLExtendedFetch**oraz zapewnić wsparcie niezbędne, samej siebie.  
  
 **SQLGetInfo**, **SQL_SCROLL_OPTIONS** musi obsługiwać **SQL_SO_STATIC**.  
  
## <a name="dynaset-cursors"></a>Kursory dynamiczny  
 Poniżej znajdują się minimalne pomocy technicznej, wymagane, aby otworzyć dynamiczny:  
  
 **SQLGetInfo**, **SQL_ODBC_VER** musi zwracać > "01".  
  
 **SQLGetInfo**, **SQL_SCROLL_OPTIONS** musi obsługiwać **SQL_SO_KEYSET_DRIVEN**.  
  
 **SQLGetInfo**, **SQL_ROW_UPDATES** musi zwracać "Y".  
  
 **SQLGetInfo**, **SQL_POSITIONED_UPDATES** musi obsługiwać **SQL_PS_POSITIONED_DELETE** i **SQL_PS_POSITIONED_UPDATE**.  
  
 Ponadto, jeśli żądanie pesymistyczne blokowanie wywołanie **SQLSetPos** irow 1, fRefresh FALSE i stada **SQL_LCK_EXCLUSIVE** zostanie podjęta.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

