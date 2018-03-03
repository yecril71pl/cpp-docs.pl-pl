---
title: Klasa CDBException | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDBException
- AFXDB/CDBException
- AFXDB/CDBException::m_nRetCode
- AFXDB/CDBException::m_strError
- AFXDB/CDBException::m_strStateNativeOrigin
dev_langs:
- C++
helpviewer_keywords:
- CDBException [MFC], m_nRetCode
- CDBException [MFC], m_strError
- CDBException [MFC], m_strStateNativeOrigin
ms.assetid: eb9e1119-89f5-49a7-b9d4-b91cee1ccc82
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 295b0d9ed9ce37988766455741a168b8c1d5ee6b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdbexception-class"></a>Klasa CDBException
Reprezentuje warunku wyjątku wynikających z klasami baz danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDBException : public CException  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDBException::m_nRetCode](#m_nretcode)|Zawiera kod powrotu otwarte połączenie bazy danych (ODBC), typu **RETCODE**.|  
|[CDBException::m_strError](#m_strerror)|Zawiera ciąg opisujący błąd względem alfanumeryczne.|  
|[CDBException::m_strStateNativeOrigin](#m_strstatenativeorigin)|Zawiera ciąg opisujący błąd pod względem kodów błędów zwróconych przez ODBC.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa ta obejmuje dwa publiczne elementy członkowskie danych używanych w celu ustalenia przyczyny wyjątku lub, aby wyświetlić wiadomość SMS opisujący wyjątek. `CDBException`obiekty są zbudowane i zgłaszanych przez funkcje Członkowskie klas bazy danych.  
  
> [!NOTE]
>  Ta klasa jest jedną z klas otwarte połączenie bazy danych (ODBC) MFC. Jeśli zamiast tego są przy użyciu nowszej klas obiektów DAO (Data Access), użyj [CDaoException](../../mfc/reference/cdaoexception-class.md) zamiast tego. Wszystkie nazwy klasy DAO mają "CDao" jako prefiksu. Aby uzyskać więcej informacji, zobacz artykuł [omówienie: programowania bazy danych](../../data/data-access-programming-mfc-atl.md).  
  
 Wyjątki przypadków nietypowe wykonanie obejmujące warunki poza kontrolą programu, np. źródła danych lub sieci błędów We/Wy. Błędy, które mogą powinny być widoczne w trakcie normalnego przebiegu wykonywania programu zwykle nie są uznawane za wyjątki.  
  
 Można uzyskać dostępu do tych obiektów w zakresie **CATCH** wyrażenia. Można również zgłosić `CDBException` obiektów z kodu za pomocą `AfxThrowDBException` funkcji globalnej.  
  
 Aby uzyskać więcej informacji na temat obsługi wyjątków w ogólne lub o `CDBException` obiektów, zobacz artykuły [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md) i [wyjątki: wyjątki bazy danych](../../mfc/exceptions-database-exceptions.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cexception —](../../mfc/reference/cexception-class.md)  
  
 `CDBException`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  
  
##  <a name="m_nretcode"></a>CDBException::m_nRetCode  
 Zawiera kod błędu ODBC typu **RETCODE** zwracane przez aplikację ODBC programowania funkcji interfejsu API.  
  
### <a name="remarks"></a>Uwagi  
 Ten typ zawiera prefiks SQL zdefiniowany przez sterownik ODBC i prefiksem AFX_SQL kodów wynika z klasami baz danych. Aby uzyskać `CDBException`, ten użytkownik będzie zawierać jedną z następujących wartości:  
  
- **AFX_SQL_ERROR_API_CONFORMANCE** sterownik `CDatabase::OpenEx` lub `CDatabase::Open` wywołania nie jest zgodna z wymagany poziom zgodności interfejsu API ODBC 1 ( **SQL_OAC_LEVEL1**).  
  
- **AFX_SQL_ERROR_CONNECT_FAIL** połączenie ze źródłem danych nie powiodło się. Zostanie przekazany **NULL** `CDatabase` wskaźnik do konstruktora z zestawu rekordów i kolejna próba utworzenia połączenia na podstawie `GetDefaultConnect` nie powiodło się.  
  
- **AFX_SQL_ERROR_DATA_TRUNCATED** żądany więcej danych niż podana magazynu dla. Aby uzyskać informacje o zwiększenie magazyn danych podany dla `CString` lub `CByteArray` , zobacz `nMaxLength` argument [rfx_text —](record-field-exchange-functions.md#rfx_text) i [rfx_binary —](record-field-exchange-functions.md#rfx_binary) w obszarze "makra i Zmienne globalne."  
  
- **AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED** wywołanie `CRecordset::Open` dynamiczny żądanie nie powiodło się. Zestawy dynamiczne nie są obsługiwane przez sterownik.  
  
- **AFX_SQL_ERROR_EMPTY_COLUMN_LIST** podjęto próbę otwarcia tabeli (lub należy nadać nie można zidentyfikować jako wywołanie procedury lub **wybierz** instrukcji), ale nie kolumn określonych w wymiana pól rekordów (RFX) odwołuje się funkcja Twoje `DoFieldExchange` zastąpienia.  
  
- **AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH** typ funkcji RFX w Twojej `DoFieldExchange` override nie jest zgodny z typem danych kolumn w zestawie rekordów.  
  
- **AFX_SQL_ERROR_ILLEGAL_MODE** należy wywołać `CRecordset::Update` bez wcześniejszego wywołania metody `CRecordset::AddNew` lub `CRecordset::Edit`.  
  
- **AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED** nie można przeprowadzić żądanie blokady rekordów do aktualizacji, ponieważ sterownik ODBC nie obsługuje operacji blokowania.  
  
- **AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED** należy wywołać `CRecordset::Update` lub **usunąć** dla tabeli bez klucza unikatowy i zmienić wielu rekordów.  
  
- **AFX_SQL_ERROR_NO_CURRENT_RECORD** próbowano edytować lub usunąć wcześniej usunięty rekord. Po usunięciu musi przewiń bieżącego rekordu.  
  
- **AFX_SQL_ERROR_NO_POSITIONED_UPDATES** Twojego żądania dla dynamiczny zestaw wyników nie może być spełnione, ponieważ sterownik ODBC nie obsługuje aktualizacje pozycjonowane.  
  
- **AFX_SQL_ERROR_NO_ROWS_AFFECTED** należy wywołać `CRecordset::Update` lub **usunąć**, ale w momencie rozpoczęcia operacji nie można odnaleźć rekordu.  
  
- **AFX_SQL_ERROR_ODBC_LOAD_FAILED** próba załadowania ODBC. Biblioteki DLL nie powiodła się; System Windows nie może znaleźć lub nie można załadować tę bibliotekę DLL. Ten błąd jest krytyczny.  
  
- **AFX_SQL_ERROR_ODBC_V2_REQUIRED** nie można przeprowadzić żądanie dynamiczny, ponieważ poziom 2 zgodny sterownik ODBC jest wymagany.  
  
- **AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY** Próba przewinięcia nie powiodła się, ponieważ źródło danych nie obsługuje przewijanie do tyłu.  
  
- **AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED** wywołanie `CRecordset::Open` żąda migawki nie powiodło się. Migawki nie są obsługiwane przez sterownik. (Ten może występować tylko gdy Biblioteka kursorów ODBC ODBCCURS. Biblioteki DLL nie jest obecny).  
  
- **AFX_SQL_ERROR_SQL_CONFORMANCE** sterownik `CDatabase::OpenEx` lub `CDatabase::Open` wywołania są niezgodne z poziomu zgodności SQL ODBC "Minimalna" ( **SQL_OSC_MINIMUM**).  
  
- **AFX_SQL_ERROR_SQL_NO_TOTAL** sterownik ODBC nie może określić całkowity rozmiar `CLongBinary` wartości danych. Operacja prawdopodobnie nie powiodła się, ponieważ nie można wstępnie przydzielonych blok pamięci globalnej.  
  
- **AFX_SQL_ERROR_RECORDSET_READONLY** podjęła próbę zaktualizowania rekordów tylko do odczytu lub źródło danych jest tylko do odczytu. Żadne operacje aktualizacji może odbywać się przy użyciu zestawu rekordów lub `CDatabase` obiekt jest skojarzony.  
  
- **Wartość SQL_ERROR** funkcji nie powiodło się. Komunikat o błędzie zwrócony przez funkcję ODBC **SQLError** są przechowywane w **m_strError** element członkowski danych.  
  
- **SQL_INVALID_HANDLE** funkcji nie powiodło się z powodu środowiska nieprawidłowy uchwyt, dojścia połączenia lub instrukcji. Oznacza to błąd programistyczny. Dodatkowe informacje są niedostępne z funkcji ODBC **SQLError**.  
  
 Kody prefiksem SQL są definiowane przez sterownik ODBC. Kody prefiksem AFX są definiowane w AFXDB. H w MFC\INCLUDE.  
  
##  <a name="m_strerror"></a>CDBException::m_strError  
 Zawiera ciąg opisujący błąd, który spowodował wyjątek.  
  
### <a name="remarks"></a>Uwagi  
 Ciąg opisem błędu względem alfanumeryczne. Aby uzyskać szczegółowe informacje i przykładem, zobacz **m_strStateNativeOrigin**.  
  
##  <a name="m_strstatenativeorigin"></a>CDBException::m_strStateNativeOrigin  
 Zawiera ciąg opisujący błąd, który spowodował wyjątek.  
  
### <a name="remarks"></a>Uwagi  
 Ten ciąg ma formularza "Stan: % s, Native: % ld źródła: % s", gdzie kodów formatu w kolejności, są zastępowane przez wartości, które opisują:  
  
-   **SQLSTATE**, zerem ciąg zawierający 5 znaków zwrócony kod w *szSqlState* parametru funkcji ODBC **SQLError**. **SQLSTATE** wartości są wymienione w dodatku A [kody błędów ODBC](https://msdn.microsoft.com/library/ms714687.aspx)w *Podręcznik programisty ODBC*. Przykład: "S0022".  
  
-   Zwrócony kod błędu macierzystego, określonego w źródle danych w *pfNativeError* parametr **SQLError** funkcji. Przykład: 207.  
  
-   Tekst komunikatu o błędzie zwracany w *szErrorMsg* parametr **SQLError** funkcji. Ten komunikat składa się z kilku nazw w nawiasach kwadratowych. Jako błąd jest przekazywany od źródła do użytkownika, każdy składnik ODBC (źródła danych, sterowników i Menedżera sterowników) dołącza własną nazwę. Informacje te pomagają wskazać przyczynę błędu. Przykład: [Microsoft] [sterownik ODBC SQL Server] [SQL Server]  
  
 Platformę interpretuje ciąg błędu i umieszczenie jej składników do **m_strStateNativeOrigin**; Jeśli **m_strStateNativeOrigin** zawiera informacje o więcej niż jeden błąd, błędy są oddzielone newlines. Platformę umieszcza tekst błędu alfanumeryczne w **m_strError**.  
  
 Aby uzyskać dodatkowe informacje o kodach umożliwia tworzą ten ciąg, zobacz [SQLError](https://msdn.microsoft.com/library/ms716312.aspx) działać w *Podręcznik programisty ODBC*.  
  
### <a name="example"></a>Przykład  
  Z ODBC: "Stan: S0022, Native: 207, pochodzenia: [Microsoft] [sterownik ODBC SQL Server] [SQL Server] nieprawidłową nazwę kolumny 'Nazwa kolumny'"  
  
 W **m_strStateNativeOrigin**: "Stan: S0022, Native: 207, pochodzenia: [Microsoft] [sterownik ODBC SQL Server] [SQL Server]"  
  
 W **m_strError**: "nieprawidłową nazwę kolumny 'Nazwa kolumny'"  
  
## <a name="see-also"></a>Zobacz też  
 [Cexception — klasa](../../mfc/reference/cexception-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cdatabase — klasa](../../mfc/reference/cdatabase-class.md)   
 [Crecordset — klasa](../../mfc/reference/crecordset-class.md)   
 [Klasa CFieldExchange](../../mfc/reference/cfieldexchange-class.md)   
 [CRecordset::Update](../../mfc/reference/crecordset-class.md#update)   
 [CRecordset::Delete](../../mfc/reference/crecordset-class.md#delete)   
 [Klasa CException](../../mfc/reference/cexception-class.md)
