---
title: Klasa CBindStatusCallback
ms.date: 11/04/2016
f1_keywords:
- CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback::CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback::Download
- ATLCTL/ATL::CBindStatusCallback::GetBindInfo
- ATLCTL/ATL::CBindStatusCallback::GetPriority
- ATLCTL/ATL::CBindStatusCallback::OnDataAvailable
- ATLCTL/ATL::CBindStatusCallback::OnLowResource
- ATLCTL/ATL::CBindStatusCallback::OnObjectAvailable
- ATLCTL/ATL::CBindStatusCallback::OnProgress
- ATLCTL/ATL::CBindStatusCallback::OnStartBinding
- ATLCTL/ATL::CBindStatusCallback::OnStopBinding
- ATLCTL/ATL::CBindStatusCallback::StartAsyncDownload
- ATLCTL/ATL::CBindStatusCallback::m_dwAvailableToRead
- ATLCTL/ATL::CBindStatusCallback::m_dwTotalRead
- ATLCTL/ATL::CBindStatusCallback::m_pFunc
- ATLCTL/ATL::CBindStatusCallback::m_pT
- ATLCTL/ATL::CBindStatusCallback::m_spBindCtx
- ATLCTL/ATL::CBindStatusCallback::m_spBinding
- ATLCTL/ATL::CBindStatusCallback::m_spMoniker
- ATLCTL/ATL::CBindStatusCallback::m_spStream
helpviewer_keywords:
- asynchronous data transfer [C++]
- data transfer [C++]
- data transfer [C++], asynchronous
- CBindStatusCallback class
ms.assetid: 0f5da276-6031-4418-b2a9-a4750ef29e77
ms.openlocfilehash: 16e97b994ad30fdd4c255dac45e8b56fd04f663a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583316"
---
# <a name="cbindstatuscallback-class"></a>Klasa CBindStatusCallback

Ta klasa implementuje `IBindStatusCallback` interfejsu.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS | BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa zawierająca funkcję, która zostanie wywołana, ponieważ dane są odebrane.

*nBindFlags*<br/>
Określa flagi powiązania, które są zwracane przez [GetBindInfo](#getbindinfo). Domyślna implementacja ustawia asynchronicznego powiązanie, pobiera najnowszą wersję obiektu danych/i pobrane dane przechowywane w pamięci podręcznej dysku.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBindStatusCallback::CBindStatusCallback](#cbindstatuscallback)|Konstruktor.|
|[CBindStatusCallback:: ~ CBindStatusCallback](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBindStatusCallback::Download](#download)|Tworzy metodę statyczną, która rozpoczyna się proces pobierania `CBindStatusCallback` obiektu i wywołania `StartAsyncDownload`.|
|[CBindStatusCallback::GetBindInfo](#getbindinfo)|Metoda wywoływana przez asynchroniczne moniker na żądanie informacji od typu powiązania ma zostać utworzony.|
|[CBindStatusCallback::GetPriority](#getpriority)|Metoda wywoływana przez asynchroniczne moniker można pobrać priorytet Operacja powiązania. Zwraca implementację ATL `E_NOTIMPL`.|
|[CBindStatusCallback::OnDataAvailable](#ondataavailable)|Wywoływana w celu zapewnienia danych do aplikacji po jej udostępnieniu. Odczytuje dane, a następnie wywołuje funkcję wymagał, aby użyć danych.|
|[CBindStatusCallback::OnLowResource](#onlowresource)|Wywołuje się, gdy brakuje zasobów. Implementacja biblioteki ATL, zwraca wartość S_OK.|
|[CBindStatusCallback::OnObjectAvailable](#onobjectavailable)|Metoda wywoływana przez asynchroniczne monikera do przekazania obiektu wskaźnik interfejsu do aplikacji. Implementacja biblioteki ATL, zwraca wartość S_OK.|
|[CBindStatusCallback::OnProgress](#onprogress)|Wywołuje się, by wskazać proces pobierania danych. Implementacja biblioteki ATL, zwraca wartość S_OK.|
|[CBindStatusCallback::OnStartBinding](#onstartbinding)|Wywołuje się, gdy powiązanie jest uruchomiona.|
|[CBindStatusCallback::OnStopBinding](#onstopbinding)|Wywołuje się, gdy zatrzymano transfer danych asynchronicznego.|
|[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)|Inicjuje dostępnych bajtów i bajtów odczytanych na zero, tworzy obiekt strumienia typu push z adresu URL i wywołania `OnDataAvailable` za każdym razem, gdy dane są dostępne.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CBindStatusCallback::m_dwAvailableToRead](#m_dwavailabletoread)|Liczba bajtów dostępnych do odczytu.|
|[CBindStatusCallback::m_dwTotalRead](#m_dwtotalread)|Całkowita liczba bajtów do odczytu.|
|[CBindStatusCallback::m_pFunc](#m_pfunc)|Wskaźnik do funkcji wywoływane, gdy dane są dostępne.|
|[CBindStatusCallback::m_pT](#m_pt)|Wskaźnik do obiektu żądającego transferu asynchronicznego danych.|
|[CBindStatusCallback::m_spBindCtx](#m_spbindctx)|Wskaźnik do [IBindCtx](/windows/desktop/api/objidl/nn-objidl-ibindctx) interfejs dla bieżącej operacji wiązania.|
|[CBindStatusCallback::m_spBinding](#m_spbinding)|Wskaźnik do `IBinding` interfejs dla bieżącej operacji wiązania.|
|[CBindStatusCallback::m_spMoniker](#m_spmoniker)|Wskaźnik do [imoniker —](/windows/desktop/api/objidl/nn-objidl-imoniker) interfejsu dla adresu URL do użycia.|
|[CBindStatusCallback::m_spStream](#m_spstream)|Wskaźnik do [IStream](/windows/desktop/api/objidl/nn-objidl-istream) interfejsu do transferu danych.|

## <a name="remarks"></a>Uwagi

`CBindStatusCallback` Klasy implementuje `IBindStatusCallback` interfejsu. `IBindStatusCallback` muszą być zaimplementowane przez aplikację, więc może ona odbierać powiadomienia z transferu asynchronicznego danych. Używa asynchronicznej krótkiej nazwy systemu `IBindStatusCallback` metody służące do wysyłania i odbierania informacji o danych asynchroniczne przesyłanie do i z obiektu.

Zazwyczaj `CBindStatusCallback` obiekt jest skojarzony z operacją określonego powiązania. Na przykład w [ASYNC](../../visual-cpp-samples.md) próbki, gdy ustawiona jest właściwość URL tworzy `CBindStatusCallback` obiektów w wywołaniu `Download`:

[!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]

Moniker asynchroniczne za pomocą funkcji wywołania zwrotnego `OnData` do wywołania aplikacji, gdy ma ona danych. Asynchroniczne moniker jest dostarczany przez system.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CComObjectRootBase`

`IBindStatusCallback`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`CBindStatusCallback`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

##  <a name="cbindstatuscallback"></a>  CBindStatusCallback::CBindStatusCallback

Konstruktor.

```
CBindStatusCallback();
```

### <a name="remarks"></a>Uwagi

Tworzy obiekt, aby otrzymywać powiadomienia dotyczące transferu asynchronicznego danych. Zazwyczaj jeden obiekt jest tworzony dla każdej operacji wiązania.

Konstruktor inicjuje również [m_pT](#m_pt) i [m_pFunc](#m_pfunc) na wartość NULL.

##  <a name="dtor"></a>  CBindStatusCallback:: ~ CBindStatusCallback

Destruktor.

```
~CBindStatusCallback();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby.

##  <a name="download"></a>  CBindStatusCallback::Download

Tworzy `CBindStatusCallback` obiektów i wywołuje `StartAsyncDownload` można uruchomić pobierania danych asynchronicznie z określonego adresu URL.

```
static HRESULT Download(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Parametry

*(CZAS PACYFICZNY)*<br/>
[in] Wskaźnik do obiektu żądającego transferu asynchronicznego danych. `CBindStatusCallback` Obiektu jest szablonowana na klasy tego obiektu.

*pFunc*<br/>
[in] Wskaźnik do funkcji, która odbiera dane, który jest odczytywany. Funkcja jest elementem członkowskim klasy do obiektu typu `T`. Zobacz [StartAsyncDownload](#startasyncdownload) dla składni i przykłady.

*bstrURL*<br/>
[in] Adres URL można uzyskać danych z. Może być Dowolna prawidłowa nazwa adresu URL lub pliku. Nie może mieć wartości NULL. Na przykład:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
[in] `IUnknown` Kontenera. Wartość NULL, domyślnie.

*bRelative*<br/>
[in] Flaga wskazująca, czy adres URL jest względna lub bezwzględna. Wartość FALSE, domyślnie, co oznacza adres URL jest bezwzględna.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

Za każdym razem, gdy dane są dostępne są wysyłane za pośrednictwem `OnDataAvailable`. `OnDataAvailable` odczytuje dane i wywołuje funkcję wskazywany przez *pFunc* (na przykład, aby przechowywać dane, lub wydrukuj ją do ekranu).

##  <a name="getbindinfo"></a>  CBindStatusCallback::GetBindInfo

Wywołuje się, by sprawdzić moniker, jak powiązać.

```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```

### <a name="parameters"></a>Parametry

*pgrfBSCF*<br/>
[out] Wskaźnik do BINDF wartości wyliczenia wskazująca na to, jak powinna wystąpić operacja powiązania. Domyślnie ustawiony przy użyciu następujących wartości wyliczenia:

Pobieranie asynchroniczne BINDF_ASYNCHRONOUS.

BINDF_ASYNCSTORAGE `OnDataAvailable` zwraca E_PENDING, gdy dane nie są jeszcze dostępne, a nie blokuje, dopóki dane są dostępne.

Operacja powiązania BINDF_GETNEWESTVERSION Pobierz najnowszą wersję dane.

BINDF_NOWRITECACHE, który nie należy przechowywać Operacja powiązania pobrać dane w pamięci podręcznej dysku.

*pbindinfo*<br/>
[out w] Wskaźnik do `BINDINFO` struktury, co daje więcej informacji na temat jak obiekt chce powiązań, wystąpią.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

Domyślna implementacja ustawia powiązanie asynchronicznego i użyć modelu wypychania danych. W modelu danych wypychania moniker dyski operacja asynchronicznego powiązania i stale powiadamia klient zawsze wtedy, gdy nowe dane są dostępne.

##  <a name="getpriority"></a>  CBindStatusCallback::GetPriority

Metoda wywoływana przez asynchroniczne moniker można pobrać priorytet Operacja powiązania.

```
STDMETHOD(GetPriority)(LONG* pnPriority);
```

### <a name="parameters"></a>Parametry

*pnPriority*<br/>
[out] Adres **długie** zmiennej, która w przypadku powodzenia odbiera priorytet.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

##  <a name="m_dwavailabletoread"></a>  CBindStatusCallback::m_dwAvailableToRead

Mogą być używane do przechowywania liczby bajtów dostępnych do odczytu.

```
DWORD m_dwAvailableToRead;
```

### <a name="remarks"></a>Uwagi

Zainicjowana na zero `StartAsyncDownload`.

##  <a name="m_dwtotalread"></a>  CBindStatusCallback::m_dwTotalRead

Łączna liczba bajtów do odczytu transferu asynchronicznego danych.

```
DWORD m_dwTotalRead;
```

### <a name="remarks"></a>Uwagi

Zwiększana w każdym `OnDataAvailable` jest wywoływana przez liczbę faktycznie odczytanych bajtów. Zainicjowana na zero `StartAsyncDownload`.

##  <a name="m_pfunc"></a>  CBindStatusCallback::m_pFunc

Funkcja wskazywany przez `m_pFunc` jest wywoływana przez `OnDataAvailable` po odczytuje dostępne dane (na przykład, aby przechowywać dane, lub wydrukuj ją do ekranu).

```
ATL_PDATAAVAILABLE m_pFunc;
```

### <a name="remarks"></a>Uwagi

Funkcja wskazywany przez `m_pFunc` jest elementem członkowskim klasy z obiektu i ma następującą składnię:

```
void Function_Name(
   CBindStatusCallback<T>* pbsc,
   BYTE* pBytes,
   DWORD dwSize
   );
```

##  <a name="m_pt"></a>  CBindStatusCallback::m_pT

Wskaźnik do obiektu żądającego transferu asynchronicznego danych.

```
T* m_pT;
```

### <a name="remarks"></a>Uwagi

`CBindStatusCallback` Obiektu jest szablonowana na klasy tego obiektu.

##  <a name="m_spbindctx"></a>  CBindStatusCallback::m_spBindCtx

Wskaźnik do [IBindCtx](/windows/desktop/api/objidl/nn-objidl-ibindctx) interfejs, który zapewnia dostęp do kontekstu powiązania (obiekt, który przechowuje informacje o operacji wiązania określonej krótkiej nazwy).

```
CComPtr<IBindCtx> m_spBindCtx;
```

### <a name="remarks"></a>Uwagi

Zainicjowane w `StartAsyncDownload`.

##  <a name="m_spbinding"></a>  CBindStatusCallback::m_spBinding

Wskaźnik do `IBinding` interfejsu bieżącej operacji wiązania.

```
CComPtr<IBinding> m_spBinding;
```

### <a name="remarks"></a>Uwagi

Zainicjowane w `OnStartBinding` i wydawane w `OnStopBinding`.

##  <a name="m_spmoniker"></a>  CBindStatusCallback::m_spMoniker

Wskaźnik do [imoniker —](/windows/desktop/api/objidl/nn-objidl-imoniker) interfejsu dla adresu URL do użycia.

```
CComPtr<IMoniker> m_spMoniker;
```

### <a name="remarks"></a>Uwagi

Zainicjowane w `StartAsyncDownload`.

##  <a name="m_spstream"></a>  CBindStatusCallback::m_spStream

Wskaźnik do [IStream](/windows/desktop/api/objidl/nn-objidl-istream) interfejsu bieżącej operacji wiązania.

```
CComPtr<IStream> m_spStream;
```

### <a name="remarks"></a>Uwagi

Zainicjowane w `OnDataAvailable` z `STGMEDIUM` struktury, gdy flaga BCSF BCSF_FIRSTDATANOTIFICATION jest zwalniany, gdy flaga BCSF jest BCSF_LASTDATANOTIFICATION.

##  <a name="ondataavailable"></a>  CBindStatusCallback::OnDataAvailable

Wywołania dostarczane przez system asynchronicznego moniker `OnDataAvailable` do przekazywania danych do obiektu, po jej udostępnieniu.

```
STDMETHOD(
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```

### <a name="parameters"></a>Parametry

*grfBSCF*<br/>
[in] Wartość wyliczenia BSCF. Co najmniej jeden z następujących czynności: BSCF_FIRSTDATANOTIFICATION, BSCF_INTERMEDIARYDATANOTIFICATION lub BSCF_LASTDATANOTIFICATION.

*niezerowego*<br/>
[in] Zbiorcza kwota (w bajtach) dostępnych od początku powiązanie danych. Może być równy zero, wskazującą, ilości danych nie jest ważna, lub że bez żadnej kwoty określone stały się dostępne.

*pformatetc*<br/>
[in] Wskaźnik do [FORMATETC](/windows/desktop/com/the-formatetc-structure) strukturę, która zawiera format dostępnych danych. W przypadku formatu nie może być CF_NULL.

*pstgmed*<br/>
[in] Wskaźnik do [STGMEDIUM](/windows/desktop/com/the-stgmedium-structure) strukturę, która przechowuje dane rzeczywiste, która jest teraz dostępna.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

`OnDataAvailable` odczytuje dane, a następnie wywołuje metodę klasy obiektu (na przykład, aby przechowywać dane, lub wydrukuj ją do ekranu). Zobacz [CBindStatusCallback::StartAsyncDownload](#startasyncdownload) Aby uzyskać szczegółowe informacje.

##  <a name="onlowresource"></a>  CBindStatusCallback::OnLowResource

Wywołuje się, gdy brakuje zasobów.

```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```

### <a name="parameters"></a>Parametry

*dwReserved*<br/>
Zastrzeżone.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK.

##  <a name="onobjectavailable"></a>  CBindStatusCallback::OnObjectAvailable

Metoda wywoływana przez asynchroniczne monikera do przekazania obiektu wskaźnik interfejsu do aplikacji.

```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```

### <a name="parameters"></a>Parametry

*Parametr riid*<br/>
Identyfikator interfejsu żądanego interfejsu. Nieużywane.

*punk*<br/>
Adres interfejsu IUnknown. Nieużywane.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK.

##  <a name="onprogress"></a>  CBindStatusCallback::OnProgress

Wywołuje się, by wskazać proces pobierania danych.

```
STDMETHOD(OnProgress)(
    ULONG /* ulProgress */,
    ULONG /* ulProgressMax */,
    ULONG /* ulStatusCode */,
    LPCWSTRONG /* szStatusText */);
```

### <a name="parameters"></a>Parametry

*ulProgress*<br/>
Niepodpisane długa liczba całkowita. Nieużywane.

*ulProgressMax*<br/>
Długa liczba całkowita bez znaku węzła nieużywane.

*ulStatusCode*<br/>
Niepodpisane długa liczba całkowita. Nieużywane.

*szStatusText*<br/>
Adres wartość ciągu. Nieużywane.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK.

##  <a name="onstartbinding"></a>  CBindStatusCallback::OnStartBinding

Ustawia element członkowski danych [m_spBinding](#m_spbinding) do `IBinding` wskaźnika w *pBinding*.

```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```

### <a name="parameters"></a>Parametry

*dwReserved*<br/>
Zarezerwowane do użytku w przyszłości.

*pBinding*<br/>
[in] Operacja powiązania adres interfejsu IBinding bieżącego. To nie może mieć wartości NULL. Klient powinien wywoływać AddRef na ten wskaźnik, aby zapewnić odwołanie do obiektu powiązania.

##  <a name="onstopbinding"></a>  CBindStatusCallback::OnStopBinding

Wersje `IBinding` wskaźnika w składowej danych [m_spBinding](#m_spbinding).

```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```

### <a name="parameters"></a>Parametry

*wartość HRESULT*<br/>
Kod stanu zwrócony przez operację powiązania.

*szError*<br/>
Adres wartość ciągu. Nieużywane.

### <a name="remarks"></a>Uwagi

Metoda wywoływana przez dostarczane przez system moniker asynchronicznych do wskazania koniec operacji wiązania.

##  <a name="startasyncdownload"></a>  CBindStatusCallback::StartAsyncDownload

Uruchamia asynchronicznie pobieranie danych z określonego adresu URL.

```
HRESULT StartAsyncDownload(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Parametry

*(CZAS PACYFICZNY)*<br/>
[in] Wskaźnik do obiektu żądającego transferu asynchronicznego danych. `CBindStatusCallback` Obiektu jest szablonowana na klasy tego obiektu.

*pFunc*<br/>
[in] Wskaźnik do funkcji, która odbiera odczytywanych danych. Funkcja jest elementem członkowskim klasy do obiektu typu `T`. Zobacz **uwagi** dla składni i przykłady.

*bstrURL*<br/>
[in] Adres URL można uzyskać danych z. Może być Dowolna prawidłowa nazwa adresu URL lub pliku. Nie może mieć wartości NULL. Na przykład:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
[in] `IUnknown` Kontenera. Wartość NULL, domyślnie.

*bRelative*<br/>
[in] Flaga wskazująca, czy adres URL jest względna lub bezwzględna. Wartość FALSE, domyślnie, co oznacza adres URL jest bezwzględna.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

Za każdym razem, gdy dane są dostępne są wysyłane za pośrednictwem `OnDataAvailable`. `OnDataAvailable` odczytuje dane i wywołuje funkcję wskazywany przez *pFunc* (na przykład, aby przechowywać dane, lub wydrukuj ją do ekranu).

Funkcja wskazywany przez *pFunc* jest elementem członkowskim klasy z obiektu i ma następującą składnię:

```
void Function_Name(
    CBindStatusCallback<T>* pbsc,
    BYTE* pBytes,
    DWORD dwSize);
```

W poniższym przykładzie (z [ASYNC](../../visual-cpp-samples.md) przykładowych), funkcja `OnData` zapisuje odebrane dane w polu tekstowym.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)
