---
title: 'TN042: zalecenia dla deweloperów sterowników ODBC'
ms.date: 11/04/2016
f1_keywords:
- vc.odbc
helpviewer_keywords:
- ODBC drivers [MFC], writing
- databases [MFC], ODBC
- TN042
ms.assetid: ecc6b5d9-f480-4582-9e22-8309fe561dad
ms.openlocfilehash: 67f7a86a247b60be66dabb0a89f04d39ce76222b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372135"
---
# <a name="tn042-odbc-driver-developer-recommendations"></a>TN042: zalecenia dla deweloperów sterowników ODBC

> [!NOTE]
> Następująca uwaga techniczna nie została zaktualizowana, ponieważ została po raz pierwszy uwzględniona w dokumentacji online. W rezultacie niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zaleca się wyszukicie tematu interesującego w indeksie dokumentacji online.

W tej notatce opisano wytyczne dotyczące modułów zapisu sterowników ODBC. Przedstawiono ogólne wymagania i założenia funkcji ODBC, które sprawiają klasy bazy danych MFC i różne oczekiwane szczegóły semantyczne. Opisano funkcje sterownika wymagane `CRecordset` do obsługi trzech trybów Open **(forwardOnly**, **snapshot** i **dynaset**).

## <a name="odbcs-cursor-library"></a>Biblioteka kursorów ODBC

Klasy bazy danych MFC prezentują funkcje dla użytkownika, który w wielu przypadkach przewyższa funkcje zapewniane przez większość sterowników ODBC poziomu 1. Na szczęście biblioteka kursora ODBC będzie warstwa się między klasami bazy danych i sterownika i automatycznie zapewni wiele z tej dodatkowej funkcji.

Na przykład większość sterowników 1.0 nie obsługuje przewijania wstecz. Biblioteka kursorów może to wykryć i buforuje wiersze ze sterownika i `SQLExtendedFetch`przedstawia je zgodnie z żądaniem FETCH_PREV wywołania w programie .

Innym ważnym przykładem zależności biblioteki kursora jest pozycjonowane aktualizacje. Większość sterowników 1.0 również nie ma pozycjonowanych aktualizacji, ale biblioteka kursorów wygeneruje instrukcje aktualizacji, które identyfikują wiersz docelowy w źródle danych na podstawie jego bieżących wartości danych w pamięci podręcznej lub buforowanej wartości sygnatury czasowej.

Biblioteka klas nigdy nie korzysta z wielu zestawów wierszy. W związku z `SQLSetPos` tym kilka instrukcji są zawsze stosowane do wiersza 1 zestawu wierszy.

## <a name="cdatabases"></a>Bazy danych C

Każdy `CDatabase` przydziela jeden **HDBC**. (Jeśli `CDatabase`używana `ExecuteSQL` jest funkcja 's, **HSTMT** jest tymczasowo przydzielany). Więc jeśli `CDatabase`wymagana jest wiele 's, wiele **HDBC**s na **HENV** muszą być obsługiwane.

Klasy bazy danych wymagają biblioteki kursora. Znajduje to odzwierciedlenie `SQLSetConnections` w **SQL_ODBC_CURSORS**połączenia **, SQL_CUR_USE_ODBC**.

`SQLDriverConnect`, **SQL_DRIVER_COMPLETE** jest używany `CDatabase::Open` do ustanowienia połączenia ze źródłem danych.

Sterownik musi `SQLGetInfo SQL_ODBC_API_CONFORMANCE`  >= obsługiwać **SQL_OAC_LEVEL1** `SQLGetInfo SQL_ODBC_SQL_CONFORMANCE`  >=  **, SQL_OSC_MINIMUM**.

Aby `CDatabase` transakcje były obsługiwane dla i jego zależnych `SQLGetInfo SQL_CURSOR_COMMIT_BEHAVIOR` rekordów, a **SQL_CURSOR_ROLLBACK_BEHAVIOR** musi mieć **SQL_CR_PRESERVE**. W przeciwnym razie próby wykonania kontroli transakcji zostaną zignorowane.

`SQLGetInfo SQL_DATA_SOURCE_READ_ONLY`muszą być wspierane. Jeśli zwraca "Y", żadne operacje aktualizacji nie będą wykonywane w źródle danych.

Jeśli `CDatabase` zostanie otwarty readonly, próba ustawienie tylko do odczytu `SQLSetConnectOption SQL_ACCESS_MODE`źródła danych zostanie podjęta za pomocą , **SQL_MODE_READ_ONLY**.

Jeśli identyfikatory wymagają cytowania, te informacje powinny `SQLGetInfo SQL_IDENTIFIER_QUOTE_CHAR` być zwracane od sterownika za pomocą połączenia.

Do celów debugowania `SQLGetInfo SQL_DBMS_VER` i **SQL_DBMS_NAME** są pobierane ze sterownika.

`SQLSetStmtOption SQL_QUERY_TIMEOUT`i **SQL_ASYNC_ENABLE** mogą być wywoływane `CDatabase`na **'s HDBC**.

`SQLError`mogą być wywoływane z dowolnym lub wszystkimi argumentami NULL.

Oczywiście , `SQLAllocEnv` `SQLAllocConnect`i `SQLDisconnect` `SQLFreeConnect` musi być wspierany.

## <a name="executesql"></a>Executesql

Oprócz przydzielania i zwalniania tymczasowego **HSTMT**, `ExecuteSQL` `SQLNumResultCol` połączeń `SQLMoreResults` `SQLExecDirect`, `SQLFetch`i . `SQLCancel`mogą być wywoływane na **HSTMT**.

## <a name="getdatabasename"></a>Getdatabasename

`SQLGetInfo SQL_DATABASE_NAME`zostanie wywołana.

## <a name="begintrans-committrans-rollback"></a>BeginTrans, CommitTrans, Wycofywanie

`SQLSetConnectOption SQL_AUTOCOMMIT`oraz `SQLTransact SQL_COMMIT` **SQL_ROLLBACK** i **SQL_AUTOCOMMIT** będą wywoływane w przypadku składania wniosków o transakcje.

## <a name="crecordsets"></a>CRejesyny

`SQLAllocStmt`, `SQLPrepare` `SQLExecute` , `Open` (For i `Requery`), `SQLExecDirect` `SQLFreeStmt` (dla operacji aktualizacji) muszą być obsługiwane. `SQLNumResultCols`i `SQLDescribeCol` będą wzywane do wyników ustalonych w różnym czasie.

`SQLSetParam`jest szeroko stosowany do wiązania danych parametrów i **funkcji DATA_AT_EXEC.**

`SQLBindCol`jest szeroko stosowany do rejestrowania danych wyjściowych Lokalizacje przechowywania danych kolumn z ODBC.

Dwa `SQLGetData` wywołania są używane do pobierania **danych SQL_LONG_VARCHAR** i **SQL_LONG_VARBINARY.** Pierwsze wywołanie próbuje znaleźć całkowitą długość wartości `SQLGetData` kolumny, wywołując z cbMaxValue 0, ale z prawidłową wartość pcbValue. Jeśli pcbValue posiada **SQL_NO_TOTAL**, wyjątek. W przeciwnym razie **HGLOBAL** jest `SQLGetData` przydzielany i inne wywołanie wykonane w celu pobrania całego wyniku.

## <a name="updating"></a>Aktualizowanie

Jeśli wymagane jest pesymistyczne `SQLGetInfo SQL_LOCK_TYPES` blokowanie, zostanie zapytany. Jeśli **SQL_LCK_EXCLUSIVE** nie jest obsługiwana, zostanie zgłoszony wyjątek.

Próby aktualizacji `CRecordset` **(migawka** lub **dynaset)** spowoduje, że drugi **HSTMT** mają być przydzielone. W przypadku sterowników, które nie obsługują drugiego **HSTMT,** biblioteka kursorów symuluje tę funkcję. Niestety może to czasami oznaczać wymuszanie bieżącej kwerendy na pierwszym HSTMT do zakończenia przed przetworzeniem drugiego żądania HSTMT.Unfortunately, this may sometimes mean forcing the current query on the first **HSTMT** to completion before processing the second **HSTMT's**request.

`SQLFreeStmt SQL_CLOSE`i **SQL_RESET_PARAMS** i `SQLGetCursorName` zostanie wywołana podczas operacji aktualizacji.

Jeśli istnieją **CLongBinarys** w **outputColumns**, DATA_AT_EXEC **funkcji** ODBC musi być obsługiwana. Obejmuje to zwracanie **SQL_NEED_DATA** `SQLExecDirect`z `SQLParamData` `SQLPutData`i .

`SQLRowCount`jest wywoływana po wykonaniu, aby sprawdzić, czy `SQLExecDirect`tylko 1 rekord został zaktualizowany przez .

## <a name="forwardonly-cursors"></a>Kursory tylko do przodu

Tylko `SQLFetch` jest wymagane `Move` dla operacji. Należy zauważyć, że **forwardOnly** kursory nie obsługują aktualizacji.

## <a name="snapshot-cursors"></a>Kursory migawek

Funkcja migawki wymaga `SQLExtendedFetch` obsługi. Jak wspomniano powyżej, biblioteka kursorów ODBC wykryje, gdy sterownik nie obsługuje `SQLExtendedFetch`, i zapewnić niezbędne wsparcie się.

`SQLGetInfo`, **SQL_SCROLL_OPTIONS** musi wspierać **SQL_SO_STATIC**.

## <a name="dynaset-cursors"></a>Kursory dynaset

Poniżej znajduje się minimalne wsparcie wymagane do otwarcia zestawu dynamiki:

`SQLGetInfo`, **SQL_ODBC_VER** musi zwrócić > "01".

`SQLGetInfo`, **SQL_SCROLL_OPTIONS** musi wspierać **SQL_SO_KEYSET_DRIVEN**.

`SQLGetInfo`, **SQL_ROW_UPDATES** musi zwrócić "Y".

`SQLGetInfo`, **SQL_POSITIONED_UPDATES** musi wspierać **SQL_PS_POSITIONED_DELETE** i **SQL_PS_POSITIONED_UPDATE**.

Ponadto, jeśli pesymistyczne blokowanie jest wymagane, `SQLSetPos` wywołanie z irow 1, fRefresh FALSE i fLock **SQL_LCK_EXCLUSIVE** zostanie wykonane.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
