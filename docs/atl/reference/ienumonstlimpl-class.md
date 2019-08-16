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
ms.openlocfilehash: 7cf777f3ff0d298f224157735a06bf57a2c10cf5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495860"
---
# <a name="ienumonstlimpl-class"></a>Klasa IEnumOnSTLImpl

Ta klasa definiuje interfejs modułu wyliczającego na C++ podstawie standardowej kolekcji biblioteki.

## <a name="syntax"></a>Składnia

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```

#### <a name="parameters"></a>Parametry

*Opiera*<br/>
Moduł wyliczający COM. Zapoznaj się z przykładem [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) .

*piid*<br/>
Wskaźnik do identyfikatora interfejsu w interfejsie modułu wyliczającego.

*T*<br/>
Typ elementu uwidocznionego przez interfejs modułu wyliczającego.

*Kopiuj*<br/>
[Klasa zasad kopiowania](../../atl/atl-copy-policy-classes.md).

*CollType*<br/>
Klasa C++ kontenera biblioteki standardowej.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IEnumOnSTLImpl:: Clone](#clone)|Implementacja klonowania.|
|[IEnumOnSTLImpl:: init](#init)|Inicjuje moduł wyliczający.|
|[IEnumOnSTLImpl:: Next](#next)|Implementacja **następnej**.|
|[IEnumOnSTLImpl:: Reset](#reset)|Implementacja **Reset**.|
|[IEnumOnSTLImpl:: Skip](#skip)|Implementacja pomijania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[IEnumOnSTLImpl::m_iter](#m_iter)|Iterator reprezentujący bieżącą pozycję modułu wyliczającego w kolekcji.|
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|Wskaźnik do kontenera biblioteki C++ standardowej przechowującego elementy do wyliczenia.|
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|`IUnknown` Wskaźnik obiektu dostarczającego kolekcję.|

## <a name="remarks"></a>Uwagi

`IEnumOnSTLImpl`zapewnia implementację interfejsu modułu wyliczającego COM, w którym wyliczane elementy są przechowywane w C++ standardowym kontenerze zgodnym z biblioteką. Ta klasa jest analogiczna do klasy [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md) , która dostarcza implementację interfejsu modułu wyliczającego na podstawie tablicy.

> [!NOTE]
>  Zobacz [CComEnumImpl:: init](../../atl/reference/ccomenumimpl-class.md#init) , aby uzyskać szczegółowe informacje na `CComEnumImpl` temat `IEnumOnSTLImpl`dalszych różnic między i.

Zazwyczaj *nie* trzeba tworzyć własnej klasy modułu wyliczającego, pobierając ją z tej implementacji interfejsu. Jeśli chcesz użyć modułu wyliczającego opartego na procesorze ATL C++ na podstawie standardowego kontenera biblioteki, bardziej powszechne jest utworzenie wystąpienia [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)lub utworzenie klasy kolekcji, która zwraca moduł wyliczający przez wyprowadzanie z [ICollectionOnSTLImpl ](../../atl/reference/icollectiononstlimpl-class.md).

Jednakże w przypadku konieczności zapewnienia niestandardowego modułu wyliczającego (na przykład, który uwidacznia interfejsy oprócz interfejsu wyliczającego) można utworzyć z tej klasy. W takiej sytuacji prawdopodobnie trzeba przesłonić metodę klonowania, aby [](#clone) zapewnić własną implementację.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Base`

`IEnumOnSTLImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="init"></a>IEnumOnSTLImpl:: init

Inicjuje moduł wyliczający.

```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```

### <a name="parameters"></a>Parametry

*pUnkForRelease*<br/>
podczas `IUnknown` Wskaźnik obiektu, który musi być utrzymywany w okresie istnienia modułu wyliczającego. Przekaż wartość NULL, jeśli taki obiekt nie istnieje.

*zbiera*<br/>
Odwołanie do kontenera biblioteki C++ standardowej zawierające elementy do wyliczenia.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli przekazujesz `Init` odwołanie do kolekcji przechowywanej w innym obiekcie, możesz użyć parametru *pUnkForRelease* , aby upewnić się, że obiekt i kolekcja, które przechowuje, są dostępne tak długo, jak moduł wyliczający wymaga tego.

Należy wywołać tę metodę przed przekazaniem wskaźnika do interfejsu modułu wyliczającego z powrotem do dowolnego klienta.

##  <a name="clone"></a>IEnumOnSTLImpl:: Clone

Ta metoda zapewnia implementację metody **klonowania** przez utworzenie obiektu typu `CComEnumOnSTL`, zainicjowanie go z tą samą kolekcją i iteratorem używanym przez bieżący obiekt i zwróceniem interfejsu na nowo utworzony obiekt.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Parametry

*ppEnum*<br/>
określoną Interfejs modułu wyliczającego na nowo utworzonym obiekcie sklonowanym z bieżącego modułu wyliczającego.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

##  <a name="m_spunk"></a>IEnumOnSTLImpl::m_spUnk

`IUnknown` Wskaźnik obiektu dostarczającego kolekcję.

```
CComPtr<IUnknown> m_spUnk;
```

### <a name="remarks"></a>Uwagi

Ten inteligentny wskaźnik zachowuje odwołanie do obiektu przenoszonego do [IEnumOnSTLImpl:: init](#init), upewniając się, że pozostaje aktywny w okresie istnienia modułu wyliczającego.

##  <a name="m_pcollection"></a>IEnumOnSTLImpl::m_pcollection

Ten element członkowski wskazuje kolekcję, która dostarcza dane prowadzące do implementacji interfejsu modułu wyliczającego.

```
CollType* m_pcollection;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski jest inicjowany przez wywołanie [IEnumOnSTLImpl:: init](#init).

##  <a name="m_iter"></a>IEnumOnSTLImpl::m_iter

Ten element członkowski zawiera iterator używany do oznaczania bieżącej pozycji w kolekcji i przechodzenia do kolejnych elementów.

```
CollType::iterator m_iter;
```

##  <a name="next"></a>IEnumOnSTLImpl:: Next

Ta metoda zapewnia implementację **następnej** metody.

```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```

### <a name="parameters"></a>Parametry

*celt*<br/>
podczas Liczba żądanych elementów.

*rgelt*<br/>
określoną Tablica, która ma zostać wypełniona elementami.

*pceltFetched*<br/>
określoną Liczba elementów faktycznie zwróconych w *rgelt*. Może to być mniejsze niż *celt* , jeśli na liście pozostanie mniej niż *celt* elementów.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

##  <a name="reset"></a>IEnumOnSTLImpl:: Reset

Ta metoda zapewnia implementację metody **Reset** .

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

##  <a name="skip"></a>IEnumOnSTLImpl:: Skip

Ta metoda zapewnia implementację metody **Skip** .

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Parametry

*celt*<br/>
podczas Liczba elementów do pominięcia.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
