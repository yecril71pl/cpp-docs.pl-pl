---
title: ICommandPropertiesImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
- ICommandPropertiesImpl::GetProperties
- ICommandPropertiesImpl.GetProperties
- ICommandPropertiesImpl.SetProperties
- ICommandPropertiesImpl::SetProperties
helpviewer_keywords:
- ICommandPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
ms.openlocfilehash: f71ca7f5fb675916c9db7e5720e6c148f2131351
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845578"
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl — Klasa

Zapewnia implementację interfejsu [ICommandProperties](/previous-versions/windows/desktop/ms723044(v=vs.85)) .

## <a name="syntax"></a>Składnia

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ICommandPropertiesImpl
   : public ICommandProperties, public CUtlProps<PropClass>
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa pochodna

*PropClass*<br/>
Klasa właściwości.

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Elementy członkowskie

### <a name="interface-methods"></a>Metody interfejsu

| Nazwa | Opis |
|-|-|
|[GetProperties](#getproperties)|Zwraca listę właściwości w grupie Właściwości zestawu wierszy, która aktualnie żąda zestawu wierszy.|
|[SetProperties](#setproperties)|Ustawia właściwości w grupie Właściwości zestawu wierszy.|

## <a name="remarks"></a>Uwagi

Jest to obowiązkowe dla poleceń. Implementacja jest dostarczana przez funkcję statyczną zdefiniowaną przez makro [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) .

## <a name="icommandpropertiesimplgetproperties"></a><a name="getproperties"></a> ICommandPropertiesImpl:: GetProperties

Zwraca wszystkie żądane zestawy właściwości przy użyciu mapy właściwości polecenia.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetProperties)(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG * pcPropertySets,
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>Parametry

Zobacz [ICommandProperties:: GetProperties](/previous-versions/windows/desktop/ms723119(v=vs.85)) w *Kompendium OLE DB programisty*.

### <a name="remarks"></a>Uwagi

Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

## <a name="icommandpropertiesimplsetproperties"></a><a name="setproperties"></a> ICommandPropertiesImpl:: SetProperties

Ustawia właściwości dla obiektu polecenia.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>Parametry

Zobacz [ICommandProperties:: SetProperties](/previous-versions/windows/desktop/ms711497(v=vs.85)) w *Kompendium OLE DB programisty*.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
