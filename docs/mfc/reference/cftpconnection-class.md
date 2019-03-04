---
title: Klasa CFtpConnection
ms.date: 11/04/2016
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
ms.openlocfilehash: 12ef4de16279c5c2033a95df5928a6dfb7a2a652
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295126"
---
# <a name="cftpconnection-class"></a>Klasa CFtpConnection

Zarządza połączeniem FTP do serwera internetowego i umożliwia bezpośrednie manipulacje katalogami i plikami na tym serwerze.

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
|[CFtpConnection::GetFile](#getfile)|Pobiera plik z połączonego serwera|
|[CFtpConnection::OpenFile](#openfile)|Otwiera plik na połączonym serwerze.|
|[CFtpConnection::PutFile](#putfile)|Umieszczanie pliku na serwerze.|
|[CFtpConnection::Remove](#remove)|Usuwa plik z serwera.|
|[CFtpConnection::RemoveDirectory](#removedirectory)|Usuwa określony katalog z serwera.|
|[CFtpConnection::Rename](#rename)|Zmienia nazwę pliku na serwerze.|
|[CFtpConnection::SetCurrentDirectory](#setcurrentdirectory)|Ustawia bieżący katalog FTP.|

## <a name="remarks"></a>Uwagi

FTP jest jednym z trzech usług internetowych, rozpoznawane przez klas MFC WinInet.

Aby komunikować się z serwerem FTP internetowym, należy najpierw utworzyć wystąpienie [CInternetSession](../../mfc/reference/cinternetsession-class.md), a następnie utwórz `CFtpConnection` obiektu. Nigdy nie twórz `CFtpConnection` obiektu bezpośrednio, zamiast zaproszenia [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), co powoduje utworzenie `CFtpConnection` obiektu i zwraca wskaźnik do niego.

Aby dowiedzieć się więcej o tym, jak `CFtpConnection` współpracuje z innych klas MFC Internet, zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md). Aby uzyskać więcej informacji na temat podczas komunikowania się z dwóch, obsługiwane usługi, HTTP i gopher, zobacz klasy [CHttpConnection](../../mfc/reference/chttpconnection-class.md) i [CGopherConnection](../../mfc/reference/cgopherconnection-class.md).

## <a name="example"></a>Przykład

  Zobacz przykład w [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) klasa — Przegląd.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CFtpConnection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

##  <a name="cftpconnection"></a>  CFtpConnection::CFtpConnection

Ta funkcja członkowska jest wywoływana, aby skonstruować `CFtpConnection` obiektu.

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

*pSession*<br/>
Wskaźnik do powiązane [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu.

*hConnected*<br/>
Uchwyt Windows bieżącej sesji internetowej.

*pstrServer*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera FTP.

*dwContext*<br/>
Identyfikator kontekstu dla tej operacji. *dwContext* określa informacje o stanie operacji zwrócony przez [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). Wartość domyślna jest ustawiona na 1; Jednakże można jawnie przypisać identyfikator kontekstu określonego dla operacji. Obiekt i wszelkie prace, które wykonuje zostanie skojarzona z tym identyfikatorem kontekstu.

*pstrUserName*<br/>
Wskaźnik na ciąg zakończony znakiem null, określający nazwę użytkownika, aby zalogować się. Jeśli ma wartość NULL, wartość domyślna jest anonimowy.

*pstrPassword*<br/>
Wskaźnik Określa hasło używane do logowania się w ciąg zakończony znakiem null. Jeśli oba *pstrPassword* i *pstrUserName* mają wartość NULL, domyślne hasło anonimowe to nazwa adres e-mail użytkownika. Jeśli *pstrPassword* ma wartość NULL (lub pustego ciągu), ale *pstrUserName* nie ma wartości NULL, puste hasło jest używane. W poniższej tabeli opisano zachowanie cztery ustawienia możliwe *pstrUserName* i *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Nazwa użytkownika jest wysyłane do serwera FTP|Hasła przesyłanych do serwera FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|Wartość NULL lub ""|Wartość NULL lub ""|"anonimowy"|Nazwa e-mail użytkownika|
|Ciąg znaków innych niż NULL|Wartość NULL lub ""|*pstrUserName*|" "|
|PUSTY ciąg inną niż NULL|BŁĄD|BŁĄD||
|Ciąg znaków innych niż NULL|Ciąg znaków innych niż NULL|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
Liczba, która identyfikuje port TCP/IP używany na serwerze.

*bPassive*<br/>
Określa tryb pasywny lub aktywny dla tej sesji FTP. Jeśli ma wartość TRUE, ustawia Win32 API *dwFlag* do INTERNET_FLAG_PASSIVE.

### <a name="remarks"></a>Uwagi

Nigdy nie twórz `CFtpConnection` obiektu bezpośrednio. Zamiast tego należy wywołać [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), co powoduje utworzenie `CFptConnection` obiektu.

##  <a name="command"></a>  CFtpConnection::Command

Wysyła polecenie bezpośrednio do serwera FTP.

```
CInternetFile* Command(
    LPCTSTR pszCommand,
    CmdResponseType eResponse = CmdRespNone,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pszCommand*<br/>
Wskaźnik do ciągu zawierającego polecenia do wysłania.

*eResponse*<br/>
Określa, czy odpowiedź jest oczekiwana z serwera FTP. Może być jednym z następujących wartości:

- `CmdRespNone` Brak odpowiedzi jest oczekiwany.

- `CmdRespRead` Odpowiedź jest oczekiwany.

*dwFlags*<br/>
Wartość flagami, które kontrolują tej funkcji. Aby uzyskać pełną listę, zobacz [polecenie FTP](/windows/desktop/api/wininet/nf-wininet-ftpcommanda).

*dwContext*<br/>
Wskaźnik do wartości zawierającej wartość zdefiniowanych przez aplikację, używany do identyfikowania kontekst aplikacji w wywołań zwrotnych.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska emuluje funkcjonalność [polecenie FTP](/windows/desktop/api/wininet/nf-wininet-ftpcommanda) działać zgodnie z opisem w zestawie Windows SDK.

Jeśli wystąpi błąd, MFC, zgłasza wyjątek typu [CInternetException](../../mfc/reference/cinternetexception-class.md).

##  <a name="createdirectory"></a>  CFtpConnection::CreateDirectory

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć katalog na połączonym serwerze.

```
BOOL CreateDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parametry

*pstrDirName*<br/>
Wskaźnik do ciągu zawierającego nazwę katalogu do utworzenia.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. Jeśli wywołanie zakończy się niepowodzeniem, funkcja Windows [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

Użyj `GetCurrentDirectory` Aby określić bieżący katalog roboczy dla tego połączenia z serwerem. Nie należy zakładać, że system zdalny połączył należy do katalogu głównego.

`pstrDirName` Parametru może być częściowo lub w pełni kwalifikowana nazwa pliku względem bieżącego katalogu. Ukośnik odwrotny (\\) lub ukośnika (/) może być używany jako separator katalogu dla obu nazwy. `CreateDirectory` wykonuje translację separatora nazwy katalogów na odpowiednie znaki, zanim zostaną użyte.

##  <a name="getcurrentdirectory"></a>  CFtpConnection::GetCurrentDirectory

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać nazwę bieżącego katalogu.

```
BOOL GetCurrentDirectory(CString& strDirName) const;

BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Parametry

*strDirName*<br/>
Odwołanie do ciągu, który będzie otrzymywał nazwę katalogu.

*pstrDirName*<br/>
Wskaźnik do ciągu, który będzie otrzymywał nazwę katalogu.

*lpdwLen*<br/>
Wskaźnik do typu DWORD, który zawiera następujące informacje:

|||
|-|-|
|Przy uruchamianiu|Rozmiar buforu odwołuje się *pstrDirName*.|
|Przy powrocie|Liczba znaków przechowywanych *pstrDirName*. Jeśli funkcja elementu członkowskiego nie powiedzie się, jak i ERROR_INSUFFICIENT_BUFFER ma zostać zwrócona, następnie *lpdwLen* zawiera liczbę bajtów, które aplikacji należy przydzielić w celu odbierania ciągu.|

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

Aby uzyskać nazwę katalogu jako adres URL zamiast tego, wywołaj [GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl).

Parametry *pstrDirName* lub *strDirName* może być albo częściowo kwalifikowane nazwy plików względem bieżącego katalogu lub w pełni kwalifikowana. Ukośnik odwrotny (\\) lub ukośnika (/) może być używany jako separator katalogu dla obu nazwy. `GetCurrentDirectory` wykonuje translację separatora nazwy katalogów na odpowiednie znaki, zanim zostaną użyte.

##  <a name="getcurrentdirectoryasurl"></a>  CFtpConnection::GetCurrentDirectoryAsURL

Wywołaj tę funkcję elementu członkowskiego, można uzyskać nazwy bieżącego katalogu jako adres URL.

```
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;

BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Parametry

*strDirName*<br/>
Odwołanie do ciągu, który będzie otrzymywał nazwę katalogu.

*pstrDirName*<br/>
Wskaźnik do ciągu, który będzie otrzymywał nazwę katalogu.

*lpdwLen*<br/>
Wskaźnik do typu DWORD, który zawiera następujące informacje:

|||
|-|-|
|Przy uruchamianiu|Rozmiar buforu odwołuje się *pstrDirName*.|
|Przy powrocie|Liczba znaków przechowywanych *pstrDirName*. Jeśli funkcja elementu członkowskiego nie powiedzie się, jak i ERROR_INSUFFICIENT_BUFFER ma zostać zwrócona, następnie *lpdwLen* zawiera liczbę bajtów, które aplikacji należy przydzielić w celu odbierania ciągu.|

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

`GetCurrentDirectoryAsURL` działa tak samo jak [GetCurrentDirectory](#getcurrentdirectory)

Parametr *strDirName* może być albo częściowo kwalifikowane nazwy plików względem bieżącego katalogu lub w pełni kwalifikowana. Ukośnik odwrotny (\\) lub ukośnika (/) może być używany jako separator katalogu dla obu nazwy. `GetCurrentDirectoryAsURL` wykonuje translację separatora nazwy katalogów na odpowiednie znaki, zanim zostaną użyte.

##  <a name="getfile"></a>  CFtpConnection::GetFile

Wywołaj tę funkcję elementu członkowskiego, aby pobrać plik z serwera FTP i zapisz go na komputerze lokalnym.

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

*pstrRemoteFile*<br/>
Wskaźnik na ciąg zakończony wartością null zawierający nazwę pliku do pobrania z serwera FTP.

*pstrLocalFile*<br/>
Wskaźnik na ciąg zakończony wartością null zawierający nazwę pliku do utworzenia w systemie lokalnym.

*bFailIfExists*<br/>
Wskazuje, czy nazwa pliku może być już używana przez istniejący plik. Jeśli nazwa lokalnego pliku już istnieje, a ten parametr ma wartość PRAWDA, `GetFile` zakończy się niepowodzeniem. W przeciwnym razie `GetFile` spowoduje usunięcie istniejących kopii pliku.

*dwAttributes*<br/>
Określa atrybuty pliku. Może to być dowolną kombinacją następujących flag FILE_ATTRIBUTE_ *.

- FILE_ATTRIBUTE_ARCHIVE plik jest plikiem archiwum. Aplikacje użyć tego atrybutu, aby oznaczyć pliki w kopii zapasowej lub usunięcia.

- FILE_ATTRIBUTE_COMPRESSED pliku lub katalogu jest skompresowany. Dla pliku kompresji oznacza, że wszystkie dane w pliku jest skompresowany. Dla katalogu kompresja jest ustawieniem domyślnym dla nowo tworzonych plików i podkatalogów.

- FILE_ATTRIBUTE_DIRECTORY pliku jest katalogiem.

- FILE_ATTRIBUTE_NORMAL pliku nie ma innych atrybutów zestawu. Ten atrybut jest prawidłowy tylko wtedy, gdy użyte bez parametrów. Wszystkie inne atrybuty pliku zastąpić FILE_ATTRIBUTE_NORMAL:

- FILE_ATTRIBUTE_HIDDEN pliku jest ukryty. Jest nie powinny zostać uwzględnione na liście zawartości katalogu zwykłej.

- FILE_ATTRIBUTE_READONLY plik jest tylko do odczytu. Aplikacje można odczytać pliku, ale nie można w nim zapisywać lub usunąć łącznik.

- FILE_ATTRIBUTE_SYSTEM plik jest częścią lub jest używana wyłącznie przez system operacyjny.

- FILE_ATTRIBUTE_TEMPORARY plik jest używany do tymczasowego przechowywania danych. Aplikacje należy zapisywać do pliku, tylko wtedy, gdy jest to absolutnie konieczne. Większość plików danych pozostaje w pamięci bez opróżnianych na nośniku, ponieważ plik zostanie wkrótce usunięty.

*dwFlags*<br/>
Określa warunki, na których występuje transferu. Ten parametr może być dowolny z *Flagidw* wartości opisane w [FtpGetFile](/windows/desktop/api/wininet/nf-wininet-ftpgetfilea) w zestawie Windows SDK.

*dwContext*<br/>
Identyfikator kontekstu do pobierania plików. Zobacz **uwagi** Aby uzyskać więcej informacji na temat *dwContext*.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

`GetFile` jest procedurę wysokiego poziomu, która obsługuje wszystkie obciążenia związanego z Odczyt pliku z serwera FTP i zapisuje ją lokalnie. Aplikacje, które tylko pobieranie plików danych lub które wymagają ścisłą kontrolę nad transferu plików, powinny używać `OpenFile` i [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read) zamiast tego.

Jeśli *Flagidw* FILE_TRANSFER_TYPE_ASCII, tłumaczenia pliku danych również konwertuje kontroli i formatowanie znaków na Windows odpowiedniki. Transfer domyślny jest trybie binarnym, gdzie plik jest pobierany w tym samym formacie, jak są przechowywane na serwerze.

Zarówno *pstrRemoteFile* i *pstrLocalFile* może być albo częściowo kwalifikowane nazwy plików względem bieżącego katalogu lub w pełni kwalifikowana. Ukośnik odwrotny (\\) lub ukośnika (/) może być używany jako separator katalogu dla obu nazwy. `GetFile` wykonuje translację separatora nazwy katalogów na odpowiednie znaki, zanim zostaną użyte.

Zastąp *dwContext* domyślne, aby ustawić identyfikator kontekstu do wybranej wartości. Identyfikator kontekstu jest skojarzony z tym działania związane z `CFtpConnection` obiekt utworzony przez jego [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu. Zwracana jest wartość [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) do udostępniania informacji o stanie operacji za pomocą którego jest identyfikowana. Zapoznaj się z artykułem [Internet pierwsze kroki: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.

##  <a name="openfile"></a>  CFtpConnection::OpenFile

Wywołaj tę funkcję elementu członkowskiego, aby otworzyć plik znajdujący się na serwerze FTP do odczytu lub zapisu.

```
CInternetFile* OpenFile(
    LPCTSTR pstrFileName,
    DWORD dwAccess = GENERIC_READ,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pstrFileName*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku, który ma zostać otwarty.

*dwAccess*<br/>
Określa, jak plik będzie dostępny. Może być GENERIC_READ lub GENERIC_WRITE, ale nie oba.

*dwFlags*<br/>
Określa warunki, w których kolejnych Transfer odbywa się. Może to być dowolny z następujących stałych FTP_TRANSFER_ *:

- FTP_TRANSFER_TYPE_ASCII pliku przesyła przy użyciu metody transferu FTP ASCII (typ A). Konwertuje kontroli i informacje o formatowaniu na lokalne odpowiedniki.

- FTP_TRANSFER_TYPE_BINARY pliku transfery danych za pomocą metody transferu obrazu FTP's, (Type I). Transfer danych plików w takiej postaci, jak istnieje, bez konieczności wprowadzania zmian. Jest to domyślna metoda transferu.

*dwContext*<br/>
Identyfikator kontekstu do otwierania pliku. Zobacz **uwagi** Aby uzyskać więcej informacji na temat *dwContext*.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CInternetFile](../../mfc/reference/cinternetfile-class.md) obiektu.

### <a name="remarks"></a>Uwagi

`OpenFile` należy użyć w następujących sytuacjach:

- Aplikacja ma dane, które musi być wysyłane oraz stworzony jako plik na serwerze FTP, jednak, że dane nie są w pliku lokalnym. Gdy `OpenFile` otwiera plik, aplikacja używa [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write) do wysyłania danych pliku FTP do serwera.

- Aplikacja musi pobrać plik z serwera i umieść ją w pamięci kontrolowane przez aplikację, zamiast zapisywania dysku. Aplikacja używa [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read) po użyciu `OpenFile` można otworzyć pliku.

- Aplikacja musi poprawnie poziom kontroli nad transferu plików. Aplikacja może na przykład chcesz wyświetlić postępu kontroli informowania o postępie stanu transferu plików, podczas pobierania pliku.

Po wywołaniu `OpenFile` i do momentu wywołania `CInternetConnection::Close`, aplikacja może wywołać tylko [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read), [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write), `CInternetConnection::Close`, lub [ CFtpFileFind::FindFile](../../mfc/reference/cftpfilefind-class.md#findfile). Wywołań do innych funkcji FTP dla tej samej sesji FTP ma zakończyć się niepowodzeniem i Ustaw kod błędu: FTP_ETRANSFER_IN_PROGRESS.

*PstrFileName* parametr może być albo częściowo kwalifikowane nazwy pliku względem bieżącego katalogu lub w pełni kwalifikowana. Ukośnik odwrotny (\\) lub ukośnika (/) może być używany jako separator katalogu dla obu nazwy. `OpenFile` wykonuje translację separatora nazwy katalogów na odpowiednie znaki, przed jego użyciem.

Zastąp *dwContext* domyślne, aby ustawić identyfikator kontekstu do wybranej wartości. Identyfikator kontekstu jest skojarzony z tym działania związane z `CFtpConnection` obiekt utworzony przez jego [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu. Zwracana jest wartość [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) do udostępniania informacji o stanie operacji za pomocą którego jest identyfikowana. Zapoznaj się z artykułem [Internet pierwsze kroki: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.

##  <a name="putfile"></a>  CFtpConnection::PutFile

Wywołaj tę funkcję elementu członkowskiego do przechowywania plików na serwerze FTP.

```
BOOL PutFile(
    LPCTSTR pstrLocalFile,
    LPCTSTR pstrRemoteFile,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pstrLocalFile*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku do wysłania z systemu lokalnego.

*pstrRemoteFile*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku do utworzenia na serwerze FTP.

*dwFlags*<br/>
Określa warunki, na których występuje transfer pliku. Może być dowolną ze stałych FTP_TRANSFER_ * opisanego w [OpenFile](#openfile).

*dwContext*<br/>
Identyfikator kontekstu umieszczenie pliku. Zobacz **uwagi** Aby uzyskać więcej informacji na temat *dwContext*.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

`PutFile` jest procedurę wysokiego poziomu, która obsługuje wszystkich operacji związanych z przechowywaniem plików na serwerze FTP. Aplikacje wysyłać tylko dane lub które wymagają ściślejszej kontroli nad transferu plików, powinny używać [OpenFile](#openfile) i [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write).

Zastąp `dwContext` domyślne, aby ustawić identyfikator kontekstu do wybranej wartości. Identyfikator kontekstu jest skojarzony z tym działania związane z `CFtpConnection` obiekt utworzony przez jego [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu. Zwracana jest wartość [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) do udostępniania informacji o stanie operacji za pomocą którego jest identyfikowana. Zapoznaj się z artykułem [Internet pierwsze kroki: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.

##  <a name="remove"></a>  CFtpConnection::Remove

Wywołaj tę funkcję elementu członkowskiego, aby usunąć określony plik z połączonego serwera.

```
BOOL Remove(LPCTSTR pstrFileName);
```

### <a name="parameters"></a>Parametry

*pstrFileName*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

*PstrFileName* parametr może być albo częściowo kwalifikowane nazwy pliku względem bieżącego katalogu lub w pełni kwalifikowana. Ukośnik odwrotny (\\) lub ukośnika (/) może być używany jako separator katalogu dla obu nazwy. `Remove` Funkcja tłumaczy separatora nazwy katalogów na odpowiednie znaki, zanim zostaną użyte.

##  <a name="removedirectory"></a>  CFtpConnection::RemoveDirectory

Wywołaj tę funkcję elementu członkowskiego, aby usunąć określony katalog z połączonego serwera.

```
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parametry

*pstrDirName*<br/>
Wskaźnik do ciągu zawierającego katalogu, który ma zostać usunięty.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

Użyj [GetCurrentDirectory](#getcurrentdirectory) można określić bieżącego katalogu roboczego serwera. Nie należy zakładać, że system zdalny połączył należy do katalogu głównego.

*PstrDirName* parametr może być częściowo lub w pełni kwalifikowaną nazwę względem bieżącego katalogu. Ukośnik odwrotny (\\) lub ukośnika (/) może być używany jako separator katalogu dla obu nazwy. `RemoveDirectory` wykonuje translację separatora nazwy katalogów na odpowiednie znaki, zanim zostaną użyte.

##  <a name="rename"></a>  CFtpConnection::Rename

Wywołaj tę funkcję elementu członkowskiego, aby zmienić nazwę określonego pliku na połączonym serwerze.

```
BOOL Rename(
    LPCTSTR pstrExisting,
    LPCTSTR pstrNew);
```

### <a name="parameters"></a>Parametry

*pstrExisting*<br/>
Wskaźnik do ciągu zawierającego nazwę bieżącego pliku, który można zmienić nazwy.

*pstrNew*<br/>
Wskaźnik do ciągu zawierającego nazwę nowego pliku.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

*PstrExisting* i *pstrNew* parametry mogą być albo częściowo kwalifikowane nazwy pliku względem bieżącego katalogu lub w pełni kwalifikowana. Ukośnik odwrotny (\\) lub ukośnika (/) może być używany jako separator katalogu dla obu nazwy. `Rename` wykonuje translację separatora nazwy katalogów na odpowiednie znaki, zanim zostaną użyte.

##  <a name="setcurrentdirectory"></a>  CFtpConnection::SetCurrentDirectory

Wywołaj tę funkcję elementu członkowskiego, aby przejść do innego katalogu na serwerze FTP.

```
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parametry

*pstrDirName*<br/>
Wskaźnik do ciągu zawierającego nazwę katalogu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

*PstrDirName* parametr może być częściowo lub w pełni kwalifikowaną nazwę względem bieżącego katalogu. Ukośnik odwrotny (\\) lub ukośnika (/) może być używany jako separator katalogu dla obu nazwy. `SetCurrentDirectory` wykonuje translację separatora nazwy katalogów na odpowiednie znaki, zanim zostaną użyte.

Użyj [GetCurrentDirectory](#getcurrentdirectory) Aby określić bieżący katalog roboczy serwer FTP. Nie należy zakładać, że system zdalny połączył należy do katalogu głównego.

## <a name="see-also"></a>Zobacz także

[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Klasa CInternetSession](../../mfc/reference/cinternetsession-class.md)
