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
ms.openlocfilehash: de6ffb45fe5c6f73ab656d5c6185b70d9f5edd38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327641"
---
# <a name="ccomobject-class"></a>Klasa CComObject

Ta klasa `IUnknown` implementuje dla obiektu nieagregowanego.

## <a name="syntax"></a>Składnia

```
template<class Base>
class CComObject : public Base
```

#### <a name="parameters"></a>Parametry

*Podstawowej*<br/>
Klasa, pochodzące z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również z innych interfejsów, które mają być obsługiwane na obiekcie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComObject::CComObject](#ccomobject)|Konstruktor.|
|[CComObject::~CComObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComObject::Odnośnik](#addref)|Zwiększa liczbę odwołań do obiektu.|
|[CComObject::CreateInstance](#createinstance)|(Statyczne) Tworzy nowy `CComObject` obiekt.|
|[CComObject::QueryInterface](#queryinterface)|Pobiera wskaźnik do żądanego interfejsu.|
|[CComObject::Release CComObject::Release CComObject::Release CCom](#release)|Zmniejsza liczbę odwołań na obiekcie.|

## <a name="remarks"></a>Uwagi

`CComObject`implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) dla obiektu nieagregowanego. Jednak wywołania `QueryInterface` `AddRef`, `Release` , i `CComObjectRootEx`są delegowane do .

Aby uzyskać więcej `CComObject`informacji na temat używania , zobacz artykuł [Podstawy obiektów COM ATL](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Base`

`CComObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ccomobjectaddref"></a><a name="addref"></a>CComObject::Odnośnik

Zwiększa liczbę odwołań do obiektu.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Wartość zwracana

Ta funkcja zwraca nową przyrostową liczbę odwołań dla obiektu. Ta wartość może być przydatna do diagnostyki lub testowania.

## <a name="ccomobjectccomobject"></a><a name="ccomobject"></a>CComObject::CComObject

Konstruktor zwiększa liczbę blokad modułu.

```
CComObject(void* = NULL);
```

### <a name="parameters"></a>Parametry

<em>void\*</em><br/>
[w] Ten nienazwany parametr nie jest używany. Istnieje dla symetrii `CComXXXObjectXXX` z innymi konstruktorami.

### <a name="remarks"></a>Uwagi

Destruktor go zmniejsza.

`CComObject`Jeśli obiekt pochodny zostanie pomyślnie skonstruowany przy użyciu **nowego** operatora, początkowa liczba odwołań wynosi 0. Aby ustawić liczbę odwołań na odpowiednią wartość (1), należy wywołać funkcję [AddRef.](#addref)

## <a name="ccomobjectccomobject"></a><a name="dtor"></a>CComObject::~CComObject

Destruktor.

```
CComObject();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby, wywołuje [FinalRelease](ccomobjectrootex-class.md#finalrelease)i zmniejsza liczbę blokad modułu.

## <a name="ccomobjectcreateinstance"></a><a name="createinstance"></a>CComObject::CreateInstance

Ta funkcja statyczna umożliwia utworzenie nowego `Base` **>** **obiektu CComObject<,** bez narzutu [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```

### <a name="parameters"></a>Parametry

*S*<br/>
[na zewnątrz] Wskaźnik do `Base` **>** **wskaźnika<CComObject.** Jeśli `CreateInstance` nie powiedzie się, *pp* jest ustawiona na wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Zwrócony obiekt ma liczbę odwołań `AddRef` zero, więc `Release` natychmiast wywołać, a następnie użyć do zwolnienia odwołania na wskaźnik obiektu po zakończeniu.

Jeśli nie potrzebujesz bezpośredniego dostępu do obiektu, ale nadal chcesz utworzyć `CoCreateInstance`nowy obiekt bez narzutu , użyj [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) zamiast.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]

[!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]

## <a name="ccomobjectqueryinterface"></a><a name="queryinterface"></a>CComObject::QueryInterface

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

## <a name="ccomobjectrelease"></a><a name="release"></a>CComObject::Release CComObject::Release CComObject::Release CCom

Zmniejsza liczbę odwołań na obiekcie.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Wartość zwracana

Ta funkcja zwraca nową liczbę odwołań z dekrementowanym obiektem. W kompilacjach debugowania zwracana wartość może być przydatna do diagnostyki lub testowania. W kompilacjach innych niż `Release` debugowanie zawsze zwraca wartość 0.

## <a name="see-also"></a>Zobacz też

[Klasa CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Klasa CComPolyObject](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
