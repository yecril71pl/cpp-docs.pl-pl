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
ms.openlocfilehash: aeeca008499ca43cdcebd008390e5cb6c5a9e63c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845526"
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl — Klasa

Dostarcza implementację interfejsu [IDBCreateSession](/previous-versions/windows/desktop/ms724076(v=vs.85)) .

## <a name="syntax"></a>Składnia

```cpp
template <class T, class SessionClass>
class ATL_NO_VTABLE IDBCreateSessionImpl
   : public IDBCreateSession
```

### <a name="parameters"></a>Parametry

*T*<br/>
KLASA POCHODNA

*SessionClass*<br/>
Obiekt sesji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Elementy członkowskie

### <a name="interface-methods"></a>Metody interfejsu

| Nazwa | Opis |
|-|-|
|[Moja sesja](#createsession)|Tworzy nową sesję z obiektu źródła danych i zwraca żądany interfejs w nowo utworzonej sesji.|

## <a name="remarks"></a>Uwagi

Obowiązkowy interfejs dla obiektów źródła danych.

## <a name="idbcreatesessionimplcreatesession"></a><a name="createsession"></a> IDBCreateSessionImpl —:: issession

Tworzy nową sesję z obiektu źródła danych i zwraca żądany interfejs w nowo utworzonej sesji.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(CreateSession)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppDBSession);
```

#### <a name="parameters"></a>Parametry

Zobacz [IDBCreateSession:: issession](/previous-versions/windows/desktop/ms714942(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
