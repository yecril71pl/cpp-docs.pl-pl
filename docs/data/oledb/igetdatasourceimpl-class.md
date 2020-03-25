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
ms.openlocfilehash: 596dd2ea7f65040ae526662974d210c1f99a0cf2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210616"
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl — Klasa

Dostarcza implementację obiektu [IGetDataSource](/previous-versions/windows/desktop/ms709721(v=vs.85)) .

## <a name="syntax"></a>Składnia

```cpp
template <class T>
class ATL_NO_VTABLE IGetDataSourceImpl : public IGetDataSource
```

### <a name="parameters"></a>Parametry

*&*<br/>
Klasa, która pochodzi od `IGetDataSourceImpl`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Members

### <a name="interface-methods"></a>Metody interfejsu

|||
|-|-|
|[GetDataSource](#getdatasource)|Zwraca wskaźnik interfejsu w obiekcie źródła danych, który utworzył sesję.|

## <a name="remarks"></a>Uwagi

Jest to obowiązkowy interfejs w sesji w celu uzyskania wskaźnika interfejsu do obiektu źródła danych.

## <a name="igetdatasourceimplgetdatasource"></a><a name="getdatasource"></a>IGetDataSourceImpl —:: GetDataSource

Zwraca wskaźnik interfejsu w obiekcie źródła danych, który utworzył sesję.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetDataSource)(REFIID riid,
   IUnknown ** ppDataSource);
```

#### <a name="parameters"></a>Parametry

Zobacz [IGetDataSource:: GetDataSource](/previous-versions/windows/desktop/ms725443(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="remarks"></a>Uwagi

Przydatne, jeśli trzeba uzyskać dostęp do właściwości w obiekcie źródła danych.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
