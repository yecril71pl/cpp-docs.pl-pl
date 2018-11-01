---
title: Klasa CComObjectStack
ms.date: 11/04/2016
f1_keywords:
- CComObjectStack
- ATLCOM/ATL::CComObjectStack
- ATLCOM/ATL::CComObjectStack::CComObjectStack
- ATLCOM/ATL::CComObjectStack::AddRef
- ATLCOM/ATL::CComObjectStack::QueryInterface
- ATLCOM/ATL::CComObjectStack::Release
- ATLCOM/ATL::CComObjectStack::m_hResFinalConstruct
helpviewer_keywords:
- CComObjectStack class
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
ms.openlocfilehash: dfe8c58803a0eb06ea17ae1b241e1e435f0263f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579273"
---
# <a name="ccomobjectstack-class"></a>Klasa CComObjectStack

Ta klasa tworzy tymczasowy obiekt COM i dostarcza mu szkieletowych implementacji `IUnknown`.

## <a name="syntax"></a>Składnia

```
template <class  Base>
class CComObjectStack : public Base
```

#### <a name="parameters"></a>Parametry

*podstawowy*<br/>
Z klasą pochodną [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również od innych interfejsu mają być obsługiwane w obiekcie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComObjectStack::CComObjectStack](#ccomobjectstack)|Konstruktor.|
|[CComObjectStack:: ~ CComObjectStack](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComObjectStack::AddRef](#addref)|Zwraca wartość zero. W trybie debugowania, wywołuje `_ASSERTE`.|
|[CComObjectStack::QueryInterface](#queryinterface)|Zwraca E_NOINTERFACE. W trybie debugowania, wywołuje `_ASSERTE`.|
|[CComObjectStack::Release](#release)|Zwraca wartość zero. W trybie debugowania, wywołuje `_ASSERTE`. ~|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComObjectStack::m_hResFinalConstruct](#m_hresfinalconstruct)|Zawiera wartość HRESULT zwracane podczas konstruowania z `CComObjectStack` obiektu.|

## <a name="remarks"></a>Uwagi

`CComObjectStack` Służy do tworzenia tymczasowych obiektów COM i udostępnia obiekt szkieletowych implementację `IUnknown`. Zazwyczaj obiekt jest używany jako zmienna lokalna w obrębie jednej funkcji (która jest wypychane na stosie). Ponieważ obiekt jest niszczony, kiedy funkcja kończy, zliczanie odwołań nie odbywa się zwiększyć wydajność.

Poniższy przykład pokazuje, jak utworzyć obiekt modelu COM, używana wewnątrz funkcji:

[!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/cpp/ccomobjectstack-class_1.cpp)]

Tymczasowy obiekt `Tempobj` są wypychane na stosie i automatycznie znika po zakończeniu funkcji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Base`

`CComObjectStack`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="addref"></a>  CComObjectStack::AddRef

Zwraca wartość zero.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero.

### <a name="remarks"></a>Uwagi

W trybie debugowania, wywołuje `_ASSERTE`.

##  <a name="ccomobjectstack"></a>  CComObjectStack::CComObjectStack

Konstruktor.

```
CComObjectStack(void* = NULL);
```

### <a name="remarks"></a>Uwagi

Wywołania `FinalConstruct` , a następnie ustawia [m_hResFinalConstruct](#m_hresfinalconstruct) HRESULT zwracane przez `FinalConstruct`. Jeśli masz nie pochodzi z klasy podstawowej [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), należy podać własne `FinalConstruct` metody. Wywołania destruktora `FinalRelease`.

##  <a name="dtor"></a>  CComObjectStack:: ~ CComObjectStack

Destruktor.

```
CComObjectStack();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby i wywołania [FinalRelease](ccomobjectrootex-class.md#finalrelease).

##  <a name="m_hresfinalconstruct"></a>  CComObjectStack::m_hResFinalConstruct

Zawiera wartość HRESULT zwracane z wywołania `FinalConstruct` podczas konstruowania `CComObjectStack` obiektu.

```
HRESULT    m_hResFinalConstruct;
```

##  <a name="queryinterface"></a>  CComObjectStack::QueryInterface

Zwraca E_NOINTERFACE.

```
HRESULT    QueryInterface(REFIID, void**);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOINTERFACE.

### <a name="remarks"></a>Uwagi

W trybie debugowania, wywołuje `_ASSERTE`.

##  <a name="release"></a>  CComObjectStack::Release

Zwraca wartość zero.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero.

### <a name="remarks"></a>Uwagi

W trybie debugowania, wywołuje `_ASSERTE`.

## <a name="see-also"></a>Zobacz też

[Klasa CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Klasa CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Klasa CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
