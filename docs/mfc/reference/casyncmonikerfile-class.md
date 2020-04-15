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
ms.openlocfilehash: 57ab463445f249b4e9393f19af103b7588962d5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376995"
---
# <a name="casyncmonikerfile-class"></a>Klasa CAsyncMonikerFile

Zapewnia funkcje do korzystania z monikerów asynchronicznych w formantach ActiveX (dawniej formanty OLE).

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
|[CAsyncMonikerFile::Zamknij](#close)|Zamyka i zwalnia wszystkie zasoby.|
|[Plik CAsyncMoniker::GetBinding](#getbinding)|Pobiera wskaźnik do powiązania transferu asynchroniiowego.|
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|Pobiera format danych w strumieniu.|
|[CAsyncMonikerFile::Otwórz](#open)|Otwiera plik asynchronicznie.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|Tworzy obiekt COM, `IBindStatusCallback`który implementuje .|
|[Plik CAsyncMoniker::GetBindInfo](#getbindinfo)|Wywoływana przez bibliotekę systemu OLE do żądania informacji o typie powiązania, który ma zostać utworzony.|
|[CAsyncMonikerFile::GetPriority](#getpriority)|Wywoływane przez bibliotekę systemu OLE, aby uzyskać priorytet powiązania.|
|[CAsyncMonikerFile::OnDataDostępne](#ondataavailable)|Wywoływane w celu dostarczenia danych, gdy staje się dostępny dla klienta podczas operacji wiązania asynchronizowego.|
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|Wywoływane, gdy zasoby są niskie.|
|[CAsyncMonikerFile::OnProgress](#onprogress)|Wywoływana w celu wskazania postępu procesu pobierania danych.|
|[Plik CAsyncMoniker::OnStartBinding](#onstartbinding)|Wywoływane, gdy uruchamianie powiązania.|
|[Plik CAsyncMoniker::OnStopBinding](#onstopbinding)|Wywoływana, gdy transfer asynchroniczne jest zatrzymany.|

## <a name="remarks"></a>Uwagi

Pochodzi z [CMonikerFile](../../mfc/reference/cmonikerfile-class.md), który z kolei pochodzi z `CAsyncMonikerFile` [COleStreamFile](../../mfc/reference/colestreamfile-class.md), używa interfejsu [IMoniker,](/windows/win32/api/objidl/nn-objidl-imoniker) aby uzyskać dostęp do dowolnego strumienia danych asynchronicznie, w tym ładowania plików asynchronicznie z adresu URL. Pliki mogą być właściwościami ścieżki danych formantów ActiveX.

Monikery asynchroniczne są używane głównie w aplikacjach z dostępem do Internetu i formantach ActiveX, aby zapewnić responsywny interfejs użytkownika podczas przesyłania plików. Najlepszym tego przykładem jest użycie [właściwości CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) w celu zapewnienia właściwości asynchronicznych dla formantów ActiveX. Obiekt `CDataPathProperty` będzie wielokrotnie uzyskać wywołania zwrotnego, aby wskazać dostępność nowych danych podczas długiego procesu wymiany właściwości.

Aby uzyskać więcej informacji na temat używania monikerów asynchronicznych i formantów ActiveX w aplikacjach internetowych, zobacz następujące artykuły:

- [Pierwsze kroki internetowe: Asynchroniczne Monikers](../../mfc/asynchronous-monikers-on-the-internet.md)

- [Pierwsze kroki w Internecie: Formanty ActiveX](../../mfc/activex-controls-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cfile](../../mfc/reference/cfile-class.md)

[Colestreamfile](../../mfc/reference/colestreamfile-class.md)

[Plik CMoniker](../../mfc/reference/cmonikerfile-class.md)

`CAsyncMonikerFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

## <a name="casyncmonikerfilecasyncmonikerfile"></a><a name="casyncmonikerfile"></a>CAsyncMonikerFile::CAsyncMonikerFile

Konstruuje `CAsyncMonikerFile` obiekt.

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>Uwagi

Nie tworzy `IBindHost` interfejsu. `IBindHost`jest używany tylko wtedy, `Open` gdy podasz go w funkcji elementu członkowskiego.

Opis `IBindHost` interfejsu można znaleźć w zestaw Windows SDK.

## <a name="casyncmonikerfileclose"></a><a name="close"></a>CAsyncMonikerFile::Zamknij

Wywołanie tej funkcji, aby zamknąć i zwolnić wszystkie zasoby.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Można wywołać na nieotwartych lub już zamkniętych plikach.

## <a name="casyncmonikerfilecreatebindstatuscallback"></a><a name="createbindstatuscallback"></a>CAsyncMonikerFile::CreateBindStatusCallback

Tworzy obiekt COM, `IBindStatusCallback`który implementuje .

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>Parametry

*pUnkKontrolowanie*<br/>
Wskaźnik do kontroli nieznany (zewnętrzne) `IUnknown`lub NULL, jeśli agregacja nie jest używany.

### <a name="return-value"></a>Wartość zwracana

Jeśli *pUnkControlling* nie jest null, funkcja zwraca `IUnknown` wskaźnik do wewnętrznego `IBindStatusCallback`na nowy obiekt COM obsługujących . Jeśli `pUnkControlling` ma wartość NULL, funkcja `IUnknown` zwraca wskaźnik do nowego `IBindStatusCallback`obiektu COM obsługującego .

### <a name="remarks"></a>Uwagi

`CAsyncMonikerFile`wymaga obiektu COM, `IBindStatusCallback`który implementuje . MFC implementuje taki obiekt i jest agregowalne. Można `CreateBindStatusCallback` zastąpić, aby zwrócić własny obiekt COM. Obiekt COM można agregować implementacji `CreateBindStatusCallback` MFC przez wywołanie z kontrolowaniem nieznany obiektu COM. Obiekty COM zaimplementowane przy użyciu `CCmdTarget` obsługi `CCmdTarget::GetControllingUnknown`COM mogą pobierać kontrolowanie nieznane za pomocą .

Alternatywnie obiekt COM może delegować do implementacji MFC, wywołując . `CreateBindStatusCallback( NULL )`

[CAsyncMonikerFile::Otwórz](#open) `CreateBindStatusCallback`połączenia .

Aby uzyskać więcej informacji na temat monikerów asynchronicznych i wiązania asynchronicznie, zobacz interfejs [IBindStatusCallback](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775060\(v=vs.85\)) i [jak działa asynchroniczne powiązanie i magazynowanie.](/windows/win32/Stg/how-asynchronous-binding-and-storage-work) Aby zapoznać się z omówieniem agregacji, zobacz [Agregacja](/windows/win32/com/aggregation). Wszystkie trzy tematy znajdują się w sdk systemu Windows.

## <a name="casyncmonikerfilegetbindinfo"></a><a name="getbindinfo"></a>Plik CAsyncMoniker::GetBindInfo

Wywoływana od klienta asynchroniiowego monikera, aby poinformować asynchroniką, jak chce się powiązać.

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>Wartość zwracana

Pobiera ustawienia dla `IBindStatusCallBack`. Opis `IBindStatusCallback` interfejsu można znaleźć w zestaw Windows SDK.

### <a name="remarks"></a>Uwagi

Domyślna implementacja ustawia powiązanie jako asynchroniczne, aby użyć nośnika magazynu (strumienia) i użyć modelu wypychania danych. Zastądnie tej funkcji, jeśli chcesz zmienić zachowanie powiązania.

Jednym z powodów, dla tego byłoby powiązanie przy użyciu modelu ściągania danych zamiast modelu wypychania danych. W modelu ściągania danych klient kieruje operacją powiązania, a moniker udostępnia dane tylko klientowi po jego odczytie. W modelu wypychania danych moniker napędza operację wiązania asynchronicznego i stale powiadamia klienta, gdy dostępne są nowe dane.

## <a name="casyncmonikerfilegetbinding"></a><a name="getbinding"></a>Plik CAsyncMoniker::GetBinding

Wywołanie tej funkcji, aby pobrać wskaźnik do powiązania transferu asynchroniiowego.

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `IBinding` interfejsu pod warunkiem, gdy rozpoczyna się transfer asynchroniczne. Zwraca wartość NULL, jeśli z jakiegokolwiek powodu nie można dokonać transferu asynchronicznie.

### <a name="remarks"></a>Uwagi

Pozwala to kontrolować proces transferu danych `IBinding` za pośrednictwem interfejsu, `IBinding::Pause`na `IBinding::Resume`przykład za pomocą `IBinding::Abort`, i .

Opis `IBinding` interfejsu można znaleźć w zestaw Windows SDK.

## <a name="casyncmonikerfilegetformatetc"></a><a name="getformatetc"></a>CAsyncMonikerFile::GetFormatEtc

Wywołanie tej funkcji, aby pobrać format danych w strumieniu.

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do struktury systemu Windows [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dla aktualnie otwartego strumienia. Zwraca wartość NULL, jeśli moniker nie został powiązany, jeśli nie jest asynchroniczną lub jeśli operacja asynchroniczną nie została rozpoczęta.

## <a name="casyncmonikerfilegetpriority"></a><a name="getpriority"></a>CAsyncMonikerFile::GetPriority

Wywoływane od klienta asynchroniczną moniker jako proces wiązania zaczyna odbierać priorytet nadany wątku dla operacji wiązania.

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>Wartość zwracana

Priorytet, w którym odbędzie się transfer asynchroniczne. Jedna ze standardowych flag priorytetu wątku: THREAD_PRIORITY_ABOVE_NORMAL, THREAD_PRIORITY_BELOW_NORMAL, THREAD_PRIORITY_HIGHEST, THREAD_PRIORITY_IDLE, THREAD_PRIORITY_LOWEST, THREAD_PRIORITY_NORMAL i THREAD_PRIORITY_TIME_CRITICAL. Opis tych wartości można znaleźć w funkcji Windows [SetThreadPriority.](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority)

### <a name="remarks"></a>Uwagi

`GetPriority`nie należy wywoływać bezpośrednio. THREAD_PRIORITY_NORMAL jest zwracany przez domyślną implementację.

## <a name="casyncmonikerfileondataavailable"></a><a name="ondataavailable"></a>CAsyncMonikerFile::OnDataDostępne

Asynchronialny moniker `OnDataAvailable` wywołania, aby zapewnić dane do klienta, gdy staje się dostępny, podczas operacji wiązania asynchroniiowego.

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>Parametry

*dwSize (rozmiar)*<br/>
Skumulowana kwota (w bajtach) danych dostępnych od początku powiązania. Może być równa zeru, co oznacza, że ilość danych nie jest istotna dla operacji lub że nie udostępnino żadnej określonej kwoty.

*bscfFlag*<br/>
Wartość wyliczenia BSCF. Może być jedną lub kilkoma z następujących wartości:

- BSCF_FIRSTDATANOTIFICATION Identyfikuje pierwsze wywołanie `OnDataAvailable` dla danej operacji wiązania.

- BSCF_INTERMEDIATEDATANOTIFICATION Identyfikuje wywołanie pośrednie `OnDataAvailable` dla operacji powiązania.

- BSCF_LASTDATANOTIFICATION Identyfikuje ostatnie wywołanie `OnDataAvailable` operacji powiązania.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji nic nie robi. Zobacz poniższy przykład dla implementacji przykładowej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

## <a name="casyncmonikerfileonlowresource"></a><a name="onlowresource"></a>CAsyncMonikerFile::OnLowResource

Wywoływany przez moniker, gdy zasoby są niskie.

```
virtual void OnLowResource();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołuje `GetBinding( )-> Abort( )`.

## <a name="casyncmonikerfileonprogress"></a><a name="onprogress"></a>CAsyncMonikerFile::OnProgress

Wywoływane przez moniker wielokrotnie, aby wskazać bieżący postęp tej operacji wiązania, zazwyczaj w rozsądnych odstępach czasu podczas długiej operacji.

```
virtual void OnProgress(
    ULONG ulProgress,
    ULONG ulProgressMax,
    ULONG ulStatusCode,
    LPCTSTR szStatusText);
```

### <a name="parameters"></a>Parametry

*ulProgress*<br/>
Wskazuje bieżący postęp operacji wiązania względem oczekiwanej maksymalnej wskazanej w *ulProgressMax*.

*ulProgressMax*<br/>
Wskazuje oczekiwaną maksymalną wartość *ulProgress* na `OnProgress` czas trwania wywołań dla tej operacji.

*ulStatusCode (kod ulStatusCode)*<br/>
Zawiera dodatkowe informacje dotyczące postępu operacji wiązania. Prawidłowe wartości są `BINDSTATUS` pobierane z wyliczenia. Zobacz Uwagi dotyczące możliwych wartości.

*szStatusText (Tekst szStatus)*<br/>
Informacje o bieżącym postępie, w zależności od wartości *ulStatusCode*. Zobacz Uwagi dotyczące możliwych wartości.

### <a name="remarks"></a>Uwagi

Możliwe wartości *dla ulStatusCode* (i *szStatusText* dla każdej wartości) to:

|||
|-|-|
|BINDSTATUS_FINDINGRESOURCE  |Operacja powiązania jest znalezienie zasobu, który przechowuje obiekt lub magazyn jest powiązany z. *SzStatusText* zawiera nazwę wyświetlaną wyszukiwanego zasobu (na przykład "www.microsoft.com").  |
|BINDSTATUS_CONNECTING  |Operacja powiązania łączy się z zasobem, z którego powiązany jest obiekt lub magazyn. *SzStatusText* zawiera wyświetlaną nazwę zasobu, z którego jest nawiązywane (na przykład adres IP).  |
|BINDSTATUS_SENDINGREQUEST|Operacja powiązania jest żądanie obiektu lub magazynu jest powiązany z. *SzStatusText* zawiera wyświetlaną nazwę obiektu (na przykład nazwę pliku).|
|BINDSTATUS_REDIRECTING  |Operacja powiązania została przekierowana do innej lokalizacji danych. *SzStatusText* zawiera nazwę wyświetlaną nowej lokalizacji danych.  |
|BINDSTATUS_USINGCACHEDCOPY  |Operacja powiązania pobiera żądany obiekt lub magazyn z kopii buforowanej. *SzStatusText* ma wartość NULL.  |
|BINDSTATUS_BEGINDOWNLOADDATA  |Operacja powiązania rozpoczęła odbieranie obiektu lub magazynu jest powiązany z. *SzStatusText* zawiera wyświetlaną nazwę lokalizacji danych.|
|BINDSTATUS_DOWNLOADINGDATA  |Operacja powiązania kontynuuje odbieranie obiektu lub magazynu jest powiązany z. *SzStatusText* zawiera wyświetlaną nazwę lokalizacji danych.  |
|BINDSTATUS_ENDDOWNLOADDATA  |Operacja wiązania zakończyła odbieranie obiektu lub magazynu jest powiązany z. *SzStatusText* zawiera wyświetlaną nazwę lokalizacji danych.  |
|BINDSTATUS_CLASSIDAVAILABLE  |Wystąpienie obiektu, do który jest powiązany, ma zostać utworzony. *SzStatusText* udostępnia CLSID nowego obiektu w formacie ciągu, dzięki czemu klient możliwość anulowania operacji wiązania, w razie potrzeby.  |

## <a name="casyncmonikerfileonstartbinding"></a><a name="onstartbinding"></a>Plik CAsyncMoniker::OnStartBinding

Zastąpić tę funkcję w klasach pochodnych do wykonywania akcji podczas uruchamiania powiązania.

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana przez moniker. Domyślna implementacja nic nie robi.

## <a name="casyncmonikerfileonstopbinding"></a><a name="onstopbinding"></a>Plik CAsyncMoniker::OnStopBinding

Wywoływana przez moniker na końcu operacji wiązania.

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>Parametry

*Hresult*<br/>
HRESULT, który jest wartością błędu lub ostrzeżenia.

*SzErrort (szerrort)*<br/>
Ciąg znaków opisujący błąd.

### <a name="remarks"></a>Uwagi

Zastąd w tej funkcji należy wykonywać akcje po zatrzymaniu transferu. Domyślnie funkcja zwalnia `IBinding`.

Opis `IBinding` interfejsu można znaleźć w zestaw Windows SDK.

## <a name="casyncmonikerfileopen"></a><a name="open"></a>CAsyncMonikerFile::Otwórz

Wywołanie tej funkcji elementu członkowskiego, aby otworzyć plik asynchronicznie.

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
Wskaźnik do pliku, który ma być otwierany asynchronicznie. Plik może być dowolny prawidłowy adres URL lub nazwa pliku.

*Perror*<br/>
Wskaźnik do wyjątków pliku. W przypadku wystąpienia błędu zostanie on ustawiony na przyczynę.

*pMoniker (własnik pmoniker)*<br/>
Wskaźnik do interfejsu `IMoniker`asynchroniiowego monikera , precyzyjny moniker, który jest kombinacją własnego monikera dokumentu, który można pobrać za pomocą `IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)`programu , oraz moniker utworzony na podstawie nazwy ścieżki. Formant może używać tego monikera do powiązania, ale nie jest to moniker, który formant powinien zapisać.

*pBindHost (pBindHost)*<br/>
Wskaźnik do `IBindHost` interfejsu, który będzie używany do tworzenia monikera z potencjalnie względnej nazwy ścieżki. Jeśli host wiązania jest nieprawidłowy lub nie udostępnia monikera, wywołanie jest domyślnie wywoływane `Open(lpszFileName,pError)`. Opis `IBindHost` interfejsu można znaleźć w zestaw Windows SDK.

*pServiceProvider*<br/>
Wskaźnik do `IServiceProvider` interfejsu. Jeśli usługodawca jest nieprawidłowy lub nie `IBindHost`może świadczyć `Open(lpszFileName,pError)`usługi, wywołanie jest domyślne na .

*pNiezna*<br/>
Wskaźnik do `IUnknown` interfejsu. Jeśli `IServiceProvider` zostanie znaleziony, funkcja `IBindHost`kwerendy dla . Jeśli usługodawca jest nieprawidłowy lub nie `IBindHost`może świadczyć `Open(lpszFileName,pError)`usługi, wywołanie jest domyślne na .

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli plik został pomyślnie otwarty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

To wywołanie inicjuje proces wiązania.

Można użyć adresu URL lub nazwy pliku dla parametru *lpszURL.* Przykład:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\-lub -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CMonikerFile](../../mfc/reference/cmonikerfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CMonikerFile](../../mfc/reference/cmonikerfile-class.md)<br/>
[Klasa CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)
