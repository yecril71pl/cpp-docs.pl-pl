---
title: Klasa CComEnumImpl
ms.date: 11/04/2016
f1_keywords:
- CComEnumImpl
- ATLCOM/ATL::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::Clone
- ATLCOM/ATL::CComEnumImpl::Init
- ATLCOM/ATL::CComEnumImpl::Next
- ATLCOM/ATL::CComEnumImpl::Reset
- ATLCOM/ATL::CComEnumImpl::Skip
- ATLCOM/ATL::CComEnumImpl::m_begin
- ATLCOM/ATL::CComEnumImpl::m_dwFlags
- ATLCOM/ATL::CComEnumImpl::m_end
- ATLCOM/ATL::CComEnumImpl::m_iter
- ATLCOM/ATL::CComEnumImpl::m_spUnk
helpviewer_keywords:
- CComEnumImpl class
ms.assetid: cc0d8e76-e608-46db-87cd-4c7161fe32d2
ms.openlocfilehash: 517a4e90ca21e22dcf161aefcff61a40437eabe0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226610"
---
# <a name="ccomenumimpl-class"></a>Klasa CComEnumImpl

Ta klasa udostępnia implementację interfejsu modułu wyliczającego COM, w którym wyliczane elementy są przechowywane w tablicy.

## <a name="syntax"></a>Składnia

```
template <class Base,
    const IID* piid, class T, class Copy>
class ATL_NO_VTABLE CComEnumImpl : public Base
```

#### <a name="parameters"></a>Parametry

*Opiera*<br/>
Interfejs modułu wyliczającego COM. Zapoznaj się z przykładem [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) .

*piid*<br/>
Wskaźnik do identyfikatora interfejsu w interfejsie modułu wyliczającego.

*T*<br/>
Typ elementu uwidocznionego przez interfejs modułu wyliczającego.

*Kopiuj*<br/>
Jednorodna [Klasa zasad kopiowania](../../atl/atl-copy-policy-classes.md).

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|Konstruktor.|
|[CComEnumImpl:: ~ CComEnumImpl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComEnumImpl:: Clone](#clone)|Implementacja metody interfejsu wyliczania **klonowania** .|
|[CComEnumImpl:: init](#init)|Inicjuje moduł wyliczający.|
|[CComEnumImpl:: Next](#next)|Implementacja **następnej**.|
|[CComEnumImpl:: Reset](#reset)|Implementacja **Reset**.|
|[CComEnumImpl:: Skip](#skip)|Implementacja **pomijania**.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComEnumImpl:: m_begin](#m_begin)|Wskaźnik do pierwszego elementu w tablicy.|
|[CComEnumImpl:: m_dwFlags](#m_dwflags)|Kopiuj flagi przenoszone przez `Init` .|
|[CComEnumImpl:: m_end](#m_end)|Wskaźnik do lokalizacji tylko poza ostatnim elementem w tablicy.|
|[CComEnumImpl:: m_iter](#m_iter)|Wskaźnik do bieżącego elementu w tablicy.|
|[CComEnumImpl:: m_spUnk](#m_spunk)|`IUnknown`Wskaźnik obiektu dostarczającego wyliczaną kolekcję.|

## <a name="remarks"></a>Uwagi

Zobacz [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) , aby zapoznać się z przykładem implementacji metod. `CComEnumImpl`zapewnia implementację interfejsu modułu wyliczającego COM, w którym wyliczane elementy są przechowywane w tablicy. Ta klasa jest analogiczna do `IEnumOnSTLImpl` klasy, która dostarcza implementację interfejsu modułu wyliczającego na podstawie kontenera standardowej biblioteki języka C++.

> [!NOTE]
> Aby uzyskać szczegółowe informacje na temat dalszych różnic między programami `CComEnumImpl` i `IEnumOnSTLImpl` , zobacz [CComEnumImpl:: init](#init).

Zazwyczaj *nie* trzeba tworzyć własnej klasy modułu wyliczającego, pobierając ją z tej implementacji interfejsu. Jeśli chcesz użyć modułu wyliczającego opartego na procesorze ATL na podstawie tablicy, bardziej powszechne jest utworzenie wystąpienia [CComEnum](../../atl/reference/ccomenum-class.md).

Jednakże w przypadku konieczności zapewnienia niestandardowego modułu wyliczającego (na przykład, który uwidacznia interfejsy oprócz interfejsu wyliczającego) można utworzyć z tej klasy. W takiej sytuacji prawdopodobnie trzeba przesłonić metodę [CComEnumImpl:: Clone](#clone) , aby zapewnić własną implementację.

Aby uzyskać więcej informacji, zobacz [zestawy ATL i moduły wyliczające](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Base`

`CComEnumImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

## <a name="ccomenumimplccomenumimpl"></a><a name="ccomenumimpl"></a>CComEnumImpl::CComEnumImpl

Konstruktor.

```
CComEnumImpl();
```

## <a name="ccomenumimplccomenumimpl"></a><a name="dtor"></a>CComEnumImpl:: ~ CComEnumImpl

Destruktor.

```
~CComEnumImpl();
```

## <a name="ccomenumimplinit"></a><a name="init"></a>CComEnumImpl:: init

Należy wywołać tę metodę przed przekazaniem wskaźnika do interfejsu modułu wyliczającego z powrotem do dowolnego klienta.

```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```

### <a name="parameters"></a>Parametry

*zaczną*<br/>
Wskaźnik do pierwszego elementu tablicy zawierającej elementy, które mają zostać wyliczone.

*punktów*<br/>
Wskaźnik do lokalizacji tuż poza ostatnim elementem tablicy zawierającej elementy, które mają zostać wyliczone.

*Punkt*<br/>
podczas `IUnknown`Wskaźnik obiektu, który musi być utrzymywany w okresie istnienia modułu wyliczającego. Przekaż wartość NULL, jeśli taki obiekt nie istnieje.

*flagi*<br/>
Flagi określające, czy moduł wyliczający powinien przejąć własność tablicy, czy utworzyć jego kopię. Możliwe wartości są opisane poniżej.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Tylko jednokrotnie Wywołaj tę metodę — zainicjuj moduł wyliczający, użyj go, a następnie zgłoś go.

Jeśli przekazujesz wskaźniki do elementów w tablicy przechowywanej w innym obiekcie (i nie podasz tego modułu wyliczającego w celu skopiowania danych), możesz użyć parametru *punktowy* , aby upewnić się, że obiekt i tablica, do których jest ona dostępna, są dostępne tak długo, jak moduł wyliczający je potrzebuje. Moduł wyliczający po prostu przechowuje odwołanie COM do obiektu, aby go zachować. Odwołanie COM jest automatycznie uwalniane, gdy moduł wyliczający zostanie zniszczony.

Parametr *flags* umożliwia określenie sposobu, w jaki moduł wyliczający ma traktować elementy tablicy, do których są przesyłane. *flagi* mogą przyjmować jedną z wartości z `CComEnumFlags` wyliczenia pokazanego poniżej:

```
enum CComEnumFlags
   {
   AtlFlagNoCopy = 0,
   AtlFlagTakeOwnership = 2, // BitOwn
   AtlFlagCopy = 3           // BitOwn | BitCopy
   };
```

`AtlFlagNoCopy`oznacza, że okres istnienia tablicy nie jest kontrolowany przez moduł wyliczający. W takim przypadku tablica będzie statyczna lub obiekt identyfikowany za pomocą parametru *punktowy* będzie odpowiedzialny za zwolnienie tablicy, gdy nie jest już potrzebne.

`AtlFlagTakeOwnership`oznacza, że niszczenie tablicy ma być kontrolowane przez moduł wyliczający. W takim przypadku Tablica musi być przydzielana dynamicznie przy użyciu **`new`** . Moduł wyliczający usunie tablicę z destruktora. Zazwyczaj można przekazać wartość NULL dla elementu *punkt*, chociaż można nadal przekazywać prawidłowy wskaźnik, jeśli trzeba będzie powiadamiać o zniszczeniu modułu wyliczającego z jakiegoś powodu.

`AtlFlagCopy`oznacza, że nowa tablica ma zostać utworzona przez skopiowanie tablicy przekazaną do `Init` . Okres istnienia nowej tablicy jest kontrolowany przez moduł wyliczający. Moduł wyliczający usunie tablicę z destruktora. Zazwyczaj można przekazać wartość NULL dla elementu *punkt*, chociaż można nadal przekazywać prawidłowy wskaźnik, jeśli trzeba będzie powiadamiać o zniszczeniu modułu wyliczającego z jakiegoś powodu.

> [!NOTE]
> Prototyp tej metody określa elementy tablicy jako typ `T` , gdzie `T` został zdefiniowany jako parametr szablonu dla klasy. Jest to ten sam typ, który jest udostępniany przez metodę interfejsu COM [CComEnumImpl:: Next](#next). Jest to takie, jak w przeciwieństwie do [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md), ta klasa nie obsługuje różnych magazynów i uwidocznionych typów danych. Typ danych elementów w tablicy musi być taki sam jak typ danych uwidoczniony za pomocą interfejsu COM.

## <a name="ccomenumimplclone"></a><a name="clone"></a>CComEnumImpl:: Clone

Ta metoda zapewnia implementację metody **klonowania** przez utworzenie obiektu typu `CComEnum` , zainicjowanie go z tą samą tablicą i iteratorem używanym przez bieżący obiekt i zwróceniem interfejsu na nowo utworzony obiekt.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Parametry

*ppEnum*<br/>
określoną Interfejs modułu wyliczającego na nowo utworzonym obiekcie sklonowanym z bieżącego modułu wyliczającego.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Należy zauważyć, że sklonowane moduły wyliczające nigdy nie wykonują własnych kopii (ani nie przejmować na własność) danych używanych przez oryginalny moduł wyliczający. W razie potrzeby sklonowane Numeratory zachowują pierwotny moduł wyliczający (przy użyciu odwołania COM), aby upewnić się, że dane są dostępne tak długo, jak ich potrzebują.

## <a name="ccomenumimplm_spunk"></a><a name="m_spunk"></a>CComEnumImpl:: m_spUnk

Ten inteligentny wskaźnik zachowuje odwołanie do obiektu przenoszonego do [CComEnumImpl:: init](#init), upewniając się, że pozostaje aktywny w okresie istnienia modułu wyliczającego.

```
CComPtr<IUnknown> m_spUnk;
```

## <a name="ccomenumimplm_begin"></a><a name="m_begin"></a>CComEnumImpl:: m_begin

Wskaźnik do lokalizacji tuż poza ostatnim elementem tablicy zawierającej elementy, które mają zostać wyliczone.

```
T* m_begin;
```

## <a name="ccomenumimplm_end"></a><a name="m_end"></a>CComEnumImpl:: m_end

Wskaźnik do pierwszego elementu tablicy zawierającej elementy, które mają zostać wyliczone.

```
T* m_end;
```

## <a name="ccomenumimplm_iter"></a><a name="m_iter"></a>CComEnumImpl:: m_iter

Wskaźnik do bieżącego elementu tablicy zawierającej elementy, które mają zostać wyliczone.

```
T* m_iter;
```

## <a name="ccomenumimplm_dwflags"></a><a name="m_dwflags"></a>CComEnumImpl:: m_dwFlags

Flagi przesłane do [CComEnumImpl:: init](#init).

```
DWORD m_dwFlags;
```

## <a name="ccomenumimplnext"></a><a name="next"></a>CComEnumImpl:: Next

Ta metoda zapewnia implementację **następnej** metody.

```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```

### <a name="parameters"></a>Parametry

*celt*<br/>
podczas Liczba żądanych elementów.

*rgelt*<br/>
określoną Tablica, która ma zostać wypełniona elementami.

*pceltFetched*<br/>
określoną Liczba elementów faktycznie zwróconych w *rgelt*. Może to być mniejsze niż *celt* , jeśli na liście pozostał mniej niż *celt* elementów.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="ccomenumimplreset"></a><a name="reset"></a>CComEnumImpl:: Reset

Ta metoda zapewnia implementację metody **Reset** .

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="ccomenumimplskip"></a><a name="skip"></a>CComEnumImpl:: Skip

Ta metoda zapewnia implementację metody **Skip** .

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Parametry

*celt*<br/>
podczas Liczba elementów do pominięcia.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Zwraca E_INVALIDARG, jeśli *celt* ma wartość zero, zwraca S_FALSE, jeśli zwracane są elementy mniejsze niż *celt* , zwraca S_OK w przeciwnym razie.

## <a name="see-also"></a>Zobacz także

[Klasa IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)<br/>
[Klasa CComEnum](../../atl/reference/ccomenum-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
