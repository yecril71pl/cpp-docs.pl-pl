---
title: Klasa CBindStatusCallback | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- asynchronous data transfer [C++]
- data transfer [C++]
- data transfer [C++], asynchronous
- CBindStatusCallback class
ms.assetid: 0f5da276-6031-4418-b2a9-a4750ef29e77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43a51b98710ea92f153581945007f21864dca6f4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365663"
---
# <a name="cbindstatuscallback-class"></a>Klasa CBindStatusCallback
Ta klasa implementuje `IBindStatusCallback` interfejsu.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS |   BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>  
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx
 <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasy zawierający funkcję, która zostanie wywołana, ponieważ dane są odebrane.  
  
 *nBindFlags*  
 Określa flagi powiązania, które są zwracane przez [GetBindInfo](#getbindinfo). Domyślna implementacja ustawia powiązanie była asynchroniczna, pobiera najnowsza wersja obiektu/danych i pobrane dane przechowywane w pamięci podręcznej dysku.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CBindStatusCallback::CBindStatusCallback](#cbindstatuscallback)|Konstruktor.|  
|[CBindStatusCallback:: ~ CBindStatusCallback](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CBindStatusCallback::Download](#download)|Tworzy metody statycznej, która rozpoczyna się proces pobierania `CBindStatusCallback` obiektu i wywołania `StartAsyncDownload`.|  
|[CBindStatusCallback::GetBindInfo](#getbindinfo)|Wywołuje asynchroniczną krótkiej nazwy do żądania informacji na temat rodzaju powiązania ma zostać utworzony.|  
|[CBindStatusCallback::GetPriority](#getpriority)|Metoda wywoływana przez asynchroniczne moniker uzyskanie priorytet Operacja powiązania. Zwraca implementację ATL `E_NOTIMPL`.|  
|[CBindStatusCallback::OnDataAvailable](#ondataavailable)|Wywoływane w celu dostarczania danych do aplikacji po jej udostępnieniu. Odczytuje dane, a następnie wywołuje funkcję przekazywania za pomocą danych.|  
|[CBindStatusCallback::OnLowResource](#onlowresource)|Wywoływane, gdy zasoby są małe. Zwraca implementację ATL `S_OK`.|  
|[CBindStatusCallback::OnObjectAvailable](#onobjectavailable)|Wywołuje asynchroniczną krótkiej nazwy do przekazania wskaźnika interfejsu obiektu do aplikacji. Zwraca implementację ATL `S_OK`.|  
|[CBindStatusCallback::OnProgress](#onprogress)|Wywołuje się, by wskazać proces pobierania danych. Zwraca implementację ATL `S_OK`.|  
|[CBindStatusCallback::OnStartBinding](#onstartbinding)|Wywoływane, gdy powiązanie jest uruchomiona.|  
|[CBindStatusCallback::OnStopBinding](#onstopbinding)|Wywoływane, gdy zatrzymano transfer danych asynchronicznych.|  
|[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)|Inicjuje liczby dostępnych bajtów i odczytana liczba bajtów do zera, tworzy obiekt typu wypychania strumienia z adresu URL i wywołania `OnDataAvailable` za każdym razem, gdy dane są dostępne.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CBindStatusCallback::m_dwAvailableToRead](#m_dwavailabletoread)|Liczba bajtów dostępnych do odczytu.|  
|[CBindStatusCallback::m_dwTotalRead](#m_dwtotalread)|Całkowita liczba bajtów do odczytu.|  
|[CBindStatusCallback::m_pFunc](#m_pfunc)|Wskaźnik do funkcji wywoływana, gdy dane są dostępne.|  
|[CBindStatusCallback::m_pT](#m_pt)|Wskaźnik do obiektu żądającego transferu danych asynchronicznych.|  
|[CBindStatusCallback::m_spBindCtx](#m_spbindctx)|Wskaźnik do [IBindCtx](http://msdn.microsoft.com/library/windows/desktop/ms693755) interfejs dla bieżącej operacji wiązania.|  
|[CBindStatusCallback::m_spBinding](#m_spbinding)|Wskaźnik do `IBinding` interfejs dla bieżącej operacji wiązania.|  
|[CBindStatusCallback::m_spMoniker](#m_spmoniker)|Wskaźnik do [imoniker —](http://msdn.microsoft.com/library/windows/desktop/ms679705) interfejs dla adresu URL do użycia.|  
|[CBindStatusCallback::m_spStream](#m_spstream)|Wskaźnik do [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) interfejs do transferu danych.|  
  
## <a name="remarks"></a>Uwagi  
 `CBindStatusCallback` Klasa implementuje `IBindStatusCallback` interfejsu. `IBindStatusCallback` musi być implementowana przez aplikację, więc może odbierać powiadomienia z transferu danych asynchronicznych. Korzysta z asynchronicznego krótkiej nazwy systemu `IBindStatusCallback` metody służące do wysyłania i odbierania informacji na temat danych asynchronicznych transferu do i z obiektu.  
  
 Zazwyczaj `CBindStatusCallback` obiekt jest skojarzony z operacją określonego powiązania. Na przykład w [ASYNC](../../visual-cpp-samples.md) próbki, gdy wartość właściwości adresu URL tworzy `CBindStatusCallback` obiektu w wywołaniu `Download`:  
  
 [!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]  
  
 Asynchroniczne moniker funkcja wywołania zwrotnego `OnData` do wywołania aplikacji, gdy zawiera on danych. Moniker asynchroniczne są udostępniane przez system.  
  
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
 Tworzy obiekt do odbierania powiadomień dotyczących przekazywania danych asynchronicznych. Zazwyczaj jeden obiekt jest tworzona dla każdej operacji wiązania.  
  
 Konstruktor inicjuje również [m_pT](#m_pt) i [m_pFunc](#m_pfunc) do **NULL**.  
  
##  <a name="dtor"></a>  CBindStatusCallback:: ~ CBindStatusCallback  
 Destruktor.  
  
```
~CBindStatusCallback();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie przydzielone zasoby.  
  
##  <a name="download"></a>  CBindStatusCallback::Download  
 Tworzy `CBindStatusCallback` obiektu i wywołania `StartAsyncDownload` uruchomić asynchronicznie pobieranie danych z określonego adresu URL.  
  
```
static HRESULT Download(  
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 *PT*  
 [in] Wskaźnik do obiektu żądającego transferu danych asynchronicznych. `CBindStatusCallback` Obiektu jest którego ma zastosowany szablon dla tego obiektu klasy.  
  
 *pFunc*  
 [in] Wskaźnik do funkcji, która odbiera dane, które jest do odczytu. Funkcja jest elementem członkowskim klasy do obiektu typu `T`. Zobacz [StartAsyncDownload](#startasyncdownload) składnię i przykład.  
  
 `bstrURL`  
 [in] Adres URL mają zostać pobrane dane. Może być dowolną prawidłową nazwę pliku lub adres URL. Nie może być **NULL**. Na przykład:  
  
 `CComBSTR mybstr =_T("http://somesite/data.htm")`  
  
 `pUnkContainer`  
 [in] **IUnknown** kontenera. **Wartość NULL** domyślnie.  
  
 `bRelative`  
 [in] Flaga wskazująca, czy adres URL jest względna lub bezwzględna. **FALSE** domyślnie, czyli adres URL jest bezwzględna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy `HRESULT` wartości.  
  
### <a name="remarks"></a>Uwagi  
 Za każdym razem, gdy dane są dostępne są wysyłane za pośrednictwem `OnDataAvailable`. `OnDataAvailable` odczytuje dane i wywołuje funkcję wskazywana przez *pFunc* (na przykład do przechowywania danych, lub wydrukuj ją do ekranu).  
  
##  <a name="getbindinfo"></a>  CBindStatusCallback::GetBindInfo  
 Wywołuje się, by Poinformuj krótkiej nazwy, jak można powiązać.  
  
```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```  
  
### <a name="parameters"></a>Parametry  
 *pgrfBSCF*  
 [out] Wskaźnik do **BINDF** wartości wyliczenia wskazująca, jak powinna wystąpić operacja powiązania. Domyślnie ustawiony z następującymi wartościami wyliczenia:  
  
 **BINDF_ASYNCHRONOUS** asynchronicznego pobierania.  
  
 **BINDF_ASYNCSTORAGE** `OnDataAvailable` zwraca **E_PENDING** gdy dane nie są jeszcze dostępne zamiast zablokowana do czasu dane są dostępne.  
  
 **BINDF_GETNEWESTVERSION** Operacja powiązania należy pobrać najnowszą wersję danych.  
  
 **BINDF_NOWRITECACHE** Operacja powiązania nie należy przechowywać pobrane dane w pamięci podręcznej dysku.  
  
 *pbindinfo*  
 [w, out] Wskaźnik do **wiązania** struktury nadanie więcej informacji na temat jak obiekt chce powiązanie występuje.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy `HRESULT` wartości.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja ustawia powiązanie asynchroniczne i użyć wypychania danych modelu. W modelu wypychania danych moniker dyski operacja asynchronicznego powiązania i stale powiadamia klient zawsze, gdy nowe dane są dostępne.  
  
##  <a name="getpriority"></a>  CBindStatusCallback::GetPriority  
 Metoda wywoływana przez asynchroniczne moniker uzyskanie priorytet Operacja powiązania.  
  
```
STDMETHOD(GetPriority)(LONG* pnPriority);
```  
  
### <a name="parameters"></a>Parametry  
 *pnPriority*  
 [out] Adres **DŁUGI** zmiennej, która w przypadku powodzenia otrzymuje priorytet.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **E_NOTIMPL**.  
  
##  <a name="m_dwavailabletoread"></a>  CBindStatusCallback::m_dwAvailableToRead  
 Może służyć do przechowywania liczbę bajtów dostępnych do odczytu.  
  
```
DWORD m_dwAvailableToRead;
```  
  
### <a name="remarks"></a>Uwagi  
 Zainicjowane zero w `StartAsyncDownload`.  
  
##  <a name="m_dwtotalread"></a>  CBindStatusCallback::m_dwTotalRead  
 Łączna liczba bajtów odczytanych w transferu danych asynchronicznych.  
  
```
DWORD m_dwTotalRead;
```  
  
### <a name="remarks"></a>Uwagi  
 Zwiększany zawsze `OnDataAvailable` jest wywoływana przez liczbę bajtów odczytanych w rzeczywistości. Zainicjowane zero w `StartAsyncDownload`.  
  
##  <a name="m_pfunc"></a>  CBindStatusCallback::m_pFunc  
 Funkcja wskazywana przez `m_pFunc` jest wywoływana przez `OnDataAvailable` po odczytuje dostępnych danych (na przykład do przechowywania danych, lub wydrukuj ją do ekranu).  
  
```
ATL_PDATAAVAILABLE m_pFunc;
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja wskazywana przez `m_pFunc` jest elementem członkowskim klasy do obiektu i ma następującą składnię:  
  
```  
void Function_Name(  
   CBindStatusCallback<T>* pbsc,  
   BYTE* pBytes,  
   DWORD dwSize  
   );  
```  
  
##  <a name="m_pt"></a>  CBindStatusCallback::m_pT  
 Wskaźnik do obiektu żądającego transferu danych asynchronicznych.  
  
```
T* m_pT;
```  
  
### <a name="remarks"></a>Uwagi  
 `CBindStatusCallback` Obiektu jest którego ma zastosowany szablon dla tego obiektu klasy.  
  
##  <a name="m_spbindctx"></a>  CBindStatusCallback::m_spBindCtx  
 Wskaźnik do [IBindCtx](http://msdn.microsoft.com/library/windows/desktop/ms693755) interfejs, który zapewnia dostęp do kontekstu powiązania (obiekt, który przechowuje informacje dotyczące operacji wiązania określonego krótkiej nazwy).  
  
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
 Zainicjowane w `OnStartBinding` i wydanej w `OnStopBinding`.  
  
##  <a name="m_spmoniker"></a>  CBindStatusCallback::m_spMoniker  
 Wskaźnik do [imoniker —](http://msdn.microsoft.com/library/windows/desktop/ms679705) interfejs dla adresu URL do użycia.  
  
```
CComPtr<IMoniker> m_spMoniker;
```  
  
### <a name="remarks"></a>Uwagi  
 Zainicjowane w `StartAsyncDownload`.  
  
##  <a name="m_spstream"></a>  CBindStatusCallback::m_spStream  
 Wskaźnik do [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) interfejsu bieżącej operacji wiązania.  
  
```
CComPtr<IStream> m_spStream;
```  
  
### <a name="remarks"></a>Uwagi  
 Zainicjowane w `OnDataAvailable` z **STGMEDIUM** struktury, kiedy **BCSF** flaga jest **BCSF_FIRSTDATANOTIFICATION** i kiedy **BCSF**  flaga jest **BCSF_LASTDATANOTIFICATION**.  
  
##  <a name="ondataavailable"></a>  CBindStatusCallback::OnDataAvailable  
 Wywołania dostarczany przez system asynchroniczne krótkiej nazwy `OnDataAvailable` dostarczający dane do obiektu, ponieważ staje się dostępny.  
  
```
STDMETHOD(  
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```  
  
### <a name="parameters"></a>Parametry  
 *grfBSCF*  
 [in] A **BSCF** wartości wyliczenia. Co najmniej jeden z następujących: **BSCF_FIRSTDATANOTIFICATION**, **BSCF_INTERMEDIARYDATANOTIFICATION**, lub **BSCF_LASTDATANOTIFICATION**.  
  
 `dwSize`  
 [in] Zbiorcza ilość (w bajtach) dostępne od początku powiązania danych. Może być równa zero, wskazując ilość danych nie jest ważna, lub że nie kwotę stały się dostępne.  
  
 *pformatetc*  
 [in] Wskaźnik do [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682242) strukturę, która zawiera format dostępnych danych. Jeśli nie ma formatu, może być **CF_NULL**.  
  
 *pstgmed*  
 [in] Wskaźnik do [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms695269) struktury, która przechowuje dane teraz dostępne.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy `HRESULT` wartości.  
  
### <a name="remarks"></a>Uwagi  
 `OnDataAvailable` odczytuje dane, a następnie wywołuje metodę klasy do obiektu (na przykład do przechowywania danych, lub wydrukuj ją do ekranu). Zobacz [CBindStatusCallback::StartAsyncDownload](#startasyncdownload) szczegółowe informacje.  
  
##  <a name="onlowresource"></a>  CBindStatusCallback::OnLowResource  
 Wywoływane, gdy zasoby są małe.  
  
```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```  
  
### <a name="parameters"></a>Parametry  
 `dwReserved`  
 Zastrzeżone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
##  <a name="onobjectavailable"></a>  CBindStatusCallback::OnObjectAvailable  
 Wywołuje asynchroniczną krótkiej nazwy do przekazania wskaźnika interfejsu obiektu do aplikacji.  
  
```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```  
  
### <a name="parameters"></a>Parametry  
 `riid`  
 Identyfikator interfejsu wymaganego interfejsu. Nieużywane.  
  
 `punk`  
 Adres interfejsu IUnknown. Nieużywane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
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
 `ulProgress`  
 Długich liczb całkowitych bez znaku. Nieużywane.  
  
 `ulProgressMax`  
 Niepodpisane długich liczb całkowitych węzła nieużywane.  
  
 `ulStatusCode`  
 Długich liczb całkowitych bez znaku. Nieużywane.  
  
 `szStatusText`  
 Adres wartość ciągu. Nieużywane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
##  <a name="onstartbinding"></a>  CBindStatusCallback::OnStartBinding  
 Ustawia element członkowski danych [m_spBinding](#m_spbinding) do `IBinding` wskaźnika w `pBinding`.  
  
```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```  
  
### <a name="parameters"></a>Parametry  
 `dwReserved`  
 Zarezerwowane do użytku w przyszłości.  
  
 `pBinding`  
 [in] Operacja powiązania adres interfejsu IBinding bieżącego. To nie może mieć wartości NULL. Klient powinien wywoływać AddRef na wskaźnik do odwołania do obiektu powiązania zachowania.  
  
##  <a name="onstopbinding"></a>  CBindStatusCallback::OnStopBinding  
 Wersje `IBinding` wskaźnika w elemencie członkowskim danych [m_spBinding](#m_spbinding).  
  
```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```  
  
### <a name="parameters"></a>Parametry  
 `hresult`  
 Kod stanu zwrócony przez operację powiązania.  
  
 szStatusText  
 Adres węzła nieużywane wartość ciągu.  
  
### <a name="remarks"></a>Uwagi  
 Metoda wywoływana przez dostarczany przez system moniker asynchroniczne wskazująca koniec operacji wiązania.  
  
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
 *PT*  
 [in] Wskaźnik do obiektu żądającego transferu danych asynchronicznych. `CBindStatusCallback` Obiektu jest którego ma zastosowany szablon dla tego obiektu klasy.  
  
 *pFunc*  
 [in] Wskaźnik do funkcji, która odbiera odczytywane dane. Funkcja jest elementem członkowskim klasy do obiektu typu `T`. Zobacz **uwagi** składnię i przykład.  
  
 `bstrURL`  
 [in] Adres URL mają zostać pobrane dane. Może być dowolną prawidłową nazwę pliku lub adres URL. Nie może być **NULL**. Na przykład:  
  
 `CComBSTR mybstr =_T("http://somesite/data.htm")`  
  
 `pUnkContainer`  
 [in] **IUnknown** kontenera. **Wartość NULL** domyślnie.  
  
 `bRelative`  
 [in] Flaga wskazująca, czy adres URL jest względna lub bezwzględna. **FALSE** domyślnie, czyli adres URL jest bezwzględna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy `HRESULT` wartości.  
  
### <a name="remarks"></a>Uwagi  
 Za każdym razem, gdy dane są dostępne są wysyłane za pośrednictwem `OnDataAvailable`. `OnDataAvailable` odczytuje dane i wywołuje funkcję wskazywana przez *pFunc* (na przykład do przechowywania danych, lub wydrukuj ją do ekranu).  
  
 Funkcja wskazywana przez *pFunc* jest elementem członkowskim klasy do obiektu i ma następującą składnię:  
  
 `void Function_Name(`  
  
 `CBindStatusCallback<T>*` `pbsc` `,`  
  
 `BYTE*` `pBytes` `,`  
  
 `DWORD``dwSize`  
  
 `);`  
  
 W poniższym przykładzie (pobierane z [ASYNC](../../visual-cpp-samples.md) przykładowe), funkcja `OnData` zapisuje odebranych danych w polu tekstowym.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
