---
title: 'TN042: Zalecenia dla deweloperów sterowników ODBC | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.odbc
dev_langs:
- C++
helpviewer_keywords:
- ODBC drivers [MFC], writing
- databases [MFC], ODBC
- TN042
ms.assetid: ecc6b5d9-f480-4582-9e22-8309fe561dad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 87e31fa0884adc78d3f1026afc59dd0b46ac7602
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375258"
---
# <a name="tn042-odbc-driver-developer-recommendations"></a>TN042: zalecenia dla deweloperów sterowników ODBC

> [!NOTE]
>  Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Ta uwaga opisuje wytyczne dla modułów zapisujących sterownika ODBC. Zawiera ogólne wymagania i założenia funkcji ODBC, które ułatwiają klas baz danych MFC i różne oczekiwane szczegóły semantyki. Wymagane funkcje sterownik do obsługi trzech `CRecordset` Otwórz tryby (**forwardOnly**, **migawki** i **dynamiczny**) są opisane.

## <a name="odbcs-cursor-library"></a>Biblioteka kursorów ODBC firmy

Klasy baz danych MFC są wyświetlane funkcji użytkownika, wliczoną w wielu przypadkach funkcje udostępniane przez większość sterowników ODBC poziomu 1. Na szczęście Biblioteka kursorów ODBC firmy warstwy sam między klasami bazy danych i sterownik i automatycznie zapewni znacznie ta dodatkowa funkcja.

Na przykład większość sterowników 1.0 nie obsługują przewijanie do tyłu. Biblioteka kursorów można wykryć i będzie wiersze ze sterownika w pamięci podręcznej i pokażesz mu zgodnie z żądaniem w wywołaniach FETCH_PREV w `SQLExtendedFetch`.

Inny przykład istotne znaczenie Biblioteka kursorów to Aktualizacje pozycjonowane. Większość sterowników 1.0 nie mają też Aktualizacje pozycjonowane, ale z biblioteki kursorów wygeneruje instrukcji update, które identyfikują wiersz docelowy w źródle danych, w zależności od jego bieżących wartości danych w pamięci podręcznej lub wartość znacznika czasu pamięci podręcznej.

Biblioteka klas nigdy nie korzysta z wielu zestawów wierszy. W związku z tym, kilka `SQLSetPos` instrukcje są zawsze stosowane do wiersz 1 zestaw wierszy.

## <a name="cdatabases"></a>CDatabases

Każdy `CDatabase` przydziela pojedynczy **HDBC**. (Jeśli `CDatabase`firmy `ExecuteSQL` funkcja jest używana, **HSTMT** tymczasowo jest przydzielany.) Dlatego jeśli wiele `CDatabase`firmy są wymagane, wiele **HDBC**s na **HENV** muszą być obsługiwane.

Klasy baz danych wymagają z biblioteki kursorów. Znajduje to odzwierciedlenie w `SQLSetConnections` wywołania **SQL_ODBC_CURSORS**, **SQL_CUR_USE_ODBC**.

`SQLDriverConnect`, **SQL_DRIVER_COMPLETE** jest używany przez `CDatabase::Open` do nawiązania połączenia ze źródłem danych.

Sterownik musi obsługiwać `SQLGetInfo SQL_ODBC_API_CONFORMANCE`  >=  **SQL_OAC_LEVEL1**, `SQLGetInfo SQL_ODBC_SQL_CONFORMANCE`  >=  **SQL_OSC_MINIMUM**.

Aby transakcji, które mają być obsługiwane dla `CDatabase` i jego zależne zestawy rekordów `SQLGetInfo SQL_CURSOR_COMMIT_BEHAVIOR` i **SQL_CURSOR_ROLLBACK_BEHAVIOR** musi mieć **SQL_CR_PRESERVE**. W przeciwnym razie próby wykonania Kontrola transakcji zostaną zignorowane.

`SQLGetInfo SQL_DATA_SOURCE_READ_ONLY` muszą być obsługiwane. Jeśli zostanie zwrócona "Y", żadne operacje aktualizacji odbędzie się w źródle danych.

Jeśli `CDatabase` jest otwarty tylko do odczytu, aby ustawić źródło danych odczytu tylko zostanie podjęta próba przy użyciu `SQLSetConnectOption SQL_ACCESS_MODE`, **SQL_MODE_READ_ONLY**.

Jeśli identyfikatory wymagają cytowanie, te informacje powinny być zwracane z sterownika z `SQLGetInfo SQL_IDENTIFIER_QUOTE_CHAR` wywołania.

Dla celów debugowania, `SQLGetInfo SQL_DBMS_VER` i **SQL_DBMS_NAME** są pobierane z sterownika.

`SQLSetStmtOption SQL_QUERY_TIMEOUT` i **SQL_ASYNC_ENABLE** może być wywołana dla `CDatabase`firmy **HDBC**.

`SQLError` może zostać wywołana z argumentami lub wszystkie wartości NULL.

Oczywiście `SQLAllocEnv`, `SQLAllocConnect`, `SQLDisconnect` i `SQLFreeConnect` muszą być obsługiwane.

## <a name="executesql"></a>ExecuteSQL

Oprócz przydzielanie i zwalnianie tymczasowego **HSTMT**, `ExecuteSQL` wywołania `SQLExecDirect`, `SQLFetch`, `SQLNumResultCol` i `SQLMoreResults`. `SQLCancel` może być wywołana dla **HSTMT**.

## <a name="getdatabasename"></a>GetDatabaseName

`SQLGetInfo SQL_DATABASE_NAME` zostanie wywołana.

## <a name="begintrans-committrans-rollback"></a>BeginTrans, z CommitTrans, wycofywanie

`SQLSetConnectOption SQL_AUTOCOMMIT` i `SQLTransact SQL_COMMIT`, **SQL_ROLLBACK** i **SQL_AUTOCOMMIT** zostanie wywołana, jeśli żądań transakcji.

## <a name="crecordsets"></a>CRecordsets

`SQLAllocStmt`, `SQLPrepare`, `SQLExecute` (Dla `Open` i `Requery`), `SQLExecDirect` (dla operacji aktualizacji) `SQLFreeStmt` muszą być obsługiwane. `SQLNumResultCols` i `SQLDescribeCol` zostanie wywołana na wynikach, ustaw w różnym czasie.

`SQLSetParam` jest często używana do wiązania danych parametru i **DATA_AT_EXEC** funkcji.

`SQLBindCol` jest często używane do rejestrowania danych wyjściowych lokalizacje przechowywania danych kolumny z ODBC.

Dwa `SQLGetData` wywołania są używane do pobierania **SQL_LONG_VARCHAR** i **SQL_LONG_VARBINARY** danych. Pierwsze wywołanie próbuje znaleźć całkowita długość wartości kolumny, wywołując `SQLGetData` cbMaxValue 0, ale pcbValue prawidłowe. Jeśli posiada pcbValue **SQL_NO_TOTAL**, zgłaszany jest wyjątek. W przeciwnym razie **wartości HGLOBAL** jest przydzielany, a inny `SQLGetData` wywołania do pobrania całego wyników.

## <a name="updating"></a>Aktualizowanie

Jeśli wymagana jest pesymistycznego blokowania, `SQLGetInfo SQL_LOCK_TYPES` będą badane. Jeśli **SQL_LCK_EXCLUSIVE** jest nieobsługiwana, zostanie zgłoszony wyjątek.

Próbuje zaktualizować `CRecordset` (**migawki** lub **dynamiczny**) spowoduje, że drugi **HSTMT** do przydzielenia. Sterowniki, które nie obsługują drugie **HSTMT**, Biblioteka kursorów przeprowadzić symulację tej funkcji. Niestety, oznacza to, może czasami wymuszenie bieżącego zapytania na pierwszy **HSTMT** ukończone przed przetworzeniem drugi **HSTMT**żądania użytkownika.

`SQLFreeStmt SQL_CLOSE` i **SQL_RESET_PARAMS** i `SQLGetCursorName` zostaną wywołane podczas operacji aktualizacji.

W przypadku **CLongBinarys** w **outputColumns**, ODBC firmy **DATA_AT_EXEC** funkcji muszą być obsługiwane. Obejmuje to zwracanie **SQL_NEED_DATA** z `SQLExecDirect`, `SQLParamData` i `SQLPutData`.

`SQLRowCount` jest wywoływana po wykonaniu, aby sprawdzić, czy tylko 1 rekord został zaktualizowany przez `SQLExecDirect`.

## <a name="forwardonly-cursors"></a>Kursory ForwardOnly

Tylko `SQLFetch` jest wymagany dla `Move` operacji. Należy pamiętać, że **forwardOnly** kursory nie obsługują aktualizacji.

## <a name="snapshot-cursors"></a>Kursory migawki

Funkcja migawek wymaga `SQLExtendedFetch` pomocy technicznej. Jak wspomniano powyżej, Biblioteka kursorów ODBC wykryje, jeśli sterownik nie obsługuje `SQLExtendedFetch`oraz zapewnić wsparcie niezbędne, sam.

`SQLGetInfo`, **SQL_SCROLL_OPTIONS** musi obsługiwać **SQL_SO_STATIC**.

## <a name="dynaset-cursors"></a>Kursory zestawu dynamicznego

Poniżej przedstawiono minimalne pomocy technicznej, wymagane, aby otworzyć dynamiczny:

`SQLGetInfo`, **SQL_ODBC_VER** musi zwracać > "01".

`SQLGetInfo`, **SQL_SCROLL_OPTIONS** musi obsługiwać **SQL_SO_KEYSET_DRIVEN**.

`SQLGetInfo`, **SQL_ROW_UPDATES** musi zwracać "Y".

`SQLGetInfo`, **SQL_POSITIONED_UPDATES** musi obsługiwać **SQL_PS_POSITIONED_DELETE** i **SQL_PS_POSITIONED_UPDATE**.

Ponadto, jeśli pesymistycznego blokowania jest wymagana wywołanie `SQLSetPos` irow 1, fRefresh FALSE i stada **SQL_LCK_EXCLUSIVE** zostaną wprowadzone.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

