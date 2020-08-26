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
ms.openlocfilehash: 0dc53bce8b43677e7fe0aa1787d1adcc16a560c4
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837530"
---
# <a name="database-macros-and-globals"></a>Makra i funkcje globalne bazy danych

Makra i Globals wymienione poniżej mają zastosowanie do aplikacji baz danych opartych na ODBC. Nie są one używane z aplikacjami opartymi na programie DAO.

Przed MFC 4,2 makra `AFX_SQL_ASYNC` i `AFX_SQL_SYNC` wydawały operacje asynchroniczne umożliwiają uzyskanie czasu do innych procesów. Począwszy od MFC 4,2, implementacja tych makr została zmieniona, ponieważ klasy MFC ODBC używały tylko operacji synchronicznych. Makro `AFX_ODBC_CALL` było nowe w MFC 4,2.

### <a name="database-macros"></a>Makra bazy danych

|Nazwa|Opis|
|-|-|
|[AFX_ODBC_CALL](#afx_odbc_call)|Wywołuje funkcję interfejsu API ODBC, która zwraca wartość `SQL_STILL_EXECUTING` . `AFX_ODBC_CALL` Program będzie wielokrotnie wywoływał funkcję do momentu, gdy nie będzie już zwracać `SQL_STILL_EXECUTING` .|
|[AFX_SQL_ASYNC](#afx_sql_async)|Wywołania `AFX_ODBC_CALL` .|
|[AFX_SQL_SYNC](#afx_sql_sync)|Wywołuje funkcję interfejsu API ODBC, która nie zwraca `SQL_STILL_EXECUTING` .|

### <a name="database-globals"></a>Globals bazy danych

|Nazwa|Opis|
|-|-|
|[AfxDbInitModule](#afxdbinitmodule)|Dodaje obsługę bazy danych dla zwykłej biblioteki MFC DLL, która jest dynamicznie połączona z MFC.|
|[AfxGetHENV](#afxgethenv)|Pobiera dojście do środowiska ODBC, które jest aktualnie używane przez MFC. Tego uchwytu można użyć w bezpośrednich wywołaniach ODBC.|

## <a name="afxdbinitmodule"></a><a name="afxdbinitmodule"></a> AfxDbInitModule

W przypadku obsługi bazy danych MFC (lub DAO) ze zwykłej biblioteki MFC DLL, która jest dynamicznie połączona z MFC, Dodaj wywołanie tej funkcji w funkcji regularnej biblioteki DLL MFC, `CWinApp::InitInstance` Aby zainicjować bibliotekę DLL bazy danych MFC.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI AfxDbInitModule( );
```

### <a name="remarks"></a>Uwagi

Upewnij się, że to wywołanie występuje przed dowolnymi wywołaniami klasy bazowej lub dodanym kodem, który uzyskuje dostęp do biblioteki DLL bazy danych MFC. Biblioteka DLL bazy danych MFC jest biblioteką DLL rozszerzenia MFC; Aby biblioteka DLL rozszerzenia MFC mogła zostać podłączona do `CDynLinkLibrary` łańcucha, musi utworzyć `CDynLinkLibrary` obiekt w kontekście każdego modułu, który będzie go używać. `AfxDbInitModule` tworzy `CDynLinkLibrary` obiekt w kontekście regularnej biblioteki DLL MFC, dzięki czemu będzie on połączony z `CDynLinkLibrary` łańcuchem obiektów zwykłej biblioteki MFC DLL.

### <a name="requirements"></a>Wymagania

**Nagłówek:**\<afxdll_.h>

## <a name="afx_odbc_call"></a><a name="afx_odbc_call"></a> AFX_ODBC_CALL

To makro służy do wywoływania dowolnej funkcji ODBC API, która może zwrócić `SQL_STILL_EXECUTING` .

```
AFX_ODBC_CALL(SQLFunc)
```

### <a name="parameters"></a>Parametry

*Sqlfunc*<br/>
Funkcja interfejsu API ODBC. Aby uzyskać więcej informacji na temat funkcji ODBC API, zobacz Windows SDK.

### <a name="remarks"></a>Uwagi

`AFX_ODBC_CALL` wielokrotnie wywołuje funkcję do momentu, aż już nie zwraca `SQL_STILL_EXECUTING` .

Przed wywołaniem `AFX_ODBC_CALL` należy zadeklarować zmienną, `nRetCode` , typu RETCODE.

Należy pamiętać, że klasy MFC ODBC używają teraz tylko przetwarzania synchronicznego. Aby można było wykonać operację asynchroniczną, należy wywołać funkcję interfejsu API ODBC `SQLSetConnectOption` . Aby uzyskać więcej informacji, zobacz temat "wykonywanie funkcji asynchronicznie" w Windows SDK.

### <a name="example"></a>Przykład

Ten przykład używa `AFX_ODBC_CALL` do wywoływania `SQLColumns` funkcji ODBC API, która zwraca listę kolumn w tabeli o nazwie przez `strTableName` . Należy zwrócić uwagę na deklarację `nRetCode` i użycie składowych danych zestawu rekordów do przekazywania parametrów do funkcji. Przykład ilustruje także sprawdzanie wyników wywołania z `Check` , funkcja członkowska klasy `CRecordset` . Zmienna `prs` jest wskaźnikiem do `CRecordset` obiektu, zadeklarowanym w innym miejscu.

[!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="afx_sql_async"></a><a name="afx_sql_async"></a> AFX_SQL_ASYNC

Implementacja tego makra została zmieniona w MFC 4,2.

```
AFX_SQL_ASYNC(prs, SQLFunc)
```

### <a name="parameters"></a>Parametry

*żądań ściągnięcia*<br/>
Wskaźnik do `CRecordset` obiektu lub `CDatabase` obiektu. Począwszy od MFC 4,2, wartość tego parametru jest ignorowana.

*Sqlfunc*<br/>
Funkcja interfejsu API ODBC. Aby uzyskać więcej informacji na temat funkcji ODBC API, zobacz Windows SDK.

### <a name="remarks"></a>Uwagi

`AFX_SQL_ASYNC` po prostu wywołuje makro [AFX_ODBC_CALL](#afx_odbc_call) i ignoruje parametr *żądań ściągnięcia* . W wersjach MFC wcześniejszych niż 4,2 program `AFX_SQL_ASYNC` został użyty do wywołania funkcji interfejsu API ODBC, które mogą zwrócić `SQL_STILL_EXECUTING` . Jeśli funkcja interfejsu API ODBC zwróci `SQL_STILL_EXECUTING` `AFX_SQL_ASYNC` metodę, wywoła `prs->OnWaitForDataSource` .

> [!NOTE]
> Klasy MFC ODBC używają teraz tylko przetwarzania synchronicznego. Aby można było wykonać operację asynchroniczną, należy wywołać funkcję interfejsu API ODBC `SQLSetConnectOption` . Aby uzyskać więcej informacji, zobacz temat "wykonywanie funkcji asynchronicznie" w Windows SDK.

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDB. h

## <a name="afx_sql_sync"></a><a name="afx_sql_sync"></a> AFX_SQL_SYNC

`AFX_SQL_SYNC`Makro po prostu wywołuje funkcję `SQLFunc` .

```
AFX_SQL_SYNC(SQLFunc)
```

### <a name="parameters"></a>Parametry

*Sqlfunc*<br/>
Funkcja interfejsu API ODBC. Aby uzyskać więcej informacji o tych funkcjach, zobacz Windows SDK.

### <a name="remarks"></a>Uwagi

To makro służy do wywoływania funkcji interfejsu API ODBC, które nie zostaną zwrócone `SQL_STILL_EXECUTING` .

Przed wywołaniem `AFX_SQL_SYNC` należy zadeklarować zmienną `nRetCode` typu RETCODE. Możesz sprawdzić wartość `nRetCode` po wywołaniu makra.

Należy zauważyć, że implementacja `AFX_SQL_SYNC` została zmieniona w MFC 4,2. Ponieważ sprawdzenie stanu serwera nie jest już wymagane, `AFX_SQL_SYNC` po prostu przypisuje wartość do `nRetCode` . Na przykład zamiast wywołania

[!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]

można po prostu utworzyć przypisanie

[!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDB. h

## <a name="afxgethenv"></a><a name="afxgethenv"></a> AfxGetHENV

Można użyć zwracanego uchwytu w bezpośrednich wywołaniach ODBC, ale nie można zamknąć uchwytu ani założyć, że dojście nadal jest prawidłowe i dostępne po `CDatabase` zniszczeniu wszystkich istniejących lub `CRecordset` pochodnych obiektów.

```
HENV AFXAPI AfxGetHENV();
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do środowiska ODBC, który jest obecnie używany przez MFC. Może mieć `SQL_HENV_NULL` zastosowanie w przypadku braku obiektów [CDatabase](../../mfc/reference/cdatabase-class.md) i braku obiektów [CRecordset](../../mfc/reference/crecordset-class.md) .

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDB. h

## <a name="see-also"></a>Zobacz też

[Makra i Globals](../../mfc/reference/mfc-macros-and-globals.md)
