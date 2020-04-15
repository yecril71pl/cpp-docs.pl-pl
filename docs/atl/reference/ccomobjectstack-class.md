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
ms.openlocfilehash: 8c3fd56635da8b80c84f6151009586b7bd2b4341
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327575"
---
# <a name="ccomobjectstack-class"></a>Klasa CComObjectStack

Ta klasa tworzy tymczasowy obiekt COM i zapewnia jego `IUnknown`szkieletową implementację .

## <a name="syntax"></a>Składnia

```
template <class  Base>
class CComObjectStack : public Base
```

#### <a name="parameters"></a>Parametry

*Podstawowej*<br/>
Klasa, pochodzące z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również z dowolnego innego interfejsu, który chcesz obsługiwać na obiekcie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComObjectStack::CComObjectStack](#ccomobjectstack)|Konstruktor.|
|[CComObjectStack::~CComObjectStack](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComObjectStack::AddRef](#addref)|Zwraca zero. W trybie debugowania wywołania `_ASSERTE`.|
|[CComObjectStack::QueryInterface](#queryinterface)|Zwraca E_NOINTERFACE. W trybie debugowania wywołania `_ASSERTE`.|
|[CComObjectStack::Release CComObjectStack::Release CComObjectStack::Release CCom](#release)|Zwraca zero. W trybie debugowania wywołania `_ASSERTE`. ~|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComObjectStack::m_hResFinalConstruct](#m_hresfinalconstruct)|Zawiera HRESULT zwrócony podczas `CComObjectStack` budowy obiektu.|

## <a name="remarks"></a>Uwagi

`CComObjectStack`służy do tworzenia tymczasowego obiektu COM i dostarczania obiektowi `IUnknown`szkieletowej implementacji . Zazwyczaj obiekt jest używany jako zmienna lokalna w ramach jednej funkcji (czyli wypchnięte na stosie). Ponieważ obiekt jest niszczony po zakończeniu funkcji, zliczanie odwołań nie jest wykonywane w celu zwiększenia wydajności.

W poniższym przykładzie pokazano, jak utworzyć obiekt COM używany wewnątrz funkcji:

[!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/cpp/ccomobjectstack-class_1.cpp)]

Obiekt `Tempobj` tymczasowy jest wypychany na stos i automatycznie znika po zakończeniu funkcji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Base`

`CComObjectStack`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ccomobjectstackaddref"></a><a name="addref"></a>CComObjectStack::AddRef

Zwraca zero.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca zero.

### <a name="remarks"></a>Uwagi

W trybie debugowania wywołania `_ASSERTE`.

## <a name="ccomobjectstackccomobjectstack"></a><a name="ccomobjectstack"></a>CComObjectStack::CComObjectStack

Konstruktor.

```
CComObjectStack(void* = NULL);
```

### <a name="remarks"></a>Uwagi

Wywołania, `FinalConstruct` a następnie ustawia [m_hResFinalConstruct](#m_hresfinalconstruct) do HRESULT zwracany przez `FinalConstruct`. Jeśli klasa podstawowa nie została wyprowadzona z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), należy podać własną `FinalConstruct` metodę. Destruktor wywołuje `FinalRelease`.

## <a name="ccomobjectstackccomobjectstack"></a><a name="dtor"></a>CComObjectStack::~CComObjectStack

Destruktor.

```
CComObjectStack();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby i wywołuje [FinalRelease](ccomobjectrootex-class.md#finalrelease).

## <a name="ccomobjectstackm_hresfinalconstruct"></a><a name="m_hresfinalconstruct"></a>CComObjectStack::m_hResFinalConstruct

Zawiera HRESULT zwrócony `FinalConstruct` z wywołania podczas budowy `CComObjectStack` obiektu.

```
HRESULT    m_hResFinalConstruct;
```

## <a name="ccomobjectstackqueryinterface"></a><a name="queryinterface"></a>CComObjectStack::QueryInterface

Zwraca E_NOINTERFACE.

```
HRESULT    QueryInterface(REFIID, void**);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOINTERFACE.

### <a name="remarks"></a>Uwagi

W trybie debugowania wywołania `_ASSERTE`.

## <a name="ccomobjectstackrelease"></a><a name="release"></a>CComObjectStack::Release CComObjectStack::Release CComObjectStack::Release CCom

Zwraca zero.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca zero.

### <a name="remarks"></a>Uwagi

W trybie debugowania wywołania `_ASSERTE`.

## <a name="see-also"></a>Zobacz też

[Klasa CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Klasa CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Klasa CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
