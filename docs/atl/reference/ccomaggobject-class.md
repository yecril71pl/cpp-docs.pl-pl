---
title: Klasa CComAggObject | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComAggObject class
ms.assetid: 7aa90d69-d399-477b-880d-e2cdf0ef7881
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76a85b840aba9d52600b3cf730eada0e8095eb98
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43756327"
---
# <a name="ccomaggobject-class"></a>Klasa CComAggObject

Ta klasa implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) interfejs dla obiektu zagregowanego. Zgodnie z definicją obiektu zagregowanego jest zawarty w obiekcie zewnętrznym. `CComAggObject` Klasa jest podobna do [klasa CComObject](../../atl/reference/ccomobject-class.md), z tą różnicą, że udostępnia interfejs, który jest bezpośrednio dostępny dla klientów zewnętrznych.

## <a name="syntax"></a>Składnia

```
template<class contained>  
class CComAggObject : public IUnknown, 
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parametry

*zawiera*  
Z klasą pochodną [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również od innych interfejsów, które chcesz obsługiwać obiektu.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComAggObject::CComAggObject](#ccomaggobject)|Konstruktor.|
|[CComAggObject:: ~ CComAggObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComAggObject::AddRef](#addref)|Zwiększa licznik odwołań obiektu zagregowanego.|
|[CComAggObject::CreateInstance](#createinstance)|Ta funkcja statyczna służy do tworzenia nowego **CComAggObject <** `contained` **>** obiektu bez konieczności [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComAggObject::FinalConstruct](#finalconstruct)|Wykonuje końcowe inicjowanie `m_contained`.|
|[CComAggObject::FinalRelease](#finalrelease)|Wykonuje końcowe zniszczenie `m_contained`.|
|[CComAggObject::QueryInterface](#queryinterface)|Pobiera wskaźnik do żądanego interfejsu.|
|[CComAggObject::Release](#release)|Dekrementuje liczbę odwołań w obiekcie zagregowane.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComAggObject::m_contained](#m_contained)|Delegaty `IUnknown` wywołania zewnętrznego nieznany.|

## <a name="remarks"></a>Uwagi

`CComAggObject` implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) dla obiektu zagregowanego. `CComAggObject` ma swój własny `IUnknown` interfejs, niezależnie od obiektu zewnętrznego `IUnknown` interfejs i przechowuje swoje własne licznika odwołań.

Aby uzyskać więcej informacji na temat agregacji, zobacz artykuł [podstawy ATL obiektów COM](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComAggObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="addref"></a>  CComAggObject::AddRef

Zwiększa licznik odwołań obiektu zagregowanego.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być użyteczna, diagnostykę lub testowania.

##  <a name="ccomaggobject"></a>  CComAggObject::CComAggObject

Konstruktor.

```
CComAggObject(void* pv);
```

### <a name="parameters"></a>Parametry

*Wa*  
[in] Nieznany zewnętrznego.

### <a name="remarks"></a>Uwagi

Inicjuje `CComContainedObject` elementu członkowskiego, [m_contained](#m_contained)i zwiększa liczbę blokad modułu.

Dekrementuje destruktor liczbę blokad modułu.

##  <a name="dtor"></a>  CComAggObject:: ~ CComAggObject

Destruktor.

```
~CComAggObject();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby, wywołania [FinalRelease](#finalrelease), oraz liczbę blokad modułu zmniejsza.

##  <a name="createinstance"></a>  CComAggObject::CreateInstance

Ta funkcja statyczna służy do tworzenia nowego **CComAggObject <** `contained` **>** obiektu bez konieczności [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```

### <a name="parameters"></a>Parametry

*strony*  
[out] Wskaźnik do **CComAggObject\<**<em>zawarte</em> **>** wskaźnika. Jeśli `CreateInstance` zakończy się niepowodzeniem, *pp* ma wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Zwrócony obiekt ma liczebności referencyjnej równej zero, więc wywołanie `AddRef` natychmiast, następnie użyć `Release` zwolnienie odwołania na wskaźnik do obiektu, gdy wszystko będzie gotowe.

Jeśli nie potrzebujesz bezpośredni dostęp do obiektu, ale mimo to chcesz utworzyć nowy obiekt bez konieczności `CoCreateInstance`, użyj [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) zamiast tego.

##  <a name="finalconstruct"></a>  CComAggObject::FinalConstruct

Wywołuje się w końcowym etapie konstrukcji obiektu, ta metoda wykonuje końcowe inicjowanie na [m_contained](#m_contained) elementu członkowskiego.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="finalrelease"></a>  CComAggObject::FinalRelease

Wywoływana podczas niszczenia obiektu, ta metoda zwalnia [m_contained](#m_contained) elementu członkowskiego.

```
void FinalRelease();
```

##  <a name="m_contained"></a>  CComAggObject::m_contained

A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) obiekt pochodzi od klasy.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Parametry

*zawiera*  
[in] Z klasą pochodną [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również od innych interfejsów, które chcesz obsługiwać obiektu.

### <a name="remarks"></a>Uwagi

Wszystkie `IUnknown` połączenia za pośrednictwem `m_contained` są delegowane do zewnętrznego nieznany.

##  <a name="queryinterface"></a>  CComAggObject::QueryInterface

Pobiera wskaźnik do żądanego interfejsu.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>Parametry

*IID*  
[in] Identyfikator interfejsu żądanej.

*ppvObject*  
[out] Wskaźnik do wskaźnika interfejsu identyfikowane przez *iid*. Jeśli obiekt nie obsługuje ten interfejs *ppvObject* ma wartość NULL.

*strony*  
[out] Wskaźnik do wskaźnika interfejsu identyfikowanych według typu `Q`. Jeśli obiekt nie obsługuje ten interfejs *pp* ma wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli jest żądany interfejs `IUnknown`, `QueryInterface` zwraca wskaźnik do zagregowanych obiektu własnych `IUnknown` i zwiększa liczbę odwołań. W przeciwnym razie ta metoda wysyła zapytanie o interfejs, za pomocą `CComContainedObject` elementu członkowskiego, [m_contained](#m_contained).

##  <a name="release"></a>  CComAggObject::Release

Dekrementuje liczbę odwołań w obiekcie zagregowane.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Wartość zwracana

W kompilacjach do debugowania `Release` zwraca wartość, która może być użyteczna, diagnostykę lub testowania. W kompilacjach nieprzeznaczonych do debugowania `Release` zawsze zwraca wartość 0.

## <a name="see-also"></a>Zobacz też

[Klasa CComObject](../../atl/reference/ccomobject-class.md)   
[Klasa CComPolyObject](../../atl/reference/ccompolyobject-class.md)   
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)   
[DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)   
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)   
[Klasa — Przegląd](../../atl/atl-class-overview.md)
