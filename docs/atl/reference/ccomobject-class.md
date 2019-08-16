---
title: Klasa CComObject
ms.date: 11/04/2016
f1_keywords:
- CComObject
- ATLCOM/ATL::CComObject
- ATLCOM/ATL::CComObject::CComObject
- ATLCOM/ATL::CComObject::AddRef
- ATLCOM/ATL::CComObject::CreateInstance
- ATLCOM/ATL::CComObject::QueryInterface
- ATLCOM/ATL::CComObject::Release
helpviewer_keywords:
- CComObject class
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
ms.openlocfilehash: a2051932413d8658eb7cedb67ed0eab2077b599d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497131"
---
# <a name="ccomobject-class"></a>Klasa CComObject

Ta klasa implementuje `IUnknown` dla niezagregowanego obiektu.

## <a name="syntax"></a>Składnia

```
template<class Base>
class CComObject : public Base
```

#### <a name="parameters"></a>Parametry

*Opiera*<br/>
Klasa, pochodząca z [klasy CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), a także z innych interfejsów, które mają być obsługiwane w obiekcie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComObject::CComObject](#ccomobject)|Konstruktor.|
|[CComObject::~CComObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComObject::AddRef](#addref)|Zwiększa liczbę odwołań do obiektu.|
|[CComObject::CreateInstance](#createinstance)|Ruchom Tworzy nowy `CComObject` obiekt.|
|[CComObject::QueryInterface](#queryinterface)|Pobiera wskaźnik do żądanego interfejsu.|
|[CComObject::Release](#release)|Zmniejsza liczbę odwołań do obiektu.|

## <a name="remarks"></a>Uwagi

`CComObject`implementuje [interfejs IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) dla niezagregowanego obiektu. Jednak wywołania do `QueryInterface`, `AddRef`i `Release` są delegowane do `CComObjectRootEx`.

Aby uzyskać więcej informacji o `CComObject`używaniu programu, zobacz artykuł [podstawowe elementy ATL com](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Base`

`CComObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="addref"></a>CComObject:: AddRef

Zwiększa liczbę odwołań do obiektu.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Wartość zwracana

Ta funkcja zwraca nowy przyrostowy licznik odwołań dla obiektu. Ta wartość może być przydatna w przypadku diagnostyki lub testowania.

##  <a name="ccomobject"></a>CComObject::CComObject

Konstruktor zwiększa liczbę blokad modułu.

```
CComObject(void* = NULL);
```

### <a name="parameters"></a>Parametry

<em>pozycję\*</em><br/>
podczas Ten parametr bez nazwy nie jest używany. Istnieje dla symetrii z innymi `CComXXXObjectXXX` konstruktorami.

### <a name="remarks"></a>Uwagi

Destruktor zmniejsza go.

Jeśli obiekt pochodny został pomyślnie skonstruowany przy użyciu operatora new, początkowa liczba odwołań wynosi 0. `CComObject` Aby ustawić liczbę odwołań na poprawną wartość (1), należy wywołać funkcję [AddRef](#addref) .

##  <a name="dtor"></a>  CComObject::~CComObject

Destruktor.

```
CComObject();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzieloną zasoby, wywołuje [FinalRelease](ccomobjectrootex-class.md#finalrelease)i zmniejsza liczbę blokad modułu.

##  <a name="createinstance"></a>CComObject:: CreateInstance

Ta funkcja statyczna pozwala utworzyć nowy obiekt **<** `Base` **>** CComObject bez narzutu na polecenie [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```

### <a name="parameters"></a>Parametry

*miesięcznie*<br/>
określoną Wskaźnik do CComObjectego wskaźnika **<** `Base` **>** . Jeśli `CreateInstance` to się nie powiedzie, *PP* ma ustawioną wartość null.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Zwrócony obiekt ma liczbę odwołań równą zero, więc Wywołaj `AddRef` natychmiast, a następnie `Release` Użyj, aby zwolnić odwołanie na wskaźniku obiektu po zakończeniu.

Jeśli nie potrzebujesz bezpośredniego dostępu do obiektu, ale nadal chcesz utworzyć nowy obiekt bez nakładu pracy `CoCreateInstance`, zamiast tego użyj [CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]

[!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]

##  <a name="queryinterface"></a>CComObject:: QueryInterface

Pobiera wskaźnik do żądanego interfejsu.

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

##  <a name="release"></a>CComObject:: Release

Zmniejsza liczbę odwołań do obiektu.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Wartość zwracana

Ta funkcja zwraca nową, zmniejszoną liczbę odwołań do obiektu. W kompilacjach debugowania wartość zwracana może być przydatna w przypadku diagnostyki lub testowania. W kompilacjach `Release` niedebugowanych zawsze zwraca wartość 0.

## <a name="see-also"></a>Zobacz także

[Klasa CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Klasa CComPolyObject](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
