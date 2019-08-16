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
ms.openlocfilehash: deed29b5fb80ea8bbd06b3d50f45e38740b1619f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497152"
---
# <a name="ccompolyobject-class"></a>Klasa CComPolyObject

Ta klasa implementuje `IUnknown` obiekt zagregowany lub niezagregowany.

## <a name="syntax"></a>Składnia

```
template<class contained>
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parametry

*przechowywany*<br/>
Klasa, pochodząca z [klasy CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), a także z innych interfejsów, które mają być obsługiwane w obiekcie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComPolyObject::CComPolyObject](#ccompolyobject)|Konstruktor.|
|[CComPolyObject::~CComPolyObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComPolyObject:: AddRef](#addref)|Zwiększa liczbę odwołań obiektu.|
|[CComPolyObject:: CreateInstance](#createinstance)|Ruchom Umożliwia utworzenie nowego obiektu **<** `contained` **>** CComPolyObject bez nakładu pracy funkcji [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComPolyObject::FinalConstruct](#finalconstruct)|Wykonuje ostateczną inicjalizację `m_contained`.|
|[CComPolyObject:: FinalRelease](#finalrelease)|Wykonuje ostateczne zniszczenie `m_contained`.|
|[CComPolyObject:: QueryInterface](#queryinterface)|Pobiera wskaźnik do żądanego interfejsu.|
|[CComPolyObject::Release](#release)|Zmniejsza liczbę odwołań obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComPolyObject:: m_contained](#m_contained)|Deleguje `IUnknown` wywołania do `IUnknown` elementu zewnętrznego nieznane, jeśli obiekt jest agregowany lub do obiektu, jeśli obiekt nie jest agregowany.|

## <a name="remarks"></a>Uwagi

`CComPolyObject`implementuje [interfejs IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) dla zagregowanego lub niezagregowanego obiektu.

Po utworzeniu wystąpienia elementu `CComPolyObject` jest sprawdzana wartość nieznanego elementu zewnętrznego. Jeśli ma wartość null, `IUnknown` jest zaimplementowana dla niezagregowanego obiektu. Jeśli nieznana zewnętrzna nie ma wartości null `IUnknown` , jest zaimplementowana dla obiektu agregowanego.

Zaletą korzystania `CComPolyObject` z programu jest uniknięcie, że zarówno [CComAggObject](../../atl/reference/ccomaggobject-class.md) , jak i [CComObject](../../atl/reference/ccomobject-class.md) w module służą do obsługi zagregowanych i niezagregowanych przypadków. Pojedynczy `CComPolyObject` obiekt obsługuje oba przypadki. Oznacza to, że w module istnieją tylko jedną kopię tabeli metod wirtualnych i jedną kopię funkcji. W przypadku dużej liczby tablic wirtualnych może to znacznie zmniejszyć rozmiar modułu. Jeśli jednak tablica tablicowa jest mała, użycie `CComPolyObject` może spowodować nieco większy rozmiar modułu, ponieważ nie jest zoptymalizowany pod kątem zagregowanych lub niezagregowanych obiektów, ponieważ są `CComAggObject` i `CComObject`.

Jeśli makro DECLARE_POLY_AGGREGATABLE jest określone w definicji klasy obiektu, `CComPolyObject` zostanie użyte do utworzenia obiektu. DECLARE_POLY_AGGREGATABLE zostanie automatycznie zadeklarowany, jeśli używasz Kreatora projektu ATL do tworzenia kontrolki Pełna kontrola lub programu Internet Explorer.

Jeśli agregowany, `CComPolyObject` obiekt jest własny `IUnknown`, oddzielony `IUnknown`od obiektu zewnętrznego i utrzymuje swój własny licznik odwołań. `CComPolyObject`używa [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) do delegowania do nieznanego zewnętrznego.

Aby uzyskać więcej informacji na temat agregacji, zapoznaj się z artykułem [podstawy obiektów ATL com](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="addref"></a>CComPolyObject:: AddRef

Zwiększa liczbę odwołań do obiektu.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatna w przypadku diagnostyki lub testowania.

##  <a name="ccompolyobject"></a>  CComPolyObject::CComPolyObject

Konstruktor.

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>Parametry

*wa*<br/>
podczas Wskaźnik do elementu zewnętrznego nieznany, jeśli obiekt ma być zagregowany, lub wartość NULL, jeśli obiekt nie jest agregowany.

### <a name="remarks"></a>Uwagi

Inicjuje element członkowski [](#m_contained) danych,m_containedizwiększaliczbęblokad`CComContainedObject` modułu.

Destruktor zmniejsza liczbę blokad modułu.

##  <a name="dtor"></a>  CComPolyObject::~CComPolyObject

Destruktor.

```
~CComPolyObject();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzieloną zasoby, wywołuje [FinalRelease](#finalrelease)i zmniejsza liczbę blokad modułu.

##  <a name="createinstance"></a>CComPolyObject:: CreateInstance

Umożliwia utworzenie nowego obiektu **<** `contained` **>** CComPolyObject bez nakładu pracy funkcji [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>Parametry

*miesięcznie*<br/>
określoną Wskaźnik do CComPolyObjectego wskaźnika **<** `contained` **>** . Jeśli `CreateInstance` to się nie powiedzie, *PP* ma ustawioną wartość null.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Zwrócony obiekt ma liczbę odwołań równą zero, więc Wywołaj `AddRef` natychmiast, a następnie `Release` Użyj, aby zwolnić odwołanie na wskaźniku obiektu po zakończeniu.

Jeśli nie potrzebujesz bezpośredniego dostępu do obiektu, ale nadal chcesz utworzyć nowy obiekt bez nakładu pracy `CoCreateInstance`, zamiast tego użyj [CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) .

##  <a name="finalconstruct"></a>  CComPolyObject::FinalConstruct

Wywoływana podczas końcowych etapów konstruowania obiektu, ta metoda wykonuje wszelkie końcowe inicjalizacje elementu członkowskiego danych [m_contained](#m_contained) .

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

##  <a name="finalrelease"></a>CComPolyObject:: FinalRelease

Wywoływana podczas niszczenia obiektu, ta metoda zwalnia element członkowski danych [m_contained](#m_contained) .

```
void FinalRelease();
```

##  <a name="m_contained"></a>CComPolyObject:: m_contained

Obiekt [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) pochodzący od klasy.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Parametry

*przechowywany*<br/>
podczas Klasa, pochodząca z [klasy CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), a także z innych interfejsów, które mają być obsługiwane w obiekcie.

### <a name="remarks"></a>Uwagi

`IUnknown`wywołania przez `m_contained` są delegowane do `IUnknown` elementu zewnętrznego nieznanego, jeśli obiekt jest agregowany lub do tego obiektu, jeśli obiekt nie jest zagregowany.

##  <a name="queryinterface"></a>CComPolyObject:: QueryInterface

Pobiera wskaźnik do żądanego interfejsu.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT QueryInterface(Q** pp);
```

### <a name="parameters"></a>Parametry

*PYTANIA*<br/>
Interfejs COM.

*IID*<br/>
podczas Identyfikator żądanego interfejsu.

*ppvObject*<br/>
określoną Wskaźnik do wskaźnika interfejsu identyfikowanego przez *Identyfikator IID*. Jeśli obiekt nie obsługuje tego interfejsu, *ppvObject* ma wartość null.

*miesięcznie*<br/>
określoną Wskaźnik do interfejsu identyfikowanego przez `__uuidof(Q)`.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

W przypadku obiektu agregowanego, jeśli żądany interfejs to `IUnknown`, `QueryInterface` zwraca wskaźnik do własnego `IUnknown` obiektu zagregowanego i zwiększa liczbę odwołań. W przeciwnym razie ta metoda wysyła zapytanie do interfejsu za `CComContainedObject` pomocą elementu członkowskiego danych [m_contained](#m_contained).

##  <a name="release"></a>CComPolyObject:: Release

Zmniejsza liczbę odwołań do obiektu.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Wartość zwracana

W kompilacjach `Release` debugowania zwraca wartość, która może być przydatna w przypadku diagnostyki lub testowania. W kompilacjach `Release` niedebugowanych zawsze zwraca wartość 0.

## <a name="see-also"></a>Zobacz także

[Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
