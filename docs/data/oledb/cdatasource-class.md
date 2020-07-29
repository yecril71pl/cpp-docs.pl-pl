---
title: CDataSource — Klasa
ms.date: 11/04/2016
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
ms.openlocfilehash: f6b5182fdc451217e2f61642f96e77f679c45d37
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216508"
---
# <a name="cdatasource-class"></a>CDataSource — Klasa

Odnosi się do obiektu źródła danych OLE DB, który reprezentuje połączenie przez dostawcę ze źródłem danych.

## <a name="syntax"></a>Składnia

```cpp
class CDataSource
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Zamknij](#close)|Zamknięcie połączenia.|
|[GetInitializationString](#getinitializationstring)|Pobiera ciąg inicjujący źródła danych, które jest aktualnie otwarte.|
|[GetProperties](#getproperties)|Pobiera wartości właściwości aktualnie ustawionych dla połączonego źródła danych.|
|[GetProperty](#getproperty)|Pobiera wartość pojedynczej właściwości, która jest aktualnie ustawiona dla połączonego źródła danych.|
|[Otwórz](#open)|Tworzy połączenie z dostawcą (źródłem danych) przy użyciu albo `CLSID` `ProgID` lub `CEnumerator` monikera dostarczonego przez wywołującego.|
|[OpenFromFileName](#openfromfilename)|Otwiera źródło danych z pliku określonego przez nazwę pliku dostarczoną przez użytkownika.|
|[OpenFromInitializationString](#openfrominitializationstring)|Otwiera źródło danych określone przez ciąg inicjujący.|
|[OpenWithPromptFileName](#openwithpromptfilename)|Umożliwia użytkownikowi wybranie utworzonego wcześniej pliku linku danych w celu otworzenia odpowiedniego źródła danych.|
|[OpenWithServiceComponents](#openwithservicecomponents)|Otwiera obiekt źródła danych za pomocą okna dialogowego łącze danych.|

## <a name="remarks"></a>Uwagi

Co najmniej jedna sesja bazy danych może zostać utworzona dla jednego połączenia. Te sesje są reprezentowane przez program `CSession` . Musisz wywołać [CDataSource:: Open](../../data/oledb/cdatasource-open.md) , aby otworzyć połączenie przed utworzeniem sesji przy użyciu usługi `CSession::Open` .

Aby zapoznać się z przykładem sposobu użycia `CDataSource` , zobacz przykład [catdb](../../overview/visual-cpp-samples.md) .

## <a name="cdatasourceclose"></a><a name="close"></a>CDataSource:: Close

Zamyka połączenie, zwalniając `m_spInit` wskaźnik.

### <a name="syntax"></a>Składnia

```cpp
void Close() throw();
```

## <a name="cdatasourcegetinitializationstring"></a><a name="getinitializationstring"></a>CDataSource:: GetInitializationString

Pobiera ciąg inicjujący źródła danych, które jest aktualnie otwarte.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetInitializationString(BSTR* pInitializationString,
   bool bIncludePassword = false) throw();
```

#### <a name="parameters"></a>Parametry

*pInitializationString*<br/>
określoną Wskaźnik do ciągu inicjującego.

*bIncludePassword*<br/>
[w] **`true`** Jeśli ciąg zawiera hasło; w przeciwnym razie **`false`** .

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Otrzymany ciąg inicjujący może zostać użyty do późniejszego ponownego otwarcia tego połączenia ze źródłem danych.

## <a name="cdatasourcegetproperties"></a><a name="getproperties"></a>CDataSource:: GetProperties

Zwraca informacje o właściwościach żądane dla połączonego obiektu źródła danych.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetProperties(ULONG ulPropIDSets,
   constDBPROPIDSET* pPropIDSet,
   ULONG* pulPropertySets,
   DBPROPSET** ppPropsets) const throw();
```

#### <a name="parameters"></a>Parametry

Zobacz [IDBProperties:: GetProperties](/previous-versions/windows/desktop/ms714344(v=vs.85)) w *odniesieniu do OLE DB programisty* w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Aby uzyskać pojedynczą właściwość, należy użyć [GetProperty](../../data/oledb/cdatasource-getproperty.md).

## <a name="cdatasourcegetproperty"></a><a name="getproperty"></a>CDataSource:: GetProperty

Zwraca wartość określonej właściwości dla połączonego obiektu źródła danych.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetProperty(const GUID& guid,
   DBPROPID propid,
   VARIANT* pVariant) const throw();
```

#### <a name="parameters"></a>Parametry

*ident*<br/>
podczas Identyfikator GUID identyfikujący zestaw właściwości, dla którego ma zostać zwrócona właściwość.

*identyfikatora właściwości*<br/>
podczas Identyfikator właściwości do zwrócenia.

*pVariant*<br/>
określoną Wskaźnik do wariantu, gdzie `GetProperty` zwraca wartość właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Aby uzyskać wiele właściwości, użyj [Właściwości GetProperties](../../data/oledb/cdatasource-getproperties.md).

## <a name="cdatasourceopen"></a><a name="open"></a>CDataSource:: Open

Otwiera połączenie ze źródłem danych przy użyciu `CLSID` , `ProgID` lub `CEnumerator` moniker lub wyświetla użytkownikowi okno dialogowe lokalizatora.

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

*Identyfikator*<br/>
podczas `CLSID`Dostawcy danych.

*pPropSet*<br/>
podczas Wskaźnik do tablicy struktur [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) zawierających właściwości i wartości, które mają zostać ustawione. Zobacz [zestawy właściwości i grupy właściwości](/previous-versions/windows/desktop/ms713696(v=vs.85)) w *odniesieniu do OLE DB programisty* w Windows SDK.

*nPropertySets*<br/>
podczas Liczba struktur [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) przeniesiona w argumencie *pPropSet* .

*pName*<br/>
podczas Nazwa bazy danych, z którą ma zostać nawiązane połączenie.

*pUserName*<br/>
podczas Nazwa użytkownika.

*pPassword*<br/>
podczas Hasło użytkownika.

*nInitMode*<br/>
podczas Tryb inicjalizacji bazy danych. Aby zapoznać się z listą prawidłowych trybów inicjalizacji, zobacz [Właściwości inicjacji](/previous-versions/windows/desktop/ms723127(v=vs.85))w *Kompendium OLE DB programisty* w Windows SDK. Jeśli *nInitMode* ma wartość zero, w zestawie właściwości używanym do otwierania połączenia nie jest dostępny żaden tryb inicjalizacji.

*szProgID*<br/>
podczas Identyfikator programu.

*liczeni*<br/>
podczas Obiekt [CEnumerator](../../data/oledb/cenumerator-class.md) używany do uzyskania monikera otwierającego połączenie, gdy obiekt wywołujący nie określi `CLSID` .

*Właściwość*<br/>
podczas Dojście do okna, które ma być obiektem nadrzędnym okna dialogowego. Użycie przeciążenia funkcji korzystającej z parametru *HWND* spowoduje automatyczne wywołanie składników usługi; Aby uzyskać szczegółowe informacje, zobacz uwagi.

*dwPromptOptions*<br/>
podczas Określa styl okna dialogowego lokalizatora do wyświetlenia. Więcej wartości można znaleźć w Msdasc. h.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Przeciążenie metody, która używa parametru *HWND* otwiera obiekt źródła danych ze składnikami usługi w oledb32.dll; Ta biblioteka DLL zawiera implementację funkcji składników usługi, takich jak pule zasobów, automatyczne rejestracje transakcji itd. Aby uzyskać więcej informacji, zobacz informacje dotyczące OLE DB w [podręczniku OLE DB programisty](/previous-versions/windows/desktop/ms713643(v=vs.85)).

Przeciążenia metody, które nie używają parametru *HWND* , otwierają obiekt źródła danych bez używania składników usługi w oledb32.dll. Obiekt [CDataSource](../../data/oledb/cdatasource-class.md) otwarty przy użyciu tych przeciążeń funkcji nie będzie mógł korzystać z żadnej funkcji składników usługi.

### <a name="example"></a>Przykład

Poniższy kod pokazuje, jak otworzyć źródło danych aparatu Jet 4,0 przy użyciu szablonów OLE DB. Źródło danych aparatu Jet jest traktowane jako OLE DB źródło danych. Jednak połączenie `Open` wymaga dwóch zestawów właściwości: jeden dla DBPROPSET_DBINIT i innych dla DBPROPSET_JETOLEDB_DBINIT, dzięki czemu można ustawić DBPROP_JETOLEDB_DATABASEPASSWORD.

[!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/cpp/cdatasource-open_1.cpp)]

## <a name="cdatasourceopenfromfilename"></a><a name="openfromfilename"></a>CDataSource:: OpenFromFileName

Otwiera źródło danych z pliku określonego przez nazwę pliku dostarczoną przez użytkownika.

### <a name="syntax"></a>Składnia

```cpp
HRESULT OpenFromFileName(LPCOLESTR szFileName) throw();
```

#### <a name="parameters"></a>Parametry

*szFileName*<br/>
podczas Nazwa pliku, zazwyczaj połączenie ze źródłem danych (. UDL).

Aby uzyskać więcej informacji na temat plików łączy danych (pliki. udl), zobacz [Omówienie interfejsu API linku danych](/previous-versions/windows/desktop/ms718102(v=vs.85)) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta metoda otwiera obiekt źródła danych przy użyciu składników usługi w oledb32.dll; Ta biblioteka DLL zawiera implementację funkcji składników usługi, takich jak pule zasobów, automatyczne rejestracje transakcji itd. Aby uzyskać więcej informacji, zobacz informacje dotyczące OLE DB w [podręczniku OLE DB programisty](/previous-versions/windows/desktop/ms713643(v=vs.85)).

## <a name="cdatasourceopenfrominitializationstring"></a><a name="openfrominitializationstring"></a>CDataSource:: OpenFromInitializationString

Otwiera źródło danych określone przez podany przez użytkownika ciąg inicjujący.

### <a name="syntax"></a>Składnia

```cpp
HRESULT OpenFromInitializationString(LPCOLESTR szInitializationString,
   bool fPromptForInfo= false) throw();
```

#### <a name="parameters"></a>Parametry

*szInitializationString*<br/>
podczas Ciąg inicjujący.

*fPromptForInfo*<br/>
podczas Jeśli ten argument jest ustawiony na **`true`** , `OpenFromInitializationString` zostanie ustawiona właściwość DBPROP_INIT_PROMPT na DBPROMPT_COMPLETEREQUIRED, co oznacza, że użytkownik zostanie poproszony tylko wtedy, gdy potrzebujesz więcej informacji. Jest to przydatne w sytuacjach, w których ciąg inicjujący określa bazę danych, która wymaga hasła, ale ciąg nie zawiera hasła. Podczas próby nawiązania połączenia z bazą danych użytkownik zostanie poproszony o podanie hasła (lub innych brakujących informacji).

Wartość domyślna to **`false`** , która określa, że użytkownik nigdy nie jest monitowany (ustawia DBPROP_INIT_PROMPT na DBPROMPT_NOPROMPT).

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta metoda otwiera obiekt źródła danych przy użyciu składników usługi w oledb32.dll; Ta biblioteka DLL zawiera implementację funkcji składników usługi, takich jak pule zasobów, automatyczne rejestracje transakcji itd.

## <a name="cdatasourceopenwithpromptfilename"></a><a name="openwithpromptfilename"></a>CDataSource:: OpenWithPromptFileName

Ta metoda wyświetla użytkownikowi okno dialogowe, a następnie otwiera źródło danych przy użyciu pliku określonego przez użytkownika.

### <a name="syntax"></a>Składnia

```cpp
HRESULT OpenWithPromptFileName(HWND hWnd = GetActiveWindow(   ),
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_NONE,
   LPCOLESTR szInitialDirectory = NULL) throw();
```

#### <a name="parameters"></a>Parametry

*Właściwość*<br/>
podczas Dojście do okna, które ma być obiektem nadrzędnym okna dialogowego.

*dwPromptOptions*<br/>
podczas Określa styl okna dialogowego lokalizatora do wyświetlenia. Więcej wartości można znaleźć w Msdasc. h.

*szInitialDirectory*<br/>
podczas Początkowy katalog do wyświetlenia w oknie dialogowym lokalizatora.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta metoda otwiera obiekt źródła danych przy użyciu składników usługi w oledb32.dll; Ta biblioteka DLL zawiera implementację funkcji składników usługi, takich jak pule zasobów, automatyczne rejestracje transakcji itd. Aby uzyskać więcej informacji, zobacz informacje dotyczące OLE DB w [podręczniku OLE DB programisty](/previous-versions/windows/desktop/ms713643(v=vs.85)).

## <a name="cdatasourceopenwithservicecomponents"></a><a name="openwithservicecomponents"></a>CDataSource:: OpenWithServiceComponents

Otwiera obiekt źródła danych przy użyciu składników usługi w oledb32.dll.

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

*Identyfikator*<br/>
podczas `CLSID`Dostawcy danych.

*szProgID*<br/>
podczas Identyfikator programu dostawcy danych.

*pPropset*<br/>
podczas Wskaźnik do tablicy struktur [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) zawierających właściwości i wartości, które mają zostać ustawione. Zobacz [zestawy właściwości i grupy właściwości](/previous-versions/windows/desktop/ms713696(v=vs.85)) w *odniesieniu do OLE DB programisty* w Windows SDK. Jeśli obiekt źródła danych jest zainicjowany, właściwości muszą należeć do grupy właściwości źródła danych. Jeśli ta sama właściwość została określona więcej niż raz w *pPropset*, a następnie używana jest wartość określona dla dostawcy. Jeśli *ulPropSets* ma wartość zero, ten parametr jest ignorowany.

*ulPropSets*<br/>
podczas Liczba struktur [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) przeniesiona w argumencie *pPropSet* . Jeśli wartość jest równa zero, Dostawca ignoruje *pPropset*.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta metoda otwiera obiekt źródła danych przy użyciu składników usługi w oledb32.dll; Ta biblioteka DLL zawiera implementację funkcji składników usługi, takich jak pule zasobów, automatyczne rejestracje transakcji itd. Aby uzyskać więcej informacji, zobacz informacje dotyczące OLE DB w [podręczniku OLE DB programisty](/previous-versions/windows/desktop/ms713643(v=vs.85)).

## <a name="see-also"></a>Zobacz także

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Dokumentacja szablonów klientów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
