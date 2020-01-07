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
ms.openlocfilehash: 740920225fc513a869b4a92344f87004831e4768
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298617"
---
# <a name="ccomptrbase-class"></a>Klasa CComPtrBase

Ta klasa stanowi podstawę dla klas wskaźników inteligentnych korzystających z procedur pamięci opartych na modelu COM.

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
|[CComPtrBase::~CComPtrBase](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComPtrBase:: Advise](#advise)|Wywołaj tę metodę, aby utworzyć połączenie między punktem połączenia `CComPtrBase`i ujściam klienta.|
|[CComPtrBase::Attach](#attach)|Wywołaj tę metodę, aby przejąć na własność istniejący wskaźnik.|
|[CComPtrBase:: CoCreateInstance](#cocreateinstance)|Wywołaj tę metodę, aby utworzyć obiekt klasy skojarzonej z określonym IDENTYFIKATORem klasy lub IDENTYFIKATORem programu.|
|[CComPtrBase::CopyTo](#copyto)|Wywołaj tę metodę, aby skopiować wskaźnik `CComPtrBase` do innej zmiennej wskaźnika.|
|[CComPtrBase::Detach](#detach)|Wywołaj tę metodę, aby zwolnić własność wskaźnika.|
|[CComPtrBase:: isequalobject](#isequalobject)|Wywołaj tę metodę, aby sprawdzić, czy określony `IUnknown` wskazuje na ten sam obiekt skojarzony z obiektem `CComPtrBase`.|
|[CComPtrBase:: QueryInterface](#queryinterface)|Wywołaj tę metodę, aby zwrócić wskaźnik do określonego interfejsu.|
|[CComPtrBase::Release](#release)|Wywołaj tę metodę, aby zwolnić interfejs.|
|[CComPtrBase:: SetSite](#setsite)|Wywołaj tę metodę, aby ustawić lokację obiektu `CComPtrBase` na `IUnknown` obiektu nadrzędnego.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComPtrBase:: operator T *](#operator_t_star)|Operator rzutowania.|
|[CComPtrBase:: operator!](#operator_not)|Operator NOT.|
|[CComPtrBase:: operator &](#operator_amp)|Operator &.|
|[CComPtrBase:: operator *](#operator_star)|Operator \*.|
|[CComPtrBase:: operator <](#ccomptrbase__operator lt)|Operator mniejszości.|
|[CComPtrBase:: operator = =](#operator_eq_eq)|Operator równości.|
|[CComPtrBase:: operator->](#operator_ptr)|Operator wskaźnika do elementów członkowskich.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComPtrBase::p](#p)|Zmienna elementu członkowskiego danych wskaźnika.|

## <a name="remarks"></a>Uwagi

Ta klasa stanowi podstawę dla innych inteligentnych wskaźników, w których używane są procedury zarządzania pamięcią COM, takie jak [CComQIPtr](../../atl/reference/ccomqiptr-class.md) i [CComPtr](../../atl/reference/ccomptr-class.md). Klasy pochodne dodają własne konstruktory i operatory, ale polegają na metodach dostarczonych przez `CComPtrBase`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcomcli. h

##  <a name="advise"></a>CComPtrBase:: Advise

Wywołaj tę metodę, aby utworzyć połączenie między punktem połączenia `CComPtrBase`i ujściam klienta.

```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
Wskaźnik do `IUnknown`klienta.

*IID*<br/>
Identyfikator GUID punktu połączenia. Zwykle jest to takie samo, jak interfejs wychodzący zarządzany przez punkt połączenia.

*Kreatora*<br/>
Wskaźnik do pliku cookie, który jednoznacznie identyfikuje połączenie.

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [AtlAdvise](connection-point-global-functions.md#atladvise) .

##  <a name="attach"></a>CComPtrBase:: Attach

Wywołaj tę metodę, aby przejąć na własność istniejący wskaźnik.

```
void Attach(T* p2) throw();
```

### <a name="parameters"></a>Parametry

*P2*<br/>
Obiekt `CComPtrBase` przejdzie na własność tego wskaźnika.

### <a name="remarks"></a>Uwagi

`Attach` wywołuje [CComPtrBase:: Release](#release) w istniejącej zmiennej składowej [CComPtrBase::p](#p) , a następnie przypisuje *P2* do `CComPtrBase::p`. Gdy obiekt `CComPtrBase` przejmuje własność wskaźnika, automatycznie wywoła `Release` na wskaźniku, który spowoduje usunięcie wskaźnika i wszelkich przyznanych danych, jeśli liczba odwołań w obiekcie przejdzie do 0.

##  <a name="dtor"></a>CComPtrBase:: ~ CComPtrBase

Destruktor.

```
~CComPtrBase() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia interfejs wskazywany przez `CComPtrBase`.

##  <a name="cocreateinstance"></a>CComPtrBase:: CoCreateInstance

Wywołaj tę metodę, aby utworzyć obiekt klasy skojarzonej z określonym IDENTYFIKATORem klasy lub IDENTYFIKATORem programu.

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

*szProgID*<br/>
Wskaźnik do identyfikatora ProgID używany do odzyskania identyfikatora CLSID.

*pUnkOuter*<br/>
Jeśli wartość jest równa NULL, wskazuje, że obiekt nie jest tworzony w ramach agregacji. Jeśli wartość nie jest równa NULL, jest wskaźnikiem do interfejsu `IUnknown` obiektu agregacji (kontrolowanie `IUnknown`).

*dwClsContext*<br/>
Kontekst, w którym zostanie uruchomiony kod zarządzający nowo utworzonym obiektem.

*rclsid*<br/>
Identyfikator CLSID skojarzony z danymi i kodem, który zostanie użyty do utworzenia obiektu.

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK dla sukcesu lub REGDB_E_CLASSNOTREG, CLASS_E_NOAGGREGATION, CO_E_CLASSSTRING lub E_NOINTERFACE w przypadku niepowodzenia. Opis tych błędów można znaleźć w tematach [CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) i [CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid) .

### <a name="remarks"></a>Uwagi

Jeśli zostanie wywołana pierwsza forma metody, [CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid) jest używana do odzyskania identyfikatora CLSID. Oba formularze następnie wywołują [CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli [CComPtrBase::p](#p) nie jest równa null.

##  <a name="copyto"></a>CComPtrBase:: CopyTo

Wywołaj tę metodę, aby skopiować wskaźnik `CComPtrBase` do innej zmiennej wskaźnika.

```
HRESULT CopyTo(T** ppT) throw();
```

### <a name="parameters"></a>Parametry

*ppT*<br/>
Adres zmiennej, która będzie odbierać wskaźnik `CComPtrBase`.

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu, E_POINTER w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Kopiuje wskaźnik `CComPtrBase` do *PPT*. Liczba odwołań dla zmiennej składowej [CComPtrBase::p](#p) jest zwiększana.

Błąd HRESULT zostanie zwrócony, jeśli wartość *PPT* jest równa null. W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli *PPT* będzie równa null.

##  <a name="detach"></a>CComPtrBase::D etach

Wywołaj tę metodę, aby zwolnić własność wskaźnika.

```
T* Detach() throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca kopię wskaźnika.

### <a name="remarks"></a>Uwagi

Zwalnia własność wskaźnika, ustawia zmienną składową danych [CComPtrBase::p](#p) na null i zwraca kopię wskaźnika.

##  <a name="isequalobject"></a>CComPtrBase:: isequalobject

Wywołaj tę metodę, aby sprawdzić, czy określony `IUnknown` wskazuje na ten sam obiekt skojarzony z obiektem `CComPtrBase`.

```
bool IsEqualObject(IUnknown* pOther) throw();
```

### <a name="parameters"></a>Parametry

*pOther*<br/>
`IUnknown *` do porównania.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość true, jeśli obiekty są identyczne, w przeciwnym razie false.

##  <a name="operator_not"></a>CComPtrBase:: operator!

Operator NOT.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość true, jeśli wskaźnik `CComHeapPtr` ma wartość NULL, w przeciwnym razie false.

##  <a name="operator_amp"></a>CComPtrBase:: operator &amp;

Operator &.

```
T** operator&() throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca adres obiektu wskazywanego przez obiekt `CComPtrBase`.

##  <a name="operator_star"></a>CComPtrBase:: operator \*

Operator \*.

```
T& operator*() const throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość [CComPtrBase::p](#p); oznacza to, że wskaźnik do obiektu, do którego odwołuje się obiekt `CComPtrBase`.

W przypadku kompilacji debugowania wystąpi błąd potwierdzenia, jeśli [CComPtrBase::p](#p) nie jest równa null.

##  <a name="operator_eq_eq"></a>CComPtrBase:: operator = =

Operator równości.

```
bool operator== (T* pT) const throw();
```

### <a name="parameters"></a>Parametry

*Zmiennoprzecinkow*<br/>
Wskaźnik do obiektu.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość true, jeśli `CComPtrBase` i *pt* wskazuje na ten sam obiekt, w przeciwnym razie false.

##  <a name="operator_ptr"></a>CComPtrBase:: operator-&gt;

Operator wskaźnika do składowej.

```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość zmiennej składowej danych [CComPtrBase::p](#p) .

### <a name="remarks"></a>Uwagi

Użyj tego operatora, aby wywołać metodę w klasie wskazywanej przez obiekt `CComPtrBase`. W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli element członkowski danych `CComPtrBase` wskazuje wartość NULL.

##  <a name="operator_lt"></a>CComPtrBase:: operator &lt;

Operator mniejszości.

```
bool operator<(T* pT) const throw();
```

### <a name="parameters"></a>Parametry

*Zmiennoprzecinkow*<br/>
Wskaźnik do obiektu.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość true, jeśli wskaźnik zarządzany przez bieżący obiekt jest mniejszy niż wskaźnik, do którego jest porównywany.

##  <a name="operator_t_star"></a>CComPtrBase:: operator T\*

Operator rzutowania.

```
operator T*() const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wskaźnik do typu danych obiektu zdefiniowanego w szablonie klasy.

##  <a name="p"></a>CComPtrBase::p

Zmienna elementu członkowskiego danych wskaźnika.

```
T* p;
```

### <a name="remarks"></a>Uwagi

Ta zmienna członkowska zawiera informacje o wskaźniku.

##  <a name="queryinterface"></a>CComPtrBase:: QueryInterface

Wywołaj tę metodę, aby zwrócić wskaźnik do określonego interfejsu.

```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```

### <a name="parameters"></a>Parametry

*Pytania*<br/>
Typ obiektu, którego wskaźnik interfejsu jest wymagany.

*miesięcznie*<br/>
Adres zmiennej wyjściowej, która odbiera żądany wskaźnik interfejsu.

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu lub E_NOINTERFACE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)).

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli *PP* nie jest równy null.

##  <a name="release"></a>CComPtrBase:: Release

Wywołaj tę metodę, aby zwolnić interfejs.

```
void Release() throw();
```

### <a name="remarks"></a>Uwagi

Interfejs jest wydawany, a [CComPtrBase::p](#p) ma wartość null.

##  <a name="setsite"></a>CComPtrBase:: SetSite

Wywołaj tę metodę, aby ustawić lokację obiektu `CComPtrBase` na `IUnknown` obiektu nadrzędnego.

```
HRESULT SetSite(IUnknown* punkParent) throw();
```

### <a name="parameters"></a>Parametry

*punkParent*<br/>
Wskaźnik do interfejsu `IUnknown` elementu nadrzędnego.

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite).

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
