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
ms.openlocfilehash: 755b89635eedd7808f900dc63cd3039845db1dd3
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328535"
---
# <a name="cdbexception-class"></a>Klasa CDBException

Przedstawia warunek wyjątku wynikający z klas baz danych.

## <a name="syntax"></a>Składnia

```
class CDBException : public CException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDBException::m_nRetCode](#m_nretcode)|Zawiera kod powrotny Open Database Connectivity (ODBC), typu RETCODE.|
|[CDBException::m_strError](#m_strerror)|Zawiera ciąg, który opisuje błąd w warunkach alfanumeryczne.|
|[CDBException::m_strStateNativeOrigin](#m_strstatenativeorigin)|Zawiera ciąg opisujący błąd pod względem kodów błędów zwróconych przez ODBC.|

## <a name="remarks"></a>Uwagi

Klasa zawiera dwa elementy członkowskie danych publicznych, których można użyć, aby ustalić przyczynę wyjątku lub, aby wyświetlić wiadomość SMS z opisem wyjątku. `CDBException` obiekty są zbudowane i generowane przez funkcje składowe klasy bazy danych.

> [!NOTE]
>  Ta klasa jest jedną z klas interfejsu Open Database Connectivity (ODBC) biblioteki MFC. Jeśli zamiast tego są przy użyciu nowszej klas obiektów dostępu do danych (DAO), użyj [CDaoException](../../mfc/reference/cdaoexception-class.md) zamiast tego. Wszystkie nazwy klasy DAO mają "CDao" jako prefiksu. Aby uzyskać więcej informacji, zobacz artykuł [omówienie: Baza danych programowania](../../data/data-access-programming-mfc-atl.md).

Wyjątki są przypadki nietypowe wykonanie obejmujące warunki poza kontrolą programu, takie jak źródło danych lub błędy We/Wy sieci. Błędy, które można by oczekiwać w trakcie normalnego wykonania programu zwykle nie są uznawane za wyjątki.

Możesz uzyskać dostęp tych obiektów w zakresie **CATCH** wyrażenia. Może również zgłosić `CDBException` obiektów w kodzie za pomocą `AfxThrowDBException` funkcja globalna.

Aby uzyskać więcej informacji na temat obsługi wyjątków w ogólne lub wkrótce `CDBException` obiektów, zobacz artykuły [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md) i [wyjątków: Baza danych wyjątki](../../mfc/exceptions-database-exceptions.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDBException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

##  <a name="m_nretcode"></a>  CDBException::m_nRetCode

Zawiera kod błędu ODBC typu RETCODE zwrócony przez programowania funkcja interfejsu API ODBC aplikacji.

### <a name="remarks"></a>Uwagi

Ten typ zawiera prefiks SQL zdefiniowane przez sterownik ODBC i prefiksem AFX_SQL kodów zdefiniowanych przez klasy bazy danych. Aby uzyskać `CDBException`, ten element członkowski będzie zawierać jedną z następujących wartości:

- AFX_SQL_ERROR_API_CONFORMANCE sterownika dla `CDatabase::OpenEx` lub `CDatabase::Open` wywołanie nie jest zgodny z wymagany poziom zgodności interfejsu API ODBC 1 (SQL_OAC_LEVEL1).

- AFX_SQL_ERROR_CONNECT_FAIL połączenia ze źródłem danych nie powiodło się. Przekazana wartość NULL`CDatabase` wskaźnik do Konstruktora zestawu rekordów i kolejna próba utworzenia połączenia na podstawie `GetDefaultConnect` nie powiodło się.

- AFX_SQL_ERROR_DATA_TRUNCATED zażądano większej ilości danych niż podano magazyn. Instrukcje dotyczące zwiększenie magazyn udostępnionych danych dla `CString` lub `CByteArray` typów danych, zobacz `nMaxLength` argument [rfx_text —](record-field-exchange-functions.md#rfx_text) i [rfx_binary —](record-field-exchange-functions.md#rfx_binary) w obszarze "makra i Funkcje globalne."

- Wywołanie AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED A `CRecordset::Open` dynamiczny żądanie nie powiodło się. Zestawy dynamiczne nie są obsługiwane przez sterownik.

- AFX_SQL_ERROR_EMPTY_COLUMN_LIST próby otwarcia tabeli (lub należy nadać nie można zidentyfikować jako wywołanie procedury lub **wybierz** instrukcji), ale nie kolumn określonych w wywołań funkcji ewidencjonowania pól rekordów (RFX) programu exchange w Twoje `DoFieldExchange` zastąpienia.

- AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH typ RFX działać w swojej `DoFieldExchange` override nie jest zgodny z typem danych kolumn w zestawie rekordów.

- AFX_SQL_ERROR_ILLEGAL_MODE nastąpiło wywołanie `CRecordset::Update` bez wywoływania wcześniej `CRecordset::AddNew` lub `CRecordset::Edit`.

- Nie można spełnione AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED Twoje żądanie blokady rekordów do aktualizacji, ponieważ sterownik ODBC nie obsługuje blokowania.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED nastąpiło wywołanie `CRecordset::Update` lub `Delete` dla tabeli bez klucza unikatowy i zmienić wiele rekordów.

- AFX_SQL_ERROR_NO_CURRENT_RECORD próbowano edytować lub usunąć wcześniej usunięty rekord. Po usunięciu musi przewiń nowe bieżącego rekordu.

- AFX_SQL_ERROR_NO_POSITIONED_UPDATES, który nie jest spełnione Twoje żądanie dotyczące dynamicznego, ponieważ sterownik ODBC nie obsługuje umieszczony aktualizacji.

- AFX_SQL_ERROR_NO_ROWS_AFFECTED nastąpiło wywołanie `CRecordset::Update` lub `Delete`, ale w momencie rozpoczęcia operacji nie można odnaleźć rekordu.

- AFX_SQL_ERROR_ODBC_LOAD_FAILED próba załadowania ODBC. Biblioteka DLL nie powiodła się; Windows nie może znaleźć lub nie można załadować tę bibliotekę DLL. Ten błąd jest krytyczny.

- AFX_SQL_ERROR_ODBC_V2_REQUIRED, który nie jest spełnione Twoje żądanie dotyczące dynamicznego, ponieważ poziomu 2 zgodny sterownik ODBC jest wymagany.

- Próba przewiń AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY nie powiodła się, ponieważ źródło danych nie obsługuje przewijanie do tyłu.

- Wywołanie AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED A `CRecordset::Open` żądanie migawki nie powiodło się. Migawki nie są obsługiwane przez sterownik. (To powinno nastąpić tylko jeśli Biblioteka kursorów ODBC ODBCCURS. Biblioteka DLL nie jest obecna).

- AFX_SQL_ERROR_SQL_CONFORMANCE sterownika dla `CDatabase::OpenEx` lub `CDatabase::Open` wywołanie nie jest zgodny z wymagany stopień zgodności ze standardem ODBC SQL w "Minimum" (SQL_OSC_MINIMUM).

- Sterownik ODBC AFX_SQL_ERROR_SQL_NO_TOTAL nie może określić całkowity rozmiar `CLongBinary` wartości danych. Operacja prawdopodobnie nie powiodła się, ponieważ nie można wstępnie przydzielonych bloku pamięci globalnej.

- AFX_SQL_ERROR_RECORDSET_READONLY próby zaktualizowania rekordów tylko do odczytu lub źródło danych jest tylko do odczytu. Żadne operacje aktualizacji mogą być wykonywane przy użyciu zestawu rekordów lub `CDatabase` obiekt jest skojarzony.

- SQL_ERROR Function failed. Komunikat o błędzie zwrócona przez funkcję ODBC `SQLError` są przechowywane w `m_strError` element członkowski danych.

- Funkcja SQL_INVALID_HANDLE nie powiodło się z powodu nieprawidłowych dojścia, dojścia połączenia lub dojście instrukcji. Oznacza to błąd programistyczny. Nie dodatkowe informacje są dostępne z funkcji ODBC `SQLError`.

Kody prefiks SQL są definiowane przez sterownik ODBC. Prefiks AFX kody są definiowane w AFXDB. H w MFC\INCLUDE.

##  <a name="m_strerror"></a>  CDBException::m_strError

Zawiera ciąg opisujący błąd, który spowodował wyjątek.

### <a name="remarks"></a>Uwagi

Ciąg opisuje błąd w warunkach alfanumeryczne. Aby uzyskać więcej szczegółowych informacji i obejrzeć przykład, zobacz `m_strStateNativeOrigin`.

##  <a name="m_strstatenativeorigin"></a>  CDBException::m_strStateNativeOrigin

Zawiera ciąg opisujący błąd, który spowodował wyjątek.

### <a name="remarks"></a>Uwagi

Ten ciąg jest formularz "Stan: % s, natywne: % ld źródła: % s", gdzie kody format, w kolejności, zastępuje wartości, które opisują:

- SQLSTATE, ciąg zakończony wartością null zawierający kod błędu pięcioznakowe zwracane w *szSqlState* parametru funkcji ODBC `SQLError`. SQLSTATE wartości wymieniono w załączniku A, [kody błędów ODBC](/previous-versions/windows/desktop/ms714687(v=vs.85))w *odwołania programisty ODBC*. Przykład: "S0022".

- Zwrócony kod błędu macierzystego, specyficzne dla źródła danych w *pfNativeError* parametru `SQLError` funkcji. Przykład: 207.

- Tekst komunikatu o błędzie, które są zwracane w *szErrorMsg* parametru `SQLError` funkcji. Ten komunikat zawiera kilka nazw w nawiasach kwadratowych. Jako błąd jest przekazywany ze źródła do użytkownika, poszczególnych składników ODBC (źródła danych, sterowników, Menedżer sterowników) dołącza własną nazwę. Informacje te pomagają wskazać przyczynę błędu. Przykład: [Microsoft] [sterownik ODBC SQL Server] [SQL Server]

Framework interpretuje ciąg błędu i umieszcza jej składników `m_strStateNativeOrigin`; Jeśli `m_strStateNativeOrigin` zawiera informacje o więcej niż jeden błąd, błędy są oddzielone tabulacji. Struktura umieszcza tekst błędu alfanumeryczne do `m_strError`.

Aby uzyskać dodatkowe informacje na temat kodów umożliwia tworzą ten ciąg, zobacz [SQLError](/previous-versions/windows/desktop/ms716312(v=vs.85)) działa w programach *odwołania programisty ODBC*.

### <a name="example"></a>Przykład

  Z ODBC: "Stan: S0022, natywne: 207, źródło:\[Microsoft]\[sterownik ODBC SQL Server]\[programu SQL Server] Nieprawidłowa nazwa kolumny"Nazwa kolumny""

W `m_strStateNativeOrigin`: "State:S0022,Native:207,Origin:\[Microsoft]\[ODBC SQL Server Driver]\[SQL Server]"

W `m_strError`: "Nieprawidłowa nazwa kolumny"Nazwa kolumny""

## <a name="see-also"></a>Zobacz także

[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Klasa CFieldExchange](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::Update](../../mfc/reference/crecordset-class.md#update)<br/>
[CRecordset::Delete](../../mfc/reference/crecordset-class.md#delete)<br/>
[Klasa CException](../../mfc/reference/cexception-class.md)
