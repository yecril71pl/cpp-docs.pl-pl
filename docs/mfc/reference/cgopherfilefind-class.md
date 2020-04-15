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
ms.openlocfilehash: 7a42b99c919abd9098bff1897c4c5febf443314d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373682"
---
# <a name="cgopherfilefind-class"></a>Klasa CGopherFileFind

Pomaga w wyszukiwaniu plików internetowych serwerów gopher.

> [!NOTE]
> Klasy `CGopherConnection`, `CGopherFile` `CGopherFileFind`, `CGopherLocator` i ich członkowie zostały przestarzałe, ponieważ nie działają na platformie Windows XP, ale będą nadal działać na wcześniejszych platformach.

## <a name="syntax"></a>Składnia

```
class CGopherFileFind : public CFileFind
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGopherFileFind::CGopherFileFind](#cgopherfilefind)|Konstruuje `CGopherFileFind` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGopherFileFind::FindFile](#findfile)|Znajduje plik na serwerze gopher.|
|[CGopherFileFind::FindNextFile](#findnextfile)|Kontynuuje wyszukiwanie plików z poprzedniego połączenia do [FindFile](#findfile).|
|[CGopherFileFind::GetCreationTime](#getcreationtime)|Pobiera czas określony plik został utworzony.|
|[CGopherFileFind::GetLastAccessTime](#getlastaccesstime)|Pobiera czas, w której ostatnio dostęp do określonego pliku.|
|[CGopherFileFind::GetLastWriteTime](#getlastwritetime)|Pobiera czas określony plik został ostatnio zapisany.|
|[CGopherFileFind::GetLength](#getlength)|Pobiera długość znalezionego pliku w bajtach.|
|[CGopherFileFind::GetLocator](#getlocator)|Pobierz `CGopherLocator` obiekt.|
|[CGopherFileFind::GetScreenName](#getscreenname)|Pobiera nazwę ekranu gopher.|
|[CGopherFileFind::IsDots](#isdots)|Testy dla bieżącego katalogu i nadrzędnych znaczników katalogów podczas iteracji za pośrednictwem plików.|

## <a name="remarks"></a>Uwagi

`CGopherFileFind`zawiera funkcje członkowskie, które rozpoczynają wyszukiwanie, lokalizują plik i zwracają adres URL pliku.

Inne klasy MFC przeznaczone do wyszukiwania w Internecie i plikach lokalnych obejmują [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) i [CFileFind](../../mfc/reference/cfilefind-class.md). Wraz `CGopherFileFind`z programem , klasy te zapewniają bezproblemowy mechanizm znajdowania określonych plików przez użytkownika, niezależnie od protokołu serwera, typu pliku lub lokalizacji (komputera lokalnego lub serwera zdalnego). Należy zauważyć, że nie ma klasy MFC do wyszukiwania na serwerach HTTP, ponieważ protokół HTTP nie obsługuje bezpośredniej manipulacji plikami wymaganej przez wyszukiwania.

> [!NOTE]
> `CGopherFileFind`nie obsługuje następujących funkcji członkowskich swojej klasy podstawowej [CFileFind:](../../mfc/reference/cfilefind-class.md)

- [Getroot](../../mfc/reference/cfilefind-class.md#getroot)

- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)

- [Ścieżka GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)

- [GetFileTitle (GetFileTitle)](../../mfc/reference/cfilefind-class.md#getfiletitle)

- [Plik GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)

Ponadto, gdy jest `CGopherFileFind`używana `CFileFind` z funkcją elementu członkowskiego [IsDots](../../mfc/reference/cfilefind-class.md#isdots) jest zawsze FALSE.

Aby uzyskać więcej informacji `CGopherFileFind` na temat używania i innych klas WinInet, zobacz artykuł [Programowanie internetowe z wininet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cfilefind](../../mfc/reference/cfilefind-class.md)

`CGopherFileFind`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

## <a name="cgopherfilefindcgopherfilefind"></a><a name="cgopherfilefind"></a>CGopherFileFind::CGopherFileFind

Ta funkcja elementu członkowskiego `CGopherFileFind` jest wywoływana do konstruowania obiektu.

```
explicit CGopherFileFind(
    CGopherConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pZkładanie*<br/>
Wskaźnik do [obiektu CGopherConnection.](../../mfc/reference/cgopherconnection-class.md)

*Dwcontext*<br/>
Identyfikator kontekstu dla operacji. Zobacz **Uwagi, aby** uzyskać więcej informacji na temat *dwContext*.

### <a name="remarks"></a>Uwagi

Wartość domyślna dla *dwContext* jest wysyłana przez MFC do `CGopherFileFind` obiektu z `CGopherFileFind` [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu, który utworzył obiekt. Podczas konstruowania `CGopherFileFind` obiektu, można zastąpić domyślne, aby ustawić identyfikator kontekstu do wartości wybranej. Identyfikator kontekstu jest zwracany do [CInternetSession::OnStatusCallback,](../../mfc/reference/cinternetsession-class.md#onstatuscallback) aby zapewnić stan obiektu, z którym jest identyfikowany. Zobacz artykuł [Pierwsze kroki internetowe: WinInet, aby](../../mfc/wininet-basics.md) uzyskać więcej informacji na temat identyfikatora kontekstu.

## <a name="cgopherfilefindfindfile"></a><a name="findfile"></a>CGopherFileFind::FindFile

Wywołanie tej funkcji elementu członkowskiego, aby znaleźć plik gopher.

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

*reflocator*<br/>
Odwołanie do [obiektu CGopherLocator.](../../mfc/reference/cgopherlocator-class.md)

*pstrString (wysnuwanie sznurkiem)*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku.

*Dwflags*<br/>
Flagi opisujące sposób obsługi tej sesji. Prawidłowe flagi to:

- INTERNET_FLAG_RELOAD Pobierz dane z serwera zdalnego, nawet jeśli są buforowane lokalnie.

- INTERNET_FLAG_DONT_CACHE Nie buforuj danych lokalnie ani w żadnych bramkach.

- INTERNET_FLAG_SECURE Żądaj bezpiecznych transakcji w sieci za pomocą warstwy bezpiecznych gniazd lub PCT. Ta flaga ma zastosowanie tylko do żądań HTTP.

- INTERNET_FLAG_USE_EXISTING Jeśli to możliwe, ponownie użyć istniejących połączeń `FindFile` z serwerem dla nowych żądań, zamiast tworzyć nową sesję dla każdego żądania.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać funkcję [Win32 GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Uwagi

Po `FindFile` wywołaniu, aby pobrać pierwszy obiekt gopher, można wywołać [FindNextFile,](#findnextfile) aby pobrać kolejne pliki gopher.

## <a name="cgopherfilefindfindnextfile"></a><a name="findnextfile"></a>CGopherFileFind::FindNextFile

Wywołanie tej funkcji elementu członkowskiego, aby kontynuować wyszukiwanie plików rozpoczęte wywołaniem [CGopherFileFind::FindFile](#findfile).

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli jest więcej plików; zero, jeśli znaleziony plik jest ostatnim w katalogu lub jeśli wystąpił błąd. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać funkcję [Win32 GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror). Jeśli znaleziony plik jest ostatnim plikiem w katalogu lub jeśli nie `GetLastError` można znaleźć pasujących plików, funkcja zwraca ERROR_NO_MORE_FILES.

## <a name="cgopherfilefindgetcreationtime"></a><a name="getcreationtime"></a>CGopherFileFind::GetCreationTime

Pobiera czas tworzenia dla bieżącego pliku.

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parametry

*pStał z czasem*<br/>
Wskaźnik do struktury [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) zawierającej czas utworzenia pliku.

*refTime (czas ref)*<br/>
Odwołanie do [obiektu CTime.](../../atl-mfc-shared/reference/ctime-class.md)

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; 0, jeśli się nie powiedzie. `GetCreationTime`zwraca wartość 0 tylko wtedy, [gdy findnextFile](#findnextfile) nigdy nie został wywołany dla tego `CGopherFileFind` obiektu.

### <a name="remarks"></a>Uwagi

Przed wywołaniem `GetCreationTime`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

> [!NOTE]
> Nie wszystkie systemy plików używają tej samej semantyki do zaimplementowania sygnatury czasowej zwracanej przez tę funkcję. Ta funkcja może zwracać tę samą wartość zwróconą przez inne funkcje sygnatury czasowej, jeśli podstawowy system plików lub serwer nie obsługuje zachowania atrybutu czasu. Zobacz [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) struktury, aby uzyskać informacje o formatach czasu. W niektórych systemach operacyjnych zwracany czas znajduje się w strefie czasowej lokalnej do komputera, gdy plik znajduje się. Aby uzyskać więcej informacji, zobacz interfejs API Systemu Plików Systemu Win32 [FileTimeToLocalFileTime.](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)

## <a name="cgopherfilefindgetlastaccesstime"></a><a name="getlastaccesstime"></a>CGopherFileFind::GetLastAccessTime

Pobiera czas, w której ostatnio dostęp do określonego pliku.

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>Parametry

*refTime (czas ref)*<br/>
Odwołanie do [obiektu CTime.](../../atl-mfc-shared/reference/ctime-class.md)

*pStał z czasem*<br/>
Wskaźnik do struktury [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) zawierającej czas ostatniego dostępu do pliku.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; 0, jeśli się nie powiedzie. `GetLastAccessTime`zwraca wartość 0 tylko wtedy, [gdy findnextFile](#findnextfile) nigdy nie został wywołany dla tego `CGopherFileFind` obiektu.

### <a name="remarks"></a>Uwagi

Przed wywołaniem `GetLastAccessTime`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

> [!NOTE]
> Nie wszystkie systemy plików używają tej samej semantyki do zaimplementowania sygnatury czasowej zwracanej przez tę funkcję. Ta funkcja może zwracać tę samą wartość zwróconą przez inne funkcje sygnatury czasowej, jeśli podstawowy system plików lub serwer nie obsługuje zachowania atrybutu czasu. Zobacz [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) struktury, aby uzyskać informacje o formatach czasu. W niektórych systemach operacyjnych zwracany czas znajduje się w strefie czasowej lokalnej do komputera, gdy plik znajduje się. Aby uzyskać więcej informacji, zobacz interfejs API Systemu Plików Systemu Win32 [FileTimeToLocalFileTime.](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)

## <a name="cgopherfilefindgetlastwritetime"></a><a name="getlastwritetime"></a>CGopherFileFind::GetLastWriteTime

Pobiera ostatni raz plik został zmieniony.

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parametry

*pStał z czasem*<br/>
Wskaźnik do struktury [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) zawierający czas, w której plik został ostatnio zapisany.

*refTime (czas ref)*<br/>
Odwołanie do [obiektu CTime.](../../atl-mfc-shared/reference/ctime-class.md)

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; 0, jeśli się nie powiedzie. `GetLastWriteTime`zwraca wartość 0 tylko wtedy, [gdy findnextFile](#findnextfile) nigdy nie został wywołany dla tego `CGopherFileFind` obiektu.

### <a name="remarks"></a>Uwagi

Przed wywołaniem `GetLastWriteTime`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

> [!NOTE]
> Nie wszystkie systemy plików używają tej samej semantyki do zaimplementowania sygnatury czasowej zwracanej przez tę funkcję. Ta funkcja może zwracać tę samą wartość zwróconą przez inne funkcje sygnatury czasowej, jeśli podstawowy system plików lub serwer nie obsługuje zachowania atrybutu czasu. Zobacz [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) struktury, aby uzyskać informacje o formatach czasu. W niektórych systemach operacyjnych zwracany czas znajduje się w strefie czasowej lokalnej do komputera, gdy plik znajduje się. Aby uzyskać więcej informacji, zobacz interfejs API Systemu Plików Systemu Win32 [FileTimeToLocalFileTime.](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)

## <a name="cgopherfilefindgetlength"></a><a name="getlength"></a>CGopherFileFind::GetLength

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać długość, w bajtach, znalezionego pliku.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość w bajtach znalezionego pliku.

### <a name="remarks"></a>Uwagi

`GetLength`Używa struktury Win32 [WIN32_FIND_DATA,](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) aby uzyskać wartość rozmiaru pliku w bajtach.

> [!NOTE]
> Od MFC 7.0 `GetLength` obsługuje 64-bitowe typy całkowite. Wcześniej istniejący kod utworzony za pomocą tej nowszej wersji biblioteki może spowodować ostrzeżenia o obcięciem.

### <a name="example"></a>Przykład

  Zobacz przykład [CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) (implementacji klasy podstawowej).

## <a name="cgopherfilefindgetlocator"></a><a name="getlocator"></a>CGopherFileFind::GetLocator

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) obiektu, który [FindFile](#findfile) używa do znalezienia pliku gopher.

```
CGopherLocator GetLocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt `CGopherLocator`.

## <a name="cgopherfilefindgetscreenname"></a><a name="getscreenname"></a>CGopherFileFind::GetScreenName

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać nazwę ekranu gopher.

```
CString GetScreenName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa ekranu gopher.

## <a name="cgopherfilefindisdots"></a><a name="isdots"></a>CGopherFileFind::IsDots

Testy dla bieżącego katalogu i nadrzędnych znaczników katalogów podczas iteracji za pośrednictwem plików.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli znaleziony plik ma nazwę "." lub "..", co oznacza, że znaleziony plik jest w rzeczywistości katalogiem. W przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Przed wywołaniem `IsDots`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

## <a name="see-also"></a>Zobacz też

[Klasa CFileFind](../../mfc/reference/cfilefind-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)<br/>
[Klasa CFileFind](../../mfc/reference/cfilefind-class.md)<br/>
[Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Klasa CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[Klasa CHttpFile](../../mfc/reference/chttpfile-class.md)
