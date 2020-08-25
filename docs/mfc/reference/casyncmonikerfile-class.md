---
title: Klasa CAsyncMonikerFile
ms.date: 11/04/2016
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
ms.openlocfilehash: 259d31b9c1e198b326ba616481dbbf5315225546
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845942"
---
# <a name="casyncmonikerfile-class"></a>Klasa CAsyncMonikerFile

Zapewnia funkcjonalność używania asynchronicznych monikerów w kontrolkach ActiveX (dawniej formanty OLE).

## <a name="syntax"></a>Składnia

```
class CAsyncMonikerFile : public CMonikerFile
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAsyncMonikerFile::CAsyncMonikerFile](#casyncmonikerfile)|Konstruuje `CAsyncMonikerFile` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAsyncMonikerFile:: Close](#close)|Zamyka i zwalnia wszystkie zasoby.|
|[CAsyncMonikerFile:: GetBinding](#getbinding)|Pobiera wskaźnik do powiązania transferu asynchronicznego.|
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|Pobiera format danych w strumieniu.|
|[CAsyncMonikerFile:: Open](#open)|Otwiera plik asynchronicznie.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|Tworzy obiekt COM, który implementuje `IBindStatusCallback` .|
|[CAsyncMonikerFile:: GetBindInfo](#getbindinfo)|Wywoływane przez bibliotekę systemową OLE do żądania informacji o typie powiązania, który ma zostać utworzony.|
|[CAsyncMonikerFile:: GetPriority](#getpriority)|Wywoływane przez bibliotekę systemową OLE, aby uzyskać priorytet powiązania.|
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|Wywołuje się, by zapewnić dane, które staną się dostępne dla klienta podczas asynchronicznych operacji wiązania.|
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|Wywoływana, gdy zasoby są niskie.|
|[CAsyncMonikerFile:: OnProgress](#onprogress)|Wywołuje się, by wskazać postęp procesu pobierania danych.|
|[CAsyncMonikerFile:: OnStartBinding](#onstartbinding)|Wywoływana, gdy trwa uruchamianie powiązania.|
|[CAsyncMonikerFile:: OnStopBinding](#onstopbinding)|Wywołuje się, gdy transfer asynchroniczny został zatrzymany.|

## <a name="remarks"></a>Uwagi

Pochodny od [CMonikerFile](../../mfc/reference/cmonikerfile-class.md), który z kolei jest wyprowadzany z [COleStreamFile](../../mfc/reference/colestreamfile-class.md), `CAsyncMonikerFile` korzysta z interfejsu [IMoniker —](/windows/win32/api/objidl/nn-objidl-imoniker) , aby asynchronicznie uzyskiwać dostęp do strumienia danych, łącznie z ładowaniem plików asynchronicznie z adresu URL. Pliki mogą być właściwościami datapath formantów ActiveX.

Monikery asynchroniczne są używane przede wszystkim w aplikacjach internetowych i kontrolkach ActiveX w celu zapewnienia, że interfejs użytkownika odpowiada podczas transferu plików. Przykładem jest użycie [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) do dostarczania właściwości asynchronicznych dla formantów ActiveX. `CDataPathProperty`Obiekt będzie wielokrotnie pobierać wywołanie zwrotne, aby wskazać dostępność nowych danych podczas długotrwałego procesu wymiany właściwości.

Aby uzyskać więcej informacji o sposobach korzystania z monikerów asynchronicznych i kontrolek ActiveX w aplikacjach internetowych, zobacz następujące artykuły:

- [Pierwsze kroki w Internecie: monikery asynchroniczne](../../mfc/asynchronous-monikers-on-the-internet.md)

- [Internet — pierwsze kroki: kontrolki ActiveX](../../mfc/activex-controls-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

`CAsyncMonikerFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** Afxole. h

## <a name="casyncmonikerfilecasyncmonikerfile"></a><a name="casyncmonikerfile"></a> CAsyncMonikerFile::CAsyncMonikerFile

Konstruuje `CAsyncMonikerFile` obiekt.

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>Uwagi

Nie tworzy `IBindHost` interfejsu. `IBindHost` jest używana tylko wtedy, gdy podajesz ją w `Open` funkcji członkowskiej.

Opis `IBindHost` interfejsu można znaleźć w Windows SDK.

## <a name="casyncmonikerfileclose"></a><a name="close"></a> CAsyncMonikerFile:: Close

Wywołaj tę funkcję, aby zamknąć i zwolnić wszystkie zasoby.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Może być wywoływana dla nieotwartych lub już zamkniętych plików.

## <a name="casyncmonikerfilecreatebindstatuscallback"></a><a name="createbindstatuscallback"></a> CAsyncMonikerFile::CreateBindStatusCallback

Tworzy obiekt COM, który implementuje `IBindStatusCallback` .

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>Parametry

*pUnkControlling*<br/>
Wskaźnik do kontrolki nieznany (zewnętrzny `IUnknown` ) lub null, jeśli agregacja nie jest używana.

### <a name="return-value"></a>Wartość zwracana

Jeśli *pUnkControlling* nie ma wartości null, funkcja zwraca wskaźnik do `IUnknown` elementu wewnętrznego w nowym obiekcie com obsługującym `IBindStatusCallback` . Jeśli `pUnkControlling` ma wartość null, funkcja zwraca wskaźnik do `IUnknown` nowego obiektu com, który obsługuje `IBindStatusCallback` .

### <a name="remarks"></a>Uwagi

`CAsyncMonikerFile` wymaga obiektu COM, który implementuje `IBindStatusCallback` . MFC implementuje taki obiekt i jest agregowany. Można przesłonić, `CreateBindStatusCallback` Aby zwrócić własny obiekt com. Obiekt COM może agregować implementację MFC przez wywołanie `CreateBindStatusCallback` z nieznanym obiektem com. Obiekty COM zaimplementowane przy użyciu `CCmdTarget` obsługi com mogą pobrać kontrolki nieznane przy użyciu `CCmdTarget::GetControllingUnknown` .

Alternatywnie obiekt COM może delegować do implementacji MFC przez wywołanie `CreateBindStatusCallback( NULL )` .

[CAsyncMonikerFile:: Open —](#open) wywołania `CreateBindStatusCallback` .

Aby uzyskać więcej informacji na temat monikerów asynchronicznych i powiązań asynchronicznych, zobacz Interfejs [IBindStatusCallback](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775060\(v=vs.85\)) oraz [sposób działania powiązań asynchronicznych i magazynu](/windows/win32/Stg/how-asynchronous-binding-and-storage-work). Aby zapoznać się z omówieniem agregacji, zobacz [agregacja](/windows/win32/com/aggregation). Wszystkie trzy tematy znajdują się w Windows SDK.

## <a name="casyncmonikerfilegetbindinfo"></a><a name="getbindinfo"></a> CAsyncMonikerFile:: GetBindInfo

Wywołuje się od klienta synchronicznej monikera, aby poinformować asynchroniczną moniker, w jaki sposób chce powiązać.

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>Wartość zwracana

Pobiera ustawienia dla `IBindStatusCallBack` . Opis `IBindStatusCallback` interfejsu można znaleźć w Windows SDK.

### <a name="remarks"></a>Uwagi

Domyślna implementacja ustawia powiązanie jako asynchroniczne, aby użyć nośnika magazynu (strumienia) i użyć modelu wypychania danych. Zastąp tę funkcję, jeśli chcesz zmienić zachowanie powiązania.

Jedną z przyczyn tego problemu będzie powiązanie przy użyciu modelu ściągania danych, a nie modelu wypychania danych. W modelu ściągania danych klient kieruje operację wiązania, a moniker udostępnia dane klientowi tylko wtedy, gdy jest odczytywany. W modelu wypychania danych moniker jest używany do asynchronicznej operacji wiązania i ciągle powiadamia klienta za każdym razem, gdy nowe dane są dostępne.

## <a name="casyncmonikerfilegetbinding"></a><a name="getbinding"></a> CAsyncMonikerFile:: GetBinding

Wywołaj tę funkcję, aby pobrać wskaźnik do powiązania transferu asynchronicznego.

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu, który jest `IBinding` dostarczany po rozpoczęciu transferu asynchronicznego. Zwraca wartość NULL, jeśli z jakiegoś powodu nie można wykonać transferu asynchronicznego.

### <a name="remarks"></a>Uwagi

Dzięki temu można kontrolować proces transferu danych za pomocą `IBinding` interfejsu, na przykład z `IBinding::Abort` , `IBinding::Pause` , i `IBinding::Resume` .

Opis `IBinding` interfejsu można znaleźć w Windows SDK.

## <a name="casyncmonikerfilegetformatetc"></a><a name="getformatetc"></a> CAsyncMonikerFile::GetFormatEtc

Wywołaj tę funkcję, aby pobrać format danych w strumieniu.

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do struktury systemu Windows [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dla aktualnie otwartego strumienia. Zwraca wartość NULL, jeśli moniker nie został powiązany, jeśli nie jest asynchroniczny lub jeśli operacja asynchroniczna nie została rozpoczęta.

## <a name="casyncmonikerfilegetpriority"></a><a name="getpriority"></a> CAsyncMonikerFile:: GetPriority

Wywoływana z klienta asynchronicznej monikera, ponieważ proces powiązania zaczyna otrzymywać priorytet przyznany do wątku dla operacji powiązania.

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>Wartość zwracana

Priorytet, w którym będzie miało miejsce transfer asynchroniczny. Jedna z flag standardowego priorytetu wątku: THREAD_PRIORITY_ABOVE_NORMAL, THREAD_PRIORITY_BELOW_NORMAL, THREAD_PRIORITY_HIGHEST, THREAD_PRIORITY_IDLE, THREAD_PRIORITY_LOWEST, THREAD_PRIORITY_NORMAL i THREAD_PRIORITY_TIME_CRITICAL. Aby uzyskać opis tych wartości, zobacz [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) funkcji systemu Windows.

### <a name="remarks"></a>Uwagi

`GetPriority` nie powinien być wywoływany bezpośrednio. THREAD_PRIORITY_NORMAL jest zwracana przez implementację domyślną.

## <a name="casyncmonikerfileondataavailable"></a><a name="ondataavailable"></a> CAsyncMonikerFile::OnDataAvailable

Asynchroniczne wywołania monikera `OnDataAvailable` umożliwiające dostarczenie danych do klienta w miarę ich udostępnienia podczas asynchronicznych operacji wiązania.

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>Parametry

*dwSize*<br/>
Łączna ilość danych (w bajtach) dostępnych od początku powiązania. Może być równa zero, co oznacza, że ilość danych nie jest istotna dla operacji lub że żadna określona kwota nie stanie się dostępna.

*bscfFlag*<br/>
Wartość wyliczenia BSCF. Może mieć jedną lub więcej z następujących wartości:

- BSCF_FIRSTDATANOTIFICATION identyfikuje pierwsze wywołanie `OnDataAvailable` dla danej operacji wiązania.

- BSCF_INTERMEDIATEDATANOTIFICATION identyfikuje pośredniego wywołania `OnDataAvailable` dla operacji wiązania.

- BSCF_LASTDATANOTIFICATION identyfikuje ostatnie wywołanie `OnDataAvailable` dla operacji wiązania.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji nic nie robi. Zobacz Poniższy przykład dla przykładowej implementacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

## <a name="casyncmonikerfileonlowresource"></a><a name="onlowresource"></a> CAsyncMonikerFile::OnLowResource

Wywoływane przez moniker, gdy zasoby są niskie.

```
virtual void OnLowResource();
```

### <a name="remarks"></a>Uwagi

Domyślne wywołania implementacji `GetBinding( )-> Abort( )` .

## <a name="casyncmonikerfileonprogress"></a><a name="onprogress"></a> CAsyncMonikerFile:: OnProgress

Wielokrotnie wywoływane przez moniker, aby wskazać bieżący postęp tej operacji wiązania, zwykle w rozsądnych odstępach czasu podczas długotrwałej operacji.

```
virtual void OnProgress(
    ULONG ulProgress,
    ULONG ulProgressMax,
    ULONG ulStatusCode,
    LPCTSTR szStatusText);
```

### <a name="parameters"></a>Parametry

*ulProgress*<br/>
Wskazuje bieżący postęp operacji wiązania względem oczekiwanej wartości maksymalnej wskazanej w *ulProgressMax*.

*ulProgressMax*<br/>
Wskazuje oczekiwaną maksymalną wartość *ulProgress* dla czasu trwania wywołań `OnProgress` dla tej operacji.

*ulStatusCode*<br/>
Zawiera dodatkowe informacje dotyczące postępu operacji wiązania. Prawidłowe wartości są pobierane z `BINDSTATUS` wyliczenia. Zobacz uwagi dotyczące możliwych wartości.

*szStatusText*<br/>
Informacje o bieżącym postępie, w zależności od wartości *ulStatusCode*. Zobacz uwagi dotyczące możliwych wartości.

### <a name="remarks"></a>Uwagi

Możliwe wartości dla *ulStatusCode* (i *szStatusText* dla każdej wartości) są następujące:

| Wartość | Opis |
|--|--|
| BINDSTATUS_FINDINGRESOURCE | Operacja powiązania polega na znalezieniu zasobu, z którym jest powiązany obiekt lub magazyn. *SzStatusText* zawiera nazwę wyświetlaną przeszukiwanego zasobu (na przykład "www.Microsoft.com"). |
| BINDSTATUS_CONNECTING | Operacja powiązania nawiązuje połączenie z zasobem, z którym jest powiązany obiekt lub magazyn. *SzStatusText* zawiera nazwę wyświetlaną zasobu, z którym jest połączony (na przykład adres IP). |
| BINDSTATUS_SENDINGREQUEST | Operacja bind żąda obiektu lub magazynu, z którym jest powiązany. *SzStatusText* zawiera nazwę wyświetlaną obiektu (na przykład nazwę pliku). |
| BINDSTATUS_REDIRECTING | Operacja powiązania została przekierowana do innej lokalizacji danych. *SzStatusText* zawiera nazwę wyświetlaną nowej lokalizacji danych. |
| BINDSTATUS_USINGCACHEDCOPY | Operacja bind pobiera żądany obiekt lub magazyn z kopii w pamięci podręcznej. *SzStatusText* ma wartość null. |
| BINDSTATUS_BEGINDOWNLOADDATA | Operacja powiązania rozpoczęła Pobieranie obiektu lub magazynu, z którym jest powiązana. *SzStatusText* zawiera nazwę wyświetlaną lokalizacji danych. |
| BINDSTATUS_DOWNLOADINGDATA | Operacja powiązania nadal odbiera obiekt lub magazyn, z którym jest powiązany. *SzStatusText* zawiera nazwę wyświetlaną lokalizacji danych. |
| BINDSTATUS_ENDDOWNLOADDATA | Operacja powiązania zakończyła Pobieranie obiektu lub magazynu, z którym jest powiązany. *SzStatusText* zawiera nazwę wyświetlaną lokalizacji danych. |
| BINDSTATUS_CLASSIDAVAILABLE | Wystąpienie obiektu, z którym jest powiązane, ma tylko zostać utworzone. *SzStatusText* zawiera identyfikator CLSID nowego obiektu w formacie ciągu, dzięki czemu klient może anulować operację powiązania, w razie potrzeby. |

## <a name="casyncmonikerfileonstartbinding"></a><a name="onstartbinding"></a> CAsyncMonikerFile:: OnStartBinding

Przesłoń tę funkcję w klasach pochodnych, aby wykonać akcje po uruchomieniu powiązania.

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana z powrotem przez moniker. Domyślna implementacja nie robi nic.

## <a name="casyncmonikerfileonstopbinding"></a><a name="onstopbinding"></a> CAsyncMonikerFile:: OnStopBinding

Wywoływane przez moniker na końcu operacji wiązania.

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>Parametry

*wynik*<br/>
Wartość HRESULT, która jest wartością błędu lub ostrzeżenia.

*szErrort*<br/>
Ciąg znaków opisujący błąd.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję, aby wykonać akcje, gdy transfer zostanie zatrzymany. Domyślnie wersje funkcji `IBinding` .

Opis `IBinding` interfejsu można znaleźć w Windows SDK.

## <a name="casyncmonikerfileopen"></a><a name="open"></a> CAsyncMonikerFile:: Open

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
Wskaźnik do pliku, który ma zostać otwarty asynchronicznie. Może to być dowolny prawidłowy adres URL lub nazwa pliku.

*pError*<br/>
Wskaźnik do wyjątków plików. W przypadku błędu zostanie ona ustawiona na przyczynę.

*pMoniker*<br/>
Wskaźnik do asynchronicznego interfejsu monikera `IMoniker` , precyzyjne moniker, który jest kombinacją własnego monikera dokumentu, który można pobrać z `IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)` i moniker utworzony na podstawie nazwy ścieżki. Kontrolka może użyć tej monikera do powiązania, ale nie jest to moniker, który powinien zostać zapisany w formancie.

*pBindHost*<br/>
Wskaźnik do `IBindHost` interfejsu, który zostanie użyty do utworzenia monikera z potencjalnie względnej nazwy ścieżki. Jeśli host BIND jest nieprawidłowy lub nie zawiera monikera, wywołanie jest domyślnie `Open(lpszFileName,pError)` . Opis `IBindHost` interfejsu można znaleźć w Windows SDK.

*pServiceProvider*<br/>
Wskaźnik do `IServiceProvider` interfejsu. Jeśli Dostawca usługi jest nieprawidłowy lub nie powiodło się dostarczenie usługi dla `IBindHost` , wywołanie jest domyślnie `Open(lpszFileName,pError)` .

*pUnknown*<br/>
Wskaźnik do `IUnknown` interfejsu. Jeśli `IServiceProvider` zostanie znaleziony, funkcja wysyła zapytanie do `IBindHost` . Jeśli Dostawca usługi jest nieprawidłowy lub nie powiodło się dostarczenie usługi dla `IBindHost` , wywołanie jest domyślnie `Open(lpszFileName,pError)` .

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli plik zostanie otwarty pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

To wywołanie inicjuje proces powiązania.

Możesz użyć adresu URL lub nazwy pliku dla parametru *lpszURL* . Na przykład:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\- oraz

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CMonikerFile](../../mfc/reference/cmonikerfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CMonikerFile](../../mfc/reference/cmonikerfile-class.md)<br/>
[Klasa CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)
