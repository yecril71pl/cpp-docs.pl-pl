---
title: IDBCreateSessionImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- IDBCreateSessionImpl
- ATL.IDBCreateSessionImpl
- ATL::IDBCreateSessionImpl
- IDBCreateSessionImpl::CreateSession
- IDBCreateSessionImpl.CreateSession
- CreateSession
helpviewer_keywords:
- IDBCreateSessionImpl class
- CreateSession method
ms.assetid: 48c02c5c-8362-45ac-af8e-bb119cf8c5c7
ms.openlocfilehash: ecc06bf5e3514ea87c86de17dbafd59b9da9f8b6
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556425"
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl — Klasa

Udostępnia implementację na potrzeby [IDBCreateSession](https://docs.microsoft.com/previous-versions/windows/desktop/ms724076(v=vs.85)) interfejsu.

## <a name="syntax"></a>Składnia

```cpp
template <class T, class SessionClass>
class ATL_NO_VTABLE IDBCreateSessionImpl
   : public IDBCreateSession
```

### <a name="parameters"></a>Parametry

*T*<br/>
KLASY POCHODZĄCE Z

*SessionClass*<br/>
Obiekt sesji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldb.h

## <a name="members"></a>Elementy członkowskie

### <a name="interface-methods"></a>Metody interfejsu

|||
|-|-|
|[Createsession —](#createsession)|Tworzy nową sesję z obiektu źródła danych i zwraca żądanego interfejsu na nowo utworzoną sesji.|

## <a name="remarks"></a>Uwagi

Obowiązkowego interfejsu na obiekty źródła danych.

## <a name="createsession"></a> IDBCreateSessionImpl::CreateSession

Tworzy nową sesję z obiektu źródła danych i zwraca żądanego interfejsu na nowo utworzoną sesji.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(CreateSession)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppDBSession);
```

#### <a name="parameters"></a>Parametry

Zobacz [IDBCreateSession::CreateSession](https://docs.microsoft.com/previous-versions/windows/desktop/ms714942(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)