---
title: Klasa CComContainedObject | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComContainedObject
- ATLCOM/ATL::CComContainedObject
- ATLCOM/ATL::CComContainedObject::CComContainedObject
- ATLCOM/ATL::CComContainedObject::AddRef
- ATLCOM/ATL::CComContainedObject::GetControllingUnknown
- ATLCOM/ATL::CComContainedObject::QueryInterface
- ATLCOM/ATL::CComContainedObject::Release
dev_langs:
- C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComContainedObject class
ms.assetid: e8616b41-c200-47b8-bf2c-fb9f713ebdad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f38fc3499ecc5956369a78c37f94358a1006cc2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108693"
---
# <a name="ccomcontainedobject-class"></a>Klasa CComContainedObject

Ta klasa implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) przez delegowanie do obiektu właściciela `IUnknown`.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template<class Base>
class CComContainedObject : public Base
```

#### <a name="parameters"></a>Parametry

*podstawowy*<br/>
Z klasą pochodną [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|Konstruktor. Inicjuje element członkowski wskaźnik do obiektu właściciela `IUnknown`.|
|[CComContainedObject:: ~ CComContainedObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComContainedObject::AddRef](#addref)|Zwiększa liczbę odwołań dla obiektu właściciela.|
|[CComContainedObject::GetControllingUnknown](#getcontrollingunknown)|Pobiera obiekt właściciela `IUnknown`.|
|[CComContainedObject::QueryInterface](#queryinterface)|Pobiera wskaźnik do interfejsu zażądana obiekt właściciela.|
|[CComContainedObject::Release](#release)|Dekrementuje liczbę odwołań dla obiektu właściciela.|

## <a name="remarks"></a>Uwagi

Używa ATL `CComContainedObject` w klasach [CComAggObject](../../atl/reference/ccomaggobject-class.md), [CComPolyObject](../../atl/reference/ccompolyobject-class.md), i [CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md). `CComContainedObject` implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) przez delegowanie do obiektu właściciela `IUnknown`. (Właściciel jest zewnętrzny obiekt agregacji lub obiekt, dla którego jest tworzony interfejs odrywania). `CComContainedObject` wywołania `CComObjectRootEx`firmy `OuterQueryInterface`, `OuterAddRef`, i `OuterRelease`, wszystkie odziedziczone za pośrednictwem `Base`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Base`

`CComContainedObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="addref"></a>  CComContainedObject::AddRef

Zwiększa liczbę odwołań dla obiektu właściciela.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być użyteczna, diagnostykę lub testowania.

##  <a name="ccomcontainedobject"></a>  CComContainedObject::CComContainedObject

Konstruktor.

```
CComContainedObject(void* pv);
```

### <a name="parameters"></a>Parametry

*Wa*<br/>
[in] Obiekt właściciela `IUnknown`.

### <a name="remarks"></a>Uwagi

Zestawy `m_pOuterUnknown` wskaźnika elementu członkowskiego (dziedziczone `Base` klasy) do *pv*.

##  <a name="dtor"></a>  CComContainedObject:: ~ CComContainedObject

Destruktor.

```
~CComContainedObject();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby.

##  <a name="getcontrollingunknown"></a>  CComContainedObject::GetControllingUnknown

Zwraca `m_pOuterUnknown` wskaźnika elementu członkowskiego (dziedziczone *Base* klasy) zawierający obiekt właściciela `IUnknown`.

```
IUnknown* GetControllingUnknown();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt właściciela `IUnknown`.

### <a name="remarks"></a>Uwagi

Ta metoda może być wirtualny Jeśli `Base` zadeklarował [DECLARE_GET_CONTROLLING_UNKNOWN](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown) makra.

##  <a name="queryinterface"></a>  CComContainedObject::QueryInterface

Pobiera wskaźnik do interfejsu zażądana obiekt właściciela.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>Parametry

*IID*<br/>
[in] Identyfikator interfejsu żądanej.

*ppvObject*<br/>
[out] Wskaźnik do wskaźnika interfejsu identyfikowane przez *iid*. Jeśli obiekt nie obsługuje ten interfejs *ppvObject* ma wartość NULL.

*strony*<br/>
[out] Wskaźnik do wskaźnika interfejsu identyfikowanych według typu `Q`. Jeśli obiekt nie obsługuje ten interfejs *pp* ma wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="release"></a>  CComContainedObject::Release

Dekrementuje liczbę odwołań dla obiektu właściciela.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Wartość zwracana

W kompilacjach do debugowania `Release` zwraca wartość, która może być użyteczna, diagnostykę lub testowania. W kompilacjach nieprzeznaczonych do debugowania `Release` zawsze zwraca wartość 0.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)
