---
title: Klasa CAsyncMonikerFile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile::CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile::Close
- AFXOLE/CAsyncMonikerFile::GetBinding
- AFXOLE/CAsyncMonikerFile::GetFormatEtc
- AFXOLE/CAsyncMonikerFile::Open
- AFXOLE/CAsyncMonikerFile::CreateBindStatusCallback
- AFXOLE/CAsyncMonikerFile::GetBindInfo
- AFXOLE/CAsyncMonikerFile::GetPriority
- AFXOLE/CAsyncMonikerFile::OnDataAvailable
- AFXOLE/CAsyncMonikerFile::OnLowResource
- AFXOLE/CAsyncMonikerFile::OnProgress
- AFXOLE/CAsyncMonikerFile::OnStartBinding
- AFXOLE/CAsyncMonikerFile::OnStopBinding
dev_langs:
- C++
helpviewer_keywords:
- CAsyncMonikerFile [MFC], CAsyncMonikerFile
- CAsyncMonikerFile [MFC], Close
- CAsyncMonikerFile [MFC], GetBinding
- CAsyncMonikerFile [MFC], GetFormatEtc
- CAsyncMonikerFile [MFC], Open
- CAsyncMonikerFile [MFC], CreateBindStatusCallback
- CAsyncMonikerFile [MFC], GetBindInfo
- CAsyncMonikerFile [MFC], GetPriority
- CAsyncMonikerFile [MFC], OnDataAvailable
- CAsyncMonikerFile [MFC], OnLowResource
- CAsyncMonikerFile [MFC], OnProgress
- CAsyncMonikerFile [MFC], OnStartBinding
- CAsyncMonikerFile [MFC], OnStopBinding
ms.assetid: 17378b66-a49a-4b67-88e3-7756ad26a2fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c40d012ba32d2ea656024af77779f2cf8f67419a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433028"
---
# <a name="casyncmonikerfile-class"></a>Klasa CAsyncMonikerFile

Oferuje funkcję do użytku z monikerów asynchronicznych w kontrolkach ActiveX (dawniej kontrolka OLE).

## <a name="syntax"></a>Składnia

```
class CAsyncMonikerFile : public CMonikerFile
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAsyncMonikerFile::CAsyncMonikerFile](#casyncmonikerfile)|Konstruuje `CAsyncMonikerFile` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAsyncMonikerFile::Close](#close)|Zamyka i zwalnia wszystkie zasoby.|
|[CAsyncMonikerFile::GetBinding](#getbinding)|Pobiera wskaźnik do transferu asynchronicznego powiązania.|
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|Pobiera format danych w strumieniu.|
|[CAsyncMonikerFile::Open](#open)|Otwiera plik asynchronicznie.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|Tworzy obiekt COM, który implementuje `IBindStatusCallback`.|
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|Metoda wywoływana przez biblioteka systemowa OLE na żądanie informacji od typu powiązania ma zostać utworzony.|
|[CAsyncMonikerFile::GetPriority](#getpriority)|Metoda wywoływana przez biblioteki OLE systemu można pobrać priorytet powiązania.|
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|Wywoływana w celu zapewnienia danych po jej udostępnieniu do klienta podczas wykonywania operacji asynchronicznej powiązania.|
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|Wywołuje się, gdy brakuje zasobów.|
|[CAsyncMonikerFile::OnProgress](#onprogress)|Wywołuje się, by wskazać proces pobierania danych.|
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|Wywołuje się, gdy rozpoczyna się wiązanie.|
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|Wywołuje się, gdy zatrzymano transfer asynchronicznego.|

## <a name="remarks"></a>Uwagi

Pochodną [CMonikerFile](../../mfc/reference/cmonikerfile-class.md), który z kolei pochodzi od [COleStreamFile](../../mfc/reference/colestreamfile-class.md), `CAsyncMonikerFile` używa [imoniker —](/windows/desktop/api/objidl/nn-objidl-imoniker) interfejs zapewnia dostęp dowolny strumień danych do asynchronicznie w tym asynchroniczne ładowanie plików z adresu URL. Pliki mogą być ścieżki danych właściwości formantów ActiveX.

Monikery asynchroniczne są używane głównie w aplikacje internetowe i formantów ActiveX zapewnienie dynamicznego interfejsu użytkownika podczas transferu plików. Głównym przykładem polega na użyciu [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) zapewnienie asynchronicznej właściwości formantów ActiveX. `CDataPathProperty` Obiektu wielokrotnie otrzyma wywołanie zwrotne do wskazania dostępności nowych danych podczas procesu wymiany długich właściwości.

Aby uzyskać więcej informacji o sposobie używania formantów ActiveX i monikerów asynchronicznych w aplikacjach internetowych zobacz następujące artykuły:

- [Internecie pierwsze kroki: Monikery asynchroniczne](../../mfc/asynchronous-monikers-on-the-internet.md)

- [Internecie pierwsze kroki: Kontrolki ActiveX](../../mfc/activex-controls-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

`CAsyncMonikerFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

##  <a name="casyncmonikerfile"></a>  CAsyncMonikerFile::CAsyncMonikerFile

Konstruuje `CAsyncMonikerFile` obiektu.

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>Uwagi

Nie powoduje utworzenia `IBindHost` interfejsu. `IBindHost` jest używana tylko wtedy, gdy podasz w `Open` funkcja elementu członkowskiego.

Aby uzyskać opis `IBindHost` interfejsu, zobacz zestaw Windows SDK.

##  <a name="close"></a>  CAsyncMonikerFile::Close

Wywołaj tę funkcję, aby zamknąć i zwolnić wszystkie zasoby.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Można wywołać w plikach nieotwarte lub już zamknięte.

##  <a name="createbindstatuscallback"></a>  CAsyncMonikerFile::CreateBindStatusCallback

Tworzy obiekt COM, który implementuje `IBindStatusCallback`.

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>Parametry

*pUnkControlling*<br/>
Wskaźnik do kontrolowanie nieznane (zewnętrzny `IUnknown`) lub wartość NULL, jeśli nie jest używana agregacja.

### <a name="return-value"></a>Wartość zwracana

Jeśli *pUnkControlling* nie ma wartości NULL, funkcja zwraca wskaźnik do wewnętrznej `IUnknown` na nowe obsługujący obiekt COM `IBindStatusCallback`. Jeśli `pUnkControlling` ma wartość NULL, funkcja zwraca wskaźnik do `IUnknown` na nowe obsługujący obiekt COM `IBindStatusCallback`.

### <a name="remarks"></a>Uwagi

`CAsyncMonikerFile` wymaga obiektu COM, który implementuje `IBindStatusCallback`. MFC implementuje takiego obiektu, a jest się agregowaniu. Można zastąpić `CreateBindStatusCallback` zwracać obiekt COM. Obiekt COM może agregować implementacji MFC, wywołując `CreateBindStatusCallback` z kontrolowanie nieznane obiektu COM. Obiekty COM implementowane przy użyciu `CCmdTarget` Obsługa COM można pobrać kontrolowanie nieznane za pomocą `CCmdTarget::GetControllingUnknown`.

Alternatywnie obiekt COM można delegować do implementacji MFC, wywołując `CreateBindStatusCallback( NULL )`.

[CAsyncMonikerFile::Open](#open) wywołania `CreateBindStatusCallback`.

Aby uzyskać więcej informacji na temat monikerów asynchronicznych i wiązania asynchronicznego, zobacz [IBindStatusCallback](https://msdn.microsoft.com/library/ie/ms775060) interfejsu i [jak asynchroniczne wiązanie i Praca magazynu](/windows/desktop/Stg/how-asynchronous-binding-and-storage-work). Aby uzyskać omówienie agregacji, zobacz [agregacji](/windows/desktop/com/aggregation). Wszystkie trzy tematy znajdują się w zestawie Windows SDK.

##  <a name="getbindinfo"></a>  CAsyncMonikerFile::GetBindInfo

Wywołuje się, od klientów asynchronicznego moniker mówić asynchronicznego moniker jak potrzebuje do powiązania.

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>Wartość zwracana

Pobiera ustawienia `IBindStatusCallBack`. Aby uzyskać opis `IBindStatusCallback` interfejsu, zobacz zestaw Windows SDK.

### <a name="remarks"></a>Uwagi

Domyślna implementacja ustawia powiązanie asynchroniczny, aby użyć nośnika magazynowania (strumień) i używania tego modelu wypychania danych. Należy przesłonić tę funkcję, jeśli chcesz zmienić zachowanie wiązania.

Jednym z powodów w ten sposób będzie można powiązać, przy użyciu modelu ściągania danych zamiast model wypychania danych. W modelu ściągania danych klienta dyski Operacja powiązania i moniker tylko dostarcza dane do klienta została przeczytana. W modelu danych wypychania moniker dyski operacja asynchronicznego powiązania i stale powiadamia klient zawsze wtedy, gdy nowe dane są dostępne.

##  <a name="getbinding"></a>  CAsyncMonikerFile::GetBinding

Wywołaj tę funkcję, aby pobrać wskaźnika do transferu asynchronicznego powiązania.

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `IBinding` interfejsu po rozpoczęciu transferu asynchronicznego. Zwraca wartość NULL, jeśli jakichś powodów przeniesienia nie może podlegać asynchronicznie.

### <a name="remarks"></a>Uwagi

To umożliwia kontrolowanie transferu danych za pomocą `IBinding` interfejsu, na przykład za pomocą `IBinding::Abort`, `IBinding::Pause`, i `IBinding::Resume`.

Aby uzyskać opis `IBinding` interfejsu, zobacz zestaw Windows SDK.

##  <a name="getformatetc"></a>  CAsyncMonikerFile::GetFormatEtc

Wywołaj tę funkcję, aby pobrać formatu danych w strumieniu.

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do struktury Windows [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) dla aktualnie otwartą strumienia. Zwraca wartość NULL, jeśli moniker nie została powiązana, jeśli nie jest asynchroniczne albo operacja asynchroniczna nie zostało uruchomione.

##  <a name="getpriority"></a>  CAsyncMonikerFile::GetPriority

O nazwie od klienta asynchronicznego moniker proces wiązania zacznie otrzymywać pierwszeństwa do wątku dla operacji wiązania.

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>Wartość zwracana

Priorytet, w którym odbędzie się transferu asynchronicznego. Jeden flagi priorytet wątku standardowe: THREAD_PRIORITY_ABOVE_NORMAL, THREAD_PRIORITY_BELOW_NORMAL, THREAD_PRIORITY_HIGHEST, THREAD_PRIORITY_IDLE, THREAD_PRIORITY_LOWEST, THREAD_PRIORITY_NORMAL i THREAD_PRIORITY_TIME_CRITICAL. Zobacz opis funkcji Windows [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) opis tych wartości.

### <a name="remarks"></a>Uwagi

`GetPriority` nie należy wywoływać bezpośrednio. THREAD_PRIORITY_NORMAL jest zwracany przez domyślne wdrożenie.

##  <a name="ondataavailable"></a>  CAsyncMonikerFile::OnDataAvailable

Wywołuje asynchroniczną moniker `OnDataAvailable` do dostarczania danych do klienta, gdy tylko zostanie udostępniona, podczas asynchronicznego powiązanie operacji.

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>Parametry

*niezerowego*<br/>
Zbiorcza kwota (w bajtach) dostępnych od początku powiązanie danych. Może być równy zero, wskazujący ilość danych nie jest odpowiednie do operacji lub że bez żadnej kwoty określone stały się dostępne.

*bscfFlag*<br/>
Wartość wyliczenia BSCF. Może być co najmniej jeden z następujących wartości:

- BSCF_FIRSTDATANOTIFICATION identyfikuje pierwsze wywołanie `OnDataAvailable` powiązania danej operacji.

- BSCF_INTERMEDIATEDATANOTIFICATION identyfikuje wywołanie pośrednie `OnDataAvailable` dla operacji wiązania.

- BSCF_LASTDATANOTIFICATION identyfikuje ostatnie wywołanie elementu `OnDataAvailable` dla operacji wiązania.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji, nic nie robi. Zobacz poniższy przykład przykładową implementację.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

##  <a name="onlowresource"></a>  CAsyncMonikerFile::OnLowResource

Metoda wywoływana przez monikera programu, gdy zasoby są małe.

```
virtual void OnLowResource();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołuje `GetBinding( )-> Abort( )`.

##  <a name="onprogress"></a>  CAsyncMonikerFile::OnProgress

Metoda wywoływana przez moniker wielokrotnie, aby wskazać Bieżący postęp tej operacji powiązania, zwykle znajduje się w odpowiednich odstępach czasu podczas długotrwałej operacji.

```
virtual void OnProgress(
    ULONG ulProgress,
    ULONG ulProgressMax,
    ULONG ulStatusCode,
    LPCTSTR szStatusText);
```

### <a name="parameters"></a>Parametry

*ulProgress*<br/>
Wskazuje bieżący postęp operacji powiązania względem maksymalna oczekiwana wartość podana w *ulProgressMax*.

*ulProgressMax*<br/>
Wskazuje oczekiwany maksymalną wartość *ulProgress* na czas trwania wywołania `OnProgress` dla tej operacji.

*ulStatusCode*<br/>
Zawiera dodatkowe informacje na temat postępu operacji wiązania. Prawidłowe wartości są pobierane z `BINDSTATUS` wyliczenia. Możliwe wartości można znaleźć w temacie uwagi.

*szStatusText*<br/>
Informacje o postępie bieżącej, w zależności od wartości *ulStatusCode*. Możliwe wartości można znaleźć w temacie uwagi.

### <a name="remarks"></a>Uwagi

Możliwe wartości dla *ulStatusCode* (i *szStatusText* dla każdej wartości) są:

|||
|-|-|
|BINDSTATUS_FINDINGRESOURCE  |Operacja powiązania jest znalezienie zasobu, który zawiera obiekt lub związania z magazynu. *SzStatusText* zawiera nazwę wyświetlaną zasobów wyszukiwany dla (na przykład "www.microsoft.com").  |
|BINDSTATUS_CONNECTING  |Operacja powiązania nawiązuje połączenie z zasobem, który zawiera obiekt lub związania z magazynu. *SzStatusText* zawiera nazwę wyświetlaną zasobu połączenia (na przykład adres IP).  |
|BINDSTATUS_SENDINGREQUEST|Operacja powiązania żąda obiektu lub związania z magazynu. *SzStatusText* zawiera nazwę wyświetlaną obiektu (na przykład, nazwa pliku).|
|BINDSTATUS_REDIRECTING  |Operacja powiązania został przekierowany do lokalizacji danych. *SzStatusText* zawiera nazwę wyświetlaną nowej lokalizacji danych.  |
|BINDSTATUS_USINGCACHEDCOPY  |Operacja powiązania pobiera żądany obiekt lub magazynu z kopii w pamięci podręcznej. *SzStatusText* ma wartość NULL.  |
|BINDSTATUS_BEGINDOWNLOADDATA  |Operacja powiązania rozpoczął odbieranie obiektu lub związania z magazynu. *SzStatusText* zawiera nazwę wyświetlaną lokalizacji danych.|
|BINDSTATUS_DOWNLOADINGDATA  |Operacja powiązania w dalszym ciągu otrzymywać obiekt lub związania z magazynu. *SzStatusText* zawiera nazwę wyświetlaną lokalizacji danych.  |
|BINDSTATUS_ENDDOWNLOADDATA  |Operacja powiązania zostało zakończone, odbieranie obiektu lub związania z magazynu. *SzStatusText* zawiera nazwę wyświetlaną lokalizacji danych.  |
|BINDSTATUS_CLASSIDAVAILABLE  |Wystąpienie obiektu powiązania jest niemal ma zostać utworzony. *SzStatusText* udostępnia CLSID nowego obiektu w postaci ciągu, co pozwala klientowi możliwość anulowania operacji wiązania w razie potrzeby.  |

##  <a name="onstartbinding"></a>  CAsyncMonikerFile::OnStartBinding

Przesłonić tę funkcję w swojej klasy pochodne, aby wykonywać akcje w przypadku, gdy rozpoczyna się wiązanie.

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>Uwagi

Ta funkcja zostanie wywołane przez moniker. Domyślna implementacja nic nie robi.

##  <a name="onstopbinding"></a>  CAsyncMonikerFile::OnStopBinding

Metoda wywoływana przez moniker na końcu Operacja powiązania.

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>Parametry

*wartość HRESULT*<br/>
Błąd lub ostrzeżenie wartość HRESULT.

*szErrort*<br/>
Ciąg znaków z opisem błędu.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę funkcję, aby wykonać akcje, gdy zatrzymano transfer. Domyślnie funkcja zwolni `IBinding`.

Aby uzyskać opis `IBinding` interfejsu, zobacz zestaw Windows SDK.

##  <a name="open"></a>  CAsyncMonikerFile::Open

Wywołaj tę funkcję elementu członkowskiego, aby otworzyć plik asynchronicznie.

```
virtual BOOL Open(
    LPCTSTR lpszURL,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IBindHost* pBindHost,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IBindHost* pBindHost,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IServiceProvider* pServiceProvider,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IServiceProvider* pServiceProvider,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IUnknown* pUnknown,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IUnknown* pUnknown,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*lpszURL*<br/>
Wskaźnik do otwarcia asynchronicznie. Plik może być prawidłowym adresem URL lub nazwy pliku.

*pError*<br/>
Wskaźnik do wyjątków pliku. W przypadku wystąpienia błędu zostanie ustawiona przyczynie.

*pMoniker*<br/>
Wskaźnik do interfejsu asynchronicznego moniker `IMoniker`, dokładne moniker, stanowiący połączenie moniker własny dokument, który można pobrać z `IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)`i krótka utworzone na podstawie nazwy ścieżki. Kontrolki można użyć tej krótkiej nazwy do powiązania, ale nie jest to moniker zapisywaniu formantu.

*pBindHost*<br/>
Wskaźnik do `IBindHost` interfejsu, która będzie służyć do tworzenia krótkiej nazwy z potencjalnie względną nazwę ścieżki. Jeśli host powiązania jest nieprawidłowy lub nie zapewnia krótka, wywołanie domyślnie `Open(lpszFileName,pError)`. Aby uzyskać opis `IBindHost` interfejsu, zobacz zestaw Windows SDK.

*pServiceProvider*<br/>
Wskaźnik do `IServiceProvider` interfejsu. Jeśli dostawca usług jest nieprawidłowy lub nie powiedzie się zapewnić obsługę dla `IBindHost`, wartością domyślną jest wywołanie `Open(lpszFileName,pError)`.

*pUnknown*<br/>
Wskaźnik do `IUnknown` interfejsu. Jeśli `IServiceProvider` zostanie znaleziony, zapytania funkcji dla `IBindHost`. Jeśli dostawca usług jest nieprawidłowy lub nie powiedzie się zapewnić obsługę dla `IBindHost`, wartością domyślną jest wywołanie `Open(lpszFileName,pError)`.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli plik jest otwarty pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

To wywołanie inicjuje proces wiązania.

Możesz użyć adresu URL lub nazwę pliku do *lpszURL* parametru. Na przykład:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\- lub —

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CMonikerFile](../../mfc/reference/cmonikerfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CMonikerFile](../../mfc/reference/cmonikerfile-class.md)<br/>
[Klasa CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)
