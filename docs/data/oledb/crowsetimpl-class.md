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
ms.openlocfilehash: 35a80503597b7e59ec10618b9c8e18e0e69f018e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221513"
---
# <a name="crowsetimpl-class"></a>CRowsetImpl — Klasa

Zapewnia standardową implementację zestawu wierszy OLE DB, bez konieczności dziedziczenia wielu interfejsów implementacji.

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
Klasa użytkownika, która dziedziczy z `CRowsetImpl` .

*Magazyn*<br/>
Klasa rekordu użytkownika.

*CreatorClass*<br/>
Klasa, która zawiera właściwości zestawu wierszy; zwykle polecenie.

*ArrayType*<br/>
Klasa, która będzie pełnić funkcję magazynu dla danych zestawu wierszy. Ten parametr ma wartość domyślną `CAtlArray` , ale może być dowolną klasą, która obsługuje wymagane funkcje.

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[NameFromDBID](#namefromdbid)|Wyodrębnia ciąg z `DBID` i kopiuje go do nieprzesłanego elementu *BSTR* .|
|[SetCommandText](#setcommandtext)|Sprawdza poprawność i przechowuje `DBID` w dwóch ciągach ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).|

### <a name="overridable-methods"></a>Metody, które zostały zastąpione

|||
|-|-|
|[GetColumnInfo](#getcolumninfo)|Pobiera informacje o kolumnie dla określonego żądania klienta.|
|[GetCommandFromID](#getcommandfromid)|Sprawdza, czy jeden lub oba parametry zawierają wartości ciągów, a jeśli tak, kopiuje wartości ciągu do elementów członkowskich danych [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|
|[ValidateCommandID](#validatecommandid)|Sprawdza, czy oba lub oba `DBID` elementy s zawierają wartości ciągów, a jeśli tak, kopiuje je do swoich elementów członkowskich danych [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_rgRowData](#rgrowdata)|Domyślnie `CAtlArray` templatizes w argumencie szablonu rekordu użytkownika do `CRowsetImpl` . Inna Klasa typu tablicy może być używana przez zmianę `ArrayType` argumentu szablonu na `CRowsetImpl` .|
|[m_strCommandText](#strcommandtext)|Zawiera początkowe polecenie zestawu wierszy.|
|[m_strIndexText](#strindextext)|Zawiera początkowy indeks zestawu wierszy.|

## <a name="remarks"></a>Uwagi

`CRowsetImpl`zawiera zastąpienia w formie statycznych przerzutów. Metody kontrolują sposób, w jaki dany zestaw wierszy będzie sprawdzać poprawność tekstu polecenia. Można utworzyć własną `CRowsetImpl` klasę stylu, wprowadzając wiele dziedziczonych interfejsów implementacji. Jedyną metodą, dla której należy podać implementację, jest `Execute` . W zależności od typu tworzonego zestawu wierszy metody twórcy będą oczekiwać różnej sygnatury dla `Execute` . Na przykład jeśli używasz `CRowsetImpl` klasy pochodnej do implementowania zestawu wierszy schematu, `Execute` Metoda będzie miała następujący podpis:

`HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`

Jeśli tworzysz `CRowsetImpl` klasę pochodną, aby zaimplementować zestaw wierszy polecenia lub sesji, `Execute` Metoda będzie miała następujący podpis:

`HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`

Aby zaimplementować dowolne `CRowsetImpl` `Execute` metody pochodne, należy wypełnić wewnętrzne bufory danych ([m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)).

## <a name="crowsetimplnamefromdbid"></a><a name="namefromdbid"></a>CRowsetImpl:: NameFromDBID

Wyodrębnia ciąg z `DBID` i kopiuje go do nieprzesłanego elementu *BSTR* .

### <a name="syntax"></a>Składnia

```cpp
HRESULT CRowsetBaseImpl::NameFromDBID(DBID* pDBID,
   CComBSTR& bstr,
   bool bIndex);
```

#### <a name="parameters"></a>Parametry

*pDBID*<br/>
podczas Wskaźnik do elementu, `DBID` z którego ma zostać wyodrębniony ciąg.

*bstr*<br/>
podczas Odwołanie [CComBSTR](../../atl/reference/ccombstr-class.md) do umieszczenia kopii `DBID` ciągu.

*bIndex*<br/>
[w] **`true`** Jeśli indeks `DBID` ; **`false`** jest tabelą `DBID` .

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT. W zależności od tego `DBID` , czy jest to tabela czy indeks (oznaczone przez *bIndex*), metoda zwróci wartość DB_E_NOINDEX lub DB_E_NOTABLE.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez `CRowsetImpl` implementacje [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) i [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md).

## <a name="crowsetimplsetcommandtext"></a><a name="setcommandtext"></a>CRowsetImpl:: SetCommandText

Sprawdza poprawność i przechowuje `DBID` w dwóch ciągach ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).

### <a name="syntax"></a>Składnia

```cpp
HRESULT CRowsetBaseImpl::SetCommandText(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Parametry

*pTableID*<br/>
podczas Wskaźnik do `DBID` reprezentujący identyfikator tabeli.

*pIndexID*<br/>
podczas Wskaźnik do `DBID` reprezentujący identyfikator indeksu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

`SetCommentText`Metoda jest wywoływana przez `CreateRowset` , statyczną metodę szablonowana `IOpenRowsetImpl` .

Ta metoda deleguje swoją służbę, wywołując [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) i [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md) za pomocą wskaźnika z przerzutem.

## <a name="crowsetimplgetcolumninfo"></a><a name="getcolumninfo"></a>CRowsetImpl:: GetColumnInfo

Pobiera informacje o kolumnie dla określonego żądania klienta.

### <a name="syntax"></a>Składnia

```cpp
static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(T* pv,
   ULONG* pcCols);
```

#### <a name="parameters"></a>Parametry

*wa*<br/>
podczas Wskaźnik do `CRowsetImpl` klasy pochodnej użytkownika.

*pcCols*<br/>
podczas Wskaźnik (wynikowy) do liczby zwracanych kolumn.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do struktury statycznej `ATLCOLUMNINFO` .

### <a name="remarks"></a>Uwagi

Ta metoda jest zaawansowaną zastępowaniem.

Ta metoda jest wywoływana przez kilka podstawowych klas implementacji, aby pobrać informacje o kolumnie dla określonego żądania klienta. Zwykle ta metoda jest wywoływana przez `IColumnsInfoImpl` . W przypadku zastąpienia tej metody należy umieścić wersję metody w `CRowsetImpl` klasie pochodnej. Ponieważ metoda może być umieszczona w klasie innej niż szablonowana, należy zmienić wartość *PV* na odpowiednią `CRowsetImpl` klasę pochodną.

Poniższy przykład ilustruje `GetColumnInfo` użycie. W tym przykładzie `CMyRowset` jest `CRowsetImpl` klasą pochodną. Aby przesłonić `GetColumnInfo` wszystkie wystąpienia tej klasy, należy umieścić następującą metodę w `CMyRowset` definicji klasy:

[!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/cpp/crowsetimpl-getcolumninfo_1.h)]

## <a name="crowsetimplgetcommandfromid"></a><a name="getcommandfromid"></a>CRowsetImpl:: GetCommandFromID

Sprawdza, czy jeden lub oba parametry zawierają wartości ciągów, a jeśli tak, kopiuje wartości ciągu do elementów członkowskich danych [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).

### <a name="syntax"></a>Składnia

```cpp
HRESULT CRowsetBaseImpl::GetCommandFromID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Parametry

*pTableID*<br/>
podczas Wskaźnik do `DBID` reprezentujący identyfikator tabeli.

*pIndexID*<br/>
podczas Wskaźnik do `DBID` reprezentujący identyfikator indeksu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana za pomocą statycznego przerzutowania przez, `CRowsetImpl` Aby wypełnić elementy członkowskie danych [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). Domyślnie ta metoda sprawdza, czy oba parametry zawierają wartości ciągu. Jeśli zawierają wartości ciągu, ta metoda kopiuje wartości ciągu do elementów członkowskich danych. Umieszczając metodę z podpisem w `CRowsetImpl` klasie pochodnej, Metoda zostanie wywołana zamiast implementacji podstawowej.

## <a name="crowsetimplvalidatecommandid"></a><a name="validatecommandid"></a>CRowsetImpl:: ValidateCommandID

Sprawdza, czy oba lub oba `DBID` elementy s zawierają wartości ciągów, a jeśli tak, kopiuje je do swoich elementów członkowskich danych [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).

### <a name="syntax"></a>Składnia

```cpp
HRESULT CRowsetBaseImpl::ValidateCommandID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Parametry

*pTableID*<br/>
podczas Wskaźnik do `DBID` reprezentujący identyfikator tabeli.

*pIndexID*<br/>
podczas Wskaźnik do `DBID` reprezentujący identyfikator indeksu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana za pomocą statycznego przerzutowania przez, `CRowsetImpl` Aby wypełnić jego składowe danych [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). Domyślnie ta metoda sprawdza, czy oba lub oba `DBID` elementy s zawierają wartości ciągów, a jeśli tak, kopiuje je do elementów członkowskich danych. Umieszczając metodę z podpisem w `CRowsetImpl` klasie pochodnej, Metoda zostanie wywołana zamiast implementacji podstawowej.

## <a name="crowsetimplm_rgrowdata"></a><a name="rgrowdata"></a>CRowsetImpl:: m_rgRowData

Domyślnie `CAtlArray` templatizes w argumencie szablonu rekordu użytkownika do `CRowsetImpl` .

### <a name="syntax"></a>Składnia

```cpp
ArrayType CRowsetBaseImpl::m_rgRowData;
```

### <a name="remarks"></a>Uwagi

*ArrayType* jest parametrem szablonu do `CRowsetImpl` .

## <a name="crowsetimplm_strcommandtext"></a><a name="strcommandtext"></a>CRowsetImpl:: m_strCommandText

Zawiera początkowe polecenie zestawu wierszy.

### <a name="syntax"></a>Składnia

```cpp
CComBSTR CRowsetBaseImpl::m_strCommandText;
```

## <a name="crowsetimplm_strindextext"></a><a name="strindextext"></a>CRowsetImpl:: m_strIndexText

Zawiera początkowy indeks zestawu wierszy.

### <a name="syntax"></a>Składnia

```cpp
CComBSTR CRowsetBaseImpl::m_strIndexText;
```
