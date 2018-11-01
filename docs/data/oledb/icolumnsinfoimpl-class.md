---
title: IColumnsInfoImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL.IColumnsInfoImpl<T>
- ATL::IColumnsInfoImpl
- IColumnsInfoImpl
- ATL.IColumnsInfoImpl
- ATL::IColumnsInfoImpl<T>
- GetColumnInfo
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
ms.openlocfilehash: 149d8ea9b23abffb73b5ea620ea094d6f5b792b9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498933"
---
# <a name="icolumnsinfoimpl-class"></a>IColumnsInfoImpl — Klasa

Udostępnia implementację [IColumnsInfo](/previous-versions/windows/desktop/ms724541) interfejsu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
class ATL_NO_VTABLE IColumnsInfoImpl :
   public IColumnsInfo,  
   public CDBIDOps
```

### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `IColumnsInfoImpl`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldb.h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[GetColumnInfo](#getcolumninfo)|Zwraca metadane kolumny wymagane przez większość klientów.|
|[MapColumnIDs](#mapcolumnids)|Zwraca tablicę liczb porządkowych kolumn w zestawie wierszy, które są identyfikowane za pomocą określonej kolumny identyfikatorów.|

## <a name="remarks"></a>Uwagi

Obowiązkowego interfejsu na polecenia i zestawy wierszy. Aby zmodyfikować zachowanie Twój dostawca `IColumnsInfo` wdrożenia, należy zmodyfikować dostawcy mapy kolumny.

## <a name="getcolumninfo"></a> IColumnsInfoImpl::GetColumnInfo

Zwraca metadane kolumny wymagane przez większość klientów.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (GetColumnInfo)(DBORDINAL* pcColumns,
   DBCOLUMNINFO** prgInfo,
   OLECHAR** ppStringsBuffer);
```

#### <a name="parameters"></a>Parametry

Zobacz [IColumnsInfo::GetColumnInfo](/previous-versions/windows/desktop/ms722704) w *OLE DB Podręcznik programisty*.

## <a name="mapcolumnids"></a> IColumnsInfoImpl::MapColumnIDs

Zwraca tablicę liczb porządkowych kolumn w zestawie wierszy, które są identyfikowane za pomocą określonej kolumny identyfikatorów.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (MapColumnIDs)(DBORDINAL cColumnIDs,
   const DBID rgColumnIDs[],
   DBORDINAL rgColumns[]);
```

#### <a name="parameters"></a>Parametry

Zobacz [IColumnsInfo::MapColumnIDs](/previous-versions/windows/desktop/ms714200) w *OLE DB Podręcznik programisty*.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)