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
ms.openlocfilehash: 89c65ff034cf7471c379b28116a741b62269a00c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497602"
---
# <a name="cbindstatuscallback-class"></a>Klasa CBindStatusCallback

Ta klasa implementuje `IBindStatusCallback` interfejs.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS | BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa zawierająca funkcję, która zostanie wywołana jako dane są odbierane.

*nBindFlags*<br/>
Określa flagi wiązania, które są zwracane przez [GetBindInfo](#getbindinfo). Domyślna implementacja ustawia powiązanie jako asynchroniczne, Pobiera najnowszą wersję danych/obiektu i nie przechowuje pobranych danych w pamięci podręcznej dysków.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBindStatusCallback::CBindStatusCallback](#cbindstatuscallback)|Konstruktor.|
|[CBindStatusCallback::~CBindStatusCallback](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBindStatusCallback::D obierz](#download)|Metoda statyczna, która uruchamia proces pobierania, tworzy `CBindStatusCallback` obiekt i wywołuje. `StartAsyncDownload`|
|[CBindStatusCallback:: GetBindInfo](#getbindinfo)|Wywoływane przez moniker asynchroniczny, aby zażądać informacji o typie powiązania, który ma zostać utworzony.|
|[CBindStatusCallback:: GetPriority](#getpriority)|Wywoływane przez moniker asynchroniczny, aby uzyskać priorytet operacji wiązania. Implementacja ATL zwraca `E_NOTIMPL`.|
|[CBindStatusCallback::OnDataAvailable](#ondataavailable)|Wywołuje się, by dostarczać dane do aplikacji w miarę ich udostępniania. Odczytuje dane, a następnie wywołuje funkcję przekazaną do niej, aby użyć danych.|
|[CBindStatusCallback::OnLowResource](#onlowresource)|Wywoływana, gdy zasoby są niskie. Implementacja ATL zwraca S_OK.|
|[CBindStatusCallback::OnObjectAvailable](#onobjectavailable)|Wywoływane przez moniker asynchroniczny, aby przekazać wskaźnik interfejsu obiektu do aplikacji. Implementacja ATL zwraca S_OK.|
|[CBindStatusCallback::OnProgress](#onprogress)|Wywołuje się, by wskazać postęp procesu pobierania danych. Implementacja ATL zwraca S_OK.|
|[CBindStatusCallback:: OnStartBinding](#onstartbinding)|Wywoływana po rozpoczęciu tworzenia powiązania.|
|[CBindStatusCallback:: OnStopBinding](#onstopbinding)|Wywoływana, gdy asynchroniczny transfer danych jest zatrzymany.|
|[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)|Inicjuje dostępne bajty i Bajty odczytane do zera, tworzy obiekt strumienia typu push na podstawie adresu URL i `OnDataAvailable` wywołuje każde dane czasu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CBindStatusCallback::m_dwAvailableToRead](#m_dwavailabletoread)|Liczba bajtów dostępnych do odczytu.|
|[CBindStatusCallback::m_dwTotalRead](#m_dwtotalread)|Łączna Liczba odczytanych bajtów.|
|[CBindStatusCallback::m_pFunc](#m_pfunc)|Wskaźnik do funkcji wywoływanej, gdy dane są dostępne.|
|[CBindStatusCallback::m_pT](#m_pt)|Wskaźnik do obiektu żądającego asynchronicznego transferu danych.|
|[CBindStatusCallback::m_spBindCtx](#m_spbindctx)|Wskaźnik do interfejsu [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) dla bieżącej operacji wiązania.|
|[CBindStatusCallback::m_spBinding](#m_spbinding)|Wskaźnik do `IBinding` interfejsu dla bieżącej operacji wiązania.|
|[CBindStatusCallback::m_spMoniker](#m_spmoniker)|Wskaźnik do interfejsu [IMoniker —](/windows/win32/api/objidl/nn-objidl-imoniker) dla adresu URL, który ma być używany.|
|[CBindStatusCallback::m_spStream](#m_spstream)|Wskaźnik do interfejsu [IStream](/windows/win32/api/objidl/nn-objidl-istream) do transferu danych.|

## <a name="remarks"></a>Uwagi

`CBindStatusCallback` Klasa`IBindStatusCallback` implementuje interfejs. `IBindStatusCallback`musi być zaimplementowany przez aplikację, aby można było otrzymywać powiadomienia o asynchronicznym transferze danych. Moniker asynchroniczny dostarczony przez system używa `IBindStatusCallback` metod do wysyłania i odbierania informacji o asynchronicznym przekazywaniu danych do i z obiektu.

`CBindStatusCallback` Zazwyczaj obiekt jest skojarzony z określoną operacją wiązania. Na przykład w próbce [asynchronicznej](../../overview/visual-cpp-samples.md) podczas ustawiania właściwości adresu URL tworzy `CBindStatusCallback` obiekt `Download`w wywołaniu:

[!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]

Moniker asynchroniczny używa funkcji `OnData` wywołania zwrotnego do wywołania aplikacji, gdy ma ona dane. Moniker asynchroniczny jest dostarczany przez system.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CComObjectRootBase`

`IBindStatusCallback`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`CBindStatusCallback`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl. h

##  <a name="cbindstatuscallback"></a>CBindStatusCallback::CBindStatusCallback

Konstruktor.

```
CBindStatusCallback();
```

### <a name="remarks"></a>Uwagi

Tworzy obiekt do odbierania powiadomień dotyczących asynchronicznego transferu danych. Zazwyczaj jeden obiekt jest tworzony dla każdej operacji wiązania.

Konstruktor inicjuje także [m_pT](#m_pt) i [m_pFunc](#m_pfunc) do wartości null.

##  <a name="dtor"></a>CBindStatusCallback:: ~ CBindStatusCallback

Destruktor.

```
~CBindStatusCallback();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzieloną zasoby.

##  <a name="download"></a>CBindStatusCallback::D obierz

Tworzy obiekt i wywołuje `StartAsyncDownload` , aby rozpocząć pobieranie danych asynchronicznie z podanego adresu URL. `CBindStatusCallback`

```
static HRESULT Download(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Parametry

*Zmiennoprzecinkow*<br/>
podczas Wskaźnik do obiektu żądającego asynchronicznego transferu danych. `CBindStatusCallback` Obiekt jest szablonowana dla klasy tego obiektu.

*pFunc*<br/>
podczas Wskaźnik do funkcji, która otrzymuje dane, które są odczytywane. Funkcja jest elementem członkowskim klasy obiektu typu `T`. Zobacz [StartAsyncDownload](#startasyncdownload) , aby poznać składnię i przykład.

*bstrURL*<br/>
podczas Adres URL, z którego mają zostać uzyskane dane. Może to być dowolny prawidłowy adres URL lub nazwa pliku. Nie może mieć wartości NULL. Przykład:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
podczas `IUnknown` Kontener. Domyślnie wartość NULL.

*bRelative*<br/>
podczas Flaga wskazująca, czy adres URL jest względny, czy bezwzględny. Wartość domyślna to FALSE, co oznacza, że adres URL jest bezwzględny.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Za każdym razem, gdy dane są dostępne, są wysyłane do `OnDataAvailable`obiektu za pomocą. `OnDataAvailable`odczytuje dane i wywołuje funkcję wskazywaną przez *pFunc* (na przykład w celu przechowywania danych lub drukowania na ekranie).

##  <a name="getbindinfo"></a>CBindStatusCallback:: GetBindInfo

Wywołuje się, by poinformować moniker o sposobie powiązania.

```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```

### <a name="parameters"></a>Parametry

*pgrfBSCF*<br/>
określoną Wskaźnik do BINDF wartości wyliczenia wskazujący sposób działania powiązania. Domyślnie Ustaw następujące wartości wyliczenia:

BINDF_ASYNCHRONOUS asynchroniczne pobieranie.

BINDF_ASYNCSTORAGE `OnDataAvailable` zwraca E_PENDING, gdy dane nie są jeszcze dostępne, a nie BLOKOWANIE do momentu udostępnienia danych.

BINDF_GETNEWESTVERSION operacja bind powinna pobrać najnowszą wersję danych.

BINDF_NOWRITECACHE operacja bind nie powinna przechowywać pobranych danych w pamięci podręcznej dysków.

*pbindinfo*<br/>
[in. out] Wskaźnik do struktury, `BINDINFO` zawierający więcej informacji o tym, jak obiekt chce mieć powiązania.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Domyślna implementacja ustawia powiązanie jako asynchroniczne i do korzystania z modelu wypychania danych. W modelu wypychania danych moniker jest używany do asynchronicznej operacji wiązania i ciągle powiadamia klienta za każdym razem, gdy nowe dane są dostępne.

##  <a name="getpriority"></a>CBindStatusCallback:: GetPriority

Wywoływane przez moniker asynchroniczny, aby uzyskać priorytet operacji wiązania.

```
STDMETHOD(GetPriority)(LONG* pnPriority);
```

### <a name="parameters"></a>Parametry

*pnPriority*<br/>
określoną Adres zmiennej **długiej** , która po powodzeniu otrzymuje priorytet.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

##  <a name="m_dwavailabletoread"></a>CBindStatusCallback::m_dwAvailableToRead

Może służyć do przechowywania liczby bajtów dostępnych do odczytu.

```
DWORD m_dwAvailableToRead;
```

### <a name="remarks"></a>Uwagi

Zainicjowany do zera w `StartAsyncDownload`.

##  <a name="m_dwtotalread"></a>CBindStatusCallback::m_dwTotalRead

Łączna liczba bajtów odczytanych w asynchronicznym transferze danych.

```
DWORD m_dwTotalRead;
```

### <a name="remarks"></a>Uwagi

Każdy czas `OnDataAvailable` jest wywoływany przez liczbę bajtów, które faktycznie są odczytywane. Zainicjowany do zera w `StartAsyncDownload`.

##  <a name="m_pfunc"></a>  CBindStatusCallback::m_pFunc

Funkcja wskazywana przez `m_pFunc` jest wywoływana przez `OnDataAvailable` program, gdy odczytuje dostępne dane (na przykład w celu przechowywania danych lub drukowania na ekranie).

```
ATL_PDATAAVAILABLE m_pFunc;
```

### <a name="remarks"></a>Uwagi

Funkcja wskazywana przez `m_pFunc` to element członkowski klasy obiektu i ma następującą składnię:

```
void Function_Name(
   CBindStatusCallback<T>* pbsc,
   BYTE* pBytes,
   DWORD dwSize
   );
```

##  <a name="m_pt"></a>CBindStatusCallback::m_pT

Wskaźnik do obiektu żądającego asynchronicznego transferu danych.

```
T* m_pT;
```

### <a name="remarks"></a>Uwagi

`CBindStatusCallback` Obiekt jest szablonowana dla klasy tego obiektu.

##  <a name="m_spbindctx"></a>CBindStatusCallback::m_spBindCtx

Wskaźnik do interfejsu [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) , który zapewnia dostęp do kontekstu wiązania (obiektu, który przechowuje informacje o określonej operacji powiązania monikera).

```
CComPtr<IBindCtx> m_spBindCtx;
```

### <a name="remarks"></a>Uwagi

Zainicjowane w `StartAsyncDownload`.

##  <a name="m_spbinding"></a>CBindStatusCallback::m_spBinding

Wskaźnik do `IBinding` interfejsu bieżącej operacji wiązania.

```
CComPtr<IBinding> m_spBinding;
```

### <a name="remarks"></a>Uwagi

Zainicjowany w `OnStartBinding` i wydano `OnStopBinding`w.

##  <a name="m_spmoniker"></a>CBindStatusCallback::m_spMoniker

Wskaźnik do interfejsu [IMoniker —](/windows/win32/api/objidl/nn-objidl-imoniker) dla adresu URL, który ma być używany.

```
CComPtr<IMoniker> m_spMoniker;
```

### <a name="remarks"></a>Uwagi

Zainicjowane w `StartAsyncDownload`.

##  <a name="m_spstream"></a>CBindStatusCallback::m_spStream

Wskaźnik do interfejsu [IStream](/windows/win32/api/objidl/nn-objidl-istream) bieżącej operacji wiązania.

```
CComPtr<IStream> m_spStream;
```

### <a name="remarks"></a>Uwagi

Zainicjowany w `OnDataAvailable` ramach `STGMEDIUM` struktury, gdy flaga BCSF jest BCSF_FIRSTDATANOTIFICATION i wydano, gdy flaga BCSF to BCSF_LASTDATANOTIFICATION.

##  <a name="ondataavailable"></a>CBindStatusCallback::OnDataAvailable

Asynchroniczne wywołania `OnDataAvailable` monikera dostarczone przez system w celu dostarczenia danych do obiektu, gdy staną się dostępne.

```
STDMETHOD(
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```

### <a name="parameters"></a>Parametry

*grfBSCF*<br/>
podczas Wartość wyliczenia BSCF. Co najmniej jeden z następujących elementów: BSCF_FIRSTDATANOTIFICATION, BSCF_INTERMEDIARYDATANOTIFICATION lub BSCF_LASTDATANOTIFICATION.

*dwSize*<br/>
podczas Łączna ilość danych (w bajtach) dostępnych od początku powiązania. Może być równa zero, co oznacza, że ilość danych nie jest istotna lub nie jest dostępna żadna określona kwota.

*pformatetc*<br/>
podczas Wskaźnik do struktury [FORMATETC](/windows/win32/com/the-formatetc-structure) , która zawiera format dostępnych danych. Jeśli nie ma żadnego formatu, można CF_NULL.

*pstgmed*<br/>
podczas Wskaźnik do struktury [STGMEDIUM](/windows/win32/com/the-stgmedium-structure) , która zawiera rzeczywiste dane, są teraz dostępne.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

`OnDataAvailable`odczytuje dane, a następnie wywołuje metodę klasy obiektu (na przykład w celu przechowywania danych lub drukowania na ekranie). Aby uzyskać szczegółowe informacje, zobacz [CBindStatusCallback:: StartAsyncDownload](#startasyncdownload) .

##  <a name="onlowresource"></a>CBindStatusCallback::OnLowResource

Wywoływana, gdy zasoby są niskie.

```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```

### <a name="parameters"></a>Parametry

*dwReserved*<br/>
Rezerwacj.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

##  <a name="onobjectavailable"></a>CBindStatusCallback::OnObjectAvailable

Wywoływane przez moniker asynchroniczny, aby przekazać wskaźnik interfejsu obiektu do aplikacji.

```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Identyfikator interfejsu żądanego interfejsu. Przestrzeń.

*punkt*<br/>
Adres interfejsu IUnknown. Przestrzeń.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

##  <a name="onprogress"></a>CBindStatusCallback:: OnProgress

Wywołuje się, by wskazać postęp procesu pobierania danych.

```
STDMETHOD(OnProgress)(
    ULONG /* ulProgress */,
    ULONG /* ulProgressMax */,
    ULONG /* ulStatusCode */,
    LPCWSTRONG /* szStatusText */);
```

### <a name="parameters"></a>Parametry

*ulProgress*<br/>
Długa liczba całkowita bez znaku. Przestrzeń.

*ulProgressMax*<br/>
Nieużywana długa liczba całkowita bez znaku.

*ulStatusCode*<br/>
Długa liczba całkowita bez znaku. Przestrzeń.

*szStatusText*<br/>
Adres wartości ciągu. Przestrzeń.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

##  <a name="onstartbinding"></a>CBindStatusCallback:: OnStartBinding

Ustawia element członkowski danych [m_spBinding](#m_spbinding) na `IBinding` wskaźnik w *pBinding*.

```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```

### <a name="parameters"></a>Parametry

*dwReserved*<br/>
Zarezerwowane do użytku w przyszłości.

*pBinding*<br/>
podczas Adres interfejsu IBinding bieżącej operacji wiązania. Nie może to być wartość zerowa. Klient powinien wywołać AddRef na tym wskaźniku, aby zachować odwołanie do obiektu powiązania.

##  <a name="onstopbinding"></a>CBindStatusCallback:: OnStopBinding

Zwalnia wskaźnik z elementu członkowskiego danych [m_spBinding.](#m_spbinding) `IBinding`

```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```

### <a name="parameters"></a>Parametry

*wynik*<br/>
Kod stanu zwrócony z operacji wiązania.

*szError*<br/>
Adres wartości ciągu. Przestrzeń.

### <a name="remarks"></a>Uwagi

Wywoływane przez asynchroniczną moniker dostarczony przez system, aby wskazać koniec operacji wiązania.

##  <a name="startasyncdownload"></a>CBindStatusCallback::StartAsyncDownload

Zaczyna pobieranie danych asynchronicznie z podanego adresu URL.

```
HRESULT StartAsyncDownload(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Parametry

*Zmiennoprzecinkow*<br/>
podczas Wskaźnik do obiektu żądającego asynchronicznego transferu danych. `CBindStatusCallback` Obiekt jest szablonowana dla klasy tego obiektu.

*pFunc*<br/>
podczas Wskaźnik do funkcji, która otrzymuje dane, które są odczytywane. Funkcja jest elementem członkowskim klasy obiektu typu `T`. Zobacz **uwagi** dotyczące składni i przykładu.

*bstrURL*<br/>
podczas Adres URL, z którego mają zostać uzyskane dane. Może to być dowolny prawidłowy adres URL lub nazwa pliku. Nie może mieć wartości NULL. Na przykład:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
podczas `IUnknown` Kontener. Domyślnie wartość NULL.

*bRelative*<br/>
podczas Flaga wskazująca, czy adres URL jest względny, czy bezwzględny. Wartość domyślna to FALSE, co oznacza, że adres URL jest bezwzględny.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Za każdym razem, gdy dane są dostępne, są wysyłane do `OnDataAvailable`obiektu za pomocą. `OnDataAvailable`odczytuje dane i wywołuje funkcję wskazywaną przez *pFunc* (na przykład w celu przechowywania danych lub drukowania na ekranie).

Funkcja wskazywana przez *pFunc* jest elementem członkowskim klasy obiektu i ma następującą składnię:

```
void Function_Name(
    CBindStatusCallback<T>* pbsc,
    BYTE* pBytes,
    DWORD dwSize);
```

W poniższym przykładzie (pobranym z próbki [asynchronicznej](../../overview/visual-cpp-samples.md) ) funkcja `OnData` zapisuje odebrane dane do pola tekstowego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
