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
- GetProperties
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
ms.openlocfilehash: b42ecf6c03dd1023d1ba150d579f77c4bae8998a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029174"
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl — Klasa

Udostępnia implementację na potrzeby [IRowsetInfo](/previous-versions/windows/desktop/ms724541(v=vs.85)) interfejsu.

## <a name="syntax"></a>Składnia

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE IRowsetInfoImpl :
   public IRowsetInfo, 
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `IRowsetInfoImpl`.

*PropClass*<br/>
Klasa definiowanych przez użytkownika właściwości, która domyślnie *T*.

## <a name="requirements"></a>Wymagania

**Nagłówek:** altdb.h

## <a name="members"></a>Elementy członkowskie

### <a name="interface-methods"></a>Metody interfejsu

|||
|-|-|
|[GetProperties](#getproperties)|Zwraca bieżące ustawienia właściwości wszystkich obsługiwanych przez zestaw wierszy.|
|[Getreferencedrowset —](#getreferencedrowset)|Zwraca wskaźnik interfejsu do zestawu wierszy, do której stosują się zakładki.|
|[Getspecification —](#getspecification)|Zwraca wskaźnik interfejsu na obiekcie (polecenie lub sesji), który utworzył ten zestaw wierszy.|

## <a name="remarks"></a>Uwagi

Interfejs obowiązkowy zestawów wierszy. Ta klasa implementuje właściwości zestawu wierszy przy użyciu [Mapa zestawu właściwości](../../data/oledb/begin-propset-map.md) zdefiniowany w klasie polecenia. Mimo że klasy zestawu wierszy jest wyświetlane, można za pomocą właściwości klasy poleceń zestawy, zestaw wierszy jest dostarczany ze swoją własną kopią właściwości czasu wykonywania, po utworzeniu obiektu sesji lub polecenie.

## <a name="getproperties"></a> IRowsetInfoImpl::GetProperties

Zwraca bieżące ustawienia właściwości w `DBPROPSET_ROWSET` grupy.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (GetProperties )(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG* pcPropertySets,
   DBPROPSET** prgPropertySets);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetInfo::GetProperties](/previous-versions/windows/desktop/ms719611(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="getreferencedrowset"></a> IRowsetInfoImpl::GetReferencedRowset

Zwraca wskaźnik interfejsu do zestawu wierszy, do której stosują się zakładki.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (GetReferencedRowset )(DBORDINAL iOrdinal,
   REFIID riid,
   IUnknown** ppReferencedRowset);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetInfo::GetReferencedRowset](/previous-versions/windows/desktop/ms721145(v=vs.85)) w *OLE DB Podręcznik programisty*. *IOrdinal* parametr musi być kolumną zakładki.

## <a name="getspecification"></a> IRowsetInfoImpl::GetSpecification

Zwraca wskaźnik interfejsu na obiekcie (polecenie lub sesji), który utworzył ten zestaw wierszy.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (GetSpecification )(REFIID riid,
   IUnknown** ppSpecification);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetInfo::GetSpecification](/previous-versions/windows/desktop/ms716746(v=vs.85)) w *OLE DB Podręcznik programisty*.

### <a name="remarks"></a>Uwagi

Użyj tej metody za pomocą [igetdatasourceimpl —](../../data/oledb/igetdatasourceimpl-class.md) można pobrać właściwości z obiektu źródła danych.

## <a name="see-also"></a>Zobacz także

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)