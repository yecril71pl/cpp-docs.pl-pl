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
ms.openlocfilehash: 019b90c932de144d05fbf05f3ca339f4e5d6edd1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748102"
---
# <a name="ccomcachedtearoffobject-class"></a>Klasa CComCachedTearOffObject

Ta klasa implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) dla interfejsu odrywane.

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

*Zawarte*<br/>
Twoja klasa tear-off, `CComTearOffObjectBase` pochodzące z i interfejsów, które mają twój obiekt odrywane do obsługi.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|Konstruktor.|
|[CComCachedTearOffObject::~CComCachedTearOffObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCachedTearOffObject::AddRef](#addref)|Zwiększa liczbę odwołań dla `CComCachedTearOffObject` obiektu.|
|[CComCachedTearOffObject::FinalConstruct CComCachedTearOffObject::FinalConstruct CComCachedTearOffObject::FinalConstruct CCom](#finalconstruct)|Wywołuje `m_contained::FinalConstruct` (metoda klasy odrywu).|
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|Wywołuje `m_contained::FinalRelease` (metoda klasy odrywu).|
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|Zwraca wskaźnik do `IUnknown` `CComCachedTearOffObject` obiektu lub do żądanego interfejsu w klasie odrywać `contained`(klasa).|
|[CComCachedTearOffObject::Release CComCachedTearOffObject::Release CComCachedTearOffObject::Release CCom](#release)|Zmniejsza liczbę odwołań dla `CComCachedTearOffObject` obiektu i niszczy go, jeśli liczba odwołań wynosi 0.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComCachedTearOffObject::m_contained](#m_contained)|Obiekt `CComContainedObject` pochodzący z klasy odrywane (klasa). `contained`|

## <a name="remarks"></a>Uwagi

`CComCachedTearOffObject`implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) dla oderwanego interfejsu. Ta klasa różni `CComTearOffObject` się `CComCachedTearOffObject` od `IUnknown`tej ma swój własny `IUnknown` , oddzielony od obiektu właściciela (właściciel jest obiektem, dla którego tworzony jest odrywany). `CComCachedTearOffObject`utrzymuje własną liczbę odwołań `IUnknown` na jego i usuwa się, gdy jego liczba odwołań wynosi zero. Jednak jeśli kwerendy dla któregokolwiek z jego interfejsów odryw, `IUnknown` liczba odwołań obiektu właściciela zostanie przyrostowana.

Jeśli `CComCachedTearOffObject` obiekt implementujący tear-off jest już wystąpienia, a interfejs odrywane jest `CComCachedTearOffObject` wyszukiwany ponownie, ten sam obiekt jest ponownie. Z drugiej strony, jeśli interfejs odrywa zaimplementowany przez `CComTearOffObject` a `CComTearOffObject` jest ponownie poszukiwany za pośrednictwem obiektu właściciela, inny zostanie skonkrzetowany.

Klasa właściciela musi `FinalRelease` zaimplementować `IUnknown` i `CComCachedTearOffObject`wywołać `Release` buforowane dla , który zmniejszy jego liczbę odwołań. Spowoduje to, `FinalRelease` że "s być wywołane i usunąć odrywać.This will cause's `CComCachedTearOffObject`to be called and delete the tear-off.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CComObjectRootBase`

[Ccomobjectrootex](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComCachedTearOffObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ccomcachedtearoffobjectaddref"></a><a name="addref"></a>CComCachedTearOffObject::AddRef

Zwiększa liczbę odwołań `CComCachedTearOffObject` obiektu o 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatna do diagnostyki i testowania.

## <a name="ccomcachedtearoffobjectccomcachedtearoffobject"></a><a name="ccomcachedtearoffobject"></a>CComCachedTearOffObject::CComCachedTearOffObject

Konstruktor.

```
CComCachedTearOffObject(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
[w] Wskaźnik do `IUnknown` pliku `CComCachedTearOffObject`.

### <a name="remarks"></a>Uwagi

Inicjuje `CComContainedObject` element członkowski, [m_contained](#m_contained).

## <a name="ccomcachedtearoffobjectccomcachedtearoffobject"></a><a name="dtor"></a>CComCachedTearOffObject::~CComCachedTearOffObject

Destruktor.

```
~CComCachedTearOffObject();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby i wywołuje [FinalRelease](#finalrelease).

## <a name="ccomcachedtearoffobjectfinalconstruct"></a><a name="finalconstruct"></a>CComCachedTearOffObject::FinalConstruct CComCachedTearOffObject::FinalConstruct CComCachedTearOffObject::FinalConstruct CCom

`m_contained::FinalConstruct` Wywołania, `m_contained`aby `CComContainedObject` <  `contained` utworzyć obiekt> używany do uzyskiwania dostępu do interfejsu zaimplementowanego przez klasę odrywać.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="ccomcachedtearoffobjectfinalrelease"></a><a name="finalrelease"></a>CComCachedTearOffObject::FinalRelease

Połączenia `m_contained::FinalRelease` do `m_contained`bezpłatnego `CComContainedObject` <  `contained` ,> obiektu.

```cpp
void FinalRelease();
```

## <a name="ccomcachedtearoffobjectm_contained"></a><a name="m_contained"></a>CComCachedTearOffObject::m_contained

A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) obiekt pochodzi od odrynia klasy.

```
CcomContainedObject <contained> m_contained;
```

### <a name="parameters"></a>Parametry

*Zawarte*<br/>
[w] Twoja klasa tear-off, `CComTearOffObjectBase` pochodzące z i interfejsów, które mają twój obiekt odrywane do obsługi.

### <a name="remarks"></a>Uwagi

Metody `m_contained` dziedziczenia są używane do uzyskiwania dostępu do interfejsu odrywania w klasie `QueryInterface`odrywania za pośrednictwem buforowanego obiektu odrywania i `FinalConstruct`. `FinalRelease`

## <a name="ccomcachedtearoffobjectqueryinterface"></a><a name="queryinterface"></a>CComCachedTearOffObject::QueryInterface

Pobiera wskaźnik do żądanego interfejsu.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[w] Identyfikator GUID żądanego interfejsu.

*ppvObiekt*<br/>
[na zewnątrz] Wskaźnik do wskaźnika interfejsu identyfikowanego przez *iid*lub NULL, jeśli interfejs nie zostanie znaleziony.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli żądany interfejs `IUnknown`jest , zwraca `CComCachedTearOffObject`wskaźnik `IUnknown` do 's własnych i zwiększa liczbę odwołań. W przeciwnym razie kwerendy dla interfejsu w klasie odrywa przy użyciu `CComObjectRootEx` [InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) metoda dziedziczona z .

## <a name="ccomcachedtearoffobjectrelease"></a><a name="release"></a>CComCachedTearOffObject::Release CComCachedTearOffObject::Release CComCachedTearOffObject::Release CCom

Zmniejsza liczbę odwołań o 1, a jeśli liczba odwołań `CComCachedTearOffObject` wynosi 0, usuwa obiekt.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Wartość zwracana

W kompilacjach innych niż debugowanie zawsze zwraca wartość 0. W kompilacjach debugowania zwraca wartość, która może być przydatna do diagnostyki lub testowania.

## <a name="see-also"></a>Zobacz też

[Klasa CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)<br/>
[Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
