---
title: Klasa CGopherFileFind
ms.date: 11/04/2016
f1_keywords:
- CGopherFileFind
- AFXINET/CGopherFileFind
- AFXINET/CGopherFileFind::CGopherFileFind
- AFXINET/CGopherFileFind::FindFile
- AFXINET/CGopherFileFind::FindNextFile
- AFXINET/CGopherFileFind::GetCreationTime
- AFXINET/CGopherFileFind::GetLastAccessTime
- AFXINET/CGopherFileFind::GetLastWriteTime
- AFXINET/CGopherFileFind::GetLength
- AFXINET/CGopherFileFind::GetLocator
- AFXINET/CGopherFileFind::GetScreenName
- AFXINET/CGopherFileFind::IsDots
helpviewer_keywords:
- CGopherFileFind [MFC], CGopherFileFind
- CGopherFileFind [MFC], FindFile
- CGopherFileFind [MFC], FindNextFile
- CGopherFileFind [MFC], GetCreationTime
- CGopherFileFind [MFC], GetLastAccessTime
- CGopherFileFind [MFC], GetLastWriteTime
- CGopherFileFind [MFC], GetLength
- CGopherFileFind [MFC], GetLocator
- CGopherFileFind [MFC], GetScreenName
- CGopherFileFind [MFC], IsDots
ms.assetid: 8465a979-6323-496d-ab4b-e81383fb999d
ms.openlocfilehash: 55c40fc04934f00ccb541a01cce611d9532bee1a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418581"
---
# <a name="cgopherfilefind-class"></a>Klasa CGopherFileFind

Pomoc dla wyszukiwania w pliku internetowym serwerów Gopher.

> [!NOTE]
>  Klasy `CGopherConnection`, `CGopherFile`, `CGopherFileFind``CGopherLocator` i ich członkowie są przestarzałe, ponieważ nie działają na platformie Windows XP, ale będą nadal działały na wcześniejszych platformach.

## <a name="syntax"></a>Składnia

```
class CGopherFileFind : public CFileFind
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CGopherFileFind::CGopherFileFind](#cgopherfilefind)|Konstruuje obiekt `CGopherFileFind`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CGopherFileFind:: FindFile —](#findfile)|Znajduje plik na serwerze gopher.|
|[CGopherFileFind::FindNextFile](#findnextfile)|Kontynuuje wyszukiwanie plików od poprzedniego wywołania do [FindFile —](#findfile).|
|[CGopherFileFind::GetCreationTime](#getcreationtime)|Pobiera godzinę utworzenia określonego pliku.|
|[CGopherFileFind::GetLastAccessTime](#getlastaccesstime)|Pobiera czas ostatniego dostępu do określonego pliku.|
|[CGopherFileFind::GetLastWriteTime](#getlastwritetime)|Pobiera czas, w którym określony plik został ostatnio zapisany.|
|[CGopherFileFind:: GetLength](#getlength)|Pobiera długość znalezionego pliku w bajtach.|
|[CGopherFileFind:: getlocatorer](#getlocator)|Pobierz obiekt `CGopherLocator`.|
|[CGopherFileFind:: getscreenname](#getscreenname)|Pobiera nazwę ekranu gopher.|
|[CGopherFileFind:: iskropek](#isdots)|Testuje znaczniki bieżącego katalogu i katalogu nadrzędnego podczas iterowania przez pliki.|

## <a name="remarks"></a>Uwagi

`CGopherFileFind` obejmuje funkcje członkowskie, które rozpoczynają wyszukiwanie, lokalizują plik i zwracają adres URL pliku.

Inne klasy MFC przeznaczone do przeszukiwania Internetu i plików lokalnych obejmują [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) i [CFileFind](../../mfc/reference/cfilefind-class.md). Wraz z `CGopherFileFind`mi te klasy zapewniają bezproblemowe mechanizmy użytkownika do znajdowania określonych plików, niezależnie od protokołu serwera, typu pliku lub lokalizacji (komputera lokalnego lub serwera zdalnego). Należy zauważyć, że nie istnieje klasa MFC do wyszukiwania na serwerach HTTP, ponieważ protokół HTTP nie obsługuje bezpośredniego manipulowania plikami wymaganego przez wyszukiwania.

> [!NOTE]
> `CGopherFileFind` nie obsługuje następujących funkcji Członkowskich swojej klasy podstawowej [CFileFind](../../mfc/reference/cfilefind-class.md):

- [Operacja GetRoot](../../mfc/reference/cfilefind-class.md#getroot)

- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)

- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)

- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)

- [GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)

Ponadto, gdy jest używany z `CGopherFileFind`, funkcja elementu członkowskiego `CFileFind` [iskropek](../../mfc/reference/cfilefind-class.md#isdots) ma zawsze wartość false.

Aby uzyskać więcej informacji o sposobach używania `CGopherFileFind` i innych klas WinInet, zobacz artykuł [programowanie internetowe za pomocą usługi WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CGopherFileFind`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet. h

##  <a name="cgopherfilefind"></a>CGopherFileFind::CGopherFileFind

Ta funkcja członkowska jest wywoływana w celu skonstruowania obiektu `CGopherFileFind`.

```
explicit CGopherFileFind(
    CGopherConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pConnection*<br/>
Wskaźnik do obiektu [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) .

*dwContext*<br/>
Identyfikator kontekstu dla operacji. Aby uzyskać więcej informacji na temat *dwContext*, zobacz **uwagi** .

### <a name="remarks"></a>Uwagi

Wartość domyślna parametru *dwContext* jest wysyłana przez MFC do obiektu `CGopherFileFind` z obiektu [CInternetSession](../../mfc/reference/cinternetsession-class.md) , który utworzył obiekt `CGopherFileFind`. Podczas konstruowania obiektu `CGopherFileFind` można zastąpić ustawienie domyślne, aby ustawić identyfikator kontekstu na wybraną wartość. Identyfikator kontekstu jest zwracany do [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) w celu udostępnienia stanu obiektu, z którym został zidentyfikowany. Zapoznaj się z artykułem [internetowym pierwsze kroki: WinInet](../../mfc/wininet-basics.md) , aby uzyskać więcej informacji na temat identyfikatora kontekstu.

##  <a name="findfile"></a>CGopherFileFind:: FindFile —

Wywołaj tę funkcję elementu członkowskiego, aby znaleźć plik gopher.

```
virtual BOOL FindFile(
    CGopherLocator& refLocator,
    LPCTSTR pstrString,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);

virtual BOOL FindFile(
    LPCTSTR pstrString,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>Parametry

*refLocator*<br/>
Odwołanie do obiektu [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) .

*pstrString*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku.

*flagiDW*<br/>
Flagi opisujące, jak obsłużyć tę sesję. Prawidłowe flagi to:

- INTERNET_FLAG_RELOAD pobrać danych z serwera zdalnego, nawet jeśli jest on buforowany lokalnie.

- INTERNET_FLAG_DONT_CACHE nie Buforuj danych lokalnie ani w żadnej bramie.

- INTERNET_FLAG_SECURE Żądaj bezpiecznych transakcji w sieci z SSL lub PCT. Ta flaga ma zastosowanie tylko do żądań HTTP.

- INTERNET_FLAG_USE_EXISTING Jeśli to możliwe, należy ponownie użyć istniejących połączeń z serwerem dla nowych żądań `FindFile`, zamiast tworzyć nową sesję dla każdego żądania.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0. Aby uzyskać rozszerzone informacje o błędzie, wywołaj [wartość GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)funkcji Win32.

### <a name="remarks"></a>Uwagi

Po wywołaniu `FindFile` do pobrania pierwszego obiektu gopher można wywołać [FindNextFile](#findnextfile) w celu pobrania kolejnych plików gopher.

##  <a name="findnextfile"></a>CGopherFileFind::FindNextFile

Wywołaj tę funkcję elementu członkowskiego, aby kontynuować wyszukiwanie plików rozpoczęte przy użyciu wywołania [CGopherFileFind:: FindFile —](#findfile).

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli istnieje więcej plików; zero, jeśli znaleziony plik jest ostatnim z nich w katalogu lub wystąpił błąd. Aby uzyskać rozszerzone informacje o błędzie, wywołaj [wartość GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)funkcji Win32. Jeśli znaleziony plik to ostatni plik w katalogu lub nie można znaleźć pasujących plików, funkcja `GetLastError` zwraca ERROR_NO_MORE_FILES.

##  <a name="getcreationtime"></a>CGopherFileFind::GetCreationTime

Pobiera godzinę utworzenia bieżącego pliku.

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parametry

*pTimeStamp*<br/>
Wskaźnik do struktury [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) zawierającej czas utworzenia pliku.

*refTime*<br/>
Odwołanie do obiektu [CTime](../../atl-mfc-shared/reference/ctime-class.md) .

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; 0, jeśli nie powiodło się. `GetCreationTime` zwraca wartość 0 tylko wtedy, gdy [FindNextFile](#findnextfile) nigdy nie został wywołany w tym obiekcie `CGopherFileFind`.

### <a name="remarks"></a>Uwagi

Musisz wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetCreationTime`.

> [!NOTE]
>  Nie wszystkie systemy plików używają tej samej semantyki do implementowania sygnatury czasowej zwracanej przez tę funkcję. Ta funkcja może zwracać tę samą wartość zwracaną przez inne funkcje sygnatur czasowych, jeśli podstawowy system plików lub serwer nie obsługuje zachowywania atrybutu czasu. Zapoznaj się ze strukturą [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) , aby uzyskać informacje na temat formatów czasu. W niektórych systemach operacyjnych zwracany czas znajduje się w strefie czasowej na komputerze lokalnym, na którym znajduje się plik. Aby uzyskać więcej informacji, zobacz Interfejs API Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) .

##  <a name="getlastaccesstime"></a>CGopherFileFind::GetLastAccessTime

Pobiera czas ostatniego dostępu do określonego pliku.

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>Parametry

*refTime*<br/>
Odwołanie do obiektu [CTime](../../atl-mfc-shared/reference/ctime-class.md) .

*pTimeStamp*<br/>
Wskaźnik do struktury [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) zawierający czas ostatniego dostępu do pliku.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; 0, jeśli nie powiodło się. `GetLastAccessTime` zwraca wartość 0 tylko wtedy, gdy [FindNextFile](#findnextfile) nigdy nie został wywołany w tym obiekcie `CGopherFileFind`.

### <a name="remarks"></a>Uwagi

Musisz wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetLastAccessTime`.

> [!NOTE]
>  Nie wszystkie systemy plików używają tej samej semantyki do implementowania sygnatury czasowej zwracanej przez tę funkcję. Ta funkcja może zwracać tę samą wartość zwracaną przez inne funkcje sygnatur czasowych, jeśli podstawowy system plików lub serwer nie obsługuje zachowywania atrybutu czasu. Zapoznaj się ze strukturą [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) , aby uzyskać informacje na temat formatów czasu. W niektórych systemach operacyjnych zwracany czas znajduje się w strefie czasowej na komputerze lokalnym, na którym znajduje się plik. Aby uzyskać więcej informacji, zobacz Interfejs API Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) .

##  <a name="getlastwritetime"></a>CGopherFileFind::GetLastWriteTime

Pobiera czas ostatniego zmiany pliku.

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parametry

*pTimeStamp*<br/>
Wskaźnik do struktury [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) zawierającej godzinę ostatniego zapisania pliku.

*refTime*<br/>
Odwołanie do obiektu [CTime](../../atl-mfc-shared/reference/ctime-class.md) .

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; 0, jeśli nie powiodło się. `GetLastWriteTime` zwraca wartość 0 tylko wtedy, gdy [FindNextFile](#findnextfile) nigdy nie został wywołany w tym obiekcie `CGopherFileFind`.

### <a name="remarks"></a>Uwagi

Musisz wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetLastWriteTime`.

> [!NOTE]
>  Nie wszystkie systemy plików używają tej samej semantyki do implementowania sygnatury czasowej zwracanej przez tę funkcję. Ta funkcja może zwracać tę samą wartość zwracaną przez inne funkcje sygnatur czasowych, jeśli podstawowy system plików lub serwer nie obsługuje zachowywania atrybutu czasu. Zapoznaj się ze strukturą [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) , aby uzyskać informacje na temat formatów czasu. W niektórych systemach operacyjnych zwracany czas znajduje się w strefie czasowej na komputerze lokalnym, na którym znajduje się plik. Aby uzyskać więcej informacji, zobacz Interfejs API Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) .

##  <a name="getlength"></a>CGopherFileFind:: GetLength

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać długość (w bajtach) znalezionego pliku.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Wartość zwrócona

Długość znalezionego pliku w bajtach.

### <a name="remarks"></a>Uwagi

`GetLength` używa struktury Win32 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) , aby uzyskać wartość rozmiaru pliku w bajtach.

> [!NOTE]
>  Począwszy od MFC 7,0, `GetLength` obsługuje 64-bitowe liczby całkowite. Wcześniej istniejący kod utworzony przy użyciu tej nowszej wersji biblioteki może spowodować ostrzeżenia obcinania.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CFile:: GetLength](../../mfc/reference/cfile-class.md#getlength) (Implementacja klasy bazowej).

##  <a name="getlocator"></a>CGopherFileFind:: getlocatorer

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać obiekt [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) , którego [FindFile —](#findfile) używa do znajdowania pliku gopher.

```
CGopherLocator GetLocator() const;
```

### <a name="return-value"></a>Wartość zwrócona

Obiekt `CGopherLocator`.

##  <a name="getscreenname"></a>CGopherFileFind:: getscreenname

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać nazwę ekranu gopher.

```
CString GetScreenName() const;
```

### <a name="return-value"></a>Wartość zwrócona

Nazwa ekranu gopher.

##  <a name="isdots"></a>CGopherFileFind:: iskropek

Testuje znaczniki bieżącego katalogu i katalogu nadrzędnego podczas iterowania przez pliki.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli znaleziony plik ma nazwę "." lub "..", co oznacza, że znaleziony plik jest w rzeczywistości katalogiem. W przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Musisz wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `IsDots`.

## <a name="see-also"></a>Zobacz też

[Klasa CFileFind](../../mfc/reference/cfilefind-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)<br/>
[Klasa CFileFind](../../mfc/reference/cfilefind-class.md)<br/>
[Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Klasa CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[Klasa CHttpFile](../../mfc/reference/chttpfile-class.md)
