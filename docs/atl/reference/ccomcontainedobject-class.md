---
title: Klasa CComContainedObject
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
ms.openlocfilehash: c5e2fa64cc0938e632a37eac7dd1d6e9111c3d98
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497320"
---
# <a name="ccomcontainedobject-class"></a>Klasa CComContainedObject

Ta klasa implementuje [interfejs IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) przez delegowanie do obiektu `IUnknown`właściciela.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class Base>
class CComContainedObject : public Base
```

#### <a name="parameters"></a>Parametry

*Opiera*<br/>
Klasa, która pochodzi od [klasy CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|Konstruktor. Inicjuje wskaźnik elementu członkowskiego do obiektu `IUnknown`właściciela.|
|[CComContainedObject:: ~ CComContainedObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComContainedObject:: AddRef](#addref)|Zwiększa liczbę odwołań do obiektu właściciela.|
|[CComContainedObject::GetControllingUnknown](#getcontrollingunknown)|Pobiera obiekt `IUnknown`Owner.|
|[CComContainedObject:: QueryInterface](#queryinterface)|Pobiera wskaźnik do interfejsu żądanego w obiekcie Owner.|
|[CComContainedObject:: Release](#release)|Zmniejsza liczbę odwołań do obiektu właściciela.|

## <a name="remarks"></a>Uwagi

Użycie `CComContainedObject` ATL w klasach [CComAggObject](../../atl/reference/ccomaggobject-class.md), [CComPolyObject](../../atl/reference/ccompolyobject-class.md)i [CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md). `CComContainedObject`implementuje [interfejs IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) przez delegowanie do obiektu `IUnknown`właściciela. (Właściciel jest obiektem zewnętrznym agregacji lub obiektem, dla którego tworzony jest interfejs odrywający). `CComContainedObject` wywołania`CComObjectRootEx`, ,i`OuterRelease`, wszystkie Odziedziczone przez .`Base` `OuterQueryInterface` `OuterAddRef`

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Base`

`CComContainedObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="addref"></a>CComContainedObject:: AddRef

Zwiększa liczbę odwołań do obiektu właściciela.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatna w przypadku diagnostyki lub testowania.

##  <a name="ccomcontainedobject"></a>CComContainedObject::CComContainedObject

Konstruktor.

```
CComContainedObject(void* pv);
```

### <a name="parameters"></a>Parametry

*wa*<br/>
podczas Obiekt `IUnknown`Owner.

### <a name="remarks"></a>Uwagi

Ustawia wskaźnik `Base` elementu członkowskiego (Dziedziczony przez klasę) na *WB.* `m_pOuterUnknown`

##  <a name="dtor"></a>CComContainedObject:: ~ CComContainedObject

Destruktor.

```
~CComContainedObject();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzieloną zasoby.

##  <a name="getcontrollingunknown"></a>CComContainedObject::GetControllingUnknown

Zwraca wskaźnik `IUnknown`elementu członkowskiego (Dziedziczony przez klasę bazową), który zawiera obiekt Owner. `m_pOuterUnknown`

```
IUnknown* GetControllingUnknown();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt `IUnknown`Owner.

### <a name="remarks"></a>Uwagi

Ta metoda może być wirtualna, `Base` Jeśli zadeklaruje makro [DECLARE_GET_CONTROLLING_UNKNOWN](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown) .

##  <a name="queryinterface"></a>CComContainedObject:: QueryInterface

Pobiera wskaźnik do interfejsu żądanego w obiekcie Owner.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>Parametry

*IID*<br/>
podczas Identyfikator żądanego interfejsu.

*ppvObject*<br/>
określoną Wskaźnik do wskaźnika interfejsu identyfikowanego przez *Identyfikator IID*. Jeśli obiekt nie obsługuje tego interfejsu, *ppvObject* ma wartość null.

*miesięcznie*<br/>
określoną Wskaźnik do wskaźnika interfejsu identyfikowanego przez typ `Q`. Jeśli obiekt nie obsługuje tego interfejsu, ma ustawioną wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

##  <a name="release"></a>CComContainedObject:: Release

Zmniejsza liczbę odwołań do obiektu właściciela.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Wartość zwracana

W kompilacjach `Release` debugowania zwraca wartość, która może być przydatna w przypadku diagnostyki lub testowania. W kompilacjach `Release` niedebugowanych zawsze zwraca wartość 0.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
