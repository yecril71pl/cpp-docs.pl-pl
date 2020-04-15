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
ms.openlocfilehash: de7528d3972991c233ee4b9037f609b89d0f7434
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327322"
---
# <a name="ccomtearoffobject-class"></a>Klasa CComTearOffObject

Ta klasa implementuje interfejs odryw.

## <a name="syntax"></a>Składnia

```
template<class Base>
class CComTearOffObject : public Base
```

#### <a name="parameters"></a>Parametry

*Podstawowej*<br/>
Twoja klasa tear-off, `CComTearOffObjectBase` pochodzące z i interfejsów, które mają twój obiekt odrywane do obsługi.

ATL implementuje swoje interfejsy odrywane w `CComTearOffObjectBase` dwóch fazach `QueryInterface`— `CComTearOffObject` metody obsługują liczbę odwołań i, podczas wdrażania [IUnknown.](/windows/win32/api/unknwn/nn-unknwn-iunknown)

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
|[CComTearOffObject::QueryInterface](#queryinterface)|Zwraca wskaźnik do żądanego interfejsu w klasie odrywać lub w klasie właściciela.|
|[CComTearOffObject::Release CComTearOffObject::Release CComTearOffObject::Release CCom](#release)|Zmniejsza liczbę odwołań dla `CComTearOffObject` obiektu i niszczy go.|

### <a name="ccomtearoffobjectbase-methods"></a>Metody CComTearOffObjectBase

|||
|-|-|
|[Baza CComTearOffObjectBase](#ccomtearoffobjectbase)|Konstruktor.|

### <a name="ccomtearoffobjectbase-data-members"></a>Elementy członkowskie danych CComTearOffObjectBase

|||
|-|-|
|[m_pOwner](#m_powner)|Wskaźnik do `CComObject` pochodnej klasy właściciela.|

## <a name="remarks"></a>Uwagi

`CComTearOffObject`implementuje interfejs odrywa jako oddzielny obiekt, który jest tworzone tylko wtedy, gdy ten interfejs jest poszukiwany. Odrywać jest usuwany, gdy jego liczba odwołań staje się zero. Zazwyczaj tworzysz interfejs odrywa dla interfejsu, który jest rzadko używany, ponieważ przy użyciu tear-off zapisuje wskaźnik vtable we wszystkich wystąpieniach obiektu głównego.

Należy wyprowadzić klasy implementacji tear-off `CComTearOffObjectBase` z i z interfejsów, które mają być odrywane obiektu do obsługi. `CComTearOffObjectBase`jest szablonowany na klasę właściciela i model wątku. Klasa właściciela jest klasą obiektu, dla którego jest implementowany odrywany. Jeśli nie określisz modelu wątku, używany jest domyślny model wątku.

Należy utworzyć mapę COM dla klasy odrywu. Gdy ATL tworzy wystąpienia tear-off, `CComTearOffObject<CYourTearOffClass>` utworzy lub `CComCachedTearOffObject<CYourTearOffClass>`.

Na przykład w próbce BEEPER `CBeeper2` klasa jest klasą `CBeeper` odrywkową, a klasa jest klasą właściciela:

[!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Base`

`CComTearOffObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ccomtearoffobjectaddref"></a><a name="addref"></a>CComTearOffObject::AddRef

Zwiększa liczbę odwołań `CComTearOffObject` obiektu o jeden.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatna do diagnostyki i testowania.

## <a name="ccomtearoffobjectccomtearoffobject"></a><a name="ccomtearoffobject"></a>CComTearOffObject::CComTearOffObject

Konstruktor.

```
CComTearOffObject(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
[w] Wskaźnik, który zostanie przekonwertowany na wskaźnik do `CComObject<Owner>` obiektu.

### <a name="remarks"></a>Uwagi

Zwiększa liczbę odwołań właściciela o jeden.

## <a name="ccomtearoffobjectccomtearoffobject"></a><a name="dtor"></a>CComTearOffObject::~CComTearOffObject

Destruktor.

```
~CComTearOffObject();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby, wywołuje FinalRelease i zmniejsza liczbę blokad modułu.

## <a name="ccomtearoffobjectccomtearoffobjectbase"></a><a name="ccomtearoffobjectbase"></a>CComTearOffObject::CComTearOffObjectBase

Konstruktor.

```
CComTearOffObjectBase();
```

### <a name="remarks"></a>Uwagi

Inicjuje [element członkowski m_pOwner](#m_powner) do null.

## <a name="ccomtearoffobjectm_powner"></a><a name="m_powner"></a>CComTearOffObject::m_pOwner

Wskaźnik do obiektu [CComObject](../../atl/reference/ccomobject-class.md) pochodzi od *owner*.

```
CComObject<Owner>* m_pOwner;
```

### <a name="parameters"></a>Parametry

*Właściciel*<br/>
[w] Klasa, dla której jest implementowana odryw.

### <a name="remarks"></a>Uwagi

Wskaźnik jest inicjowany do null podczas budowy.

## <a name="ccomtearoffobjectqueryinterface"></a><a name="queryinterface"></a>CComTearOffObject::QueryInterface

Pobiera wskaźnik do żądanego interfejsu.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[w] Identyfikator żądanego interfejsu.

*ppvObiekt*<br/>
[na zewnątrz] Wskaźnik do wskaźnika interfejsu identyfikowanego przez *iid*lub NULL, jeśli interfejs nie zostanie znaleziony.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Zapytania najpierw dla interfejsów w klasie odrywu. Jeśli interfejs nie istnieje, kwerendy dotyczące interfejsu na obiekcie właściciela. Jeśli żądany interfejs `IUnknown`jest `IUnknown` , zwraca właściciela.

## <a name="ccomtearoffobjectrelease"></a><a name="release"></a>CComTearOffObject::Release CComTearOffObject::Release CComTearOffObject::Release CCom

Zmniejsza liczbę odwołań o jeden, a jeśli liczba odwołań `CComTearOffObject`wynosi zero, usuwa plik .

```
STDMETHOD_ULONG Release();
```

### <a name="return-value"></a>Wartość zwracana

W kompilacjach innych niż debugowanie zawsze zwraca zero. W kompilacjach debugowania zwraca wartość, która może być przydatna do diagnostyki lub testowania.

## <a name="see-also"></a>Zobacz też

[Klasa CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
