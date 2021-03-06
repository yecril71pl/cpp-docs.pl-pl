---
title: IRowsetImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- IRowsetImpl
- IRowsetImpl::AddRefRows
- IRowsetImpl.AddRefRows
- ATL::IRowsetImpl::AddRefRows
- ATL.IRowsetImpl.AddRefRows
- IRowsetImpl.CreateRow
- ATL.IRowsetImpl.CreateRow
- ATL::IRowsetImpl::CreateRow
- CreateRow
- IRowsetImpl::CreateRow
- ATL.IRowsetImpl.GetData
- ATL::IRowsetImpl::GetData
- IRowsetImpl::GetData
- IRowsetImpl.GetData
- GetDBStatus
- IRowsetImpl.GetDBStatus
- IRowsetImpl::GetDBStatus
- GetNextRows
- ATL.IRowsetImpl.GetNextRows
- ATL::IRowsetImpl::GetNextRows
- IRowsetImpl::GetNextRows
- IRowsetImpl.GetNextRows
- IRowsetImpl.IRowsetImpl
- ATL::IRowsetImpl::IRowsetImpl
- ATL.IRowsetImpl.IRowsetImpl
- IRowsetImpl::IRowsetImpl
- ATL::IRowsetImpl::RefRows
- ATL.IRowsetImpl.RefRows
- IRowsetImpl.RefRows
- RefRows
- IRowsetImpl::RefRows
- ATL.IRowsetImpl.ReleaseRows
- IRowsetImpl::ReleaseRows
- ATL::IRowsetImpl::ReleaseRows
- IRowsetImpl.ReleaseRows
- ATL.IRowsetImpl.RestartPosition
- IRowsetImpl::RestartPosition
- RestartPosition
- ATL::IRowsetImpl::RestartPosition
- IRowsetImpl.RestartPosition
- IRowsetImpl.SetDBStatus
- IRowsetImpl::SetDBStatus
- SetDBStatus
- ATL.IRowsetImpl.m_bCanFetchBack
- ATL::IRowsetImpl::m_bCanFetchBack
- IRowsetImpl.m_bCanFetchBack
- IRowsetImpl::m_bCanFetchBack
- m_bCanFetchBack
- IRowsetImpl::m_bCanScrollBack
- ATL::IRowsetImpl::m_bCanScrollBack
- IRowsetImpl.m_bCanScrollBack
- ATL.IRowsetImpl.m_bCanScrollBack
- m_bCanScrollBack
- ATL.IRowsetImpl.m_bReset
- IRowsetImpl.m_bReset
- m_bReset
- IRowsetImpl::m_bReset
- ATL::IRowsetImpl::m_bReset
- IRowsetImpl::m_iRowset
- IRowsetImpl.m_iRowset
- ATL::IRowsetImpl::m_iRowset
- ATL.IRowsetImpl.m_iRowset
- m_iRowset
- IRowsetImpl::m_rgRowHandles
- IRowsetImpl.m_rgRowHandles
- m_rgRowHandles
- ATL::IRowsetImpl::m_rgRowHandles
- ATL.IRowsetImpl.m_rgRowHandles
helpviewer_keywords:
- IRowsetImpl class
- AddRefRows method
- CreateRow method
- GetData method [OLE DB]
- GetDBStatus method
- GetNextRows method
- IRowsetImpl constructor
- RefRows method
- ReleaseRows method
- RestartPosition method
- SetDBStatus method
- m_bCanFetchBack
- m_bCanScrollBack
- m_bReset
- m_iRowset
- m_rgRowHandles
ms.assetid: 6a9189af-7556-45b1-adcb-9d62bb36704c
ms.openlocfilehash: 27a07d10256147d3c3ed383744ba1ee5fdfd06a1
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504079"
---
# <a name="irowsetimpl-class"></a>IRowsetImpl — Klasa

Zapewnia implementację `IRowset` interfejsu.

## <a name="syntax"></a>Składnia

```cpp
template <
   class T,
   class RowsetInterface,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <
      RowClass::KeyType,
      RowClass*>>
class ATL_NO_VTABLE IRowsetImpl : public RowsetInterface
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która pochodzi od `IRowsetImpl` .

*RowsetInterface*<br/>
Klasa pochodna `IRowsetImpl` .

*RowClass*<br/>
Jednostka magazynowa dla `HROW` .

*MapClass*<br/>
Jednostka magazynowa dla wszystkich dojść do wierszy przechowywanych przez dostawcę.

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

| Nazwa | Opis |
|-|-|
|[AddRefRows](#addrefrows)|Dodaje liczbę odwołań do istniejącego dojścia do wiersza.|
|[CreateRow](#createrow)|Wywoływane przez [GetNextRows](#getnextrows) w celu przydzielenia nowego elementu `HROW` . Nie wywołano bezpośrednio przez użytkownika.|
|[GetData](#getdata)|Pobiera dane z kopii wiersza zestawu wierszy.|
|[GetDBStatus](#getdbstatus)|Zwraca stan dla określonego pola.|
|[GetNextRows](#getnextrows)|Pobiera wiersze sekwencyjnie, zapamiętając poprzednią pozycję.|
|[IRowsetImpl](#irowsetimpl)|Konstruktor. Nie wywołano bezpośrednio przez użytkownika.|
|[RefRows](#refrows)|Wywoływane przez [AddRefRows](#addrefrows) i [ReleaseRows](#releaserows). Nie wywołano bezpośrednio przez użytkownika.|
|[ReleaseRows](#releaserows)|Zwalnia wiersze.|
|[Operacja RestartPosition wykonywana](#restartposition)|Zmienia położenie następnego pobrania do jego pozycji początkowej; oznacza to, że jego położenie podczas pierwszego utworzenia zestawu wierszy.|
|[SetDBStatus](#setdbstatus)|Ustawia flagi stanu dla określonego pola.|

### <a name="data-members"></a>Elementy członkowskie danych

| Nazwa | Opis |
|-|-|
|[m_bCanFetchBack](#bcanfetchback)|Wskazuje, czy dostawca obsługuje pobieranie wsteczne.|
|[m_bCanScrollBack](#bcanscrollback)|Wskazuje, czy dostawca może przewijać kursor wstecz.|
|[m_bReset](#breset)|Wskazuje, czy dostawca resetuje położenie kursora. Ma to specjalne znaczenie podczas przewijania do tyłu lub pobierania z tyłu w [GetNextRows](#getnextrows).|
|[m_iRowset](#irowset)|Indeks zestawu wierszy reprezentujący kursor.|
|[m_rgRowHandles](#rgrowhandles)|Lista dojść do wierszy.|

## <a name="remarks"></a>Uwagi

[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85)) jest podstawowym interfejsem zestawu wierszy.

## <a name="irowsetimpladdrefrows"></a><a name="addrefrows"></a> IRowsetImpl:: AddRefRows

Dodaje liczbę odwołań do istniejącego dojścia do wiersza.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(AddRefRows )(DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowset:: AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="irowsetimplcreaterow"></a><a name="createrow"></a> IRowsetImpl:: CreateRow

Metoda pomocnika wywołana przez [GetNextRows](#getnextrows) do przydzielenia nowego elementu `HROW` .

### <a name="syntax"></a>Składnia

```cpp
HRESULT CreateRow(DBROWOFFSET lRowsOffset,
   DBCOUNTITEM& cRowsObtained,
   HROW* rgRows);
```

#### <a name="parameters"></a>Parametry

*lRowsOffset*<br/>
Położenie kursora tworzonego wiersza.

*cRowsObtained*<br/>
Odwołanie zostało przesłane z powrotem do użytkownika wskazującego liczbę utworzonych wierszy.

*rgRows*<br/>
Tablica `HROW` s zwrócona do obiektu wywołującego z nowo utworzonym wierszem.

### <a name="remarks"></a>Uwagi

Jeśli wiersz istnieje, ta metoda wywołuje [AddRefRows](#addrefrows) i zwraca. W przeciwnym razie przydziela nowe wystąpienie zmiennej szablonu RowClass i dodaje ją do [m_rgRowHandles](#rgrowhandles).

## <a name="irowsetimplgetdata"></a><a name="getdata"></a> IRowsetImpl:: GetData

Pobiera dane z kopii wiersza zestawu wierszy.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pDstData);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowset:: GetData](/previous-versions/windows/desktop/ms716988(v=vs.85)) w *dokumentacji programisty OLE DB*.

Niektóre parametry odpowiadają parametrom *referencyjnym programisty OLE DB* różnymi nazwami, które są opisane w `IRowset::GetData` :

|OLE DB parametry szablonu|*OLE DB parametry odwołania programisty*|
|--------------------------------|------------------------------------------------|
|*pDstData*|*pData*|

### <a name="remarks"></a>Uwagi

Obsługuje również konwersję danych przy użyciu biblioteki DLL konwersji danych OLE DB.

## <a name="irowsetimplgetdbstatus"></a><a name="getdbstatus"></a> IRowsetImpl:: GetDBStatus

Zwraca flagi stanu DBSTATUS dla określonego pola.

### <a name="syntax"></a>Składnia

```cpp
virtual DBSTATUS GetDBStatus(RowClass* currentRow,
   ATLCOLUMNINFO* columnNames);
```

#### <a name="parameters"></a>Parametry

*currentRow*<br/>
podczas Bieżący wiersz.

*columnNames*<br/>
podczas Kolumna, dla której jest żądany stan.

### <a name="return-value"></a>Wartość zwracana

Flagi [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) dla kolumny.

## <a name="irowsetimplgetnextrows"></a><a name="getnextrows"></a> IRowsetImpl:: GetNextRows

Pobiera wiersze sekwencyjnie, zapamiętając poprzednią pozycję.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetNextRows )(HCHAPTER hReserved,
   DBROWOFFSET lRowsOffset,
   DBROWCOUNT cRows,
   DBCOUNTITEM* pcRowsObtained,
   HROW** prghRows);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowset:: GetNextRows](/previous-versions/windows/desktop/ms709827(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="irowsetimplirowsetimpl"></a><a name="irowsetimpl"></a> IRowsetImpl:: IRowsetImpl

Konstruktor.

### <a name="syntax"></a>Składnia

```cpp
IRowsetImpl();
```

### <a name="remarks"></a>Uwagi

Zazwyczaj nie trzeba wywoływać tej metody bezpośrednio.

## <a name="irowsetimplrefrows"></a><a name="refrows"></a> IRowsetImpl:: RefRows

Wywoływane przez [AddRefRows](#addrefrows) i [ReleaseRows](#releaserows) w celu zwiększenia lub zwolnienia liczby odwołań do istniejącego uchwytu wiersza.

### <a name="syntax"></a>Składnia

```cpp
HRESULT RefRows(DBCOUNTITEM cRows,
   const HROWrghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[],
   BOOL bAdd);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowset:: AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="irowsetimplreleaserows"></a><a name="releaserows"></a> IRowsetImpl:: ReleaseRows

Zwalnia wiersze.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(ReleaseRows )(DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWOPTIONS rgRowOptions[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowset:: ReleaseRows](/previous-versions/windows/desktop/ms719771(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="irowsetimplrestartposition"></a><a name="restartposition"></a> IRowsetImpl:: operacja RestartPosition wykonywana

Zmienia położenie następnego pobrania do jego pozycji początkowej; oznacza to, że jego położenie podczas pierwszego utworzenia zestawu wierszy.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(RestartPosition )(HCHAPTER /* hReserved */);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowset:: operacja RestartPosition wykonywana](/previous-versions/windows/desktop/ms712877(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="remarks"></a>Uwagi

Pozycja zestawu wierszy jest niezdefiniowana, dopóki nie `GetNextRow` zostanie wywołana. Można przenieść do tyłu w rowet przez wywołanie `RestartPosition` , a następnie pobranie lub przewinięcie do tyłu.

## <a name="irowsetimplsetdbstatus"></a><a name="setdbstatus"></a> IRowsetImpl:: SetDBStatus

Ustawia flagi stanu DBSTATUS dla określonego pola.

### <a name="syntax"></a>Składnia

```cpp
virtual HRESULT SetDBStatus(DBSTATUS* statusFlags,
   RowClass* currentRow,
   ATLCOLUMNINFO* columnInfo);
```

#### <a name="parameters"></a>Parametry

*statusFlags*<br/>
Flagi [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) do ustawienia dla kolumny.

*currentRow*<br/>
Bieżący wiersz.

*columnInfo*<br/>
Kolumna, dla której jest ustawiany stan.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Dostawca zastępuje tę funkcję, aby zapewnić specjalne przetwarzanie DBSTATUS_S_ISNULL i DBSTATUS_S_DEFAULT.

## <a name="irowsetimplm_bcanfetchback"></a><a name="bcanfetchback"></a> IRowsetImpl:: m_bCanFetchBack

Wskazuje, czy dostawca obsługuje pobieranie wsteczne.

### <a name="syntax"></a>Składnia

```cpp
unsigned m_bCanFetchBack:1;
```

### <a name="remarks"></a>Uwagi

Połączono z `DBPROP_CANFETCHBACKWARDS` właściwością w `DBPROPSET_ROWSET` grupie. Dostawca musi obsługiwać `DBPROP_CANFETCHBACKWARDS` `m_bCanFetchBackwards` do **`true`** .

## <a name="irowsetimplm_bcanscrollback"></a><a name="bcanscrollback"></a> IRowsetImpl:: m_bCanScrollBack

Wskazuje, czy dostawca może przewijać kursor wstecz.

### <a name="syntax"></a>Składnia

```cpp
unsigned  m_bCanScrollBack:1;
```

### <a name="remarks"></a>Uwagi

Połączono z `DBPROP_CANSCROLLBACKWARDS` właściwością w `DBPROPSET_ROWSET` grupie. Dostawca musi obsługiwać `DBPROP_CANSCROLLBACKWARDS` `m_bCanFetchBackwards` do **`true`** .

## <a name="irowsetimplm_breset"></a><a name="breset"></a> IRowsetImpl:: m_bReset

Flaga bitowa użyta do określenia, czy pozycja kursora jest zdefiniowana w zestawie wierszy.

### <a name="syntax"></a>Składnia

```cpp
unsigned m_bReset:1;
```

### <a name="remarks"></a>Uwagi

Jeśli odbiorca wywołuje [GetNextRows](#getnextrows) z wartością ujemną `lOffset` lub *łapki* i `m_bReset` ma wartość true, `GetNextRows` przenosi się na koniec zestawu wierszy. Jeśli `m_bReset` ma wartość false, odbiorca otrzymuje kod błędu w zgodności ze specyfikacją OLE DB. `m_bReset`Flaga jest ustawiana na **`true`** czas pierwszego utworzenia zestawu wierszy i gdy odbiorca wywołuje [IRowsetImpl:: operacja RestartPosition wykonywana](#restartposition). Jest on ustawiany **`false`** podczas wywoływania `GetNextRows` .

## <a name="irowsetimplm_irowset"></a><a name="irowset"></a> IRowsetImpl:: m_iRowset

Indeks zestawu wierszy reprezentujący kursor.

### <a name="syntax"></a>Składnia

```cpp
DBROWOFFSET m_iRowset;
```

## <a name="irowsetimplm_rgrowhandles"></a><a name="rgrowhandles"></a> IRowsetImpl:: m_rgRowHandles

Mapa uchwytów wiersza aktualnie zawartych przez dostawcę w odpowiedzi na `GetNextRows` .

### <a name="syntax"></a>Składnia

```cpp
MapClass m_rgRowHandles;
```

### <a name="remarks"></a>Uwagi

Uchwyty wierszy są usuwane przez wywołanie `ReleaseRows` . Zobacz [IRowsetImpl Omówienie](../../data/oledb/irowsetimpl-class.md) definicji *MapClass*.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Klasa CSimpleRow](../../data/oledb/csimplerow-class.md)
