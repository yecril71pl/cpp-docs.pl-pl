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
ms.openlocfilehash: 4e9700311bbc20ea017675357a91a56813cc4bde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376963"
---
# <a name="database-macros-and-globals"></a>Makra i funkcje globalne bazy danych

Makra i globalne wymienione poniżej dotyczą aplikacji baz danych opartych na odbc. Nie są one używane z aplikacjami opartymi na DAO.

Przed MFC 4.2 `AFX_SQL_ASYNC` makra `AFX_SQL_SYNC` i dał operacji asynchronicznych możliwość dać czas do innych procesów. Począwszy od MFC 4.2, implementacja tych makr uległa zmianie, ponieważ klasy ODBC MFC używane tylko operacje synchroniczne. Makro `AFX_ODBC_CALL` było nowością w MFC 4.2.

### <a name="database-macros"></a>Makra bazy danych

|||
|-|-|
|[AFX_ODBC_CALL](#afx_odbc_call)|Wywołuje funkcję interfejsu API `SQL_STILL_EXECUTING`ODBC, która zwraca . `AFX_ODBC_CALL`będzie wielokrotnie wywoływać funkcję, dopóki `SQL_STILL_EXECUTING`nie powróci .|
|[AFX_SQL_ASYNC](#afx_sql_async)|Połączenia `AFX_ODBC_CALL`.|
|[AFX_SQL_SYNC](#afx_sql_sync)|Wywołuje funkcję interfejsu API ODBC, która nie zwraca `SQL_STILL_EXECUTING`.|

### <a name="database-globals"></a>Globalne bazy danych

|||
|-|-|
|[AfxDbInitModule](#afxdbinitmodule)|Dodaje obsługę bazy danych dla zwykłej biblioteki DLL MFC, która jest dynamicznie łączona z MFC.|
|[AfxGetHENV ( AfxGetHENV )](#afxgethenv)|Pobiera dojście do środowiska ODBC aktualnie używane przez MFC. Tego dojścia można używać w bezpośrednich wywołaniach ODBC.|

## <a name="afxdbinitmodule"></a><a name="afxdbinitmodule"></a>AfxDbInitModule

W przypadku obsługi bazy danych MFC (lub DAO) z zwykłej biblioteki DLL MFC, która jest dynamicznie `CWinApp::InitInstance` połączona z MFC, dodaj wywołanie tej funkcji w funkcji zwykłej biblioteki DLL MFC, aby zainicjować bibliotekę DLL bazy danych MFC.

### <a name="syntax"></a>Składnia

```
void AFXAPI AfxDbInitModule( );
```

### <a name="remarks"></a>Uwagi

Upewnij się, że to wywołanie występuje przed wywołaniem klasy podstawowej lub dowolnym dodanym kodem, który uzyskuje dostęp do biblioteki DLL bazy danych MFC. Biblioteka DLL bazy danych MFC jest biblioteką DLL rozszerzenia MFC; aby biblioteka DLL rozszerzenia MFC została `CDynLinkLibrary` podłączona do łańcucha, musi utworzyć `CDynLinkLibrary` obiekt w kontekście każdego modułu, który będzie go używał. `AfxDbInitModule`tworzy `CDynLinkLibrary` obiekt w kontekście regularnych bibliotek DLL MFC, tak `CDynLinkLibrary` aby pobierał podłączony do łańcucha obiektów zwykłej biblioteki DLL MFC.

### <a name="requirements"></a>Wymagania

**Nagłówek:** \<afxdll_.h>

## <a name="afx_odbc_call"></a><a name="afx_odbc_call"></a>AFX_ODBC_CALL

Użyj tego makra, aby wywołać `SQL_STILL_EXECUTING`dowolną funkcję INTERFEJSU API ODBC, która może powrócić .

```
AFX_ODBC_CALL(SQLFunc)
```

### <a name="parameters"></a>Parametry

*SQLFunc (Niemki)*<br/>
Funkcja INTERFEJSU API ODBC. Aby uzyskać więcej informacji na temat funkcji interfejsu API ODBC, zobacz SDK systemu Windows.

### <a name="remarks"></a>Uwagi

`AFX_ODBC_CALL`wywołuje funkcję, aż przestanie `SQL_STILL_EXECUTING`zwracać .

Przed wywołaniem `AFX_ODBC_CALL`, należy zadeklarować zmienną, `nRetCode`typu RETCODE.

Należy zauważyć, że klasy ODBC MFC używają teraz tylko przetwarzania synchroniczowego. Aby wykonać operację asynchronizacyjną, należy wywołać `SQLSetConnectOption`funkcję INTERFEJSU API ODBC . Aby uzyskać więcej informacji, zobacz temat "Wykonywanie funkcji asynchronicznie" w windows SDK.

### <a name="example"></a>Przykład

W tym `AFX_ODBC_CALL` przykładzie `SQLColumns` użyto do wywołania funkcji INTERFEJSU API ODBC, `strTableName`która zwraca listę kolumn w tabeli o nazwie . Zanotuj `nRetCode` deklarację i użycie elementów członkowskich danych zestawu rekordów w celu przekazania parametrów do funkcji. Przykład ilustruje również sprawdzanie wyników wywołania za pomocą `Check` `CRecordset`funkcji elementu członkowskiego klasy . Zmienna `prs` jest wskaźnikiem `CRecordset` do obiektu, zadeklarowanym w innym miejscu.

[!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="afx_sql_async"></a><a name="afx_sql_async"></a>AFX_SQL_ASYNC

Implementacja tego makra uległa zmianie w MFC 4.2.

```
AFX_SQL_ASYNC(prs, SQLFunc)
```

### <a name="parameters"></a>Parametry

*Prs*<br/>
Wskaźnik do `CRecordset` obiektu lub `CDatabase` obiektu. Począwszy od MFC 4.2, ta wartość parametru jest ignorowana.

*SQLFunc (Niemki)*<br/>
Funkcja INTERFEJSU API ODBC. Aby uzyskać więcej informacji na temat funkcji interfejsu API ODBC, zobacz SDK systemu Windows.

### <a name="remarks"></a>Uwagi

`AFX_SQL_ASYNC`po prostu wywołuje [makro AFX_ODBC_CALL](#afx_odbc_call) i ignoruje parametr *prs.* W wersjach MFC przed 4.2, `AFX_SQL_ASYNC` był używany do wywoływania funkcji INTERFEJSU API ODBC, które mogą powrócić `SQL_STILL_EXECUTING`. Jeśli funkcja INTERFEJSU API `SQL_STILL_EXECUTING`ODBC `AFX_SQL_ASYNC` powróciła, wywołałoby to . `prs->OnWaitForDataSource`

> [!NOTE]
> Klasy Odbc MFC używają teraz tylko przetwarzania synchroniczowego. Aby wykonać operację asynchronizacyjną, należy wywołać `SQLSetConnectOption`funkcję INTERFEJSU API ODBC . Aby uzyskać więcej informacji, zobacz temat "Wykonywanie funkcji asynchronicznie" w windows SDK.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdb.h

## <a name="afx_sql_sync"></a><a name="afx_sql_sync"></a>AFX_SQL_SYNC

Makro `AFX_SQL_SYNC` po prostu `SQLFunc`wywołuje funkcję .

```
AFX_SQL_SYNC(SQLFunc)
```

### <a name="parameters"></a>Parametry

*SQLFunc (Niemki)*<br/>
Funkcja INTERFEJSU API ODBC. Aby uzyskać więcej informacji na temat tych funkcji, zobacz SDK systemu Windows.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby wywołać `SQL_STILL_EXECUTING`funkcje INTERFEJSU API ODBC, które nie będą zwracać .

Przed `AFX_SQL_SYNC`wywołaniem , należy `nRetCode`zadeklarować zmienną, typu RETCODE. Można sprawdzić wartość `nRetCode` po wywołaniu makra.

Należy zauważyć, `AFX_SQL_SYNC` że implementacja zmienionych w MFC 4.2. Ponieważ sprawdzanie stanu serwera nie było `AFX_SQL_SYNC` już wymagane, wystarczy `nRetCode`przypisać wartość do programu . Na przykład zamiast nawiązywania połączenia

[!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]

można po prostu wykonać zadanie

[!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdb.h

## <a name="afxgethenv"></a><a name="afxgethenv"></a>AfxGetHENV ( AfxGetHENV )

Zwracany dojście można użyć w bezpośrednich wywołań ODBC, ale nie należy zamykać `CDatabase`dojścia lub zakładać, że dojście jest nadal prawidłowe i dostępne po zniszczeniu istniejących - lub `CRecordset`-pochodnych obiektów.

```
HENV AFXAPI AfxGetHENV();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do środowiska ODBC aktualnie używane przez MFC. Może `SQL_HENV_NULL` być, jeśli nie ma żadnych [obiektów CDatabase](../../mfc/reference/cdatabase-class.md) i nie [CRecordset](../../mfc/reference/crecordset-class.md) obiektów w użyciu.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdb.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](../../mfc/reference/mfc-macros-and-globals.md)
