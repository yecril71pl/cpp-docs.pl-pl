---
title: Klasa CFtpConnection
ms.date: 08/29/2019
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
ms.openlocfilehash: a1fe516869aa98cc291597211eee175ef591e45d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373774"
---
# <a name="cftpconnection-class"></a>Klasa CFtpConnection

Zarządza połączeniem FTP z serwerem internetowym i umożliwia bezpośrednią manipulację katalogami i plikami na tym serwerze.

## <a name="syntax"></a>Składnia

```
class CFtpConnection : public CInternetConnection
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFtpConnection::CFtpConnection](#cftpconnection)|Konstruuje `CFtpConnection` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFtpConnection::Polecenie](#command)|Wysyła polecenie bezpośrednio do serwera FTP.|
|[CFtpConnection::CreateDirectory](#createdirectory)|Tworzy katalog na serwerze.|
|[CFtpConnection::GetCurrentDirectory](#getcurrentdirectory)|Pobiera bieżący katalog dla tego połączenia.|
|[CFtpConnection::GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)|Pobiera bieżący katalog dla tego połączenia jako adres URL.|
|[CFtpConnection::GetFile](#getfile)|Pobiera plik z podłączonego serwera|
|[CFtpConnection::OpenFile](#openfile)|Otwiera plik na podłączonym serwerze.|
|[CFtpConnection::PutFile](#putfile)|Umieszcza plik na serwerze.|
|[CFtpConnection::Usuń](#remove)|Usuwa plik z serwera.|
|[CFtpConnection::Usuńkatedystykę](#removedirectory)|Usuwa określony katalog z serwera.|
|[CFtpConnection::Zmień nazwę](#rename)|Zmienia nazwę pliku na serwerze.|
|[CFtpConnection::SetCurrentDirectory](#setcurrentdirectory)|Ustawia bieżący katalog FTP.|

## <a name="remarks"></a>Uwagi

FTP jest jedną z trzech usług internetowych rozpoznawanych przez klasy MFC WinInet.

Aby komunikować się z serwerem internetowym FTP, należy najpierw utworzyć [wystąpienie CInternetSession](../../mfc/reference/cinternetsession-class.md), a następnie utworzyć `CFtpConnection` obiekt. Nigdy nie `CFtpConnection` tworzysz obiektu bezpośrednio; zamiast, wywołać [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection) `CFtpConnection` , który tworzy obiekt i zwraca wskaźnik do niego.

Aby dowiedzieć `CFtpConnection` się więcej o tym, jak działa z innymi klasami MFC Internet, zobacz artykuł [Programowanie internetowe z WinInet](../../mfc/win32-internet-extensions-wininet.md). Aby uzyskać więcej informacji na temat komunikowania się z pozostałymi dwiema obsługiwanymi usługami, HTTP i gopher, zobacz klasy [CHttpConnection](../../mfc/reference/chttpconnection-class.md) i [CGopherConnection](../../mfc/reference/cgopherconnection-class.md).

## <a name="example"></a>Przykład

  Zobacz przykład w omówienie klasy [CFtpFileFind.](../../mfc/reference/cftpfilefind-class.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Połączenie międzysystemowe CInternet](../../mfc/reference/cinternetconnection-class.md)

`CFtpConnection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

## <a name="cftpconnectioncftpconnection"></a><a name="cftpconnection"></a>CFtpConnection::CFtpConnection

Ta funkcja elementu członkowskiego `CFtpConnection` jest wywoływana do konstruowania obiektu.

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

*pSesja*<br/>
Wskaźnik do powiązanego [obiektu CInternetSession.](../../mfc/reference/cinternetsession-class.md)

*hPołączone*<br/>
Uchwyt systemu Windows bieżącej sesji internetowej.

*pstrServer (serwer pstrServer)*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera FTP.

*Dwcontext*<br/>
Identyfikator kontekstu dla operacji. *dwContext* identyfikuje informacje o stanie operacji zwrócone przez [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). Wartość domyślna jest ustawiona na 1; jednak można jawnie przypisać identyfikator określonego kontekstu dla operacji. Obiekt i wszelkie prace, które wykonuje, będą skojarzone z tym identyfikatorem kontekstu.

*pstrUserName*<br/>
Wskaźnik do ciągu zakończonego zerem, który określa nazwę użytkownika do logowania. Jeśli null, wartość domyślna jest anonimowa.

*pstr Hasło*<br/>
Wskaźnik do ciągu zakończonego wartością null, który określa hasło używane do logowania. Jeśli zarówno *pstrPassword,* jak i *pstrUserName* mają wartość NULL, domyślnym anonimowym hasłem jest nazwa e-mail użytkownika. Jeśli *pstrPassword* ma wartość NULL (lub pusty ciąg), ale *pstrUserName* nie ma wartości NULL, używane jest puste hasło. W poniższej tabeli opisano zachowanie czterech możliwych ustawień *pstrUserName* i *pstrPassword*:

|*pstrUserName*|*pstr Hasło*|Nazwa użytkownika wysłana do serwera FTP|Hasło wysłane do serwera FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL lub " " "|NULL lub " " "|"anonimowy"|Nazwa e-mail użytkownika|
|Ciąg nienawidkowy|NULL lub " " "|*pstrUserName*|" "|
|Ciąg null nienawidkowy|BŁĄD|BŁĄD||
|Ciąg nienawidkowy|Ciąg nienawidkowy|*pstrUserName*|*pstr Hasło*|

*Nport*<br/>
Liczba identyfikująca port TCP/IP do użycia na serwerze.

*bPasażerka*<br/>
Określa tryb pasywny lub aktywny dla tej sesji FTP. Jeśli ustawiona wartość TRUE, ustawia *dwFlag* interfejsu API Win32 do INTERNET_FLAG_PASSIVE.

### <a name="remarks"></a>Uwagi

Nigdy nie `CFtpConnection` tworzysz obiektu bezpośrednio. Zamiast tego wywołać [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection) `CFptConnection` , który tworzy obiekt.

## <a name="cftpconnectioncommand"></a><a name="command"></a>CFtpConnection::Polecenie

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
Wskaźnik do ciągu zawierającego polecenie, które ma zostać wysłane.

*eOdpowiedzialność*<br/>
Określa, czy oczekiwana jest odpowiedź z serwera FTP. Może być jedną z następujących wartości:

- `CmdRespNone`Nie oczekuje się odpowiedzi.
- `CmdRespRead`Oczekuje się odpowiedzi.
- `CmdRespWrite`Nie używane.

CmdResponseType jest członkiem CFtpConnection, zdefiniowanym w *afxinet.h*.

*Dwflags*<br/>
Wartość zawierająca flagi, które kontrolują tę funkcję. Aby uzyskać pełną listę, zobacz [FTPCommand](/windows/win32/api/wininet/nf-wininet-ftpcommandw).

*Dwcontext*<br/>
Wskaźnik do wartości zawierającej wartość zdefiniowaną przez aplikację używaną do identyfikowania kontekstu aplikacji w wywołaniach zwrotnych.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego emuluje funkcjonalność funkcji [FTPCommand,](/windows/win32/api/wininet/nf-wininet-ftpcommandw) zgodnie z opisem w windows SDK.

Jeśli wystąpi błąd, MFC zgłasza wyjątek typu [CInternetException](../../mfc/reference/cinternetexception-class.md).

## <a name="cftpconnectioncreatedirectory"></a><a name="createdirectory"></a>CFtpConnection::CreateDirectory

Wywołanie tej funkcji elementu członkowskiego, aby utworzyć katalog na podłączonym serwerze.

```
BOOL CreateDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parametry

*pstrDirName (nazwa pstrDirname)*<br/>
Wskaźnik do ciągu zawierającego nazwę katalogu do utworzenia.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, funkcja systemu Windows [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

Służy `GetCurrentDirectory` do określania bieżącego katalogu roboczego dla tego połączenia z serwerem. Nie należy zakładać, że system zdalny połączył cię z katalogiem głównym.

Parametr `pstrDirName` może być częściowo lub w pełni kwalifikowaną nazwę pliku w stosunku do bieżącego katalogu. Ukośnik\\odwrotny ( ) lub ukośnik do przodu (/) może służyć jako separator katalogu dla każdej nazwy. `CreateDirectory`tłumaczy separatory nazw katalogów na odpowiednie znaki, zanim zostaną użyte.

## <a name="cftpconnectiongetcurrentdirectory"></a><a name="getcurrentdirectory"></a>CFtpConnection::GetCurrentDirectory

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać nazwę bieżącego katalogu.

```
BOOL GetCurrentDirectory(CString& strDirName) const;

BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Parametry

*nazwa strDirname*<br/>
Odwołanie do ciągu, który otrzyma nazwę katalogu.

*pstrDirName (nazwa pstrDirname)*<br/>
Wskaźnik do ciągu, który otrzyma nazwę katalogu.

*lpdwLen ( lpdwLen )*<br/>
Wskaźnik do DWORD, który zawiera następujące informacje:

|||
|-|-|
|Przy wejściu|Rozmiar buforu, do którego odwołuje się *pstrDirName*.|
|Po powrocie|Liczba znaków przechowywanych w *pstrDirName*. Jeśli funkcja elementu członkowskiego nie powiedzie się i ERROR_INSUFFICIENT_BUFFER jest zwracana, a następnie *lpdwLen* zawiera liczbę bajtów, które aplikacja musi przydzielić w celu odebrania ciągu.|

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, funkcja Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

Aby zamiast tego uzyskać nazwę katalogu jako adres URL, zadzwoń do [getcurrentdirectoryasurl](#getcurrentdirectoryasurl).

Parametry *pstrDirName* lub *strDirName* mogą być częściowo kwalifikowanymi nazwami plików względem bieżącego katalogu lub w pełni kwalifikowanymi. Ukośnik\\odwrotny ( ) lub ukośnik do przodu (/) może służyć jako separator katalogu dla każdej nazwy. `GetCurrentDirectory`tłumaczy separatory nazw katalogów na odpowiednie znaki, zanim zostaną użyte.

## <a name="cftpconnectiongetcurrentdirectoryasurl"></a><a name="getcurrentdirectoryasurl"></a>CFtpConnection::GetCurrentDirectoryAsURL

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać nazwę bieżącego katalogu jako adres URL.

```
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;

BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Parametry

*nazwa strDirname*<br/>
Odwołanie do ciągu, który otrzyma nazwę katalogu.

*pstrDirName (nazwa pstrDirname)*<br/>
Wskaźnik do ciągu, który otrzyma nazwę katalogu.

*lpdwLen ( lpdwLen )*<br/>
Wskaźnik do DWORD, który zawiera następujące informacje:

|||
|-|-|
|Przy wejściu|Rozmiar buforu, do którego odwołuje się *pstrDirName*.|
|Po powrocie|Liczba znaków przechowywanych w *pstrDirName*. Jeśli funkcja elementu członkowskiego nie powiedzie się i ERROR_INSUFFICIENT_BUFFER jest zwracana, a następnie *lpdwLen* zawiera liczbę bajtów, które aplikacja musi przydzielić w celu odebrania ciągu.|

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, funkcja Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

`GetCurrentDirectoryAsURL`zachowuje się tak samo jak [Program GetCurrentDirectory](#getcurrentdirectory)

Parametr *strDirName* może być częściowo kwalifikowane nazwy plików w stosunku do bieżącego katalogu lub w pełni kwalifikowany. Ukośnik\\odwrotny ( ) lub ukośnik do przodu (/) może służyć jako separator katalogu dla każdej nazwy. `GetCurrentDirectoryAsURL`tłumaczy separatory nazw katalogów na odpowiednie znaki, zanim zostaną użyte.

## <a name="cftpconnectiongetfile"></a><a name="getfile"></a>CFtpConnection::GetFile

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać plik z serwera FTP i przechowywać go na komputerze lokalnym.

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
Wskaźnik do ciągu zakończonego wartością null zawierającego nazwę pliku do pobrania z serwera FTP.

*pstrLocalFile (Plik lokalialny)*<br/>
Wskaźnik do ciągu zakończonego wartością null zawierającego nazwę pliku do utworzenia w systemie lokalnym.

*bFailIfExists (Niebezpieczeństwo)*<br/>
Wskazuje, czy nazwa pliku może być już używana przez istniejący plik. Jeśli lokalna nazwa pliku już istnieje, a `GetFile` ten parametr ma wartość PRAWDA, kończy się niepowodzeniem. W `GetFile` przeciwnym razie usunie istniejącą kopię pliku.

*dwAttributes (przyw.*<br/>
Wskazuje atrybuty pliku. Może to być dowolna kombinacja następujących flag FILE_ATTRIBUTE_*.

- FILE_ATTRIBUTE_ARCHIVE Plik jest plikiem archiwum. Aplikacje używają tego atrybutu do oznaczania plików do tworzenia kopii zapasowych lub usuwania.

- FILE_ATTRIBUTE_COMPRESSED Plik lub katalog jest skompresowany. W przypadku pliku kompresja oznacza, że wszystkie dane w pliku są kompresowane. W przypadku katalogu kompresja jest wartością domyślną dla nowo utworzonych plików i podkatalogów.

- FILE_ATTRIBUTE_DIRECTORY Plik jest katalogiem.

- FILE_ATTRIBUTE_NORMAL Plik nie ma ustawionego żadnych innych atrybutów. Ten atrybut jest prawidłowy tylko wtedy, gdy jest używany samodzielnie. Wszystkie inne atrybuty plików zastępują FILE_ATTRIBUTE_NORMAL:

- FILE_ATTRIBUTE_HIDDEN Plik jest ukryty. Nie należy go włączać do zwykłej listy katalogów.

- FILE_ATTRIBUTE_READONLY Plik jest tylko do odczytu. Aplikacje mogą odczytać plik, ale nie mogą go zapisać ani usunąć.

- FILE_ATTRIBUTE_SYSTEM Plik jest częścią lub jest używany wyłącznie przez system operacyjny.

- FILE_ATTRIBUTE_TEMPORARY Plik jest używany do przechowywania tymczasowego. Aplikacje powinny zapisywać do pliku tylko wtedy, gdy jest to absolutnie konieczne. Większość danych pliku pozostaje w pamięci bez opróżnienia na nośnik, ponieważ plik zostanie wkrótce usunięty.

*Dwflags*<br/>
Określa warunki, w jakich następuje transfer. Ten parametr może być dowolną z wartości *dwFlags* opisane w [FtpGetFile](/windows/win32/api/wininet/nf-wininet-ftpgetfilew) w windows SDK.

*Dwcontext*<br/>
Identyfikator kontekstu pobierania pliku. Zobacz **Uwagi, aby** uzyskać więcej informacji na temat *dwContext*.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, funkcja Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

`GetFile`to procedura wysokiego poziomu, która obsługuje wszystkie obciążenie związane z odczytaniem pliku z serwera FTP i przechowywaniem go lokalnie. Aplikacje, które pobierają tylko dane plików lub które wymagają `OpenFile` ścisłej kontroli nad transferem plików, powinny używać i [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read) zamiast tego.

Jeśli *dwFlags* jest FILE_TRANSFER_TYPE_ASCII, tłumaczenie danych plików konwertuje również znaki kontroli i formatowania na odpowiedniki systemu Windows. Transfer domyślny to tryb binarny, w którym plik jest pobierany w tym samym formacie, w jakim jest przechowywany na serwerze.

Zarówno *pstrRemoteFile,* jak i *pstrLocalFile* mogą być częściowo kwalifikowanymi nazwami plików w stosunku do bieżącego katalogu lub w pełni kwalifikowanymi. Ukośnik\\odwrotny ( ) lub ukośnik do przodu (/) może służyć jako separator katalogu dla każdej nazwy. `GetFile`tłumaczy separatory nazw katalogów na odpowiednie znaki, zanim zostaną użyte.

Zastąd w ustawieniach domyślnego *dwContext,* aby ustawić identyfikator kontekstu na wartość wybranej. Identyfikator kontekstu jest skojarzony z tą `CFtpConnection` określoną operacją obiektu utworzonego przez jego [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu. Wartość jest zwracana do [CInternetSession::OnStatusCallback,](../../mfc/reference/cinternetsession-class.md#onstatuscallback) aby zapewnić stan operacji, z którą jest identyfikowany. Zobacz artykuł [Pierwsze kroki internetowe: WinInet, aby](../../mfc/wininet-basics.md) uzyskać więcej informacji na temat identyfikatora kontekstu.

## <a name="cftpconnectionopenfile"></a><a name="openfile"></a>CFtpConnection::OpenFile

Wywołanie tej funkcji elementu członkowskiego, aby otworzyć plik znajdujący się na serwerze FTP do odczytu lub zapisu.

```
CInternetFile* OpenFile(
    LPCTSTR pstrFileName,
    DWORD dwAccess = GENERIC_READ,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*nazwa pliku pstrFile*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku, który ma zostać otwarty.

*dwAccess*<br/>
Określa, w jaki sposób plik będzie dostępny. Może być GENERIC_READ lub GENERIC_WRITE, ale nie oba.

*Dwflags*<br/>
Określa warunki, w jakich występują kolejne transfery. Może to być dowolny z następujących FTP_TRANSFER_* stałych:

- FTP_TRANSFER_TYPE_ASCII Transfery plików przy użyciu metody transferu FTP ASCII (typ A). Konwertuje informacje o kontroli i formatowaniu na lokalne odpowiedniki.

- FTP_TRANSFER_TYPE_BINARY Plik przesyła dane przy użyciu metody transferu obrazu FTP (typ I). Plik przesyła dane dokładnie tak, jak istnieje, bez żadnych zmian. Jest to domyślna metoda transferu.

*Dwcontext*<br/>
Identyfikator kontekstu do otwierania pliku. Zobacz **Uwagi, aby** uzyskać więcej informacji na temat *dwContext*.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [obiektu CInternetFile.](../../mfc/reference/cinternetfile-class.md)

### <a name="remarks"></a>Uwagi

`OpenFile`należy stosować w następujących sytuacjach:

- Aplikacja ma dane, które muszą być wysyłane i tworzone jako plik na serwerze FTP, ale dane te nie są w pliku lokalnym. Po `OpenFile` otwarciu pliku aplikacja używa [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write) do wysyłania danych pliku FTP do serwera.

- Aplikacja musi pobrać plik z serwera i umieścić go w pamięci kontrolowanej przez aplikację, zamiast zapisywać go na dysku. Aplikacja używa [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read) po `OpenFile` użyciu, aby otworzyć plik.

- Aplikacja wymaga precyzyjnego poziomu kontroli nad transferem plików. Na przykład aplikacja może chcieć wyświetlić formant postępu wskazać postęp stanu transferu plików podczas pobierania pliku.

Po `OpenFile` wywołaniu `CInternetConnection::Close`i do momentu wywołania aplikacja może wywołać tylko [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read), [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write), `CInternetConnection::Close`lub [CFtpFileFind::FindFile](../../mfc/reference/cftpfilefind-class.md#findfile). Wywołania innych funkcji FTP dla tej samej sesji FTP zakończy się niepowodzeniem i ustawić kod błędu, aby FTP_ETRANSFER_IN_PROGRESS.

Parametr *pstrFileName* może być częściowo kwalifikowaną nazwęą pliku względem bieżącego katalogu lub w pełni kwalifikowany. Ukośnik\\odwrotny ( ) lub ukośnik do przodu (/) może służyć jako separator katalogu dla każdej nazwy. `OpenFile`przed użyciem separatory nazw katalogu na odpowiednie znaki.

Zastąd w ustawieniach domyślnego *dwContext,* aby ustawić identyfikator kontekstu na wartość wybranej. Identyfikator kontekstu jest skojarzony z tą `CFtpConnection` określoną operacją obiektu utworzonego przez jego [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu. Wartość jest zwracana do [CInternetSession::OnStatusCallback,](../../mfc/reference/cinternetsession-class.md#onstatuscallback) aby zapewnić stan operacji, z którą jest identyfikowany. Zobacz artykuł [Pierwsze kroki internetowe: WinInet, aby](../../mfc/wininet-basics.md) uzyskać więcej informacji na temat identyfikatora kontekstu.

## <a name="cftpconnectionputfile"></a><a name="putfile"></a>CFtpConnection::PutFile

Wywołanie tej funkcji członkowskiej do przechowywania pliku na serwerze FTP.

```
BOOL PutFile(
    LPCTSTR pstrLocalFile,
    LPCTSTR pstrRemoteFile,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pstrLocalFile (Plik lokalialny)*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku do wysłania z systemu lokalnego.

*pstrRemoteFile*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku do utworzenia na serwerze FTP.

*Dwflags*<br/>
Określa warunki, w jakich następuje przeniesienie pliku. Może to być dowolny z FTP_TRANSFER_* stałych opisanych w [pliku OpenFile](#openfile).

*Dwcontext*<br/>
Identyfikator kontekstu do umieszczenia pliku. Zobacz **Uwagi, aby** uzyskać więcej informacji na temat *dwContext*.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, funkcja Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

`PutFile`to procedura wysokiego poziomu, która obsługuje wszystkie operacje związane z przechowywaniem pliku na serwerze FTP. Aplikacje, które wysyłają tylko dane lub wymagają ściślejszej kontroli nad transferem plików, powinny używać [Plików OpenFile](#openfile) i [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write).

Zastąd `dwContext` w polu domyślnym należy ustawić identyfikator kontekstu na wartość według wyboru. Identyfikator kontekstu jest skojarzony z tą `CFtpConnection` określoną operacją obiektu utworzonego przez jego [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu. Wartość jest zwracana do [CInternetSession::OnStatusCallback,](../../mfc/reference/cinternetsession-class.md#onstatuscallback) aby zapewnić stan operacji, z którą jest identyfikowany. Zobacz artykuł [Pierwsze kroki internetowe: WinInet, aby](../../mfc/wininet-basics.md) uzyskać więcej informacji na temat identyfikatora kontekstu.

## <a name="cftpconnectionremove"></a><a name="remove"></a>CFtpConnection::Usuń

Wywołanie tej funkcji elementu członkowskiego, aby usunąć określony plik z podłączonego serwera.

```
BOOL Remove(LPCTSTR pstrFileName);
```

### <a name="parameters"></a>Parametry

*nazwa pliku pstrFile*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, funkcja Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

Parametr *pstrFileName* może być częściowo kwalifikowaną nazwęą pliku względem bieżącego katalogu lub w pełni kwalifikowany. Ukośnik\\odwrotny ( ) lub ukośnik do przodu (/) może służyć jako separator katalogu dla każdej nazwy. Funkcja `Remove` tłumaczy separatory nazw katalogów na odpowiednie znaki, zanim zostaną użyte.

## <a name="cftpconnectionremovedirectory"></a><a name="removedirectory"></a>CFtpConnection::Usuńkatedystykę

Wywołanie tej funkcji elementu członkowskiego, aby usunąć określony katalog z podłączonego serwera.

```
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parametry

*pstrDirName (nazwa pstrDirname)*<br/>
Wskaźnik do ciągu zawierającego katalog do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, funkcja Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

Użyj [GetCurrentDirectory,](#getcurrentdirectory) aby określić bieżący katalog roboczy serwera. Nie należy zakładać, że system zdalny połączył cię z katalogiem głównym.

Parametr *pstrDirName* może być częściowo lub w pełni kwalifikowaną nazwę pliku w stosunku do bieżącego katalogu. Ukośnik\\odwrotny ( ) lub ukośnik do przodu (/) może służyć jako separator katalogu dla każdej nazwy. `RemoveDirectory`tłumaczy separatory nazw katalogów na odpowiednie znaki, zanim zostaną użyte.

## <a name="cftpconnectionrename"></a><a name="rename"></a>CFtpConnection::Zmień nazwę

Wywołanie tej funkcji elementu członkowskiego, aby zmienić nazwę określonego pliku na podłączonym serwerze.

```
BOOL Rename(
    LPCTSTR pstrExisting,
    LPCTSTR pstrNew);
```

### <a name="parameters"></a>Parametry

*pstrExisting*<br/>
Wskaźnik do ciągu zawierającego bieżącą nazwę pliku, który ma zostać zmieniony.

*pstrNowy*<br/>
Wskaźnik do ciągu zawierającego nową nazwę pliku.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, funkcja Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

*PstrExisting* i *pstrNew* parametry mogą być częściowo kwalifikowaną nazwę pliku w stosunku do bieżącego katalogu lub w pełni kwalifikowany. Ukośnik\\odwrotny ( ) lub ukośnik do przodu (/) może służyć jako separator katalogu dla każdej nazwy. `Rename`tłumaczy separatory nazw katalogów na odpowiednie znaki, zanim zostaną użyte.

## <a name="cftpconnectionsetcurrentdirectory"></a><a name="setcurrentdirectory"></a>CFtpConnection::SetCurrentDirectory

Wywołanie tej funkcji elementu członkowskiego, aby zmienić do innego katalogu na serwerze FTP.

```
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parametry

*pstrDirName (nazwa pstrDirname)*<br/>
Wskaźnik do ciągu zawierającego nazwę katalogu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, funkcja Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

Parametr *pstrDirName* może być częściowo lub w pełni kwalifikowaną nazwę pliku w stosunku do bieżącego katalogu. Ukośnik\\odwrotny ( ) lub ukośnik do przodu (/) może służyć jako separator katalogu dla każdej nazwy. `SetCurrentDirectory`tłumaczy separatory nazw katalogów na odpowiednie znaki, zanim zostaną użyte.

Użyj [programu GetCurrentDirectory,](#getcurrentdirectory) aby określić bieżący katalog roboczy serwera FTP. Nie należy zakładać, że system zdalny połączył cię z katalogiem głównym.

## <a name="see-also"></a>Zobacz też

[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Klasa CInternetSession](../../mfc/reference/cinternetsession-class.md)
