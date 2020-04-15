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
ms.openlocfilehash: 6347a42b9065239f768c6b50c430946393358df1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370746"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl — Klasa

Implementacja szablonów ole db interfejsu [IRowsetUpdate.](/previous-versions/windows/desktop/ms714401(v=vs.85))

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
Klasa pochodząca `IRowsetUpdateImpl`z .

*Storage*<br/>
Rekord użytkownika.

*UpdateArray (AktualizacjaArray)*<br/>
Tablica zawierająca buforowane dane do aktualizowania zestawu wierszy.

*Klasa rowu*<br/>
Jednostka pamięci masowej `HROW`dla .

*Klasa mapy*<br/>
Jednostka magazynu dla wszystkich uchwytów wiersza posiadanych przez dostawcę.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldb.h

## <a name="members"></a>Elementy członkowskie

### <a name="interface-methods-used-with-irowsetchange"></a>Metody interfejsu (używane z IRowsetChange)

|||
|-|-|
|[Setdata](#setdata)|Ustawia wartości danych w jednej lub większej liczbie kolumn.|

### <a name="interface-methods-used-with-irowsetupdate"></a>Metody interfejsu (używane z IRowsetUpdate)

|||
|-|-|
|[GetOriginalDana](#getoriginaldata)|Pobiera dane ostatnio przesyłane do lub uzyskane ze źródła danych, ignorując oczekujące zmiany.|
|[Wychowania GetPendingRows](#getpendingrows)|Zwraca listę wierszy z oczekującymi zmianami.|
|[Stan GetRow](#getrowstatus)|Zwraca stan określonych wierszy.|
|[Cofanie](#undo)|Cofa wszelkie zmiany w wierszu od ostatniego pobrania lub aktualizacji.|
|[Aktualizacja](#update)|Przesyła wszelkie zmiany wprowadzone do wiersza od ostatniego pobrania lub aktualizacji.|

### <a name="implementation-methods-callback"></a>Metody implementacji (wywołanie zwrotne)

|||
|-|-|
|[Dozwolone jest zwędczenie obowiązuje](#isupdateallowed)|Służy do sprawdzania zabezpieczeń, integralności i tak dalej przed zezwoleniem na aktualizacje.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_mapCachedData](#mapcacheddata)|Zawiera oryginalne dane dla odroczonej operacji.|

## <a name="remarks"></a>Uwagi

Należy najpierw przeczytać i zrozumieć dokumentację [dla IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)), ponieważ wszystko opisane tam również dotyczy tutaj. Należy również przeczytać rozdział 6 *ole DB Programista odwołania* na ustawienie danych.

`IRowsetUpdateImpl`implementuje interfejs OLE `IRowsetUpdate` DB, który umożliwia konsumentom opóźnianie `IRowsetChange` transmisji zmian wprowadzonych do źródła danych i cofanie zmian przed transmisją.

> [!IMPORTANT]
> Zdecydowanie zaleca się przeczytanie następującej dokumentacji PRZED podjęciem próby zaimplementowania dostawcy:

- [Tworzenie dostawcy podlegającego aktualizacji](../../data/oledb/creating-an-updatable-provider.md)

- Rozdział 6 *odniesienia dla programisty OLE DB*

- Zobacz też, `RUpdateRowset` jak klasa jest używana w przykładzie [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)

## <a name="irowsetupdateimplsetdata"></a><a name="setdata"></a>IRowsetUpdateImpl::SetData

Ustawia wartości danych w jednej lub większej liczbie kolumn.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetChange::SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) w *odwołaniu programisty OLE DB*.

### <a name="remarks"></a>Uwagi

Ta metoda zastępuje [IRowsetChangeImpl::SetData](../../data/oledb/irowsetchangeimpl-setdata.md) metody, ale obejmuje buforowanie oryginalnych danych, aby umożliwić natychmiastowe lub odroczone przetwarzanie operacji.

## <a name="irowsetupdateimplgetoriginaldata"></a><a name="getoriginaldata"></a>IRowsetUpdateImpl::GetOriginalData

Pobiera dane ostatnio przesyłane do lub uzyskane ze źródła danych, ignorując oczekujące zmiany.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (GetOriginalData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pData);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetUpdate::GetOriginalData](/previous-versions/windows/desktop/ms709947(v=vs.85)) w *odwołaniu programisty OLE DB*.

## <a name="irowsetupdateimplgetpendingrows"></a><a name="getpendingrows"></a>IRowsetUpdateImpl::GetPendingRows

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
[w] Odpowiada parametrowi *hChapter* w [pliku IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)).

Aby uzyskać inne parametry, zobacz [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) w *odwołaniu programisty OLE DB*.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) w *odwołaniu programisty OLE DB*.

## <a name="irowsetupdateimplgetrowstatus"></a><a name="getrowstatus"></a>IRowsetUpdateImpl::GetRowStatus

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
[w] Odpowiada parametrowi *hChapter* w [pliku IRowsetUpdate::GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)).

Aby uzyskać inne parametry, zobacz [IRowsetUpdate::GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)) w *odwołaniu programisty OLE DB*.

## <a name="irowsetupdateimplundo"></a><a name="undo"></a>IRowsetUpdateImpl::Cofnij

Cofa wszelkie zmiany w wierszu od ostatniego pobrania lub aktualizacji.

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
[w] Odpowiada parametrowi *hChapter* w [pliku IRowsetUpdate::Cofnij](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*pcRowsUndone ( pcRowsUndone )*<br/>
[na zewnątrz] Odpowiada parametrowi *pcRows* w [pliku IRowsetUpdate::Cofnij](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*prgRowsUndone*<br/>
[w] Odpowiada parametrowi *prgRows* w [pliku IRowsetUpdate::Cofnij](/previous-versions/windows/desktop/ms719655(v=vs.85)).

Aby uzyskać inne parametry, zobacz [IRowsetUpdate::Cofnij](/previous-versions/windows/desktop/ms719655(v=vs.85)) w *odwołaniu programisty OLE DB*.

## <a name="irowsetupdateimplupdate"></a><a name="update"></a>IRowsetUpdateImpl::Aktualizacja

Przesyła wszelkie zmiany wprowadzone do wiersza od ostatniego pobrania lub aktualizacji.

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
[w] Odpowiada parametrowi *hChapter* w [pliku IRowsetUpdate::Update](/previous-versions/windows/desktop/ms719709(v=vs.85)).

Aby uzyskać inne parametry, zobacz [IRowsetUpdate::Update](/previous-versions/windows/desktop/ms719709(v=vs.85)) w *odwołaniu programisty OLE DB*.

### <a name="remarks"></a>Uwagi

Zmiany są przesyłane przez [wywołanie IRowsetChangeImpl::FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md). Konsument musi wywołać [CRowset::Update](../../data/oledb/crowset-update.md) dla zmian, które mają zostać wprowadzone. Ustaw *prgRowstatus* na odpowiednią wartość opisaną w [stanach wierszy](/previous-versions/windows/desktop/ms722752(v=vs.85)) w *odwołaniu programisty OLE DB*.

## <a name="irowsetupdateimplisupdateallowed"></a><a name="isupdateallowed"></a>IRowsetUpdateImpl::IsUpdateAllowed

Zastąd w tej metodzie należy sprawdzić bezpieczeństwo, integralność itd.

### <a name="syntax"></a>Składnia

```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,
   HROW /* [in] */ /* hRowUpdate */,
   DBROWSTATUS* /* [out] */ /* pRowStatus */);
```

#### <a name="parameters"></a>Parametry

*Stan*<br/>
[w] Stan oczekujących operacji w wierszach.

*hRowUpdate (hRowUpdate)*<br/>
[w] Dojście do wierszy, które użytkownik chce zaktualizować.

*pRowStatus (stan pRow)*<br/>
[na zewnątrz] Stan zwrócony do użytkownika.

### <a name="remarks"></a>Uwagi

Jeśli okaże się, że aktualizacja powinna być dozwolona, zwraca S_OK; w przeciwnym razie zwraca E_FAIL. Jeśli zezwolisz na aktualizację, musisz `DBROWSTATUS` również ustawić w [IRowsetUpdateImpl::Update](../../data/oledb/irowsetupdateimpl-update.md) do odpowiedniego [stanu wiersza](/previous-versions/windows/desktop/ms722752(v=vs.85)).

## <a name="irowsetupdateimplm_mapcacheddata"></a><a name="mapcacheddata"></a>IRowsetUpdateImpl::m_mapCachedData

Mapa zawierająca oryginalne dane dla odroczonej operacji.

### <a name="syntax"></a>Składnia

```cpp
CAtlMap<
   HROW hRow,
   Storage* pData
>
m_mapCachedData;
```

#### <a name="parameters"></a>Parametry

*hRow (właz)*<br/>
Dojście do wierszy dla danych.

*Pdata*<br/>
Wskaźnik do danych, które mają być buforowane. Dane są typu *Magazyn* (klasa rekordu użytkownika). Zobacz argument *szablonu magazynu* w [klasie IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md).

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Tworzenie dostawcy podlegającego aktualizacji](../../data/oledb/creating-an-updatable-provider.md)
