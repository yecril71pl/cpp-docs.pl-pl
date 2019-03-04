---
title: Makra i funkcje globalne bazy danych
ms.date: 11/04/2016
f1_keywords:
- AFXDB/AFX_ODBC_CALL
- AFXDB/AFX_SQL_ASYNC
- AFXDB/AFX_SQL_SYNC
- AFXDB/AfxGetHENV
helpviewer_keywords:
- global database functions [MFC]
- database macros [MFC]
- database globals [MFC]
- global functions [MFC], database functions
- macros [MFC], MFC database
ms.assetid: 5b9b9e61-1cf9-4345-9f29-3807dd466488
ms.openlocfilehash: 47a1bb434801c24ab8eee048d9ef8f93793101cc
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268723"
---
# <a name="database-macros-and-globals"></a>Makra i funkcje globalne bazy danych

Makra i funkcje globalne wymienione poniżej dotyczą aplikacji na podstawie ODBC baz danych. Nie są używane z aplikacji opartych na DAO.

Przed 4.2 MFC, makra `AFX_SQL_ASYNC` i `AFX_SQL_SYNC` udostępniła możliwość uzyskanie czas na inne procesy operacji asynchronicznych. Począwszy od 4.2 MFC, implementacja tych makr, zmieniać, ponieważ klasach MFC ODBC używane tylko operacje synchroniczne. Makro `AFX_ODBC_CALL` nowych do MFC 4.2.

### <a name="database-macros"></a>Makra bazy danych

|||
|-|-|
|[AFX_ODBC_CALL](#afx_odbc_call)|Wywołuje funkcję interfejsu API ODBC, która zwraca `SQL_STILL_EXECUTING`. `AFX_ODBC_CALL` wielokrotnie wywoła funkcję dopóki nie jest już zwraca `SQL_STILL_EXECUTING`.|
|[AFX_SQL_ASYNC](#afx_sql_async)|Wywołania `AFX_ODBC_CALL`.|
|[AFX_SQL_SYNC](#afx_sql_sync)|Wywołuje funkcję interfejsu API ODBC, która nie zwraca `SQL_STILL_EXECUTING`.|

### <a name="database-globals"></a>Zmienne globalne bazy danych

|||
|-|-|
|[AfxDbInitModule](#afxdbinitmodule)|Dodaje obsługę bazy danych dla zwykłej biblioteki MFC DLL, która jest połączona dynamicznie z MFC.|
|[AfxGetHENV](#afxgethenv)|Pobranie dojścia środowiska ODBC, obecnie w użyciu przez MFC. Przy użyciu tego uchwytu w bezpośrednie wywołania ODBC.|

## <a name="afxdbinitmodule"></a> AfxDbInitModule

Baza danych MFC (lub DAO) dotyczących pomocy technicznej od zwykłej biblioteki MFC DLL, która jest połączona dynamicznie z MFC, dodaj wywołanie tej funkcji w swojej zwykłej biblioteki MFC DLL w `CWinApp::InitInstance` funkcji, aby zainicjować MFC bazy danych biblioteki DLL.

### <a name="syntax"></a>Składnia

```
void AFXAPI AfxDbInitModule( );
```

### <a name="remarks"></a>Uwagi

Upewnij się, to wywołanie występuje przed wywołaniem dowolnej klasy podstawowej lub wszyscy dodani kod, który uzyskuje dostęp do bazy danych MFC DLL. Baza danych MFC DLL jest rozszerzeniem MFC DLL; w celu rozszerzenia MFC biblioteki DLL Pobierz połączonymi w `CDynLinkLibrary` łańcucha, należy utworzyć `CDynLinkLibrary` obiektu w kontekście każdego modułu, który będzie go używać. `AfxDbInitModule` Tworzy `CDynLinkLibrary` obiekt w kontekście swojej zwykłej biblioteki MFC DLL firmy, tak, aby go pobiera połączonymi w `CDynLinkLibrary` obiektu łańcucha zwykłej biblioteki MFC DLL.

### <a name="requirements"></a>Wymagania

**Header:** \<afxdll_.h>

##  <a name="afx_odbc_call"></a>  AFX_ODBC_CALL

Użyj tego makra do wywołań dowolnej funkcji interfejsu API ODBC, która może zwracać `SQL_STILL_EXECUTING`.

```
AFX_ODBC_CALL(SQLFunc)
```

### <a name="parameters"></a>Parametry

*SQLFunc*<br/>
Funkcja interfejsu API ODBC. Aby uzyskać więcej informacji na temat funkcji interfejsu API ODBC zobacz zestaw Windows SDK.

### <a name="remarks"></a>Uwagi

`AFX_ODBC_CALL` wielokrotnie wywołuje funkcję dopóki nie jest już zwraca `SQL_STILL_EXECUTING`.

Przed wywołaniem `AFX_ODBC_CALL`, należy zadeklarować zmienną, `nRetCode`, typu RETCODE.

Należy pamiętać, że MFC ODBC klasy teraz Użyj tylko synchronicznego przetwarzania. Aby można było wykonać operację asynchroniczną, musi wywołać funkcji interfejsu API ODBC `SQLSetConnectOption`. Aby uzyskać więcej informacji zobacz temat "Wykonywanie funkcji asynchronicznie" w zestawie Windows SDK.

### <a name="example"></a>Przykład

W tym przykładzie użyto `AFX_ODBC_CALL` do wywołania `SQLColumns` funkcji interfejsu API ODBC, która zwraca listę kolumn w tabeli o nazwie określonej przez `strTableName`. Należy pamiętać, deklaracja `nRetCode` i umożliwia korzystanie z zestawu rekordów elementów członkowskich danych parametry są przekazywane do funkcji. Ten przykład ilustruje, sprawdzanie wyników wywołania z `Check`, funkcji składowej klasy `CRecordset`. Zmienna `prs` jest wskaźnikiem do `CRecordset` obiektu, zadeklarowany w innym miejscu.

[!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

##  <a name="afx_sql_async"></a>  AFX_SQL_ASYNC

Implementacja tego makra zmienione w MFC 4.2.

```
AFX_SQL_ASYNC(prs, SQLFunc)
```

### <a name="parameters"></a>Parametry

*żądania ściągnięcia*<br/>
Wskaźnik do `CRecordset` obiektu lub `CDatabase` obiektu. Począwszy od MFC 4.2 wartości tego parametru jest ignorowana.

*SQLFunc*<br/>
Funkcja interfejsu API ODBC. Aby uzyskać więcej informacji na temat funkcji interfejsu API ODBC zobacz zestaw Windows SDK.

### <a name="remarks"></a>Uwagi

`AFX_SQL_ASYNC` po prostu wywołuje makro [AFX_ODBC_CALL](#afx_odbc_call) i ignoruje *żądań ściągnięcia* parametru. W wersjach MFC przed 4.2 `AFX_SQL_ASYNC` zostało użyte do wywołania funkcji interfejsu API ODBC, które mogą zwracać `SQL_STILL_EXECUTING`. Jeśli funkcja interfejsu API ODBC zwrócił `SQL_STILL_EXECUTING`, następnie `AFX_SQL_ASYNC` wywoływałby `prs->OnWaitForDataSource`.

> [!NOTE]
>  Przetwarzanie tylko synchroniczne można teraz używać w klasach MFC ODBC. Aby można było wykonać operację asynchroniczną, musi wywołać funkcji interfejsu API ODBC `SQLSetConnectOption`. Aby uzyskać więcej informacji zobacz temat "Wykonywanie funkcji asynchronicznie" w zestawie Windows SDK.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdb.h

##  <a name="afx_sql_sync"></a>  AFX_SQL_SYNC

`AFX_SQL_SYNC` — Makro po prostu wywołuje funkcję `SQLFunc`.

```
AFX_SQL_SYNC(SQLFunc)
```

### <a name="parameters"></a>Parametry

*SQLFunc*<br/>
Funkcja interfejsu API ODBC. Aby uzyskać więcej informacji o tych funkcjach zobacz zestaw Windows SDK.

### <a name="remarks"></a>Uwagi

Użyj tego makra do wywołania funkcji interfejsu API ODBC, które nie zwracają `SQL_STILL_EXECUTING`.

Przed wywołaniem `AFX_SQL_SYNC`, należy zadeklarować zmienną, `nRetCode`, typu RETCODE. Możesz sprawdzić wartość `nRetCode` po wywołaniu makra.

Należy pamiętać, że implementacja `AFX_SQL_SYNC` zmienione w MFC 4.2. Ponieważ sprawdzanie stanu serwera nie jest już wymagane, `AFX_SQL_SYNC` po prostu przypisuje wartość do `nRetCode`. Na przykład zamiast wywołania

[!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]

Możesz po prostu wprowadzić przypisania

[!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdb.h

##  <a name="afxgethenv"></a>  Afxgethenv —

Zwracany uchwyt można używać w bezpośrednie wywołania ODBC, ale nie może zamknąć dojścia lub przyjęto założenie, że dojście jest nadal prawidłowa i dostępna po wszystkich istniejących `CDatabase`— lub `CRecordset`-zniszczeniu obiektów pochodnych.

```
HENV AFXAPI AfxGetHENV();
```

### <a name="return-value"></a>Wartość zwracana

Dojścia środowiska ODBC, obecnie w użyciu przez MFC. Może być `SQL_HENV_NULL` w przypadku nie [CDatabase](../../mfc/reference/cdatabase-class.md) obiektów i nie [CRecordset](../../mfc/reference/crecordset-class.md) obiektów w użyciu.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdb.h

## <a name="see-also"></a>Zobacz także

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
