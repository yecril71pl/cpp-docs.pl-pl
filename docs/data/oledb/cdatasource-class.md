---
title: Cdatasource — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDataSource
- ATL::CDataSource
- CDataSource
- ATL::CDataSource::Close
- ATL.CDataSource.Close
- CDataSource::Close
- CDataSource.Close
- ATL::CDataSource::GetInitializationString
- CDataSource.GetInitializationString
- GetInitializationString
- CDataSource::GetInitializationString
- ATL.CDataSource.GetInitializationString
- CDataSource::GetProperties
- ATL.CDataSource.GetProperties
- CDataSource.GetProperties
- ATL::CDataSource::GetProperties
- GetProperties
- ATL::CDataSource::GetProperty
- ATL.CDataSource.GetProperty
- CDataSource.GetProperty
- CDataSource::GetProperty
- ATL::CDataSource::Open
- ATL.CDataSource.Open
- CDataSource::Open
- CDataSource.Open
- CDataSource::OpenFromFileName
- ATL::CDataSource::OpenFromFileName
- OpenFromFileName
- CDataSource.OpenFromFileName
- ATL.CDataSource.OpenFromFileName
- CDataSource.OpenFromInitializationString
- OpenFromInitializationString
- CDataSource::OpenFromInitializationString
- ATL::CDataSource::OpenFromInitializationString
- ATL.CDataSource.OpenFromInitializationString
- CDataSource.OpenWithPromptFileName
- OpenWithPromptFileName
- ATL::CDataSource::OpenWithPromptFileName
- ATL.CDataSource.OpenWithPromptFileName
- CDataSource::OpenWithPromptFileName
- CDataSource::OpenWithServiceComponents
- OpenWithServiceComponents
- CDataSource.OpenWithServiceComponents
dev_langs:
- C++
helpviewer_keywords:
- CDataSource class
- Close method
- GetInitializationString method
- GetProperties method
- GetProperty method
- Open method
- OpenFromFileName method
- OpenFromInitializationString method
- OpenWithPromptFileName method
- OpenWithServiceComponents method
ms.assetid: 99bf862c-9d5c-4117-9501-aa0e2672085c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: df5a93ae8b646eb0b4f012484ef8c13d07d328da
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106314"
---
# <a name="cdatasource-class"></a>CDataSource — Klasa

Odnosi się do obiektu źródła danych OLE DB, który reprezentuje połączenie za pośrednictwem dostawcy ze źródłem danych.  
  
## <a name="syntax"></a>Składnia

```cpp
class CDataSource  
```  

## <a name="requirements"></a>Wymagania  

**Nagłówek:** atldbcli.h 
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Zamknij](#close)|Zamyka połączenie.|  
|[GetInitializationString](#getinitializationstring)|Pobiera ciąg inicjowania źródła danych, która jest obecnie otwarta.|  
|[Getproperties —](#getproperties)|Pobiera wartości właściwości ustawione dla połączonego źródła danych.|  
|[GetProperty](#getproperty)|Pobiera wartość jednej właściwości aktualnie ustawione dla połączonego źródła danych.|  
|[Otwórz](#open)|Tworzy połączenie dostawcy (źródła danych) przy użyciu `CLSID`, `ProgID`, lub `CEnumerator` moniker dostarczane przez obiekt wywołujący.|  
|[OpenFromFileName](#openfromfilename)|Otwiera źródło danych z pliku określonego przez nazwę pliku dostarczone przez użytkownika.|  
|[OpenFromInitializationString](#openfrominitializationstring)|Otwiera źródło danych, określona przez ciąg inicjalizacji.|  
|[OpenWithPromptFileName](#openwithpromptfilename)|Zezwala użytkownikowi na wybranie utworzonej wcześniej danych pliku łącza do otwarcia odpowiedniego źródła danych.|  
|[OpenWithServiceComponents](#openwithservicecomponents)|Zostanie otwarty obiekt źródła danych za pomocą okna dialogowego Łącze danych.|  
  
## <a name="remarks"></a>Uwagi  

Co najmniej jednej sesji bazy danych mogą być tworzone dla pojedynczego połączenia. Sesje te są reprezentowane przez `CSession`. Należy wywołać [CDataSource::Open](../../data/oledb/cdatasource-open.md) można otworzyć połączenia przed utworzeniem sesji z `CSession::Open`.  
  
Aby uzyskać przykład sposobu użycia `CDataSource`, zobacz [CatDB](../../visual-cpp-samples.md) próbki.  

## <a name="close"></a> CDataSource::Close

Zamyka połączenie, zwalniając `m_spInit` wskaźnika.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
void Close() throw();  
``` 

## <a name="getinitializationstring"></a> CDataSource::GetInitializationString

Pobiera ciąg inicjowania źródła danych, która jest obecnie otwarta.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetInitializationString(BSTR* pInitializationString,   
   bool bIncludePassword = false) throw();  
```  
  
#### <a name="parameters"></a>Parametry  

*pInitializationString*<br/>
[out] Wskaźnik do ciągu inicjującego.  
  
*bIncludePassword*<br/>
[in] **true** Jeśli ciąg zawiera hasło; w przeciwnym razie **false**.  
  
### <a name="return-value"></a>Wartość zwracana  

Standardowa HRESULT.  
  
### <a name="remarks"></a>Uwagi  

Wynikowy ciąg inicjowania może służyć do później ponownie otworzyć to połączenie ze źródłem danych. 
 
## <a name="getproperties"></a> CDataSource::GetProperties

Zwraca informacje o właściwości żądania obiektu źródłowego połączonych danych.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetProperties(ULONG ulPropIDSets,   
   constDBPROPIDSET* pPropIDSet,   
   ULONG* pulPropertySets,   
   DBPROPSET** ppPropsets) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  

Zobacz [IDBProperties::GetProperties](/previous-versions/windows/desktop/ms714344\(v=vs.85\)) w *OLE DB Podręcznik programisty* w Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  

Standardowa HRESULT.  
  
### <a name="remarks"></a>Uwagi  

Aby uzyskać jedną właściwość, należy użyć [GetProperty](../../data/oledb/cdatasource-getproperty.md).

## <a name="getproperty"></a> CDataSource::GetProperty

Zwraca wartość określonej właściwości dla obiektu źródłowego połączonych danych.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetProperty(const GUID& guid,   
   DBPROPID propid,   
   VARIANT* pVariant) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  

*Identyfikator GUID*<br/>
[in] Identyfikator GUID właściwością, dla której ma zostać zwrócone właściwości.  
  
*identyfikatora właściwości*<br/>
[in] Identyfikator właściwości dla właściwości do zwrócenia.  
  
*pVariant*<br/>
[out] Wskaźnik do wariant gdzie `GetProperty` zwraca wartość właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  

Standardowa HRESULT.  
  
### <a name="remarks"></a>Uwagi  

Aby uzyskać wiele właściwości, użyj [getproperties —](../../data/oledb/cdatasource-getproperties.md).

## <a name="open"></a> CDataSource::Open

Otwiera połączenie źródła danych przy użyciu `CLSID`, `ProgID`, lub `CEnumerator` monikera lub monit okna dialogowego lokalizatora.  
  
### <a name="syntax"></a>Składnia  
  
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

*Identyfikator klasy*<br/>
[in] `CLSID` Dostawcy danych.  
  
*pPropSet*<br/>
[in] Wskaźnik do tablicy [DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\)) struktury zawierający właściwości i wartości do ustawienia. Zobacz [zestawy właściwości i właściwości grupy](/previous-versions/windows/desktop/ms713696\(v=vs.85\)) w *OLE DB Podręcznik programisty* w Windows SDK.  
  
*nPropertySets*<br/>
[in] Liczba [DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\)) struktury przekazany *pPropSet* argumentu.  
  
*pName*<br/>
[in] Nazwa bazy danych, którym chcesz się połączyć.  
  
*pUserName*<br/>
[in] Nazwa użytkownika.  
  
*pPassword*<br/>
[in] Hasło użytkownika.  
  
*nInitMode*<br/>
[in] Tryb inicjowania bazy danych. Zobacz [właściwości inicjowania](/previous-versions/windows/desktop/ms723127\(v=vs.85\))w *OLE DB Podręcznik programisty* w zestawie Windows SDK dla listy metod inicjowania prawidłowe. Jeśli *nInitMode* to inicjowanie, zerowego, tryb znajduje się zestaw właściwości używany do otwierania połączenia.  
  
*szProgID*<br/>
[in] Identyfikator programu.  
  
*enumerator*<br/>
[in] A [CEnumerator](../../data/oledb/cenumerator-class.md) obiekt używany do uzyskania moniker Otwieranie połączenia, gdy obiekt wywołujący nie określi `CLSID`.  
  
*hWnd*<br/>
[in] Dojście do okna, który ma być elementem nadrzędnym okno dialogowe. Za pomocą przeciążenia funkcji, która używa *hWnd* parametr będzie automatycznie wywoływać składniki usługi; Zobacz uwagi, aby uzyskać szczegółowe informacje.  
  
*dwPromptOptions*<br/>
[in] Określa styl okna dialogowego lokalizatora do wyświetlenia. Możliwe wartości można znaleźć w temacie Msdasc.h.  
  
### <a name="return-value"></a>Wartość zwracana  

Standardowa HRESULT.  
  
### <a name="remarks"></a>Uwagi  

Przeciążenia metody, która używa *hWnd* parametru otwiera obiekt źródła danych za pomocą składników usługi w oledb32.dll; tę bibliotekę DLL zawiera implementację składniki usługi funkcje, takie jak pule zasobów, automatyczne Rejestracji w transakcji i tak dalej. Aby uzyskać więcej informacji, zobacz "OLE DB usług" w odwołaniu OLE DB programisty w [ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).  
  
Przeciążenia metody, które nie korzystają z *hWnd* parametru Otwórz obiekt źródła danych bez używania składników usługi w oledb32.dll. A [CDataSource](../../data/oledb/cdatasource-class.md) obiektu otwartej z te przeciążenia funkcji nie będzie można korzystać z funkcjonalności składniki usługi.  
  
### <a name="example"></a>Przykład  

Poniższy kod przedstawia sposób otwierania źródła danych Jet 4.0 z szablonami OLE DB. Źródło danych Jet można traktować jako źródło danych OLE DB. Jednak wywołania do `Open` wymaga dwóch zestawów właściwości: jeden dla DBPROPSET_DBINIT i inne DBPROPSET_JETOLEDB_DBINIT, dzięki czemu można ustawić DBPROP_JETOLEDB_DATABASEPASSWORD.  
  
[!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/cpp/cdatasource-open_1.cpp)]  

## <a name="openfromfilename"></a> CDataSource::OpenFromFileName

Otwiera źródło danych z pliku określonego przez nazwę pliku dostarczone przez użytkownika.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OpenFromFileName(LPCOLESTR szFileName) throw();  
```  
  
#### <a name="parameters"></a>Parametry  

*szFileName*<br/>
[in] Nazwa pliku, zwykle połączenie ze źródłem danych (. Plik UDL).  
  
Aby uzyskać więcej informacji na temat danych łączy pliki (udl), zobacz [omówienie interfejsu API łącza danych](/previous-versions/windows/desktop/ms718102\(v=vs.85\)) w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  

Standardowa HRESULT.  
  
### <a name="remarks"></a>Uwagi  

Ta metoda zostanie otwarty przy użyciu składników usługi w oledb32.dll; obiekt źródła danych Ta biblioteka DLL zawiera implementację składniki usługi funkcje, takie jak pule zasobów, automatycznej rejestracji w transakcji i tak dalej. Aby uzyskać więcej informacji, zobacz "OLE DB usług" w odwołaniu OLE DB programisty w [ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).  

## <a name="openfrominitializationstring"></a> CDataSource::OpenFromInitializationString

Otwiera źródło danych określona przez ciąg inicjowania dostarczone przez użytkownika.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OpenFromInitializationString(LPCOLESTR szInitializationString,   
   bool fPromptForInfo= false) throw();  
```  
  
#### <a name="parameters"></a>Parametry  

*szInitializationString*<br/>
[in] Ciąg inicjalizacji.  
  
*fPromptForInfo*<br/>
[in] Jeśli ten argument jest równa **true**, następnie `OpenFromInitializationString` ustawi właściwość DBPROP_INIT_PROMPT DBPROMPT_COMPLETEREQUIRED, który określa, że użytkownik jest monitowany tylko wtedy, gdy potrzeba więcej informacji. Jest to przydatne w sytuacjach, w których ciąg inicjujący określa bazę danych, który wymaga hasła, ale ciąg nie zawiera hasła. Użytkownik jest monitowany o hasło (lub wszystkie brakujące informacje) podczas próby nawiązania połączenia z bazą danych.  
  
Wartość domyślna to **false**, która określa, że użytkownik nigdy nie być monitem (zestawy DBPROP_INIT_PROMPT do DBPROMPT_NOPROMPT).  
  
### <a name="return-value"></a>Wartość zwracana  

Standardowa HRESULT.  
  
### <a name="remarks"></a>Uwagi  

Ta metoda zostanie otwarty przy użyciu składników usługi w oledb32.dll; obiekt źródła danych Ta biblioteka DLL zawiera implementację składniki usługi funkcje, takie jak pule zasobów, automatycznej rejestracji w transakcji i tak dalej.  

## <a name="openwithpromptfilename"></a> CDataSource::OpenWithPromptFileName

Ta metoda wyświetla monit okna dialogowego, a następnie otwiera źródło danych przy użyciu pliku określonego przez użytkownika.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OpenWithPromptFileName(HWND hWnd = GetActiveWindow(   ),   
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_NONE,   
   LPCOLESTR szInitialDirectory = NULL) throw();  
```  
  
#### <a name="parameters"></a>Parametry  

*hWnd*<br/>
[in] Dojście do okna, który ma być elementem nadrzędnym okno dialogowe.  
  
*dwPromptOptions*<br/>
[in] Określa styl okna dialogowego lokalizatora do wyświetlenia. Możliwe wartości można znaleźć w temacie Msdasc.h.  
  
*szInitialDirectory*<br/>
[in] Początkowy katalog do wyświetlenia w oknie dialogowym lokalizatora.  
  
### <a name="return-value"></a>Wartość zwracana  

Standardowa HRESULT.  
  
### <a name="remarks"></a>Uwagi  

Ta metoda zostanie otwarty przy użyciu składników usługi w oledb32.dll; obiekt źródła danych Ta biblioteka DLL zawiera implementację składniki usługi funkcje, takie jak pule zasobów, automatycznej rejestracji w transakcji i tak dalej. Aby uzyskać więcej informacji, zobacz "OLE DB usług" w odwołaniu OLE DB programisty w [ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).

## <a name="openwithservicecomponents"></a> CDataSource::OpenWithServiceComponents

Zostanie otwarty przy użyciu składników usługi w oledb32.dll obiektu źródła danych.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OpenWithServiceComponents (const CLSID clsid,  
   DBPROPSET* pPropset = NULL,  
   ULONG ulPropSets = 1);  

HRESULT OpenWithServiceComponents (LPCSTR szProgID,  
   DBPROPSET* pPropset = NULL,  
   ULONG ulPropSets = 1);  
```  
  
#### <a name="parameters"></a>Parametry  

*Identyfikator klasy*<br/>
[in] `CLSID` Dostawcy danych.  
  
*szProgID*<br/>
[in] Identyfikator programu dostawcę danych.  
  
*pPropset*<br/>
[in] Wskaźnik do tablicy [DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\)) struktury zawierający właściwości i wartości do ustawienia. Zobacz [zestawy właściwości i właściwości grupy](/previous-versions/windows/desktop/ms713696\(v=vs.85\)) w *OLE DB Podręcznik programisty* w Windows SDK. Jeśli obiekt źródła danych jest inicjowany, właściwości muszą należeć do grupy właściwości źródła danych. Jeśli tę samą właściwość została określona więcej niż jeden raz w *pPropset*, która wartość zostaje użyta jest specyficzny dla dostawcy. Jeśli *ulPropSets* wynosi zero, ten parametr jest ignorowany.  
  
*ulPropSets*<br/>
[in] Liczba [DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\)) struktury przekazany *pPropSet* argumentu. Jeśli jest to zero, dostawca ignoruje *pPropset*.  
  
### <a name="return-value"></a>Wartość zwracana  

Standardowa HRESULT.  
  
### <a name="remarks"></a>Uwagi  

Ta metoda zostanie otwarty przy użyciu składników usługi w oledb32.dll; obiekt źródła danych Ta biblioteka DLL zawiera implementację składniki usługi funkcje, takie jak pule zasobów, automatycznej rejestracji w transakcji i tak dalej. Aby uzyskać więcej informacji, zobacz "OLE DB usług" w odwołaniu OLE DB programisty w [ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).    

## <a name="see-also"></a>Zobacz też  

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)