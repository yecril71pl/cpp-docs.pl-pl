---
title: CInternetSession Class
ms.date: 06/20/2018
f1_keywords:
- CInternetSession
- AFXINET/CInternetSession
- AFXINET/CInternetSession::CInternetSession
- AFXINET/CInternetSession::Close
- AFXINET/CInternetSession::EnableStatusCallback
- AFXINET/CInternetSession::GetContext
- AFXINET/CInternetSession::GetCookie
- AFXINET/CInternetSession::GetCookieLength
- AFXINET/CInternetSession::GetFtpConnection
- AFXINET/CInternetSession::GetGopherConnection
- AFXINET/CInternetSession::GetHttpConnection
- AFXINET/CInternetSession::OnStatusCallback
- AFXINET/CInternetSession::OpenURL
- AFXINET/CInternetSession::SetCookie
- AFXINET/CInternetSession::SetOption
helpviewer_keywords:
- CInternetSession [MFC], CInternetSession
- CInternetSession [MFC], Close
- CInternetSession [MFC], EnableStatusCallback
- CInternetSession [MFC], GetContext
- CInternetSession [MFC], GetCookie
- CInternetSession [MFC], GetCookieLength
- CInternetSession [MFC], GetFtpConnection
- CInternetSession [MFC], GetGopherConnection
- CInternetSession [MFC], GetHttpConnection
- CInternetSession [MFC], OnStatusCallback
- CInternetSession [MFC], OpenURL
- CInternetSession [MFC], SetCookie
- CInternetSession [MFC], SetOption
ms.assetid: ef54feb4-9d0f-4e65-a45d-7a4cf6c40e51
ms.openlocfilehash: 5ad1a1a0dde32358828d58a8f237337c4f62f3e5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261300"
---
# <a name="cinternetsession-class"></a>CInternetSession Class

Tworzy i inicjuje jedną lub kilka jednoczesnych sesji internetowej, a jeśli to konieczne, opisuje Twoje połączenie serwera proxy.

## <a name="syntax"></a>Składnia

```cpp
class CInternetSession : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInternetSession::CInternetSession](#cinternetsession)|Konstruuje `CInternetSession` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInternetSession::Close](#close)|Zamyka połączenie z Internetem podczas sesji internetowej zostanie zakończony.|
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|Ustanawia procedura wywołania zwrotnego stanu.|
|[CInternetSession::GetContext](#getcontext)|Zamyka połączenie z Internetem podczas sesji internetowej zostanie zakończony.|
|[CInternetSession::GetCookie](#getcookie)|Zwraca plików cookie dla określonego adresu URL i jego obiektu nadrzędnego adresów URL.|
|[CInternetSession::GetCookieLength](#getcookielength)|Pobiera zmienną określającą długość pliku cookie przechowywane w buforze.|
|[CInternetSession::GetFtpConnection](#getftpconnection)|Otwiera sesję FTP z serwerem. Loguje się użytkownik.|
|[CInternetSession::GetGopherConnection](#getgopherconnection)|Zostanie otwarty dla aplikacji, która próbuje otworzyć połączenie z serwera gopher.|
|[CInternetSession::GetHttpConnection](#gethttpconnection)|Zostanie otwarty z serwerem HTTP dla aplikacji, która próbuje otworzyć połączenie.|
|[CInternetSession::OnStatusCallback](#onstatuscallback)|Aktualizuje stan operacji, gdy wywołanie zwrotne dla stanu jest włączone.|
|[CInternetSession::OpenURL](#openurl)|Analizuje i otwiera adres URL.|
|[CInternetSession::SetCookie](#setcookie)|Ustawia plik cookie dla określonego adresu URL.|
|[CInternetSession::SetOption](#setoption)|Ustawia opcje sesji internetowej.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInternetSession::operator HINTERNET](#operator_hinternet)|Dojście do bieżącej sesji Internet.|

## <a name="remarks"></a>Uwagi

Jeśli połączenie z Internetem muszą być utrzymywane w czasie trwania operacji aplikacji, możesz utworzyć `CInternetSession` składową klasy [CWinApp](../../mfc/reference/cwinapp-class.md).

Po ustanowieniu sesji Internetu, można wywołać [OpenURL](#openurl). `CInternetSession` następnie analizuje adres URL dla Ciebie przez wywołanie funkcji globalnych [afxparseurl —](internet-url-parsing-globals.md#afxparseurl). Niezależnie od jego typu protokołu `CInternetSession` interpretuje adres URL i zarządza nim automatycznie. Może obsługiwać żądania dotyczące plików lokalnych identyfikowane przez zasób adresu URL "file://". `OpenURL` Zwraca wskaźnik do [CStdioFile](../../mfc/reference/cstdiofile-class.md) obiektu, jeśli nazwa przekazywania jest plikiem lokalnym.

Jeśli otworzysz na adres URL na serwerze Internetu za pomocą `OpenURL`, można odczytać informacji z witryny. Jeśli chcesz wykonać akcje specyficzne dla usługi (na przykład HTTP, FTP lub gopher) na pliki znajdujące się na serwerze, należy ustanowić odpowiednie połączenie z tym serwerem. Aby otworzyć określony rodzaj połączenia bezpośrednio do określonej usługi, użyj jednej z następujących funkcji elementów członkowskich:

- [GetGopherConnection](#getgopherconnection) można otworzyć połączenia z usługą gopher.

- [GetHttpConnection](#gethttpconnection) można otworzyć połączenia z usługą HTTP.

- [GetFtpConnection](#getftpconnection) można otworzyć połączenia z usługą FTP.

[SetOption](#setoption) pozwala ustawić opcje kwerendy sesji, takie jak wartości limitu czasu, liczbę ponownych prób i tak dalej.

`CInternetSession` Funkcje Członkowskie [SetCookie](#setcookie), [GetCookie](#getcookie), i [GetCookieLength](#getcookielength) zapewniają środki do zarządzania bazą danych pliku cookie Win32, za pomocą których obsługa serwerów i skrypty informacje o stanie dotyczących stacji roboczej użytkownika.

Aby uzyskać więcej informacji na temat podstawowe zadania programowania Internet, zobacz artykuł [Internet pierwsze kroki: WinInet](../../mfc/wininet-basics.md). Aby uzyskać ogólne informacje dotyczące używania klas MFC WinInet, zobacz artykuł [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md).

> [!NOTE]
> `CInternetSession` zgłosi [afxthrownotsupportedexception —](exception-processing.md#afxthrownotsupportedexception) dla typów nieobsługiwana usługa. Obecnie obsługiwane są tylko następujące typy usługi: FTP, HTTP, gopher i plików.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`CInternetSession`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

## <a name="cinternetsession"></a> CInternetSession::CInternetSession

Ta funkcja członkowska jest wywoływana, gdy `CInternetSession` obiekt zostanie utworzony.

```cpp
CInternetSession(
    LPCTSTR pstrAgent = NULL,
    DWORD_PTR dwContext = 1,
    DWORD dwAccessType = PRE_CONFIG_INTERNET_ACCESS,
    LPCTSTR pstrProxyName = NULL,
    LPCTSTR pstrProxyBypass = NULL,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parametry

*pstrAgent*<br/>
Wskaźnik do ciągu, który identyfikuje nazwę aplikacji lub jednostki wywoływanie funkcji Internet (na przykład "Microsoft przeglądarki internetowej"). Jeśli *pstrAgent* ma wartość NULL (ustawienie domyślne), struktura wywołuje funkcja globalna [afxgetappname —](application-information-and-management.md#afxgetappname), która zwraca ciąg zakończony wartością null zawierający nazwę aplikacji. Niektóre protokoły Użyj tych parametrów do identyfikowania Twojej aplikacji na serwerze.

*dwContext*<br/>
Identyfikator kontekstu dla tej operacji. *dwContext* określa informacje o stanie operacji zwrócony przez [CInternetSession::OnStatusCallback](#onstatuscallback). Wartość domyślna jest ustawiona na 1; Jednakże można jawnie przypisać identyfikator kontekstu określonego dla operacji. Obiekt i wszelkie prace, które wykonuje zostanie skojarzona z tym identyfikatorem kontekstu.

*dwAccessType*<br/>
Typ dostępu do uprawnień wymaganych. Poniżej przedstawiono prawidłowe wartości, mogą być dostarczane dokładnie jeden z nich:

- Połącz INTERNET_OPEN_TYPE_PRECONFIG przy użyciu wstępnie skonfigurowanych ustawień w rejestrze. Ten typ dostępu jest ustawiony jako domyślny. Aby połączyć za pośrednictwem serwera proxy na tym, należy ustawić *dwAccessType* na tę wartości; następnie ustawiamy rejestru odpowiednio.

- INTERNET_OPEN_TYPE_DIRECT łączyć się bezpośrednio z Internetu.

- INTERNET_OPEN_TYPE_PROXY nawiązać połączenie za pośrednictwem serwera proxy CERN.

Aby uzyskać informacje na temat łączenia się z różnymi typami serwerów proxy, zobacz [kroki w typowej aplikacji klienckiej FTP](../../mfc/steps-in-a-typical-ftp-client-application.md).

*pstrProxyName*<br/>
Nazwa preferowanego serwera proxy CERN Jeśli *dwAccessType* jest ustawiony jako INTERNET_OPEN_TYPE_PROXY. Wartość domyślna to NULL.

*pstrProxyBypass*<br/>
Wskaźnik do ciągu zawierającego opcjonalną listę adresów serwerów. Te adresy mogą pominąć, korzystając z dostępu do serwera proxy. Jeśli podano wartość NULL, Lista pomijania będzie można odczytać z rejestru. Ten parametr ma znaczenie tylko wtedy, gdy *dwAccessType* jest ustawiona na INTERNET_OPEN_TYPE_PROXY.

*dwFlags*<br/>
Określa różne opcje pamięci podręcznej. Wartość domyślna jest równa 0. Możliwe wartości:

- INTERNET_FLAG_DONT_CACHE nie buforują dane, lokalnie lub w dowolne serwery bramy.

- Pobierz INTERNET_FLAG_OFFLINE operacje są spełnione przez trwałej pamięci podręcznej tylko. Jeśli element nie istnieje w pamięci podręcznej, zwracany jest kod odpowiedni komunikat o błędzie. Ta flaga mogą być łączone za pomocą operatora testu koniunkcji **lub** ( **&#124;**) — operator.

### <a name="remarks"></a>Uwagi

`CInternetSession` Pierwsza funkcja Internet jest wywoływane przez aplikację. Inicjuje struktur danych wewnętrznych się i przygotowuje przyszłych wywołań z aplikacji.

Jeśli brak połączenia z Internetem mogą być otwierane, `CInternetSession` zgłasza [afxthrowinternetexception —](internet-url-parsing-globals.md#afxthrowinternetexception).

### <a name="example"></a>Przykład

Zobacz przykład [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="close"></a>  CInternetSession::Close

Wywołaj tę funkcję, elementu członkowskiego, gdy Twoja aplikacja zakończy `CInternetSession` obiektu.

```cpp
virtual void Close();
```

### <a name="example"></a>Przykład

Zobacz przykład [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="enablestatuscallback"></a>  CInternetSession::EnableStatusCallback

Wywołaj tę funkcję elementu członkowskiego, aby włączyć stan wywołania zwrotnego.

```cpp
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bWłączenie*<br/>
Określa, czy wywołanie zwrotne jest włączone. Wartość domyślna to TRUE.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. Jeśli wywołanie zakończy się niepowodzeniem, należy określić przyczynę niepowodzenia, sprawdzając zgłoszony [CInternetException](../../mfc/reference/cinternetexception-class.md) obiektu.

### <a name="remarks"></a>Uwagi

Podczas obsługi wywołanie zwrotne dla stanu, możesz podać stan o postępie operacji (takie jak rozpoznawania nazwy, nawiązywania połączenia z serwerem i tak dalej), na pasku stanu aplikacji. Wyświetlanie stanu operacji jest szczególnie pożądane podczas operacji długoterminowego.

Ponieważ wywołania zwrotne pojawia się podczas przetwarzania żądania, aplikacji powinni spędzać jako trochę czasu, jak to możliwe, podczas wywołania zwrotnego, aby zapobiec degradacji przepływność danych w sieci. Na przykład umieszczenie okno dialogowe, w wywołaniu zwrotnym może być taki długotrwałej operacji serwera kończy się żądanie.

Nie można usunąć stanu wywołania zwrotnego, tak długo, jak długo trwa żadnych wywołań zwrotnych.

Aby obsłużyć dowolne operacje asynchroniczne, możesz utworzyć własne wątku lub użyć funkcji interfejsu WinInet bez MFC.

## <a name="getcontext"></a>  CInternetSession::GetContext

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wartość kontekstu sesji określonej aplikacji.

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Wartość zwracana

Zdefiniowane przez aplikację kontekst identyfikatora.

### <a name="remarks"></a>Uwagi

[Onstatuscallback —](#onstatuscallback) używa identyfikator kontekstu zwrócony przez `GetContext` zgłoszenia stanu określonej aplikacji. Na przykład gdy użytkownik aktywuje żądania internetowego, który obejmuje zwracania informacji o stanie, wywołanie zwrotne stanu używa identyfikator kontekstu, aby zgłosić stan dla tego konkretnego żądania. Jeśli użytkownik aktywuje dwa oddzielne żądania internetowe zarówno obejmują zwracania informacji o stanie, `OnStatusCallback` używa identyfikatorów kontekstu, zostać zwrócony stan o ich odpowiednie żądania. W związku z tym identyfikator kontekstu jest używana dla wszystkich operacji wywołania zwrotnego stanu i jest on skojarzony z sesji do czasu, sesja zostanie zakończona.

Aby uzyskać więcej informacji na temat operacji asynchronicznych, zobacz artykuł [Internet pierwsze kroki: WinInet](../../mfc/wininet-basics.md).

## <a name="getcookie"></a>  CInternetSession::GetCookie

Ta funkcja elementu członkowskiego implementuje zachowanie funkcji Win32 [InternetGetCookie](/windows/desktop/api/wininet/nf-wininet-internetgetcookiea), zgodnie z opisem w zestawie Windows SDK.

```cpp
static BOOL GetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPTSTR pstrCookieData,
    DWORD dwBufLen);

static BOOL GetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    CString& strCookieData);
```

### <a name="parameters"></a>Parametry

*pstrUrl*<br/>
Wskaźnik do ciągu zawierającego adres URL.

*pstrCookieName*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku cookie można uzyskać pod określony adres URL.

*pstrCookieData*<br/>
W pierwszym przeciążenia wskaźnik do ciągu zawierającego adres buforu, który otrzymuje dane pliku cookie. Ta wartość może mieć wartości NULL. W drugie przeciążenie odwołanie do [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiekt, aby odbierać dane pliku cookie.

*dwBufLen*<br/>
Zmienna określania rozmiaru *pstrCookieData* buforu. Jeśli funkcja się powiedzie, bufor odbiera ilość danych skopiowanych do *pstrCookieData* buforu. Jeśli *pstrCookieData* ma wartość NULL, ten parametr odbiera wartość, która określa rozmiar buforu, które są niezbędne skopiować dane pliku cookie.

### <a name="return-value"></a>Wartość zwracana

W przeciwnym razie zwraca wartość TRUE, jeśli kończy się pomyślnie, lub FAŁSZ. Jeśli wywołanie zakończy się niepowodzeniem, należy wywołać funkcję Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) w celu ustalenia przyczyny błędu. Stosuje się następujące wartości błędów:

- ERROR_NO_MORE_ITEMS istnieje pliki cookie, nie dla określonego adresu URL i wszystkich jego elementów nadrzędnych.

- ERROR_INSUFFICIENT_BUFFER wartości przekazanej w *dwBufLen* jest za mało skopiować dane pliku cookie. Wartość zwracana w *dwBufLen* jest niezbędne pobrać wszystkie dane rozmiar buforu.

### <a name="remarks"></a>Uwagi

W drugie przeciążenie MFC pobiera dane pliku cookie w podanym `CString` obiektu.

## <a name="getcookielength"></a>  CInternetSession::GetCookieLength

Wywołaj tę funkcję elementu członkowskiego, aby pobrać długość pliku cookie przechowywane w buforze.

```cpp
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName);
```

### <a name="parameters"></a>Parametry

*pstrUrl*<br/>
Wskaźnik do ciągu zawierającego adres URL

*pstrCookieName*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku cookie.

### <a name="return-value"></a>Wartość zwracana

Wartość DWORD wskazujący długość pliku cookie, są przechowywane w buforze. Zero, jeśli pliki cookie nie o nazwie wskazywanym przez *pstrCookieName* istnieje.

### <a name="remarks"></a>Uwagi

Ta wartość jest używana przez [GetCookie](#getcookie).

## <a name="getftpconnection"></a>  CInternetSession::GetFtpConnection

Wywołaj tę funkcję elementu członkowskiego, aby nawiązać połączenie FTP i Uzyskaj wskaźnik do `CFtpConnection` obiektu.

```cpp
CFtpConnection* GetFtpConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    BOOL bPassive = FALSE);
```

### <a name="parameters"></a>Parametry

*pstrServer*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera FTP.

*pstrUserName*<br/>
Wskaźnik na ciąg zakończony znakiem null, określający nazwę użytkownika, aby zalogować się. Jeśli ma wartość NULL, wartość domyślna jest anonimowy.

*pstrPassword*<br/>
Wskaźnik Określa hasło używane do logowania się w ciąg zakończony znakiem null. Jeśli oba *pstrPassword* i *pstrUserName* mają wartość NULL, domyślne hasło anonimowe to nazwa adres e-mail użytkownika. Jeśli *pstrPassword* ma wartość NULL (lub pustego ciągu), ale *pstrUserName* nie ma wartości NULL, puste hasło jest używane. W poniższej tabeli opisano zachowanie cztery ustawienia możliwe *pstrUserName* i *pstrPassword*:

| *pstrUserName*  | *pstrPassword*  | Nazwa użytkownika jest wysyłane do serwera FTP | Hasła przesyłanych do serwera FTP |
|-----------------|-----------------|-----------------------------|-----------------------------|
|   Wartość NULL lub ""   |   Wartość NULL lub ""   |         "anonimowy"         |      Nazwa e-mail użytkownika      |
| Ciąg znaków innych niż NULL |   Wartość NULL lub ""   |       *pstrUserName*        |             " "             |
|      NULL       | Ciąg znaków innych niż NULL |            BŁĄD            |            BŁĄD            |
| Ciąg znaków innych niż NULL | Ciąg znaków innych niż NULL |       *pstrUserName*        |       *pstrPassword*        |

*nPort*<br/>
Liczba, która identyfikuje port TCP/IP używany na serwerze.

*bPassive*<br/>
Określa tryb pasywny lub aktywny dla tej sesji FTP. Jeśli ma wartość TRUE, ustawia Win32 API `dwFlag` do INTERNET_FLAG_PASSIVE.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CFtpConnection](../../mfc/reference/cftpconnection-class.md) obiektu. Jeśli wywołanie zakończy się niepowodzeniem, należy określić przyczynę niepowodzenia, sprawdzając zgłoszony [CInternetException](../../mfc/reference/cinternetexception-class.md) obiektu.

### <a name="remarks"></a>Uwagi

`GetFtpConnection` nawiązanie połączenia z serwerem FTP i tworzy i zwraca wskaźnik do `CFTPConnection` obiektu. Ale nie wykonuje żadnych określonych operacji na serwerze. Jeśli zamierzasz odczytu lub zapisu do plików, na przykład, należy wykonać te operacje jako oddzielne kroki. Zawiera opis klas [CFtpConnection](../../mfc/reference/cftpconnection-class.md) i [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) dla informacji na temat wyszukiwania plików otwierania plików, a odczyt lub zapis do plików. Zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md) dla kroków wykonywania typowych zadań połączenia FTP.

### <a name="example"></a>Przykład

Zobacz przykład [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="getgopherconnection"></a>  CInternetSession::GetGopherConnection

Wywołaj tę funkcję elementu członkowskiego, aby ustanowić nowe połączenia gopher i Uzyskaj wskaźnik do `CGopherConnection` obiektu.

```cpp
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>Parametry

*pstrServer*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera gopher.

*pstrUserName*<br/>
Wskaźnik do ciągu zawierającego nazwę użytkownika.

*pstrPassword*<br/>
Wskaźnik do ciągu zawierającego hasła dostępu.

*nPort*<br/>
Liczba, która identyfikuje port TCP/IP używany na serwerze.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) obiektu. Jeśli wywołanie zakończy się niepowodzeniem, należy określić przyczynę niepowodzenia, sprawdzając zgłoszony [CInternetException](../../mfc/reference/cinternetexception-class.md) obiektu.

### <a name="remarks"></a>Uwagi

`GetGopherConnection` nawiązanie połączenia z serwera gopher i tworzy i zwraca wskaźnik do `CGopherConnection` obiektu. Ale nie wykonuje żadnych określonych operacji na serwerze. Jeśli zamierzasz odczytu lub zapisu danych, na przykład, należy wykonać te operacje jako oddzielne kroki. Zawiera opis klas [CGopherConnection](../../mfc/reference/cgopherconnection-class.md), [CGopherFile](../../mfc/reference/cgopherfile-class.md), i [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) dla informacji na temat wyszukiwania plików otwierania plików, a odczyt lub zapis do plików. Aby dowiedzieć się, jak przeglądanie witryny FTP, zobacz Funkcja elementu członkowskiego [OpenURL](#openurl). Zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md) dla kroków wykonywania typowych zadań połączenia gopher.

## <a name="gethttpconnection"></a>  CInternetSession::GetHttpConnection

Wywołaj tę funkcję elementu członkowskiego, aby nawiązać połączenie HTTP i Uzyskaj wskaźnik do `CHttpConnection` obiektu.

```cpp
CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL);

CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,
    DWORD dwFlags,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL);
```

### <a name="parameters"></a>Parametry

*pstrServer*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera HTTP.

*nPort*<br/>
Liczba, która identyfikuje port TCP/IP używany na serwerze.

*pstrUserName*<br/>
Wskaźnik do ciągu zawierającego nazwę użytkownika.

*pstrPassword*<br/>
Wskaźnik do ciągu zawierającego hasła dostępu.

*dwflags*<br/>
Dowolną kombinację `INTERNET_FLAG_*` flag. Zobacz tabelę w **uwagi** części [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) opis *Flagidw* wartości.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CHttpConnection](../../mfc/reference/chttpconnection-class.md) obiektu. Jeśli wywołanie zakończy się niepowodzeniem, należy określić przyczynę niepowodzenia, sprawdzając zgłoszony [CInternetException](../../mfc/reference/cinternetexception-class.md) obiektu.

### <a name="remarks"></a>Uwagi

`GetHttpConnection` nawiązanie połączenia z serwerem HTTP i tworzy i zwraca wskaźnik do `CHttpConnection` obiektu. Ale nie wykonuje żadnych określonych operacji na serwerze. Jeśli zamierzasz zbadać nagłówka HTTP, na przykład, należy wykonać tej operacji w osobnym kroku. Zawiera opis klas [CHttpConnection](../../mfc/reference/chttpconnection-class.md) i [CHttpFile](../../mfc/reference/chttpfile-class.md) uzyskać informacji o operacjach, można wykonać przy użyciu połączenia z serwerem HTTP. Aby dowiedzieć się, jak przeglądanie witryny HTTP, zobacz Funkcja elementu członkowskiego [OpenURL](#openurl). Zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md) dla kroków wykonywania typowych zadań połączenia HTTP.

## <a name="onstatuscallback"></a>  CInternetSession::OnStatusCallback

Ta funkcja członkowska jest wywoływana przez platformę, aby zaktualizować stan, gdy wywołanie zwrotne dla stanu jest włączone i operacji jest w stanie oczekiwania.

```cpp
virtual void OnStatusCallback(
    DWORD_PTR dwContext,
    DWORD dwInternetStatus,
    LPVOID lpvStatusInformation,
    DWORD dwStatusInformationLength);
```

### <a name="parameters"></a>Parametry

*dwContext*<br/>
Wartość kontekstu dostarczoną przez aplikację.

*dwInternetStatus*<br/>
Kod stanu, który wskazuje, dlaczego jest wykonywane wywołanie zwrotne. Zobacz **uwagi** dla tabeli możliwych wartości.

*lpvStatusInformation*<br/>
Wskaźnik do buforu, zawierające informacje dotyczące tego wywołania zwrotnego.

*dwStatusInformationLength*<br/>
Rozmiar *lpvStatusInformation*.

### <a name="remarks"></a>Uwagi

Najpierw musisz wywołać [EnableStatusCallback](#enablestatuscallback) z zalet wywołanie zwrotne dla stanu.

*DwInternetStatus* parametr wskazuje wykonywanej operacji i określa, jakie zawartość *lpvStatusInformation* będzie. *dwStatusInformationLength* wskazuje długość danych zawartych w *lpvStatusInformation*. Wartości stanu następujących *dwInternetStatus* są zdefiniowane w następujący sposób:

|Wartość|Znaczenie|
|-----------|-------------|
|INTERNET_STATUS_RESOLVING_NAME|Wyszukiwanie adresu IP, nazwy zawarte w *lpvStatusInformation*.|
|INTERNET_STATUS_NAME_RESOLVED|Pomyślnie odnaleziono adres IP o nazwie zawarte w *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTING_TO_SERVER|Nawiązywanie połączenia z adresu gniazda ([SOCKADDR](/windows/desktop/winsock/sockaddr-2)) wskazywany przez *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTED_TO_SERVER|Pomyślnie połączono z adresu gniazda (SOCKADDR), wskazywana przez *lpvStatusInformation*.|
|INTERNET_STATUS_SENDING_REQUEST|Prośba o informacje dotyczące wysyłania do serwera. *LpvStatusInformation* parametr ma wartość NULL.|
|INTERNET_STATUS_ REQUEST_SENT|Pomyślnie wysłano żądanie informacji, na serwerze. *LpvStatusInformation* parametr ma wartość NULL.|
|INTERNET_STATUS_RECEIVING_RESPONSE|Oczekiwanie na odpowiedź na żądanie z serwera. *LpvStatusInformation* parametr ma wartość NULL.|
|INTERNET_STATUS_RESPONSE_RECEIVED|Pomyślnie odebrano odpowiedź z serwera. *LpvStatusInformation* parametr ma wartość NULL.|
|INTERNET_STATUS_CLOSING_CONNECTION|Zamyka połączenie z serwerem. *LpvStatusInformation* parametr ma wartość NULL.|
|INTERNET_STATUS_CONNECTION_CLOSED|Pomyślnie zamknął połączenie z serwerem. *LpvStatusInformation* parametr ma wartość NULL.|
|INTERNET_STATUS_HANDLE_CREATED|Używane przez funkcję Win32 API [funkcji InternetConnect](/windows/desktop/api/wininet/nf-wininet-internetconnecta) do wskazania, że utworzył nowy uchwyt. Dzięki temu funkcja wywołanie Win32 aplikacji [InternetCloseHandle](/windows/desktop/api/wininet/nf-wininet-internetclosehandle) z innego wątku, jeśli połączenia trwa zbyt długo. Zobacz Windows SDKfor więcej informacji na temat tych funkcji.|
|INTERNET_STATUS_HANDLE_CLOSING|Ta wartość dojścia zostały przerwane pomyślnie.|

Zastąp tę funkcję elementu członkowskiego, aby wymagać niektóre akcje, przed wykonaniem procedura wywołania zwrotnego stanu.

> [!NOTE]
> Stan wywołania zwrotne wymagać ochrony stan wątku. Jeśli używasz MFC w bibliotece udostępnionej, Dodaj następujący wiersz na początku przesłonięcia:

[!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]

Aby uzyskać więcej informacji na temat operacji asynchronicznych, zobacz artykuł [Internet pierwsze kroki: WinInet](../../mfc/wininet-basics.md).

## <a name="openurl"></a>  CInternetSession::OpenURL

Ten element członkowski należy wywołać funkcję, aby wysłać żądanie do serwera HTTP i zezwolić na klientów określić dodatkowe RFC822 MIME lub nagłówki HTTP do wysłania wraz z żądaniem.

```cpp
CStdioFile* OpenURL(
    LPCTSTR pstrURL,
    DWORD_PTR dwContext = 1,
    DWORD dwFlags = INTERNET_FLAG_TRANSFER_ASCII,
    LPCTSTR pstrHeaders = NULL,
    DWORD dwHeadersLength = 0);
```

### <a name="parameters"></a>Parametry

*pstrURL*<br/>
Wskaźnik na nazwę adresu URL, aby rozpocząć się odczyt. Tylko adresy URL rozpoczynające się od pliku:, ftp:, gopher:, lub http: są obsługiwane. Potwierdza, jeśli *pstrURL* ma wartość NULL.

*dwContext*<br/>
Wartości zdefiniowane przez aplikację wykryto zwracany uchwyt w wywołania zwrotnego.

*dwFlags*<br/>
Flagi opisujące sposób obsługi tego połączenia. Zobacz **uwagi** Aby uzyskać więcej informacji na temat prawidłowe flagi. Prawidłowe flagi są:

- INTERNET_FLAG_TRANSFER_ASCII domyślną. Przetransferuj plik jako tekst w formacie ASCII.

- INTERNET_FLAG_TRANSFER_BINARY przetransferować plik jako plik binarny.

- INTERNET_FLAG_RELOAD uzyskać danych z sieci, nawet jeśli jest ona buforowana lokalnie.

- INTERNET_FLAG_DONT_CACHE nie buforują dane, lokalnie lub w żadnych bram.

- INTERNET_FLAG_SECURE ta flaga ma zastosowanie tylko żądania HTTP. Żąda bezpiecznego transakcji na potrzeby przesyłu Secure Sockets Layer lub procent

- INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT, jeśli jest to możliwe, ponowne używanie istniejących połączeń z serwerem dla nowych żądań generowanych przez `OpenUrl` zamiast tworzenia nowej sesji dla każdego żądania połączenia.

- INTERNET_FLAG_PASSIVE używane dla witryny FTP. Używa pasywnych FTP semantyki. Używane z [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) z `OpenURL`.

*pstrHeaders*<br/>
Wskaźnik do ciągu zawierającego nagłówki, które zostanie wysłane do serwera HTTP.

*dwHeadersLength*<br/>
Długość w znakach dodatkowych nagłówków. Jeśli jest L-1 i *pstrHeaders* jest różna od NULL, następnie *pstrHeaders* założono, zerowego zakończony i długość jest obliczana.

### <a name="return-value"></a>Wartość zwracana

Zwraca dojście do pliku dla tylko usługi FTP, GOPHER, HTTP i Internet typu pliku. Zwraca wartość NULL, jeśli analiza kodu nie powiodło się.

Wskaźnik, `OpenURL` zależy od zwraca *pstrURL*przez typ usługi. W poniższej tabeli przedstawiono możliwe wskaźniki `OpenURL` może zwrócić.

|Typ adresu URL|Zwraca|
|--------------|-------------|
|file://|`CStdioFile*`|
|http://|`CHttpFile*`|
|Gopher://|`CGopherFile*`|
|ftp://|`CInternetFile*`|

### <a name="remarks"></a>Uwagi

Parametr *Flagidw* musi zawierać INTERNET_FLAG_TRANSFER_ASCII lub INTERNET_FLAG_TRANSFER_BINARY, ale nie oba. Pozostałe flagi można łączyć za pomocą operatora testu koniunkcji **lub** — operator ( **&#124;**).

`OpenURL`, który opakowuje funkcję Win32 `InternetOpenURL`, umożliwia tylko pobieranie, pobieranie i odczytywanie danych z serwera internetowego. `OpenURL` Umożliwia nie manipulowania plików w lokalizacji zdalnej, dzięki czemu wymaga nie [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) obiektu.

Aby użyć konkretnego połączenia (oznacza to, związane z protokołem) funkcje, takie jak zapisywanie do pliku, użytkownik musi Otwórz sesję programu, otwórz szczególnego rodzaju połączenia, a następnie użyj tego połączenia, aby otworzyć plik w żądany tryb. Zobacz `CInternetConnection` Aby uzyskać więcej informacji na temat funkcji specyficznych dla połączenia.

## <a name="operator_hinternet"></a>  CInternetSession::operator HINTERNET

Można pobrać uchwytu Windows dla bieżącej sesji Internet, należy użyć tego operatora.

```cpp
operator HINTERNET() const;
```

## <a name="setcookie"></a>  CInternetSession::SetCookie

Ustawia plik cookie dla określonego adresu URL.

```cpp
static BOOL SetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPCTSTR pstrCookieData);
```

### <a name="parameters"></a>Parametry

*pstrUrl*<br/>
Wskaźnik na ciąg zakończony znakiem null, który określa adres URL, dla którego plik cookie powinna być ustawiona.

*pstrCookieName*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku cookie.

*pstrCookieData*<br/>
Wskaźnik do ciągu zawierającego dane ciągu do skojarzenia z adresem URL.

### <a name="return-value"></a>Wartość zwracana

W przeciwnym razie zwraca wartość TRUE, jeśli kończy się pomyślnie, lub FAŁSZ. Aby uzyskać kod błędu, należy wywołać `GetLastError.`

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [InternetSetCookie](/windows/desktop/api/wininet/nf-wininet-internetsetcookiea), zgodnie z opisem w zestawie Windows SDK.

## <a name="setoption"></a>  CInternetSession::SetOption

Wywołaj tę funkcję elementu członkowskiego, aby ustawić opcje dla sesji internetowej.

```cpp
BOOL SetOption(
    DWORD dwOption,
    LPVOID lpBuffer,
    DWORD dwBufferLength,
    DWORD dwFlags = 0);

BOOL SetOption(
    DWORD dwOption,
    DWORD dwValue,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parametry

*dwOption*<br/>
Internet możliwość ustawienia. Zobacz [flagi opcji](/windows/desktop/WinInet/option-flags) w SDKfor Windows lista możliwych opcji.

*lpBuffer*<br/>
Bufor, który zawiera ustawienia opcji.

*dwBufferLength*<br/>
Długość *sprawdzanie* ani rozmiaru *dwValue*.

*dwValue*<br/>
DWORD, który zawiera ustawienia opcji.

*dwFlags*<br/>
Określa różne opcje pamięci podręcznej. Wartość domyślna jest równa 0. Możliwe wartości:

- INTERNET_FLAG_DONT_CACHE nie buforują dane, lokalnie lub w dowolne serwery bramy.

- Pobierz INTERNET_FLAG_OFFLINE operacje są spełnione przez trwałej pamięci podręcznej tylko. Jeśli element nie istnieje w pamięci podręcznej, zwracany jest kod odpowiedni komunikat o błędzie. Ta flaga mogą być łączone za pomocą operatora testu koniunkcji **lub** ( **&#124;**) — operator.

### <a name="return-value"></a>Wartość zwracana

Jeśli operacja zakończyła się pomyślnie, zwracana jest wartość TRUE. Jeśli wystąpi błąd, jest zwracana wartość FAŁSZ. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.

## <a name="see-also"></a>Zobacz także

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Klasa CHttpConnection](../../mfc/reference/chttpconnection-class.md)<br/>
[Klasa CFtpConnection](../../mfc/reference/cftpconnection-class.md)<br/>
[Klasa CGopherConnection](../../mfc/reference/cgopherconnection-class.md)
