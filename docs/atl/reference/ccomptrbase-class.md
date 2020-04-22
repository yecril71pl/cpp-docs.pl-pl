---
title: Klasa CComPtrBase
ms.date: 11/04/2016
f1_keywords:
- CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase::Advise
- ATLCOMCLI/ATL::CComPtrBase::Attach
- ATLCOMCLI/ATL::CComPtrBase::CoCreateInstance
- ATLCOMCLI/ATL::CComPtrBase::CopyTo
- ATLCOMCLI/ATL::CComPtrBase::Detach
- ATLCOMCLI/ATL::CComPtrBase::IsEqualObject
- ATLCOMCLI/ATL::CComPtrBase::QueryInterface
- ATLCOMCLI/ATL::CComPtrBase::Release
- ATLCOMCLI/ATL::CComPtrBase::SetSite
- ATLCOMCLI/ATL::CComPtrBase::p
helpviewer_keywords:
- CComPtrBase class
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
ms.openlocfilehash: 9c62cc912b3fea3ea68390882bdda37cbfb25a7e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747761"
---
# <a name="ccomptrbase-class"></a>Klasa CComPtrBase

Ta klasa stanowi podstawę dla inteligentnych klas wskaźnika przy użyciu procedur pamięci opartych na kom.

## <a name="syntax"></a>Składnia

```
template <class T>
class CComPtrBase
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ obiektu, do którego odwołuje się inteligentny wskaźnik.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Baza CComPtrBase::~CComPtrBase](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComPtrBase::Doradzić](#advise)|Wywołanie tej metody, aby `CComPtrBase`utworzyć połączenie między punktem połączenia "s i ujścia klienta.|
|[CComPtrBase::Dołącz](#attach)|Wywołanie tej metody, aby przejąć na własność istniejącego wskaźnika.|
|[CComPtrBase::CoCreateInstance](#cocreateinstance)|Wywołanie tej metody, aby utworzyć obiekt klasy skojarzonej z określonym identyfikatorem klasy lub identyfikatorem programu.|
|[CComPtrBase::CopyTo](#copyto)|Wywołanie tej metody, aby skopiować `CComPtrBase` wskaźnik do innej zmiennej wskaźnika.|
|[CComPtrBase::Detach](#detach)|Wywołanie tej metody, aby zwolnić własność wskaźnika.|
|[CComPtrBase::IsEqualObject](#isequalobject)|Wywołanie tej metody, `IUnknown` aby sprawdzić, czy określone `CComPtrBase` punkty do tego samego obiektu skojarzonego z obiektem.|
|[CComPtrBase::QueryInterface](#queryinterface)|Wywołanie tej metody, aby zwrócić wskaźnik do określonego interfejsu.|
|[CComPtrBase::Release](#release)|Wywołanie tej metody, aby zwolnić interfejs.|
|[CComPtrBase::SetSite](#setsite)|Wywołanie tej metody, aby `CComPtrBase` ustawić `IUnknown` witrynę obiektu do obiektu nadrzędnego.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComPtrBase::operator T*](#operator_t_star)|Operator odlewu.|
|[CComPtrBase::operator !](#operator_not)|Operator NOT.|
|[CComPtrBase::operator &](#operator_amp)|Operator &.|
|[CComPtrBase::operator *](#operator_star)|Operator \*.|
|[CComPtrBase::operator <](#ccomptrbase__operator lt)|Operator mniej niż.|
|[CComPtrBase::operator ==](#operator_eq_eq)|Operator równości.|
|[CComPtrBase::operator ->](#operator_ptr)|Operator wskaźnik-do-członków.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComPtrBase::p](#p)|Zmienna elementu członkowskiego danych wskaźnika.|

## <a name="remarks"></a>Uwagi

Ta klasa stanowi podstawę dla innych inteligentnych wskaźników, które używają procedur zarządzania pamięcią COM, takich jak [CComQIPtr](../../atl/reference/ccomqiptr-class.md) i [CComPtr](../../atl/reference/ccomptr-class.md). Klasy pochodne dodają własne konstruktory i operatory, ale opierają się na metodach dostarczonych przez `CComPtrBase`program .

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcomcli.h

## <a name="ccomptrbaseadvise"></a><a name="advise"></a>CComPtrBase::Doradzić

Wywołanie tej metody, aby `CComPtrBase`utworzyć połączenie między punktem połączenia "s i ujścia klienta.

```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
Wskaźnik do klienta `IUnknown`.

*Iid*<br/>
Identyfikator GUID punktu połączenia. Zazwyczaj jest to taka sama jak interfejs wychodzący zarządzany przez punkt połączenia.

*Pdw*<br/>
Wskaźnik do pliku cookie, który jednoznacznie identyfikuje połączenie.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Zobacz [AtlAdvise aby](connection-point-global-functions.md#atladvise) uzyskać więcej informacji.

## <a name="ccomptrbaseattach"></a><a name="attach"></a>CComPtrBase::Dołącz

Wywołanie tej metody, aby przejąć na własność istniejącego wskaźnika.

```cpp
void Attach(T* p2) throw();
```

### <a name="parameters"></a>Parametry

*p2*<br/>
Obiekt `CComPtrBase` przejmie na własność ten wskaźnik.

### <a name="remarks"></a>Uwagi

`Attach`wywołuje [CComPtrBase::Release](#release) na istniejącej zmiennej [CComPtrBase::p,](#p) a `CComPtrBase::p`następnie przypisuje *p2* do . Gdy `CComPtrBase` obiekt przejmuje na własność wskaźnik, automatycznie `Release` wywoła wskaźnik, który usunie wskaźnik i wszystkie przydzielone dane, jeśli liczba odwołań na obiekcie przejdzie do 0.

## <a name="ccomptrbaseccomptrbase"></a><a name="dtor"></a>Baza CComPtrBase::~CComPtrBase

Destruktor.

```
~CComPtrBase() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia interfejs wskazany `CComPtrBase`przez .

## <a name="ccomptrbasecocreateinstance"></a><a name="cocreateinstance"></a>CComPtrBase::CoCreateInstance

Wywołanie tej metody, aby utworzyć obiekt klasy skojarzonej z określonym identyfikatorem klasy lub identyfikatorem programu.

```
HRESULT CoCreateInstance(
    LPCOLESTR szProgID,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();

HRESULT CoCreateInstance(
    REFCLSID rclsid,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();
```

### <a name="parameters"></a>Parametry

*szProgID (szProgID)*<br/>
Wskaźnik do identyfikatora progid, używany do odzyskiwania identyfikatora CLSID.

*pUnkOuter (Nieunikat.*<br/>
Jeśli NULL, wskazuje, że obiekt nie jest tworzony jako część agregacji. Jeśli nie- NULL, jest wskaźnikiem do `IUnknown` interfejsu obiektu `IUnknown`agregacji (controlling ).

*dwClsContext*<br/>
Kontekst, w którym zostanie uruchomiony kod, który zarządza nowo utworzonym obiektem.

*rclsid ( rclsid )*<br/>
IDENTYFIKATOR CLSID skojarzony z danymi i kodem, który będzie używany do tworzenia obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub REGDB_E_CLASSNOTREG, CLASS_E_NOAGGREGATION, CO_E_CLASSSTRING lub E_NOINTERFACE na niepowodzenie. Zobacz [CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) i [CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid) opis tych błędów.

### <a name="remarks"></a>Uwagi

Jeśli wywoływana jest pierwsza forma metody, [CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid) jest używany do odzyskiwania CLSID. Oba formularze następnie wywołać [CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli [CComPtrBase::p](#p) nie jest równa NULL.

## <a name="ccomptrbasecopyto"></a><a name="copyto"></a>CComPtrBase::CopyTo

Wywołanie tej metody, aby skopiować `CComPtrBase` wskaźnik do innej zmiennej wskaźnika.

```
HRESULT CopyTo(T** ppT) throw();
```

### <a name="parameters"></a>Parametry

*Ppt*<br/>
Adres zmiennej, która `CComPtrBase` otrzyma wskaźnik.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces, E_POINTER na porażkę.

### <a name="remarks"></a>Uwagi

Kopiuje `CComPtrBase` wskaźnik do *ppT*. Liczba odwołań dla zmiennej [CComPtrBase::p](#p) element członkowski jest zwiększana.

Błąd HRESULT zostanie zwrócony, jeśli *ppT* jest równa null. W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli *ppT* jest równa NULL.

## <a name="ccomptrbasedetach"></a><a name="detach"></a>CComPtrBase::Detach

Wywołanie tej metody, aby zwolnić własność wskaźnika.

```
T* Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca kopię wskaźnika.

### <a name="remarks"></a>Uwagi

Zwalnia własność wskaźnika, ustawia zmienną elementu członkowskiego [CComPtrBase::p](#p) na NULL i zwraca kopię wskaźnika.

## <a name="ccomptrbaseisequalobject"></a><a name="isequalobject"></a>CComPtrBase::IsEqualObject

Wywołanie tej metody, `IUnknown` aby sprawdzić, czy określone `CComPtrBase` punkty do tego samego obiektu skojarzonego z obiektem.

```
bool IsEqualObject(IUnknown* pOther) throw();
```

### <a name="parameters"></a>Parametry

*pOther*<br/>
Do `IUnknown *` porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli obiekty są identyczne, false inaczej.

## <a name="ccomptrbaseoperator-"></a><a name="operator_not"></a>CComPtrBase::operator !

Operator NOT.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość `CComHeapPtr` true, jeśli wskaźnik jest równy null, false w przeciwnym razie.

## <a name="ccomptrbaseoperator-amp"></a><a name="operator_amp"></a>CComPtrBase::operator&amp;

Operator &.

```
T** operator&() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca adres obiektu wskazywalnego przez `CComPtrBase` obiekt.

## <a name="ccomptrbaseoperator-"></a><a name="operator_star"></a>CComPtrBase::operator\*

Operator \*.

```
T& operator*() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość [CComPtrBase::p](#p); oznacza to, że wskaźnik do obiektu, do którego odwołuje się `CComPtrBase` obiekt.

Jeśli debugowanie kompilacji, błąd potwierdzenia wystąpi, jeśli [CComPtrBase::p](#p) nie jest równa NULL.

## <a name="ccomptrbaseoperator-"></a><a name="operator_eq_eq"></a>CComPtrBase::operator ==

Operator równości.

```
bool operator== (T* pT) const throw();
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
Wskaźnik do obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość `CComPtrBase` true if i *pT* wskazują na ten sam obiekt, false w przeciwnym razie.

## <a name="ccomptrbaseoperator--gt"></a><a name="operator_ptr"></a>CComPtrBase::operator -&gt;

Operator wskaźnik-element.

```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość zmiennej elementu członkowskiego [CComPtrBase::p](#p) danych.

### <a name="remarks"></a>Uwagi

Ten operator służy do wywoływania metody w `CComPtrBase` klasie wskazywaluj przez obiekt. W kompilacjach debugowania błąd potwierdzenia `CComPtrBase` wystąpi, jeśli element członkowski danych wskazuje wartość NULL.

## <a name="ccomptrbaseoperator-lt"></a><a name="operator_lt"></a>CComPtrBase::operator&lt;

Operator mniej niż.

```
bool operator<(T* pT) const throw();
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
Wskaźnik do obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli wskaźnik zarządzany przez bieżący obiekt jest mniejszy niż wskaźnik, do którego jest porównywany.

## <a name="ccomptrbaseoperator-t"></a><a name="operator_t_star"></a>CComPtrBase::operator T\*

Operator odlewu.

```
operator T*() const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wskaźnik do typu danych obiektu zdefiniowanego w szablonie klasy.

## <a name="ccomptrbasep"></a><a name="p"></a>CComPtrBase::p

Zmienna elementu członkowskiego danych wskaźnika.

```
T* p;
```

### <a name="remarks"></a>Uwagi

Ta zmienna elementu członkowskiego zawiera informacje o wskaźniku.

## <a name="ccomptrbasequeryinterface"></a><a name="queryinterface"></a>CComPtrBase::QueryInterface

Wywołanie tej metody, aby zwrócić wskaźnik do określonego interfejsu.

```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Typ obiektu, którego wskaźnik interfejsu jest wymagany.

*S*<br/>
Adres zmiennej wyjściowej odbieranej żądanego wskaźnika interfejsu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub E_NOINTERFACE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [IUnknown::QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)).

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli *pp* nie jest równa NULL.

## <a name="ccomptrbaserelease"></a><a name="release"></a>CComPtrBase::Release

Wywołanie tej metody, aby zwolnić interfejs.

```cpp
void Release() throw();
```

### <a name="remarks"></a>Uwagi

Interfejs jest zwalniany, a [CComPtrBase::p](#p) jest ustawiona na wartość NULL.

## <a name="ccomptrbasesetsite"></a><a name="setsite"></a>CComPtrBase::SetSite

Wywołanie tej metody, aby `CComPtrBase` ustawić `IUnknown` witrynę obiektu do obiektu nadrzędnego.

```
HRESULT SetSite(IUnknown* punkParent) throw();
```

### <a name="parameters"></a>Parametry

*punkRożka*<br/>
Wskaźnik do `IUnknown` interfejsu nadrzędnego.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite).

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
