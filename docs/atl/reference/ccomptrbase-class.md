---
title: Klasa CComPtrBase | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CComPtrBase class
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 70ba26e5893b21393a3466ae7cf1c6cea43b81ef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070161"
---
# <a name="ccomptrbase-class"></a>Klasa CComPtrBase

Ta klasa stanowi podstawę dla klas inteligentnego wskaźnika za pomocą procedury opartym na modelu COM pamięci.

## <a name="syntax"></a>Składnia

```
template <class T>
class CComPtrBase
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ obiektu, być przywoływane przez inteligentny wskaźnik.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComPtrBase:: ~ CComPtrBase](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComPtrBase::Advise](#advise)|Wywołanie tej metody, aby utworzyć połączenie między `CComPtrBase`przez punkt połączenia a zbiornikiem klienta.|
|[CComPtrBase::Attach](#attach)|Wywołaj tę metodę, aby przejąć prawo własności istniejącego wskaźnika.|
|[CComPtrBase::CoCreateInstance](#cocreateinstance)|Wywołanie tej metody, aby utworzyć obiekt klasy skojarzone z określonego Identyfikatora klasy lub identyfikator programu.|
|[CComPtrBase::CopyTo](#copyto)|Wywołaj tę metodę, aby skopiować `CComPtrBase` wskaźnika do innej zmiennej wskaźnika.|
|[CComPtrBase::Detach](#detach)|Wywołaj tę metodę, aby zwolnić własność wskaźnika.|
|[CComPtrBase::IsEqualObject](#isequalobject)|Wywołaj tę metodę, aby sprawdzić, czy określony `IUnknown` wskazuje ten sam obiekt skojarzony z `CComPtrBase` obiektu.|
|[CComPtrBase::QueryInterface](#queryinterface)|Wywołaj tę metodę, aby zwrócić wskaźnik do określonego interfejsu.|
|[CComPtrBase::Release](#release)|Wywołaj tę metodę, aby zwolnić interfejsu.|
|[CComPtrBase::SetSite](#setsite)|Wywołanie tej metody można ustawić po witrynie `CComPtrBase` obiekt `IUnknown` obiektu nadrzędnego.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComPtrBase::operator T *](#operator_t_star)|Operator rzutowania.|
|[CComPtrBase::operator!](#operator_not)|NOT operator.|
|[CComPtrBase::operator &](#operator_amp)|& — Operator.|
|[CComPtrBase::operator *](#operator_star)|Operator \*.|
|[CComPtrBase::operator <](#ccomptrbase__operator lt)|Mniej-niż operator.|
|[CComPtrBase::operator ==](#operator_eq_eq)|Operator równości.|
|[CComPtrBase::operator ->](#operator_ptr)|Operator wskaźników do elementów członkowskich.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComPtrBase::p](#p)|Zmiennej składowej danych wskaźnika.|

## <a name="remarks"></a>Uwagi

Ta klasa stanowi podstawę dla innych inteligentnych wskaźników, które używają procedury zarządzania pamięci dla modelu COM, takich jak [CComQIPtr](../../atl/reference/ccomqiptr-class.md) i [CComPtr](../../atl/reference/ccomptr-class.md). Klasy pochodne dodać własne operatory i konstruktory, ale zależą od metod dostarczonych przez `CComPtrBase`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcomcli.h

##  <a name="advise"></a>  CComPtrBase::Advise

Wywołanie tej metody, aby utworzyć połączenie między `CComPtrBase`przez punkt połączenia a zbiornikiem klienta.

```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
Wskaźnik do klienta `IUnknown`.

*IID*<br/>
Identyfikator GUID punktu połączenia. Zazwyczaj jest taka sama jak interfejsu wychodzącego zarządzane przez punkt połączenia.

*PDW*<br/>
Wskaźnik do pliku cookie, który unikatowo identyfikuje połączenie.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Zobacz [AtlAdvise](connection-point-global-functions.md#atladvise) Aby uzyskać więcej informacji.

##  <a name="attach"></a>  CComPtrBase::Attach

Wywołaj tę metodę, aby przejąć prawo własności istniejącego wskaźnika.

```
void Attach(T* p2) throw();
```

### <a name="parameters"></a>Parametry

*P2*<br/>
`CComPtrBase` Obiekt będzie przejęcie na własność ten wskaźnik.

### <a name="remarks"></a>Uwagi

`Attach` wywołania [CComPtrBase::Release](#release) na istniejące [CComPtrBase::p](#p) zmiennej składowej, a następnie przypisuje *p2* do `CComPtrBase::p`. Gdy `CComPtrBase` obiektu przejmuje na własność wskaźnika, będzie automatycznie wywoływać `Release` we wskaźniku, co spowoduje usunięcie wskaźnika i wszystkie przydzielone dane, jeśli licznik odwołań obiektu wynosić 0.

##  <a name="dtor"></a>  CComPtrBase:: ~ CComPtrBase

Destruktor.

```
~CComPtrBase() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia interfejs wskazywany przez `CComPtrBase`.

##  <a name="cocreateinstance"></a>  CComPtrBase::CoCreateInstance

Wywołanie tej metody, aby utworzyć obiekt klasy skojarzone z określonego Identyfikatora klasy lub identyfikator programu.

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
Wskaźnik do ProgID, używał do odzyskiwania identyfikator CLSID.

*pUnkOuter*<br/>
Jeśli ma wartość NULL, wskazuje, że obiekt nie został utworzony jako część agregacji. Jeśli innych niż NULL, jest wskaźnikiem do obiektu agregacji `IUnknown` interfejsu (kontrolowanie `IUnknown`).

*dwClsContext*<br/>
Kontekst, w którym będzie uruchamiany kod, który zarządza nowo utworzony obiekt.

*rclsid*<br/>
Identyfikator CLSID skojarzonego z danymi i kod, który będzie używany do utworzenia obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w sukces, lub REGDB_E_CLASSNOTREG, CLASS_E_NOAGGREGATION, CO_E_CLASSSTRING lub E_NOINTERFACE w przypadku niepowodzenia. Zobacz [CoCreateClassInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance) i [CLSIDFromProgID](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromprogid) opis tych błędów.

### <a name="remarks"></a>Uwagi

Jeśli pierwszy formularz metoda jest wywoływana, [CLSIDFromProgID](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromprogid) służy do odzyskania identyfikator CLSID. Następnie wywołaj obie formy [CoCreateClassInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).

W kompilacjach debugowania, wystąpi błąd asercji Jeśli [CComPtrBase::p](#p) nie jest równa NULL.

##  <a name="copyto"></a>  CComPtrBase::CopyTo

Wywołaj tę metodę, aby skopiować `CComPtrBase` wskaźnika do innej zmiennej wskaźnika.

```
HRESULT CopyTo(T** ppT) throw();
```

### <a name="parameters"></a>Parametry

*ppT*<br/>
Adres zmiennej, która otrzyma `CComPtrBase` wskaźnika.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia E_POINTER w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Kopiuje `CComPtrBase` wskaźnik do *ppT*. Możesz liczyć na odwołanie [CComPtrBase::p](#p) zmiennej elementu członkowskiego jest zwiększany.

Błąd HRESULT zostanie zwrócona, jeśli *ppT* jest równa NULL. W kompilacjach debugowania, wystąpi błąd asercji Jeśli *ppT* jest równa NULL.

##  <a name="detach"></a>  CComPtrBase::Detach

Wywołaj tę metodę, aby zwolnić własność wskaźnika.

```
T* Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca kopię wskaźnika.

### <a name="remarks"></a>Uwagi

Uwalnia własność wskaźnika, ustawia [CComPtrBase::p](#p) zmiennej składowej danych na wartość NULL i zwraca kopię wskaźnika.

##  <a name="isequalobject"></a>  CComPtrBase::IsEqualObject

Wywołaj tę metodę, aby sprawdzić, czy określony `IUnknown` wskazuje ten sam obiekt skojarzony z `CComPtrBase` obiektu.

```
bool IsEqualObject(IUnknown* pOther) throw();
```

### <a name="parameters"></a>Parametry

*pOther*<br/>
`IUnknown *` Do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli obiekty są identyczne, wartość false w przeciwnym razie.

##  <a name="operator_not"></a>  CComPtrBase::operator!

NOT operator.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli `CComHeapPtr` wskaźnik jest równa NULL, wartość false w przeciwnym razie.

##  <a name="operator_amp"></a>  CComPtrBase::operator &amp;

& — Operator.

```
T** operator&() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca adres obiektu wskazywanego przez `CComPtrBase` obiektu.

##  <a name="operator_star"></a>  CComPtrBase::operator \*

Operator \*.

```
T& operator*() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość [CComPtrBase::p](#p); oznacza to, wskaźnik do obiektu, który odwołuje się `CComPtrBase` obiektu.

Jeśli wydajność debugowania kompilacji, potwierdzenie wystąpi błąd Jeśli [CComPtrBase::p](#p) nie jest równa NULL.

##  <a name="operator_eq_eq"></a>  CComPtrBase::operator ==

Operator równości.

```
bool operator== (T* pT) const throw();
```

### <a name="parameters"></a>Parametry

*(CZAS PACYFICZNY)*<br/>
Wskaźnik do obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli `CComPtrBase` i *pT* wskazują ten sam obiekt false w przeciwnym razie.

##  <a name="operator_ptr"></a>  CComPtrBase::operator-&gt;

Operator wskaźnika do elementu członkowskiego.

```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość [CComPtrBase::p](#p) zmiennej składowej danych.

### <a name="remarks"></a>Uwagi

Użyj tego operatora do wywołania metody w klasie, do których prowadzą `CComPtrBase` obiektu. W kompilacjach do debugowania błędu potwierdzenia wystąpi `CComPtrBase` wskazuje element członkowski danych o wartości NULL.

##  <a name="operator_lt"></a>  CComPtrBase::operator &lt;

Mniej-niż operator.

```
bool operator<(T* pT) const throw();
```

### <a name="parameters"></a>Parametry

*(CZAS PACYFICZNY)*<br/>
Wskaźnik do obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli wskaźnik jest zarządzany przez bieżący obiekt jest mniejszy niż wskaźnika, które są porównywane.

##  <a name="operator_t_star"></a>  CComPtrBase::operator T\*

Operator rzutowania.

```
operator T*() const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wskaźnik do typu danych obiektu zdefiniowane w szablonie klasy.

##  <a name="p"></a>  CComPtrBase::p

Zmiennej składowej danych wskaźnika.

```
T* p;
```

### <a name="remarks"></a>Uwagi

Ta zmienna członka przechowuje informacje o wskaźnikach.

##  <a name="queryinterface"></a>  CComPtrBase::QueryInterface

Wywołaj tę metodę, aby zwrócić wskaźnik do określonego interfejsu.

```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```

### <a name="parameters"></a>Parametry

*PYTANIA I ODPOWIEDZI*<br/>
Typ obiektu, którego wskaźnika interfejsu jest wymagana.

*strony*<br/>
Adres zmiennej dane wyjściowe, która otrzymuje wskaźnik żądanego interfejsu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w sukces lub E_NOINTERFACE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [IUnknown::QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)).

W kompilacjach debugowania, wystąpi błąd asercji Jeśli *pp* nie jest równa NULL.

##  <a name="release"></a>  CComPtrBase::Release

Wywołaj tę metodę, aby zwolnić interfejsu.

```
void Release() throw();
```

### <a name="remarks"></a>Uwagi

Interfejs jest zwalniana, a [CComPtrBase::p](#p) ma wartość NULL.

##  <a name="setsite"></a>  CComPtrBase::SetSite

Wywołanie tej metody można ustawić po witrynie `CComPtrBase` obiekt `IUnknown` obiektu nadrzędnego.

```
HRESULT SetSite(IUnknown* punkParent) throw();
```

### <a name="parameters"></a>Parametry

*punkParent*<br/>
Wskaźnik do `IUnknown` interfejsu elementu nadrzędnego.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite).

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)
