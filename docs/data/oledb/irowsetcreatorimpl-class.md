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
ms.openlocfilehash: a53cd653258980d21e9dd297ae61c458732b7250
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210551"
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl — Klasa

Wykonuje te same funkcje co `IObjectWithSite`, ale również włącza `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS`właściwości OLE DB.

## <a name="syntax"></a>Składnia

```cpp
template < class T >
class ATL_NO_VTABLE IRowsetCreatorImpl
   : public IObjectWithSiteImpl< T >
```

### <a name="parameters"></a>Parametry

*&*<br/>
Klasa pochodna `IRowsetCreator`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Members

### <a name="methods"></a>Metody

|||
|-|-|
|[SetSite](#setsite)|Ustawia lokację zawierającą obiekt zestawu wierszy.|

## <a name="remarks"></a>Uwagi

Ta klasa dziedziczy z [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) i przesłania [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite). Gdy polecenie dostawcy lub obiekt sesji tworzy zestaw wierszy, wywołuje `QueryInterface` w obiekcie zestawu wierszy szukające `IObjectWithSite` i wywołań `SetSite` przekazanie interfejsu `IUnkown` obiektu zestawu wierszy jako interfejsu lokacji.

## <a name="irowsetcreatorimplsetsite"></a><a name="setsite"></a>IRowsetCreatorImpl —:: SetSite

Ustawia lokację zawierającą obiekt zestawu wierszy. Aby uzyskać więcej informacji, zobacz [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite).

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(SetSite )(IUnknown* pCreator);
```

#### <a name="parameters"></a>Parametry

*pCreator*<br/>
podczas Wskaźnik do wskaźnika interfejsu `IUnknown` lokacji zarządzającej obiektem zestawu wierszy.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ponadto `IRowsetCreatorImpl::SetSite` włącza OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` właściwości.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
