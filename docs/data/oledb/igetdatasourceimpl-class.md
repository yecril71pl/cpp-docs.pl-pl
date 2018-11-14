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
ms.openlocfilehash: cd6b56f4281a2fdde77229ec54be6d6289a87148
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556572"
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl — Klasa

Udostępnia implementację [IGetDataSource](https://docs.microsoft.com/previous-versions/windows/desktop/ms709721(v=vs.85)) obiektu.

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

Zobacz [IGetDataSource::GetDataSource](https://docs.microsoft.com/previous-versions/windows/desktop/ms725443(v=vs.85)) w *OLE DB Podręcznik programisty*.

### <a name="remarks"></a>Uwagi

Parametr jest przydatne, jeśli potrzebujesz uzyskać dostęp do właściwości w obiekcie źródła danych.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)