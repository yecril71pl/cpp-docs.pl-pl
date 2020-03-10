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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866649"
---
# <a name="database-macros-and-globals"></a>Makra i funkcje globalne bazy danych

Makra i Globals wymienione poniżej mają zastosowanie do aplikacji baz danych opartych na ODBC. Nie są one używane z aplikacjami opartymi na programie DAO.

Przed MFC 4,2 makra `AFX_SQL_ASYNC` i `AFX_SQL_SYNC` wydawały asynchroniczne operacje, które umożliwiają uzyskanie czasu do innych procesów. Począwszy od MFC 4,2, implementacja tych makr została zmieniona, ponieważ klasy MFC ODBC używały tylko operacji synchronicznych. Makro `AFX_ODBC_CALL` było nowością w MFC 4,2.

### <a name="database-macros"></a>Makra bazy danych

|||
|-|-|
|[AFX_ODBC_CALL](#afx_odbc_call)|Wywołuje funkcję interfejsu API ODBC, która zwraca `SQL_STILL_EXECUTING`. `AFX_ODBC_CALL` będzie wielokrotnie wywoływał funkcję do momentu, gdy nie zwróci już `SQL_STILL_EXECUTING`.|
|[AFX_SQL_ASYNC](#afx_sql_async)|Wywołania `AFX_ODBC_CALL`.|
|[AFX_SQL_SYNC](#afx_sql_sync)|Wywołuje funkcję interfejsu API ODBC, która nie zwraca `SQL_STILL_EXECUTING`.|

### <a name="database-globals"></a>Globals bazy danych

|||
|-|-|
|[AfxDbInitModule](#afxdbinitmodule)|Dodaje obsługę bazy danych dla zwykłej biblioteki MFC DLL, która jest dynamicznie połączona z MFC.|
|[AfxGetHENV](#afxgethenv)|Pobiera dojście do środowiska ODBC, które jest aktualnie używane przez MFC. Tego uchwytu można użyć w bezpośrednich wywołaniach ODBC.|

## <a name="afxdbinitmodule"></a>AfxDbInitModule

W przypadku bazy danych MFC (lub DAO) obsługiwanej przez zwykłą bibliotekę MFC DLL, która jest dynamicznie łączona z MFC, Dodaj wywołanie tej funkcji w funkcji `CWinApp::InitInstance` normalnej biblioteki MFC DLL, aby zainicjować bibliotekę DLL bazy danych MFC.

### <a name="syntax"></a>Składnia

```
void AFXAPI AfxDbInitModule( );
```

### <a name="remarks"></a>Uwagi

Upewnij się, że to wywołanie występuje przed dowolnymi wywołaniami klasy bazowej lub dodanym kodem, który uzyskuje dostęp do biblioteki DLL bazy danych MFC. Biblioteka DLL bazy danych MFC jest biblioteką DLL rozszerzenia MFC; Aby biblioteka DLL rozszerzenia MFC mogła zostać podłączona do łańcucha `CDynLinkLibrary`, należy utworzyć obiekt `CDynLinkLibrary` w kontekście każdego modułu, który będzie go używać. `AfxDbInitModule` tworzy obiekt `CDynLinkLibrary` w kontekście regularnej biblioteki DLL MFC, dzięki czemu będzie on połączony z łańcuchem obiektów `CDynLinkLibrary` zwykłej biblioteki MFC DLL.

### <a name="requirements"></a>Wymagania

**Nagłówek:** \<AFXDLL_. h >

##  <a name="afx_odbc_call"></a>AFX_ODBC_CALL

To makro służy do wywoływania dowolnej funkcji interfejsu API ODBC, która może zwracać `SQL_STILL_EXECUTING`.

```
AFX_ODBC_CALL(SQLFunc)
```

### <a name="parameters"></a>Parametry

*Sqlfunc*<br/>
Funkcja interfejsu API ODBC. Aby uzyskać więcej informacji na temat funkcji ODBC API, zobacz Windows SDK.

### <a name="remarks"></a>Uwagi

`AFX_ODBC_CALL` wielokrotnie wywołuje funkcję do momentu, aż nie zwróci już `SQL_STILL_EXECUTING`.

Przed wywołaniem `AFX_ODBC_CALL`należy zadeklarować zmienną, `nRetCode`, typu RETCODE.

Należy pamiętać, że klasy MFC ODBC używają teraz tylko przetwarzania synchronicznego. Aby można było wykonać operację asynchroniczną, należy wywołać funkcję interfejsu API ODBC `SQLSetConnectOption`. Aby uzyskać więcej informacji, zobacz temat "wykonywanie funkcji asynchronicznie" w Windows SDK.

### <a name="example"></a>Przykład

Ten przykład używa `AFX_ODBC_CALL` do wywołania funkcji `SQLColumns` interfejsu API ODBC, która zwraca listę kolumn w tabeli o nazwie przez `strTableName`. Zwróć uwagę na deklarację `nRetCode` i użycie składowych danych zestawu rekordów do przekazywania parametrów do funkcji. Przykład ilustruje także sprawdzanie wyników wywołania przy użyciu `Check`, funkcji składowej klasy `CRecordset`. Zmienna `prs` jest wskaźnikiem do obiektu `CRecordset`, zadeklarowanym w innym miejscu.

[!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

##  <a name="afx_sql_async"></a>AFX_SQL_ASYNC

Implementacja tego makra została zmieniona w MFC 4,2.

```
AFX_SQL_ASYNC(prs, SQLFunc)
```

### <a name="parameters"></a>Parametry

*żądań ściągnięcia*<br/>
Wskaźnik do obiektu `CRecordset` lub `CDatabase` obiektu. Począwszy od MFC 4,2, wartość tego parametru jest ignorowana.

*Sqlfunc*<br/>
Funkcja interfejsu API ODBC. Aby uzyskać więcej informacji na temat funkcji ODBC API, zobacz Windows SDK.

### <a name="remarks"></a>Uwagi

`AFX_SQL_ASYNC` po prostu wywołuje makro [AFX_ODBC_CALL](#afx_odbc_call) i ignoruje parametr *żądań ściągnięcia* . W wersjach MFC wcześniejszych niż 4,2 `AFX_SQL_ASYNC` został użyty do wywołania funkcji interfejsu API ODBC, które mogą zwrócić `SQL_STILL_EXECUTING`. Jeśli funkcja interfejsu API ODBC zwróci `SQL_STILL_EXECUTING`, `AFX_SQL_ASYNC` wywoła `prs->OnWaitForDataSource`.

> [!NOTE]
>  Klasy MFC ODBC używają teraz tylko przetwarzania synchronicznego. Aby można było wykonać operację asynchroniczną, należy wywołać funkcję interfejsu API ODBC `SQLSetConnectOption`. Aby uzyskać więcej informacji, zobacz temat "wykonywanie funkcji asynchronicznie" w Windows SDK.

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDB. h

##  <a name="afx_sql_sync"></a>AFX_SQL_SYNC

Makro `AFX_SQL_SYNC` po prostu wywołuje funkcję `SQLFunc`.

```
AFX_SQL_SYNC(SQLFunc)
```

### <a name="parameters"></a>Parametry

*Sqlfunc*<br/>
Funkcja interfejsu API ODBC. Aby uzyskać więcej informacji o tych funkcjach, zobacz Windows SDK.

### <a name="remarks"></a>Uwagi

To makro służy do wywoływania funkcji interfejsu API ODBC, które nie zwracają `SQL_STILL_EXECUTING`.

Przed wywołaniem `AFX_SQL_SYNC`należy zadeklarować zmienną, `nRetCode`, typu RETCODE. Możesz sprawdzić wartość `nRetCode` po wywołaniu makra.

Należy zauważyć, że implementacja `AFX_SQL_SYNC` zmieniona w MFC 4,2. Ponieważ sprawdzenie stanu serwera nie jest już wymagane, `AFX_SQL_SYNC` po prostu przypisuje wartość do `nRetCode`. Na przykład zamiast wywołania

[!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]

można po prostu utworzyć przypisanie

[!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDB. h

##  <a name="afxgethenv"></a>AfxGetHENV

Można użyć zwróconego dojścia w bezpośrednich wywołaniach ODBC, ale nie można zamknąć uchwytu ani założyć, że dojście nadal jest prawidłowe i dostępne po usunięciu jakichkolwiek istniejących obiektów `CDatabase`lub `CRecordset`.

```
HENV AFXAPI AfxGetHENV();
```

### <a name="return-value"></a>Wartość zwrócona

Uchwyt do środowiska ODBC, który jest obecnie używany przez MFC. Można `SQL_HENV_NULL`, jeśli nie ma żadnych obiektów [CDatabase](../../mfc/reference/cdatabase-class.md) i nie ma obiektów [CRecordset](../../mfc/reference/crecordset-class.md) .

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDB. h

## <a name="see-also"></a>Zobacz też

[Makra i Globals](../../mfc/reference/mfc-macros-and-globals.md)
