---
title: Klasa CComObjectNoLock
ms.date: 11/04/2016
f1_keywords:
- CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::AddRef
- ATLCOM/ATL::CComObjectNoLock::QueryInterface
- ATLCOM/ATL::CComObjectNoLock::Release
helpviewer_keywords:
- CComObjectNoLock class
ms.assetid: 288c6506-7da8-4127-8d58-7f4bd779539a
ms.openlocfilehash: c190f495e284e98b27a6c6dc2099a8dfc4b1693d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327616"
---
# <a name="ccomobjectnolock-class"></a>Klasa CComObjectNoLock

Ta klasa `IUnknown` implementuje dla obiektu nieagregowanego, ale nie zwiększa liczby blokad modułu w konstruktorze.

## <a name="syntax"></a>Składnia

```
template<class Base>
class CComObjectNoLock : public Base
```

#### <a name="parameters"></a>Parametry

*Podstawowej*<br/>
Klasa, pochodzące z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również z dowolnego innego interfejsu, który chcesz obsługiwać na obiekcie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComObjectNoLock::CComObjectNoLock](#ccomobjectnolock)|Konstruktor.|
|[CComObjectNoLock::~CComObjectNoLock](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComObjectNoLock::AddRef](#addref)|Zwiększa liczbę odwołań do obiektu.|
|[CComObjectNoLock::QueryInterface](#queryinterface)|Zwraca wskaźnik do żądanego interfejsu.|
|[CComObjectNoLock::Release CComObjectNoLock::Release CComObjectNoLock::Release CCom](#release)|Zmniejsza liczbę odwołań na obiekcie.|

## <a name="remarks"></a>Uwagi

`CComObjectNoLock`jest podobny do [CComObject](../../atl/reference/ccomobject-class.md) w tym implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) dla obiektu nieagregowanego; jednak `CComObjectNoLock` nie zwiększa liczbę blokad modułu w konstruktorze.

ATL używa `CComObjectNoLock` wewnętrznie dla fabryk klas. Ogólnie rzecz biorąc nie będzie używać tej klasy bezpośrednio.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Base`

`CComObjectNoLock`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ccomobjectnolockaddref"></a><a name="addref"></a>CComObjectNoLock::AddRef

Zwiększa liczbę odwołań do obiektu.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatna do diagnostyki lub testowania.

## <a name="ccomobjectnolockccomobjectnolock"></a><a name="ccomobjectnolock"></a>CComObjectNoLock::CComObjectNoLock

Konstruktor. W przeciwieństwie do [CComObject](../../atl/reference/ccomobject-class.md), nie zwiększa liczbę blokad modułu.

```
CComObjectNoLock(void* = NULL);
```

### <a name="parameters"></a>Parametry

<em>void\*</em><br/>
[w] Ten nienazwany parametr nie jest używany. Istnieje dla symetrii `CComXXXObjectXXX` z innymi konstruktorami.

## <a name="ccomobjectnolockccomobjectnolock"></a><a name="dtor"></a>CComObjectNoLock::~CComObjectNoLock

Destruktor.

```
~CComObjectNoLock();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby i wywołuje [FinalRelease](ccomobjectrootex-class.md#finalrelease).

## <a name="ccomobjectnolockqueryinterface"></a><a name="queryinterface"></a>CComObjectNoLock::QueryInterface

Pobiera wskaźnik do żądanego interfejsu.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[w] Identyfikator żądanego interfejsu.

*ppvObiekt*<br/>
[na zewnątrz] Wskaźnik do wskaźnika interfejsu identyfikowanego przez *iid*. Jeśli obiekt nie obsługuje tego interfejsu, *ppvObject* jest ustawiona na wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="ccomobjectnolockrelease"></a><a name="release"></a>CComObjectNoLock::Release CComObjectNoLock::Release CComObjectNoLock::Release CCom

Zmniejsza liczbę odwołań na obiekcie.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Wartość zwracana

W kompilacjach debugowania zwraca wartość, `Release` która może być przydatna do diagnostyki lub testowania. W kompilacjach innych niż `Release` debugowanie zawsze zwraca wartość 0.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
