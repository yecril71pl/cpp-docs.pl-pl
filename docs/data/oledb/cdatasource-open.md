---
title: CDataSource::Open | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDataSource::Open
- ATL.CDataSource.Open
- CDataSource::Open
- CDataSource.Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: a6d28bd1-799a-48ed-8993-5f82d1705b77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3196aa89426e895dd6b73b28ce197e8f271a0262
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdatasourceopen"></a>CDataSource::Open
Otwiera połączenie źródła danych przy użyciu **CLSID**, **ProgID**, lub `CEnumerator` krótkiej nazwy lub monitu z oknem dialogowym lokalizatora.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Open(const CLSID& clsid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1) throw();  


HRESULT Open(const CLSID& clsid,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0) throw();HRESULT Open(LPCTSTR szProgID,  
  DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1) throw();HRESULT Open(LPCTSTR szProgID,  
   LPCTSTR pName,  LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0) throw();  

HRESULT Open(const CEnumerator& enumerator,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1) throw();  

HRESULT Open(const CEnumerator& enumerator,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0) throw();  

HRESULT Open(HWND hWnd = GetActiveWindow(),  
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_WIZARDSHEET) throw();

HRESULT Open(LPCWSTR szProgID,   
  DBPROPSET* pPropSet = NULL,   
   ULONG nPropertySets = 1) throw();

HRESULT Open(LPCSTR szProgID,   
   LPCTSTR pName,LPCTSTR pUserName = NULL,   
   LPCTSTR pPassword = NULL,   
   long nInitMode = 0) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `clsid`  
 [in] **CLSID** dostawcy danych.  
  
 *pPropSet*  
 [in] Wskaźnik do tablicy [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) struktury zawierające właściwości i wartości, które można ustawić. Zobacz [zestawy właściwości i grup właściwości](https://msdn.microsoft.com/en-us/library/ms713696.aspx) w *OLE DB Podręcznik programisty* w systemie Windows SDK.  
  
 *nPropertySets*  
 [in] Liczba [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) przekazano struktury *pPropSet* argumentu.  
  
 *pName*  
 [in] Nazwa bazy danych, którym chcesz się połączyć.  
  
 *pUserName*  
 [in] Nazwa użytkownika.  
  
 *pPassword*  
 [in] Hasło użytkownika.  
  
 `nInitMode`  
 [in] Tryb inicjowania bazy danych. Zobacz [właściwości inicjowania](https://msdn.microsoft.com/en-us/library/ms723127.aspx)w *OLE DB Podręcznik programisty* w zestawie Windows SDK dla listy metod inicjowania prawidłowe. Jeśli `nInitMode` jest zero, inicjowanie tryb jest uwzględniona w zestawie właściwości użyty do otwarcia połączenia.  
  
 `szProgID`  
 [in] Identyfikator programu.  
  
 `enumerator`  
 [in] A [CEnumerator](../../data/oledb/cenumerator-class.md) obiekt używany do uzyskania moniker otwierania połączenia, gdy obiekt wywołujący nie określi **CLSID**.  
  
 `hWnd`  
 [in] Dojście do okna, który ma być nadrzędną okna dialogowego. Przy użyciu przeciążenie funkcji, która używa `hWnd` parametru automatycznie wywoła składniki usługi; więcej szczegółów, zobacz uwagi.  
  
 `dwPromptOptions`  
 [in] Określa styl okna dialogowego lokalizatora do wyświetlenia. Możliwe wartości można znaleźć w temacie Msdasc.h.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Przeciążenie metody, która używa `hWnd` parametru otwiera obiekt źródła danych ze składnikami usługi w oledb32.dll; tej biblioteki DLL zawiera implementację funkcji składników usług, takich jak pule zasobów, automatycznej rejestracji w transakcji, i tak dalej. Aby uzyskać więcej informacji, zobacz "OLE DB Services" w OLE DB Podręcznik programisty na [ http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).  
  
 Przeciążenia metody, które nie używają `hWnd` parametru otworzyć obiektu źródła danych bez użycia w oledb32.dll składników usługi. A [CDataSource](../../data/oledb/cdatasource-class.md) obiektu otworzyć za pomocą przeciążenia tych funkcji nie będzie można korzystać z funkcjonalności składników usługi.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób otwierania Jet 4.0 źródła danych z szablonami OLE DB. Źródło danych Jet są traktowane jako źródło danych OLE DB. Jednak wywołania do **Otwórz** potrzebuje dwóch zestawów właściwości: jeden dla **DBPROPSET_DBINIT** i drugi dla **DBPROPSET_JETOLEDB_DBINIT**, dzięki czemu można ustawić  **DBPROP_JETOLEDB_DATABASEPASSWORD**.  
  
 [!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/cpp/cdatasource-open_1.cpp)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDataSource, klasa](../../data/oledb/cdatasource-class.md)
