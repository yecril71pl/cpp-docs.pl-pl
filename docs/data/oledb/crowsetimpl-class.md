---
title: CRowsetImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- CRowsetImpl
- ATL.CRowsetImpl
- ATL::CRowsetImpl
- CRowsetImpl.NameFromDBID
- CRowsetImpl::NameFromDBID
- CRowsetImpl.SetCommandText
- CRowsetImpl::SetCommandText
- GetColumnInfo
- CRowsetImpl.GetColumnInfo
- CRowsetImpl::GetColumnInfo
- CRowsetImpl::GetCommandFromID
- GetCommandFromID
- CRowsetImpl.GetCommandFromID
- CRowsetImpl.ValidateCommandID
- CRowsetImpl::ValidateCommandID
- CRowsetImpl.m_rgRowData
- CRowsetImpl::m_rgRowData
- CRowsetImpl::m_strCommandText
- CRowsetImpl.m_strCommandText
- CRowsetImpl::m_strIndexText
- CRowsetImpl.m_strIndexText
helpviewer_keywords:
- CRowsetImpl class
- NameFromDBID method
- SetCommandText method
- GetColumnInfo method
- GetCommandFromID method
- ValidateCommandID method
- m_rgRowData
- m_strCommandText
- m_strIndexText
ms.assetid: e97614b3-b11d-4806-a0d3-b9401331473f
ms.openlocfilehash: 1fac3a74ca259fe3b680355fadc7f9bbd6e3cc13
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368711"
---
# <a name="crowsetimpl-class"></a>CRowsetImpl — Klasa

Zapewnia standardową implementację zestawu wierszy OLE DB bez konieczności wielokrotnego dziedziczenia wiele implementacji interfejsów.

## <a name="syntax"></a>Składnia

```cpp
template <
   class T,
   class Storage,
   class CreatorClass,
   class ArrayType = CAtlArray<Storage>,
   class RowClass = CSimpleRow,
   class RowsetInterface = IRowsetImpl <T, IRowset>
>
class CRowsetImpl : 
   public CComObjectRootEx<CreatorClass::_ThreadModel>,
   public CRowsetBaseImpl<T, Storage, ArrayType, RowsetInterface>,
   public IRowsetInfoImpl<T, CreatorClass::_PropClass>
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa użytkownika, która pochodzi od klasy `CRowsetImpl`.

*Storage*<br/>
Klasa rekordu użytkownika.

*CreatorClass*<br/>
Klasa, która zawiera właściwości dla zestawu wierszy; Zazwyczaj polecenia.

*ArrayType*<br/>
Klasa, która będzie działał jako magazyn dla zestawu wierszy danych. Ten parametr `CAtlArray`, ale może być dowolnym klasę, która obsługuje wymaganych funkcji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldb.h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[NameFromDBID](#namefromdbid)|Wyodrębnia z ciągu `DBID` i kopiuje go do *bstr* przekazany.|
|[SetCommandText](#setcommandtext)|Weryfikuje i przechowuje `DBID`s w dwóch ciągów ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).|

### <a name="overridable-methods"></a>Możliwym do zastąpienia metody

|||
|-|-|
|[GetColumnInfo](#getcolumninfo)|Pobiera informacje o kolumnach dla żądania danego klienta.|
|[GetCommandFromID](#getcommandfromid)|Sprawdza, jeśli jednego lub obu tych parametrów zawiera wartości typu ciąg i kopiuje wartości ciągu do elementów członkowskich danych [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|
|[ValidateCommandID](#validatecommandid)|Sprawdza, aby zobaczyć, czy w obu i / lub `DBID`s zawierają wartości ciągu, a jeśli tak, kopiuje je do swoich elementów członkowskich danych [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_rgRowData](#rgrowdata)|Domyślnie `CAtlArray` , templatizes na argument szablonu rekordu użytkownika `CRowsetImpl`. Innej tablicy typu klasy mogą być używane przez zmianę `ArrayType` argumentu szablonu `CRowsetImpl`.|
|[m_strCommandText](#strcommandtext)|Zawiera polecenia początkowego zestawu wierszy.|
|[m_strIndexText](#strindextext)|Zawiera indeksu początkowego zestawu wierszy.|

## <a name="remarks"></a>Uwagi

`CRowsetImpl` udostępnia zastąpień w formie upcasts statyczne. Metody kontrolowania sposobu, w którym dany zestaw wierszy zostanie przeprowadzona Weryfikacja tekst polecenia. Możesz utworzyć swój własny `CRowsetImpl`-stylu klasy, wprowadzając interfejsów sieci implementacji dziedziczone wielu. Jedyną metodą, dla którego należy podać implementacja jest `Execute`. W zależności od rodzaju zestawu wierszy jest tworzony, metody creator będzie oczekiwać na różnych podpisów dla `Execute`. Na przykład, jeśli używasz `CRowsetImpl`-klasy do zaimplementowania zestawu wierszy schematu `Execute` metoda będzie mieć następujący podpis:

`HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`

Jeśli tworzysz `CRowsetImpl`-klasy do zaimplementowania polecenia lub zestaw wierszy sesji, `Execute` metoda będzie mieć następujący podpis:

`HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`

Do wdrożenia z żadnego z `CRowsetImpl`-pochodne `Execute` metod, musi wypełnić swoje buforów danych wewnętrznych ([m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)).

## <a name="namefromdbid"></a> CRowsetImpl::NameFromDBID

Wyodrębnia z ciągu `DBID` i kopiuje go do *bstr* przekazany.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CRowsetBaseImpl::NameFromDBID(DBID* pDBID,
   CComBSTR& bstr,
   bool bIndex);
```

#### <a name="parameters"></a>Parametry

*pDBID*<br/>
[in] Wskaźnik do `DBID` z którego mają zostać wyodrębnione ciągu.

*BSTR*<br/>
[in] A [CComBSTR](../../atl/reference/ccombstr-class.md) odwołanie do Umieść kopię `DBID` ciągu.

*bIndex*<br/>
[in] **true** Jeśli indeks `DBID`; **false** Jeśli tabela `DBID`.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT. W zależności od tego, czy `DBID` tabeli lub indeksu (wskazywane przez *bIndex*), metoda zwraca DB_E_NOINDEX lub DB_E_NOTABLE.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana `CRowsetImpl` implementacje [validatecommandid —](../../data/oledb/crowsetimpl-validatecommandid.md) i [getcommandfromid —](../../data/oledb/crowsetimpl-getcommandfromid.md).

## <a name="setcommandtext"></a> CRowsetImpl::SetCommandText

Weryfikuje i przechowuje `DBID`s w dwóch ciągów ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).

### <a name="syntax"></a>Składnia

```cpp
HRESULT CRowsetBaseImpl::SetCommandText(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Parametry

*pTableID*<br/>
[in] Wskaźnik do `DBID` reprezentujący identyfikator tabeli.

*pIndexID*<br/>
[in] Wskaźnik do `DBID` reprezentujący identyfikator indeksu.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT.

### <a name="remarks"></a>Uwagi

`SetCommentText` Metoda jest wywoływana przez `CreateRowset`, statycznego szablonowana metody `IOpenRowsetImpl`.

Ta metoda deleguje swoją pracę, wywołując [validatecommandid —](../../data/oledb/crowsetimpl-validatecommandid.md) i [getcommandfromid —](../../data/oledb/crowsetimpl-getcommandfromid.md) za pomocą upcasted wskaźnika.

## <a name="getcolumninfo"></a> CRowsetImpl::GetColumnInfo

Pobiera informacje o kolumnach dla żądania danego klienta.

### <a name="syntax"></a>Składnia

```cpp
static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(T* pv,
   ULONG* pcCols);
```

#### <a name="parameters"></a>Parametry

*Wa*<br/>
[in] Wskaźnik do użytkownika `CRowsetImpl` klasy pochodnej.

*pcCols*<br/>
[in] Wskaźnik (dane wyjściowe) do liczby kolumn zwracana.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do statycznego `ATLCOLUMNINFO` struktury.

### <a name="remarks"></a>Uwagi

Ta metoda jest przesłonięciem zaawansowane.

Ta metoda jest wywoływana przez kilka klas implementację podstawową można pobrać informacji o kolumnie dla żądania danego klienta. Zazwyczaj ta metoda będzie wywoływana przez `IColumnsInfoImpl`. Jeśli zastąpisz tę metodę, należy umieścić wersji metody w swojej `CRowsetImpl`-klasy pochodnej. Ponieważ metoda może być umieszczane w klasie szablonowana, należy zmienić *pv* do odpowiedniego `CRowsetImpl`-klasy pochodnej.

W poniższym przykładzie pokazano `GetColumnInfo` użycia. W tym przykładzie `CMyRowset` jest `CRowsetImpl`-klasy pochodnej. Aby zastąpić `GetColumnInfo` dla wszystkich wystąpień tej klasy, umieść następującą metodę w `CMyRowset` definicję klasy:

[!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/cpp/crowsetimpl-getcolumninfo_1.h)]

## <a name="getcommandfromid"></a> CRowsetImpl::GetCommandFromID

Sprawdza, jeśli jednego lub obu tych parametrów zawiera wartości typu ciąg i kopiuje wartości ciągu do elementów członkowskich danych [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).

### <a name="syntax"></a>Składnia

```cpp
HRESULT CRowsetBaseImpl::GetCommandFromID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Parametry

*pTableID*<br/>
[in] Wskaźnik do `DBID` reprezentujący nazwę tabeli.

*pIndexID*<br/>
[in] Wskaźnik do `DBID` reprezentujący nazwę indeksu.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana za pomocą statycznych rozszerzające przez `CRowsetImpl` do wypełniania elementów członkowskich danych [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). Domyślnie ta metoda sprawdza Jeśli jednego lub obu tych parametrów zawiera wartości ciągu. Jeśli zawierają one wartości ciągu, ta metoda kopiuje wartości ciągu do składowych danych. Umieszczając metody z tą sygnaturą w Twojej `CRowsetImpl`-klasy, zostanie wywołana metoda zamiast implementację podstawową.

## <a name="validatecommandid"></a> CRowsetImpl::ValidateCommandID

Sprawdza, aby zobaczyć, czy w obu i / lub `DBID`s zawierają wartości ciągu, a jeśli tak, kopiuje je do swoich elementów członkowskich danych [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).

### <a name="syntax"></a>Składnia

```cpp
HRESULT CRowsetBaseImpl::ValidateCommandID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Parametry

*pTableID*<br/>
[in] Wskaźnik do `DBID` reprezentujący identyfikator tabeli.

*pIndexID*<br/>
[in] Wskaźnik do `DBID` reprezentujący identyfikator indeksu.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana za pomocą statycznych rozszerzające przez `CRowsetImpl` do wypełnienia jej składowych danych [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). Domyślnie ta metoda sprawdza, aby zobaczyć, czy w obu i / lub `DBID`s zawierają wartości ciągu, a jeśli tak, kopiuje je do swoich elementów członkowskich danych. Umieszczając metody z tą sygnaturą w Twojej `CRowsetImpl`-klasy, zostanie wywołana metoda zamiast implementację podstawową.

## <a name="rgrowdata"></a> CRowsetImpl::m_rgRowData

Domyślnie `CAtlArray` , templatizes na argument szablonu rekordu użytkownika `CRowsetImpl`.

### <a name="syntax"></a>Składnia

```cpp
ArrayType CRowsetBaseImpl::m_rgRowData;
```

### <a name="remarks"></a>Uwagi

*ArrayType —* jest parametrem szablonu `CRowsetImpl`.

## <a name="strcommandtext"></a> CRowsetImpl::m_strCommandText

Zawiera polecenia początkowego zestawu wierszy.

### <a name="syntax"></a>Składnia

```cpp
CComBSTR CRowsetBaseImpl::m_strCommandText;
```

## <a name="strindextext"></a> CRowsetImpl::m_strIndexText

Zawiera indeksu początkowego zestawu wierszy.

### <a name="syntax"></a>Składnia

```cpp
CComBSTR CRowsetBaseImpl::m_strIndexText;
```