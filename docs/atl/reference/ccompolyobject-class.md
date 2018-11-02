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
ms.openlocfilehash: 9f84c022ac1dee34b6dca2931abb349eefb7d690
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495891"
---
# <a name="ccompolyobject-class"></a>Klasa CComPolyObject

Ta klasa implementuje `IUnknown` zagregowane lub nieagregowane w obiekcie.

## <a name="syntax"></a>Składnia

```
template<class contained>
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parametry

*zawiera*<br/>
Z klasą pochodną [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również od innych interfejsów, które chcesz obsługiwać obiektu.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComPolyObject::CComPolyObject](#ccompolyobject)|Konstruktor.|
|[CComPolyObject:: ~ CComPolyObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComPolyObject::AddRef](#addref)|Zwiększa licznik odwołań obiektu.|
|[CComPolyObject::CreateInstance](#createinstance)|(Statyczny) Służy do tworzenia nowego **CComPolyObject <** `contained` **>** obiektu bez konieczności [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComPolyObject::FinalConstruct](#finalconstruct)|Wykonuje końcowe inicjowanie `m_contained`.|
|[CComPolyObject::FinalRelease](#finalrelease)|Wykonuje końcowe zniszczenie `m_contained`.|
|[CComPolyObject::QueryInterface](#queryinterface)|Pobiera wskaźnik do żądanego interfejsu.|
|[CComPolyObject::Release](#release)|Dekrementuje liczbę odwołań obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComPolyObject::m_contained](#m_contained)|Delegaty `IUnknown` wywołuje zewnętrzne nieznany, jeśli obiekt jest zagregowany, lub aby `IUnknown` obiektu, jeśli obiekt nie jest agregowany.|

## <a name="remarks"></a>Uwagi

`CComPolyObject` implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) zagregowane lub nieagregowane w obiekcie.

Jeśli wystąpienie `CComPolyObject` utworzeniu wartość zewnętrzny zaznaczono opcję nieznane. Jeśli ma wartość NULL, `IUnknown` został zaimplementowany dla obiektu nieagregowane. Jeśli nieznany zewnętrzny nie ma wartość NULL, `IUnknown` został zaimplementowany dla obiektu zagregowanego.

Zaletą korzystania z `CComPolyObject` to uniknąć konieczności zarówno [CComAggObject](../../atl/reference/ccomaggobject-class.md) i [CComObject](../../atl/reference/ccomobject-class.md) w module sposób obsługiwać przypadki zagregowane i nieagregowane. Pojedynczy `CComPolyObject` obiektu obsługuje w obu przypadkach. Oznacza to, że tylko jedna kopia vtable i jedną kopię funkcje istnieją w module. Jeśli Twoje vtable jest duży, to znacznie zmniejszyć rozmiar modułu. Jednak jeśli Twoja vtable jest mały, za pomocą `CComPolyObject` może spowodować nieco większy rozmiar modułu, ponieważ nie jest zoptymalizowana do zagregowanych lub nieagregowane obiektu, ponieważ są `CComAggObject` i `CComObject`.

Jeśli makro DECLARE_POLY_AGGREGATABLE została określona w definicji klasy do obiektu, `CComPolyObject` będzie służyć do tworzenia obiektu. DECLARE_POLY_AGGREGATABLE automatycznie zostanie zadeklarowany, jeśli używasz Kreator projektów ATL do utworzenia Pełna kontrola lub sterowania w programie Internet Explorer.

Jeśli zagregowany, `CComPolyObject` obiekt ma swój własny `IUnknown`, niezależne od obiektu zewnętrznego `IUnknown`i przechowuje swoje własne licznika odwołań. `CComPolyObject` używa [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) delegować do zewnętrznego nieznany.

Aby uzyskać więcej informacji na temat agregacji, zobacz artykuł [podstawy ATL obiektów COM](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="addref"></a>  CComPolyObject::AddRef

Zwiększa liczbę odwołań do obiektu.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być użyteczna, diagnostykę lub testowania.

##  <a name="ccompolyobject"></a>  CComPolyObject::CComPolyObject

Konstruktor.

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>Parametry

*Wa*<br/>
[in] Wskaźnik do nieznanego zewnętrzne, jeśli obiekt jest agregowane, lub wartość NULL, jeśli obiekt, jeśli obiekt nie jest agregowany.

### <a name="remarks"></a>Uwagi

Inicjuje `CComContainedObject` element członkowski danych, [m_contained](#m_contained)i zwiększa liczbę blokad modułu.

Dekrementuje destruktor liczbę blokad modułu.

##  <a name="dtor"></a>  CComPolyObject:: ~ CComPolyObject

Destruktor.

```
~CComPolyObject();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby, wywołania [FinalRelease](#finalrelease), oraz liczbę blokad modułu zmniejsza.

##  <a name="createinstance"></a>  CComPolyObject::CreateInstance

Służy do tworzenia nowego **CComPolyObject <** `contained` **>** obiektu bez konieczności [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>Parametry

*strony*<br/>
[out] Wskaźnik do **CComPolyObject <** `contained` **>** wskaźnika. Jeśli `CreateInstance` zakończy się niepowodzeniem, *pp* ma wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Zwrócony obiekt ma liczebności referencyjnej równej zero, więc wywołanie `AddRef` natychmiast, następnie użyć `Release` zwolnienie odwołania na wskaźnik do obiektu, gdy wszystko będzie gotowe.

Jeśli nie potrzebujesz bezpośredni dostęp do obiektu, ale mimo to chcesz utworzyć nowy obiekt bez konieczności `CoCreateInstance`, użyj [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) zamiast tego.

##  <a name="finalconstruct"></a>  CComPolyObject::FinalConstruct

Wywołuje się w końcowym etapie konstrukcji obiektu, ta metoda wykonuje końcowe inicjowanie na [m_contained](#m_contained) element członkowski danych.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="finalrelease"></a>  CComPolyObject::FinalRelease

Wywoływana podczas niszczenia obiektu, ta metoda zwalnia [m_contained](#m_contained) element członkowski danych.

```
void FinalRelease();
```

##  <a name="m_contained"></a>  CComPolyObject::m_contained

A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) obiekt pochodzi od klasy.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Parametry

*zawiera*<br/>
[in] Z klasą pochodną [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również od innych interfejsów, które chcesz obsługiwać obiektu.

### <a name="remarks"></a>Uwagi

`IUnknown` połączenia za pośrednictwem `m_contained` są delegowane do zewnętrznego nieznany, jeśli obiekt jest zagregowany, lub do `IUnknown` tego obiektu, jeśli obiekt nie jest agregowany.

##  <a name="queryinterface"></a>  CComPolyObject::QueryInterface

Pobiera wskaźnik do żądanego interfejsu.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT QueryInterface(Q** pp);
```

### <a name="parameters"></a>Parametry

*PYTANIA I ODPOWIEDZI*<br/>
Interfejs COM.

*IID*<br/>
[in] Identyfikator interfejsu żądanej.

*ppvObject*<br/>
[out] Wskaźnik do wskaźnika interfejsu identyfikowane przez *iid*. Jeśli obiekt nie obsługuje ten interfejs *ppvObject* ma wartość NULL.

*strony*<br/>
[out] Wskaźnik do interfejsu identyfikowane przez `__uuidof(Q)`.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Zagregowane obiektu, jeśli jest żądany interfejs `IUnknown`, `QueryInterface` zwraca wskaźnik do zagregowanych obiektu własnych `IUnknown` i zwiększa liczbę odwołań. W przeciwnym razie ta metoda wysyła zapytanie o interfejs, za pomocą `CComContainedObject` element członkowski danych, [m_contained](#m_contained).

##  <a name="release"></a>  CComPolyObject::Release

Dekrementuje liczbę odwołań do obiektu.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Wartość zwracana

W kompilacjach do debugowania `Release` zwraca wartość, która może być użyteczna, diagnostykę lub testowania. W kompilacjach nondebug `Release` zawsze zwraca wartość 0.

## <a name="see-also"></a>Zobacz też

[Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
