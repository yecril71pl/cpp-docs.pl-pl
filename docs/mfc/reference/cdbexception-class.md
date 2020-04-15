---
title: Klasa CDBException
ms.date: 11/04/2016
f1_keywords:
- CDBException
- AFXDB/CDBException
- AFXDB/CDBException::m_nRetCode
- AFXDB/CDBException::m_strError
- AFXDB/CDBException::m_strStateNativeOrigin
helpviewer_keywords:
- CDBException [MFC], m_nRetCode
- CDBException [MFC], m_strError
- CDBException [MFC], m_strStateNativeOrigin
ms.assetid: eb9e1119-89f5-49a7-b9d4-b91cee1ccc82
ms.openlocfilehash: 1ab7daeb3af55c92985c951c632b1d4050681474
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321891"
---
# <a name="cdbexception-class"></a>Klasa CDBException

Reprezentuje warunek wyjątku wynikające z klas bazy danych.

## <a name="syntax"></a>Składnia

```
class CDBException : public CException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDBException::m_nRetCode](#m_nretcode)|Zawiera kod zwrotny open database connectivity (ODBC) typu RETCODE.|
|[CDBException::m_strError](#m_strerror)|Zawiera ciąg opisujący błąd w terminach alfanumerycznym.|
|[CDBException::m_strStateNativeOrigin](#m_strstatenativeorigin)|Zawiera ciąg opisujący błąd pod względem kodów błędów zwracanych przez ODBC.|

## <a name="remarks"></a>Uwagi

Klasa zawiera dwa elementy członkowskie danych publicznych, których można użyć do określenia przyczyny wyjątku lub wyświetlenia wiadomości tekstowej opisującej wyjątek. `CDBException`obiekty są konstruowane i generowane przez funkcje członkowskie klas bazy danych.

> [!NOTE]
> Ta klasa jest jedną z klas łączności otwartej bazy danych (ODBC) mfc. Jeśli zamiast tego używasz nowszych obiektów dostępu do danych (DAO), należy użyć [CDaoException](../../mfc/reference/cdaoexception-class.md) zamiast tego. Wszystkie nazwy klas DAO mają "CDao" jako prefiks. Aby uzyskać więcej informacji, zobacz artykuł [Omówienie: Programowanie baz danych](../../data/data-access-programming-mfc-atl.md).

Wyjątki to przypadki nieprawidłowego wykonania obejmujące warunki poza kontrolą programu, takie jak błędy we/wy źródła danych lub sieci. Błędy, których można się spodziewać w normalnym trakcie wykonywania programu, zwykle nie są uważane za wyjątki.

Można uzyskać dostęp do tych obiektów w zakresie wyrażenia **CATCH.** Można również `CDBException` rzutować obiekty z `AfxThrowDBException` własnego kodu za pomocą funkcji globalnej.

Aby uzyskać więcej informacji na temat `CDBException` obsługi wyjątków w ogóle lub o obiektach, zobacz artykuły [Obsługa wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md) i [Wyjątki: Wyjątki bazy danych](../../mfc/exceptions-database-exceptions.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cexception](../../mfc/reference/cexception-class.md)

`CDBException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="cdbexceptionm_nretcode"></a><a name="m_nretcode"></a>CDBException::m_nRetCode

Zawiera kod błędu ODBC typu RETCODE zwracany przez funkcję interfejsu programowania aplikacji ODBC (API).

### <a name="remarks"></a>Uwagi

Ten typ zawiera kody z prefiksami SQL zdefiniowane przez ODBC i kody z prefiksami AFX_SQL zdefiniowane przez klasy bazy danych. W `CDBException`przypadku elementu członkowskiego ten będzie zawierał jedną z następujących wartości:

- AFX_SQL_ERROR_API_CONFORMANCE Sterownik lub `CDatabase::OpenEx` `CDatabase::Open` wywołanie nie jest zgodny z wymaganym poziomem zgodności interfejsu API ODBC 1 (SQL_OAC_LEVEL1).

- AFX_SQL_ERROR_CONNECT_FAIL Połączenie ze źródłem danych nie powiodło się. Przekazano wskaźnik`CDatabase` NULL do konstruktora pliku recordset i `GetDefaultConnect` późniejszą próbę utworzenia połączenia na podstawie nie powiodło się.

- AFX_SQL_ERROR_DATA_TRUNCATED Użytkownik zażądał więcej danych niż w przypadku przechowywania. Aby uzyskać informacje na temat `CString` `CByteArray` zwiększania dostępnego `nMaxLength` przechowywania danych lub typów danych, zobacz argument [RFX_Text](record-field-exchange-functions.md#rfx_text) i [RFX_Binary](record-field-exchange-functions.md#rfx_binary) w obszarze "Makra i globalne".

- AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED Wywołanie żądania `CRecordset::Open` dynaset nie powiodło się. Dynasets nie są obsługiwane przez sterownik.

- AFX_SQL_ERROR_EMPTY_COLUMN_LIST Próbowano otworzyć tabelę (lub nie można zidentyfikować tej tabeli jako wywołania procedury lub instrukcji **SELECT),** ale w `DoFieldExchange` zastąpieniu nie ma kolumn zidentyfikowanych w wywołaniach funkcji wymiany pól rekordów (RFX).

- AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH Typ funkcji RFX w `DoFieldExchange` zastąpiona jest niezgodny z typem danych kolumny w fachu.

- AFX_SQL_ERROR_ILLEGAL_MODE Zadzwoniłeś `CRecordset::Update` bez wcześniejszego `CRecordset::AddNew` dzwonienia lub `CRecordset::Edit`.

- AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED Żądanie zablokowania rekordów do aktualizacji nie może zostać spełnione, ponieważ sterownik ODBC nie obsługuje blokowania.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED Zadzwoniłeś `CRecordset::Update` lub `Delete` dla tabeli bez unikatowego klucza i zmieniłeś wiele rekordów.

- AFX_SQL_ERROR_NO_CURRENT_RECORD Próbowano edytować lub usunąć poprzednio usunięty rekord. Po usunięciu należy przewinąć do nowego bieżącego rekordu.

- AFX_SQL_ERROR_NO_POSITIONED_UPDATES Żądanie dynaset nie może zostać spełnione, ponieważ sterownik ODBC nie obsługuje pozycjonowanych aktualizacji.

- AFX_SQL_ERROR_NO_ROWS_AFFECTED Zadzwoniłeś `CRecordset::Update` lub `Delete`, ale po rozpoczęciu operacji rekord nie można już znaleźć.

- AFX_SQL_ERROR_ODBC_LOAD_FAILED Próba załadowania odbc. Biblioteka DLL nie powiodła się; System Windows nie może odnaleźć lub nie można załadować tej biblioteki DLL. Ten błąd jest krytyczny.

- AFX_SQL_ERROR_ODBC_V2_REQUIRED Żądanie dynaset nie może być spełnione, ponieważ poziom 2 zgodny sterownik ODBC jest wymagane.

- AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY Próba przewijania nie powiodła się, ponieważ źródło danych nie obsługuje przewijania wstecznego.

- AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED Wywołanie żądania `CRecordset::Open` migawki nie powiodło się. Migawki nie są obsługiwane przez sterownik. (Powinno to nastąpić tylko wtedy, gdy biblioteka kursora ODBC ODBCCURS. Biblioteka DLL nie jest obecna.)

- AFX_SQL_ERROR_SQL_CONFORMANCE Sterownik lub `CDatabase::OpenEx` `CDatabase::Open` wywołanie nie jest zgodny z wymaganym poziomem zgodności SQL ODBC "Minimum" (SQL_OSC_MINIMUM).

- AFX_SQL_ERROR_SQL_NO_TOTAL Sterownik ODBC nie może określić całkowitego `CLongBinary` rozmiaru wartości danych. Operacja prawdopodobnie nie powiodła się, ponieważ nie można wstępnie przydzielić globalnego bloku pamięci.

- AFX_SQL_ERROR_RECORDSET_READONLY Próbowano zaktualizować zestaw rekordów tylko do odczytu lub źródło danych jest tylko do odczytu. Nie można wykonać żadnych operacji aktualizacji `CDatabase` z akcesem rekordów ani obiektem, z który jest skojarzony.

- funkcja SQL_ERROR nie powiodła się. Komunikat o błędzie zwrócony `SQLError` przez funkcję `m_strError` ODBC jest przechowywany w elementów członkowskich danych.

- funkcja SQL_INVALID_HANDLE nie powiodła się z powodu nieprawidłowego dojścia do środowiska, dojścia połączenia lub dojścia instrukcji. Oznacza to błąd programowania. Funkcja ODBC nie jest dostępna `SQLError`w żaden sposób.

Kody z prefiksem SQL są definiowane przez ODBC. Kody z poprzedzonym AFX są zdefiniowane w AFXDB. H, znaleziono w MFC\INCLUDE.

## <a name="cdbexceptionm_strerror"></a><a name="m_strerror"></a>CDBException::m_strError

Zawiera ciąg opisujący błąd, który spowodował wyjątek.

### <a name="remarks"></a>Uwagi

Ciąg opisuje błąd w kategoriach alfanumeryczne. Aby uzyskać bardziej szczegółowe informacje `m_strStateNativeOrigin`i przykład, zobacz .

## <a name="cdbexceptionm_strstatenativeorigin"></a><a name="m_strstatenativeorigin"></a>CDBException::m_strStateNativeOrigin

Zawiera ciąg opisujący błąd, który spowodował wyjątek.

### <a name="remarks"></a>Uwagi

Ciąg ma formę "State:%s,Native:%ld,Origin:%s", gdzie kody formatów w kolejności są zastępowane wartościami opisującymi:

- SQLSTATE, ciąg zakończony zerem zawierający pięcioznakowy kod błędu zwrócony w parametrze *szSqlState* funkcji `SQLError`ODBC . Wartości SQLSTATE są wymienione w dodatku A, [kody błędów ODBC](/sql/odbc/reference/appendixes/appendix-a-odbc-error-codes), w *odwołaniu programisty ODBC*. Przykład: "S0022".

- Natywny kod błędu, specyficzne dla źródła danych, zwrócony w *pfNativeError* parametr `SQLError` funkcji. Przykład: 207.

- Tekst komunikatu o błędzie zwrócony w parametrze *szErrorMsg* `SQLError` funkcji. Ten komunikat składa się z kilku nazw w nawiasach. Ponieważ błąd jest przekazywany ze źródła do użytkownika, każdy składnik ODBC (źródło danych, sterownik, menedżer sterowników) dołącza własną nazwę. Te informacje pomagają określić pochodzenie błędu. Przykład: [Microsoft][STEROWNIK PROGRAMU SQL SERVER][SQL Server]

Struktura interpretuje ciąg błędu i umieszcza `m_strStateNativeOrigin`jego składniki w ; jeśli `m_strStateNativeOrigin` zawiera informacje o więcej niż jeden błąd, błędy są oddzielone newlines. Struktura umieszcza tekst błędu alfanumerycznego w `m_strError`.

Aby uzyskać dodatkowe informacje na temat kodów użytych do utworzenia tego ciągu, zobacz funkcję [SQLError](/sql/odbc/reference/syntax/sqlerror-function) w *odwołaniu programisty ODBC*.

### <a name="example"></a>Przykład

Od ODBC:\["Stan:S0022,Native:207,Origin:\[Microsoft] ODBC\[SQL Server Driver] SQL Server] Nieprawidłowa nazwa kolumny 'ColName'"

W `m_strStateNativeOrigin`:\["State:S0022,Native:207,Origin:\[Microsoft] ODBC\[SQL Server Driver] SQL Server]"

W `m_strError`: "Nieprawidłowa nazwa kolumny 'ColName'"

## <a name="see-also"></a>Zobacz też

[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Klasa CFieldExchange](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::Aktualizacja](../../mfc/reference/crecordset-class.md#update)<br/>
[CRecordset::Delete](../../mfc/reference/crecordset-class.md#delete)<br/>
[Klasa CException](../../mfc/reference/cexception-class.md)
