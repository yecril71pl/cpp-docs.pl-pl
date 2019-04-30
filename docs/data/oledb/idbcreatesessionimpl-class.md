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
ms.openlocfilehash: ae59abc542a4599d289c099801fc34d56b2b13d4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409164"
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl — Klasa

Udostępnia implementację na potrzeby [IDBCreateSession](/previous-versions/windows/desktop/ms724076(v=vs.85)) interfejsu.

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
|[CreateSession](#createsession)|Tworzy nową sesję z obiektu źródła danych i zwraca żądanego interfejsu na nowo utworzoną sesji.|

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

Zobacz [IDBCreateSession::CreateSession](/previous-versions/windows/desktop/ms714942(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="see-also"></a>Zobacz także

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)