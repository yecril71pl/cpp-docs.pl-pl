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
ms.openlocfilehash: 9253c7495f4d13ed6ce609988251d8abd09592ad
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497034"
---
# <a name="ccomobjectnolock-class"></a>Klasa CComObjectNoLock

Ta klasa implementuje `IUnknown` dla niezagregowanego obiektu, ale nie zwiększa liczby blokad modułu w konstruktorze.

## <a name="syntax"></a>Składnia

```
template<class Base>
class CComObjectNoLock : public Base
```

#### <a name="parameters"></a>Parametry

*Opiera*<br/>
Klasa, pochodząca z [klasy CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), a także z dowolnego innego interfejsu, który ma być obsługiwany w obiekcie.

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
|[CComObjectNoLock::Release](#release)|Zmniejsza liczbę odwołań do obiektu.|

## <a name="remarks"></a>Uwagi

`CComObjectNoLock`jest podobna do [CComObject](../../atl/reference/ccomobject-class.md) w tym, że implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) dla obiektu niezagregowanego; `CComObjectNoLock` jednak nie zwiększa liczby blokad modułu w konstruktorze.

Biblioteki ATL `CComObjectNoLock` używają wewnętrznie dla fabryk klas. Ogólnie rzecz biorąc, ta klasa nie zostanie użyta bezpośrednio.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Base`

`CComObjectNoLock`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="addref"></a>CComObjectNoLock:: AddRef

Zwiększa liczbę odwołań do obiektu.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatna w przypadku diagnostyki lub testowania.

##  <a name="ccomobjectnolock"></a>CComObjectNoLock::CComObjectNoLock

Konstruktor. W przeciwieństwie do [CComObject](../../atl/reference/ccomobject-class.md), nie zwiększa liczby blokad modułu.

```
CComObjectNoLock(void* = NULL);
```

### <a name="parameters"></a>Parametry

<em>pozycję\*</em><br/>
podczas Ten parametr bez nazwy nie jest używany. Istnieje dla symetrii z innymi `CComXXXObjectXXX` konstruktorami.

##  <a name="dtor"></a>CComObjectNoLock:: ~ CComObjectNoLock

Destruktor.

```
~CComObjectNoLock();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzieloną zasoby i wywołuje [FinalRelease](ccomobjectrootex-class.md#finalrelease).

##  <a name="queryinterface"></a>CComObjectNoLock:: QueryInterface

Pobiera wskaźnik do żądanego interfejsu.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*IID*<br/>
podczas Identyfikator żądanego interfejsu.

*ppvObject*<br/>
określoną Wskaźnik do wskaźnika interfejsu identyfikowanego przez *Identyfikator IID*. Jeśli obiekt nie obsługuje tego interfejsu, *ppvObject* ma wartość null.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

##  <a name="release"></a>CComObjectNoLock:: Release

Zmniejsza liczbę odwołań do obiektu.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Wartość zwracana

W kompilacjach `Release` debugowania zwraca wartość, która może być przydatna w przypadku diagnostyki lub testowania. W kompilacjach `Release` niedebugowanych zawsze zwraca wartość 0.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
