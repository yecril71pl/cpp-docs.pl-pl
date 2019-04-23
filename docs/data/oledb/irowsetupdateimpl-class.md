---
title: IRowsetUpdateImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
- SetData
- IRowsetUpdateImpl::SetData
- IRowsetUpdateImpl.SetData
- ATL::IRowsetUpdateImpl::SetData
- ATL.IRowsetUpdateImpl.SetData
- ATL.IRowsetUpdateImpl.GetOriginalData
- IRowsetUpdateImpl.GetOriginalData
- GetOriginalData
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
- GetRowStatus
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
ms.openlocfilehash: 6c20698e2219cf7c3e1d840e23b5f8113947ae9f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037721"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl — Klasa

Szablony OLE DB implementacji [IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85)) interfejsu.

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
Klasa pochodząca z `IRowsetUpdateImpl`.

*Storage*<br/>
Rekordzie użytkownika.

*UpdateArray*<br/>
Tablica zawierająca dane w pamięci podręcznej do aktualizowania zestawu wierszy.

*RowClass*<br/>
Jednostki magazynu na potrzeby `HROW`.

*MapClass*<br/>
Jednostki magazynu na potrzeby wszystkich dojść do wierszy są przechowywane przez dostawcę.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldb.h

## <a name="members"></a>Elementy członkowskie

### <a name="interface-methods-used-with-irowsetchange"></a>Metody interfejsu (używana w IRowsetChange)

|||
|-|-|
|[SetData](#setdata)|Ustawia wartości danych w co najmniej jedną kolumnę.|

### <a name="interface-methods-used-with-irowsetupdate"></a>Metody interfejsu (używana w IRowsetUpdate)

|||
|-|-|
|[GetOriginalData](#getoriginaldata)|Pobiera dane ostatnio przekazane lub uzyskany ze źródła danych, ignorowanie oczekujące zmiany.|
|[GetPendingRows](#getpendingrows)|Zwraca listę wierszy z oczekującymi zmianami.|
|[GetRowStatus](#getrowstatus)|Zwraca stan określonych wierszy.|
|[Cofnij](#undo)|Cofa zmiany wiersza od czasu ostatniego pobrania lub aktualizacji.|
|[Aktualizacja](#update)|Przesyła wszelkie zmiany wprowadzone do wiersza od czasu ostatniego pobrania lub aktualizacji.|

### <a name="implementation-methods-callback"></a>Metody wdrażania (wywołanie zwrotne)

|||
|-|-|
|[IsUpdateAllowed](#isupdateallowed)|Użytych do sprawdzenia integralności, bezpieczeństwa i tak dalej przed zezwoleniem na aktualizacje.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_mapCachedData](#mapcacheddata)|Zawiera oryginalne dane do odroczonego wykonania operacji.|

## <a name="remarks"></a>Uwagi

Najpierw należy przeczytać i zrozumieć, w dokumentacji dotyczącej [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)), ponieważ wszystko, co jest opisane ma również zastosowanie w tym miejscu. Należy również przeczytać Rozdział 6 *OLE DB Podręcznik programisty* na temat ustawiania danych.

`IRowsetUpdateImpl` implementuje OLE DB `IRowsetUpdate` interfejs, który umożliwia opóźnienie transmisji w trybie zmiany wprowadzone za pomocą `IRowsetChange` do źródła danych i Cofnij zmiany przed rozpoczęciem transmisji.

> [!IMPORTANT]
>  Zdecydowanie zaleca się przeczytanie poniższej dokumentacji przed podjęciem próby wdrożenia dostawcy:

- [Tworzenie aktualizowalnego dostawcy](../../data/oledb/creating-an-updatable-provider.md)

- Rozdział 6 *OLE DB Podręcznik programisty*

- Zobacz też sposób, w jaki `RUpdateRowset` klasa jest używana w [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) próbki

## <a name="setdata"></a> IRowsetUpdateImpl::SetData

Ustawia wartości danych w co najmniej jedną kolumnę.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetChange::SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) w *OLE DB Podręcznik programisty*.

### <a name="remarks"></a>Uwagi

Ta metoda zastępuje [IRowsetChangeImpl::SetData](../../data/oledb/irowsetchangeimpl-setdata.md) ale zawiera buforowania oryginalnych danych jest natychmiastowa lub odroczone przetwarzanie operacji.

## <a name="getoriginaldata"></a> IRowsetUpdateImpl::GetOriginalData

Pobiera dane ostatnio przekazane lub uzyskany ze źródła danych, ignorowanie oczekujące zmiany.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (GetOriginalData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pData);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetUpdate::GetOriginalData](/previous-versions/windows/desktop/ms709947(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="getpendingrows"></a> IRowsetUpdateImpl::GetPendingRows

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
[in] Odnosi się do *hChapter* parametru w [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)).

Dla innych parametrów, zobacz [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) w *OLE DB Podręcznik programisty*.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="getrowstatus"></a> IRowsetUpdateImpl::GetRowStatus

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
[in] Odnosi się do *hChapter* parametru w [IRowsetUpdate::GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)).

Dla innych parametrów, zobacz [IRowsetUpdate::GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="undo"></a> IRowsetUpdateImpl::Undo

Cofa zmiany wiersza od czasu ostatniego pobrania lub aktualizacji.

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
[in] Odnosi się do *hChapter* parametru w [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*pcRowsUndone*<br/>
[out] Odnosi się do *pcRows* parametru w [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*prgRowsUndone*<br/>
[in] Odnosi się do *prgRows* parametru w [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

Dla innych parametrów, zobacz [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="update"></a> IRowsetUpdateImpl::Update

Przesyła wszelkie zmiany wprowadzone do wiersza od czasu ostatniego pobrania lub aktualizacji.

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
[in] Odnosi się do *hChapter* parametru w [IRowsetUpdate::Update](/previous-versions/windows/desktop/ms719709(v=vs.85)).

Dla innych parametrów, zobacz [IRowsetUpdate::Update](/previous-versions/windows/desktop/ms719709(v=vs.85)) w *OLE DB Podręcznik programisty*.

### <a name="remarks"></a>Uwagi

Zmiany są przesyłane przez wywołanie metody [IRowsetChangeImpl::FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md). Konsument musi wywołać [CRowset::Update](../../data/oledb/crowset-update.md) aby zmiany zaczęły obowiązywać. Ustaw *prgRowstatus* do odpowiedniej wartości zgodnie z opisem w [stany wiersza](/previous-versions/windows/desktop/ms722752(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="isupdateallowed"></a> IRowsetUpdateImpl::IsUpdateAllowed

Zastępuje tę metodę pod kątem bezpieczeństwa i integralności i tak dalej przed aktualizacji.

### <a name="syntax"></a>Składnia

```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,
   HROW /* [in] */ /* hRowUpdate */,
   DBROWSTATUS* /* [out] */ /* pRowStatus */);
```

#### <a name="parameters"></a>Parametry

*status*<br/>
[in] Stan Oczekujące operacje na wierszach.

*hRowUpdate*<br/>
[in] Dojście do wiersze, które użytkownik chce, aby zaktualizować.

*pRowStatus*<br/>
[out] Zwrócony kod stanu użytkownika.

### <a name="remarks"></a>Uwagi

Jeśli okaże się, że aktualizacji powinien być dozwolony, zwraca wartość S_OK; w przeciwnym razie zwraca E_FAIL. Jeśli zezwolisz na aktualizację, należy również ustawić `DBROWSTATUS` w [IRowsetUpdateImpl::Update](../../data/oledb/irowsetupdateimpl-update.md) do odpowiedniej [wiersz stanu](/previous-versions/windows/desktop/ms722752(v=vs.85)).

## <a name="mapcacheddata"></a> IRowsetUpdateImpl::m_mapCachedData

Mapa zawierającego oryginalne dane do odroczonego wykonania operacji.

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
Wskaźnik do danych w pamięci podręcznej. Dane są typu *magazynu* (klasy rekordów użytkowników). Zobacz *magazynu* argumentem szablonu w [irowsetupdateimpl — klasa](../../data/oledb/irowsetupdateimpl-class.md).

## <a name="see-also"></a>Zobacz także

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Tworzenie aktualizowalnego dostawcy](../../data/oledb/creating-an-updatable-provider.md)