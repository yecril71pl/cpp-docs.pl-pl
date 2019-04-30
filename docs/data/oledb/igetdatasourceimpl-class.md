---
title: IGetDataSourceImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- IGetDataSourceImpl
- ATL.IGetDataSourceImpl<T>
- ATL.IGetDataSourceImpl
- ATL::IGetDataSourceImpl
- ATL::IGetDataSourceImpl<T>
- GetDataSource
- IGetDataSourceImpl.GetDataSource
- IGetDataSourceImpl::GetDataSource
helpviewer_keywords:
- IGetDataSourceImpl class
- GetDataSource method
ms.assetid: d63f3178-d663-4f01-8c09-8aab2dd6805a
ms.openlocfilehash: 2056b93fd6c1d32b72996970352e87670ff406de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408943"
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl — Klasa

Udostępnia implementację [IGetDataSource](/previous-versions/windows/desktop/ms709721(v=vs.85)) obiektu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
class ATL_NO_VTABLE IGetDataSourceImpl : public IGetDataSource
```

### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `IGetDataSourceImpl`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldb.h

## <a name="members"></a>Elementy członkowskie

### <a name="interface-methods"></a>Metody interfejsu

|||
|-|-|
|[GetDataSource](#getdatasource)|Zwraca wskaźnik interfejsu na obiekt źródła danych, do utworzenia sesji.|

## <a name="remarks"></a>Uwagi

To obowiązkowego interfejsu na sesję umożliwiającą uzyskanie wskaźnika interfejsu do obiektu źródła danych.

## <a name="getdatasource"></a> IGetDataSourceImpl::GetDataSource

Zwraca wskaźnik interfejsu na obiekt źródła danych, do utworzenia sesji.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetDataSource)(REFIID riid,
   IUnknown ** ppDataSource);
```

#### <a name="parameters"></a>Parametry

Zobacz [IGetDataSource::GetDataSource](/previous-versions/windows/desktop/ms725443(v=vs.85)) w *OLE DB Podręcznik programisty*.

### <a name="remarks"></a>Uwagi

Parametr jest przydatne, jeśli potrzebujesz uzyskać dostęp do właściwości w obiekcie źródła danych.

## <a name="see-also"></a>Zobacz także

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)