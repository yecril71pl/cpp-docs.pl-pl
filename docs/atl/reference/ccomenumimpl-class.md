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
ms.openlocfilehash: 965e0a8bf6c890882754b60e2785832933d1c52c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327860"
---
# <a name="ccomenumimpl-class"></a>Klasa CComEnumImpl

Ta klasa zapewnia implementację interfejsu modułu wyliczacza COM, w którym elementy są wyliczone są przechowywane w tablicy.

## <a name="syntax"></a>Składnia

```
template <class Base,
    const IID* piid, class T, class Copy>
class ATL_NO_VTABLE CComEnumImpl : public Base
```

#### <a name="parameters"></a>Parametry

*Podstawowej*<br/>
Interfejs modułu wyliczaczajnego COM. Zobacz [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) na przykład.

*piid*<br/>
Wskaźnik do identyfikatora interfejsu modułu wyliczanego.

*T*<br/>
Typ elementu udostępniane przez interfejs modułu wyliczacza.

*Kopii*<br/>
Jednorodna [klasa zasad kopiowania](../../atl/atl-copy-policy-classes.md).

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|Konstruktor.|
|[CComEnumImpl::~CComEnumImpl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComEnumImpl::Klonuj](#clone)|Implementacja **clone** metody interfejsu wyliczenia.|
|[CComEnumImpl::Init](#init)|Inicjuje wyliczacz.|
|[CComEnumImpl::Następny](#next)|Wdrożenie **Next**.|
|[CComEnumImpl::Reset](#reset)|Implementacja **Reset**.|
|[CComEnumImpl::Pomiń](#skip)|Wdrożenie **Skip**.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComEnumImpl::m_begin](#m_begin)|Wskaźnik do pierwszego elementu w tablicy.|
|[CComEnumImpl::m_dwFlags](#m_dwflags)|Flagi kopiowania `Init`przeszły przez plik .|
|[CComEnumImpl::m_end](#m_end)|Wskaźnik do lokalizacji tuż za ostatnim elementem w tablicy.|
|[CComEnumImpl::m_iter](#m_iter)|Wskaźnik do bieżącego elementu w tablicy.|
|[CComEnumImpl::m_spUnk](#m_spunk)|Wskaźnik `IUnknown` obiektu dostarczającego kolekcji są wyliczone.|

## <a name="remarks"></a>Uwagi

Zobacz [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) na przykład implementacji metody. `CComEnumImpl`zapewnia implementację interfejsu modułu wyliczacza COM, w którym wyliczone elementy są przechowywane w tablicy. Ta klasa jest analogiczna do `IEnumOnSTLImpl` klasy, która zapewnia implementację interfejsu modułu wyliczającego na podstawie kontenera biblioteki standardowej języka C++.

> [!NOTE]
> Aby uzyskać szczegółowe informacje `CComEnumImpl` `IEnumOnSTLImpl`na temat dalszych różnic między i , zobacz [CComEnumImpl::Init](#init).

Zazwyczaj *nie* trzeba tworzyć własne klasy modułu wyliczającego przez wynikające z tej implementacji interfejsu. Jeśli chcesz użyć wyliczenia dostarczonego przez ATL na podstawie tablicy, bardziej często można utworzyć wystąpienie [CComEnum](../../atl/reference/ccomenum-class.md).

Jeśli jednak trzeba podać niestandardowy moduł wyliczania (na przykład taki, który udostępnia interfejsy oprócz interfejsu modułu wyliczacza), można wyprowadzić z tej klasy. W tej sytuacji jest prawdopodobne, że trzeba zastąpić [CComEnumImpl::Clone](#clone) metody, aby zapewnić własną implementację.

Aby uzyskać więcej informacji, zobacz [Kolekcje ATL i wyliczacze](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Base`

`CComEnumImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ccomenumimplccomenumimpl"></a><a name="ccomenumimpl"></a>CComEnumImpl::CComEnumImpl

Konstruktor.

```
CComEnumImpl();
```

## <a name="ccomenumimplccomenumimpl"></a><a name="dtor"></a>CComEnumImpl::~CComEnumImpl

Destruktor.

```
~CComEnumImpl();
```

## <a name="ccomenumimplinit"></a><a name="init"></a>CComEnumImpl::Init

Należy wywołać tę metodę przed przekazaniem wskaźnika do interfejsu modułu wyliczającego z powrotem do wszystkich klientów.

```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```

### <a name="parameters"></a>Parametry

*Rozpocząć*<br/>
Wskaźnik do pierwszego elementu tablicy zawierającego elementy, które mają być wyliczone.

*Końcu*<br/>
Wskaźnik do lokalizacji tuż poza ostatnim elementem tablicy zawierającej elementy, które mają być wyliczone.

*Punk*<br/>
[w] Wskaźnik `IUnknown` obiektu, który musi być utrzymywany przy życiu w okresie istnienia wyliczacza. Przekaż wartość NULL, jeśli taki obiekt nie istnieje.

*flagi*<br/>
Flagi określające, czy wyliczacz powinien przejąć na własność tablicy lub wykonać jej kopię. Możliwe wartości są opisane poniżej.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę tylko raz — zaizwuś wyliczenie, użyj go, a następnie wyrzuć ją.

Jeśli przekażesz wskaźniki do elementów w tablicy przechowywane w innym obiekcie (i nie poprosisz wylicznika o skopiowanie danych), można użyć *parametru pUnk,* aby upewnić się, że obiekt i tablica, którą posiada, są dostępne tak długo, jak wymaga tego wylicznik. Wyliczacz po prostu posiada odwołanie COM na obiekcie, aby utrzymać go przy życiu. Odwołanie COM jest automatycznie zwalniane po zniszczeniu wylicznika.

Parametr *flags* umożliwia określenie sposobu, w jaki wyliczacz powinien traktować elementy tablicy przekazane do niego. *flagi* mogą przyjmować jedną `CComEnumFlags` z wartości z wyliczenia pokazanego poniżej:

```
enum CComEnumFlags
   {
   AtlFlagNoCopy = 0,
   AtlFlagTakeOwnership = 2, // BitOwn
   AtlFlagCopy = 3           // BitOwn | BitCopy
   };
```

`AtlFlagNoCopy`oznacza, że okres istnienia tablicy nie jest kontrolowany przez wyliczacz. W takim przypadku tablica będzie statyczna lub obiekt zidentyfikowany przez *pUnk* będzie odpowiedzialny za zwalnianie tablicy, gdy nie jest już potrzebna.

`AtlFlagTakeOwnership`oznacza, że zniszczenie tablicy ma być kontrolowane przez wyliczający. W takim przypadku tablica musi być dynamicznie przydzielana przy użyciu **nowego**programu . Wyliczacz usunie tablicę w jego destruktora. Zazwyczaj można przekazać NULL dla *pUnk*, chociaż nadal można przekazać prawidłowy wskaźnik, jeśli trzeba być powiadamiany o zniszczeniu wylicznika z jakiegoś powodu.

`AtlFlagCopy`oznacza, że nowa tablica ma zostać utworzona `Init`przez skopiowanie tablicy przekazanej do . Okres istnienia nowej tablicy ma być kontrolowany przez wyliczacz. Wyliczacz usunie tablicę w jego destruktora. Zazwyczaj można przekazać NULL dla *pUnk*, chociaż nadal można przekazać prawidłowy wskaźnik, jeśli trzeba być powiadamiany o zniszczeniu wylicznika z jakiegoś powodu.

> [!NOTE]
> Prototyp tej metody określa elementy tablicy jako `T`typ `T` , gdzie został zdefiniowany jako parametr szablonu do klasy. Jest to ten sam typ, który jest narażony za pomocą metody interfejsu COM [CComEnumImpl::Next](#next). Implikacją tego jest to, że w przeciwieństwie do [IEnumOnSTLImpl,](../../atl/reference/ienumonstlimpl-class.md)ta klasa nie obsługuje różnych typów magazynu i danych narażonych. Typ danych elementów w tablicy musi być taki sam jak typ danych udostępniane za pomocą interfejsu COM.

## <a name="ccomenumimplclone"></a><a name="clone"></a>CComEnumImpl::Klonuj

Ta metoda zapewnia implementację **Clone** metody przez utworzenie `CComEnum`obiektu typu, inicjowanie go z tej samej tablicy i iteratora używane przez bieżący obiekt i zwracanie interfejsu na nowo utworzony obiekt.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Parametry

*ppEnum (polski)*<br/>
[na zewnątrz] Interfejs modułu wyliczanego na nowo utworzony obiekt sklonowany z bieżącego modułu wyliczanego.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Należy zauważyć, że sklonowane wyliczacze nigdy nie tworzyć własną kopię (lub przejąć na własność) danych używanych przez oryginalnego wylicznika. Jeśli to konieczne, sklonowane wyliczenia zachowa oryginalny wyliczacz przy życiu (przy użyciu odwołania COM), aby upewnić się, że dane są dostępne tak długo, jak ich potrzebujesz.

## <a name="ccomenumimplm_spunk"></a><a name="m_spunk"></a>CComEnumImpl::m_spUnk

Ten inteligentny wskaźnik utrzymuje odwołanie do obiektu przekazane do [CComEnumImpl::Init](#init), zapewniając, że pozostaje żywy w okresie istnienia wylicznika.

```
CComPtr<IUnknown> m_spUnk;
```

## <a name="ccomenumimplm_begin"></a><a name="m_begin"></a>CComEnumImpl::m_begin

Wskaźnik do lokalizacji tuż poza ostatnim elementem tablicy zawierającej elementy, które mają być wyliczone.

```
T* m_begin;
```

## <a name="ccomenumimplm_end"></a><a name="m_end"></a>CComEnumImpl::m_end

Wskaźnik do pierwszego elementu tablicy zawierającego elementy, które mają być wyliczone.

```
T* m_end;
```

## <a name="ccomenumimplm_iter"></a><a name="m_iter"></a>CComEnumImpl::m_iter

Wskaźnik do bieżącego elementu tablicy zawierającej elementy, które mają być wyliczone.

```
T* m_iter;
```

## <a name="ccomenumimplm_dwflags"></a><a name="m_dwflags"></a>CComEnumImpl::m_dwFlags

Flagi przekazywane do [CComEnumImpl::Init](#init).

```
DWORD m_dwFlags;
```

## <a name="ccomenumimplnext"></a><a name="next"></a>CComEnumImpl::Następny

Ta metoda zapewnia implementację **Next** metody.

```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```

### <a name="parameters"></a>Parametry

*Celt*<br/>
[w] Liczba żądanych elementów.

*rgelt ( rgelt )*<br/>
[na zewnątrz] Tablica, która ma być wypełniona elementami.

*pceltFetched*<br/>
[na zewnątrz] Liczba elementów faktycznie zwróconych w *rgelt*. Może to być mniejsza niż *celt,* jeśli mniej niż *celt* elementy pozostały na liście.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="ccomenumimplreset"></a><a name="reset"></a>CComEnumImpl::Reset

Ta metoda zapewnia implementację **Reset** metody.

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="ccomenumimplskip"></a><a name="skip"></a>CComEnumImpl::Pomiń

Ta metoda zapewnia implementację **Skip** metody.

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Parametry

*Celt*<br/>
[w] Liczba elementów do pominięcia.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Zwraca E_INVALIDARG jeśli *celt* wynosi zero, zwraca S_FALSE, jeśli zwracane są mniej niż *elementy celt,* zwraca S_OK w przeciwnym razie.

## <a name="see-also"></a>Zobacz też

[Klasa IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)<br/>
[Klasa CComEnum](../../atl/reference/ccomenum-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
