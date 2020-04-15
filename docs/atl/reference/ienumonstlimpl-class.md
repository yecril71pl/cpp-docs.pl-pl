---
title: Klasa IEnumOnSTLImpl
ms.date: 11/04/2016
f1_keywords:
- IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl::Clone
- ATLCOM/ATL::IEnumOnSTLImpl::Init
- ATLCOM/ATL::IEnumOnSTLImpl::Next
- ATLCOM/ATL::IEnumOnSTLImpl::Reset
- ATLCOM/ATL::IEnumOnSTLImpl::Skip
- ATLCOM/ATL::IEnumOnSTLImpl::m_iter
- ATLCOM/ATL::IEnumOnSTLImpl::m_pcollection
- ATLCOM/ATL::IEnumOnSTLImpl::m_spUnk
helpviewer_keywords:
- IEnumOnSTLImpl class
ms.assetid: 1789e77b-88b8-447d-a490-806b918912ce
ms.openlocfilehash: 2fbe6ccfbea2836c42a054da7ea9ebeac4e1555d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329713"
---
# <a name="ienumonstlimpl-class"></a>Klasa IEnumOnSTLImpl

Ta klasa definiuje interfejs modułu wyliczacza na podstawie kolekcji biblioteki standardowej języka C++.

## <a name="syntax"></a>Składnia

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```

#### <a name="parameters"></a>Parametry

*Podstawowej*<br/>
Wyliczyć COM. Zobacz [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) na przykład.

*piid*<br/>
Wskaźnik do identyfikatora interfejsu modułu wyliczanego.

*T*<br/>
Typ elementu udostępniane przez interfejs modułu wyliczacza.

*Kopii*<br/>
[Klasa zasad kopiowania](../../atl/atl-copy-policy-classes.md).

*Typ sortowania*<br/>
Klasa kontenera biblioteki standardowej języka C++.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IEnumOnSTLImpl::Klonuj](#clone)|Wdrożenie **Clone**.|
|[IEnumOnSTLImpl::Init](#init)|Inicjuje wyliczacz.|
|[IEnumOnSTLImpl::Dalej](#next)|Wdrożenie **Next**.|
|[IEnumOnSTLImpl::Reset](#reset)|Implementacja **Reset**.|
|[IEnumOnSTLImpl::Pomiń](#skip)|Wdrożenie **Skip**.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[IEnumOnSTLImpl::m_iter](#m_iter)|Iterator, który reprezentuje bieżącą pozycję wylicznika w kolekcji.|
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|Wskaźnik do kontenera Biblioteki standardowej języka C++, zawierający elementy, które mają być wyliczone.|
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|Wskaźnik `IUnknown` obiektu dostarczającego kolekcję.|

## <a name="remarks"></a>Uwagi

`IEnumOnSTLImpl`zapewnia implementację interfejsu modułu wyliczającego COM, w którym wyliczone elementy są przechowywane w kontenerze zgodnym z biblioteką standardową języka C++. Ta klasa jest analogiczna do [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md) klasy, która zapewnia implementację dla interfejsu modułu wyliczacza na podstawie tablicy.

> [!NOTE]
> Zobacz [CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init) szczegółowe informacje na `CComEnumImpl` `IEnumOnSTLImpl`temat dalszych różnic między i .

Zazwyczaj *nie* trzeba tworzyć własne klasy modułu wyliczającego przez wynikające z tej implementacji interfejsu. Jeśli chcesz użyć wylicznika dostarczonego przez ATL na podstawie kontenera Biblioteki standardowej języka C++, częściej można utworzyć wystąpienie [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)lub utworzyć klasę kolekcji, która zwraca wyliczenia, wywodząc się z [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md).

Jeśli jednak trzeba podać niestandardowy moduł wyliczania (na przykład taki, który udostępnia interfejsy oprócz interfejsu modułu wyliczacza), można wyprowadzić z tej klasy. W tej sytuacji jest prawdopodobne, że trzeba zastąpić [Clone](#clone) metody, aby zapewnić własną implementację.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Base`

`IEnumOnSTLImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ienumonstlimplinit"></a><a name="init"></a>IEnumOnSTLImpl::Init

Inicjuje wyliczacz.

```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```

### <a name="parameters"></a>Parametry

*pUnkForRelease (Nie ma wersji 1000)*<br/>
[w] Wskaźnik `IUnknown` obiektu, który musi być utrzymywany przy życiu w okresie istnienia wyliczacza. Przekaż wartość NULL, jeśli taki obiekt nie istnieje.

*Kolekcji*<br/>
Odwołanie do kontenera biblioteki standardowej języka C++, który przechowuje elementy, które mają być wyliczone.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli przekażesz `Init` odwołanie do kolekcji przechowywane w innym obiekcie, można użyć *pUnkForRelease* parametru, aby upewnić się, że obiekt i kolekcja posiada, jest dostępna tak długo, jak wyliczacz potrzebuje go.

Należy wywołać tę metodę przed przekazaniem wskaźnika do interfejsu modułu wyliczającego z powrotem do wszystkich klientów.

## <a name="ienumonstlimplclone"></a><a name="clone"></a>IEnumOnSTLImpl::Klonuj

Ta metoda zapewnia implementację **Clone** metody, tworząc `CComEnumOnSTL`obiekt typu, inicjując go z tej samej kolekcji i iteratora używane przez bieżący obiekt i zwracając interfejs na nowo utworzony obiekt.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Parametry

*ppEnum (polski)*<br/>
[na zewnątrz] Interfejs modułu wyliczanego na nowo utworzony obiekt sklonowany z bieżącego modułu wyliczanego.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="ienumonstlimplm_spunk"></a><a name="m_spunk"></a>IEnumOnSTLImpl::m_spUnk

Wskaźnik `IUnknown` obiektu dostarczającego kolekcję.

```
CComPtr<IUnknown> m_spUnk;
```

### <a name="remarks"></a>Uwagi

Ten inteligentny wskaźnik utrzymuje odwołanie do obiektu przekazane do [IEnumOnSTLImpl::Init](#init), zapewniając, że pozostaje żywy w okresie istnienia wylicznika.

## <a name="ienumonstlimplm_pcollection"></a><a name="m_pcollection"></a>IEnumOnSTLImpl::m_pcollection

Ten element członkowski wskazuje na kolekcję, która udostępnia dane napędzające implementację interfejsu modułu wyliczanego.

```
CollType* m_pcollection;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski jest inicjowany przez wywołanie [IEnumOnSTLImpl::Init](#init).

## <a name="ienumonstlimplm_iter"></a><a name="m_iter"></a>IEnumOnSTLImpl::m_iter

Ten element członkowski przechowuje iterator używany do oznaczania bieżącej pozycji w kolekcji i przechodzenia do kolejnych elementów.

```
CollType::iterator m_iter;
```

## <a name="ienumonstlimplnext"></a><a name="next"></a>IEnumOnSTLImpl::Dalej

Ta metoda zapewnia implementację **Next** metody.

```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```

### <a name="parameters"></a>Parametry

*Celt*<br/>
[w] Liczba żądanych elementów.

*rgelt ( rgelt )*<br/>
[na zewnątrz] Tablica, która ma być wypełniona elementami.

*pceltFetched*<br/>
[na zewnątrz] Liczba elementów faktycznie zwróconych w *rgelt*. Może to być mniejsza niż *celt,* jeśli mniej niż *celt* elementy pozostają na liście.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="ienumonstlimplreset"></a><a name="reset"></a>IEnumOnSTLImpl::Reset

Ta metoda zapewnia implementację **Reset** metody.

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="ienumonstlimplskip"></a><a name="skip"></a>IEnumOnSTLImpl::Pomiń

Ta metoda zapewnia implementację **Skip** metody.

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Parametry

*Celt*<br/>
[w] Liczba elementów do pominięcia.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
