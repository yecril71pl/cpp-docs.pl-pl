---
title: Klasa CComObjectGlobal
ms.date: 11/04/2016
f1_keywords:
- CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::AddRef
- ATLCOM/ATL::CComObjectGlobal::QueryInterface
- ATLCOM/ATL::CComObjectGlobal::Release
- ATLCOM/ATL::CComObjectGlobal::m_hResFinalConstruct
helpviewer_keywords:
- CComObjectGlobal class
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
ms.openlocfilehash: 9a784584179186cdf1e63c1ec43cad4d59391ec3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327624"
---
# <a name="ccomobjectglobal-class"></a>Klasa CComObjectGlobal

Ta klasa zarządza liczbą odwołań na `Base` module zawierającym obiekt.

## <a name="syntax"></a>Składnia

```
template<class Base>
class CComObjectGlobal : public Base
```

#### <a name="parameters"></a>Parametry

*Podstawowej*<br/>
Klasa, pochodzące z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również z dowolnego innego interfejsu, który chcesz obsługiwać na obiekcie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComObjectGlobal::CComObjectGlobal](#ccomobjectglobal)|Konstruktor.|
|[CComObjectGlobal::~CComObjectGlobal](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComObjectGlobal::AddRef](#addref)|Implementuje globalny `AddRef`plik .|
|[CComObjectGlobal::QueryInterface](#queryinterface)|Implementuje globalny `QueryInterface`plik .|
|[CComObjectGlobal::Release CComObjectGlobal::Release CComObjectGlobal::Release CCom](#release)|Implementuje globalny `Release`plik .|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|Zawiera HRESULT zwrócony podczas `CComObjectGlobal` budowy obiektu.|

## <a name="remarks"></a>Uwagi

`CComObjectGlobal`zarządza liczbą odwołań na module `Base` zawierającym obiekt. `CComObjectGlobal`zapewnia, że obiekt nie zostanie usunięty, dopóki moduł nie zostanie zwolniony. Obiekt zostanie usunięty tylko wtedy, gdy liczba odwołań na cały moduł spadnie do zera.

Na przykład `CComObjectGlobal`za pomocą fabryki klas może pomieścić wspólny obiekt globalny, który jest współużytkowane przez wszystkich swoich klientów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Base`

`CComObjectGlobal`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ccomobjectglobaladdref"></a><a name="addref"></a>CComObjectGlobal::AddRef

Zwiększa liczbę odwołań obiektu o 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatna do diagnostyki i testowania.

### <a name="remarks"></a>Uwagi

Domyślnie `AddRef` wywołania `_Module::Lock` `_Module` , gdzie jest globalne wystąpienie [CComModule](../../atl/reference/ccommodule-class.md) lub klasy pochodne od niego.

## <a name="ccomobjectglobalccomobjectglobal"></a><a name="ccomobjectglobal"></a>CComObjectGlobal::CComObjectGlobal

Konstruktor. Wywołania, `FinalConstruct` a następnie ustawia [m_hResFinalConstruct](#m_hresfinalconstruct) do zwróconego `HRESULT` przez `FinalConstruct`.

```
CComObjectGlobal(void* = NULL));
```

### <a name="remarks"></a>Uwagi

Jeśli klasa podstawowa nie została wyprowadzona z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), należy podać własną `FinalConstruct` metodę. Destruktor wywołuje `FinalRelease`.

## <a name="ccomobjectglobalccomobjectglobal"></a><a name="dtor"></a>CComObjectGlobal::~CComObjectGlobal

Destruktor.

```
CComObjectGlobal();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby i wywołuje [FinalRelease](ccomobjectrootex-class.md#finalrelease).

## <a name="ccomobjectglobalm_hresfinalconstruct"></a><a name="m_hresfinalconstruct"></a>CComObjectGlobal::m_hResFinalConstruct

Zawiera HRESULT z `FinalConstruct` wywołania `CComObjectGlobal` podczas budowy obiektu.

```
HRESULT m_hResFinalConstruct;
```

## <a name="ccomobjectglobalqueryinterface"></a><a name="queryinterface"></a>CComObjectGlobal::QueryInterface

Pobiera wskaźnik do żądanego wskaźnika interfejsu.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[w] Identyfikator GUID żądanego interfejsu.

*ppvObiekt*<br/>
[na zewnątrz] Wskaźnik do wskaźnika interfejsu identyfikowanego przez iid lub NULL, jeśli nie zostanie znaleziony interfejs.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

`QueryInterface`obsługuje tylko interfejsy w tabeli mapy COM.

## <a name="ccomobjectglobalrelease"></a><a name="release"></a>CComObjectGlobal::Release CComObjectGlobal::Release CComObjectGlobal::Release CCom

Zmniejsza liczbę odwołań obiektu o 1.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Wartość zwracana

W kompilacjach debugowania zwraca wartość, `Release` która może być przydatna do diagnostyki i testowania. W kompilacjach innych niż `Release` debugowanie zawsze zwraca wartość 0.

### <a name="remarks"></a>Uwagi

Domyślnie `Release` wywołania `_Module::Unlock` `_Module` , gdzie jest globalne wystąpienie [CComModule](../../atl/reference/ccommodule-class.md) lub klasy pochodne od niego.

## <a name="see-also"></a>Zobacz też

[Klasa CComObjectStack](../../atl/reference/ccomobjectstack-class.md)<br/>
[Klasa CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Klasa CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
