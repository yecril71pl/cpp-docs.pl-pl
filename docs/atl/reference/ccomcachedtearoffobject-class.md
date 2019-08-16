---
title: Klasa CComCachedTearOffObject
ms.date: 11/04/2016
f1_keywords:
- CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::AddRef
- ATLCOM/ATL::CComCachedTearOffObject::FinalConstruct
- ATLCOM/ATL::CComCachedTearOffObject::FinalRelease
- ATLCOM/ATL::CComCachedTearOffObject::QueryInterface
- ATLCOM/ATL::CComCachedTearOffObject::Release
- ATLCOM/ATL::CComCachedTearOffObject::m_contained
helpviewer_keywords:
- cache, ATL cached tear-off objects
- CComCachedTearOffObject class
ms.assetid: ae19507d-a1de-4dbc-a988-da9f75a50c95
ms.openlocfilehash: d993a349d38342bda30a83dfdbe25577953799b3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497535"
---
# <a name="ccomcachedtearoffobject-class"></a>Klasa CComCachedTearOffObject

Ta klasa implementuje interfejs [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) dla interfejsu odrywanego.

## <a name="syntax"></a>Składnia

```
template
<class contained>
class CComCachedTearOffObject : public
    IUnknown,
public CComObjectRootEx<contained
::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parametry

*przechowywany*<br/>
Klasa odrywania, pochodna `CComTearOffObjectBase` i interfejsy, które mają być obsługiwane przez obiekt.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|Konstruktor.|
|[CComCachedTearOffObject::~CComCachedTearOffObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCachedTearOffObject:: AddRef](#addref)|Zwiększa liczbę odwołań dla `CComCachedTearOffObject` obiektu.|
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|Wywołuje metodę `m_contained::FinalConstruct` (Klasa odrywana).|
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|Wywołuje metodę `m_contained::FinalRelease` (Klasa odrywana).|
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|Zwraca wskaźnik do `IUnknown` `CComCachedTearOffObject` obiektu lub do żądanego interfejsu w klasie odrywanej (Klasa `contained`).|
|[CComCachedTearOffObject:: Release](#release)|Zmniejsza liczbę odwołań dla `CComCachedTearOffObject` obiektu i niszczy go, jeśli liczba odwołań wynosi 0.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComCachedTearOffObject::m_contained](#m_contained)|Obiekt pochodzący z klasy odrywania (Klasa `contained`). `CComContainedObject`|

## <a name="remarks"></a>Uwagi

`CComCachedTearOffObject`implementuje interfejs [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) dla interfejsu odrywanego. Ta klasa różni się `CComTearOffObject` od elementu `CComCachedTearOffObject` `IUnknown` w, który `IUnknown`ma swoją własną, niezależnie od obiektu będącego właścicielem (właściciel jest obiektem, dla którego jest tworzona wycofanie). `CComCachedTearOffObject`utrzymuje swoją własną liczbę `IUnknown` odwołań i usuwa siebie, gdy jej liczba odwołań wynosi zero. Jednak w przypadku wykonywania zapytań dotyczących dowolnego z jego interfejsów odrywania liczba odwołań obiektu `IUnknown` właściciela zostanie zwiększona.

Jeśli obiekt implementujący rozrywanie jest już skonkretyzowany, a interfejs odrywany jest ponownie używany do oddzielenia zapytania, ten sam `CComCachedTearOffObject` obiekt jest wykorzystany. `CComCachedTearOffObject` Z drugiej strony, jeśli interfejs odrywania zaimplementowany przez `CComTearOffObject` program jest ponownie wysyłany do zapytania za pomocą obiektu Owner, zostanie utworzone wystąpienie innego `CComTearOffObject` elementu.

Klasa Owner musi implementować `FinalRelease` i wywoływać `Release` `CComCachedTearOffObject`w pamięci `IUnknown` podręcznej dla, która zmniejszy jej liczbę odwołań. `CComCachedTearOffObject` Spowoduje`FinalRelease` to wywołanie i usunięcie odrywania.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComCachedTearOffObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="addref"></a>CComCachedTearOffObject:: AddRef

Zwiększa liczbę `CComCachedTearOffObject` odwołań obiektu o 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatna w przypadku diagnostyki i testowania.

##  <a name="ccomcachedtearoffobject"></a>CComCachedTearOffObject::CComCachedTearOffObject

Konstruktor.

```
CComCachedTearOffObject(void* pv);
```

### <a name="parameters"></a>Parametry

*wa*<br/>
podczas Wskaźnik do `IUnknown` `CComCachedTearOffObject`elementu.

### <a name="remarks"></a>Uwagi

Inicjuje element członkowski, [m_contained.](#m_contained) `CComContainedObject`

##  <a name="dtor"></a>CComCachedTearOffObject:: ~ CComCachedTearOffObject

Destruktor.

```
~CComCachedTearOffObject();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzieloną zasoby i wywołuje [FinalRelease](#finalrelease).

##  <a name="finalconstruct"></a>CComCachedTearOffObject::FinalConstruct

Wywołania `m_contained::FinalConstruct` do tworzenia `m_contained`, `CComContainedObject` Obiekt>używanydouzyskiwaniadostępudointerfejsuimplementowanegoprzezklasęodrywania.<  `contained`

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

##  <a name="finalrelease"></a>CComCachedTearOffObject::FinalRelease

Wywołania `m_contained::FinalRelease` Free `m_contained`, `CComContainedObject` >obiektu.<  `contained`

```
void FinalRelease();
```

##  <a name="m_contained"></a>CComCachedTearOffObject::m_contained

Obiekt [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) pochodzący z klasy odrywanej.

```
CcomContainedObject <contained> m_contained;
```

### <a name="parameters"></a>Parametry

*przechowywany*<br/>
podczas Klasa odrywania, pochodna `CComTearOffObjectBase` i interfejsy, które mają być obsługiwane przez obiekt.

### <a name="remarks"></a>Uwagi

Metody `m_contained` Inherits są używane w celu uzyskania dostępu do interfejsu odrywanego w klasie odrywanej przez zbuforowany `QueryInterface`obiekt, `FinalConstruct`i `FinalRelease`.

##  <a name="queryinterface"></a>CComCachedTearOffObject:: QueryInterface

Pobiera wskaźnik do żądanego interfejsu.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*IID*<br/>
podczas Identyfikator GUID żądanego interfejsu.

*ppvObject*<br/>
określoną Wskaźnik do wskaźnika interfejsu identyfikowanego przez *Identyfikator IID*lub wartość null, jeśli nie można odnaleźć interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli żądany interfejs to `IUnknown`, zwraca wskaźnik `CComCachedTearOffObject`do siebie `IUnknown` i zwiększa liczbę odwołań. W przeciwnym razie zapytania dotyczące interfejsu w klasie odrywania, przy użyciu metody [InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) odziedziczone od `CComObjectRootEx`.

##  <a name="release"></a>CComCachedTearOffObject:: Release

Zmniejsza liczbę odwołań o 1 i, jeśli liczba odwołań wynosi 0, usuwa `CComCachedTearOffObject` obiekt.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Wartość zwracana

W kompilacjach niedebugowanych zawsze zwraca wartość 0. W kompilacjach debugowania zwraca wartość, która może być przydatna w przypadku diagnostyki lub testowania.

## <a name="see-also"></a>Zobacz także

[Klasa CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)<br/>
[Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
