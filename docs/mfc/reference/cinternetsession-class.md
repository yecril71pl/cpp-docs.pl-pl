---
title: Klasa CInternetSession | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e7aad2f6ce26fd5ca9ed0ec323a8fcb05ac17f7c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cinternetsession-class"></a>Klasa CInternetSession
Tworzy i inicjuje jedną lub kilka jednoczesnych sesji internetowej i, jeśli to konieczne, w tym artykule opisano połączenie z serwerem proxy.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|[CInternetSession::Close](#close)|Zamyka połączenie internetowe, gdy Internet sesja zostanie zakończona.|  
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|Ustanawia procedura wywołania zwrotnego stanu.|  
|[CInternetSession::GetContext](#getcontext)|Zamyka połączenie internetowe, gdy Internet sesja zostanie zakończona.|  
|[CInternetSession::GetCookie](#getcookie)|Zwraca pliki cookie dla określonego adresu URL i jego elementu nadrzędnego adresów URL.|  
|[CInternetSession::GetCookieLength](#getcookielength)|Pobiera zmienną długość plik cookie przechowywany w buforze.|  
|[CInternetSession::GetFtpConnection](#getftpconnection)|Otwiera sesji FTP z serwerem. Loguje użytkownika.|  
|[CInternetSession::GetGopherConnection](#getgopherconnection)|Otwiera serwer gopher dla aplikacji, która podejmuje próbę otwarcia połączenia.|  
|[CInternetSession::GetHttpConnection](#gethttpconnection)|Otwiera serwera HTTP dla aplikacji, która podejmuje próbę otwarcia połączenia.|  
|[CInternetSession::OnStatusCallback](#onstatuscallback)|Aktualizuje stan operacji, gdy wywołanie zwrotne dla stanu jest włączone.|  
|[CInternetSession::OpenURL](#openurl)|Analizuje i otwiera adres URL.|  
|[CInternetSession::SetCookie](#setcookie)|Ustawia plik cookie dla określonego adresu URL.|  
|[CInternetSession::SetOption](#setoption)|Ustawia opcje dla sesji internetowej.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CInternetSession::operator HINTERNET](#operator_hinternet)|Dojście do bieżącej sesji Internet.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli połączenie z Internetem muszą zostać zachowane na czas trwania aplikacji, można utworzyć `CInternetSession` elementu członkowskiego klasy [CWinApp](../../mfc/reference/cwinapp-class.md).  
  
 Po ustanowieniu sesji internetowej, należy wywołać [OpenURL](#openurl). `CInternetSession`następnie analizuje adres URL dla Ciebie poprzez wywołanie funkcji globalnej [afxparseurl —](internet-url-parsing-globals.md#afxparseurl). Niezależnie od jego typ protokołu `CInternetSession` interpretuje adres URL i zarządza nim automatycznie. Może obsługiwać żądania dotyczące plików lokalnych oznaczone symbolem "file://" zasobu adresu URL. `OpenURL`Zwraca wskaźnik do [CStdioFile](../../mfc/reference/cstdiofile-class.md) obiektu, jeśli nazwa przekazujesz ją jest plikiem lokalnym.  
  
 Jeśli Otwórz adres URL na serwerze Internetu za pomocą `OpenURL`, można odczytać informacji o witrynie. Jeśli chcesz wykonać akcje specyficzne dla usługi (na przykład HTTP, FTP lub gopher) na pliki znajdujące się na serwerze, należy ustanowić odpowiedniego połączenia z tym serwerem. Aby otworzyć określonego rodzaju połączenia bezpośrednio do określonej usługi, użyj jednej z następujących funkcji Członkowskich:  
  
- [GetGopherConnection](#getgopherconnection) można otworzyć połączenia z usługą gopher.  
  
- [GetHttpConnection](#gethttpconnection) można otworzyć połączenia z usługą HTTP.  
  
- [GetFtpConnection](#getftpconnection) można otworzyć połączenia z usługą FTP.  
  
 [SetOption](#setoption) służy do ustawiania opcji zapytania sesji, takie jak wartości limitu czasu i liczby ponownych prób i tak dalej.  
  
 `CInternetSession`Funkcje Członkowskie [SetCookie](#setcookie), [GetCookie](#getcookie), i [GetCookieLength](#getcookielength) służyć do zarządzania bazą danych pliku cookie Win32, za pomocą którego Obsługa serwerów i skryptów Stan informacje o stacji roboczej klienta.  
  
 Aby uzyskać więcej informacji na temat podstawowych zadań programowania Internetu, zobacz artykuł [pierwsze kroki Internet: WinInet](../../mfc/wininet-basics.md). Aby uzyskać ogólne informacje dotyczące używania klas MFC WinInet, zobacz artykuł [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
> [!NOTE]
> `CInternetSession`zgłosi [afxthrownotsupportedexception —](exception-processing.md#afxthrownotsupportedexception) dla typów usług nieobsługiwany. Obecnie obsługiwane są tylko następujące typy usługi: FTP, HTTP gopher i plików.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CInternetSession`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxinet.h  
  
##  <a name="cinternetsession"></a>CInternetSession::CInternetSession  
 Ta funkcja członkowska jest wywoływane, gdy `CInternetSession` tworzony jest obiekt.  
  
```  
CInternetSession(
    LPCTSTR pstrAgent = NULL,  
    DWORD_PTR dwContext = 1,  
    DWORD dwAccessType = PRE_CONFIG_INTERNET_ACCESS,  
    LPCTSTR pstrProxyName = NULL,  
    LPCTSTR pstrProxyBypass = NULL,  
    DWORD dwFlags = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrAgent`  
 Wskaźnik na ciąg określający nazwę aplikacji lub jednostki wywoływanie funkcji Internet (na przykład "Microsoft przeglądarki internetowej"). Jeśli `pstrAgent` jest **NULL** (ustawienie domyślne), struktura wywołuje funkcji globalnej [afxgetappname —](application-information-and-management.md#afxgetappname), która zwraca zerem ciąg zawierający nazwę aplikacji. Niektóre protokoły użyć tego ciągu do identyfikowania aplikacji na serwerze.  
  
 `dwContext`  
 Identyfikator kontekstu dla tej operacji. `dwContext`Określa informacje o stanie operacji zwrócony przez [CInternetSession::OnStatusCallback](#onstatuscallback). Wartość domyślna jest ustawiona na 1; jednak można jawnie przypisać identyfikator kontekstu określonych dla tej operacji. Obiekt i pracę go nie będą skojarzone z tym identyfikatorem kontekstu.  
  
 `dwAccessType`  
 Typ dostępu. Poniżej przedstawiono prawidłowe wartości, można podać dokładnie jeden z nich:  
  
- **INTERNET_OPEN_TYPE_PRECONFIG** połączyć za pomocą wstępnie skonfigurowanych ustawień w rejestrze. Ten typ dostępu jest ustawiony jako domyślny. Nawiązywanie połączeń za pomocą serwera proxy TIS, ustaw `dwAccessType` tej wartości; można następnie ustawić wartość rejestru odpowiednio.  
  
- `INTERNET_OPEN_TYPE_DIRECT`Połącz bezpośrednio z Internetem.  
  
- `INTERNET_OPEN_TYPE_PROXY`Połącz za pośrednictwem serwera proxy CERN.  
  
 Aby uzyskać informacje na łączenie się z różnymi typami serwerów proxy, zobacz [kroków w typowej aplikacji klienckiej FTP](../../mfc/steps-in-a-typical-ftp-client-application.md).  
  
 *pstrProxyName*  
 Nazwę preferowanego serwera proxy CERN Jeśli `dwAccessType` jest ustawiony jako `INTERNET_OPEN_TYPE_PROXY`. Wartość domyślna to **NULL**.  
  
 *pstrProxyBypass*  
 Wskaźnik do ciąg zawierający opcjonalną listę adresów serwerów. Te adresy może pominąć, używając dostępu do serwera proxy. Jeśli **NULL** podano żadnej wartości, Lista obejść będą odczytywane z rejestru. Ten parametr ma znaczenie tylko wtedy, gdy `dwAccessType` ma ustawioną wartość `INTERNET_OPEN_TYPE_PROXY`.  
  
 `dwFlags`  
 Wskazuje różne opcje buforowania. Wartość domyślna jest równa 0. Możliwe wartości:  
  
- `INTERNET_FLAG_DONT_CACHE`Nie buforuj danych lokalnie lub w dowolne serwery bramy.  
  
- `INTERNET_FLAG_OFFLINE`Pobierz operacje są spełnione przez tylko trwałej pamięci podręcznej. Jeśli element nie istnieje w pamięci podręcznej, zostanie zwrócony kod błędu odpowiednie. Ta flaga mogą być łączone z bitowego `OR` ( **&#124;**) operatora.  
  
### <a name="remarks"></a>Uwagi  
 **CInternetSession** jest pierwszej funkcji Internet wywoływane przez aplikację. Inicjuje struktur danych wewnętrznych się i przygotowuje na potrzeby przyszłych połączeń z aplikacji.  
  
 Jeśli nie Internet można otworzyć połączenia, `CInternetSession` zgłasza [afxthrowinternetexception —](internet-url-parsing-globals.md#afxthrowinternetexception).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).  
  
##  <a name="close"></a>CInternetSession::Close  
 Wywołania funkcji członkowskiej, gdy aplikacja zakończy `CInternetSession` obiektu.  
  
```  
virtual void Close();
```  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).  
  
##  <a name="enablestatuscallback"></a>CInternetSession::EnableStatusCallback  
 Wywołanie tej funkcji elementu członkowskiego, aby włączyć stan wywołania zwrotnego.  
  
```  
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bEnable`  
 Określa, czy wywołanie zwrotne jest włączone. Wartość domyślna to **TRUE**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. Jeśli połączenie nie powiedzie się, należy określić przyczynę niepowodzenia, sprawdzając zgłoszenia [CInternetException](../../mfc/reference/cinternetexception-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Podczas obsługi stanu wywołania zwrotnego, musisz podać stanu dotyczące postępu operacji (na przykład rozpoznawania nazwy, nawiązywanie połączenia z serwerem i tak dalej), na pasku stanu aplikacji. Wyświetlanie stanu operacji jest szczególnie istotna w trakcie długoterminowej.  
  
 Ponieważ wywołania zwrotne wykonywane podczas przetwarzania żądania, aplikacji należy poświęcić czas małego, jak to możliwe w wywołanie zwrotne, aby zapobiec spadkowi przepływności danych w sieci. Na przykład umieszczania okno dialogowe w wywołaniu zwrotnym mogą być takie długotrwałej operacji przerwanie żądania serwera.  
  
 Nie można usunąć stanu wywołania zwrotnego, jak długo trwa wszystkie wywołania zwrotne.  
  
 Aby obsłużyć wszystkie operacje asynchroniczne, możesz utworzyć własne wątku lub użyć funkcji WinInet bez MFC.  
  
##  <a name="getcontext"></a>CInternetSession::GetContext  
 Wywołanie tej funkcji członkowskich można uzyskać wartość kontekstu sesji określonej aplikacji.  
  
```  
DWORD_PTR GetContext() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zdefiniowane przez aplikację kontekst identyfikator.  
  
### <a name="remarks"></a>Uwagi  
 [OnStatusCallback](#onstatuscallback) używa Identyfikatora kontekstu zwracany przez **GetContext** do raportowania stanu określonej aplikacji. Na przykład gdy użytkownik aktywuje żądanie Internet, która obejmuje zwracanie informacji o stanie, stanu wywołania zwrotnego używa Identyfikatora kontekstu do raportów o stanie dla tego konkretnego żądania. Jeśli użytkownik aktywuje dwa oddzielne żądania internetowe zarówno obejmują zwracanie informacji o stanie, `OnStatusCallback` używa identyfikatorów kontekstu ma zostać zwrócony stan o ich odpowiednie żądania. W rezultacie identyfikator kontekstu jest używany dla wszystkich operacji wywołania zwrotnego stanu i jest skojarzona z sesją, dopóki sesja zostanie zakończona.  
  
 Aby uzyskać więcej informacji na temat operacji asynchronicznych, zobacz artykuł [pierwsze kroki Internet: WinInet](../../mfc/wininet-basics.md).  
  
##  <a name="getcookie"></a>CInternetSession::GetCookie  
 Ta funkcja członkowska implementuje zachowanie funkcji Win32 [InternetGetCookie](http://msdn.microsoft.com/library/windows/desktop/aa384710), zgodnie z opisem w zestawie Windows SDK.  
  
```  
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
 `pstrUrl`  
 Wskaźnik do ciąg zawierający adres URL.  
  
 `pstrCookieName`  
 Wskaźnik do ciąg zawierający nazwę pliku cookie do pobrania dla określonego adresu URL.  
  
 `pstrCookieData`  
 W pierwszym przeciążenia wskaźnik do ciąg zawierający adres buforu, który odbiera dane pliku cookie. Ta wartość może być **NULL**. W drugim przeciążenia odwołanie do [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) obiekt, aby odbierać dane pliku cookie.  
  
 `dwBufLen`  
 Zmienna określania rozmiaru `pstrCookieData` buforu. Jeśli funkcja zakończy się powodzeniem, bufor odbiera ilość danych skopiowane do `pstrCookieData` buforu. Jeśli `pstrCookieData` jest **NULL**, ten parametr odbiera wartość określająca rozmiar bufora niezbędne skopiować dane pliku cookie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia lub **FALSE** inaczej. Jeśli połączenie nie powiedzie się, wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) w celu ustalenia przyczyny błędu. Stosuje się następujące wartości błędu:  
  
- **ERROR_NO_MORE_ITEMS** istnieje pliki cookie nie dla określonego adresu URL i wszystkich jego elementów nadrzędnych.  
  
- **ERROR_INSUFFICIENT_BUFFER** przekazanej wartości `dwBufLen` jest za mało, aby skopiować dane pliku cookie. Wartość zwracana w `dwBufLen` jest niezbędne, aby uzyskać wszystkie dane rozmiar buforu.  
  
### <a name="remarks"></a>Uwagi  
 W drugim przeciążenia MFC pobiera dane pliku cookie do podane `CString` obiektu.  
  
##  <a name="getcookielength"></a>CInternetSession::GetCookieLength  
 Wywołaj tę funkcję elementu członkowskiego, aby pobrać długości plik cookie przechowywany w buforze.  
  
```  
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,  
    LPCTSTR pstrCookieName);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrUrl`  
 Wskaźnik do ciąg zawierający adres URL  
  
 `pstrCookieName`  
 Wskaźnik do ciąg zawierający nazwę pliku cookie.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `DWORD` wartość wskazującą, długość plik cookie przechowywany w buforze. Zero, jeśli pliki cookie nie o nazwie wskazywanym przez `pstrCookieName` istnieje.  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość jest używana przez [GetCookie](#getcookie).  
  
##  <a name="getftpconnection"></a>CInternetSession::GetFtpConnection  
 Wywołanie tej funkcji Członkowskich, aby nawiązać połączenie FTP i Pobierz wskaźnik do `CFtpConnection` obiektu.  
  
```  
CFtpConnection* GetFtpConnection(
    LPCTSTR pstrServer,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    BOOL bPassive = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrServer`  
 Wskaźnik do ciąg zawierający nazwę serwera FTP.  
  
 `pstrUserName`  
 Wskaźnik do zerem ciąg, który określa nazwę użytkownika, aby się zalogować. Jeśli **NULL**, wartością domyślną jest anonimowy.  
  
 `pstrPassword`  
 Wskaźnik do zerem ciąg, który określa hasło używane do logowania. Jeśli oba `pstrPassword` i `pstrUserName` są **NULL**, domyślne hasła anonimowego jest nazwa e-mail użytkownika. Jeśli `pstrPassword` jest **NULL** (lub ciąg pusty), ale `pstrUserName` nie jest **NULL**, puste hasło jest używane. W poniższej tabeli opisano zachowanie cztery ustawienia możliwe `pstrUserName` i `pstrPassword`:  
  
|`pstrUserName`|`pstrPassword`|Nazwa użytkownika jest wysyłane do serwera FTP|Hasło wysłane do serwera FTP|  
|--------------------|--------------------|---------------------------------|---------------------------------|  
|**Wartość NULL** lub ""|**Wartość NULL** lub ""|"anonymous"|Nazwa e-mail użytkownika|  
|Nie- **NULL** ciągu|**Wartość NULL** lub ""|`pstrUserName`|" "|  
|**Wartość NULL** z systemem innym niż **NULL** ciągu|**BŁĄD**|**BŁĄD**||  
|Nie- **NULL** ciągu|Nie- **NULL** ciągu|`pstrUserName`|`pstrPassword`|  
  
 `nPort`  
 Liczba, która identyfikuje port TCP/IP używany na serwerze.  
  
 `bPassive`  
 Określa tryb pasywny lub aktywne dla tej sesji FTP. Jeśli ustawiono **TRUE**, ustawia interfejs API Win32 `dwFlag` do **INTERNET_FLAG_PASSIVE**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CFtpConnection](../../mfc/reference/cftpconnection-class.md) obiektu. Jeśli połączenie nie powiedzie się, należy określić przyczynę niepowodzenia, sprawdzając zgłoszenia [CInternetException](../../mfc/reference/cinternetexception-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 `GetFtpConnection`łączy się z serwerem FTP i tworzy i zwraca wskaźnik do **CFTPConnection** obiektu. Nie wykonuje żadnej określonej operacji na serwerze. Jeśli zamierzasz odczytu lub zapisu do plików, na przykład, należy wykonać te operacje jako oddzielne kroki. Zawiera opis klas [CFtpConnection](../../mfc/reference/cftpconnection-class.md) i [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) uzyskać informacji o wyszukiwaniu plików, otwieranie plików i Odczyt lub zapis do plików. Zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md) dla kroków wykonywania typowych zadań połączenie FTP.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).  
  
##  <a name="getgopherconnection"></a>CInternetSession::GetGopherConnection  
 Wywołanie tej funkcji Członkowskich do nawiązania nowego połączenia gopher i Pobierz wskaźnik do `CGopherConnection` obiektu.  
  
```  
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrServer`  
 Wskaźnik do ciąg zawierający nazwę serwera gopher.  
  
 `pstrUserName`  
 Wskaźnik do ciąg zawierający nazwę użytkownika.  
  
 `pstrPassword`  
 Wskaźnik do ciąg zawierający hasła dostępu.  
  
 `nPort`  
 Liczba, która identyfikuje port TCP/IP używany na serwerze.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) obiektu. Jeśli połączenie nie powiedzie się, należy określić przyczynę niepowodzenia, sprawdzając zgłoszenia [CInternetException](../../mfc/reference/cinternetexception-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 `GetGopherConnection`nawiązuje połączenie z serwerem gopher i tworzy i zwraca wskaźnik do `CGopherConnection` obiektu. Nie wykonuje żadnej określonej operacji na serwerze. Jeśli zamierzasz odczytu lub zapisu danych, na przykład, należy wykonać te operacje jako oddzielne kroki. Zawiera opis klas [CGopherConnection](../../mfc/reference/cgopherconnection-class.md), [cgopherfile —](../../mfc/reference/cgopherfile-class.md), i [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) uzyskać informacji o wyszukiwaniu plików, otwieranie plików i Odczyt lub zapis do plików. Aby dowiedzieć się, jak przeglądanie witryny FTP, zobacz funkcji członkowskiej [OpenURL](#openurl). Zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md) w wykonywania typowych zadań połączenia gopher krokach.  
  
##  <a name="gethttpconnection"></a>CInternetSession::GetHttpConnection  
 Wywołanie tej funkcji Członkowskich do nawiązania połączenia HTTP i Pobierz wskaźnik do `CHttpConnection` obiektu.  
  
```  
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
 `pstrServer`  
 Wskaźnik do ciąg zawierający nazwę serwera HTTP.  
  
 `nPort`  
 Liczba, która identyfikuje port TCP/IP używany na serwerze.  
  
 `pstrUserName`  
 Wskaźnik do ciąg zawierający nazwę użytkownika.  
  
 `pstrPassword`  
 Wskaźnik do ciąg zawierający hasła dostępu.  
  
 *wartość elementu dwFlags*  
 Dowolną kombinację **INTERNET_ FLAG_\***  flagi. Zobacz tabelę w **uwagi** sekcji [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) opis `dwFlags` wartości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CHttpConnection](../../mfc/reference/chttpconnection-class.md) obiektu. Jeśli połączenie nie powiedzie się, należy określić przyczynę niepowodzenia, sprawdzając zgłoszenia [CInternetException](../../mfc/reference/cinternetexception-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 `GetHttpConnection`łączy się z serwerem HTTP i tworzy i zwraca wskaźnik do `CHttpConnection` obiektu. Nie wykonuje żadnej określonej operacji na serwerze. Jeśli zamierzasz zapytania nagłówka HTTP, na przykład, należy wykonać tę operację w osobnym kroku. Zawiera opis klas [CHttpConnection](../../mfc/reference/chttpconnection-class.md) i [CHttpFile](../../mfc/reference/chttpfile-class.md) uzyskać informacji o operacjach można wykonywać przy użyciu połączenia z serwerem HTTP. Aby dowiedzieć się, jak przeglądanie witryny HTTP, zobacz funkcji członkowskiej [OpenURL](#openurl). Zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md) dla kroków wykonywania typowych zadań połączenia HTTP.  
  
##  <a name="onstatuscallback"></a>CInternetSession::OnStatusCallback  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, aby zaktualizować stan, gdy wywołanie zwrotne dla stanu jest włączona, a operacja oczekuje.  
  
```  
virtual void OnStatusCallback(
    DWORD_PTR dwContext,  
    DWORD dwInternetStatus,  
    LPVOID lpvStatusInformation,  
    DWORD dwStatusInformationLength);
```  
  
### <a name="parameters"></a>Parametry  
 `dwContext`  
 Wartość kontekstu dostarczone przez aplikację.  
  
 `dwInternetStatus`  
 Kod stanu wskazujący, dlaczego jest wykonywane wywołanie zwrotne. Zobacz **uwagi** dla tabeli możliwych wartości.  
  
 `lpvStatusInformation`  
 Wskaźnik do buforu, zawierające informacje dotyczące tego wywołania zwrotnego.  
  
 `dwStatusInformationLength`  
 Rozmiar `lpvStatusInformation`.  
  
### <a name="remarks"></a>Uwagi  
 Najpierw musisz wywołać [EnableStatusCallback](#enablestatuscallback) przeprowadzać stanu wywołania zwrotnego.  
  
 `dwInternetStatus` Parametr wskazuje wykonywanej operacji i określa, jakie zawartość `lpvStatusInformation` będzie. `dwStatusInformationLength`Określa długość danych zawartych w `lpvStatusInformation`. Stan następujące wartości `dwInternetStatus` są zdefiniowane w następujący sposób:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|`INTERNET_STATUS_RESOLVING_NAME`|Wyszukiwanie adresu IP z nazwą określoną w `lpvStatusInformation`.|  
|`INTERNET_STATUS_NAME_RESOLVED`|Pomyślnie odnaleziono adres IP z nazwą określoną w `lpvStatusInformation`.|  
|`INTERNET_STATUS_CONNECTING_TO_SERVER`|Łączenie z adresu gniazda ( [SOCKADDR](../../mfc/reference/sockaddr-structure.md)) wskazywana przez `lpvStatusInformation`.|  
|`INTERNET_STATUS_CONNECTED_TO_SERVER`|Pomyślnie nawiązano połączenie z adresem gniazda ( `SOCKADDR`) wskazywana przez `lpvStatusInformation`.|  
|`INTERNET_STATUS_SENDING_REQUEST`|Wysyłanie żądania informacji do serwera. `lpvStatusInformation` Parametr jest **NULL**.|  
|**INTERNET_STATUS_ REQUEST_SENT**|Pomyślnie wysłane żądanie informacji do serwera. `lpvStatusInformation` Parametr jest **NULL**.|  
|`INTERNET_STATUS_RECEIVING_RESPONSE`|Oczekiwanie na odpowiedź na żądanie serwera. `lpvStatusInformation` Parametr jest **NULL**.|  
|`INTERNET_STATUS_RESPONSE_RECEIVED`|Pomyślnie odebrał odpowiedź z serwera. `lpvStatusInformation` Parametr jest **NULL**.|  
|`INTERNET_STATUS_CLOSING_CONNECTION`|Zamykanie połączenia z serwerem. `lpvStatusInformation` Parametr jest **NULL**.|  
|`INTERNET_STATUS_CONNECTION_CLOSED`|Pomyślnie zakończył połączenie z serwerem. `lpvStatusInformation` Parametr jest **NULL**.|  
|`INTERNET_STATUS_HANDLE_CREATED`|Używany przez funkcję Win32 API [funkcji InternetConnect](http://msdn.microsoft.com/library/windows/desktop/aa384363) aby wskazać, że został utworzony nowy uchwyt. Dzięki temu funkcja wywołanie Win32 aplikacji [InternetCloseHandle](http://msdn.microsoft.com/library/windows/desktop/aa384350) z innego wątku, jeśli Połącz trwa zbyt długo. Zobacz więcej informacji o tych funkcjach SDKfor systemu Windows.|  
|`INTERNET_STATUS_HANDLE_CLOSING`|Wartość ta dojścia zostały przerwane pomyślnie.|  
  
 Przesłonić tę funkcję elementu członkowskiego, aby wymagać niektóre akcje, przed wykonaniem procedura wywołania zwrotnego stanu.  
  
> [!NOTE]
>  Stan wywołania zwrotne wymagać ochrony stan wątku. Jeśli używasz MFC w bibliotece udostępnionej, Dodaj następujący wiersz na początku zastąpienia:  
  
 [!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]  
  
 Aby uzyskać więcej informacji na temat operacji asynchronicznych, zobacz artykuł [pierwsze kroki Internet: WinInet](../../mfc/wininet-basics.md).  
  
##  <a name="openurl"></a>CInternetSession::OpenURL  
 Ten element członkowski należy wywołać funkcję wysyłania określonego żądania do serwera HTTP i umożliwić klientom Określ dodatkowe RFC822 MIME lub nagłówków HTTP do wysłania wraz z żądaniem.  
  
```  
CStdioFile* OpenURL(
    LPCTSTR pstrURL,  
    DWORD_PTR dwContext = 1,  
    DWORD dwFlags = INTERNET_FLAG_TRANSFER_ASCII,  
    LPCTSTR pstrHeaders = NULL,  
    DWORD dwHeadersLength = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *pstrURL*  
 Wskaźnik do nazwy adres URL ma rozpocząć się odczyt. Tylko adresy URL rozpoczynające się od pliku:, ftp:, gopher:, lub http: są obsługiwane. **POTWIERDZENIA** Jeśli *pszURL* jest **NULL**.  
  
 `dwContext`  
 Wartości zdefiniowane przez aplikację przekazany z uchwytu zwrócony w wywołania zwrotnego.  
  
 `dwFlags`  
 Flagi opisujące sposób obsługi tego połączenia. Zobacz **uwagi** Aby uzyskać więcej informacji na temat prawidłowe flagi. Prawidłowe flagi są:  
  
- **INTERNET_FLAG_TRANSFER_ASCII** domyślny. Przetransferuj plik jako tekst w formacie ASCII.  
  
- **INTERNET_FLAG_TRANSFER_BINARY** transferu pliku jako pliku binarnego.  
  
- `INTERNET_FLAG_RELOAD`Pobierz dane z sieci, nawet jeśli jest buforowany lokalnie.  
  
- `INTERNET_FLAG_DONT_CACHE`Nie buforuj danych lokalnie lub w żadnych bram.  
  
- `INTERNET_FLAG_SECURE`Ta flaga jest dotyczy tylko żądania HTTP. Żądania transakcji bezpiecznego przesyłania Secure Sockets Layer lub procent  
  
- **INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT** Jeśli to możliwe, ponowne użycie istniejących połączeń z serwerem nowych żądań wygenerowanych przez **OpenUrl** zamiast tworzenia nowej sesji dla każdego żądania połączenia.  
  
- **INTERNET_FLAG_PASSIVE** używane dla witryny FTP. Używa pasywnym semantyki FTP. Używane z [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) z `OpenURL`.  
  
 `pstrHeaders`  
 Wskaźnik do ciąg zawierający nagłówki, które zostanie wysłane do serwera HTTP.  
  
 *dwHeadersLength*  
 Długość w znakach dodatkowych nagłówków. Jeśli jest to L-1 i `pstrHeaders` ma wartość inną niż **NULL**, następnie `pstrHeaders` zakłada, że zero została zakończona, a długość jest obliczana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca dojście do pliku dla tylko usługi FTP, GOPHER, HTTP i Internet typu pliku. Zwraca **NULL** Jeśli analizy nie powiodło się.  
  
 Wskaźnik który `OpenURL` zależy od zwraca *pszURL*dla typu usługi. W poniższej tabeli przedstawiono możliwe wskaźniki `OpenURL` może zwrócić.  
  
|Typ adresu URL|Zwraca|  
|--------------|-------------|  
|File://|**CStdioFile\***|  
|http://|**CHttpFile\***|  
|Gopher://|**Cgopherfile —\***|  
|FTP: / /|**CInternetFile\***|  
  
### <a name="remarks"></a>Uwagi  
 Parametr `dwFlags` musi zawierać albo **INTERNET_FLAG_TRANSFER_ASCII** lub **INTERNET_FLAG_TRANSFER_BINARY**, ale nie oba. Pozostałe flagi można łączyć z bitowego `OR` — operator ( **&#124;**).  
  
 `OpenURL`, który opakowuje funkcji Win32 **InternetOpenURL**, umożliwia tylko pobieranie, pobieranie i odczytywanie danych z serwera internetowego. `OpenURL`umożliwia manipulowanie nie pliku w lokalizacji zdalnej, więc nie wymaga nr [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) obiektu.  
  
 Aby użyć konkretnego połączenia (oznacza to, oparte na protokole) funkcji, takich jak zapis do pliku, użytkownik musi Otwórz sesję programu, otwórz określonego rodzaju połączenia, a następnie otworzyć plik w trybie żądaną za pomocą tego połączenia. Zobacz `CInternetConnection` Aby uzyskać więcej informacji na temat funkcji specyficznych dla połączenia.  
  
##  <a name="operator_hinternet"></a>CInternetSession::operator HINTERNET  
 Użyj tego operatora, można pobrać uchwytu systemu Windows dla bieżącej sesji Internet.  
  
```  
operator HINTERNET() const;  
```  
  
##  <a name="setcookie"></a>CInternetSession::SetCookie  
 Ustawia plik cookie dla określonego adresu URL.  
  
```  
static BOOL SetCookie(
    LPCTSTR pstrUrl,  
    LPCTSTR pstrCookieName,  
    LPCTSTR pstrCookieData);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrUrl`  
 Wskaźnik do zerem ciągu, który określa adres URL, dla którego plik cookie powinien być ustawiony.  
  
 `pstrCookieName`  
 Wskaźnik do ciąg zawierający nazwę pliku cookie.  
  
 `pstrCookieData`  
 Wskaźnik do ciąg zawierający dane rzeczywistego ciągu do skojarzenia z adresem URL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia lub **FALSE** inaczej. Aby uzyskać kod błędu, należy wywołać **GetLastError.**  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [InternetSetCookie](http://msdn.microsoft.com/library/windows/desktop/aa385107), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="setoption"></a>CInternetSession::SetOption  
 Wywołanie tej funkcji Członkowskich, aby ustawić opcje dla sesji internetowej.  
  
```  
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
 `dwOption`  
 Opcja Internet ustawienia. Zobacz [flagi opcji](http://msdn.microsoft.com/library/windows/desktop/aa385328) w SDKfor Windows listę możliwych opcji.  
  
 `lpBuffer`  
 Bufor, który zawiera ustawienia opcji.  
  
 *dwBufferLength*  
 Długość `lpBuffer` lub rozmiaru `dwValue`.  
  
 `dwValue`  
 A `DWORD` zawierający ustawienia opcji.  
  
 `dwFlags`  
 Wskazuje różne opcje buforowania. Wartość domyślna jest równa 0. Możliwe wartości:  
  
- `INTERNET_FLAG_DONT_CACHE`Nie buforuj danych lokalnie lub w dowolne serwery bramy.  
  
- `INTERNET_FLAG_OFFLINE`Pobierz operacje są spełnione przez tylko trwałej pamięci podręcznej. Jeśli element nie istnieje w pamięci podręcznej, zostanie zwrócony kod błędu odpowiednie. Ta flaga mogą być łączone z bitowego `OR` ( **&#124;**) operatora.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja zakończyła się powodzeniem, wartość **TRUE** jest zwracany. Jeśli wystąpi błąd, wartość **FALSE** jest zwracany. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)   
 [Klasa CHttpConnection](../../mfc/reference/chttpconnection-class.md)   
 [Klasa CFtpConnection](../../mfc/reference/cftpconnection-class.md)   
 [Klasa CGopherConnection](../../mfc/reference/cgopherconnection-class.md)
