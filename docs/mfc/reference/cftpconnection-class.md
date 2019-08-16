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
ms.openlocfilehash: 977a8c9fc6dd653a59434d29bb72b0fe28900001
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506373"
---
# <a name="cftpconnection-class"></a>Klasa CFtpConnection

Zarządza połączeniem FTP z serwerem internetowym i umożliwia bezpośrednie manipulowanie katalogami i plikami na tym serwerze.

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
|[CFtpConnection:: polecenie](#command)|Wysyła polecenie bezpośrednio do serwera FTP.|
|[CFtpConnection::CreateDirectory](#createdirectory)|Tworzy katalog na serwerze.|
|[CFtpConnection::GetCurrentDirectory](#getcurrentdirectory)|Pobiera bieżący katalog dla tego połączenia.|
|[CFtpConnection::GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)|Pobiera bieżący katalog dla tego połączenia jako adres URL.|
|[CFtpConnection::GetFile](#getfile)|Pobiera plik z podłączonego serwera|
|[CFtpConnection:: OpenFile](#openfile)|Otwiera plik na połączonym serwerze.|
|[CFtpConnection::P utFile](#putfile)|Umieszcza plik na serwerze.|
|[CFtpConnection::Remove](#remove)|Usuwa plik z serwera.|
|[CFtpConnection::RemoveDirectory](#removedirectory)|Usuwa określony katalog z serwera.|
|[CFtpConnection:: Rename](#rename)|Zmienia nazwę pliku na serwerze.|
|[CFtpConnection::SetCurrentDirectory](#setcurrentdirectory)|Ustawia bieżący katalog FTP.|

## <a name="remarks"></a>Uwagi

FTP jest jedną z trzech usług internetowych uznawanych przez klasy MFC WinInet.

Aby komunikować się z serwerem internetowym FTP, należy najpierw utworzyć wystąpienie elementu [CInternetSession](../../mfc/reference/cinternetsession-class.md), a następnie utworzyć `CFtpConnection` obiekt. Nie utworzysz `CFtpConnection` bezpośrednio obiektu. zamiast tego wywołaj [CInternetSession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection) `CFtpConnection` , który tworzy obiekt i zwraca do niego wskaźnik.

Aby dowiedzieć się więcej `CFtpConnection` o tym, jak działa z innymi klasami internetowymi MFC, zobacz artykuł [programowanie internetowe za pomocą usługi WinInet](../../mfc/win32-internet-extensions-wininet.md). Aby uzyskać więcej informacji na temat komunikacji z innymi dwiema obsługiwanymi usługami, HTTP i gopher, zobacz klasy [CHttpConnection](../../mfc/reference/chttpconnection-class.md) i [CGopherConnection](../../mfc/reference/cgopherconnection-class.md).

## <a name="example"></a>Przykład

  Zobacz przykład w omówieniu klasy [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CFtpConnection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet. h

##  <a name="cftpconnection"></a>CFtpConnection::CFtpConnection

Ta funkcja członkowska jest wywoływana w celu `CFtpConnection` skonstruowania obiektu.

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
Wskaźnik do powiązanego obiektu [CInternetSession](../../mfc/reference/cinternetsession-class.md) .

*hConnected*<br/>
Dojście systemu Windows bieżącej sesji internetowej.

*pstrServer*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera FTP.

*dwContext*<br/>
Identyfikator kontekstu dla operacji. *dwContext* identyfikuje informacje o stanie operacji zwrócone przez [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). Wartość domyślna to 1; można jednak jawnie przypisać określony identyfikator kontekstu dla operacji. Obiekt i wszystkie wykonane zadania zostaną skojarzone z tym IDENTYFIKATORem kontekstu.

*pstrUserName*<br/>
Wskaźnik na ciąg zakończony znakiem null, który określa nazwę użytkownika do zalogowania. Jeśli wartość jest równa NULL, wartość domyślna to anonimowe.

*pstrPassword*<br/>
Wskaźnik do ciągu zakończonego wartością null, który określa hasło, które ma być używane do logowania. Jeśli zarówno *pstrPassword* , jak i *pstrUserName* mają wartość null, domyślnym hasłem anonimowym jest nazwa e-mail użytkownika. Jeśli *pstrPassword* ma wartość null (lub ciąg pusty), ale *pstrUserName* nie ma wartości null, używane jest puste hasło. W poniższej tabeli opisano zachowanie czterech możliwych ustawień *pstrUserName* i *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Nazwa użytkownika wysłana do serwera FTP|Hasło wysyłane do serwera FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL lub ""|NULL lub ""|anonimowe|Nazwa e-mail użytkownika|
|Ciąg o wartości innej niż NULL|NULL lub ""|*pstrUserName*|" "|
|Pusty ciąg o wartości innej niż NULL|BŁĄD|BŁĄD||
|Ciąg o wartości innej niż NULL|Ciąg o wartości innej niż NULL|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
Numer identyfikujący port TCP/IP, który ma być używany na serwerze.

*bPassive*<br/>
Określa tryb pasywny lub aktywny dla tej sesji FTP. Jeśli ustawiono wartość TRUE, ustawia Win32 API *dwFlag* na INTERNET_FLAG_PASSIVE.

### <a name="remarks"></a>Uwagi

Nie utworzysz `CFtpConnection` bezpośrednio obiektu. Zamiast tego należy wywołać metodę [CInternetSession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), która `CFptConnection` tworzy obiekt.

##  <a name="command"></a>CFtpConnection:: polecenie

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
Wskaźnik do ciągu zawierającego polecenie do wysłania.

*eResponse*<br/>
Określa, czy oczekiwano odpowiedzi z serwera FTP. Może być jedną z następujących wartości:

- `CmdRespNone`Nie oczekiwano odpowiedzi.

- `CmdRespRead`Oczekiwana jest odpowiedź.

*flagiDW*<br/>
Wartość zawierająca flagi kontrolujące tę funkcję. Aby uzyskać pełną listę, zobacz [FTPCommand](/windows/win32/api/wininet/nf-wininet-ftpcommandw).

*dwContext*<br/>
Wskaźnik do wartości zawierającej wartość zdefiniowaną przez aplikację służącą do identyfikowania kontekstu aplikacji w wywołaniach zwrotnych.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska emuluje funkcjonalność funkcji [FTPCommand](/windows/win32/api/wininet/nf-wininet-ftpcommandw) , zgodnie z opisem w Windows SDK.

Jeśli wystąpi błąd, MFC zgłosi wyjątek typu [CInternetException](../../mfc/reference/cinternetexception-class.md).

##  <a name="createdirectory"></a>CFtpConnection:: \ katalog

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć katalog na połączonym serwerze.

```
BOOL CreateDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parametry

*pstrDirName*<br/>
Wskaźnik do ciągu zawierającego nazwę katalogu do utworzenia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, może zostać wywołana funkcja [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) funkcji systemu Windows w celu określenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

Użyj `GetCurrentDirectory` , aby określić bieżący katalog roboczy dla tego połączenia z serwerem. Nie należy zakładać, że system zdalny nawiązał połączenie z katalogiem głównym.

`pstrDirName` Parametr może być częściowo lub w pełni kwalifikowana nazwa pliku względem bieżącego katalogu. Ukośnika odwrotnego\\() lub ukośnika (/) można użyć jako separatora katalogu dla każdej nazwy. `CreateDirectory`tłumaczy separatory nazw katalogów na odpowiednie znaki przed ich użyciem.

##  <a name="getcurrentdirectory"></a>CFtpConnection::GetCurrentDirectory

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
|Przy wpisie|Rozmiar buforu, do którego odwołuje się *pstrDirName*.|
|Przy zwrocie|Liczba znaków przechowywanych do *pstrDirName*. Jeśli funkcja członkowska nie powiedzie się i zostanie zwrócona wartość ERROR_INSUFFICIENT_BUFFER, *lpdwLen* zawiera liczbę bajtów, które aplikacja musi przydzielić, aby otrzymać ciąg.|

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, może zostać wywołana [wartość GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) funkcji Win32, aby określić przyczynę błędu.

### <a name="remarks"></a>Uwagi

Aby zamiast tego uzyskać nazwę katalogu jako adres URL, wywołaj [GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl).

Parametry *pstrDirName* lub *strdirname* mogą być częściowo kwalifikowanymi nazwami plików względem bieżącego katalogu lub w pełni kwalifikowanych. Ukośnika odwrotnego\\() lub ukośnika (/) można użyć jako separatora katalogu dla każdej nazwy. `GetCurrentDirectory`tłumaczy separatory nazw katalogów na odpowiednie znaki przed ich użyciem.

##  <a name="getcurrentdirectoryasurl"></a>CFtpConnection::GetCurrentDirectoryAsURL

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać nazwę bieżącego katalogu jako adres URL.

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
|Przy wpisie|Rozmiar buforu, do którego odwołuje się *pstrDirName*.|
|Przy zwrocie|Liczba znaków przechowywanych do *pstrDirName*. Jeśli funkcja członkowska nie powiedzie się i zostanie zwrócona wartość ERROR_INSUFFICIENT_BUFFER, *lpdwLen* zawiera liczbę bajtów, które aplikacja musi przydzielić, aby otrzymać ciąg.|

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, może zostać wywołana [wartość GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) funkcji Win32, aby określić przyczynę błędu.

### <a name="remarks"></a>Uwagi

`GetCurrentDirectoryAsURL`zachowuje się tak samo jak [GetCurrentDirectory](#getcurrentdirectory)

Parametr *strdirname* może być częściowo kwalifikowanymi nazwami plików względem bieżącego katalogu lub w pełni kwalifikowany. Ukośnika odwrotnego\\() lub ukośnika (/) można użyć jako separatora katalogu dla każdej nazwy. `GetCurrentDirectoryAsURL`tłumaczy separatory nazw katalogów na odpowiednie znaki przed ich użyciem.

##  <a name="getfile"></a>CFtpConnection:: GetFile

Wywołaj tę funkcję elementu członkowskiego, aby pobrać plik z serwera FTP i zapisać go na komputerze lokalnym.

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
Wskaźnik do ciągu zakończonego wartością null zawierający nazwę pliku, który ma zostać pobrany z serwera FTP.

*pstrLocalFile*<br/>
Wskaźnik do ciągu zakończonego wartością null zawierający nazwę pliku do utworzenia w systemie lokalnym.

*bFailIfExists*<br/>
Wskazuje, czy nazwa pliku może być już używana przez istniejący plik. Jeśli lokalna nazwa pliku już istnieje, a ten parametr ma wartość true, `GetFile` kończy się niepowodzeniem. W przeciwnym razie zostanie wymazana istniejąca kopia pliku. `GetFile`

*dwAttributes*<br/>
Wskazuje atrybuty pliku. Może to być dowolna kombinacja następujących flag FILE_ATTRIBUTE_ *.

- FILE_ATTRIBUTE_ARCHIVE plik jest plikiem archiwum. Aplikacje używają tego atrybutu do oznaczania plików do utworzenia kopii zapasowej lub usunięcia.

- FILE_ATTRIBUTE_COMPRESSED plik lub katalog jest skompresowany. W przypadku pliku kompresja oznacza, że wszystkie dane w pliku są skompresowane. W przypadku katalogu kompresja jest wartością domyślną dla nowo utworzonych plików i podkatalogów.

- FILE_ATTRIBUTE_DIRECTORY plik jest katalogiem.

- FILE_ATTRIBUTE_NORMAL plik nie ma żadnych innych atrybutów. Ten atrybut jest prawidłowy tylko wtedy, gdy jest używany samodzielnie. Wszystkie inne atrybuty pliku przesłaniają FILE_ATTRIBUTE_NORMAL:

- FILE_ATTRIBUTE_HIDDEN plik jest ukryty. Nie jest on uwzględniony w zwykłej liście katalogów.

- FILE_ATTRIBUTE_READONLY plik jest tylko do odczytu. Aplikacje mogą odczytywać pliki, ale nie mogą ich zapisywać ani usuwać.

- FILE_ATTRIBUTE_SYSTEM plik jest częścią lub jest używany wyłącznie przez system operacyjny.

- FILE_ATTRIBUTE_TEMPORARY plik jest używany na potrzeby magazynu tymczasowego. Aplikacje powinny zapisywać do pliku tylko wtedy, gdy jest to absolutnie konieczne. Większość danych pliku pozostaje w pamięci bez opróżniania na nośnik, ponieważ plik zostanie wkrótce usunięty.

*flagiDW*<br/>
Określa warunki, w których odbywa się transfer. Ten parametr może być dowolną wartością *flagiDW* opisaną w [FtpGetFile](/windows/win32/api/wininet/nf-wininet-ftpgetfilew) w Windows SDK.

*dwContext*<br/>
Identyfikator kontekstu pobierania pliku. Aby uzyskać więcej informacji na temat *dwContext*, zobacz **uwagi** .

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, może zostać wywołana [wartość GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) funkcji Win32, aby określić przyczynę błędu.

### <a name="remarks"></a>Uwagi

`GetFile`to procedura wysokiego poziomu, która obsługuje wszystkie obciążenia związane z odczytem pliku z serwera FTP i przechowywanie go lokalnie. Aplikacje, które pobierają tylko dane plików, lub które wymagają ścisłej kontroli nad transferem plików `OpenFile` , powinny używać i [CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read) .

Jeśli *flagiDW* jest FILE_TRANSFER_TYPE_ASCII, tłumaczenie danych plików również konwertuje znaki kontrolne i formatowania na odpowiedniki systemu Windows. Domyślny transfer jest trybem binarnym, w którym plik jest pobierany w tym samym formacie, w jakim jest przechowywany na serwerze.

Zarówno *pstrRemoteFile* , jak i *pstrLocalFile* mogą być częściowo kwalifikowanymi nazwami plików względem bieżącego katalogu lub w pełni kwalifikowanych. Ukośnika odwrotnego\\() lub ukośnika (/) można użyć jako separatora katalogu dla każdej nazwy. `GetFile`tłumaczy separatory nazw katalogów na odpowiednie znaki przed ich użyciem.

Zastąp wartości domyślne *dwContext* , aby ustawić identyfikator kontekstu na wybraną wartość. Identyfikator kontekstu jest skojarzony z tą konkretną operacją `CFtpConnection` obiektu utworzonego przez obiekt [CInternetSession](../../mfc/reference/cinternetsession-class.md) . Wartość jest zwracana do [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) w celu udostępnienia stanu operacji, z którą jest identyfikowany. Zapoznaj się [z artykułem internetowym pierwsze kroki: WinInet](../../mfc/wininet-basics.md) , aby uzyskać więcej informacji na temat identyfikatora kontekstu.

##  <a name="openfile"></a>CFtpConnection:: OpenFile

Wywołaj tę funkcję elementu członkowskiego, aby otworzyć plik znajdujący się na serwerze FTP w celu odczytu lub zapisu.

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
Określa, w jaki sposób będzie uzyskiwany dostęp do pliku. Może to być GENERIC_READ lub GENERIC_WRITE, ale nie oba jednocześnie.

*flagiDW*<br/>
Określa warunki, w których odbywa się kolejne transfery. Może to być dowolny z następujących stałych FTP_TRANSFER_ *:

- FTP_TRANSFER_TYPE_ASCII transfery plików przy użyciu metody transferu protokołu FTP ASCII (Type A). Konwertuje informacje o kontrolkach i formatowaniu na lokalne odpowiedniki.

- FTP_TRANSFER_TYPE_BINARY przesyła dane przy użyciu metody transferu obrazu (typu I) FTP. Plik przesyła dane dokładnie tak, jak istnieje, bez zmian. Jest to domyślna metoda transferu.

*dwContext*<br/>
Identyfikator kontekstu służący do otwierania pliku. Aby uzyskać więcej informacji na temat *dwContext*, zobacz **uwagi** .

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [CInternetFile](../../mfc/reference/cinternetfile-class.md) .

### <a name="remarks"></a>Uwagi

`OpenFile`powinny być używane w następujących sytuacjach:

- Aplikacja ma dane, które należy wysłać i utworzyć jako plik na serwerze FTP, ale dane te nie znajdują się w pliku lokalnym. Po `OpenFile` otwarciu pliku aplikacja używa [CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write) w celu wysyłania danych z pliku FTP na serwer.

- Aplikacja musi pobrać plik z serwera i umieścić go w pamięci kontrolowanej przez aplikację, zamiast zapisywać go na dysku. Aplikacja używa [CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read) po użyciu `OpenFile` , aby otworzyć plik.

- Aplikacja wymaga poziomu kontroli nad transferem plików. Na przykład aplikacja może chcieć wyświetlić formant postępu wskazuje postęp transferu plików podczas pobierania pliku.

Po wywołaniu `OpenFile` i do momentu wywołania `CInternetConnection::Close`aplikacja może wywołać tylko [CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read), [CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write), `CInternetConnection::Close`lub [CFtpFileFind:: FindFile —](../../mfc/reference/cftpfilefind-class.md#findfile). Wywołania innych funkcji FTP dla tej samej sesji FTP zakończą się niepowodzeniem i ustawimy kod błędu na FTP_ETRANSFER_IN_PROGRESS.

Parametr *pstrFileName* może być częściowo kwalifikowaną nazwą pliku względem bieżącego katalogu lub w pełni kwalifikowana. Ukośnika odwrotnego\\() lub ukośnika (/) można użyć jako separatora katalogu dla każdej nazwy. `OpenFile`tłumaczy separatory nazw katalogów na odpowiednie znaki przed użyciem.

Zastąp wartości domyślne *dwContext* , aby ustawić identyfikator kontekstu na wybraną wartość. Identyfikator kontekstu jest skojarzony z tą konkretną operacją `CFtpConnection` obiektu utworzonego przez obiekt [CInternetSession](../../mfc/reference/cinternetsession-class.md) . Wartość jest zwracana do [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) w celu udostępnienia stanu operacji, z którą jest identyfikowany. Zapoznaj się [z artykułem internetowym pierwsze kroki: WinInet](../../mfc/wininet-basics.md) , aby uzyskać więcej informacji na temat identyfikatora kontekstu.

##  <a name="putfile"></a>CFtpConnection::P utFile

Wywołaj tę funkcję elementu członkowskiego, aby zapisać plik na serwerze FTP.

```
BOOL PutFile(
    LPCTSTR pstrLocalFile,
    LPCTSTR pstrRemoteFile,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pstrLocalFile*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku, który ma zostać wysłany z systemu lokalnego.

*pstrRemoteFile*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku do utworzenia na serwerze FTP.

*flagiDW*<br/>
Określa warunki, w których występuje transfer pliku. Może być dowolną ze stałych FTP_TRANSFER_ * opisanych w [OpenFile](#openfile).

*dwContext*<br/>
Identyfikator kontekstu służący do umieszczania pliku. Aby uzyskać więcej informacji na temat *dwContext*, zobacz **uwagi** .

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, może zostać wywołana [wartość GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) funkcji Win32, aby określić przyczynę błędu.

### <a name="remarks"></a>Uwagi

`PutFile`to procedura wysokiego poziomu, która obsługuje wszystkie operacje związane z przechowywaniem pliku na serwerze FTP. Aplikacje, które wysyłają tylko dane lub wymagają ściślejszej kontroli nad transferem plików, powinny używać [OpenFile](#openfile) i [CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write).

Zastąp `dwContext` wartości domyślne, aby ustawić identyfikator kontekstu na wybraną wartość. Identyfikator kontekstu jest skojarzony z tą konkretną operacją `CFtpConnection` obiektu utworzonego przez obiekt [CInternetSession](../../mfc/reference/cinternetsession-class.md) . Wartość jest zwracana do [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) w celu udostępnienia stanu operacji, z którą jest identyfikowany. Zapoznaj się [z artykułem internetowym pierwsze kroki: WinInet](../../mfc/wininet-basics.md) , aby uzyskać więcej informacji na temat identyfikatora kontekstu.

##  <a name="remove"></a>CFtpConnection:: Remove

Wywołaj tę funkcję elementu członkowskiego, aby usunąć określony plik z podłączonego serwera.

```
BOOL Remove(LPCTSTR pstrFileName);
```

### <a name="parameters"></a>Parametry

*pstrFileName*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, może zostać wywołana [wartość GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) funkcji Win32, aby określić przyczynę błędu.

### <a name="remarks"></a>Uwagi

Parametr *pstrFileName* może być częściowo kwalifikowaną nazwą pliku względem bieżącego katalogu lub w pełni kwalifikowana. Ukośnika odwrotnego\\() lub ukośnika (/) można użyć jako separatora katalogu dla każdej nazwy. `Remove` Funkcja tłumaczy separatory nazw katalogów na odpowiednie znaki przed ich użyciem.

##  <a name="removedirectory"></a>CFtpConnection::RemoveDirectory

Wywołaj tę funkcję elementu członkowskiego, aby usunąć określony katalog z podłączonego serwera.

```
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parametry

*pstrDirName*<br/>
Wskaźnik do ciągu zawierającego katalog, który ma zostać usunięty.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, może zostać wywołana [wartość GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) funkcji Win32, aby określić przyczynę błędu.

### <a name="remarks"></a>Uwagi

Użyj [GetCurrentDirectory](#getcurrentdirectory) , aby określić bieżący katalog roboczy serwera. Nie należy zakładać, że system zdalny nawiązał połączenie z katalogiem głównym.

Parametr *pstrDirName* może być częściowo lub w pełni kwalifikowana nazwa pliku względem bieżącego katalogu. Ukośnika odwrotnego\\() lub ukośnika (/) można użyć jako separatora katalogu dla każdej nazwy. `RemoveDirectory`tłumaczy separatory nazw katalogów na odpowiednie znaki przed ich użyciem.

##  <a name="rename"></a>CFtpConnection:: Rename

Wywołaj tę funkcję elementu członkowskiego, aby zmienić nazwę określonego pliku na podłączonym serwerze.

```
BOOL Rename(
    LPCTSTR pstrExisting,
    LPCTSTR pstrNew);
```

### <a name="parameters"></a>Parametry

*pstrExisting*<br/>
Wskaźnik do ciągu zawierającego bieżącą nazwę pliku, który ma zostać zmieniony.

*pstrNew*<br/>
Wskaźnik do ciągu zawierającego nową nazwę pliku.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, może zostać wywołana [wartość GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) funkcji Win32, aby określić przyczynę błędu.

### <a name="remarks"></a>Uwagi

Parametry *pstrExisting* i *pstrNew* mogą być częściowo kwalifikowaną nazwą pliku względem bieżącego katalogu lub w pełni kwalifikowany. Ukośnika odwrotnego\\() lub ukośnika (/) można użyć jako separatora katalogu dla każdej nazwy. `Rename`tłumaczy separatory nazw katalogów na odpowiednie znaki przed ich użyciem.

##  <a name="setcurrentdirectory"></a>CFtpConnection::SetCurrentDirectory

Wywołaj tę funkcję elementu członkowskiego, aby zmienić katalog na serwerze FTP.

```
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parametry

*pstrDirName*<br/>
Wskaźnik do ciągu zawierającego nazwę katalogu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, może zostać wywołana [wartość GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) funkcji Win32, aby określić przyczynę błędu.

### <a name="remarks"></a>Uwagi

Parametr *pstrDirName* może być częściowo lub w pełni kwalifikowana nazwa pliku względem bieżącego katalogu. Ukośnika odwrotnego\\() lub ukośnika (/) można użyć jako separatora katalogu dla każdej nazwy. `SetCurrentDirectory`tłumaczy separatory nazw katalogów na odpowiednie znaki przed ich użyciem.

Użyj [GetCurrentDirectory](#getcurrentdirectory) , aby określić bieżący katalog roboczy serwera FTP. Nie należy zakładać, że system zdalny nawiązał połączenie z katalogiem głównym.

## <a name="see-also"></a>Zobacz także

[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Klasa CInternetSession](../../mfc/reference/cinternetsession-class.md)
