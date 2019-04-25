---
title: CComObjectNoLock Class
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
ms.openlocfilehash: 50dc4505c1da8df9efc0c9d0028461ef49c0840e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246303"
---
# <a name="ccomobjectnolock-class"></a>CComObjectNoLock Class

Ta klasa implementuje `IUnknown` nieagregowane obiektu, ale ma nie przyrostu liczbę blokad modułu w konstruktorze.

## <a name="syntax"></a>Składnia

```
template<class Base>
class CComObjectNoLock : public Base
```

#### <a name="parameters"></a>Parametry

*Base*<br/>
Z klasą pochodną [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również od innych interfejsu mają być obsługiwane w obiekcie.

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
|[CComObjectNoLock::Release](#release)|Dekrementuje liczbę odwołań do obiektu.|

## <a name="remarks"></a>Uwagi

`CComObjectNoLock` jest podobny do [CComObject](../../atl/reference/ccomobject-class.md) , implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) nieagregowane obiektu; jednak `CComObjectNoLock` jest przyrost blokady modułu count w konstruktorze.

Używa ATL `CComObjectNoLock` wewnętrznie dla fabryki klas. Ogólnie rzecz biorąc nie użyjesz tej klasy bezpośrednio.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Base`

`CComObjectNoLock`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="addref"></a>  CComObjectNoLock::AddRef

Zwiększa liczbę odwołań do obiektu.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być użyteczna, diagnostykę lub testowania.

##  <a name="ccomobjectnolock"></a>  CComObjectNoLock::CComObjectNoLock

Konstruktor. W odróżnieniu od [CComObject](../../atl/reference/ccomobject-class.md), nie zwiększa liczbę blokad modułu.

```
CComObjectNoLock(void* = NULL);
```

### <a name="parameters"></a>Parametry

<em>Void\*</em><br/>
[in] Ten parametr nienazwany nie jest używany. Istnieje symetrii z innymi `CComXXXObjectXXX` konstruktorów.

##  <a name="dtor"></a>  CComObjectNoLock::~CComObjectNoLock

Destruktor.

```
~CComObjectNoLock();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby i wywołania [FinalRelease](ccomobjectrootex-class.md#finalrelease).

##  <a name="queryinterface"></a>  CComObjectNoLock::QueryInterface

Pobiera wskaźnik do żądanego interfejsu.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*IID*<br/>
[in] Identyfikator interfejsu żądanej.

*ppvObject*<br/>
[out] Wskaźnik do wskaźnika interfejsu identyfikowane przez *iid*. Jeśli obiekt nie obsługuje ten interfejs *ppvObject* ma wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="release"></a>  CComObjectNoLock::Release

Dekrementuje liczbę odwołań do obiektu.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Wartość zwracana

W kompilacjach do debugowania `Release` zwraca wartość, która może być użyteczna, diagnostykę lub testowania. W kompilacjach nieprzeznaczonych do debugowania `Release` zawsze zwraca wartość 0.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)
