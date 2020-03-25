---
title: IColumnsInfoImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL.IColumnsInfoImpl<T>
- ATL::IColumnsInfoImpl
- IColumnsInfoImpl
- ATL.IColumnsInfoImpl
- ATL::IColumnsInfoImpl<T>
- ATL::IColumnsInfoImpl::GetColumnInfo
- ATL.IColumnsInfoImpl.GetColumnInfo
- ATL::IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl::GetColumnInfo
- IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl.GetColumnInfo
- IColumnsInfoImpl<T>::MapColumnIDs
- MapColumnIDs
- ATL::IColumnsInfoImpl::MapColumnIDs
- IColumnsInfoImpl.MapColumnIDs
- ATL::IColumnsInfoImpl<T>::MapColumnIDs
- IColumnsInfoImpl::MapColumnIDs
- ATL.IColumnsInfoImpl<T>.MapColumnIDs
- ATL.IColumnsInfoImpl.MapColumnIDs
helpviewer_keywords:
- IColumnsInfoImpl class
- GetColumnInfo method
- MapColumnIDs method
ms.assetid: ba74c1c5-2eda-4452-8b57-84919fa0d066
ms.openlocfilehash: 39aa3f5e89746d48057e0e8efe6fe62b1c2d8921
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210876"
---
# <a name="icolumnsinfoimpl-class"></a>IColumnsInfoImpl — Klasa

Zapewnia implementację interfejsu [IColumnsInfo](/previous-versions/windows/desktop/ms724541(v=vs.85)) .

## <a name="syntax"></a>Składnia

```cpp
template <class T>
class ATL_NO_VTABLE IColumnsInfoImpl :
   public IColumnsInfo,
   public CDBIDOps
```

### <a name="parameters"></a>Parametry

*&*<br/>
Klasa, która pochodzi od `IColumnsInfoImpl`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Members

### <a name="methods"></a>Metody

|||
|-|-|
|[GetColumnInfo](#getcolumninfo)|Zwraca metadane kolumny, które są zbędne przez większość użytkowników.|
|[MapColumnIDs](#mapcolumnids)|Zwraca tablicę liczb porządkowych kolumn w zestawie wierszy, które są identyfikowane przez określone identyfikatory kolumn.|

## <a name="remarks"></a>Uwagi

Obowiązkowy interfejs dla zestawów wierszy i poleceń. Aby zmodyfikować zachowanie implementacji `IColumnsInfo` dostawcy, należy zmodyfikować mapę kolumn dostawcy.

## <a name="icolumnsinfoimplgetcolumninfo"></a><a name="getcolumninfo"></a>IColumnsInfoImpl:: GetColumnInfo

Zwraca metadane kolumny, które są zbędne przez większość użytkowników.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (GetColumnInfo)(DBORDINAL* pcColumns,
   DBCOLUMNINFO** prgInfo,
   OLECHAR** ppStringsBuffer);
```

#### <a name="parameters"></a>Parametry

Zobacz [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) w *dokumentacji programisty OLE DB*.

## <a name="icolumnsinfoimplmapcolumnids"></a><a name="mapcolumnids"></a>IColumnsInfoImpl:: MapColumnIDs

Zwraca tablicę liczb porządkowych kolumn w zestawie wierszy, które są identyfikowane przez określone identyfikatory kolumn.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (MapColumnIDs)(DBORDINAL cColumnIDs,
   const DBID rgColumnIDs[],
   DBORDINAL rgColumns[]);
```

#### <a name="parameters"></a>Parametry

Zobacz [IColumnsInfo:: MapColumnIDs](/previous-versions/windows/desktop/ms714200(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
