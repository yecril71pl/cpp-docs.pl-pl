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
ms.openlocfilehash: 2104d98cbc068eb5d8f1408cdda0898fd55c9473
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467149"
---
# <a name="ccomenumimpl-class"></a>Klasa CComEnumImpl

Ta klasa zawiera implementację interfejsu modułu wyliczającego COM, gdzie elementy wyliczany są przechowywane w tablicy.

## <a name="syntax"></a>Składnia

```
template <class Base,
    const IID* piid, class T, class Copy>
class ATL_NO_VTABLE CComEnumImpl : public Base
```

#### <a name="parameters"></a>Parametry

*podstawowy*<br/>
Moduł wyliczający interfejsu COM. Zobacz [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) przykład.

*piid*<br/>
Wskaźnik do Identyfikatora interfejsu interfejsu modułu wyliczającego.

*T*<br/>
Typ elementu udostępnianych przez interfejs modułu wyliczającego.

*Kopiuj*<br/>
Jednorodnej [kopiowania klasy zasad](../../atl/atl-copy-policy-classes.md).

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|Konstruktor.|
|[CComEnumImpl:: ~ CComEnumImpl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComEnumImpl::Clone](#clone)|Implementacja **klonowania** wyliczenie metody interfejsu.|
|[CComEnumImpl::Init](#init)|Inicjuje modułu wyliczającego.|
|[CComEnumImpl::Next](#next)|Implementacja **dalej**.|
|[CComEnumImpl::Reset](#reset)|Implementacja **resetowania**.|
|[CComEnumImpl::Skip](#skip)|Implementacja **Pomiń**.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComEnumImpl::m_begin](#m_begin)|Wskaźnik do pierwszego elementu w tablicy.|
|[CComEnumImpl::m_dwFlags](#m_dwflags)|Skopiuj flagi przekazywane za pośrednictwem `Init`.|
|[CComEnumImpl::m_end](#m_end)|Wskaźnik do lokalizacji tuż za ostatnim elementem w tablicy.|
|[CComEnumImpl::m_iter](#m_iter)|Wskaźnik do bieżącego elementu w tablicy.|
|[CComEnumImpl::m_spUnk](#m_spunk)|`IUnknown` Wskaźnika obiektu dostarczenie kolekcji wyliczenia.|

## <a name="remarks"></a>Uwagi

Zobacz [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) przykład implementacje metod. `CComEnumImpl` udostępnia implementację dla interfejsu modułu wyliczającego COM, gdzie elementy wyliczany są przechowywane w tablicy. Ta klasa jest odpowiednikiem `IEnumOnSTLImpl` klasy, która dostarcza implementację interfejsu modułu wyliczającego oparte na kontenera standardowej biblioteki języka C++.

> [!NOTE]
>  Aby uzyskać szczegółowe informacje na temat dalszych różnic między `CComEnumImpl` i `IEnumOnSTLImpl`, zobacz [CComEnumImpl::Init](#init).

Zazwyczaj będzie *nie* musisz utworzyć własne klasy modułu wyliczającego, wynikających z tej implementacji interfejsu. Jeśli chcesz użyć dostarczonych ATL moduł wyliczający na podstawie tablicy jest bardziej powszechne, aby utworzyć wystąpienie [CComEnum](../../atl/reference/ccomenum-class.md).

Jednakże jeśli musisz podać niestandardowy moduł wyliczający, (na przykład taki, który uwidacznia interfejsy oprócz interfejsu modułu wyliczającego), może pochodzić z tej klasy. W tej sytuacji jest prawdopodobne, że musisz przesłonić [CComEnumImpl::Clone](#clone) metody w celu zapewnienia Twojej własnej implementacji.

Aby uzyskać więcej informacji, zobacz [kolekcje i wyliczenia ATL](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Base`

`CComEnumImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="ccomenumimpl"></a>  CComEnumImpl::CComEnumImpl

Konstruktor.

```
CComEnumImpl();
```

##  <a name="dtor"></a>  CComEnumImpl:: ~ CComEnumImpl

Destruktor.

```
~CComEnumImpl();
```

##  <a name="init"></a>  CComEnumImpl::Init

Tę metodę należy wywołać przed przekazaniem wskaźnik do interfejsu modułu wyliczającego do wszystkich klientów.

```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```

### <a name="parameters"></a>Parametry

*begin*<br/>
Wskaźnik do pierwszego elementu tablicy, zawierające elementy do wyliczenia.

*koniec*<br/>
Wskaźnik do lokalizacji tuż za ostatnim elementem tablicę zawierającą elementy do wyliczenia.

*pUnk*<br/>
[in] `IUnknown` Wskaźnika obiektu, który musi znajdować się aktywne w okresie istnienia modułu wyliczającego. Przekaż wartość NULL, jeśli taki obiekt nie istnieje.

*flagi*<br/>
Flagi, określające, czy moduł wyliczający należy przejęcie na własność tablicy lub utworzyć kopię. Możliwe wartości są opisane poniżej.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Tylko jeden raz wywołać tę metodę — Inicjowanie modułu wyliczającego, użyć go, a następnie je wyrzucać.

Jeśli przekazać wskaźniki do elementów w tablicy przechowywane w innym obiekcie i nie pytaj modułu wyliczającego, aby skopiować dane, możesz użyć *pUnk* parametru, aby upewnić się, że obiekt i Tablica przechowuje są dostępne dla tak długo, jak moduł wyliczający ich potrzebuje. Moduł wyliczający po prostu przechowuje odwołanie COM w obiekcie zapewnienie podtrzymywania połączenia. Odwołanie COM automatycznie jest zwalniany, gdy moduł wyliczający jest niszczona.

*Flagi* parametr umożliwia określenie, jak moduł wyliczający powinny traktować przekazany do niej elementy tablicy. *flagi* może mieć jedną z wartości z `CComEnumFlags` wyliczenie pokazano poniżej:

```
enum CComEnumFlags
   {
   AtlFlagNoCopy = 0,
   AtlFlagTakeOwnership = 2, // BitOwn
   AtlFlagCopy = 3           // BitOwn | BitCopy
   };
```

`AtlFlagNoCopy` oznacza to, że okres istnienia tablicy nie są kontrolowane przez moduł wyliczający. W tym przypadku tablica będzie statyczny lub obiekt identyfikowane przez *pUnk* będzie odpowiedzialny za opłacenie zwalnianie tablicy, gdy nie jest już potrzebny.

`AtlFlagTakeOwnership` oznacza, że będą kontrolowane przez moduł wyliczający zniszczenie tablicy. W tym przypadku tablicy musi być dynamicznie przydzielona za pomocą **nowe**. Moduł wyliczający spowoduje usunięcie tablicy w destruktorze. Zazwyczaj należy wprowadzić wartość NULL *pUnk*, mimo że nadal można przekazać prawidłowy wskaźnik, jeśli chcesz otrzymywać powiadomienia o zniszczenie modułu wyliczającego przyczyny.

`AtlFlagCopy` oznacza to, że nową tablicę, które ma zostać utworzony przez skopiowanie Tablica przekazana do `Init`. Okres istnienia nowej tablicy jest kontrolowany przez moduł wyliczający. Moduł wyliczający spowoduje usunięcie tablicy w destruktorze. Zazwyczaj należy wprowadzić wartość NULL *pUnk*, mimo że nadal można przekazać prawidłowy wskaźnik, jeśli chcesz otrzymywać powiadomienia o zniszczenie modułu wyliczającego przyczyny.

> [!NOTE]
>  Prototyp ta metoda określa elementy tablicy jako typu `T`, gdzie `T` został zdefiniowany jako parametr szablonu klasy. Jest to ten sam typ, który jest uwidaczniany za pomocą metody interfejsu COM [CComEnumImpl::Next](#next). Domniemanie tego jest fakt, że w przeciwieństwie do [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md), ta klasa nie obsługuje innego magazynu i dostępne typy danych. Typ danych elementów w tablicy musi być taki sam jak typ danych udostępnianych za pośrednictwem interfejsu COM.

##  <a name="clone"></a>  CComEnumImpl::Clone

Ta metoda zapewnia wykonania **klonowania** metoda przez utworzenie obiektu typu `CComEnum`, inicjując go przy użyciu tej samej tablicy i używane przez bieżący obiekt iteratora i zwraca interfejs na nowo utworzony obiekt.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Parametry

*ppEnum*<br/>
[out] Sklonowany interfejsu modułu wyliczającego na nowo utworzony obiekt z bieżącego modułu wyliczającego.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Należy pamiętać, że sklonowany moduły wyliczające nie należy wprowadzać własne kopiowania (lub przejmowanie na własność) z danymi używanymi przez oryginalny moduł wyliczający. Jeśli to konieczne, sklonowany moduły wyliczające zostanie zachowana, oryginalny moduł wyliczający aktywności (przy użyciu odwołanie COM) aby upewnić się, że dane są dostępne dla tak długo, jak ich potrzebują.

##  <a name="m_spunk"></a>  CComEnumImpl::m_spUnk

To inteligentny wskaźnik obsługuje odwołania na obiekt przekazany do [CComEnumImpl::Init](#init), zapewniając, że pozostaje aktywne w okresie istnienia modułu wyliczającego.

```
CComPtr<IUnknown> m_spUnk;
```

##  <a name="m_begin"></a>  CComEnumImpl::m_begin

Wskaźnik do lokalizacji tuż za ostatnim elementem tablicę zawierającą elementy do wyliczenia.

```
T* m_begin;
```

##  <a name="m_end"></a>  CComEnumImpl::m_end

Wskaźnik do pierwszego elementu tablicy, zawierające elementy do wyliczenia.

```
T* m_end;
```

##  <a name="m_iter"></a>  CComEnumImpl::m_iter

Wskaźnik do bieżącego elementu tablicy, zawierające elementy do wyliczenia.

```
T* m_iter;
```

##  <a name="m_dwflags"></a>  CComEnumImpl::m_dwFlags

Flagi przekazywane do [CComEnumImpl::Init](#init).

```
DWORD m_dwFlags;
```

##  <a name="next"></a>  CComEnumImpl::Next

Ta metoda zapewnia wykonania **dalej** metody.

```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```

### <a name="parameters"></a>Parametry

*celt*<br/>
[in] Liczba elementów żądanie.

*rgelt*<br/>
[out] Tablica, która ma zostać wypełniony przy użyciu elementów.

*pceltFetched*<br/>
[out] Liczba elementów, które faktycznie są zwracane w *rgelt*. Może to być mniejszy niż *celt* Jeśli mniej niż *celt* elementy pozostają na liście.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="reset"></a>  CComEnumImpl::Reset

Ta metoda zapewnia wykonania **resetowania** metody.

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="skip"></a>  CComEnumImpl::Skip

Ta metoda zapewnia wykonania **Pomiń** metody.

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Parametry

*celt*<br/>
[in] Liczba elementów do pominięcia.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Zwraca E_INVALIDARG, jeśli *celt* wynosi zero, zwraca wartość S_FALSE, jeśli są mniejsze niż *celt* elementy zostaną zwrócone, w przeciwnym razie zwraca wartość S_OK.

## <a name="see-also"></a>Zobacz też

[Klasa IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)<br/>
[Klasa CComEnum](../../atl/reference/ccomenum-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
