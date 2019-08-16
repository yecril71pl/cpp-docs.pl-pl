---
title: Klasa CInternetSession
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
ms.openlocfilehash: c9b8eaf51820dfcd08c1390c8645978fa403931d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505849"
---
# <a name="cinternetsession-class"></a>Klasa CInternetSession

Tworzy i inicjuje jedną lub kilka równoczesnych sesji internetowych oraz, w razie potrzeby, opisuje połączenie z serwerem proxy.

## <a name="syntax"></a>Składnia

```cpp
class CInternetSession : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInternetSession::CInternetSession](#cinternetsession)|Konstruuje `CInternetSession` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInternetSession:: Close](#close)|Zamyka połączenie internetowe po zakończeniu sesji internetowej.|
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|Ustanawia procedurę wywołania zwrotnego stanu.|
|[CInternetSession:: GetContext](#getcontext)|Zamyka połączenie internetowe po zakończeniu sesji internetowej.|
|[CInternetSession:: getcookas](#getcookie)|Zwraca pliki cookie dla podanego adresu URL i wszystkich jego nadrzędnych adresów URL.|
|[CInternetSession::GetCookieLength](#getcookielength)|Pobiera zmienną określającą długość pliku cookie przechowywanego w buforze.|
|[CInternetSession::GetFtpConnection](#getftpconnection)|Otwiera sesję FTP z serwerem. Rejestruje użytkownika.|
|[CInternetSession::GetGopherConnection](#getgopherconnection)|Otwiera serwer gopher dla aplikacji próbującej otworzyć połączenie.|
|[CInternetSession::GetHttpConnection](#gethttpconnection)|Otwiera serwer HTTP dla aplikacji próbującej otworzyć połączenie.|
|[CInternetSession::OnStatusCallback](#onstatuscallback)|Aktualizuje stan operacji, gdy włączone jest wywołanie zwrotne stanu.|
|[CInternetSession::OpenURL](#openurl)|Analizuje i otwiera adres URL.|
|[CInternetSession::SetCookie](#setcookie)|Ustawia plik cookie dla podanego adresu URL.|
|[CInternetSession::SetOption](#setoption)|Ustawia opcje dla sesji internetowej.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInternetSession:: operator HINTERNET](#operator_hinternet)|Dojście do bieżącej sesji internetowej.|

## <a name="remarks"></a>Uwagi

Jeśli połączenie internetowe musi być utrzymywane przez czas trwania aplikacji, można utworzyć `CInternetSession` element członkowski klasy [CWinApp](../../mfc/reference/cwinapp-class.md).

Po ustanowieniu sesji internetowej można wywołać [OpenURL](#openurl). `CInternetSession`następnie analizuje adres URL za pomocą wywołania funkcji globalnej [AfxParseURL](internet-url-parsing-globals.md#afxparseurl). Niezależnie od jego typu `CInternetSession` protokołu interpretuje adres URL i zarządza nim. Może obsługiwać żądania dla plików lokalnych identyfikowanych za pomocą zasobu adresu URL "file://". `OpenURL`Zwraca wskaźnik do obiektu [CStdioFile](../../mfc/reference/cstdiofile-class.md) , jeśli przekazana nazwa jest plikiem lokalnym.

W przypadku otwarcia adresu URL na serwerze internetowym przy `OpenURL`użyciu programu można odczytać informacje z witryny. Jeśli chcesz wykonać działania specyficzne dla usługi (na przykład HTTP, FTP lub gopher) dla plików znajdujących się na serwerze, należy ustanowić odpowiednie połączenie z tym serwerem. Aby otworzyć określony rodzaj połączenia bezpośrednio z określoną usługą, należy użyć jednej z następujących funkcji Członkowskich:

- [GetGopherConnection](#getgopherconnection) otworzyć połączenia z usługą gopher.

- [GetHttpConnection](#gethttpconnection) otworzyć połączenia z usługą http.

- [GetFtpConnection](#getftpconnection) otworzyć połączenia z usługą FTP.

[](#setoption) Metoda SetOption umożliwia ustawienie opcji zapytania dla sesji, takich jak wartości limitu czasu, liczba ponownych prób i tak dalej.

`CInternetSession`funkcje składowe [setcooka](#setcookie), getcookas i [GetCookieLength](#getcookielength) zapewniają środki do zarządzania bazą danych plików cookie Win32, za pośrednictwem których serwery i skrypty utrzymują informacje o stanie na stacji roboczej klienta. [](#getcookie)

Aby uzyskać więcej informacji na temat podstawowych zadań związanych z programowaniem [internetowym, zobacz artykuł Internet po pierwsze kroki: WinInet](../../mfc/wininet-basics.md). Aby uzyskać ogólne informacje na temat używania klas MFC WinInet, zapoznaj się z artykułem [programowanie internetowe za pomocą usługi WinInet](../../mfc/win32-internet-extensions-wininet.md).

> [!NOTE]
> `CInternetSession`spowoduje zgłoszenie elementu [AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception) dla nieobsługiwanych typów usług. Obecnie obsługiwane są tylko następujące typy usług: FTP, HTTP, Gopher i File.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`CInternetSession`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet. h

## <a name="cinternetsession"></a>CInternetSession::CInternetSession

Ta funkcja członkowska jest wywoływana, `CInternetSession` gdy obiekt zostanie utworzony.

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
Wskaźnik do ciągu, który identyfikuje nazwę aplikacji lub jednostki wywołującej funkcje internetowe (na przykład "Microsoft Internet Browser"). Jeśli *pstrAgent* ma wartość null (domyślnie), struktura wywołuje funkcję globalną [AfxGetAppName](application-information-and-management.md#afxgetappname), która zwraca ciąg zakończony znakiem null zawierający nazwę aplikacji. Niektóre protokoły używają tego ciągu do identyfikowania aplikacji na serwerze.

*dwContext*<br/>
Identyfikator kontekstu dla operacji. *dwContext* identyfikuje informacje o stanie operacji zwrócone przez [CInternetSession:: OnStatusCallback](#onstatuscallback). Wartość domyślna to 1; można jednak jawnie przypisać określony identyfikator kontekstu dla operacji. Obiekt i wszystkie wykonane zadania zostaną skojarzone z tym IDENTYFIKATORem kontekstu.

*dwAccessType*<br/>
Wymagany typ dostępu. Poniżej przedstawiono prawidłowe wartości, dokładnie jedną z nich można dostarczyć:

- INTERNET_OPEN_TYPE_PRECONFIG Połącz przy użyciu wstępnie skonfigurowanych ustawień w rejestrze. Ten typ dostępu jest ustawiany jako domyślny. Aby nawiązać połączenie za pomocą serwera proxy TIS, ustaw *dwAccessType* na tę wartość. Następnie należy odpowiednio ustawić rejestr.

- INTERNET_OPEN_TYPE_DIRECT Połącz się bezpośrednio z Internetem.

- INTERNET_OPEN_TYPE_PROXY połączenie za pomocą serwera proxy CERN.

Aby uzyskać informacje na temat łączenia się z różnymi typami serwerów proxy, zobacz [kroki w typowej aplikacji klienckiej FTP](../../mfc/steps-in-a-typical-ftp-client-application.md).

*pstrProxyName*<br/>
Nazwa preferowanego serwera proxy CERN, jeśli *dwAccessType* jest ustawiony jako INTERNET_OPEN_TYPE_PROXY. Wartość domyślna to NULL.

*pstrProxyBypass*<br/>
Wskaźnik do ciągu zawierającego opcjonalną listę adresów serwerów. Te adresy mogą być pomijane podczas korzystania z dostępu do serwera proxy. Jeśli zostanie podana wartość NULL, lista obejścia zostanie odczytana z rejestru. Ten parametr ma znaczenie tylko wtedy, gdy *dwAccessType* jest ustawiony na INTERNET_OPEN_TYPE_PROXY.

*flagiDW*<br/>
Wskazuje różne opcje buforowania. Wartość domyślna to 0. Możliwe wartości to:

- INTERNET_FLAG_DONT_CACHE nie buforuje danych lokalnie ani na żadnym serwerze bramy.

- Operacje pobierania INTERNET_FLAG_OFFLINE są spełnione tylko w trwałej pamięci podręcznej. Jeśli element nie istnieje w pamięci podręcznej, zwracany jest odpowiedni kod błędu. Ta flaga może być łączona z operatorem bitowym **&#124;** lub ().

### <a name="remarks"></a>Uwagi

`CInternetSession`jest pierwszą funkcją internetową wywoływaną przez aplikację. Inicjuje ona wewnętrzne struktury danych i przygotowuje się do przyszłych wywołań aplikacji.

Jeśli nie można otworzyć połączenia internetowego, program `CInternetSession` zgłosi [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception).

### <a name="example"></a>Przykład

Zobacz przykład dla [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="close"></a>CInternetSession:: Close

Wywołaj tę funkcję elementu członkowskiego, gdy aplikacja zakończyła pracę przy użyciu `CInternetSession` obiektu.

```cpp
virtual void Close();
```

### <a name="example"></a>Przykład

Zobacz przykład dla [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="enablestatuscallback"></a>CInternetSession::EnableStatusCallback

Wywołaj tę funkcję elementu członkowskiego, aby włączyć wywołanie zwrotne stanu.

```cpp
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Określa, czy wywołanie zwrotne jest włączone czy wyłączone. Wartość domyślna to TRUE.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0. Jeśli wywołanie zakończy się niepowodzeniem, ustal przyczynę niepowodzenia, badając zgłoszony obiekt [CInternetException](../../mfc/reference/cinternetexception-class.md) .

### <a name="remarks"></a>Uwagi

Podczas obsługi wywołania zwrotnego stanu można podać stan postępu operacji (np. rozpoznawanie nazwy, łączenie z serwerem itd.) na pasku stanu aplikacji. Wyświetlanie stanu operacji jest szczególnie pożądane podczas długotrwałej operacji.

Ponieważ wywołania zwrotne występują podczas przetwarzania żądania, aplikacja powinna spędzać się możliwie najmniejszej ilości czasu w wywołaniu wywołania zwrotnego, aby zapobiec obniżeniu przepływności danych do sieci. Na przykład umieszczenie okna dialogowego w wywołaniu zwrotnym może być długotrwałą operacją, aby serwer przerywał żądanie.

Nie można usunąć wywołania zwrotnego stanu, o ile wszystkie wywołania zwrotne są w stanie oczekiwania.

Aby obsługiwać wszystkie operacje asynchronicznie, należy utworzyć własny wątek lub użyć funkcji WinInet bez MFC.

## <a name="getcontext"></a>CInternetSession:: GetContext

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wartość kontekstu dla konkretnej sesji aplikacji.

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator kontekstu zdefiniowany przez aplikację.

### <a name="remarks"></a>Uwagi

[OnStatusCallback](#onstatuscallback) używa identyfikatora kontekstu zwróconego przez `GetContext` , aby zgłosić stan konkretnej aplikacji. Na przykład, gdy użytkownik aktywuje żądanie internetowe, które polega na zwracaniu informacji o stanie, wywołanie zwrotne stanu używa identyfikatora kontekstu do raportowania stanu określonego żądania. Jeśli użytkownik aktywuje dwa oddzielne żądania internetowe, które obejmują Zwracanie informacji o stanie, program `OnStatusCallback` używa identyfikatorów kontekstu do zwrócenia statusu o odpowiadających im żądaniach. W związku z tym identyfikator kontekstu jest używany dla wszystkich operacji wywołania zwrotnego stanu i jest skojarzony z sesją do momentu zakończenia sesji.

Aby uzyskać więcej informacji o operacjach asynchronicznych, [Zobacz artykuł Internet w pierwszej kolejności: WinInet](../../mfc/wininet-basics.md).

## <a name="getcookie"></a>CInternetSession:: getcookas

Ta funkcja członkowska implementuje zachowanie funkcji Win32 [InternetGetCookie](/windows/win32/api/wininet/nf-wininet-internetgetcookiew), zgodnie z opisem w Windows SDK.

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
Wskaźnik do ciągu zawierającego nazwę pliku cookie do pobrania dla podanego adresu URL.

*pstrCookieData*<br/>
W pierwszym przeciążeniu, wskaźnik do ciągu zawierającego adres bufora, który odbiera dane plików cookie. Ta wartość może być RÓWNa NULL. W drugim przeciążeniu odwołanie do obiektu [CString](../../atl-mfc-shared/reference/cstringt-class.md) , w którym mają zostać odebrane dane plików cookie.

*dwBufLen*<br/>
Zmienna określająca rozmiar buforu *pstrCookieData* . Jeśli funkcja się powiedzie, bufor otrzymuje ilość danych skopiowanych do buforu *pstrCookieData* . Jeśli *pstrCookieData* ma wartość null, ten parametr otrzymuje wartość określającą rozmiar buforu niezbędnego do skopiowania wszystkich danych plików cookie.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli powodzenie, lub FALSE w przeciwnym razie. Jeśli wywołanie nie powiedzie się, wywołaj [wartość GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) funkcji Win32, aby określić przyczynę błędu. Stosowane są następujące wartości błędów:

- ERROR_NO_MORE_ITEMS nie istnieje plik cookie dla podanego adresu URL i jego wszystkich elementów nadrzędnych.

- ERROR_INSUFFICIENT_BUFFER wartość przekazaną w *dwBufLen* jest niewystarczająca, aby skopiować wszystkie dane plików cookie. Wartość zwrócona w *dwBufLen* to rozmiar buforu niezbędnego do pobrania wszystkich danych.

### <a name="remarks"></a>Uwagi

W drugim przeciążeniu MFC pobiera dane plików cookie do podanego `CString` obiektu.

## <a name="getcookielength"></a>CInternetSession::GetCookieLength

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać długość pliku cookie przechowywanego w buforze.

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

Wartość DWORD wskazująca długość pliku cookie przechowywanego w buforze. Zero, jeśli nie istnieje plik cookie o nazwie wskazanej przez *pstrCookieName* .

### <a name="remarks"></a>Uwagi

Ta wartość jest używana przez [](#getcookie)getcookas.

## <a name="getftpconnection"></a>CInternetSession::GetFtpConnection

Wywołaj tę funkcję elementu członkowskiego, aby nawiązać połączenie FTP i uzyskać `CFtpConnection` wskaźnik do obiektu.

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
Wskaźnik na ciąg zakończony znakiem null, który określa nazwę użytkownika do zalogowania. Jeśli wartość jest równa NULL, wartość domyślna to anonimowe.

*pstrPassword*<br/>
Wskaźnik do ciągu zakończonego wartością null, który określa hasło, które ma być używane do logowania. Jeśli zarówno *pstrPassword* , jak i *pstrUserName* mają wartość null, domyślnym hasłem anonimowym jest nazwa e-mail użytkownika. Jeśli *pstrPassword* ma wartość null (lub ciąg pusty), ale *pstrUserName* nie ma wartości null, używane jest puste hasło. W poniższej tabeli opisano zachowanie czterech możliwych ustawień *pstrUserName* i *pstrPassword*:

| *pstrUserName*  | *pstrPassword*  | Nazwa użytkownika wysłana do serwera FTP | Hasło wysyłane do serwera FTP |
|-----------------|-----------------|-----------------------------|-----------------------------|
|   NULL lub ""   |   NULL lub ""   |         anonimowe         |      Nazwa e-mail użytkownika      |
| Ciąg o wartości innej niż NULL |   NULL lub ""   |       *pstrUserName*        |             " "             |
|      NULL       | Ciąg o wartości innej niż NULL |            BŁĄD            |            BŁĄD            |
| Ciąg o wartości innej niż NULL | Ciąg o wartości innej niż NULL |       *pstrUserName*        |       *pstrPassword*        |

*nPort*<br/>
Numer identyfikujący port TCP/IP, który ma być używany na serwerze.

*bPassive*<br/>
Określa tryb pasywny lub aktywny dla tej sesji FTP. Jeśli ustawiono wartość true, ustawia Win32 API `dwFlag` na INTERNET_FLAG_PASSIVE.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [CFtpConnection](../../mfc/reference/cftpconnection-class.md) . Jeśli wywołanie zakończy się niepowodzeniem, ustal przyczynę niepowodzenia, badając zgłoszony obiekt [CInternetException](../../mfc/reference/cinternetexception-class.md) .

### <a name="remarks"></a>Uwagi

`GetFtpConnection`nawiązuje połączenie z serwerem FTP i tworzy i zwraca wskaźnik do `CFTPConnection` obiektu. Nie wykonuje żadnych określonych operacji na serwerze. Jeśli zamierzasz odczytywać lub zapisywać pliki, na przykład należy wykonać te operacje jako oddzielne kroki. Zobacz klasy [CFtpConnection](../../mfc/reference/cftpconnection-class.md) i [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) , aby uzyskać informacje na temat wyszukiwania plików, otwierania plików i odczytywania plików lub zapisywania ich w plikach. Zapoznaj się z artykułem [programowanie internetowe za pomocą usługi WinInet](../../mfc/win32-internet-extensions-wininet.md) , aby poznać kroki wykonywania typowych zadań połączeń FTP.

### <a name="example"></a>Przykład

Zobacz przykład dla [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="getgopherconnection"></a>CInternetSession::GetGopherConnection

Wywołaj tę funkcję elementu członkowskiego, aby nawiązać nowe połączenie Gopher i uzyskać `CGopherConnection` wskaźnik do obiektu.

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
Wskaźnik do ciągu zawierającego hasło dostępu.

*nPort*<br/>
Numer identyfikujący port TCP/IP, który ma być używany na serwerze.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) . Jeśli wywołanie zakończy się niepowodzeniem, ustal przyczynę niepowodzenia, badając zgłoszony obiekt [CInternetException](../../mfc/reference/cinternetexception-class.md) .

### <a name="remarks"></a>Uwagi

`GetGopherConnection`nawiązuje połączenie z serwerem Gopher i tworzy i zwraca wskaźnik do `CGopherConnection` obiektu. Nie wykonuje żadnych określonych operacji na serwerze. Jeśli zamierzasz odczytywać lub zapisywać dane, na przykład należy wykonać te operacje jako oddzielne kroki. Zobacz klasy [CGopherConnection](../../mfc/reference/cgopherconnection-class.md), [CGopherFile](../../mfc/reference/cgopherfile-class.md)i [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) , aby uzyskać informacje na temat wyszukiwania plików, otwierania plików i odczytywania plików lub zapisywania ich w plikach. Aby uzyskać informacje na temat przeglądania witryny FTP, zobacz funkcja członkowska [OpenURL](#openurl). Zapoznaj się z artykułem [programowanie internetowe za pomocą usługi WinInet](../../mfc/win32-internet-extensions-wininet.md) , aby poznać kroki wykonywania typowych zadań związanych z połączeniami gopher.

## <a name="gethttpconnection"></a>CInternetSession::GetHttpConnection

Wywołaj tę funkcję elementu członkowskiego, aby nawiązać połączenie HTTP i uzyskać `CHttpConnection` wskaźnik do obiektu.

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
Numer identyfikujący port TCP/IP, który ma być używany na serwerze.

*pstrUserName*<br/>
Wskaźnik do ciągu zawierającego nazwę użytkownika.

*pstrPassword*<br/>
Wskaźnik do ciągu zawierającego hasło dostępu.

*flagiDW*<br/>
Dowolna kombinacja `INTERNET_FLAG_*` flag. Zapoznaj się z tabelą w sekcji **spostrzeżenia** elementu [CHttpConnection:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) , aby uzyskać opis wartości *flagiDW* .

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [CHttpConnection](../../mfc/reference/chttpconnection-class.md) . Jeśli wywołanie zakończy się niepowodzeniem, ustal przyczynę niepowodzenia, badając zgłoszony obiekt [CInternetException](../../mfc/reference/cinternetexception-class.md) .

### <a name="remarks"></a>Uwagi

`GetHttpConnection`nawiązuje połączenie z serwerem HTTP i tworzy i zwraca wskaźnik do `CHttpConnection` obiektu. Nie wykonuje żadnych określonych operacji na serwerze. Jeśli zamierzasz wysyłać zapytania do nagłówka HTTP, na przykład należy wykonać tę operację jako osobny krok. Zobacz klasy [CHttpConnection](../../mfc/reference/chttpconnection-class.md) i [CHttpFile](../../mfc/reference/chttpfile-class.md) , aby uzyskać informacje o operacjach, które można wykonać przy użyciu połączenia z serwerem HTTP. Aby uzyskać informacje na temat przeglądania witryny HTTP, zobacz funkcja członkowska [OpenURL](#openurl). Zapoznaj się z artykułem [programowanie internetowe za pomocą usługi WinInet](../../mfc/win32-internet-extensions-wininet.md) , aby poznać kroki wykonywania typowych zadań połączeń HTTP.

## <a name="onstatuscallback"></a>CInternetSession::OnStatusCallback

Ta funkcja członkowska jest wywoływana przez platformę w celu zaktualizowania stanu po włączeniu wywołania zwrotnego stanu i oczekującej operacji.

```cpp
virtual void OnStatusCallback(
    DWORD_PTR dwContext,
    DWORD dwInternetStatus,
    LPVOID lpvStatusInformation,
    DWORD dwStatusInformationLength);
```

### <a name="parameters"></a>Parametry

*dwContext*<br/>
Wartość kontekstu podana przez aplikację.

*dwInternetStatus*<br/>
Kod stanu wskazujący, że wywołanie zwrotne jest wykonywane. Zobacz **uwagi** dla tabeli możliwych wartości.

*lpvStatusInformation*<br/>
Wskaźnik do buforu zawierającego informacje dotyczące tego wywołania zwrotnego.

*dwStatusInformationLength*<br/>
Rozmiar *lpvStatusInformation*.

### <a name="remarks"></a>Uwagi

Musisz najpierw wywołać [EnableStatusCallback](#enablestatuscallback) , aby skorzystać z wywołania zwrotnego stanu.

Parametr *dwInternetStatus* wskazuje wykonywaną operację i określa zawartość *lpvStatusInformation* . *dwStatusInformationLength* wskazuje długość danych zawartych w *lpvStatusInformation*. Następujące wartości stanu dla *dwInternetStatus* są zdefiniowane w następujący sposób:

|Wartość|Znaczenie|
|-----------|-------------|
|INTERNET_STATUS_RESOLVING_NAME|Wyszukiwanie adresu IP nazwy zawartej w *lpvStatusInformation*.|
|INTERNET_STATUS_NAME_RESOLVED|Pomyślnie znaleziono adres IP nazwy zawartej w *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTING_TO_SERVER|Nawiązywanie połączenia z adresem gniazda ([SOCKADDR](/windows/win32/winsock/sockaddr-2)) wskazywanym przez *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTED_TO_SERVER|Pomyślnie nawiązano połączenie z adresem gniazda (SOCKADDR) wskazywanym przez *lpvStatusInformation*.|
|INTERNET_STATUS_SENDING_REQUEST|Wysyłanie żądania informacji do serwera. Parametr *lpvStatusInformation* ma wartość null.|
|INTERNET_STATUS_ REQUEST_SENT|Pomyślnie wysłano żądanie informacji do serwera. Parametr *lpvStatusInformation* ma wartość null.|
|INTERNET_STATUS_RECEIVING_RESPONSE|Oczekiwanie na odpowiedź serwera na żądanie. Parametr *lpvStatusInformation* ma wartość null.|
|INTERNET_STATUS_RESPONSE_RECEIVED|Pomyślnie odebrano odpowiedź z serwera. Parametr *lpvStatusInformation* ma wartość null.|
|INTERNET_STATUS_CLOSING_CONNECTION|Zamykanie połączenia z serwerem. Parametr *lpvStatusInformation* ma wartość null.|
|INTERNET_STATUS_CONNECTION_CLOSED|Pomyślnie zamknięto połączenie z serwerem. Parametr *lpvStatusInformation* ma wartość null.|
|INTERNET_STATUS_HANDLE_CREATED|Używane przez [InternetConnect](/windows/win32/api/wininet/nf-wininet-internetconnectw) funkcję Win32 API, aby wskazać, że został utworzony nowy uchwyt. Dzięki temu aplikacja wywołuje funkcję Win32 [InternetClosehandle](/windows/win32/api/wininet/nf-wininet-internetclosehandle) z innego wątku, jeśli połączenie trwa zbyt długo. Zobacz SDKfor systemu Windows, aby uzyskać więcej informacji o tych funkcjach.|
|INTERNET_STATUS_HANDLE_CLOSING|Pomyślnie zakończono tę wartość dojścia.|

Przesłoń tę funkcję elementu członkowskiego, aby wymagać pewnej akcji przed wykonaniem procedury wywołania zwrotnego stanu.

> [!NOTE]
> Wywołania zwrotne stanu wymagają ochrony przed stanem wątku. Jeśli używasz MFC w bibliotece udostępnionej, Dodaj następujący wiersz na początku przesłonięcia:

[!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]

Aby uzyskać więcej informacji o operacjach asynchronicznych, [Zobacz artykuł Internet w pierwszej kolejności: WinInet](../../mfc/wininet-basics.md).

## <a name="openurl"></a>CInternetSession::OpenURL

Wywołaj tę funkcję elementu członkowskiego, aby wysłać określone żądanie do serwera HTTP i zezwolić klientowi na określenie dodatkowych nagłówków RFC822, MIME lub HTTP do wysłania wraz z żądaniem.

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
Wskaźnik do nazwy adresu URL, aby rozpocząć odczytywanie. Obsługiwane są tylko adresy URL zaczynające się od pliku:, FTP:, gopher: lub http:. Asserts, jeśli *pstrURL* ma wartość null.

*dwContext*<br/>
Wartość zdefiniowana przez aplikację przekazana z zwróconym dojściem w wywołaniu zwrotnym.

*flagiDW*<br/>
Flagi opisujące, jak obsłużyć to połączenie. Aby uzyskać więcej informacji na temat prawidłowych flag, zobacz **uwagi** . Prawidłowe flagi to:

- INTERNET_FLAG_TRANSFER_ASCII wartość domyślną. Prześlij plik jako tekst ASCII.

- INTERNET_FLAG_TRANSFER_BINARY przenieść plik jako plik binarny.

- INTERNET_FLAG_RELOAD Pobieraj dane z przewodu nawet wtedy, gdy jest on buforowany lokalnie.

- INTERNET_FLAG_DONT_CACHE nie buforuje danych lokalnie ani w żadnej bramie.

- INTERNET_FLAG_SECURE ta flaga ma zastosowanie tylko do żądań HTTP. Żąda bezpiecznych transakcji w sieci z SSL lub PCT.

- INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT Jeśli to możliwe, Użyj istniejących połączeń z serwerem w celu uzyskania nowych żądań wygenerowanych przez `OpenUrl` program zamiast tworzenia nowej sesji dla każdego żądania połączenia.

- INTERNET_FLAG_PASSIVE używany dla witryny FTP. Używa pasywnej semantyki FTP. Używany z [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) `OpenURL`.

*pstrHeaders*<br/>
Wskaźnik do ciągu zawierającego nagłówki do wysłania do serwera HTTP.

*dwHeadersLength*<br/>
Długość (w znakach) dodatkowych nagłówków. Jeśli jest to-1L i *pstrHeaders* jest różna od null, zakłada się, że *pstrHeaders* zostanie zakończona zerem i jest obliczana długość.

### <a name="return-value"></a>Wartość zwracana

Zwraca dojście do pliku tylko dla usług FTP, GOPHER, HTTP i typu plików. Zwraca wartość NULL, jeśli analizowanie nie powiodło się.

Wskaźnik, który `OpenURL` zwraca, zależy od typu usługi *pstrURL*. W poniższej tabeli pokazano, jakie możliwe `OpenURL` wskaźniki można zwrócić.

|Typ adresu URL|Zwraca|
|--------------|-------------|
|file://|`CStdioFile*`|
|http://|`CHttpFile*`|
|gopher://|`CGopherFile*`|
|ftp://|`CInternetFile*`|

### <a name="remarks"></a>Uwagi

Parametr *flagiDW* musi zawierać wartość INTERNET_FLAG_TRANSFER_ASCII lub INTERNET_FLAG_TRANSFER_BINARY, ale nie oba jednocześnie. Pozostałe flagi można łączyć z operatorem bitowym or ( **&#124;** ).

`OpenURL`, który zawija funkcję `InternetOpenURL`Win32, umożliwia pobieranie, pobieranie i odczytywanie danych z serwera internetowego. `OpenURL`nie zezwala na manipulowanie plikami w lokalizacji zdalnej, dlatego nie wymaga żadnych obiektów [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) .

Aby korzystać z funkcji specyficznych dla połączeń (czyli specyficznych dla protokołu), takich jak zapis do pliku, należy otworzyć sesję, a następnie otworzyć określony rodzaj połączenia, a następnie użyć tego połączenia, aby otworzyć plik w żądanym trybie. Zobacz `CInternetConnection` , aby uzyskać więcej informacji o funkcjach specyficznych dla połączeń.

## <a name="operator_hinternet"></a>CInternetSession:: operator HINTERNET

Użyj tego operatora, aby uzyskać uchwyt systemu Windows dla bieżącej sesji internetowej.

```cpp
operator HINTERNET() const;
```

## <a name="setcookie"></a>CInternetSession:: setcookas

Ustawia plik cookie dla podanego adresu URL.

```cpp
static BOOL SetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPCTSTR pstrCookieData);
```

### <a name="parameters"></a>Parametry

*pstrUrl*<br/>
Wskaźnik do ciągu zakończenia o wartości null, który określa adres URL, dla którego powinien zostać ustawiony plik cookie.

*pstrCookieName*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku cookie.

*pstrCookieData*<br/>
Wskaźnik do ciągu zawierającego rzeczywiste dane ciągu do skojarzenia z adresem URL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli powodzenie, lub FALSE w przeciwnym razie. Aby uzyskać określony kod błędu, wywołaj`GetLastError.`

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [InternetSetCookie](/windows/win32/api/wininet/nf-wininet-internetsetcookiew), zgodnie z opisem w Windows SDK.

## <a name="setoption"></a>CInternetSession:: SetOption

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
Opcja internetowa, która ma zostać ustawiona. Zobacz [flagi opcji](/windows/win32/WinInet/option-flags) w systemie Windows SDKfor listę możliwych opcji.

*lpBuffer*<br/>
Bufor zawierający ustawienie opcji.

*dwBufferLength*<br/>
Długość elementu *lpBuffer* lub rozmiaru *dwValue*.

*dwValue*<br/>
Wartość typu DWORD, która zawiera ustawienie opcji.

*flagiDW*<br/>
Wskazuje różne opcje buforowania. Wartość domyślna to 0. Możliwe wartości to:

- INTERNET_FLAG_DONT_CACHE nie buforuje danych lokalnie ani na żadnym serwerze bramy.

- Operacje pobierania INTERNET_FLAG_OFFLINE są spełnione tylko w trwałej pamięci podręcznej. Jeśli element nie istnieje w pamięci podręcznej, zwracany jest odpowiedni kod błędu. Ta flaga może być łączona z operatorem bitowym **&#124;** lub ().

### <a name="return-value"></a>Wartość zwracana

Jeśli operacja zakończyła się pomyślnie, zwracana jest wartość TRUE. Jeśli wystąpi błąd, zwracana jest wartość FALSE. Jeśli wywołanie nie powiedzie się, może zostać wywołana [wartość GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) funkcji Win32, aby określić przyczynę błędu.

## <a name="see-also"></a>Zobacz także

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Klasa CHttpConnection](../../mfc/reference/chttpconnection-class.md)<br/>
[Klasa CFtpConnection](../../mfc/reference/cftpconnection-class.md)<br/>
[Klasa CGopherConnection](../../mfc/reference/cgopherconnection-class.md)
