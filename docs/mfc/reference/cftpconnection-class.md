---
title: Klasa CFtpConnection | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFtpConnection
- AFXINET/CFtpConnection
- AFXINET/CFtpConnection::CFtpConnection
- AFXINET/CFtpConnection::Command
- AFXINET/CFtpConnection::CreateDirectory
- AFXINET/CFtpConnection::GetCurrentDirectory
- AFXINET/CFtpConnection::GetCurrentDirectoryAsURL
- AFXINET/CFtpConnection::GetFile
- AFXINET/CFtpConnection::OpenFile
- AFXINET/CFtpConnection::PutFile
- AFXINET/CFtpConnection::Remove
- AFXINET/CFtpConnection::RemoveDirectory
- AFXINET/CFtpConnection::Rename
- AFXINET/CFtpConnection::SetCurrentDirectory
dev_langs: C++
helpviewer_keywords:
- CFtpConnection [MFC], CFtpConnection
- CFtpConnection [MFC], Command
- CFtpConnection [MFC], CreateDirectory
- CFtpConnection [MFC], GetCurrentDirectory
- CFtpConnection [MFC], GetCurrentDirectoryAsURL
- CFtpConnection [MFC], GetFile
- CFtpConnection [MFC], OpenFile
- CFtpConnection [MFC], PutFile
- CFtpConnection [MFC], Remove
- CFtpConnection [MFC], RemoveDirectory
- CFtpConnection [MFC], Rename
- CFtpConnection [MFC], SetCurrentDirectory
ms.assetid: 5e3a0501-8893-49cf-a3d5-0628d8d6b936
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a20ee1e3de4d5c9f61437c79bd2eda4240947947
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cftpconnection-class"></a>Klasa CFtpConnection
Zarządza połączenie FTP do serwera i umożliwia bezpośredniej katalogów i plików na tym serwerze.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CFtpConnection : public CInternetConnection  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFtpConnection::CFtpConnection](#cftpconnection)|Konstruuje `CFtpConnection` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFtpConnection::Command](#command)|Wysyła polecenie bezpośrednio do serwera FTP.|  
|[CFtpConnection::CreateDirectory](#createdirectory)|Tworzy katalog na serwerze.|  
|[CFtpConnection::GetCurrentDirectory](#getcurrentdirectory)|Pobiera bieżący katalog dla tego połączenia.|  
|[CFtpConnection::GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)|Pobiera bieżący katalog dla tego połączenia w postaci adresu URL.|  
|[CFtpConnection::GetFile](#getfile)|Pobiera plik z podłączonego serwera|  
|[CFtpConnection::OpenFile](#openfile)|Otwiera plik na połączonym serwerze.|  
|[CFtpConnection::PutFile](#putfile)|Umieszcza plik na serwerze.|  
|[CFtpConnection::Remove](#remove)|Usuwa plik z serwera.|  
|[CFtpConnection::RemoveDirectory](#removedirectory)|Usuwa określony katalog z serwera.|  
|[CFtpConnection::Rename](#rename)|Zmienia nazwę pliku na serwerze.|  
|[CFtpConnection::SetCurrentDirectory](#setcurrentdirectory)|Ustawia bieżący katalog FTP.|  
  
## <a name="remarks"></a>Uwagi  
 FTP jest jednym z trzech rozpoznaje klas MFC WinInet usług internetowych.  
  
 Do komunikacji z serwerem FTP Internet, należy najpierw utworzyć wystąpienie [CInternetSession](../../mfc/reference/cinternetsession-class.md), a następnie utwórz `CFtpConnection` obiektu. Nigdy nie twórz `CFtpConnection` obiektu bezpośrednio; zamiast wywoływać [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), co powoduje `CFtpConnection` obiektu i zwraca wskaźnik do niego.  
  
 Aby dowiedzieć się więcej na temat `CFtpConnection` współpracuje z innych klas MFC Internet, zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md). Aby uzyskać więcej informacji o komunikowania się z dwóch, obsługiwane usługi, HTTP i gopher, zobacz klasy [CHttpConnection](../../mfc/reference/chttpconnection-class.md) i [CGopherConnection](../../mfc/reference/cgopherconnection-class.md).  
  
## <a name="example"></a>Przykład  
  Zapoznaj się z przykładem w [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) Przegląd klasy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CFtpConnection`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxinet.h  
  
##  <a name="cftpconnection"></a>CFtpConnection::CFtpConnection  
 Ta funkcja elementu członkowskiego jest wywoływana w celu utworzenia `CFtpConnection` obiektu.  
  
```  
CFtpConnection(
    CInternetSession* pSession,  
    HINTERNET hConnected,  
    LPCTSTR pstrServer,  
    DWORD_PTR dwContext);

 
CFtpConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    DWORD_PTR dwContext = 0,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    BOOL bPassive = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `pSession`  
 Wskaźnik do pokrewny [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu.  
  
 `hConnected`  
 Dojście systemu Windows w bieżącej sesji Internet.  
  
 `pstrServer`  
 Wskaźnik do ciąg zawierający nazwę serwera FTP.  
  
 `dwContext`  
 Identyfikator kontekstu dla tej operacji. `dwContext`Określa informacje o stanie operacji zwrócony przez [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). Wartość domyślna jest ustawiona na 1; jednak można jawnie przypisać identyfikator kontekstu określonych dla tej operacji. Obiekt i pracę go nie będą skojarzone z tym identyfikatorem kontekstu.  
  
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
  
### <a name="remarks"></a>Uwagi  
 Nigdy nie twórz `CFtpConnection` obiekt bezpośrednio. Zamiast tego wywołać [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), co powoduje **CFptConnection** obiektu.  
  
##  <a name="command"></a>CFtpConnection::Command  
 Wysyła polecenie bezpośrednio do serwera FTP.  
  
```  
CInternetFile* Command(
    LPCTSTR pszCommand,  
    CmdResponseType eResponse = CmdRespNone,  
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `pszCommand`  
 Wskaźnik do ciąg zawierający polecenia do wysłania.  
  
 *eResponse*  
 Określa, czy oczekiwano odpowiedzi z serwera FTP. Może to być jedna z następujących wartości:  
  
- **CmdRespNone** odpowiedź nie jest oczekiwany.  
  
- **CmdRespRead** oczekiwano odpowiedzi.  
  
 `dwFlags`  
 Wartość flagami, które kontrolują tej funkcji. Aby uzyskać pełną listę, zobacz [polecenie FTP](http://msdn.microsoft.com/library/windows/desktop/aa384133).  
  
 `dwContext`  
 Wskaźnik do wartości zawierającej wartość zdefiniowanym przez aplikację, używany do identyfikowania kontekst aplikacji w wywołań zwrotnych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcje [polecenie FTP](http://msdn.microsoft.com/library/windows/desktop/aa384133) działać zgodnie z opisem w zestawie Windows SDK.  
  
 Jeśli wystąpi błąd, MFC zgłasza wyjątek typu [CInternetException](../../mfc/reference/cinternetexception-class.md).  
  
##  <a name="createdirectory"></a>CFtpConnection::CreateDirectory  
 Wywołanie tej funkcji Członkowskich do tworzenia katalogu na połączonym serwerze.  
  
```  
BOOL CreateDirectory(LPCTSTR pstrDirName);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrDirName`  
 Wskaźnik do ciąg zawierający nazwę katalogu do utworzenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji systemu Windows [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `GetCurrentDirectory` można określić bieżącego katalogu roboczego dla tego połączenia z serwerem. Nie Przypuśćmy, że system zdalny ma zostanie podłączony do katalogu głównego.  
  
 `pstrDirName` Parametru może być częściowo lub w pełni kwalifikowana nazwa pliku względem bieżącego katalogu. Ukośnik odwrotny (\\) ani ukośnika (/) może być używany jako separator katalogu dla każdej nazwy. `CreateDirectory`wykonuje translację separatorów nazwę katalogu do odpowiednich znaków, zanim zostaną użyte.  
  
##  <a name="getcurrentdirectory"></a>CFtpConnection::GetCurrentDirectory  
 Wywołanie tej funkcji elementu członkowskiego, aby uzyskać nazwę bieżącego katalogu.  
  
```  
BOOL GetCurrentDirectory(CString& strDirName) const;  
  
BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,  
    LPDWORD lpdwLen) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `strDirName`  
 Odwołanie do ciągu, który otrzyma nazwę katalogu.  
  
 `pstrDirName`  
 Wskaźnik na ciąg, który otrzyma nazwę katalogu.  
  
 `lpdwLen`  
 Wskaźnik do typu DWORD, który zawiera następujące informacje:  
  
|||  
|-|-|  
|Podczas wprowadzania|Rozmiar buforu odwołuje się `pstrDirName`.|  
|Przy powrocie|Liczba znaków, zapisać `pstrDirName`. Jeśli funkcja członkowska nie powiedzie się i ERROR_INSUFFICIENT_BUFFER jest zwracany, następnie `lpdwLen` zawiera liczbę bajtów, które aplikacji musi przydzielić w celu odbierania ciąg.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
### <a name="remarks"></a>Uwagi  
 Aby zamiast tego Pobierz nazwy katalogu jako adres URL, należy wywołać [GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl).  
  
 Parametry `pstrDirName` lub `strDirName` może być albo częściowo kwalifikowanej nazwy plików względem bieżącego katalogu lub w pełni kwalifikowana. Ukośnik odwrotny (\\) ani ukośnika (/) może być używany jako separator katalogu dla każdej nazwy. `GetCurrentDirectory`wykonuje translację separatorów nazwę katalogu do odpowiednich znaków, zanim zostaną użyte.  
  
##  <a name="getcurrentdirectoryasurl"></a>CFtpConnection::GetCurrentDirectoryAsURL  
 Wywołanie tej funkcji członkowskich można pobrać bieżącego katalogu nazwy jako adresu URL.  
  
```  
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;  
  
BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,  
    LPDWORD lpdwLen) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `strDirName`  
 Odwołanie do ciągu, który otrzyma nazwę katalogu.  
  
 `pstrDirName`  
 Wskaźnik na ciąg, który otrzyma nazwę katalogu.  
  
 `lpdwLen`  
 Wskaźnik do typu DWORD, który zawiera następujące informacje:  
  
|||  
|-|-|  
|Podczas wprowadzania|Rozmiar buforu odwołuje się `pstrDirName`.|  
|Przy powrocie|Liczba znaków, zapisać `pstrDirName`. Jeśli funkcja członkowska nie powiedzie się i ERROR_INSUFFICIENT_BUFFER jest zwracany, następnie `lpdwLen` zawiera liczbę bajtów, które aplikacji musi przydzielić w celu odbierania ciąg.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
### <a name="remarks"></a>Uwagi  
 `GetCurrentDirectoryAsURL`działa tak samo jak [GetCurrentDirectory](#getcurrentdirectory)  
  
 Parametr `strDirName` może być albo częściowo kwalifikowanej nazwy plików względem bieżącego katalogu lub w pełni kwalifikowana. Ukośnik odwrotny (\\) ani ukośnika (/) może być używany jako separator katalogu dla każdej nazwy. `GetCurrentDirectoryAsURL`wykonuje translację separatorów nazwę katalogu do odpowiednich znaków, zanim zostaną użyte.  
  
##  <a name="getfile"></a>CFtpConnection::GetFile  
 Wywołanie tej funkcji Członkowskich pobierania pliku z serwera FTP i zapisz go na komputerze lokalnym.  
  
```  
BOOL GetFile(
    LPCTSTR pstrRemoteFile,  
    LPCTSTR pstrLocalFile,  
    BOOL bFailIfExists = TRUE,  
    DWORD dwAttributes = FILE_ATTRIBUTE_NORMAL,  
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrRemoteFile`  
 Wskaźnik do zerem ciąg zawierający nazwę pliku do pobrania z serwera FTP.  
  
 `pstrLocalFile`  
 Wskaźnik do zerem ciąg zawierający nazwę pliku w systemie lokalnym.  
  
 *bFailIfExists*  
 Wskazuje, czy nazwa pliku może być już używana przez istniejący plik. Jeśli nazwa pliku lokalnego już istnieje, a ten parametr jest **TRUE**, `GetFile` nie powiedzie się. W przeciwnym razie `GetFile` spowoduje usunięcie istniejących kopii pliku.  
  
 `dwAttributes`  
 Określa atrybuty pliku. Może to być dowolną kombinację następujących flag FILE_ATTRIBUTE_ *.  
  
-   FILE_ATTRIBUTE_ARCHIVE plik jest plikiem archiwum. Aplikacje użyć tego atrybutu, aby oznaczyć pliki kopii zapasowej lub usunięcia.  
  
-   FILE_ATTRIBUTE_COMPRESSED plik lub katalog jest kompresowany. Dla pliku kompresji oznacza, że wszystkie dane w pliku skompresowane. Dla nazwy katalogu kompresji jest ustawieniem domyślnym dla nowo utworzone pliki i podkatalogi.  
  
-   FILE_ATTRIBUTE_DIRECTORY plik jest katalogiem.  
  
-   FILE_ATTRIBUTE_NORMAL pliku nie ma żadnych innych atrybutów, ustaw. Ten atrybut jest prawidłowy tylko wtedy, gdy użyte bez parametrów. Inne atrybuty pliku zastąpić FILE_ATTRIBUTE_NORMAL:  
  
-   FILE_ATTRIBUTE_HIDDEN plik jest ukryty. Jest nie powinny zostać uwzględnione na liście zawartości katalogu zwykłej.  
  
-   FILE_ATTRIBUTE_READONLY plik jest tylko do odczytu. Aplikacje można odczytać pliku, ale nie może zapisywać do niego lub usuń go.  
  
-   FILE_ATTRIBUTE_SYSTEM plik jest częścią lub jest używany wyłącznie przez system operacyjny.  
  
-   FILE_ATTRIBUTE_TEMPORARY plik jest używany do tymczasowego przechowywania danych. Aplikacje należy zapisać w pliku tylko wtedy, gdy jest to bezwzględnie konieczne. Większość plików danych pozostaje w pamięci bez opróżnianych na nośniku, ponieważ plik wkrótce zostanie usunięty.  
  
 `dwFlags`  
 Określa warunki, w których występuje transferu. Ten parametr może być dowolny z `dwFlags` wartości opisanego w [FtpGetFile](http://msdn.microsoft.com/library/windows/desktop/aa384157) w zestawie Windows SDK.  
  
 `dwContext`  
 Identyfikator kontekstu pobierania pliku. Zobacz **uwagi** uzyskać więcej informacji o `dwContext`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
### <a name="remarks"></a>Uwagi  
 `GetFile`to procedura wysokiego poziomu obsługuje wszystkie obciążenia związanego z odczytywania pliku z serwera FTP i przechowywaniu jej lokalnie. Aplikacje, które tylko pobieranie plików danych lub wymagających ścisłą kontrolę nad transfer plików powinny używać `OpenFile` i [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read) zamiast tego.  
  
 Jeśli `dwFlags` FILE_TRANSFER_TYPE_ASCII, tłumaczenia pliku danych jest także konwertuje formant i formatowanie znaków równoważniki w systemie Windows. Transfer domyślny jest trybie binarnym, którego pobrany plik w tym samym formacie jak są przechowywane na serwerze.  
  
 Zarówno `pstrRemoteFile` i `pstrLocalFile` może być albo częściowo kwalifikowanej nazwy plików względem bieżącego katalogu lub w pełni kwalifikowana. Ukośnik odwrotny (\\) ani ukośnika (/) może być używany jako separator katalogu dla każdej nazwy. `GetFile`wykonuje translację separatorów nazwę katalogu do odpowiednich znaków, zanim zostaną użyte.  
  
 Zastąpienie `dwContext` domyślne, aby skonfigurować identyfikator kontekstu wartości wybrane. Identyfikator kontekstu jest skojarzony z tym działania związane z `CFtpConnection` obiektu utworzonego przez jego [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu. Wartość jest zwracana do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zapewnienie stan operacji, z którą zostanie zidentyfikowana. Zapoznaj się z artykułem [pierwsze kroki Internet: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.  
  
##  <a name="openfile"></a>CFtpConnection::OpenFile  
 Wywołanie tej funkcji członkowskich można otworzyć pliku znajdującego się na serwerze FTP do odczytu lub zapisu.  
  
```  
CInternetFile* OpenFile(
    LPCTSTR pstrFileName,  
    DWORD dwAccess = GENERIC_READ,  
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrFileName`  
 Wskaźnik do ciąg zawierający nazwę pliku, który ma zostać otwarty.  
  
 *dwAccess*  
 Określa, jak plik będzie dostępny. Może być GENERIC_READ lub GENERIC_WRITE, ale nie oba.  
  
 `dwFlags`  
 Określa warunki, w których występują następnych transferów. Może to być dowolny z następujących stałych FTP_TRANSFER_ *:  
  
-   FTP_TRANSFER_TYPE_ASCII plik będzie przesyłana przy użyciu metody transferu FTP ASCII (typ A). Konwertuje formant i informacje dotyczące formatowania do lokalnego odpowiedniki.  
  
-   FTP_TRANSFER_TYPE_BINARY pliku transfery danych przy użyciu metody transferu obrazu FTP's, (typu I). Transfer danych plików w takiej postaci, jak istnieje bez zmian. To jest domyślna metoda transferu.  
  
 `dwContext`  
 Identyfikator kontekstu otwierania pliku. Zobacz **uwagi** uzyskać więcej informacji o `dwContext`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CInternetFile](../../mfc/reference/cinternetfile-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 `OpenFile`należy użyć w następujących sytuacjach:  
  
-   Aplikacja ma dane, które musi zostać wysłane i stworzony jako plik na serwerze FTP, ale, że dane nie są w pliku lokalnym. Raz `OpenFile` otwiera plik, aplikacja używa [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write) do wysyłania danych pliku FTP do serwera.  
  
-   Aplikacja musi pobrać pliku z serwera i umieszczenie go w pamięci kontrolowane przez aplikację, zamiast zapisywania go na dysku. Aplikacja używa [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read) po użyciu `OpenFile` można otworzyć pliku.  
  
-   Aplikacja musi poprawnie poziom kontroli nad transferu plików. Aplikacja może na przykład chcesz wyświetlić postępu kontroli informowania o postępie stanu transferu plików podczas pobierania pliku.  
  
 Po wywołaniu `OpenFile` i do wywoływania **CInternetConnection::Close**, aplikację można wywołać tylko [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read), [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write), **CInternetConnection::Close**, lub [CFtpFileFind::FindFile](../../mfc/reference/cftpfilefind-class.md#findfile). Wywołania funkcji innych FTP dla tej samej sesji FTP ma zakończyć się niepowodzeniem i Ustaw kod błędu: FTP_ETRANSFER_IN_PROGRESS.  
  
 `pstrFileName` Parametr może być albo częściowo kwalifikowanej nazwy pliku względnym w stosunku do bieżącego katalogu lub w pełni kwalifikowana. Ukośnik odwrotny (\\) ani ukośnika (/) może być używany jako separator katalogu dla każdej nazwy. `OpenFile`wykonuje translację separatorów nazwę katalogu do odpowiednie znaki przed jego użyciem.  
  
 Zastąpienie `dwContext` domyślne, aby skonfigurować identyfikator kontekstu wartości wybrane. Identyfikator kontekstu jest skojarzony z tym działania związane z `CFtpConnection` obiektu utworzonego przez jego [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu. Wartość jest zwracana do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zapewnienie stan operacji, z którą zostanie zidentyfikowana. Zapoznaj się z artykułem [pierwsze kroki Internet: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.  
  
##  <a name="putfile"></a>CFtpConnection::PutFile  
 Wywołanie tej funkcji Członkowskich do przechowywania plików na serwerze FTP.  
  
```  
BOOL PutFile(
    LPCTSTR pstrLocalFile,  
    LPCTSTR pstrRemoteFile,  
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrLocalFile`  
 Wskaźnik do ciąg zawierający nazwę pliku do wysłania z systemu lokalnego.  
  
 `pstrRemoteFile`  
 Wskaźnik do ciąg zawierający nazwę pliku do utworzenia na serwerze FTP.  
  
 `dwFlags`  
 Określa warunki, w których występuje transfer pliku. Może to być dowolna stałe FTP_TRANSFER_ * opisanego w [OpenFile](#openfile).  
  
 `dwContext`  
 Identyfikator kontekstu do umieszczenia pliku. Zobacz **uwagi** uzyskać więcej informacji o `dwContext`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
### <a name="remarks"></a>Uwagi  
 `PutFile`to procedura wysokiego poziomu obsługi wszystkich operacji związanych z przechowywaniem plików na serwerze FTP. Aplikacje wysłać tylko danych lub wymagających ściślejszej kontroli nad transfer plików powinny używać [OpenFile](#openfile) i [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write).  
  
 Zastąpienie `dwContext` domyślne, aby skonfigurować identyfikator kontekstu wartości wybrane. Identyfikator kontekstu jest skojarzony z tym działania związane z `CFtpConnection` obiektu utworzonego przez jego [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu. Wartość jest zwracana do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zapewnienie stan operacji, z którą zostanie zidentyfikowana. Zapoznaj się z artykułem [pierwsze kroki Internet: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.  
  
##  <a name="remove"></a>CFtpConnection::Remove  
 Wywołaj tę funkcję elementu członkowskiego, aby usunąć określony plik z podłączonego serwera.  
  
```  
BOOL Remove(LPCTSTR pstrFileName);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrFileName`  
 Wskaźnik do ciąg zawierający nazwę pliku do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
### <a name="remarks"></a>Uwagi  
 `pstrFileName` Parametr może być albo częściowo kwalifikowanej nazwy pliku względnym w stosunku do bieżącego katalogu lub w pełni kwalifikowana. Ukośnik odwrotny (\\) ani ukośnika (/) może być używany jako separator katalogu dla każdej nazwy. **Usuń** funkcji tłumaczy separatorów nazwę katalogu do odpowiednie znaki, zanim zostaną użyte.  
  
##  <a name="removedirectory"></a>CFtpConnection::RemoveDirectory  
 Wywołanie tej funkcji Członkowskich, aby usunąć określony katalog podłączonego serwera.  
  
```  
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrDirName`  
 Wskaźnik do ciągu zawierającego katalog ma zostać usunięty.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [GetCurrentDirectory](#getcurrentdirectory) można określić bieżącego katalogu roboczego serwera. Nie Przypuśćmy, że system zdalny ma zostanie podłączony do katalogu głównego.  
  
 `pstrDirName` Parametr może być częściowo lub w pełni kwalifikowaną nazwę względem bieżącego katalogu. Ukośnik odwrotny (\\) ani ukośnika (/) może być używany jako separator katalogu dla każdej nazwy. `RemoveDirectory`wykonuje translację separatorów nazwę katalogu do odpowiednich znaków, zanim zostaną użyte.  
  
##  <a name="rename"></a>CFtpConnection::Rename  
 Wywołanie tej funkcji Członkowskich, aby zmienić nazwę pliku na połączonym serwerze.  
  
```  
BOOL Rename(
    LPCTSTR pstrExisting,  
    LPCTSTR pstrNew);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrExisting`  
 Wskaźnik do ciąg zawierający nazwę aktualnie plików, których nazwa zostanie zmieniona.  
  
 `pstrNew`  
 Wskaźnik do ciąg zawierający nazwę nowego pliku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
### <a name="remarks"></a>Uwagi  
 `pstrExisting` i `pstrNew` parametry mogą być albo częściowo kwalifikowanej nazwy pliku względnym w stosunku do bieżącego katalogu lub w pełni kwalifikowana. Ukośnik odwrotny (\\) ani ukośnika (/) może być używany jako separator katalogu dla każdej nazwy. **Zmień nazwę** tłumaczy separatorów nazwę katalogu do odpowiednich znaków, zanim zostaną użyte.  
  
##  <a name="setcurrentdirectory"></a>CFtpConnection::SetCurrentDirectory  
 Wywołanie tej funkcji Członkowskich, aby zmienić do innego katalogu na serwerze FTP.  
  
```  
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrDirName`  
 Wskaźnik do ciąg zawierający nazwę katalogu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
### <a name="remarks"></a>Uwagi  
 `pstrDirName` Parametr może być częściowo lub w pełni kwalifikowaną nazwę względem bieżącego katalogu. Ukośnik odwrotny (\\) ani ukośnika (/) może być używany jako separator katalogu dla każdej nazwy. `SetCurrentDirectory`wykonuje translację separatorów nazwę katalogu do odpowiednich znaków, zanim zostaną użyte.  
  
 Użyj [GetCurrentDirectory](#getcurrentdirectory) ustalenie bieżący katalog roboczy serwera FTP. Nie Przypuśćmy, że system zdalny ma zostanie podłączony do katalogu głównego.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)   
 [Klasa CInternetSession](../../mfc/reference/cinternetsession-class.md)
