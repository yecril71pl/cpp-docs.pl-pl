---
title: Klasa CComPolyObject
ms.date: 11/04/2016
f1_keywords:
- CComPolyObject
- ATLCOM/ATL::CComPolyObject
- ATLCOM/ATL::CComPolyObject::CComPolyObject
- ATLCOM/ATL::CComPolyObject::AddRef
- ATLCOM/ATL::CComPolyObject::CreateInstance
- ATLCOM/ATL::CComPolyObject::FinalConstruct
- ATLCOM/ATL::CComPolyObject::FinalRelease
- ATLCOM/ATL::CComPolyObject::QueryInterface
- ATLCOM/ATL::CComPolyObject::Release
- ATLCOM/ATL::CComPolyObject::m_contained
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComPolyObject class
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
ms.openlocfilehash: e30afef455db5f83afca8ff9e515f39f015c3b8a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327560"
---
# <a name="ccompolyobject-class"></a>Klasa CComPolyObject

Ta klasa `IUnknown` implementuje dla obiektu zagregowanego lub nieagregowanego.

## <a name="syntax"></a>Składnia

```
template<class contained>
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parametry

*Zawarte*<br/>
Klasa, pochodzące z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również z innych interfejsów, które mają być obsługiwane na obiekcie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComPolyObject::CComPolyObject](#ccompolyobject)|Konstruktor.|
|[CComPolyObject::~CComPolyObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComPolyObject::AddRef](#addref)|Zwiększa liczbę odwołań do obiektu.|
|[CComPolyObject::CreateInstance](#createinstance)|(Statyczne) Umożliwia utworzenie nowego **obiektu CComPolyObject<** `contained` **>** bez narzutu [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComPolyObject::FinalConstruct](#finalconstruct)|Wykonuje końcową inicjację `m_contained`.|
|[CComPolyObject::FinalRelease](#finalrelease)|Wykonuje ostateczne zniszczenie `m_contained`.|
|[CComPolyObject::QueryInterface](#queryinterface)|Pobiera wskaźnik do żądanego interfejsu.|
|[CComPolyObject::Release CComPolyObject::Release CComPolyObject::Release CCom](#release)|Zmniejsza liczbę odwołań do obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComPolyObject::m_contained](#m_contained)|Deleguje `IUnknown` wywołania do zewnętrznej nieznany, jeśli `IUnknown` obiekt jest agregowany lub do obiektu, jeśli obiekt nie jest agregowane.|

## <a name="remarks"></a>Uwagi

`CComPolyObject`implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) dla zagregowanego lub nieagregowanego obiektu.

Po utworzeniu `CComPolyObject` wystąpienia sprawdzana jest wartość zewnętrznej nieznanej. Jeśli jest null, `IUnknown` jest zaimplementowana dla obiektu nieagregowanego. Jeśli zewnętrzna niewiadoma nie jest null, `IUnknown` jest implementowana dla zagregowanego obiektu.

Zaletą korzystania `CComPolyObject` jest, aby uniknąć konieczności [cComAggObject](../../atl/reference/ccomaggobject-class.md) i [CComObject](../../atl/reference/ccomobject-class.md) w module do obsługi przypadków zagregowane i nieagregowane. Pojedynczy `CComPolyObject` obiekt obsługuje obie sprawy. Oznacza to, że tylko jedna kopia vtable i jedna kopia funkcji istnieje w module. Jeśli twój vtable jest duży, może to znacznie zmniejszyć rozmiar modułu. Jeśli jednak tabela vtable `CComPolyObject` jest mała, użycie może spowodować nieco większy rozmiar modułu, ponieważ nie jest `CComAggObject` zoptymalizowany pod kątem zagregowanego lub nieagregowanego obiektu, tak jak są i `CComObject`.

Jeśli makro DECLARE_POLY_AGGREGATABLE jest określone w definicji klasy `CComPolyObject` obiektu, zostanie użyte do utworzenia obiektu. DECLARE_POLY_AGGREGATABLE zostanie automatycznie zadeklarowana, jeśli do utworzenia pełnej kontroli lub formantu programu Internet Explorer zostanie użyty Kreator projektu ATL.

Jeśli zagregowane, `CComPolyObject` obiekt `IUnknown`ma swój własny , `IUnknown`oddzielony od obiektu zewnętrznego i zachowuje własną liczbę odwołań. `CComPolyObject`używa [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) do delegowania do zewnętrznej nieznanej.

Aby uzyskać więcej informacji na temat agregacji, zobacz artykuł [Podstawy obiektów COM ATL](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CComObjectRootBase`

[Ccomobjectrootex](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ccompolyobjectaddref"></a><a name="addref"></a>CComPolyObject::AddRef

Zwiększa liczbę odwołań do obiektu.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatna do diagnostyki lub testowania.

## <a name="ccompolyobjectccompolyobject"></a><a name="ccompolyobject"></a>CComPolyObject::CComPolyObject

Konstruktor.

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
[w] Wskaźnik do zewnętrznej nieznany, jeśli obiekt ma być agregowane lub NULL, jeśli obiekt, jeśli obiekt nie jest agregowany.

### <a name="remarks"></a>Uwagi

Inicjuje `CComContainedObject` element członkowski danych, [m_contained](#m_contained)i zwiększa liczbę blokad modułu.

Destruktor zmniejsza liczbę blokad modułu.

## <a name="ccompolyobjectccompolyobject"></a><a name="dtor"></a>CComPolyObject::~CComPolyObject

Destruktor.

```
~CComPolyObject();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby, wywołuje [FinalRelease](#finalrelease)i zmniejsza liczbę blokad modułu.

## <a name="ccompolyobjectcreateinstance"></a><a name="createinstance"></a>CComPolyObject::CreateInstance

Umożliwia utworzenie nowego **obiektu CComPolyObject<** `contained` **>** bez narzutu [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>Parametry

*S*<br/>
[na zewnątrz] Wskaźnik do **wskaźnika<CComPolyObject.** `contained` **>** Jeśli `CreateInstance` nie powiedzie się, *pp* jest ustawiona na wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Zwrócony obiekt ma liczbę odwołań `AddRef` zero, więc `Release` natychmiast wywołać, a następnie użyć do zwolnienia odwołania na wskaźnik obiektu po zakończeniu.

Jeśli nie potrzebujesz bezpośredniego dostępu do obiektu, ale nadal chcesz utworzyć nowy `CoCreateInstance`obiekt bez narzutu , użyj [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) zamiast tego.

## <a name="ccompolyobjectfinalconstruct"></a><a name="finalconstruct"></a>CComPolyObject::FinalConstruct

Wywoływana w końcowych etapach budowy obiektu, ta metoda wykonuje wszelkie końcowe inicjowanie na [m_contained](#m_contained) element członkowski danych.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="ccompolyobjectfinalrelease"></a><a name="finalrelease"></a>CComPolyObject::FinalRelease

Wywoływana podczas niszczenia obiektów, ta metoda zwalnia [m_contained](#m_contained) element członkowski danych.

```
void FinalRelease();
```

## <a name="ccompolyobjectm_contained"></a><a name="m_contained"></a>CComPolyObject::m_contained

A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) obiekt pochodzi z klasy.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Parametry

*Zawarte*<br/>
[w] Klasa, pochodzące z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również z innych interfejsów, które mają być obsługiwane na obiekcie.

### <a name="remarks"></a>Uwagi

`IUnknown`wywołania `m_contained` za pośrednictwem są delegowane do zewnętrznej nieznane, `IUnknown` jeśli obiekt jest agregowany lub do tego obiektu, jeśli obiekt nie jest agregowany.

## <a name="ccompolyobjectqueryinterface"></a><a name="queryinterface"></a>CComPolyObject::QueryInterface

Pobiera wskaźnik do żądanego interfejsu.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT QueryInterface(Q** pp);
```

### <a name="parameters"></a>Parametry

*P*<br/>
Interfejs COM.

*Iid*<br/>
[w] Identyfikator żądanego interfejsu.

*ppvObiekt*<br/>
[na zewnątrz] Wskaźnik do wskaźnika interfejsu identyfikowanego przez *iid*. Jeśli obiekt nie obsługuje tego interfejsu, *ppvObject* jest ustawiona na wartość NULL.

*S*<br/>
[na zewnątrz] Wskaźnik do interfejsu identyfikowany przez `__uuidof(Q)`.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Dla obiektu zagregowanego, jeśli żądany interfejs jest `IUnknown`, `QueryInterface` zwraca wskaźnik `IUnknown` do zagregowanego obiektu własnego i zwiększa liczbę odwołań. W przeciwnym razie ta metoda kwerendy dla interfejsu za pośrednictwem elementu członkowskiego `CComContainedObject` danych, [m_contained](#m_contained).

## <a name="ccompolyobjectrelease"></a><a name="release"></a>CComPolyObject::Release CComPolyObject::Release CComPolyObject::Release CCom

Zmniejsza liczbę odwołań na obiekcie.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Wartość zwracana

W kompilacjach debugowania zwraca wartość, `Release` która może być przydatna do diagnostyki lub testowania. W kompilacjach nondebug `Release` zawsze zwraca wartość 0.

## <a name="see-also"></a>Zobacz też

[Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
