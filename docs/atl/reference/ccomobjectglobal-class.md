---
title: CComObjectGlobal Class
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
ms.openlocfilehash: ec3abd04ce72cce98dae72a1ed8cbb8d9fe72079
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267436"
---
# <a name="ccomobjectglobal-class"></a>CComObjectGlobal Class

Ta klasa zarządza moduł zawierający licznik odwołań do Twojej `Base` obiektu.

## <a name="syntax"></a>Składnia

```
template<class Base>
class CComObjectGlobal : public Base
```

#### <a name="parameters"></a>Parametry

*Base*<br/>
Z klasą pochodną [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również od innych interfejsu mają być obsługiwane w obiekcie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComObjectGlobal::CComObjectGlobal](#ccomobjectglobal)|Konstruktor.|
|[CComObjectGlobal::~CComObjectGlobal](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComObjectGlobal::AddRef](#addref)|Implementuje globalną `AddRef`.|
|[CComObjectGlobal::QueryInterface](#queryinterface)|Implementuje globalną `QueryInterface`.|
|[CComObjectGlobal::Release](#release)|Implementuje globalną `Release`.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|Zawiera wartość HRESULT zwracane podczas konstruowania z `CComObjectGlobal` obiektu.|

## <a name="remarks"></a>Uwagi

`CComObjectGlobal` zarządza moduł zawierający licznik odwołań do Twojej `Base` obiektu. `CComObjectGlobal` gwarantuje, że obiekt nie zostaną usunięte, tak długo, jak moduł nie jest zwalniane. Obiekt zostanie usunięty, tylko gdy licznik odwołań na cały moduł zbliża się do zera.

Na przykład za pomocą `CComObjectGlobal`, fabrykę klas może przechowywać wspólne obiekt globalny, który jest współużytkowany przez wszystkich klientów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Base`

`CComObjectGlobal`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="addref"></a>  CComObjectGlobal::AddRef

Zwiększa licznik odwołań obiektu o 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatne w przypadku diagnostyki i testowania.

### <a name="remarks"></a>Uwagi

Domyślnie `AddRef` wywołania `_Module::Lock`, gdzie `_Module` jest globalne wystąpienie [CComModule](../../atl/reference/ccommodule-class.md) lub klasa pochodnej od niego.

##  <a name="ccomobjectglobal"></a>  CComObjectGlobal::CComObjectGlobal

Konstruktor. Wywołania `FinalConstruct` , a następnie ustawia [m_hResFinalConstruct](#m_hresfinalconstruct) do `HRESULT` zwrócone przez `FinalConstruct`.

```
CComObjectGlobal(void* = NULL));
```

### <a name="remarks"></a>Uwagi

Jeśli masz nie pochodzi z klasy podstawowej [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), należy podać własne `FinalConstruct` metody. Wywołania destruktora `FinalRelease`.

##  <a name="dtor"></a>  CComObjectGlobal::~CComObjectGlobal

Destruktor.

```
CComObjectGlobal();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby i wywołania [FinalRelease](ccomobjectrootex-class.md#finalrelease).

##  <a name="m_hresfinalconstruct"></a>  CComObjectGlobal::m_hResFinalConstruct

Zawiera wartość HRESULT z wywołaniem `FinalConstruct` podczas konstruowania `CComObjectGlobal` obiektu.

```
HRESULT m_hResFinalConstruct;
```

##  <a name="queryinterface"></a>  CComObjectGlobal::QueryInterface

Pobiera wskaźnik do wskaźnika żądanego interfejsu.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*IID*<br/>
[in] Identyfikator GUID interfejsu żądanej.

*ppvObject*<br/>
[out] Wskaźnik do wskaźnika interfejsu identyfikowane przez identyfikator iid lub wartość NULL, jeśli nie można odnaleźć interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

`QueryInterface` obsługuje tylko interfejsów COM tabeli mapy.

##  <a name="release"></a>  CComObjectGlobal::Release

Dekrementuje liczbę odwołań obiektu o 1.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Wartość zwracana

W kompilacjach do debugowania `Release` zwraca wartość, która może być przydatne w przypadku diagnostyki i testowania. W kompilacjach nieprzeznaczonych do debugowania `Release` zawsze zwraca wartość 0.

### <a name="remarks"></a>Uwagi

Domyślnie `Release` wywołania `_Module::Unlock`, gdzie `_Module` jest globalne wystąpienie [CComModule](../../atl/reference/ccommodule-class.md) lub klasa pochodnej od niego.

## <a name="see-also"></a>Zobacz także

[Klasa CComObjectStack](../../atl/reference/ccomobjectstack-class.md)<br/>
[Klasa CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Klasa CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
