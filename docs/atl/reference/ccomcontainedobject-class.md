---
title: CComContainedObject, klasa
ms.date: 11/04/2016
f1_keywords:
- CComContainedObject
- ATLCOM/ATL::CComContainedObject
- ATLCOM/ATL::CComContainedObject::CComContainedObject
- ATLCOM/ATL::CComContainedObject::AddRef
- ATLCOM/ATL::CComContainedObject::GetControllingUnknown
- ATLCOM/ATL::CComContainedObject::QueryInterface
- ATLCOM/ATL::CComContainedObject::Release
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComContainedObject class
ms.assetid: e8616b41-c200-47b8-bf2c-fb9f713ebdad
ms.openlocfilehash: 72ba27c3be6576621995ffb8c98995c6abc9324c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320794"
---
# <a name="ccomcontainedobject-class"></a>CComContainedObject, klasa

Ta klasa implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) przez delegowanie `IUnknown`do obiektu właściciela .

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class Base>
class CComContainedObject : public Base
```

#### <a name="parameters"></a>Parametry

*Podstawowej*<br/>
Twoja klasa, pochodząca z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|Konstruktor. Inicjuje wskaźnik elementu członkowskiego do `IUnknown`obiektu właściciela .|
|[CComContainedObject::~CComContainedObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComContainedObject::AddRef](#addref)|Zwiększa liczbę odwołań na obiekt właściciela.|
|[CComContainedObject::GetControllingUnknown CComContainedObject::GetControllingUnknown CComContainedObject::GetControllingUnknown CCom](#getcontrollingunknown)|Pobiera obiekt właściciela `IUnknown`.|
|[CComContainedObject::QueryInterface](#queryinterface)|Pobiera wskaźnik do interfejsu żądanego w obiekcie właściciela.|
|[CComContainedObject::Release CComContainedObject::Release CComContainedObject::Release CCom](#release)|Zmniejsza liczbę odwołań dla obiektu właściciela.|

## <a name="remarks"></a>Uwagi

ATL używa `CComContainedObject` w klasach [CComAggObject](../../atl/reference/ccomaggobject-class.md), [CComPolyObject](../../atl/reference/ccompolyobject-class.md)i [CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md). `CComContainedObject`implementuje [IUnknown,](/windows/win32/api/unknwn/nn-unknwn-iunknown) delegując do `IUnknown`obiektu właściciela . (Właściciel jest zewnętrznym obiektem agregacji lub obiektem, dla którego tworzony jest interfejs odrywany). `CComContainedObject` połączenia `CComObjectRootEx`, `OuterQueryInterface` `OuterAddRef`i `OuterRelease`, wszystkie odziedziczone przez `Base`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Base`

`CComContainedObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ccomcontainedobjectaddref"></a><a name="addref"></a>CComContainedObject::AddRef

Zwiększa liczbę odwołań na obiekt właściciela.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatna do diagnostyki lub testowania.

## <a name="ccomcontainedobjectccomcontainedobject"></a><a name="ccomcontainedobject"></a>CComContainedObject::CComContainedObject

Konstruktor.

```
CComContainedObject(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
[w] Obiekt właściciela `IUnknown`.

### <a name="remarks"></a>Uwagi

Ustawia `m_pOuterUnknown` wskaźnik elementu członkowskiego (dziedziczone przez `Base` klasę) do *pv*.

## <a name="ccomcontainedobjectccomcontainedobject"></a><a name="dtor"></a>CComContainedObject::~CComContainedObject

Destruktor.

```
~CComContainedObject();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby.

## <a name="ccomcontainedobjectgetcontrollingunknown"></a><a name="getcontrollingunknown"></a>CComContainedObject::GetControllingUnknown CComContainedObject::GetControllingUnknown CComContainedObject::GetControllingUnknown CCom

Zwraca `m_pOuterUnknown` wskaźnik elementu członkowskiego (dziedziczony przez *klasę Podstawową),* który zawiera obiekt właściciela `IUnknown`.

```
IUnknown* GetControllingUnknown();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt właściciela `IUnknown`.

### <a name="remarks"></a>Uwagi

Ta metoda może `Base` być wirtualna, jeśli zadeklarowane [makra DECLARE_GET_CONTROLLING_UNKNOWN.](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown)

## <a name="ccomcontainedobjectqueryinterface"></a><a name="queryinterface"></a>CComContainedObject::QueryInterface

Pobiera wskaźnik do interfejsu żądanego w obiekcie właściciela.

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

## <a name="ccomcontainedobjectrelease"></a><a name="release"></a>CComContainedObject::Release CComContainedObject::Release CComContainedObject::Release CCom

Zmniejsza liczbę odwołań dla obiektu właściciela.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Wartość zwracana

W kompilacjach debugowania zwraca wartość, `Release` która może być przydatna do diagnostyki lub testowania. W kompilacjach innych niż `Release` debugowanie zawsze zwraca wartość 0.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
