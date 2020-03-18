---
title: IRowsetInfoImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
- ATL.IRowsetInfoImpl.GetProperties
- IRowsetInfoImpl.GetProperties
- ATL::IRowsetInfoImpl::GetProperties
- IRowsetInfoImpl::GetProperties
- ATL::IRowsetInfoImpl::GetReferencedRowset
- GetReferencedRowset
- ATL.IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl::GetReferencedRowset
- IRowsetInfoImpl::GetSpecification
- ATL.IRowsetInfoImpl.GetSpecification
- IRowsetInfoImpl.GetSpecification
- GetSpecification
- ATL::IRowsetInfoImpl::GetSpecification
helpviewer_keywords:
- IRowsetInfoImpl class
- GetProperties method
- GetReferencedRowset method
- GetSpecification method
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
ms.openlocfilehash: 7389ba689fb1f371b5fbf73045dcdc78cd465d88
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446186"
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl — Klasa

Dostarcza implementację interfejsu [IRowsetInfo](/previous-versions/windows/desktop/ms724541(v=vs.85)) .

## <a name="syntax"></a>Składnia

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE IRowsetInfoImpl :
   public IRowsetInfo, 
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>Parametry

*&*<br/>
Klasa, która pochodzi od `IRowsetInfoImpl`.

*PropClass*<br/>
Klasa właściwości, która jest określana przez użytkownika, która domyślnie ma wartość *T*.

## <a name="requirements"></a>Wymagania

**Nagłówek:** altdb. h

## <a name="members"></a>Elementy członkowskie

### <a name="interface-methods"></a>Metody interfejsu

|||
|-|-|
|[GetProperties](#getproperties)|Zwraca bieżące ustawienia wszystkich właściwości obsługiwanych przez zestaw wierszy.|
|[GetReferencedRowset](#getreferencedrowset)|Zwraca wskaźnik interfejsu do zestawu wierszy, do którego zostanie zastosowana Zakładka.|
|[Getswoistość](#getspecification)|Zwraca wskaźnik interfejsu dla obiektu (polecenia lub sesji), który utworzył ten zestaw wierszy.|

## <a name="remarks"></a>Uwagi

Obowiązkowy interfejs dla zestawów wierszy. Ta klasa implementuje właściwości zestawu wierszy przy użyciu [mapy zestawu właściwości](../../data/oledb/begin-propset-map.md) zdefiniowanej w klasie poleceń. Chociaż Klasa zestawu wierszy wydaje się używać klas poleceń klasy, zestaw wierszy jest dostarczany z własną kopią właściwości czasu wykonywania, gdy jest tworzony przez polecenie lub obiekt sesji.

## <a name="getproperties"></a>IRowsetInfoImpl:: GetProperties

Zwraca bieżące ustawienia dla właściwości w grupie `DBPROPSET_ROWSET`.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (GetProperties )(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG* pcPropertySets,
   DBPROPSET** prgPropertySets);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetInfo:: GetProperties](/previous-versions/windows/desktop/ms719611(v=vs.85)) w *Kompendium OLE DB programisty*.

## <a name="getreferencedrowset"></a>IRowsetInfoImpl:: GetReferencedRowset

Zwraca wskaźnik interfejsu do zestawu wierszy, do którego zostanie zastosowana Zakładka.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (GetReferencedRowset )(DBORDINAL iOrdinal,
   REFIID riid,
   IUnknown** ppReferencedRowset);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetInfo:: GetReferencedRowset](/previous-versions/windows/desktop/ms721145(v=vs.85)) w *dokumentacji programisty OLE DB*. Parametr *iOrdinal* musi być kolumną zakładki.

## <a name="getspecification"></a>IRowsetInfoImpl:: getswoisty

Zwraca wskaźnik interfejsu dla obiektu (polecenia lub sesji), który utworzył ten zestaw wierszy.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (GetSpecification )(REFIID riid,
   IUnknown** ppSpecification);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetInfo:: Getswoiste](/previous-versions/windows/desktop/ms716746(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="remarks"></a>Uwagi

Użyj tej metody z [IGetDataSourceImpl —](../../data/oledb/igetdatasourceimpl-class.md) , aby pobrać właściwości z obiektu źródła danych.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)