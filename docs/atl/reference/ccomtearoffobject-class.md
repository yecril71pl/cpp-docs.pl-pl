---
title: Klasa CComTearOffObject
ms.date: 11/04/2016
f1_keywords:
- CComTearOffObject
- ATLCOM/ATL::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::AddRef
- ATLCOM/ATL::CComTearOffObject::QueryInterface
- ATLCOM/ATL::CComTearOffObject::Release
- ATLCOM/ATL::CComTearOffObjectBase
- ATLCOM/ATL::m_pOwner
helpviewer_keywords:
- tear-off interfaces, ATL
- tear-off interfaces
- CComTearOffObject class
ms.assetid: d974b598-c6b2-42b1-8360-9190d9d0fbf3
ms.openlocfilehash: fd35b1e9e69c97402dd1ec357fd25fa1dcd5dd49
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274612"
---
# <a name="ccomtearoffobject-class"></a>Klasa CComTearOffObject

Ta klasa implementuje interfejs odrywania.

## <a name="syntax"></a>Składnia

```
template<class Base>
class CComTearOffObject : public Base
```

#### <a name="parameters"></a>Parametry

*Base*<br/>
Twoje odrywania klasą pochodną `CComTearOffObjectBase` i interfejsy odrywania obiektu do obsługi.

ATL implementuje interfejsy odrywania w dwóch fazach — `CComTearOffObjectBase` metody obsługują licznik odwołań i `QueryInterface`, podczas gdy `CComTearOffObject` implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown).

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComTearOffObject::CComTearOffObject](#ccomtearoffobject)|Konstruktor.|
|[CComTearOffObject::~CComTearOffObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComTearOffObject::AddRef](#addref)|Zwiększa liczbę odwołań dla `CComTearOffObject` obiektu.|
|[CComTearOffObject::QueryInterface](#queryinterface)|Zwraca wskaźnik do żądanego interfejsu w klasie odrywania lub klasy właściciela.|
|[CComTearOffObject::Release](#release)|Dekrementuje liczbę odwołań dla `CComTearOffObject` obiektu, a następnie niszczy go.|

### <a name="ccomtearoffobjectbase-methods"></a>CComTearOffObjectBase Methods

|||
|-|-|
|[CComTearOffObjectBase](#ccomtearoffobjectbase)|Konstruktor.|

### <a name="ccomtearoffobjectbase-data-members"></a>CComTearOffObjectBase Data Members

|||
|-|-|
|[m_pOwner](#m_powner)|Wskaźnik do `CComObject` pochodzi od klasy właściciela.|

## <a name="remarks"></a>Uwagi

`CComTearOffObject` implementuje interfejs odrywania jako oddzielny obiekt, który zostanie uruchomiony tylko wtedy, gdy zostaje przesłane zapytanie interfejsu. Odrywania jest usuwany po jego licznik odwołań staje się zerem. Zwykle tworzysz interfejs odrywania dla interfejsu, który jest rzadko używana, ponieważ przy użyciu odrywania zapisuje wskaźnik vtable we wszystkich wystąpieniach obiektu głównego.

Powinien pochodzić klasy Implementowanie odrywania z `CComTearOffObjectBase` i z dowolnego interfejsy mają obiektu odrywania do obsługi. `CComTearOffObjectBase` jest szablonowana na klasę właściciela i modelu wątku. Klasa właściciel jest klasę obiektu, dla którego odrywania jest implementowana. Jeśli nie określisz modelu wątku, jest używany domyślny model wątku.

Należy utworzyć mapę COM dla swojej klasy odrywania. Gdy występuje ATL odrywania, utworzy on `CComTearOffObject<CYourTearOffClass>` lub `CComCachedTearOffObject<CYourTearOffClass>`.

Na przykład, w tym przykładzie BEEPER `CBeeper2` klasa jest klasą odrywania i `CBeeper` klasa jest klasą właściciela:

[!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Base`

`CComTearOffObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="addref"></a>  CComTearOffObject::AddRef

Zwiększa liczbę odwołań z `CComTearOffObject` obiekt o jeden.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatne w przypadku diagnostyki i testowania.

##  <a name="ccomtearoffobject"></a>  CComTearOffObject::CComTearOffObject

Konstruktor.

```
CComTearOffObject(void* pv);
```

### <a name="parameters"></a>Parametry

*Wa*<br/>
[in] Wskaźnik, który zostanie przekonwertowany na wskaźnik do `CComObject<Owner>` obiektu.

### <a name="remarks"></a>Uwagi

Zwiększa liczbę odwołań właściciela o jeden.

##  <a name="dtor"></a>  CComTearOffObject::~CComTearOffObject

Destruktor.

```
~CComTearOffObject();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby, wywołuje moduł FinalRelease i zmniejsza zablokować count.

##  <a name="ccomtearoffobjectbase"></a>  CComTearOffObject::CComTearOffObjectBase

Konstruktor.

```
CComTearOffObjectBase();
```

### <a name="remarks"></a>Uwagi

Inicjuje [m_pOwner](#m_powner) elementu członkowskiego na wartość NULL.

##  <a name="m_powner"></a>  CComTearOffObject::m_pOwner

Wskaźnik do [CComObject](../../atl/reference/ccomobject-class.md) pochodną obiektu *właściciela*.

```
CComObject<Owner>* m_pOwner;
```

### <a name="parameters"></a>Parametry

*Właściciel*<br/>
[in] Klasa, dla którego odrywania jest implementowana.

### <a name="remarks"></a>Uwagi

Wskaźnik jest inicjowany do wartości NULL podczas konstruowania.

##  <a name="queryinterface"></a>  CComTearOffObject::QueryInterface

Pobiera wskaźnik do żądanego interfejsu.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*IID*<br/>
[in] Identyfikator IID interfejsu żądanej.

*ppvObject*<br/>
[out] Wskaźnik do wskaźnika interfejsu identyfikowane przez *iid*, lub wartość NULL, jeśli nie można odnaleźć interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Kwerendy, najpierw dla interfejsów w klasie odrywania. Jeśli interfejs nie jest dostępne, zapytania dotyczące interfejsu na obiekt właściciela. Jeśli jest żądany interfejs `IUnknown`, zwraca `IUnknown` właściciela.

##  <a name="release"></a>  CComTearOffObject::Release

Dekrementuje liczbę odwołań za pomocą jednej i, jeśli licznik odwołań wynosi zero, usuwa `CComTearOffObject`.

```
STDMETHOD_ULONG Release();
```

### <a name="return-value"></a>Wartość zwracana

W kompilacjach nieprzeznaczonych do debugowania zawsze zwraca wartość zero. W przypadku kompilacji do debugowania zwraca wartość, która może być użyteczna, diagnostykę lub testowania.

## <a name="see-also"></a>Zobacz także

[Klasa CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
