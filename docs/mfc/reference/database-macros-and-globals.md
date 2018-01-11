---
title: Makra i funkcje globalne bazy danych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AFXDB/AFX_ODBC_CALL
- AFXDB/AFX_SQL_ASYNC
- AFXDB/AFX_SQL_SYNC
- AFXDB/AfxGetHENV
dev_langs: C++
helpviewer_keywords:
- global database functions [MFC]
- database macros [MFC]
- database globals [MFC]
- global functions [MFC], database functions
- macros [MFC], MFC database
ms.assetid: 5b9b9e61-1cf9-4345-9f29-3807dd466488
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5f43135678c54ed2f837934c19a8543c86a65fdb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="database-macros-and-globals"></a>Makra i funkcje globalne bazy danych
Makra i funkcje globalne wymienione poniżej dotyczą aplikacji bazy danych opartej na ODBC. Nie są używane z aplikacji opartych na DAO.  
  
 Przed 4.2 MFC, makra `AFX_SQL_ASYNC` i `AFX_SQL_SYNC` nadać operacji asynchronicznych możliwość yield czasu na inne procesy. Począwszy od stosowania tych makr zmienić, ponieważ tylko operacje synchroniczne klasach MFC ODBC MFC 4.2. Makro `AFX_ODBC_CALL` nowych do MFC 4.2.  
  
### <a name="database-macros"></a>Makra bazy danych  
  
|||  
|-|-|  
|[AFX_ODBC_CALL —](#afx_odbc_call)|Wywołania funkcji ODBC API, która zwraca `SQL_STILL_EXECUTING`. `AFX_ODBC_CALL`wielokrotnie wywoła funkcję aż już zwraca `SQL_STILL_EXECUTING`.|  
|[AFX_SQL_ASYNC —](#afx_sql_async)|Wywołania `AFX_ODBC_CALL`.|  
|[AFX_SQL_SYNC —](#afx_sql_sync)|Wywołuje funkcję interfejsu API ODBC, która nie zwraca `SQL_STILL_EXECUTING`.|  
  
### <a name="database-globals"></a>Zmienne globalne bazy danych  
  
|||  
|-|-| 
|[Afxdbinitmodule —](#afxdbinitmodule)|Dodaje obsługę bazy danych regularne biblioteki DLL MFC, która jest połączona dynamicznie z MFC.| 
|[Afxgethenv —](#afxgethenv)|Pobiera dojścia środowiska ODBC obecnie w użyciu przez MFC. Przy użyciu tego uchwytu w bezpośrednie wywołania ODBC.|  


## <a name="afxdbinitmodule"></a>Afxdbinitmodule —
Dla bazy danych MFC (lub DAO) obsługuje z regularne biblioteki DLL MFC, która jest połączona dynamicznie z MFC, dodaj wywołanie tej funkcji w bibliotece regularne DLL MFC **CWinApp::InitInstance** funkcji, aby zainicjować MFC bazy danych biblioteki DLL.  
   
### <a name="syntax"></a>Składnia    
```
void AFXAPI AfxDbInitModule( );    
```  
   
### <a name="remarks"></a>Uwagi  
 Upewnij się, to wywołanie występuje przed wywołaniem dowolnej klasy podstawowej ani żadnym z dodanych kod, który uzyskuje dostęp do bazy danych MFC DLL. Baza danych MFC DLL jest rozszerzeniem MFC DLL; w celu rozszerzenia MFC DLL uzyskać przewodowej do **CDynLinkLibrary** łańcucha, należy utworzyć **CDynLinkLibrary** obiektu w kontekście każdy moduł, który będzie go używać. `AfxDbInitModule`Tworzy **CDynLinkLibrary** obiekt w kontekście użytkownika regularne DLL MFC, tak aby pobiera ona przewodowej do **CDynLinkLibrary** obiekt łańcucha regularne biblioteki DLL MFC.  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** < afxdll_.h >  
   
### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)
 
  

##  <a name="afx_odbc_call"></a>AFX_ODBC_CALL —  
 Umożliwia to makro wywołania dowolnej funkcji interfejsu API ODBC, które mogą zwracać `SQL_STILL_EXECUTING`.  
  
```  
AFX_ODBC_CALL(SQLFunc)  
```  
  
### <a name="parameters"></a>Parametry  
 `SQLFunc`  
 Funkcja interfejsu API ODBC. Aby uzyskać więcej informacji na temat funkcji interfejsu API ODBC zobacz zestaw Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 `AFX_ODBC_CALL`wielokrotnie wywołuje funkcję aż już zwraca `SQL_STILL_EXECUTING`.  
  
 Przed wywołaniem `AFX_ODBC_CALL`, należy zadeklarować zmienną, `nRetCode`, typu **RETCODE**.  
  
 Należy pamiętać, że MFC ODBC klasy teraz używana tylko synchronicznego przetwarzania. Aby można było wykonać operację asynchroniczną, musi wywoływać funkcję interfejsu API ODBC **SQLSetConnectOption**. Aby uzyskać więcej informacji zobacz temat "Wykonywania funkcji asynchronicznie" w zestawie Windows SDK.  

  
### <a name="example"></a>Przykład  
 W tym przykładzie użyto `AFX_ODBC_CALL` do wywołania **SQLColumns** funkcji interfejsu API ODBC, która zwraca listy kolumn w tabeli o nazwie `strTableName`. Należy pamiętać, deklaracji `nRetCode` i korzystania z zestawu rekordów elementy członkowskie danych do przekazania parametrów do funkcji. Również pokazano w przykładzie sprawdzanie wyników wywołania z **Sprawdź**, funkcji członkowskiej klasy `CRecordset`. Zmienna `prs` jest wskaźnikiem do `CRecordset` obiektu zadeklarowany w innym miejscu.  
  
 [!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  

##  <a name="afx_sql_async"></a>AFX_SQL_ASYNC —  
 Implementacja to makro zmienione w MFC 4.2.  
  
```   
AFX_SQL_ASYNC(prs, SQLFunc)   
```  
  
### <a name="parameters"></a>Parametry  
 `prs`  
 Wskaźnik do `CRecordset` obiektu lub `CDatabase` obiektu. Począwszy od MFC 4.2, wartość tego parametru jest ignorowana.  
  
 `SQLFunc`  
 Funkcja interfejsu API ODBC. Aby uzyskać więcej informacji na temat funkcji interfejsu API ODBC zobacz zestaw Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 `AFX_SQL_ASYNC`po prostu wywołuje makro [afx_odbc_call —](#afx_odbc_call) ignoruje `prs` parametru. W wersjach MFC przed 4.2 `AFX_SQL_ASYNC` użyto do wywołania funkcji ODBC API, które mogą zwracać `SQL_STILL_EXECUTING`. Jeśli funkcja interfejsu API ODBC został zwrócony `SQL_STILL_EXECUTING`, następnie `AFX_SQL_ASYNC` spowodowałoby wywołanie `prs->OnWaitForDataSource`.  
  
> [!NOTE]
>  Klasy MFC ODBC teraz przy użyciu przetwarzania synchronicznego tylko. Aby można było wykonać operację asynchroniczną, musi wywoływać funkcję interfejsu API ODBC **SQLSetConnectOption**. Aby uzyskać więcej informacji zobacz temat "Wykonywania funkcji asynchronicznie" w zestawie Windows SDK.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdb.h  
  
##  <a name="afx_sql_sync"></a>AFX_SQL_SYNC —  
 `AFX_SQL_SYNC` Makro po prostu wywołuje funkcję `SQLFunc`.  
  
```   
AFX_SQL_SYNC(SQLFunc)   
```  
  
### <a name="parameters"></a>Parametry  
 `SQLFunc`  
 Funkcja interfejsu API ODBC. Aby uzyskać więcej informacji o tych funkcjach zobacz zestaw Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Umożliwia to makro wywołanie funkcji ODBC API, które nie zwracają `SQL_STILL_EXECUTING`.  
  
 Przed wywołaniem `AFX_SQL_SYNC`, należy zadeklarować zmienną, `nRetCode`, typu **RETCODE**. Należy sprawdzić wartość `nRetCode` po wywołaniu makra.  
  
 Należy pamiętać, że implementacja `AFX_SQL_SYNC` zmienione w MFC 4.2. Ponieważ sprawdzanie stanu serwera nie jest już wymagane, `AFX_SQL_SYNC` po prostu przypisuje wartość do `nRetCode`. Na przykład zamiast wywołania  
  
 [!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]  
  
 po prostu umożliwia przypisanie  
  
 [!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdb.h  
  
##  <a name="afxgethenv"></a>Afxgethenv —  
 Zwracane dojście można używać w bezpośrednie wywołania ODBC, ale nie może zamknąć dojścia ani założono, że dojście jest nadal prawidłowa i dostępna po wszelkie istniejące `CDatabase`- lub `CRecordset`-obiekty pochodne zostały zniszczone.  
  
```   
HENV AFXAPI AfxGetHENV(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojścia środowiska ODBC obecnie w użyciu przez MFC. Może być `SQL_HENV_NULL` przypadku nie [cdatabase —](../../mfc/reference/cdatabase-class.md) obiektów i nie [crecordset —](../../mfc/reference/crecordset-class.md) obiektów w użyciu.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdb.h  
    
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
