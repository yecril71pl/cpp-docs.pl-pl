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
ms.openlocfilehash: 0ae7f4fcdba18be84d99140e395b6f2ac3db792a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748198"
---
# <a name="cbindstatuscallback-class"></a>Klasa CBindStatusCallback

Ta klasa implementuje `IBindStatusCallback` interfejs.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS | BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa zawierająca funkcję, która zostanie wywołana po odebraniu danych.

*nBindFlags*<br/>
Określa flagi powiązania, które są zwracane przez [GetBindInfo](#getbindinfo). Domyślna implementacja ustawia powiązanie jako asynchroniczne, pobiera najnowszą wersję danych/obiektu i nie przechowuje pobranych danych w pamięci podręcznej dysku.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBindStatusCallback::CBindStatusCallback](#cbindstatuscallback)|Konstruktor.|
|[CBindStatusCallback::~CBindStatusCallback](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBindStatusCallback::Dwłasny](#download)|Metoda statyczna, która rozpoczyna proces `CBindStatusCallback` pobierania, tworzy `StartAsyncDownload`obiekt i wywołuje .|
|[CBindStatusCallback::GetBindInfo](#getbindinfo)|Wywoływana przez asynchronizajny moniker do żądania informacji o typie powiązania do utworzenia.|
|[CBindStatusCallback::GetPriority](#getpriority)|Wywoływana przez asynchronisty moniker, aby uzyskać priorytet operacji wiązania. Implementacja ATL `E_NOTIMPL`zwraca .|
|[CBindStatusCallback::OnDataDostępne](#ondataavailable)|Wywoływana w celu dostarczenia danych do aplikacji, gdy stanie się dostępna. Odczytuje dane, a następnie wywołuje funkcję przekazywana do niego, aby użyć danych.|
|[CBindStatusCallback::OnLowResource](#onlowresource)|Wywoływane, gdy zasoby są niskie. Implementacja ATL zwraca S_OK.|
|[CBindStatusCallback::OnObjectDostępne](#onobjectavailable)|Wywoływana przez asynchroniiowy moniker przekazać wskaźnik interfejsu obiektu do aplikacji. Implementacja ATL zwraca S_OK.|
|[CBindStatusCallback::OnProgress](#onprogress)|Wywoływana w celu wskazania postępu procesu pobierania danych. Implementacja ATL zwraca S_OK.|
|[CBindStatusCallback::OnStartBinding](#onstartbinding)|Wywoływane po uruchomieniu powiązania.|
|[CBindStatusCallback::OnStopBinding](#onstopbinding)|Wywoływana, gdy transfer danych asynchronicznych jest zatrzymany.|
|[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)|Inicjuje dostępne bajty i bajty odczytywane na zero, tworzy obiekt `OnDataAvailable` strumienia typu wypychanego z adresu URL i wywołuje za każdym razem, gdy dane są dostępne.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CBindStatusCallback::m_dwAvailableToRead](#m_dwavailabletoread)|Liczba bajtów dostępnych do odczytania.|
|[CBindStatusCallback::m_dwTotalRead](#m_dwtotalread)|Całkowita liczba odczytanych bajtów.|
|[CBindStatusCallback::m_pFunc](#m_pfunc)|Wskaźnik do funkcji wywoływane, gdy dane są dostępne.|
|[CBindStatusCallback::m_pT](#m_pt)|Wskaźnik do obiektu żądającego transferu danych asynchronicznych.|
|[CBindStatusCallback::m_spBindCtx](#m_spbindctx)|Wskaźnik do interfejsu [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) dla bieżącej operacji wiązania.|
|[CBindStatusCallback::m_spBinding](#m_spbinding)|Wskaźnik do `IBinding` interfejsu dla bieżącej operacji wiązania.|
|[CBindStatusCallback::m_spMoniker](#m_spmoniker)|Wskaźnik do interfejsu [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) dla adresu URL do użycia.|
|[CBindStatusCallback::m_spStream](#m_spstream)|Wskaźnik do interfejsu [IStream](/windows/win32/api/objidl/nn-objidl-istream) do przesyłania danych.|

## <a name="remarks"></a>Uwagi

Klasa `CBindStatusCallback` implementuje interfejs `IBindStatusCallback`. `IBindStatusCallback`musi zostać zaimplementowana przez aplikację, aby mogła otrzymywać powiadomienia z asynchroniowego transferu danych. Moniker asynchroniczne dostarczone przez system `IBindStatusCallback` używa metod do wysyłania i odbierania informacji o transferze danych asynchronicznych do iz obiektu.

Zazwyczaj `CBindStatusCallback` obiekt jest skojarzony z określoną operacją powiązania. Na przykład w przykładzie [ASYNC](../../overview/visual-cpp-samples.md) po ustawieniu właściwości `CBindStatusCallback` URL tworzy obiekt `Download`w wywołaniu:

[!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]

Moniker asynchroniczne używa funkcji `OnData` wywołania zwrotnego do wywołania aplikacji, gdy ma dane. Asynchroniczne moniker jest dostarczany przez system.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CComObjectRootBase`

`IBindStatusCallback`

[Ccomobjectrootex](../../atl/reference/ccomobjectrootex-class.md)

`CBindStatusCallback`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="cbindstatuscallbackcbindstatuscallback"></a><a name="cbindstatuscallback"></a>CBindStatusCallback::CBindStatusCallback

Konstruktor.

```
CBindStatusCallback();
```

### <a name="remarks"></a>Uwagi

Tworzy obiekt do odbierania powiadomień dotyczących transferu danych asynchronicznych. Zazwyczaj jeden obiekt jest tworzony dla każdej operacji powiązania.

Konstruktor inicjuje również [m_pT](#m_pt) i [m_pFunc](#m_pfunc) do NULL.

## <a name="cbindstatuscallbackcbindstatuscallback"></a><a name="dtor"></a>CBindStatusCallback::~CBindStatusCallback

Destruktor.

```
~CBindStatusCallback();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby.

## <a name="cbindstatuscallbackdownload"></a><a name="download"></a>CBindStatusCallback::Dwłasny

Tworzy `CBindStatusCallback` obiekt i `StartAsyncDownload` wywołania, aby rozpocząć pobieranie danych asynchronicznie z określonego adresu URL.

```
static HRESULT Download(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
[w] Wskaźnik do obiektu żądającego transferu danych asynchronicznych. Obiekt `CBindStatusCallback` jest templatized na tej klasy obiektu.

*pFunc (Niemowny)*<br/>
[w] Wskaźnik do funkcji, która odbiera dane, które są odczytywane. Funkcja jest członkiem klasy typu `T`obiektu . Zobacz [StartAsyncDownload](#startasyncdownload) dla składni i przykład.

*bstrURL ( bstrURL )*<br/>
[w] Adres URL do uzyskania danych. Może to być dowolny prawidłowy adres URL lub nazwa pliku. Nie może być null. Przykład:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
[w] Pojemnik. `IUnknown` NULL domyślnie.

*bRelacyjne*<br/>
[w] Flaga wskazująca, czy adres URL jest względny, czy bezwzględny. FALSE domyślnie, co oznacza, że adres URL jest bezwzględny.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Za każdym razem, gdy dane są `OnDataAvailable`dostępne, są wysyłane do obiektu za pośrednictwem pliku . `OnDataAvailable`odczytuje dane i wywołuje funkcję wskazywany przez *pFunc* (na przykład do przechowywania danych lub drukowania na ekranie).

## <a name="cbindstatuscallbackgetbindinfo"></a><a name="getbindinfo"></a>CBindStatusCallback::GetBindInfo

Wywołany, aby powiedzieć moniker jak powiązać.

```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```

### <a name="parameters"></a>Parametry

*pgrfBSCF*<br/>
[na zewnątrz] Wskaźnik do wartości wyliczenia BINDF wskazujący, jak operacja wiązania powinna wystąpić. Domyślnie należy ustawić następujące wartości wyliczenia:

BINDF_ASYNCHRONOUS do pobrania asynchroniczego.

BINDF_ASYNCSTORAGE `OnDataAvailable` zwraca E_PENDING, gdy dane nie są jeszcze dostępne, a nie blokuje, dopóki dane nie są dostępne.

BINDF_GETNEWESTVERSION Operacja powiązania powinna pobrać najnowszą wersję danych.

BINDF_NOWRITECACHE Operacja wiązania nie powinna przechowywać pobranych danych w pamięci podręcznej dysku.

*pbindinfo*<br/>
[w, na zewnątrz] Wskaźnik do `BINDINFO` struktury, podając więcej informacji o tym, jak obiekt ma wystąpić powiązania.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Domyślna implementacja ustawia powiązanie jako asynchroniczne i używać modelu wypychania danych. W modelu wypychania danych moniker napędza operację wiązania asynchronicznego i stale powiadamia klienta, gdy dostępne są nowe dane.

## <a name="cbindstatuscallbackgetpriority"></a><a name="getpriority"></a>CBindStatusCallback::GetPriority

Wywoływana przez asynchronisty moniker, aby uzyskać priorytet operacji wiązania.

```
STDMETHOD(GetPriority)(LONG* pnPriority);
```

### <a name="parameters"></a>Parametry

*pnPriority*<br/>
[na zewnątrz] Adres zmiennej **LONG,** która po sukcesie otrzymuje priorytet.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

## <a name="cbindstatuscallbackm_dwavailabletoread"></a><a name="m_dwavailabletoread"></a>CBindStatusCallback::m_dwAvailableToRead

Może służyć do przechowywania liczby bajtów dostępnych do odczytania.

```
DWORD m_dwAvailableToRead;
```

### <a name="remarks"></a>Uwagi

Zainicjowany do `StartAsyncDownload`zera w .

## <a name="cbindstatuscallbackm_dwtotalread"></a><a name="m_dwtotalread"></a>CBindStatusCallback::m_dwTotalRead

Łączna suma bajtów odczytanych w transferze danych asynchronicznych.

```
DWORD m_dwTotalRead;
```

### <a name="remarks"></a>Uwagi

Zwiększane za każdym `OnDataAvailable` razem jest wywoływana przez liczbę bajtów faktycznie odczytywane. Zainicjowany do `StartAsyncDownload`zera w .

## <a name="cbindstatuscallbackm_pfunc"></a><a name="m_pfunc"></a>CBindStatusCallback::m_pFunc

Funkcja wskazywana `m_pFunc` przez `OnDataAvailable` jest wywoływana przez po odczytie dostępnych danych (na przykład do przechowywania danych lub drukowania ich na ekranie).

```
ATL_PDATAAVAILABLE m_pFunc;
```

### <a name="remarks"></a>Uwagi

Funkcja wskazywalna przez `m_pFunc` jest członkiem klasy obiektu i ma następującą składnię:

```cpp
void Function_Name(
   CBindStatusCallback<T>* pbsc,
   BYTE* pBytes,
   DWORD dwSize
   );
```

## <a name="cbindstatuscallbackm_pt"></a><a name="m_pt"></a>CBindStatusCallback::m_pT

Wskaźnik do obiektu żądającego transferu danych asynchronicznych.

```
T* m_pT;
```

### <a name="remarks"></a>Uwagi

Obiekt `CBindStatusCallback` jest templatized na tej klasy obiektu.

## <a name="cbindstatuscallbackm_spbindctx"></a><a name="m_spbindctx"></a>CBindStatusCallback::m_spBindCtx

Wskaźnik do interfejsu [IBindCtx,](/windows/win32/api/objidl/nn-objidl-ibindctx) który zapewnia dostęp do kontekstu powiązania (obiekt, który przechowuje informacje o określonej operacji wiązania moniker).

```
CComPtr<IBindCtx> m_spBindCtx;
```

### <a name="remarks"></a>Uwagi

Zainicjowany `StartAsyncDownload`w pliku .

## <a name="cbindstatuscallbackm_spbinding"></a><a name="m_spbinding"></a>CBindStatusCallback::m_spBinding

Wskaźnik do `IBinding` interfejsu bieżącej operacji wiązania.

```
CComPtr<IBinding> m_spBinding;
```

### <a name="remarks"></a>Uwagi

Zainicjowany `OnStartBinding` i wydany `OnStopBinding`w .

## <a name="cbindstatuscallbackm_spmoniker"></a><a name="m_spmoniker"></a>CBindStatusCallback::m_spMoniker

Wskaźnik do interfejsu [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) dla adresu URL do użycia.

```
CComPtr<IMoniker> m_spMoniker;
```

### <a name="remarks"></a>Uwagi

Zainicjowany `StartAsyncDownload`w pliku .

## <a name="cbindstatuscallbackm_spstream"></a><a name="m_spstream"></a>CBindStatusCallback::m_spStream

Wskaźnik do interfejsu [IStream](/windows/win32/api/objidl/nn-objidl-istream) bieżącej operacji powiązania.

```
CComPtr<IStream> m_spStream;
```

### <a name="remarks"></a>Uwagi

Zainicjowany `OnDataAvailable` w `STGMEDIUM` strukturze, gdy flaga BCSF jest BCSF_FIRSTDATANOTIFICATION i zwolniony, gdy flaga BCSF jest BCSF_LASTDATANOTIFICATION.

## <a name="cbindstatuscallbackondataavailable"></a><a name="ondataavailable"></a>CBindStatusCallback::OnDataDostępne

System dostarczane asynchroniczne wywołania `OnDataAvailable` moniker, aby zapewnić dane do obiektu, gdy staje się dostępny.

```
STDMETHOD(
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```

### <a name="parameters"></a>Parametry

*grfBSCF*<br/>
[w] Wartość wyliczenia BSCF. Co najmniej jedna z następujących czynności: BSCF_FIRSTDATANOTIFICATION, BSCF_INTERMEDIARYDATANOTIFICATION lub BSCF_LASTDATANOTIFICATION.

*dwSize (rozmiar)*<br/>
[w] Skumulowana kwota (w bajtach) danych dostępnych od początku powiązania. Może być równa zeru, co oznacza, że ilość danych nie jest istotna lub że nie udostępnino żadnej konkretnej kwoty.

*pformatetc ( pformatetc )*<br/>
[w] Wskaźnik do struktury [FORMATETC,](/windows/win32/com/the-formatetc-structure) która zawiera format dostępnych danych. Jeśli nie ma formatu, można je CF_NULL.

*pstgmed*<br/>
[w] Wskaźnik do struktury [STGMEDIUM,](/windows/win32/com/the-stgmedium-structure) która przechowuje rzeczywiste dane są teraz dostępne.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

`OnDataAvailable`odczytuje dane, a następnie wywołuje metodę klasy obiektu (na przykład, aby zapisać dane lub wydrukować go na ekranie). Zobacz [CBindStatusCallback::StartAsyncDownload szczegóły.](#startasyncdownload)

## <a name="cbindstatuscallbackonlowresource"></a><a name="onlowresource"></a>CBindStatusCallback::OnLowResource

Wywoływane, gdy zasoby są niskie.

```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```

### <a name="parameters"></a>Parametry

*dwReserved (niesłuszne)*<br/>
Zarezerwowany.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

## <a name="cbindstatuscallbackonobjectavailable"></a><a name="onobjectavailable"></a>CBindStatusCallback::OnObjectDostępne

Wywoływana przez asynchroniiowy moniker przekazać wskaźnik interfejsu obiektu do aplikacji.

```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```

### <a name="parameters"></a>Parametry

*Riid*<br/>
Identyfikator interfejsu żądanego interfejsu. Nieużywany.

*Punk*<br/>
Adres interfejsu IUnknown. Nieużywany.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

## <a name="cbindstatuscallbackonprogress"></a><a name="onprogress"></a>CBindStatusCallback::OnProgress

Wywoływana w celu wskazania postępu procesu pobierania danych.

```
STDMETHOD(OnProgress)(
    ULONG /* ulProgress */,
    ULONG /* ulProgressMax */,
    ULONG /* ulStatusCode */,
    LPCWSTRONG /* szStatusText */);
```

### <a name="parameters"></a>Parametry

*ulProgress*<br/>
Niepodpisane długie liczby całkowite. Nieużywany.

*ulProgressMax*<br/>
Niepodpisany długi całkowity Nieużywane.

*ulStatusCode (kod ulStatusCode)*<br/>
Niepodpisane długie liczby całkowite. Nieużywany.

*szStatusText (Tekst szStatus)*<br/>
Adres wartości ciągu. Nieużywany.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

## <a name="cbindstatuscallbackonstartbinding"></a><a name="onstartbinding"></a>CBindStatusCallback::OnStartBinding

Ustawia [m_spBinding](#m_spbinding) elementu członkowskiego danych `IBinding` na wskaźnik w *pBinding*.

```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```

### <a name="parameters"></a>Parametry

*dwReserved (niesłuszne)*<br/>
Zarezerwowane do użytku w przyszłości.

*pBinowanie*<br/>
[w] Adres interfejsu wiązania IBinding bieżącej operacji powiązania. Nie może to być wartość NULL. Klient powinien wywołać AddRef na tym wskaźniku, aby zachować odwołanie do obiektu wiązania.

## <a name="cbindstatuscallbackonstopbinding"></a><a name="onstopbinding"></a>CBindStatusCallback::OnStopBinding

Zwalnia `IBinding` wskaźnik w [m_spBinding](#m_spbinding)elementu członkowskiego danych .

```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```

### <a name="parameters"></a>Parametry

*Hresult*<br/>
Kod stanu zwrócony z operacji wiązania.

*SzError (szError)*<br/>
Adres wartości ciągu. Nieużywany.

### <a name="remarks"></a>Uwagi

Wywoływane przez system dostarczonych moniker asynchroniczne, aby wskazać koniec operacji wiązania.

## <a name="cbindstatuscallbackstartasyncdownload"></a><a name="startasyncdownload"></a>CBindStatusCallback::StartAsyncDownload

Rozpoczyna pobieranie danych asynchronicznie z określonego adresu URL.

```
HRESULT StartAsyncDownload(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
[w] Wskaźnik do obiektu żądającego transferu danych asynchronicznych. Obiekt `CBindStatusCallback` jest templatized na tej klasy obiektu.

*pFunc (Niemowny)*<br/>
[w] Wskaźnik do funkcji, która odbiera dane są odczytywane. Funkcja jest członkiem klasy typu `T`obiektu . Zobacz **Uwagi** dla składni i przykład.

*bstrURL ( bstrURL )*<br/>
[w] Adres URL do uzyskania danych. Może to być dowolny prawidłowy adres URL lub nazwa pliku. Nie może być null. Przykład:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
[w] Pojemnik. `IUnknown` NULL domyślnie.

*bRelacyjne*<br/>
[w] Flaga wskazująca, czy adres URL jest względny, czy bezwzględny. FALSE domyślnie, co oznacza, że adres URL jest bezwzględny.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Za każdym razem, gdy dane są `OnDataAvailable`dostępne, są wysyłane do obiektu za pośrednictwem pliku . `OnDataAvailable`odczytuje dane i wywołuje funkcję wskazywany przez *pFunc* (na przykład do przechowywania danych lub drukowania na ekranie).

Funkcja wskazywalna przez *pFunc* jest członkiem klasy obiektu i ma następującą składnię:

```cpp
void Function_Name(
    CBindStatusCallback<T>* pbsc,
    BYTE* pBytes,
    DWORD dwSize);
```

W poniższym przykładzie (zaczerpniętym z przykładu [ASYNC)](../../overview/visual-cpp-samples.md) funkcja `OnData` zapisuje odebrane dane w polu tekstowym.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
