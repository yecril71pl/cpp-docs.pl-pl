---
title: IRowsetCreatorImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetCreatorImpl
- ATL.IRowsetCreatorImpl
- ATL::IRowsetCreatorImpl<T>
- ATL.IRowsetCreatorImpl<T>
- IRowsetCreatorImpl
- IRowsetCreatorImpl.SetSite
- IRowsetCreatorImpl<T>::SetSite
- IRowsetCreatorImpl::SetSite
- SetSite
- ATL.IRowsetCreatorImpl.SetSite
- ATL::IRowsetCreatorImpl<T>::SetSite
- ATL::IRowsetCreatorImpl::SetSite
- ATL.IRowsetCreatorImpl<T>.SetSite
helpviewer_keywords:
- IRowsetCreatorImpl class
- SetSite method
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
ms.openlocfilehash: 8c4253d469c510f5e6eb996ed510ef836844899d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501391"
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl — Klasa

Wykonuje te same funkcje, `IObjectWithSite` co, ale również włącza właściwości `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS`OLE DB.

## <a name="syntax"></a>Składnia

```cpp
template < class T >
class ATL_NO_VTABLE IRowsetCreatorImpl
   : public IObjectWithSiteImpl< T >
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa pochodna `IRowsetCreator`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[SetSite](#setsite)|Ustawia lokację zawierającą obiekt zestawu wierszy.|

## <a name="remarks"></a>Uwagi

Ta klasa dziedziczy z [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) i przesłania [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite). Gdy polecenie dostawcy lub obiekt sesji tworzy `QueryInterface` zestaw wierszy, wywołuje obiekt zestawu wierszy `IObjectWithSite` szukający i wywołuje `SetSite` przekazanie `IUnkown` interfejsu obiektu zestawu wierszy jako interfejsu lokacji.

## <a name="setsite"></a>IRowsetCreatorImpl —:: SetSite

Ustawia lokację zawierającą obiekt zestawu wierszy. Aby uzyskać więcej informacji, zobacz [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite).

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(SetSite )(IUnknown* pCreator);
```

#### <a name="parameters"></a>Parametry

*pCreator*<br/>
podczas Wskaźnik do `IUnknown` wskaźnika interfejsu lokacji zarządzającej obiektem zestawu wierszy.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ponadto `IRowsetCreatorImpl::SetSite` włącza OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` właściwości.

## <a name="see-also"></a>Zobacz także

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)