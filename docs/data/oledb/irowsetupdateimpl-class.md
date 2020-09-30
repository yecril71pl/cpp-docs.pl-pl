---
title: IRowsetUpdateImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
- IRowsetUpdateImpl::SetData
- IRowsetUpdateImpl.SetData
- ATL::IRowsetUpdateImpl::SetData
- ATL.IRowsetUpdateImpl.SetData
- ATL.IRowsetUpdateImpl.GetOriginalData
- IRowsetUpdateImpl.GetOriginalData
- ATL::IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetPendingRows
- GetPendingRows
- IRowsetUpdateImpl.GetPendingRows
- ATL::IRowsetUpdateImpl::GetPendingRows
- ATL.IRowsetUpdateImpl.GetPendingRows
- ATL.IRowsetUpdateImpl.GetRowStatus
- IRowsetUpdateImpl::GetRowStatus
- IRowsetUpdateImpl.GetRowStatus
- ATL::IRowsetUpdateImpl::GetRowStatus
- ATL.IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Update
- IRowsetUpdateImpl::Update
- IRowsetUpdateImpl.Update
- ATL.IRowsetUpdateImpl.Update
- IRowsetUpdateImpl::IsUpdateAllowed
- IRowsetUpdateImpl.IsUpdateAllowed
- IsUpdateAllowed
- IRowsetUpdateImpl.m_mapCachedData
- IRowsetUpdateImpl::m_mapCachedData
- m_mapCachedData
helpviewer_keywords:
- providers, updatable
- IRowsetUpdateImpl class
- updatable providers, deferred update
- SetData method
- GetOriginalData method
- GetPendingRows method
- GetRowStatus method
- Undo method
- Update method
- IsUpdateAllowed method
- m_mapCachedData
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
ms.openlocfilehash: 88ee9257655c96195339ded79f2dd4d3b7c7caf5
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509782"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl — Klasa

Implementacja szablonów OLE DB interfejsu [IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85)) .

## <a name="syntax"></a>Składnia

```cpp
template <
   class T,
   class Storage,
   class UpdateArray = CAtlArray<Storage>,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>
>

class IRowsetUpdateImpl : public IRowsetChangeImpl<
   T,
   Storage,
   IRowsetUpdate,
   RowClass,
   MapClass>
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa pochodna `IRowsetUpdateImpl` .

*Storage*<br/>
Rekord użytkownika.

*UpdateArray*<br/>
Tablica zawierająca dane buforowane do zaktualizowania zestawu wierszy.

*RowClass*<br/>
Jednostka magazynowa dla `HROW` .

*MapClass*<br/>
Jednostka magazynowa dla wszystkich dojść wiersza przechowywanych przez dostawcę.

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Elementy członkowskie

### <a name="interface-methods-used-with-irowsetchange"></a>Metody interfejsu (używane z IRowsetChange)

| Nazwa | Opis |
|-|-|
|[Operację](#setdata)|Ustawia wartości danych w co najmniej jednej kolumnie.|

### <a name="interface-methods-used-with-irowsetupdate"></a>Metody interfejsu (używane z IRowsetUpdate)

| Nazwa | Opis |
|-|-|
|[GetOriginalData](#getoriginaldata)|Pobiera dane, które zostały ostatnio przesłane do lub uzyskane ze źródła danych, ignorując oczekujące zmiany.|
|[GetPendingRows](#getpendingrows)|Zwraca listę wierszy z oczekującymi zmianami.|
|[GetRowStatus](#getrowstatus)|Zwraca stan określonych wierszy.|
|[Cofnij](#undo)|Cofa wszystkie zmiany w wierszu od momentu ostatniego pobrania lub aktualizacji.|
|[Aktualizowanie](#update)|Przesyła wszelkie zmiany wprowadzone do wiersza od momentu ostatniego pobrania lub aktualizacji.|

### <a name="implementation-methods-callback"></a>Metody implementacji (wywołanie zwrotne)

| Nazwa | Opis |
|-|-|
|[IsUpdateAllowed](#isupdateallowed)|Służy do sprawdzania zabezpieczeń, integralności i tak dalej przed zezwoleniem na aktualizacje.|

### <a name="data-members"></a>Elementy członkowskie danych

| Nazwa | Opis |
|-|-|
|[m_mapCachedData](#mapcacheddata)|Zawiera oryginalne dane dla operacji odroczonej.|

## <a name="remarks"></a>Uwagi

Należy najpierw przeczytać i zrozumieć dokumentację programu [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)), ponieważ wszystkie opisane tu informacje dotyczą również tego programu. Należy również zapoznać się z rozdziałem 6 *odwołania OLE DB programisty* dotyczącego ustawiania danych.

`IRowsetUpdateImpl` implementuje interfejs OLE DB `IRowsetUpdate` , dzięki czemu klienci mogą opóźnić przekazywanie zmian wprowadzonych w `IRowsetChange` źródle danych i cofać zmiany przed przekazaniem.

> [!IMPORTANT]
> PRZED podjęciem próby wdrożenia dostawcy zdecydowanie zalecamy zapoznanie się z poniższą dokumentacją:

- [Tworzenie aktualizowalnego dostawcy](../../data/oledb/creating-an-updatable-provider.md)

- Rozdział 6 *odwołania programisty OLE DB*

- Zobacz również, jak `RUpdateRowset` Klasa jest używana w przykładzie [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)

## <a name="irowsetupdateimplsetdata"></a><a name="setdata"></a> IRowsetUpdateImpl:: SetData

Ustawia wartości danych w co najmniej jednej kolumnie.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetChange:: SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="remarks"></a>Uwagi

Ta metoda przesłania metodę [IRowsetChangeImpl:: SetData](./irowsetchangeimpl-class.md#setdata) , ale zawiera buforowanie oryginalnych danych w celu zezwolenia na natychmiastowe lub odroczone przetwarzanie operacji.

## <a name="irowsetupdateimplgetoriginaldata"></a><a name="getoriginaldata"></a> IRowsetUpdateImpl:: GetOriginalData

Pobiera dane, które zostały ostatnio przesłane do lub uzyskane ze źródła danych, ignorując oczekujące zmiany.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (GetOriginalData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pData);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetUpdate:: GetOriginalData](/previous-versions/windows/desktop/ms709947(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="irowsetupdateimplgetpendingrows"></a><a name="getpendingrows"></a> IRowsetUpdateImpl:: GetPendingRows

Zwraca listę wierszy z oczekującymi zmianami.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (GetPendingRows )(HCHAPTER /* hReserved */,
   DBPENDINGSTATUS dwRowStatus,
   DBCOUNTITEM* pcPendingRows,
   HROW** prgPendingRows,
   DBPENDINGSTATUS** prgPendingStatus);
```

#### <a name="parameters"></a>Parametry

*hReserved*<br/>
podczas Odpowiada parametrowi *hChapter* w [IRowsetUpdate:: GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)).

W przypadku innych parametrów, zobacz [IRowsetUpdate:: GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [IRowsetUpdate:: GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="irowsetupdateimplgetrowstatus"></a><a name="getrowstatus"></a> IRowsetUpdateImpl:: GetRowStatus

Zwraca stan określonych wierszy.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (GetRowStatus )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBPENDINGSTATUS rgPendingStatus[]);
```

#### <a name="parameters"></a>Parametry

*hReserved*<br/>
podczas Odpowiada parametrowi *hChapter* w [IRowsetUpdate:: GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)).

W przypadku innych parametrów, zobacz [IRowsetUpdate:: GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="irowsetupdateimplundo"></a><a name="undo"></a> IRowsetUpdateImpl:: Undo

Cofa wszystkie zmiany w wierszu od momentu ostatniego pobrania lub aktualizacji.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (Undo )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[ ],
   DBCOUNTITEM* pcRowsUndone,
   HROW** prgRowsUndone,
   DBROWSTATUS** prgRowStatus);
```

#### <a name="parameters"></a>Parametry

*hReserved*<br/>
podczas Odpowiada parametrowi *hChapter* w [IRowsetUpdate:: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*pcRowsUndone*<br/>
określoną Odpowiada parametrowi *pcRows* w [IRowsetUpdate:: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*prgRowsUndone*<br/>
podczas Odpowiada parametrowi *prgRows* w [IRowsetUpdate:: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

Aby poznać inne parametry, zobacz [IRowsetUpdate:: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="irowsetupdateimplupdate"></a><a name="update"></a> IRowsetUpdateImpl:: Update

Przesyła wszelkie zmiany wprowadzone do wiersza od momentu ostatniego pobrania lub aktualizacji.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (Update )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBCOUNTITEM* pcRows,
   HROW** prgRows,
   DBROWSTATUS** prgRowStatus);
```

#### <a name="parameters"></a>Parametry

*hReserved*<br/>
podczas Odpowiada parametrowi *hChapter* w [IRowsetUpdate:: Update](/previous-versions/windows/desktop/ms719709(v=vs.85)).

Aby poznać inne parametry, zobacz [IRowsetUpdate:: Update](/previous-versions/windows/desktop/ms719709(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="remarks"></a>Uwagi

Zmiany są przesyłane przez wywołanie [IRowsetChangeImpl:: FlushData](./irowsetchangeimpl-class.md#flushdata). Aby zmiany zaczęły obowiązywać, konsument musi wywołać [CRowset:: Update](./crowset-class.md#update) . Ustaw *prgRowStatus* na odpowiednią wartość, zgodnie z opisem w temacie [Stany wierszy](/previous-versions/windows/desktop/ms722752(v=vs.85)) w *Kompendium OLE DB programisty*.

## <a name="irowsetupdateimplisupdateallowed"></a><a name="isupdateallowed"></a> IRowsetUpdateImpl:: IsUpdateAllowed

Zastąp tę metodę, aby sprawdzić zabezpieczenia, integralność i tak dalej przed aktualizacjami.

### <a name="syntax"></a>Składnia

```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,
   HROW /* [in] */ /* hRowUpdate */,
   DBROWSTATUS* /* [out] */ /* pRowStatus */);
```

#### <a name="parameters"></a>Parametry

*Stany*<br/>
podczas Stan oczekujących operacji na wierszach.

*hRowUpdate*<br/>
podczas Dojście do wierszy, które użytkownik chce zaktualizować.

*pRowStatus*<br/>
określoną Stan zwrócony użytkownikowi.

### <a name="remarks"></a>Uwagi

Jeśli ustalisz, że aktualizacja powinna być dozwolona, zwraca S_OK; w przeciwnym razie zwraca E_FAIL. Jeśli zezwolisz na aktualizację, musisz także ustawić `DBROWSTATUS` w [IRowsetUpdateImpl:: Update](#update) do odpowiedniego [stanu wiersza](/previous-versions/windows/desktop/ms722752(v=vs.85)).

## <a name="irowsetupdateimplm_mapcacheddata"></a><a name="mapcacheddata"></a> IRowsetUpdateImpl:: m_mapCachedData

Mapa zawierająca oryginalne dane dla operacji odroczonej.

### <a name="syntax"></a>Składnia

```cpp
CAtlMap<
   HROW hRow,
   Storage* pData
>
m_mapCachedData;
```

#### <a name="parameters"></a>Parametry

*hRow*<br/>
Dojście do wierszy danych.

*pData*<br/>
Wskaźnik do danych, które mają być buforowane. Dane są typu *Storage* (Klasa rekordu użytkownika). Zobacz argument szablonu *magazynu* w [klasie IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md).

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Tworzenie aktualizowalnego dostawcy](../../data/oledb/creating-an-updatable-provider.md)
