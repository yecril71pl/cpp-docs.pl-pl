---
title: Klasa CComAggObject
ms.date: 11/04/2016
f1_keywords:
- CComAggObject
- ATLCOM/ATL::CComAggObject
- ATLCOM/ATL::CComAggObject::CComAggObject
- ATLCOM/ATL::CComAggObject::AddRef
- ATLCOM/ATL::CComAggObject::CreateInstance
- ATLCOM/ATL::CComAggObject::FinalConstruct
- ATLCOM/ATL::CComAggObject::FinalRelease
- ATLCOM/ATL::CComAggObject::QueryInterface
- ATLCOM/ATL::CComAggObject::Release
- ATLCOM/ATL::CComAggObject::m_contained
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComAggObject class
ms.assetid: 7aa90d69-d399-477b-880d-e2cdf0ef7881
ms.openlocfilehash: 9f05e83c8d0a1fd68fce3228dea9cfeab6183c96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321174"
---
# <a name="ccomaggobject-class"></a>Klasa CComAggObject

Ta klasa implementuje [interfejs IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) dla zagregowanego obiektu. Z definicji zagregowany obiekt znajduje się w obiekcie zewnętrznym. Klasa `CComAggObject` jest podobna do [CComObject Klasy](../../atl/reference/ccomobject-class.md), z tą różnicą, że udostępnia interfejs, który jest bezpośrednio dostępny dla klientów zewnętrznych.

## <a name="syntax"></a>Składnia

```
template<class contained>
class CComAggObject : public IUnknown,
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parametry

*Zawarte*<br/>
Klasa, pochodzące z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również z innych interfejsów, które mają być obsługiwane na obiekcie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComAggObject::CComAggObject](#ccomaggobject)|Konstruktor.|
|[CComAggObject::~CComAggObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComAggObject::AddRef](#addref)|Zwiększa liczbę odwołań do obiektu zagregowanego.|
|[CComAggObject::CreateInstance CComAggObject::CreateInstance CComAggObject::CreateInstance CCom](#createinstance)|Ta funkcja statyczna umożliwia utworzenie nowego **obiektu CComAggObject<** `contained` **>** bez narzutu [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComAggObject::FinalConstruct](#finalconstruct)|Wykonuje końcową inicjację `m_contained`.|
|[CComAggObject::FinalRelease](#finalrelease)|Wykonuje ostateczne zniszczenie `m_contained`.|
|[CComAggObject::QueryInterface](#queryinterface)|Pobiera wskaźnik do żądanego interfejsu.|
|[CComAggObject::Release CComAggObject::Release CComAggObject::Release CCom](#release)|Zmniejsza liczbę odwołań dla zagregowanego obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComAggObject::m_contained](#m_contained)|Delegaci `IUnknown` wywołuje do zewnętrznej nieznanej.|

## <a name="remarks"></a>Uwagi

`CComAggObject`implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) dla zagregowanego obiektu. `CComAggObject`ma swój `IUnknown` własny interfejs, oddzielony `IUnknown` od interfejsu obiektu zewnętrznego i zachowuje własną liczbę odwołań.

Aby uzyskać więcej informacji na temat agregacji, zobacz artykuł [Podstawy obiektów COM ATL](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CComObjectRootBase`

[Ccomobjectrootex](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComAggObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ccomaggobjectaddref"></a><a name="addref"></a>CComAggObject::AddRef

Zwiększa liczbę odwołań do obiektu zagregowanego.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatna do diagnostyki lub testowania.

## <a name="ccomaggobjectccomaggobject"></a><a name="ccomaggobject"></a>CComAggObject::CComAggObject

Konstruktor.

```
CComAggObject(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
[w] Zewnętrzna niewiadoma.

### <a name="remarks"></a>Uwagi

Inicjuje `CComContainedObject` element członkowski, [m_contained](#m_contained)i zwiększa liczbę blokad modułu.

Destruktor zmniejsza liczbę blokad modułu.

## <a name="ccomaggobjectccomaggobject"></a><a name="dtor"></a>CComAggObject::~CComAggObject

Destruktor.

```
~CComAggObject();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby, wywołuje [FinalRelease](#finalrelease)i zmniejsza liczbę blokad modułu.

## <a name="ccomaggobjectcreateinstance"></a><a name="createinstance"></a>CComAggObject::CreateInstance CComAggObject::CreateInstance CComAggObject::CreateInstance CCom

Ta funkcja statyczna umożliwia utworzenie nowego **obiektu CComAggObject<** `contained` **>** bez narzutu [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```

### <a name="parameters"></a>Parametry

*S*<br/>
[na zewnątrz] Wskaźnik do **CComAggObject\<**<em>zawierał</em> **>** wskaźnik. Jeśli `CreateInstance` nie powiedzie się, *pp* jest ustawiona na wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Zwrócony obiekt ma liczbę odwołań `AddRef` zero, więc `Release` natychmiast wywołać, a następnie użyć do zwolnienia odwołania na wskaźnik obiektu po zakończeniu.

Jeśli nie potrzebujesz bezpośredniego dostępu do obiektu, ale nadal chcesz utworzyć `CoCreateInstance`nowy obiekt bez narzutu , użyj [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) zamiast.

## <a name="ccomaggobjectfinalconstruct"></a><a name="finalconstruct"></a>CComAggObject::FinalConstruct

Wywoływana w końcowych etapach budowy obiektu, ta metoda wykonuje wszelkie końcowe inicjowanie na [m_contained](#m_contained) element członkowski.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="ccomaggobjectfinalrelease"></a><a name="finalrelease"></a>CComAggObject::FinalRelease

Wywoływana podczas niszczenia obiektu, ta metoda zwalnia [m_contained](#m_contained) element członkowski.

```
void FinalRelease();
```

## <a name="ccomaggobjectm_contained"></a><a name="m_contained"></a>CComAggObject::m_contained

A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) obiekt pochodzi z klasy.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Parametry

*Zawarte*<br/>
[w] Klasa, pochodzące z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również z innych interfejsów, które mają być obsługiwane na obiekcie.

### <a name="remarks"></a>Uwagi

Wszystkie `IUnknown` wywołania za pośrednictwem `m_contained` są delegowane do zewnętrznej nieznanej.

## <a name="ccomaggobjectqueryinterface"></a><a name="queryinterface"></a>CComAggObject::QueryInterface

Pobiera wskaźnik do żądanego interfejsu.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[w] Identyfikator żądanego interfejsu.

*ppvObiekt*<br/>
[na zewnątrz] Wskaźnik do wskaźnika interfejsu identyfikowanego przez *iid*. Jeśli obiekt nie obsługuje tego interfejsu, *ppvObject* jest ustawiona na wartość NULL.

*S*<br/>
[na zewnątrz] Wskaźnik do wskaźnika interfejsu identyfikowany przez typ `Q`. Jeśli obiekt nie obsługuje tego interfejsu, *pp* jest ustawiona na WARTOŚĆ NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli żądany interfejs `IUnknown` `QueryInterface` jest , zwraca wskaźnik do zagregowanego obiektu własnego `IUnknown` i zwiększa liczbę odwołań. W przeciwnym razie ta metoda kwerendy dla interfejsu za pośrednictwem `CComContainedObject` elementu członkowskiego, [m_contained](#m_contained).

## <a name="ccomaggobjectrelease"></a><a name="release"></a>CComAggObject::Release CComAggObject::Release CComAggObject::Release CCom

Zmniejsza liczbę odwołań dla zagregowanego obiektu.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Wartość zwracana

W kompilacjach debugowania zwraca wartość, `Release` która może być przydatna do diagnostyki lub testowania. W kompilacjach innych niż `Release` debugowanie zawsze zwraca wartość 0.

## <a name="see-also"></a>Zobacz też

[Klasa CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Klasa CComPolyObject](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
