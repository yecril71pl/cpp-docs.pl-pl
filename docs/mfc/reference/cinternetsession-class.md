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
ms.openlocfilehash: ddd7ca6676805e6de1b7afb5ebc77733701dfef9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372378"
---
# <a name="cinternetsession-class"></a>Klasa CInternetSession

Tworzy i inicjuje jedną lub kilka jednoczesnych sesji internetowych i, jeśli to konieczne, opisuje połączenie z serwerem proxy.

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
|[CInternetSesja::Zamknij](#close)|Zamyka połączenie internetowe po zakończeniu sesji internetowej.|
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|Ustanawia procedurę wywołania zwrotnego stanu.|
|[CInternetSesja::GetContext](#getcontext)|Zamyka połączenie internetowe po zakończeniu sesji internetowej.|
|[CInternetSession::GetCookie](#getcookie)|Zwraca pliki cookie dla określonego adresu URL i wszystkich nadrzędnych adresów URL.|
|[CInternetSession::GetCookieLength](#getcookielength)|Pobiera zmienną określającą długość pliku cookie przechowywanego w buforze.|
|[Cinternetsession::getftpconnection](#getftpconnection)|Otwiera sesję FTP z serwerem. Loguje się do użytkownika.|
|[CInternetSession::GetGopherConnection](#getgopherconnection)|Otwiera serwer gopher dla aplikacji, która próbuje otworzyć połączenie.|
|[CInternetSession::GetHttpConnection](#gethttpconnection)|Otwiera serwer HTTP dla aplikacji, która próbuje otworzyć połączenie.|
|[CInternetSession::OnStatusCallback](#onstatuscallback)|Aktualizuje stan operacji, gdy wywołanie zwrotne stanu jest włączone.|
|[CInternetSesja::OpenURL](#openurl)|Analizuje i otwiera adres URL.|
|[CInternetSession::SetCookie](#setcookie)|Ustawia plik cookie dla określonego adresu URL.|
|[CInternetSession::SetOption](#setoption)|Ustawia opcje sesji internetowej.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInternetSession::operator HINTERNET](#operator_hinternet)|Dojście do bieżącej sesji internetowej.|

## <a name="remarks"></a>Uwagi

Jeśli połączenie internetowe musi być utrzymywane przez cały czas `CInternetSession` trwania aplikacji, można utworzyć członka klasy [CWinApp](../../mfc/reference/cwinapp-class.md).

Po ustanowieniu sesji internetowej można wywołać [openurl](#openurl). `CInternetSession`następnie analizuje adres URL, wywołując funkcję globalną [AfxParseURL](internet-url-parsing-globals.md#afxparseurl). Niezależnie od typu protokołu, `CInternetSession` interpretuje adres URL i zarządza nim za Ciebie. Może obsługiwać żądania dla plików lokalnych identyfikowanych za pomocą zasobu URL "file://". `OpenURL`zwróci wskaźnik do [obiektu CStdioFile,](../../mfc/reference/cstdiofile-class.md) jeśli podają go nazwa jest plikiem lokalnym.

Jeśli otworzysz adres URL na `OpenURL`serwerze internetowym przy użyciu programu , możesz odczytać informacje z witryny. Jeśli chcesz wykonać akcje specyficzne dla usługi (na przykład HTTP, FTP lub gopher) na plikach znajdujących się na serwerze, należy ustanowić odpowiednie połączenie z tym serwerem. Aby otworzyć określony rodzaj połączenia bezpośrednio z określoną usługą, należy użyć jednej z następujących funkcji członkowskich:

- [GetGopherConnection,](#getgopherconnection) aby otworzyć połączenie z usługą gopher.

- [Pobierz usługęHttpConnection,](#gethttpconnection) aby otworzyć połączenie z usługą HTTP.

- [GetFtpConnection,](#getftpconnection) aby otworzyć połączenie z usługą FTP.

[SetOption](#setoption) umożliwia ustawienie opcji kwerendy sesji, takich jak limit czasu, liczba ponownych prób i tak dalej.

`CInternetSession`funkcje członkowskie [SetCookie](#setcookie), [GetCookie](#getcookie)i [GetCookieLength](#getcookielength) zapewniają środki do zarządzania bazą danych plików cookie Win32, za pośrednictwem której serwery i skrypty przechowują informacje o stanie stacji roboczej klienta.

Aby uzyskać więcej informacji na temat podstawowych zadań programowania internetowego, zobacz artykuł [Pierwsze kroki internetowe: WinInet](../../mfc/wininet-basics.md). Aby uzyskać ogólne informacje na temat korzystania z klas MFC WinInet, zobacz artykuł [Programowanie internetowe z WinInet](../../mfc/win32-internet-extensions-wininet.md).

> [!NOTE]
> `CInternetSession`zrzuci [AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception) dla nieobsługiwał typy usług. Obecnie obsługiwane są tylko następujące typy usług: FTP, HTTP, gopher i file.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`CInternetSession`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

## <a name="cinternetsessioncinternetsession"></a><a name="cinternetsession"></a>CInternetSession::CInternetSession

Ta funkcja elementu członkowskiego `CInternetSession` jest wywoływana podczas tworzenia obiektu.

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

*pstrAgent (pstrAgent)*<br/>
Wskaźnik do ciągu, który identyfikuje nazwę aplikacji lub jednostki wywołującej funkcje internetowe (na przykład "Przeglądarka internetowa firmy Microsoft"). Jeśli *pstrAgent* ma wartość NULL (wartość domyślna), struktura wywołuje globalną funkcję [AfxGetAppName](application-information-and-management.md#afxgetappname), która zwraca ciąg zakończony zerem zawierający nazwę aplikacji. Niektóre protokoły używają tego ciągu do identyfikowania aplikacji na serwerze.

*Dwcontext*<br/>
Identyfikator kontekstu dla operacji. *dwContext* identyfikuje informacje o stanie operacji zwrócone przez [CInternetSession::OnStatusCallback](#onstatuscallback). Wartość domyślna jest ustawiona na 1; jednak można jawnie przypisać identyfikator określonego kontekstu dla operacji. Obiekt i wszelkie prace, które wykonuje, będą skojarzone z tym identyfikatorem kontekstu.

*dwAccessType*<br/>
Wymagany typ dostępu. Są to prawidłowe wartości, z których dokładnie jedna może być dostarczona:

- INTERNET_OPEN_TYPE_PRECONFIG połącz przy użyciu wstępnie skonfigurowanych ustawień w rejestrze. Ten typ dostępu jest ustawiony jako domyślny. Aby połączyć się za pośrednictwem serwera proxy TIS, ustaw *dwAccessType* do tej wartości; następnie ustaw rejestr odpowiednio.

- INTERNET_OPEN_TYPE_DIRECT Połącz się bezpośrednio z Internetem.

- INTERNET_OPEN_TYPE_PROXY Połącz się za pośrednictwem serwera proxy CERN.

Aby uzyskać informacje na temat łączenia się z różnymi typami serwerów proxy, zobacz [Kroki typowej aplikacji klienckiej FTP](../../mfc/steps-in-a-typical-ftp-client-application.md).

*pstrProxyName*<br/>
Nazwa preferowanego serwera proxy CERN, jeśli *dwAccessType* jest ustawiona jako INTERNET_OPEN_TYPE_PROXY. Wartość domyślna to NULL.

*pstrProxyBypass*<br/>
Wskaźnik do ciągu zawierający opcjonalną listę adresów serwera. Adresy te mogą być pomijane podczas korzystania z dostępu do serwera proxy. Jeśli podano wartość NULL, lista pomijania zostanie odczytana z rejestru. Ten parametr ma znaczenie tylko wtedy, *gdy dwAccessType* jest ustawiony na INTERNET_OPEN_TYPE_PROXY.

*Dwflags*<br/>
Wskazuje różne opcje buforowania. Wartość domyślna jest ustawiona na 0. Dopuszczalne wartości to:

- INTERNET_FLAG_DONT_CACHE Nie buforuj danych lokalnie ani na serwerach bramy.

- INTERNET_FLAG_OFFLINE Operacje pobierania są spełnione tylko za pośrednictwem trwałej pamięci podręcznej. Jeśli element nie istnieje w pamięci podręcznej, zwracany jest odpowiedni kod błędu. Ta flaga może być połączona z operatorem **bitowy OR** **(&#124;). **

### <a name="remarks"></a>Uwagi

`CInternetSession`jest pierwszą funkcją internetową wywoływaną przez aplikację. Inicjuje wewnętrzne struktury danych i przygotowuje się do przyszłych wywołań z aplikacji.

Jeśli nie można otworzyć `CInternetSession` połączenia z Internetem, rzuca [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception).

### <a name="example"></a>Przykład

Zobacz przykład [cFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="cinternetsessionclose"></a><a name="close"></a>CInternetSesja::Zamknij

Wywołanie tej funkcji elementu członkowskiego `CInternetSession` po zakończeniu aplikacji przy użyciu obiektu.

```cpp
virtual void Close();
```

### <a name="example"></a>Przykład

Zobacz przykład [cFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="cinternetsessionenablestatuscallback"></a><a name="enablestatuscallback"></a>CInternetSession::EnableStatusCallback

Wywołanie tej funkcji elementu członkowskiego, aby włączyć wywołanie zwrotne stanu.

```cpp
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
Określa, czy wywołanie zwrotne jest włączone, czy wyłączone. Wartość domyślna to PRAWDA.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, należy określić przyczynę błędu, badając zgłoszony [obiekt CInternetException.](../../mfc/reference/cinternetexception-class.md)

### <a name="remarks"></a>Uwagi

Podczas obsługi wywołania zwrotnego stanu, można podać stan o postępie operacji (takich jak rozpoznawanie nazwy, łączenie się z serwerem i tak dalej) na pasku stanu aplikacji. Wyświetlanie stanu operacji jest szczególnie pożądane podczas długotrwałej pracy.

Ponieważ wywołania zwrotne występują podczas przetwarzania żądania, aplikacja powinna poświęcić jak najmniej czasu w wywołaniu zwrotnym, aby zapobiec degradacji przepływności danych do sieci. Na przykład umieszczenie okna dialogowego w wywołaniu zwrotnym może być tak długa operacja, że serwer kończy żądanie.

Nie można usunąć wywołania zwrotnego stanu, o ile oczekują na żadne wywołania zwrotne.

Aby obsłużyć wszelkie operacje asynchronicznie, należy utworzyć własny wątek lub użyć funkcji WinInet bez MFC.

## <a name="cinternetsessiongetcontext"></a><a name="getcontext"></a>CInternetSesja::GetContext

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać wartość kontekstu dla określonej sesji aplikacji.

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator kontekstu zdefiniowany przez aplikację.

### <a name="remarks"></a>Uwagi

[OnStatusCallback](#onstatuscallback) używa identyfikatora kontekstu `GetContext` zwróconego przez do raportowania stanu określonej aplikacji. Na przykład gdy użytkownik aktywuje żądanie internetowe, które obejmuje zwracanie informacji o stanie, wywołania zwrotnego stanu używa identyfikatora kontekstu do raportowania stanu dla tego konkretnego żądania. Jeśli użytkownik aktywuje dwa oddzielne żądania internetowe, które `OnStatusCallback` obejmują zwracanie informacji o stanie, używa identyfikatorów kontekstu do zwrócenia stanu odpowiadających im żądań. W związku z tym identyfikator kontekstu jest używany dla wszystkich operacji wywołania zwrotnego stanu i jest skojarzony z sesją do zakończenia sesji.

Aby uzyskać więcej informacji na temat operacji asynchronicznych, zobacz artykuł [Pierwsze kroki internetowe: WinInet](../../mfc/wininet-basics.md).

## <a name="cinternetsessiongetcookie"></a><a name="getcookie"></a>CInternetSession::GetCookie

Ta funkcja elementu członkowskiego implementuje zachowanie funkcji Win32 [InternetGetCookie](/windows/win32/api/wininet/nf-wininet-internetgetcookiew), zgodnie z opisem w windows SDK.

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

*pstrUrl (pstrUrl)*<br/>
Wskaźnik do ciągu zawierającego adres URL.

*pstrCookieName*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku cookie, aby uzyskać dla określonego adresu URL.

*pstrCookieData*<br/>
W pierwszym przeciążeniu wskaźnik do ciągu zawierającego adres buforu, który odbiera dane cookie. Ta wartość może być null. W drugim przeciążenie, odwołanie do [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiektu do odbierania danych cookie.

*dwBufLen (Niem.*<br/>
Zmienna określająca rozmiar buforu *pstrCookieData.* Jeśli funkcja powiedzie się, bufor odbiera ilość danych skopiowanych do buforu *pstrCookieData.* Jeśli *pstrCookieData* ma wartość NULL, ten parametr otrzymuje wartość, która określa rozmiar buforu niezbędnego do skopiowania wszystkich danych cookie.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli zakończy się pomyślnie lub FAŁSZ w inny sposób. Jeśli wywołanie nie powiedzie się, wywołać funkcję Win32 [GetLastError,](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aby ustalić przyczynę błędu. Obowiązują następujące wartości błędów:

- ERROR_NO_MORE_ITEMS Nie ma pliku cookie dla określonego adresu URL i wszystkich jego wiązek.

- ERROR_INSUFFICIENT_BUFFER Wartość przekazana w *dwBufLen* jest niewystarczająca do skopiowania wszystkich danych cookie. Wartość zwracana w *dwBufLen* jest rozmiar buforu niezbędne do uzyskania wszystkich danych.

### <a name="remarks"></a>Uwagi

W drugim przeciążeniu MFC pobiera dane cookie `CString` do dostarczonego obiektu.

## <a name="cinternetsessiongetcookielength"></a><a name="getcookielength"></a>CInternetSession::GetCookieLength

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać długość pliku cookie przechowywane w buforze.

```cpp
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName);
```

### <a name="parameters"></a>Parametry

*pstrUrl (pstrUrl)*<br/>
Wskaźnik do ciągu zawierającego adres URL

*pstrCookieName*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku cookie.

### <a name="return-value"></a>Wartość zwracana

Wartość DWORD wskazująca długość pliku cookie, przechowywane w buforze. Zero, jeśli nie istnieje plik cookie o nazwie wskazanej przez *pstrCookieName.*

### <a name="remarks"></a>Uwagi

Ta wartość jest używana przez [GetCookie](#getcookie).

## <a name="cinternetsessiongetftpconnection"></a><a name="getftpconnection"></a>Cinternetsession::getftpconnection

Wywołanie tej funkcji elementu członkowskiego, aby ustanowić `CFtpConnection` połączenie FTP i uzyskać wskaźnik do obiektu.

```cpp
CFtpConnection* GetFtpConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    BOOL bPassive = FALSE);
```

### <a name="parameters"></a>Parametry

*pstrServer (serwer pstrServer)*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera FTP.

*pstrUserName*<br/>
Wskaźnik do ciągu zakończonego zerem, który określa nazwę użytkownika do logowania. Jeśli null, wartość domyślna jest anonimowa.

*pstr Hasło*<br/>
Wskaźnik do ciągu zakończonego wartością null, który określa hasło używane do logowania. Jeśli zarówno *pstrPassword,* jak i *pstrUserName* mają wartość NULL, domyślnym anonimowym hasłem jest nazwa e-mail użytkownika. Jeśli *pstrPassword* ma wartość NULL (lub pusty ciąg), ale *pstrUserName* nie ma wartości NULL, używane jest puste hasło. W poniższej tabeli opisano zachowanie czterech możliwych ustawień *pstrUserName* i *pstrPassword*:

| *pstrUserName*  | *pstr Hasło*  | Nazwa użytkownika wysłana do serwera FTP | Hasło wysłane do serwera FTP |
|-----------------|-----------------|-----------------------------|-----------------------------|
|   NULL lub " " "   |   NULL lub " " "   |         "anonimowy"         |      Nazwa e-mail użytkownika      |
| Ciąg nienawiązany |   NULL lub " " "   |       *pstrUserName*        |             " "             |
|      NULL       | Ciąg nienawiązany |            BŁĄD            |            BŁĄD            |
| Ciąg nienawiązany | Ciąg nienawiązany |       *pstrUserName*        |       *pstr Hasło*        |

*Nport*<br/>
Liczba identyfikująca port TCP/IP do użycia na serwerze.

*bPasażerka*<br/>
Określa tryb pasywny lub aktywny dla tej sesji FTP. Jeśli ustawiona wartość TRUE, ustawi `dwFlag` interfejs API Win32 na INTERNET_FLAG_PASSIVE.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [CFtpConnection.](../../mfc/reference/cftpconnection-class.md) Jeśli wywołanie nie powiedzie się, należy określić przyczynę błędu, badając zgłoszony [obiekt CInternetException.](../../mfc/reference/cinternetexception-class.md)

### <a name="remarks"></a>Uwagi

`GetFtpConnection`łączy się z serwerem FTP oraz tworzy `CFTPConnection` i zwraca wskaźnik do obiektu. Nie wykonuje żadnej określonej operacji na serwerze. Jeśli zamierzasz odczytać lub zapisać do plików, na przykład, należy wykonać te operacje jako oddzielne kroki. Zobacz klasy [CFtpConnection](../../mfc/reference/cftpconnection-class.md) i [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) informacje na temat wyszukiwania plików, otwierania plików oraz odczytu lub zapisywania do plików. Zobacz artykuł [Programowanie internetowe z wininet,](../../mfc/win32-internet-extensions-wininet.md) aby uzyskać instrukcje wykonywania typowych zadań połączenia FTP.

### <a name="example"></a>Przykład

Zobacz przykład [cFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="cinternetsessiongetgopherconnection"></a><a name="getgopherconnection"></a>CInternetSession::GetGopherConnection

Wywołanie tej funkcji elementu członkowskiego, aby ustanowić `CGopherConnection` nowe połączenie gopher i uzyskać wskaźnik do obiektu.

```cpp
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>Parametry

*pstrServer (serwer pstrServer)*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera gopher.

*pstrUserName*<br/>
Wskaźnik do ciągu zawierającego nazwę użytkownika.

*pstr Hasło*<br/>
Wskaźnik do ciągu zawierającego hasło dostępu.

*Nport*<br/>
Liczba identyfikująca port TCP/IP do użycia na serwerze.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [obiektu CGopherConnection.](../../mfc/reference/cgopherconnection-class.md) Jeśli wywołanie nie powiedzie się, należy określić przyczynę błędu, badając zgłoszony [obiekt CInternetException.](../../mfc/reference/cinternetexception-class.md)

### <a name="remarks"></a>Uwagi

`GetGopherConnection`łączy się z serwerem gopher i tworzy `CGopherConnection` i zwraca wskaźnik do obiektu. Nie wykonuje żadnej określonej operacji na serwerze. Jeśli zamierzasz odczytać lub zapisać dane, na przykład, należy wykonać te operacje jako oddzielne kroki. Zobacz klasy [CGopherConnection](../../mfc/reference/cgopherconnection-class.md), [CGopherFile](../../mfc/reference/cgopherfile-class.md)i [CGopherFileFind,](../../mfc/reference/cgopherfilefind-class.md) aby uzyskać informacje na temat wyszukiwania plików, otwierania plików oraz odczytu lub zapisywania do plików. Aby uzyskać informacje na temat przeglądania witryny FTP, zobacz funkcję członkowzoną [OpenURL](#openurl). Zobacz artykuł [Programowanie internetowe z wininet](../../mfc/win32-internet-extensions-wininet.md) kroki w wykonywaniu typowych zadań połączenia gopher.

## <a name="cinternetsessiongethttpconnection"></a><a name="gethttpconnection"></a>CInternetSession::GetHttpConnection

Wywołanie tej funkcji elementu członkowskiego, aby ustanowić połączenie HTTP i uzyskać wskaźnik do `CHttpConnection` obiektu.

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

*pstrServer (serwer pstrServer)*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera HTTP.

*Nport*<br/>
Liczba identyfikująca port TCP/IP do użycia na serwerze.

*pstrUserName*<br/>
Wskaźnik do ciągu zawierającego nazwę użytkownika.

*pstr Hasło*<br/>
Wskaźnik do ciągu zawierającego hasło dostępu.

*Dwflags*<br/>
Dowolna `INTERNET_FLAG_*` kombinacja flag. Zobacz tabelę w sekcji **Uwagi** [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) opis wartości *dwFlags.*

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [CHttpConnection.](../../mfc/reference/chttpconnection-class.md) Jeśli wywołanie nie powiedzie się, należy określić przyczynę błędu, badając zgłoszony [obiekt CInternetException.](../../mfc/reference/cinternetexception-class.md)

### <a name="remarks"></a>Uwagi

`GetHttpConnection`łączy się z serwerem HTTP oraz tworzy `CHttpConnection` i zwraca wskaźnik do obiektu. Nie wykonuje żadnej określonej operacji na serwerze. Jeśli zamierzasz zbadać nagłówek HTTP, na przykład, należy wykonać tę operację jako osobny krok. Informacje o operacjach, które można wykonać przy użyciu połączenia z serwerem HTTP, można znaleźć w klasach [CHttpConnection](../../mfc/reference/chttpconnection-class.md) i [CHttpFile.](../../mfc/reference/chttpfile-class.md) Aby uzyskać informacje dotyczące przeglądania witryny HTTP, zobacz funkcję członkowną [OpenURL](#openurl). Zobacz artykuł [Programowanie internetowe z wininet,](../../mfc/win32-internet-extensions-wininet.md) aby uzyskać instrukcje wykonywania typowych zadań połączenia HTTP.

## <a name="cinternetsessiononstatuscallback"></a><a name="onstatuscallback"></a>CInternetSession::OnStatusCallback

Ta funkcja elementu członkowskiego jest wywoływana przez platformę, aby zaktualizować stan, gdy wywołanie zwrotne stanu jest włączone i operacja jest w toku.

```cpp
virtual void OnStatusCallback(
    DWORD_PTR dwContext,
    DWORD dwInternetStatus,
    LPVOID lpvStatusInformation,
    DWORD dwStatusInformationLength);
```

### <a name="parameters"></a>Parametry

*Dwcontext*<br/>
Wartość kontekstu dostarczona przez aplikację.

*dwSostałostałostał*<br/>
Kod stanu, który wskazuje, dlaczego jest dokonywane wywołanie zwrotne. Zobacz **Uwagi** dla tabeli możliwych wartości.

*lpvStatusInformation*<br/>
Wskaźnik do buforu zawierającego informacje istotne dla tego wywołania zwrotnego.

*dwStatusInformationLength*<br/>
Rozmiar *lpvStatusInformation*.

### <a name="remarks"></a>Uwagi

Należy najpierw [wywołać EnableStatusCallback,](#enablestatuscallback) aby skorzystać z wywołania zwrotnego stanu.

Parametr *dwInternetStatus* wskazuje na wykonywane działanie i określa, jaka będzie zawartość *informacji lpvStatusInformation.* *dwStatusInformationLength* wskazuje długość danych zawartych w *lpvStatusInformation*. Następujące wartości stanu *dwInternetStatus* są zdefiniowane w następujący sposób:

|Wartość|Znaczenie|
|-----------|-------------|
|INTERNET_STATUS_RESOLVING_NAME|Wyszukując adres IP nazwy zawartej w *lpvStatusInformation*.|
|INTERNET_STATUS_NAME_RESOLVED|Pomyślnie znaleziono adres IP nazwy zawartej w *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTING_TO_SERVER|Podłączanie do adresu gniazda ([SOCKADDR](/windows/win32/winsock/sockaddr-2)) wskazane przez *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTED_TO_SERVER|Pomyślnie podłączony do adresu gniazda (SOCKADDR) wskazany przez *lpvStatusInformation*.|
|INTERNET_STATUS_SENDING_REQUEST|Wysyłanie żądania informacji do serwera. Parametrem *lpvStatusInformation* jest NULL.|
|INTERNET_STATUS_ REQUEST_SENT|Pomyślnie wysłano żądanie informacji do serwera. Parametrem *lpvStatusInformation* jest NULL.|
|INTERNET_STATUS_RECEIVING_RESPONSE|Oczekiwanie na serwer, aby odpowiedzieć na żądanie. Parametrem *lpvStatusInformation* jest NULL.|
|INTERNET_STATUS_RESPONSE_RECEIVED|Pomyślnie odebrano odpowiedź z serwera. Parametrem *lpvStatusInformation* jest NULL.|
|INTERNET_STATUS_CLOSING_CONNECTION|Zamknięcie połączenia z serwerem. Parametrem *lpvStatusInformation* jest NULL.|
|INTERNET_STATUS_CONNECTION_CLOSED|Pomyślnie zamknięto połączenie z serwerem. Parametrem *lpvStatusInformation* jest NULL.|
|INTERNET_STATUS_HANDLE_CREATED|Używany przez funkcję Interfejsu API Win32 [InternetConnect,](/windows/win32/api/wininet/nf-wininet-internetconnectw) aby wskazać, że utworzono nowy uchwyt. Dzięki temu aplikacja wywołać funkcję Win32 [InternetCloseHandle](/windows/win32/api/wininet/nf-wininet-internetclosehandle) z innego wątku, jeśli połączenie trwa zbyt długo. Zobacz SDK systemu Windows, aby uzyskać więcej informacji na temat tych funkcji.|
|INTERNET_STATUS_HANDLE_CLOSING|Pomyślnie zakończona ta wartość dojścia.|

Zastąpuj tę funkcję elementu członkowskiego, aby wymagać pewnych akcji przed wykonaniem procedury wywołania zwrotnego stanu.

> [!NOTE]
> Wywołania zwrotne stanu wymagają ochrony stanu wątku. Jeśli używasz MFC w bibliotece udostępnionej, dodaj następujący wiersz na początku zastąpienia:

[!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]

Aby uzyskać więcej informacji na temat operacji asynchronicznych, zobacz artykuł [Pierwsze kroki internetowe: WinInet](../../mfc/wininet-basics.md).

## <a name="cinternetsessionopenurl"></a><a name="openurl"></a>CInternetSesja::OpenURL

Wywołanie tej funkcji elementu członkowskiego, aby wysłać określone żądanie do serwera HTTP i zezwolić klientowi na określenie dodatkowych nagłówków RFC822, MIME lub HTTP do wysłania wraz z żądaniem.

```cpp
CStdioFile* OpenURL(
    LPCTSTR pstrURL,
    DWORD_PTR dwContext = 1,
    DWORD dwFlags = INTERNET_FLAG_TRANSFER_ASCII,
    LPCTSTR pstrHeaders = NULL,
    DWORD dwHeadersLength = 0);
```

### <a name="parameters"></a>Parametry

*pstrURL (pstrURL)*<br/>
Wskaźnik do nazwy adresu URL, aby rozpocząć czytanie. Obsługiwane są tylko adresy URL rozpoczynające się od pliku:, ftp:, gopher:, lub http:. Potwierdza, jeśli *pstrURL* ma wartość NULL.

*Dwcontext*<br/>
Wartość zdefiniowana przez aplikację przekazana z zwróconym dojściem w wywołaniu zwrotnym.

*Dwflags*<br/>
Flagi opisujące sposób obsługi tego połączenia. Zobacz **Uwagi, aby** uzyskać więcej informacji na temat prawidłowych flag. Prawidłowe flagi to:

- INTERNET_FLAG_TRANSFER_ASCII Wartość domyślna. Przenieś plik jako tekst ASCII.

- INTERNET_FLAG_TRANSFER_BINARY Przenieś plik jako plik binarny.

- INTERNET_FLAG_RELOAD Pobierz dane z przewodu, nawet jeśli jest on buforowany lokalnie.

- INTERNET_FLAG_DONT_CACHE Nie buforuj danych lokalnie ani w żadnych bramkach.

- INTERNET_FLAG_SECURE Ta flaga ma zastosowanie tylko do żądań HTTP. Żąda bezpiecznych transakcji w sieci za pomocą secure sockets layer lub PCT.

- INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT Jeśli to możliwe, ponownie użyć istniejących połączeń z serwerem `OpenUrl` dla nowych żądań generowanych przez zamiast tworzenia nowej sesji dla każdego żądania połączenia.

- INTERNET_FLAG_PASSIVE Używane w witrynie FTP. Używa pasywnej semantyki FTP. Używany z [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) . `OpenURL`

*pstrHeaders (głowice)*<br/>
Wskaźnik do ciągu zawierającego nagłówki, które mają być wysyłane do serwera HTTP.

*dwHeadersLength*<br/>
Długość dodatkowych nagłówków w znakach. Jeśli jest to -1L i *pstrHeaders* jest non-NULL, a następnie *pstrHeaders* zakłada się zero zakończone i długość jest obliczana.

### <a name="return-value"></a>Wartość zwracana

Zwraca dojście do plików tylko dla usług internetowych TYPU FTP, GOPHER, HTTP i FILE. Zwraca wartość NULL, jeśli analizowanie zakończyło się niepowodzeniem.

Wskaźnik, `OpenURL` który zwraca zależy od *pstrURL*'s typu usługi. Poniższa tabela przedstawia możliwe `OpenURL` wskaźniki mogą powrócić.

|Typ adresu URL|Zwraca|
|--------------|-------------|
|`file://`|`CStdioFile*`|
|`http://`|`CHttpFile*`|
|`gopher://`|`CGopherFile*`|
|`ftp://`|`CInternetFile*`|

### <a name="remarks"></a>Uwagi

Parametr *dwFlags* musi zawierać INTERNET_FLAG_TRANSFER_ASCII lub INTERNET_FLAG_TRANSFER_BINARY, ale nie oba. Pozostałe flagi można łączyć z operatorem **or** bitowego **(&#124;**).

`OpenURL`, który zawija funkcję `InternetOpenURL`Win32, umożliwia tylko pobieranie, pobieranie i odczytywanie danych z serwera internetowego. `OpenURL`nie pozwala na manipulowanie plikami w lokalizacji zdalnej, więc nie wymaga [obiektu CInternetConnection.](../../mfc/reference/cinternetconnection-class.md)

Aby użyć funkcji specyficznych dla połączenia (czyli specyficznych dla protokołu), takich jak zapisywanie do pliku, należy otworzyć sesję, a następnie otworzyć określony rodzaj połączenia, a następnie użyć tego połączenia, aby otworzyć plik w żądanym trybie. Zobacz `CInternetConnection` więcej informacji na temat funkcji specyficznych dla połączenia.

## <a name="cinternetsessionoperator-hinternet"></a><a name="operator_hinternet"></a>CInternetSession::operator HINTERNET

Ten operator służy do obsługi systemu Windows dla bieżącej sesji internetowej.

```cpp
operator HINTERNET() const;
```

## <a name="cinternetsessionsetcookie"></a><a name="setcookie"></a>CInternetSession::SetCookie

Ustawia plik cookie dla określonego adresu URL.

```cpp
static BOOL SetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPCTSTR pstrCookieData);
```

### <a name="parameters"></a>Parametry

*pstrUrl (pstrUrl)*<br/>
Wskaźnik do ciągu zakończonego zerem, który określa adres URL, dla którego należy ustawić plik cookie.

*pstrCookieName*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku cookie.

*pstrCookieData*<br/>
Wskaźnik do ciągu zawierającego rzeczywiste dane ciągu do skojarzenia z adresem URL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli zakończy się pomyślnie lub FAŁSZ w inny sposób. Aby uzyskać określony kod błędu, zadzwoń`GetLastError.`

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [InternetSetCookie](/windows/win32/api/wininet/nf-wininet-internetsetcookiew), zgodnie z opisem w zestawie Windows SDK.

## <a name="cinternetsessionsetoption"></a><a name="setoption"></a>CInternetSession::SetOption

Wywołanie tej funkcji elementu członkowskiego, aby ustawić opcje sesji internetowej.

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

*Dwoption*<br/>
Opcja Internet, aby ustawić. Zobacz [Flagi opcji](/windows/win32/WinInet/option-flags) na zestawie Windows SDKdfor listę możliwych opcji.

*lpBuffer (lpBuffer)*<br/>
Bufor zawierający ustawienie opcji.

*dwBufferLength*<br/>
Długość *lpBuffer* lub rozmiar *dwValue*.

*dwValue (Wartość dwValue)*<br/>
A DWORD, który zawiera ustawienie opcji.

*Dwflags*<br/>
Wskazuje różne opcje buforowania. Wartość domyślna jest ustawiona na 0. Dopuszczalne wartości to:

- INTERNET_FLAG_DONT_CACHE Nie buforuj danych lokalnie ani na serwerach bramy.

- INTERNET_FLAG_OFFLINE Operacje pobierania są spełnione tylko za pośrednictwem trwałej pamięci podręcznej. Jeśli element nie istnieje w pamięci podręcznej, zwracany jest odpowiedni kod błędu. Ta flaga może być połączona z operatorem **bitowy OR** **(&#124;). **

### <a name="return-value"></a>Wartość zwracana

Jeśli operacja zakończyła się pomyślnie, zwracana jest wartość TRUE. Jeśli wystąpił błąd, zwracana jest wartość FALSE. Jeśli wywołanie nie powiedzie się, funkcja Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) może zostać wywołana w celu ustalenia przyczyny błędu.

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Klasa CHttpConnection](../../mfc/reference/chttpconnection-class.md)<br/>
[Klasa CFtpConnection](../../mfc/reference/cftpconnection-class.md)<br/>
[Klasa CGopherConnection](../../mfc/reference/cgopherconnection-class.md)
