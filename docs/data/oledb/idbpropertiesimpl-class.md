---
title: IDBPropertiesImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- IDBPropertiesImpl
- ATL.IDBPropertiesImpl
- ATL.IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl
- IDBPropertiesImpl::GetProperties
- IDBPropertiesImpl.GetProperties
- IDBPropertiesImpl::GetPropertyInfo
- IDBPropertiesImpl.GetPropertyInfo
- GetPropertyInfo
- IDBPropertiesImpl.SetProperties
- IDBPropertiesImpl::SetProperties
helpviewer_keywords:
- IDBPropertiesImpl class
- GetProperties method
- GetPropertyInfo method
- SetProperties method
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
ms.openlocfilehash: d94c5d121386989d223a55b8ce7626444c3f8950
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509070"
---
# <a name="idbpropertiesimpl-class"></a>IDBPropertiesImpl — Klasa

Zapewnia implementację `IDBProperties` interfejsu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
class ATL_NO_VTABLE IDBPropertiesImpl
   : public IDBProperties, public CUtlProps<T>
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która pochodzi od `IDBPropertiesImpl` .

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Elementy członkowskie

### <a name="interface-methods"></a>Metody interfejsu

| Nazwa | Opis |
|-|-|
|[GetProperties](#getproperties)|Zwraca wartości właściwości ze źródła danych, informacje o źródle danych i grupy właściwości inicjalizacji, które są obecnie ustawione w obiekcie źródła danych lub wartości właściwości w grupie właściwości inicjowania, które są obecnie ustawione w module wyliczającym.|
|[GetPropertyInfo](#getpropertyinfo)|Zwraca informacje o wszystkich właściwościach obsługiwanych przez dostawcę.|
|[SetProperties](#setproperties)|Ustawia właściwości w grupach właściwości źródła danych i inicjalizacji dla obiektów źródła danych lub grupy właściwości inicjalizacji dla modułów wyliczających.|

## <a name="remarks"></a>Uwagi

[IDBProperties](/previous-versions/windows/desktop/ms719607(v=vs.85)) to obowiązkowy interfejs dla obiektów źródła danych i opcjonalny interfejs dla modułów wyliczających. Jeśli jednak moduł wyliczający ujawnia [IDBInitialize](/previous-versions/windows/desktop/ms713706(v=vs.85)), musi uwidocznić `IDBProperties` . `IDBPropertiesImpl` implementuje przy `IDBProperties` użyciu funkcji statycznej zdefiniowanej przez [BEGIN_PROPSET_MAP](./macros-for-ole-db-provider-templates.md#begin_propset_map).

## <a name="idbpropertiesimplgetproperties"></a><a name="getproperties"></a> IDBPropertiesImpl:: GetProperties

Zwraca wartości właściwości ze źródła danych, informacje o źródle danych i grupy właściwości inicjalizacji, które są obecnie ustawione w obiekcie źródła danych lub wartości właściwości w grupie właściwości inicjowania, które są obecnie ustawione w module wyliczającym.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetProperties)(ULONG cPropertySets,
   const DBPROPIDSET rgPropertySets[],
   ULONG * pcProperties,
   DBPROPSET ** prgProperties);
```

#### <a name="parameters"></a>Parametry

Zobacz [IDBProperties:: GetProperties](/previous-versions/windows/desktop/ms714344(v=vs.85)) w *Kompendium OLE DB programisty*.

Niektóre parametry odpowiadają parametrom *referencyjnym programisty OLE DB* różnymi nazwami, które są opisane w `IDBProperties::GetProperties` :

|OLE DB parametry szablonu|*OLE DB parametry odwołania programisty*|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cPropertyIDSets*|
|*rgPropertySets*|*rgPropertyIDSets*|
|*pcProperties*|*pcPropertySets*|
|*prgProperties*|*prgPropertySets*|

### <a name="remarks"></a>Uwagi

Jeśli dostawca jest zainicjowany, ta metoda zwraca wartości właściwości w DBPROPSET_DATASOURCE, DBPROPSET_DATASOURCEINFO DBPROPSET_DBINIT grupy właściwości, które są obecnie ustawione dla obiektu źródła danych. Jeśli dostawca nie został zainicjowany, zwraca tylko DBPROPSET_DBINIT właściwości grupy.

## <a name="idbpropertiesimplgetpropertyinfo"></a><a name="getpropertyinfo"></a> IDBPropertiesImpl:: GetPropertyInfo

Zwraca informacje o właściwościach obsługiwane przez źródło danych.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetPropertyInfo)(ULONG cPropertySets,
   const DBPROPIDSET rgPropertySets[],
   ULONG * pcPropertyInfoSets,
   DBPROPINFOSET ** prgPropertyInfoSets,
   OLECHAR ** ppDescBuffer);
```

#### <a name="parameters"></a>Parametry

Zobacz [IDBProperties:: GetPropertyInfo](/previous-versions/windows/desktop/ms718175(v=vs.85)) w *dokumentacji programisty OLE DB*.

Niektóre parametry odpowiadają parametrom *referencyjnym programisty OLE DB* różnymi nazwami, które są opisane w `IDBProperties::GetPropertyInfo` :

|OLE DB parametry szablonu|*OLE DB parametry odwołania programisty*|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cPropertyIDSets*|
|*rgPropertySets*|*rgPropertyIDSets*|

### <a name="remarks"></a>Uwagi

Używa [IDBInitializeImpl:: m_pCUtlPropInfo](./idbinitializeimpl-class.md#pcutlpropinfo) w celu zaimplementowania tej funkcji.

## <a name="idbpropertiesimplsetproperties"></a><a name="setproperties"></a> IDBPropertiesImpl:: SetProperties

Ustawia właściwości w grupach właściwości źródła danych i inicjalizacji dla obiektów źródła danych lub grupy właściwości inicjalizacji dla modułów wyliczających.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>Parametry

Zobacz [IDBProperties:: SetProperties](/previous-versions/windows/desktop/ms723049(v=vs.85)) w *Kompendium OLE DB programisty*.

### <a name="remarks"></a>Uwagi

Jeśli dostawca jest zainicjowany, ta metoda ustawia wartości właściwości w DBPROPSET_DATASOURCE, DBPROPSET_DATASOURCEINFO DBPROPSET_DBINIT grupy właściwości dla obiektu źródła danych. Jeśli dostawca nie został zainicjowany, ustawia DBPROPSET_DBINIT tylko właściwości grupy.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
