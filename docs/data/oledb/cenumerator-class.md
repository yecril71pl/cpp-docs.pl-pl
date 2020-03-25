---
title: Klasa CEnumerator
ms.date: 11/04/2016
f1_keywords:
- CEnumerator
- CEnumerator::Find
- ATL::CEnumerator::Find
- ATL.CEnumerator.Find
- CEnumerator.Find
- GetMoniker
- CEnumerator.GetMoniker
- CEnumerator::GetMoniker
- ATL.CEnumerator.GetMoniker
- ATL::CEnumerator::GetMoniker
- ATL.CEnumerator.Open
- CEnumerator::Open
- ATL::CEnumerator::Open
- CEnumerator.Open
helpviewer_keywords:
- CEnumerator class
- Find method
- GetMoniker method
- Open method
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
ms.openlocfilehash: d0fa5f381dba4f67934007d59dbdaf4450bcfb60
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211799"
---
# <a name="cenumerator-class"></a>Klasa CEnumerator

Używa obiektu modułu wyliczającego OLE DB, który uwidacznia Interfejs [ISourcesRowset](/previous-versions/windows/desktop/ms715969(v=vs.85)) , aby zwracał zestaw wierszy, który zawiera opis wszystkich źródeł danych i modułów wyliczających.

## <a name="syntax"></a>Składnia

```cpp
class CEnumerator :
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="members"></a>Members

### <a name="methods"></a>Metody

|||
|-|-|
|[Wyszukiwanie](#find)|Wyszukuje dostępne dostawcy (źródła danych) szukające jednego z określoną nazwą.|
|[GetMoniker](#getmoniker)|Pobiera interfejs `IMoniker` dla bieżącego rekordu.|
|[Otwórz](#open)|Otwiera moduł wyliczający.|

## <a name="remarks"></a>Uwagi

`ISourcesRowset` dane można pobrać pośrednio z tej klasy.

## <a name="cenumeratorfind"></a><a name="find"></a>CEnumerator:: find

Wyszukuje określoną nazwę wśród dostępnych dostawców.

### <a name="syntax"></a>Składnia

```cpp
bool Find(TCHAR* szSearchName) throw();
```

#### <a name="parameters"></a>Parametry

*szSearchName*<br/>
podczas Nazwa do wyszukania.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli znaleziono nazwę. W przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta nazwa jest mapowana do `SOURCES_NAME`ego elementu członkowskiego interfejsu [ISourcesRowset](/previous-versions/windows/desktop/ms715969(v=vs.85)) .

## <a name="cenumeratorgetmoniker"></a><a name="getmoniker"></a>CEnumerator:: GetMoniker

Analizuje nazwę wyświetlaną, aby wyodrębnić składnik ciągu, który można przekonwertować na moniker.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetMoniker(LPMONIKER* ppMoniker) const throw();

HRESULT GetMoniker(LPMONIKER* ppMoniker,
   LPCTSTR lpszDisplayName) const throw();
```

#### <a name="parameters"></a>Parametry

*ppMoniker*<br/>
określoną Moniker przeanalizowany z nazwy wyświetlanej ([CEnumeratorAccessor:: m_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)) bieżącego wiersza.

*lpszDisplayName*<br/>
podczas Nazwa wyświetlana do przeanalizowania.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="cenumeratoropen"></a><a name="open"></a>CEnumerator:: Open

Tworzy powiązanie monikera dla modułu wyliczającego, jeśli został on określony, a następnie pobiera zestaw wierszy dla modułu wyliczającego przez wywołanie [ISourcesRowset:: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)).

### <a name="syntax"></a>Składnia

```cpp
HRESULT Open(LPMONIKER pMoniker) throw();

HRESULT Open(const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR) throw();

HRESULT Open(const CEnumerator& enumerator) throw();
```

#### <a name="parameters"></a>Parametry

*pMoniker*<br/>
podczas Wskaźnik do monikera modułu wyliczającego.

*pClsid*<br/>
podczas Wskaźnik do `CLSID` modułu wyliczającego.

*liczeni*<br/>
podczas Odwołanie do modułu wyliczającego.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="see-also"></a>Zobacz też

[DBVIEWER](../../overview/visual-cpp-samples.md)<br/>
[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)
